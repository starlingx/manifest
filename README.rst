==================
StarlingX Manifest
==================

Download
--------
The StarlingX source code can be downloaded from the default manifest XML file,
by using the git-repo tool [1]_, with the following commands::

    export MANIFEST_URL="https://opendev.org/starlingx/manifest.git"
    export MANIFEST_BRANCH="master"
    export MANIFEST="default.xml"
    repo init -u ${MANIFEST_URL} -b ${MANIFEST_BRANCH} -m ${MANIFEST}
    repo sync

StarlingX Build Environment
---------------------------
The StarlingX Build Environment [2]_ is a set of containers designed to run in a
Kubernetes environment.

As an alternative, a Vagrant-based StarlingX Build Environment is available in
the starlingx/tis-repo [3]_.

Layered Build
-------------
Build layering [4]_ is a feature to accelerate development within StarlingX.
It optimizes the build of a small set of most-used top level packages, while
avoiding rebuild of a large amount of infrequently used packages.

The packages are partitioned into the following layers, according to the
corresponding manifests:

- compiler: Low level build tools: compilers, scripts, and packaging tools;
- distro: Linux and third party packages, e.g. ceph, openstack;
- flock: Basic StarlingX packages. These are the most used ones.

Reserved Manifests
------------------
The following manifests are reserved:

- common: packages always included in the build, regardless of layer;
- containers: packages to build containers;
- default: used as a means to download the StarlingX source code.

Developer Notes
---------------
When updating XML files, please remember to update the appropriate .gitignore
file in https://opendev.org/starlingx/root otherwise the "repo status" command
will show the new repo as an untracked change.

When updating the default.xml manifest, please also remember to update the
appropriate layer manifest as well.

References
----------
.. [1] https://gerrit.googlesource.com/git-repo/#install
.. [2] https://wiki.openstack.org/wiki/StarlingX/DebianBuildEnvironment
.. [3] https://opendev.org/starlingx/tis-repo
.. [4] https://docs.starlingx.io/developer_resources/Layered_Build.html
