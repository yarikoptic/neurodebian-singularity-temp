# Copyright (c) 2017, Yaroslav O. Halchenko. All rights reserved. MIT license
#
# The purpose of the Singularity environment is to provide a relatively full
# suite of tools provided primarily by Debian/NeuroDebian for runnin various
# neuroimaging analyses.
#
# Notes:
#  - Due to  https://github.com/singularityware/singularity/issues/471
#    bootstrapping leads to non-usable/non-removable-without-reboot
#    image due to some rogue run away processes.
#    This line could help to kill them but should be used with caution
#    since could kill other unrelated processes
#
#      grep -l loop /proc/*/mountinfo | sed -e 's,/proc/\(.*\)/.*,\1,g' | while read pid; do sudo kill $pid; done
#
# Set size to be 12000 on singularity-hub
#
# Changelog
# ---------
# 2.2
#  - fresh annex with patched git to avoid "Out of memory, getdelim failed" bug
#  - added some tools useful for debugging (gdb)
#  - additional mountpoints (/scratch)
#  - (note) pip is not installed on purpose, use the one within virtualenv(s)
# 2.x
#  - switch to stretch
#  - TODO make reproducible
#  - bids-validator from 0.22
#  - Added ants, convert3d
#
# TODOs
# -----
# - package bids-validator

BootStrap: debootstrap
OSVersion: stretch
MirrorURL: http://http.debian.net/debian/
#MirrorURL: http://smaug.datalad.org:3142/debian/

# so if image is executed we just enter the environment
%runscript
    echo "Welcome to the NeuroDebian v 2.2 (Debian stretch) environment"
    echo "Please source /etc/fsl/fsl.sh if you need FSL, /etc/afni/afni.sh if you need AFNI"
    /bin/bash

%post
    echo "Configuring the environment"
