# Makefile for use with Android's kernel/build system

KBUILD_OPTIONS += CAMERA_KERNEL_ROOT=$(shell pwd)
ifeq ($(ROOT_DIR),)
KBUILD_OPTIONS += KERNEL_ROOT=$(KERNEL_SRC)
else
KBUILD_OPTIONS += KERNEL_ROOT=$(ROOT_DIR)/$(KERNEL_DIR)
endif

KBUILD_OPTIONS += MODNAME=camera
KBUILD_EXTRA_SYMBOLS := $(M)/../mmrm-driver/Module.symvers

all: modules

modules dtbs:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) modules $(KBUILD_OPTIONS) KBUILD_EXTRA_SYMBOLS="$(KBUILD_EXTRA_SYMBOLS)"

modules_install:
	$(MAKE) M=$(M) -C $(KERNEL_SRC) modules_install

clean:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) clean
