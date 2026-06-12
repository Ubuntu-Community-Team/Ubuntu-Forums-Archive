---
title: "Setting up LTSP to build a thin client system"
date: 2015-02-05
forum: Networking &amp; Wireless
---

### Post by Daniel_Vernall on 2015-02-05
[SIZE=3]I'm am trying to set up on Zorin 9 (Based on Ubuntu 14.04) but am having problems.

I've been following this How-to:

[http://ubuntuforums.org/showthread.php?t=2173749&page=2&p=13222023#post13222023](http://ubuntuforums.org/showthread.php?t=2173749&page=2&p=13222023#post13222023)

I'm having problems with the second step.
sudo ltsp-build-client

I get this when running with --debug:

DEBUG: Loading plugin: configure: /usr/share/ltsp/plugins/ltsp-build-client/common/001-load-configuration-file
DEBUG: Loading plugin: configure: /usr/share/ltsp/plugins/ltsp-build-client/common/001-set-arch
DEBUG: Loading plugin: configure: /usr/share/ltsp/plugins/ltsp-build-client/common/001-set-exclude
DEBUG: Loading plugin: configure: /usr/share/ltsp/plugins/ltsp-build-client/common/010-etc-hosts
DEBUG: Loading plugin: configure: /usr/share/ltsp/plugins/ltsp-build-client/common/010-mount-proc
DEBUG: Loading plugin: configure: /usr/share/ltsp/plugins/ltsp-build-client/common/010-set-base
DEBUG: Loading plugin: configure: /usr/share/ltsp/plugins/ltsp-build-client/common/010-set-chroot
DEBUG: Loading plugin: configure: /usr/share/ltsp/plugins/ltsp-build-client/common/020-rootpath
DEBUG: Loading plugin: configure: /usr/share/ltsp/plugins/ltsp-build-client/common/030-update-sshkeys
DEBUG: Loading plugin: configure: /usr/share/ltsp/plugins/ltsp-build-client/common/035-update-kernels
DEBUG: Loading plugin: configure: /usr/share/ltsp/plugins/ltsp-build-client/common/091-unmount-dirs
DEBUG: Loading plugins in MODE=before-install:
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/000-check-paths
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/000-enable-debug
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/001-load-configuration-file
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/001-set-arch
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/001-set-exclude
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/010-etc-hosts
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/010-mount-proc
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/010-set-base
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/010-set-chroot
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/020-rootpath
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/030-update-sshkeys
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/035-update-kernels
DEBUG: Loading plugin: before-install: /usr/share/ltsp/plugins/ltsp-build-client/common/091-unmount-dirs
DEBUG: Loading plugins in MODE=install:
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/000-check-paths
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/000-enable-debug
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/001-load-configuration-file
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/001-set-arch
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/001-set-exclude
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/010-etc-hosts
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/010-mount-proc
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/010-set-base
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/010-set-chroot
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/020-rootpath
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/030-update-sshkeys
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/035-update-kernels
DEBUG: Loading plugin: install: /usr/share/ltsp/plugins/ltsp-build-client/common/091-unmount-dirs
DEBUG: Loading plugins in MODE=after-install:
DEBUG: Loading plugin: after-install: /usr/share/ltsp/plugins/ltsp-build-client/common/000-check-paths
DEBUG: Loading plugin: after-install: /usr/share/ltsp/plugins/ltsp-build-client/common/000-enable-debug
DEBUG: Loading plugin: after-install: /usr/share/ltsp/plugins/ltsp-build-client/common/001-load-configuration-file
DEBUG: Loading plugin: after-install: /usr/share/ltsp/plugins/ltsp-build-client/common/001-set-arch
DEBUG: Loading plugin: after-install: /usr/share/ltsp/plugins/ltsp-build-client/common/001-set-exclude
DEBUG: Loading plugin: after-install: /usr/share/ltsp/plugins/ltsp-build-client/common/010-etc-hosts
/usr/share/ltsp/plugins/ltsp-build-client/common/010-etc-hosts: line 3: /opt/ltsp/amd64/etc/hosts: No such file or directory
error: LTSP client installation ended abnormally

I have tried uninstalling ltsp-server and reinstalling. But the same error occurs.

Simply running the build client script again gives:

NOTE: Root directory /opt/ltsp/amd64 already exists, this will lead to problems, please remove it before trying again. Exiting.
error: LTSP client installation ended abnormally

Which when I do returns me to the original error as above.

Any advice?

Thank you[/SIZE]

---

### Post by mrnerd2 on 2015-04-15
> **Daniel_Vernall said:**
> [SIZE=3]I'm am trying to set up on Zorin 9 (Based on Ubuntu 14.04) but am having problems.

I've been following this How-to:

[http://ubuntuforums.org/showthread.php?t=2173749&page=2&p=13222023#post13222023](http://ubuntuforums.org/showthread.php?t=2173749&page=2&p=13222023#post13222023)

I'm having problems with the second step.
sudo ltsp-build-client

I get this when running with --debug:
.....
DEBUG: Loading plugin: after-install: /usr/share/ltsp/plugins/ltsp-build-client/common/010-etc-hosts
/usr/share/ltsp/plugins/ltsp-build-client/common/010-etc-hosts: line 3: /opt/ltsp/amd64/etc/hosts: No such file or directory
error: LTSP client installation ended abnormally

I have tried uninstalling ltsp-server and reinstalling. But the same error occurs.

Simply running the build client script again gives:

NOTE: Root directory /opt/ltsp/amd64 already exists, this will lead to problems, please remove it before trying again. Exiting.
error: LTSP client installation ended abnormally

Which when I do returns me to the original error as above.

Any advice?

Thank you[/SIZE]

I just had this issue myself.  Removing the directory (in your case, amd64) and then creating a symlink to Ubuntu in /usr/share/ltsp/plugins/ltsp-build-client to the release you're on, (In my case, and yours, 'Zorin') allowed it all to build for me, which workaround I picked up here: [http://forums.linuxmint.com/viewtopic.php?f=47&t=83991](http://forums.linuxmint.com/viewtopic.php?f=47&t=83991)

So:
```

# rm -Rf /opt/ltsp/amd64
# cd /usr/share/ltsp/plugins/ltsp-build-client
# ln -s Ubuntu/ Zorin

```
Should allow it to all build successfully.

Randy

---

### Post by ramesh24 on 2016-03-05
First, completely remove the installed ltsp chroot
sudo rm -rf /opt/ltsp/*
Then rebuild the client again
sudo ltsp-build-client   
If you want to create 386 image client then suffix --arch i386 to the above mentioned command.

---

