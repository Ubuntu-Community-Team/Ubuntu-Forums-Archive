---
title: "unstable"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by vagelism on 2009-11-22
Hello to all. I had a problem with my pc. I had not adicuate free space in my disk. Now I freed up enought but still it is unstable.
My taskbar desapears when I click the shutdown icon, then I have to press the computers shut down. Many applications still tell me that I do not . What can I do?
Thank you.
Keep it simple please...
I am new to this.

---

### Post by kansasnoob on 2009-11-22
Would you post the output of the command:

```
df -H
```

That will just show info about partition size and free space.

---

### Post by vagelism on 2009-11-22
> **kansasnoob said:**
> Would you post the output of the command:

```
df -H
```

That will just show info about partition size and free space.

vagelism@unknown:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdb1               16G    16G      0 100% /
varrun                 1.1G    99k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G    46k   1.1G   1% /dev
devshm                 1.1G    13k   1.1G   1% /dev/shm
overflow               1.1M    21k   1.1M   2% /tmp
gvfs-fuse-daemon        16G    16G      0 100% /home/vagelism/.gvfs
vagelism@unknown:~$

---

### Post by kansasnoob on 2009-11-22
> **vagelism said:**
> vagelism@unknown:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdb1               16G    16G      0 100% /
varrun                 1.1G    99k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G    46k   1.1G   1% /dev
devshm                 1.1G    13k   1.1G   1% /dev/shm
overflow               1.1M    21k   1.1M   2% /tmp
gvfs-fuse-daemon        16G    16G      0 100% /home/vagelism/.gvfs
vagelism@unknown:~$

That does show the full 16GB is 100% used.

Please now post the output of:

```
sudo parted /dev/sdb print
```

---

### Post by vagelism on 2009-11-22
> **kansasnoob said:**
> That does show the full 16GB is 100% used.

Please now post the output of:

```
sudo parted /dev/sdb print
```

Disk /dev/sdb: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  15.4GB  15.4GB  primary   ext3         boot 
 2      15.4GB  16.1GB  724MB   extended                    
 5      15.4GB  16.1GB  724MB   logical   linux-swap        

Information: Don't forget to update /etc/fstab, if necessary.             

vagelism@unknown:~$

---

### Post by kansasnoob on 2009-11-22
Sorry for the delay, I had to get some rest.

That drive is just full!

You might gain a tiny amount of space running the command:

```
sudo apt-get autoclean
```

That only removes .deb archives from packages which are no longer installed on the system. The next is a bit more radical because it will remove .deb files even for packages currently installed. But most of the time you probably don't need the .debs any more, and you're in a heck of a pinch so:

```
sudo apt-get clean
```

I've seen those two commands sometimes free up in the neighborhood of 1/2GB of space, but another thing you could do is check for installed kernels. First we want to see what kernel you're using so post the output of:

```
uname -r
```

And a double check of sorts, post the output of this command:

```
apt-cache showpkg linux-libc-dev
```

Then to see how many old kernels are installed post the output of the following three commands:

```
apt-cache showpkg linux-image
```

```
apt-cache showpkg linux-headers
```

```
apt-cache showpkg linux-headers-generic
```

From that output someone here should be able to recommend which kernels may be safe to remove and how to do it. In his grub2 tutorial drs305 wrote a bit about that:

