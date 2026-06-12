---
title: "Can't install eee-control, dpkg error"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by alzorz on 2009-09-24
First i downloaded the latest .deb file from eee-controls website. The install error-ed halfway through, thou the files already installed weren't removed. So when i tried to install through synaptic i get this
```
anton@anton-laptop:~$ sudo apt-get install eee-control 
[sudo] password for anton:                             
Reading package lists... Done                          
Building dependency tree                               
Reading state information... Done                      
eee-control is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up eee-control (0.9.4) ...

Error! Could not find module source directory.
Directory: /usr/src/eeepc-laptop-20090415 does not exist.
ERROR: Failed to add module.
dpkg: error processing eee-control (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 eee-control
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I ran in to this problem one time before and to fix it then i had to reinstall ubuntu, now this time I'm wondering if there is any other solution to fix this problem?

PS. did a little try to fix the problem by removing the folder eeepc-laptop... but after i did they i got another error which is the one in the code bracket. Would like to remove any trace of eee-control from my install so i can do a fresh install with it without all the errors i get now...

Best regards alzorz

---

### Post by mikeyphi on 2009-09-24
This may help....
Open a terminal and enter the following:

sudo dpkg --configure -a



Then enter password when requested

---

### Post by alzorz on 2009-09-24
didn't work =(, got the same error...

---

### Post by drs305 on 2009-09-24
> **alzorz said:**
>  Would like to remove any trace of eee-control from my install so i can do a fresh install with it without all the errors i get now...


Try deleting/moving just the file causing the error. I don't have eec-control, so the name may be different:
```

sudo mv /var/lib/dpkg/info/[COLOR="DarkRed"]eec-control[/COLOR].postinst
sudo apt-get update

```

If you still get errors, and really want to remove the eec-control information, open the following file and remove the eec-control information section. Delete the entire section starting with "Package: eec-control" and ending with the blank line.
```

sudo cp /var/lib/dpkg/status ~/Desktop/status.bak
gksu gedit /var/lib/dpkg/status

```
Save the file, then run "sudo apt-get update" again.

---

### Post by alzorz on 2009-09-24
> 
If you still get errors, and really want to remove the eec-control information, open the following file and remove the eec-control information section. Delete the entire section starting with "Package: eec-control" and ending with the blank line.
```

sudo cp /var/lib/dpkg/status ~/Desktop/status.bak
gksu gedit /var/lib/dpkg/status

```
Save the file, then run "sudo apt-get update" again.

thanks, this worked perfectly :)

---

### Post by cong06 on 2009-11-23
Wait? how did that fix the problem?

I'm still getting an error on install:
```

isaac@phaff:~$ sudo dpkg -i web/eee/eee-control_0.9.4_all~jaunty.deb 
Selecting previously deselected package eee-control.
(Reading database ... 196189 files and directories currently installed.)
Unpacking eee-control (from .../eee-control_0.9.4_all~jaunty.deb) ...
Setting up eee-control (0.9.4) ...

Creating symlink /var/lib/dkms/eeepc-laptop/20090415/source ->
                 /usr/src/eeepc-laptop-20090415

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-14-generic"....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.31-14-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/eeepc-laptop/20090415/build/ for more information.
0
0
ERROR: Failed building module.
dpkg: error processing eee-control (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for desktop-file-utils ...
Processing triggers for sreadahead ...
Errors were encountered while processing:
 eee-control

```
Going to the folder where the log is:
```

isaac@phaff:~$ cat /var/lib/dkms/eeepc-laptop/20090415/build/make.log
DKMS make.log for eeepc-laptop-20090415 for kernel 2.6.31-14-generic (i686)
Mon Nov 23 10:08:12 EAT 2009
make[1]: Entering directory `/var/lib/dkms/eeepc-laptop/20090415/build'
cd /lib/modules/2.6.31-14-generic/build && make -C /lib/modules/2.6.31-14-generic/build M=/var/lib/dkms/eeepc-laptop/20090415/build modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.o
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:313: warning: ‘enum rfkill_state’ declared inside parameter list
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:313: warning: its scope is only this definition or declaration, which is probably not what you want
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:313: error: parameter 2 (‘state’) has incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c: In function ‘eeepc_wlan_rfkill_set’:
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:315: error: ‘RFKILL_STATE_SOFT_BLOCKED’ undeclared (first use in this function)
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:315: error: (Each undeclared identifier is reported only once
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:315: error: for each function it appears in.)
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c: At top level:
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:322: warning: ‘enum rfkill_state’ declared inside parameter list
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c: In function ‘eeepc_wlan_rfkill_state’:
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:325: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:325: error: ‘RFKILL_STATE_UNBLOCKED’ undeclared (first use in this function)
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:327: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:327: error: ‘RFKILL_STATE_SOFT_BLOCKED’ undeclared (first use in this function)
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c: At top level:
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:332: warning: ‘enum rfkill_state’ declared inside parameter list
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:332: error: parameter 2 (‘state’) has incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c: In function ‘eeepc_bluetooth_rfkill_set’:
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:334: error: ‘RFKILL_STATE_SOFT_BLOCKED’ undeclared (first use in this function)
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c: At top level:
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:341: warning: ‘enum rfkill_state’ declared inside parameter list
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c: In function ‘eeepc_bluetooth_rfkill_state’:
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:344: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:344: error: ‘RFKILL_STATE_UNBLOCKED’ undeclared (first use in this function)
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:346: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:346: error: ‘RFKILL_STATE_SOFT_BLOCKED’ undeclared (first use in this function)
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c: In function ‘eeepc_hotk_add’:
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:677: error: implicit declaration of function ‘rfkill_allocate’
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:678: warning: assignment makes pointer from integer without a cast
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:683: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:684: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:686: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:689: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:690: error: ‘RFKILL_STATE_UNBLOCKED’ undeclared (first use in this function)
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:692: error: implicit declaration of function ‘rfkill_set_default’
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:696: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:697: error: ‘RFKILL_STATE_SOFT_BLOCKED’ undeclared (first use in this function)
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:710: warning: assignment makes pointer from integer without a cast
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:715: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:716: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:719: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:723: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:730: error: dereferencing pointer to incomplete type
/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.c:750: error: implicit declaration of function ‘rfkill_free’
make[3]: *** [/var/lib/dkms/eeepc-laptop/20090415/build/eeepc-laptop.o] Error 1
make[2]: *** [_module_/var/lib/dkms/eeepc-laptop/20090415/build] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [generic] Error 2
make[1]: Leaving directory `/var/lib/dkms/eeepc-laptop/20090415/build'
make: *** [eeepc-laptop.o] Error 2

```


where is the karmic build?

---

