# Tencent is pleased to support the open source community by making TKEStack
# available.
#
# Copyright (C) 2012-2019 Tencent. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License"); you may not use
# this file except in compliance with the License. You may obtain a copy of the
# License at
#
# https://opensource.org/licenses/Apache-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
# WARRANTIES OF ANY KIND, either express or implied.  See the License for the
# specific language governing permissions and limitations under the License.

VERSION = 2.0.16-r0
REGISTRY_PREFIX ?= tkestack

TEMP_DIR:=$(shell mktemp -d)

.PHONY: all
all: keepalived

.PHONY: keepalived
keepalived:
	@echo "===========> Building $@ $(VERSION) docker image"
	@$(DOCKER) build --pull -t $(REGISTRY_PREFIX)/$@:$(VERSION) -f ./Dockerfile $(ROOT_DIR)/build/docker/tools/keepalived

	@echo "===========> Building $@ $(VERSION) docker image"
	docker build --pull -t $(REGISTRY_PREFIX)/$@:$(VERSION) -f ./Dockerfile ${TEMP_DIR}
	@echo "===========> Pushing $@ $(VERSION) image to $(REGISTRY_PREFIX)"
	docker push $(REGISTRY_PREFIX)/$@:$(VERSION)
	rm -rf "${TEMP_DIR}"