> # Too Many Kernels? Kernels removed via Synaptic or with "apt-get remove" will automatically update grub.cfg and no user action is required.

    * In Synaptic, type the kernel number in the search window at the upper right (for example - 2.6.28-11).
    * Find the "linux-image" and "linux-headers" files for the applicable kernel (example - linux-image-2.6.26-11 or "linux-image-2.6.26-11-generic).
    * Right click and select "Mark for Complete Removal" and then press the Apply main menu button.
    * The kernels will be removed from your system and from the Grub menu.
    * If you are not sure of the kernel you are currently using, in a terminal type "uname -r".
    * Many users keep one previous kernel on the machine which previously ran without problems.


Another way to free up a little bit of space is to run:

```
sudo apt-get -f install
```

Which may recommend running:

```
sudo apt-get autoremove
```

That may remove old dependencies that are no longer needed due to package removal or updates.

But ultimately we need to explore alternative storage options. The output of the following command would give us a general idea of your entire drive and partition layout:

```
sudo fdisk -l
```

BTW that's a lower case L at the end.

I'd guess that sdb is an external usb drive, eh? Maybe sda has available space that could be partitioned for shared storage?

Or maybe some DVD-RW discs could be a solution?

---

### Post by vagelism on 2009-11-22
> **kansasnoob said:**
> Sorry for the delay, I had to get some rest.

That drive is just full!

You might gain a tiny amount of space running the command:

```
sudo apt-get autoclean
```

That only removes .deb archives from packages which are no longer installed on the system. The next is a bit more radical because it will remove .deb files even for packages currently installed. But most of the time you probably don't need the .debs any more, and you're in a heck of a pinch so:

```
sudo apt-get clean
```

I've seen those two commands sometimes free up in the neighborhood of 1/2GB of space, but another thing you could do is check for installed kernels. First we want to see what kernel you're using so post the output of:

```
uname -r
```

And a double check of sorts, post the output of this command:

```
apt-cache showpkg linux-libc-dev
```

Then to see how many old kernels are installed post the output of the following three commands:

```
apt-cache showpkg linux-image
```

```
apt-cache showpkg linux-headers
```

```
apt-cache showpkg linux-headers-generic
```

From that output someone here should be able to recommend which kernels may be safe to remove and how to do it. In his grub2 tutorial drs305 wrote a bit about that:



Another way to free up a little bit of space is to run:

```
sudo apt-get -f install
```

Which may recommend running:

```
sudo apt-get autoremove
```

That may remove old dependencies that are no longer needed due to package removal or updates.

But ultimately we need to explore alternative storage options. The output of the following command would give us a general idea of your entire drive and partition layout:

```
sudo fdisk -l
```

BTW that's a lower case L at the end.

I'd guess that sdb is an external usb drive, eh? Maybe sda has available space that could be partitioned for shared storage?

Or maybe some DVD-RW discs could be a solution?





vagelism@unknown:~$ apt-cache showpkg linux-image
Package: linux-image
Versions: 
2.6.24.25.27 (/var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages) (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages
                  MD5: bbb651153b198d4cc1090132ccf7582b

2.6.24.16.18 (/var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages
                  MD5: bbb651153b198d4cc1090132ccf7582b


Reverse Depends: 
  linux,linux-image 2.6.24.25.27
  dkms,linux-image
  linux,linux-image 2.6.24.16.18
  shorewall-common,linux-image
Dependencies: 
2.6.24.25.27 - linux-image-generic (5 2.6.24.25.27) 
2.6.24.16.18 - linux-image-generic (5 2.6.24.16.18) 
Provides: 
2.6.24.25.27 - 
2.6.24.16.18 - 
Reverse Provides: 
linux-image-2.6.24-19-eeepc 2.6.24-19.34
linux-image-2.6.24-21-eeepc 2.6.24-21.39eeepc1
linux-image-2.6.24-24-xen 2.6.24-24.59
linux-image-2.6.24-24-rt 2.6.24-24.59
linux-image-2.6.24-24-openvz 2.6.24-24.59
linux-image-2.6.24-24-virtual 2.6.24-24.59
linux-image-2.6.24-24-server 2.6.24-24.59
linux-image-2.6.24-24-generic 2.6.24-24.59
linux-image-2.6.24-24-386 2.6.24-24.59
linux-image-2.6.24-25-xen 2.6.24-25.63
linux-image-2.6.24-25-rt 2.6.24-25.63
linux-image-2.6.24-25-openvz 2.6.24-25.63
linux-image-2.6.24-24-xen 2.6.24-24.61
linux-image-2.6.24-24-rt 2.6.24-24.61
linux-image-2.6.24-24-openvz 2.6.24-24.61
linux-image-2.6.24-23-xen 2.6.24-23.52
linux-image-2.6.24-23-rt 2.6.24-23.52
linux-image-2.6.24-23-openvz 2.6.24-23.52
linux-image-2.6.24-22-xen 2.6.24-22.45
linux-image-2.6.24-22-rt 2.6.24-22.45
linux-image-2.6.24-22-openvz 2.6.24-22.45
linux-image-2.6.24-21-xen 2.6.24-21.43
linux-image-2.6.24-21-rt 2.6.24-21.43
linux-image-2.6.24-21-openvz 2.6.24-21.43
linux-image-2.6.24-19-xen 2.6.24-19.41
linux-image-2.6.24-19-rt 2.6.24-19.41
linux-image-2.6.24-19-openvz 2.6.24-19.41
linux-image-2.6.24-18-xen 2.6.24-18.32
linux-image-2.6.24-18-rt 2.6.24-18.32
linux-image-2.6.24-18-openvz 2.6.24-18.32
linux-image-2.6.24-25-virtual 2.6.24-25.63
linux-image-2.6.24-25-server 2.6.24-25.63
linux-image-2.6.24-25-generic 2.6.24-25.63
linux-image-2.6.24-25-386 2.6.24-25.63
linux-image-2.6.24-24-virtual 2.6.24-24.61
linux-image-2.6.24-24-server 2.6.24-24.61
linux-image-2.6.24-24-generic 2.6.24-24.61
linux-image-2.6.24-24-386 2.6.24-24.61
linux-image-2.6.24-23-virtual 2.6.24-23.52
linux-image-2.6.24-23-server 2.6.24-23.52
linux-image-2.6.24-23-generic 2.6.24-23.52
linux-image-2.6.24-23-386 2.6.24-23.52
linux-image-2.6.24-22-virtual 2.6.24-22.45
linux-image-2.6.24-22-server 2.6.24-22.45
linux-image-2.6.24-22-generic 2.6.24-22.45
linux-image-2.6.24-22-386 2.6.24-22.45
linux-image-2.6.24-21-virtual 2.6.24-21.43
linux-image-2.6.24-21-server 2.6.24-21.43
linux-image-2.6.24-21-generic 2.6.24-21.43
linux-image-2.6.24-21-386 2.6.24-21.43
linux-image-2.6.24-19-virtual 2.6.24-19.41
linux-image-2.6.24-19-server 2.6.24-19.41
linux-image-2.6.24-19-generic 2.6.24-19.41
linux-image-2.6.24-19-386 2.6.24-19.41
linux-image-2.6.24-18-virtual 2.6.24-18.32
linux-image-2.6.24-18-server 2.6.24-18.32
linux-image-2.6.24-18-generic 2.6.24-18.32
linux-image-2.6.24-18-386 2.6.24-18.32
linux-image-2.6.24-16-xen 2.6.24-16.30
linux-image-2.6.24-16-rt 2.6.24-16.30
linux-image-2.6.24-16-openvz 2.6.24-16.30
linux-image-2.6.24-16-virtual 2.6.24-16.30
linux-image-2.6.24-16-server 2.6.24-16.30
linux-image-2.6.24-16-generic 2.6.24-16.30
linux-image-2.6.24-16-386 2.6.24-16.30
vagelism@unknown:~$ 




vagelism@unknown:~$ apt-cache showpkg linux-libc-dev
Package: linux-libc-dev
Versions: 
2.6.24-25.63 (/var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages) (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages
                  MD5: f12d9ca47be5969cd90b3d685b72b0f5

2.6.24-16.30 (/var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages
                  MD5: f12d9ca47be5969cd90b3d685b72b0f5


Reverse Depends: 
  nvidia-new-kernel-source-envy,linux-libc-dev
  nvidia-legacy-kernel-source-envy,linux-libc-dev
  nvidia-kernel-source-envy,linux-libc-dev
  fglrx-kernel-source-envy,linux-libc-dev
  libc6-dev,linux-libc-dev
  librsbac-dev,linux-libc-dev
  libc6-dev,linux-libc-dev
Dependencies: 
2.6.24-25.63 - amd64-libs-dev (1 1.1) dvb-dev (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) linux-kernel-headers (0 (null)) dvb-dev (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) linux-kernel-headers (0 (null)) 
2.6.24-16.30 - amd64-libs-dev (1 1.1) dvb-dev (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) linux-kernel-headers (0 (null)) dvb-dev (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) linux-kernel-headers (0 (null)) 
Provides: 
2.6.24-25.63 - linux-kernel-headers 
2.6.24-16.30 - linux-kernel-headers 
Reverse Provides: 
vagelism@unknown:~$ 






vagelism@unknown:~$ apt-cache showpkg linux-headers
Package: linux-headers
Versions: 

Reverse Depends: 
  nvidia-new-kernel-source-envy,linux-headers
  nvidia-legacy-kernel-source-envy,linux-headers
  nvidia-kernel-source-envy,linux-headers
  fglrx-kernel-source-envy,linux-headers
  kvm-source,linux-headers
  em8300-source,linux-headers
  kvm-source,linux-headers
  dkms,linux-headers
  alsa-source,linux-headers
Dependencies: 
Provides: 
Reverse Provides: 
linux-headers-2.6.24-19-eeepc 2.6.24-19.34
linux-headers-2.6.24-21-eeepc 2.6.24-21.39eeepc1
linux-headers-2.6.24-21 2.6.24-21.39eeepc1
linux-headers-2.6.24-24-xen 2.6.24-24.59
linux-headers-2.6.24-24-virtual 2.6.24-24.59
linux-headers-2.6.24-24-server 2.6.24-24.59
linux-headers-2.6.24-24-rt 2.6.24-24.59
linux-headers-2.6.24-24-openvz 2.6.24-24.59
linux-headers-2.6.24-24-generic 2.6.24-24.59
linux-headers-2.6.24-24-386 2.6.24-24.59
linux-headers-2.6.24-24 2.6.24-24.59
linux-headers-2.6.24-25-xen 2.6.24-25.63
linux-headers-2.6.24-25-virtual 2.6.24-25.63
linux-headers-2.6.24-25-server 2.6.24-25.63
linux-headers-2.6.24-25-rt 2.6.24-25.63
linux-headers-2.6.24-25-openvz 2.6.24-25.63
linux-headers-2.6.24-25-generic 2.6.24-25.63
linux-headers-2.6.24-25-386 2.6.24-25.63
linux-headers-2.6.24-25 2.6.24-25.63
linux-headers-2.6.24-24-xen 2.6.24-24.61
linux-headers-2.6.24-24-virtual 2.6.24-24.61
linux-headers-2.6.24-24-server 2.6.24-24.61
linux-headers-2.6.24-24-rt 2.6.24-24.61
linux-headers-2.6.24-24-openvz 2.6.24-24.61
linux-headers-2.6.24-24-generic 2.6.24-24.61
linux-headers-2.6.24-24-386 2.6.24-24.61
linux-headers-2.6.24-24 2.6.24-24.61
linux-headers-2.6.24-23-xen 2.6.24-23.52
linux-headers-2.6.24-23-virtual 2.6.24-23.52
linux-headers-2.6.24-23-server 2.6.24-23.52
linux-headers-2.6.24-23-rt 2.6.24-23.52
linux-headers-2.6.24-23-openvz 2.6.24-23.52
linux-headers-2.6.24-23-generic 2.6.24-23.52
linux-headers-2.6.24-23-386 2.6.24-23.52
linux-headers-2.6.24-23 2.6.24-23.52
linux-headers-2.6.24-22-xen 2.6.24-22.45
linux-headers-2.6.24-22-virtual 2.6.24-22.45
linux-headers-2.6.24-22-server 2.6.24-22.45
linux-headers-2.6.24-22-rt 2.6.24-22.45
linux-headers-2.6.24-22-openvz 2.6.24-22.45
linux-headers-2.6.24-22-generic 2.6.24-22.45
linux-headers-2.6.24-22-386 2.6.24-22.45
linux-headers-2.6.24-22 2.6.24-22.45
linux-headers-2.6.24-21-xen 2.6.24-21.43
linux-headers-2.6.24-21-virtual 2.6.24-21.43
linux-headers-2.6.24-21-server 2.6.24-21.43
linux-headers-2.6.24-21-rt 2.6.24-21.43
linux-headers-2.6.24-21-openvz 2.6.24-21.43
linux-headers-2.6.24-21-generic 2.6.24-21.43
linux-headers-2.6.24-21-386 2.6.24-21.43
linux-headers-2.6.24-21 2.6.24-21.43
linux-headers-2.6.24-19-xen 2.6.24-19.41
linux-headers-2.6.24-19-virtual 2.6.24-19.41
linux-headers-2.6.24-19-server 2.6.24-19.41
linux-headers-2.6.24-19-rt 2.6.24-19.41
linux-headers-2.6.24-19-openvz 2.6.24-19.41
linux-headers-2.6.24-19-generic 2.6.24-19.41
linux-headers-2.6.24-19-386 2.6.24-19.41
linux-headers-2.6.24-19 2.6.24-19.41
linux-headers-2.6.24-18-xen 2.6.24-18.32
linux-headers-2.6.24-18-virtual 2.6.24-18.32
linux-headers-2.6.24-18-server 2.6.24-18.32
linux-headers-2.6.24-18-rt 2.6.24-18.32
linux-headers-2.6.24-18-openvz 2.6.24-18.32
linux-headers-2.6.24-18-generic 2.6.24-18.32
linux-headers-2.6.24-18-386 2.6.24-18.32
linux-headers-2.6.24-18 2.6.24-18.32
linux-headers-2.6.24-16-xen 2.6.24-16.30
linux-headers-2.6.24-16-virtual 2.6.24-16.30
linux-headers-2.6.24-16-server 2.6.24-16.30
linux-headers-2.6.24-16-rt 2.6.24-16.30
linux-headers-2.6.24-16-openvz 2.6.24-16.30
linux-headers-2.6.24-16-generic 2.6.24-16.30
linux-headers-2.6.24-16-386 2.6.24-16.30
linux-headers-2.6.24-16 2.6.24-16.30
vagelism@unknown:~$ apt-cache showpkg linux-linc-dev
W: Unable to locate package linux-linc-dev
vagelism@unknown:~$ apt-cache showpkg linux-libc-dev
Package: linux-libc-dev
Versions: 
2.6.24-25.63 (/var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages) (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages
                  MD5: f12d9ca47be5969cd90b3d685b72b0f5

2.6.24-16.30 (/var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages
                  MD5: f12d9ca47be5969cd90b3d685b72b0f5


Reverse Depends: 
  nvidia-new-kernel-source-envy,linux-libc-dev
  nvidia-legacy-kernel-source-envy,linux-libc-dev
  nvidia-kernel-source-envy,linux-libc-dev
  fglrx-kernel-source-envy,linux-libc-dev
  libc6-dev,linux-libc-dev
  librsbac-dev,linux-libc-dev
  libc6-dev,linux-libc-dev
Dependencies: 
2.6.24-25.63 - amd64-libs-dev (1 1.1) dvb-dev (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) linux-kernel-headers (0 (null)) dvb-dev (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) linux-kernel-headers (0 (null)) 
2.6.24-16.30 - amd64-libs-dev (1 1.1) dvb-dev (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) linux-kernel-headers (0 (null)) dvb-dev (3 1.0.1-6) libc6-dev (3 2.3.2.ds1-6) libc6.1-dev (3 2.3.2.ds1-6) linux-kernel-headers (0 (null)) 
Provides: 
2.6.24-25.63 - linux-kernel-headers 
2.6.24-16.30 - linux-kernel-headers 
Reverse Provides:

---

### Post by kansasnoob on 2009-11-23
Did you run the autoclean and clean commands? If so how much space did that free up?

Maybe post the output of:

```
df -H
```

again so I can see how much space we have freed up.

How about apt-get -f install, did it suggest running autoremove?

I can see you have a lot of kernels installed but you didn't post the output of:

```
uname -r
```

So I don't know what kernel you're currently running.

Also no mention of options for transferring data or the output of:

```
sudo fdisk -l
```

Is that a netbook? Maybe a eeepc?

You have to help us understand your setup before we can help you.

---

### Post by slakkie on 2009-11-23
can we get a du -sh /* perhaps?

I have the feeling his homedir is using up all the space.

---

### Post by kansasnoob on 2009-11-23
> **slakkie said:**
> can we get a du -sh /* perhaps?

I have the feeling his homedir is using up all the space.

I agree. I was hopeful that he could clean up just enough to get the OS usable and then transfer data to some appropriate location.

---

### Post by vagelism on 2009-11-23
> **kansasnoob said:**
> Did you run the autoclean and clean commands? If so how much space did that free up?

Maybe post the output of:

```
df -H
```

again so I can see how much space we have freed up.

How about apt-get -f install, did it suggest running autoremove?

I can see you have a lot of kernels installed but you didn't post the output of:

```
uname -r
```




So I don't know what kernel you're currently running.

Also no mention of options for transferring data or the output of:

```
sudo fdisk -l
```

Is that a netbook? Maybe a eeepc?

You have to help us understand your setup before we can help you.



It is an eee pc 900 with 16 gb ssd.
I did the commands...
nothing at all...

---

### Post by vagelism on 2009-11-23
> **slakkie said:**
> can we get a du -sh /* perhaps?

I have the feeling his homedir is using up all the space.





vagelism@unknown:~$ sudo du -sh /*
4.0K	/array-apt-key.asc
5.4M	/bin
25M	/boot
0	/cdrom
80K	/dev
36M	/eeesupport
24M	/etc
du: cannot access `/home/vagelism/.gvfs': Permission denied
1.3G	/home
4.0K	/initrd
0	/initrd.img
0	/initrd.img.old
160M	/lib
16K	/lost+found
15G	/media
4.0K	/mnt
59M	/opt
du: cannot access `/proc/6251/task/6251/fd/4': No such file or directory
du: cannot access `/proc/6251/task/6251/fdinfo/4': No such file or directory
du: cannot access `/proc/6251/fd/4': No such file or directory
du: cannot access `/proc/6251/fdinfo/4': No such file or directory
0	/proc
5.4M	/root
7.1M	/sbin
4.0K	/srv
0	/sys
60K	/tmp
2.9G	/usr
278M	/var
0	/vmlinuz
0	/vmlinuz.old
vagelism@unknown:~$

---

### Post by slakkie on 2009-11-24
Wow, you have some /media dir. Could you run:

du -sh /media/* 


Although I would advise you to remove some of the files there. 15Gb in use of 16Gb by that dir alone. You need/must remove some files from that dir. The du -sh command will tell you what size each file has.

---

### Post by vagelism on 2009-11-24
> **slakkie said:**
> Wow, you have some /media dir. Could you run:

du -sh /media/* 


Although I would advise you to remove some of the files there. 15Gb in use of 16Gb by that dir alone. You need/must remove some files from that dir. The du -sh command will tell you what size each file has.




vagelism@unknown:~$ sudo du -sh /media/*
[sudo] password for vagelism: 
0	/media/cdrom
4.0K	/media/cdrom0
8.1G	/media/disk
6.1G	/media/disk-1
0	/media/floppy
4.0K	/media/floppy0
vagelism@unknown:~$

---

### Post by slakkie on 2009-11-24
I think you should move /media/disk and /media/disk-1 to an external disk if you want to keep the files, otherwise remove them.

---

### Post by vagelism on 2009-11-24
> **slakkie said:**
> I think you should move /media/disk and /media/disk-1 to an external disk if you want to keep the files, otherwise remove them.


Thank you for your advice. I do not realy know what is in there?
I never puted something?
What can it be? Is it crucial for the operating system?
What may i lose if I delete them?
Again thank you in advance all for your assistance

---

### Post by vagelism on 2009-11-24
OK
I found it...
There ware backup files of the system...I normaly configured it to be on the external disk-1 . I do not know what happent and it was packing the backups there ....on media/disk
Now is clean and goes fine.
THANK YOU ALL FOR YOUR ASSISTANCE.

---

