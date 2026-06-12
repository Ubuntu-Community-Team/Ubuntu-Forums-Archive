---
title: "NVIDIA drivers not working after update"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by darknuts on 2011-08-26
A few weeks ago I made some routine updates and restarted my computer and ever since, I have been unable to load my NVIDIA drivers. My GUI runs fine and I have good resolution but my advanced compiz features are not working. Here what i tried so far:

```

bearcat@bearcat8f:~$ sudo apt-get install nvidia-current
[sudo] password for bearcat: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
13 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-33-generic (2.6.32-33.72) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-33-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-33-generic; however:
  Package linux-image-2.6.32-33-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.32.33.39); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux:
 linux depends on linux-image (= 2.6.32.33.39); however:
  Package linux-image is not configured yet.
dpkg: error processing linux (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46~lucid1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-21-generic (2.6.32-21.32) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-21-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-21-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-29-generic (2.6.32-29.58) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-29-generic /boot/vmlinuz-2.6.32-29-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-29-generic /boot/vmlinuz-2.6.32-29-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-29-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-30-generic (2.6.32-30.59) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-30-generic /boot/vmlinuz-2.6.32-30-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-30-generic /boot/vmlinuz-2.6.32-30-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-30-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-31-generic (2.6.32-31.61) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-32-generic (2.6.32-32.62) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-32-generic /boot/vmlinuz-2.6.32-32-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-32-generic /boot/vmlinuz-2.6.32-32-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-32-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-33-generic (2.6.32-33.72) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-33-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.38-10-generic (2.6.38-10.46~lucid1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.38-10-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-33-generic; however:
  Package linux-headers-2.6.32-33-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-33-generic
 linux-image-generic
 linux-image
 linux
 linux-image-2.6.38-10-generic
 linux-headers-2.6.32-21-generic
 linux-headers-2.6.32-29-generic
 linux-headers-2.6.32-30-generic
 linux-headers-2.6.32-31-generic
 linux-headers-2.6.32-32-generic
 linux-headers-2.6.32-33-generic
 linux-headers-2.6.38-10-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
bearcat@bearcat8f:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

bearcat@bearcat8f:~$ 


```

I restarted and I got a screen saying ubuntu is running in low graphics mode. I reconfigured the graphics settings and restarted and now I go straight into gnome but my compiz features are not working. Any attempt to load graphics drivers come back in error. Please help.

---

### Post by darknuts on 2011-08-26
Oh I forgot to mention, I'm running 10.4 LTS 64 bit.

---

### Post by darknuts on 2011-08-27
Ok, I'm fairly certain it was the new kernel i installed that cause this error so i tried to uninstall the new kernel and roll back to the old one but to no avail. My kernel still reads the same as before: 2.6.38-10-generic

I seems i have a bunch of old kernels on my computer. Maybe if i remove all of them and start over?

---

### Post by powerpleb on 2011-08-27
Yes, this happened to me too.

What I did was download the NVidia drivers from their site and install them ([http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)). Works fine now.

When installing:
You need to go back to the terminal (not in X windows) by pressing ALT-F1 and logging in
Then type in 'sudo service gdm stop'
Then you can run the script with sudo. Make sure it is executable before running it. Also make sure it reconfigures your Xorg config file.

---

### Post by darknuts on 2011-08-27
I wanted to avoid having to manually install drivers because every time the kernel is updated you have reinstall them. Its kind of a pain. But I'll do that if all else fails.

---

### Post by cbowman57 on 2011-08-27
Do you have an xorg.conf file in /etc/X11 ?

The Nvidia driver won't load if it doesn't exist.  To create it go to the terminal and  **sudo nvidia-xconfig**

---

### Post by realzippy on 2011-08-27
OP already did:
```
bearcat@bearcat8f:~$ sudo nvidia-xconfig
```

@OP
check current kernel

```
uname -a
```

and reinstall headers generic and image generic for your kernel.
..then reinstall nvidia-driver.

---

### Post by cbowman57 on 2011-08-27
Oh, he sure did, I missed that.

---

### Post by darknuts on 2011-08-28
> **realzippy said:**
> OP already did:
```
bearcat@bearcat8f:~$ sudo nvidia-xconfig
```@OP
check current kernel

```
uname -a
```and reinstall headers generic and image generic for your kernel.
..then reinstall nvidia-driver.

ok. so i reinstalled everything you told me too and I tried reinstalling the nvidia driver and here's what i got:

```

bearcat@bearcat8f:~$ sudo apt-get install nvidia-current
[sudo] password for bearcat: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
14 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-31-generic (2.6.32-31.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-31-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-33-generic (2.6.32-33.72) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-33-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46~lucid1) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-33-generic; however:
  Package linux-image-2.6.32-33-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.33.39); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.32-21-generic (2.6.32-21.32) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-21-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-21-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-29-generic (2.6.32-29.58) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-29-generic /boot/vmlinuz-2.6.32-29-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-29-generic /boot/vmlinuz-2.6.32-29-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-29-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-30-generic (2.6.32-30.59) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-30-generic /boot/vmlinuz-2.6.32-30-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-30-generic /boot/vmlinuz-2.6.32-30-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-30-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-31-generic (2.6.32-31.61) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-32-generic (2.6.32-32.62) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-32-generic /boot/vmlinuz-2.6.32-32-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-32-generic /boot/vmlinuz-2.6.32-32-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-32-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-33-generic (2.6.32-33.72) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-33-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.38-10-generic (2.6.38-10.46~lucid1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.38-10-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-33-generic; however:
  Package linux-headers-2.6.32-33-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up nvidia-current (195.36.24-0ubuntu1~10.04) ...
update-initramfs: deferring update (trigger activated)
Removing old nvidia-current-195.36.24 DKMS files...

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-31-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-31-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-30-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-30-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-29-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-29-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-33-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-33-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-32-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-21-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-21-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....(bad exit status: 1)

DKMS: uninstall Completed.

------------------------------
Deleting module version: 195.36.24
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-current-195.36.24 DKMS files...
Building only for 2.6.38-10-generic
Building for architecture x86_64
Building initial module for 2.6.38-10-generic

[COLOR=Red]Error! Bad return status for module build on kernel: 2.6.38-10-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/195.36.24/build/ for more information.[/COLOR]
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 linux-image-2.6.32-31-generic
 linux-image-2.6.32-33-generic
 linux-image-2.6.38-10-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.32-21-generic
 linux-headers-2.6.32-29-generic
 linux-headers-2.6.32-30-generic
 linux-headers-2.6.32-31-generic
 linux-headers-2.6.32-32-generic
 linux-headers-2.6.32-33-generic
 linux-headers-2.6.38-10-generic
 linux-headers-generic
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)
bearcat@bearcat8f:~$ 


```Is there anyway to just roll back to the old kernel? Every time I try through the package manager it fails...

---

### Post by realzippy on 2011-08-28
Something seems to be messed up.pretty.

Run

```
sudo apt-get update
```

errors?If non,then run:

```
sudo apt-get upgrade
```

and please show :

```
uname -a
```

---

### Post by darknuts on 2011-08-28
Thanks for the quick reply zippy. Here's what I got:

```

bearcat@bearcat8f:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  flashplugin-installer
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
Need to get 20.5kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse flashplugin-installer 10.3.183.7ubuntu0.10.04.1 [20.5kB]
Fetched 20.5kB in 1s (13.2kB/s)                
Preconfiguring packages ...
(Reading database ... 344815 files and directories currently installed.)
Preparing to replace flashplugin-installer 10.3.183.4ubuntu0.10.04.1 (using .../flashplugin-installer_10.3.183.7ubuntu0.10.04.1_amd64.deb) ...
Unpacking replacement flashplugin-installer ...
Setting up linux-image-2.6.32-31-generic (2.6.32-31.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-31-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-33-generic (2.6.32-33.72) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-33-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46~lucid1) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-33-generic; however:
  Package linux-image-2.6.32-33-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.33.39); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.32-21-generic (2.6.32-21.32) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-21-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-21-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-29-generic (2.6.32-29.58) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-29-generic /boot/vmlinuz-2.6.32-29-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-29-generic /boot/vmlinuz-2.6.32-29-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-29-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-30-generic (2.6.32-30.59) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-30-generic /boot/vmlinuz-2.6.32-30-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-30-generic /boot/vmlinuz-2.6.32-30-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-30-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-31-generic (2.6.32-31.61) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-32-generic (2.6.32-32.62) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-32-generic /boot/vmlinuz-2.6.32-32-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-32-generic /boot/vmlinuz-2.6.32-32-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-32-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.32-33-generic (2.6.32-33.72) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-33-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.38-10-generic (2.6.38-10.46~lucid1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.38-10-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-33-generic; however:
  Package linux-headers-2.6.32-33-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-current (195.36.24-0ubuntu1~10.04) ...
No apport report written because MaxReports is reached already
                                                              update-initramfs: deferring update (trigger activated)
Removing old nvidia-current-195.36.24 DKMS files...

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-31-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-31-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-30-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-30-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-29-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-29-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-33-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-33-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-32-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....(bad exit status: 1)

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-21-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-21-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....(bad exit status: 1)

DKMS: uninstall Completed.

------------------------------
Deleting module version: 195.36.24
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-current-195.36.24 DKMS files...
Building only for 2.6.38-10-generic
Building for architecture x86_64
Building initial module for 2.6.38-10-generic

Error! Bad return status for module build on kernel: 2.6.38-10-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/195.36.24/build/ for more information.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              Setting up flashplugin-installer (10.3.183.7ubuntu0.10.04.1) ...
Downloading...
--2011-08-29 03:35:23--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.3.183.7.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5433328 (5.2M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.3.183.7.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  0% 41.1K 2m8s
    50K .......... .......... .......... .......... ..........  1% 82.3K 95s
   100K .......... .......... .......... .......... ..........  2%  164K 73s
   150K .......... .......... .......... .......... ..........  3%  165K 62s
   200K .......... .......... .......... .......... ..........  4%  164K 55s
   250K .......... .......... .......... .......... ..........  5% 1.34M 46s
   300K .......... .......... .......... .......... ..........  6%  186K 43s
   350K .......... .......... .......... .......... ..........  7%  165K 41s
   400K .......... .......... .......... .......... ..........  8%  164K 39s
   450K .......... .......... .......... .......... ..........  9%  164K 38s
   500K .......... .......... .......... .......... .......... 10% 1.43M 34s
   550K .......... .......... .......... .......... .......... 11%  185K 33s
   600K .......... .......... .......... .......... .......... 12%  165K 33s
   650K .......... .......... .......... .......... .......... 13%  164K 32s
   700K .......... .......... .......... .......... .......... 14%  165K 31s
   750K .......... .......... .......... .......... .......... 15% 1.46M 29s
   800K .......... .......... .......... .......... .......... 16%  184K 29s
   850K .......... .......... .......... .......... .......... 16%  165K 28s
   900K .......... .......... .......... .......... .......... 17%  165K 28s
   950K .......... .......... .......... .......... .......... 18%  165K 28s
  1000K .......... .......... .......... .......... .......... 19% 20.0M 26s
  1050K .......... .......... .......... .......... .......... 20%  165K 26s
  1100K .......... .......... .......... .......... .......... 21%  164K 25s
  1150K .......... .......... .......... .......... .......... 22%  165K 25s
  1200K .......... .......... .......... .......... .......... 23% 1.41M 24s
  1250K .......... .......... .......... .......... .......... 24%  184K 23s
  1300K .......... .......... .......... .......... .......... 25%  165K 23s
  1350K .......... .......... .......... .......... .......... 26%  164K 23s
  1400K .......... .......... .......... .......... .......... 27%  166K 23s
  1450K .......... .......... .......... .......... .......... 28% 1.48M 22s
  1500K .......... .......... .......... .......... .......... 29%  183K 21s
  1550K .......... .......... .......... .......... .......... 30%  164K 21s
  1600K .......... .......... .......... .......... .......... 31%  165K 21s
  1650K .......... .......... .......... .......... .......... 32%  166K 21s
  1700K .......... .......... .......... .......... .......... 32% 1.51M 20s
  1750K .......... .......... .......... .......... .......... 33%  182K 20s
  1800K .......... .......... .......... .......... .......... 34%  165K 19s
  1850K .......... .......... .......... .......... .......... 35%  165K 19s
  1900K .......... .......... .......... .......... .......... 36%  166K 19s
  1950K .......... .......... .......... .......... .......... 37% 9.41M 18s
  2000K .......... .......... .......... .......... .......... 38%  165K 18s
  2050K .......... .......... .......... .......... .......... 39%  165K 18s
  2100K .......... .......... .......... .......... .......... 40%  166K 17s
  2150K .......... .......... .......... .......... .......... 41%  485K 17s
  2200K .......... .......... .......... .......... .......... 42%  245K 17s
  2250K .......... .......... .......... .......... .......... 43%  165K 16s
  2300K .......... .......... .......... .......... .......... 44%  165K 16s
  2350K .......... .......... .......... .......... .......... 45%  165K 16s
  2400K .......... .......... .......... .......... .......... 46% 1.57M 15s
  2450K .......... .......... .......... .......... .......... 47%  180K 15s
  2500K .......... .......... .......... .......... .......... 48%  165K 15s
  2550K .......... .......... .......... .......... .......... 49%  165K 15s
  2600K .......... .......... .......... .......... .......... 49%  166K 14s
  2650K .......... .......... .......... .......... .......... 50% 1.61M 14s
  2700K .......... .......... .......... .......... .......... 51%  179K 14s
  2750K .......... .......... .......... .......... .......... 52%  166K 13s
  2800K .......... .......... .......... .......... .......... 53%  165K 13s
  2850K .......... .......... .......... .......... .......... 54%  167K 13s
  2900K .......... .......... .......... .......... .......... 55% 6.48M 12s
  2950K .......... .......... .......... .......... .......... 56%  165K 12s
  3000K .......... .......... .......... .......... .......... 57%  165K 12s
  3050K .......... .......... .......... .......... .......... 58%  165K 12s
  3100K .......... .......... .......... .......... .......... 59% 1.52M 11s
  3150K .......... .......... .......... .......... .......... 60%  181K 11s
  3200K .......... .......... .......... .......... .......... 61%  165K 11s
  3250K .......... .......... .......... .......... .......... 62%  165K 11s
  3300K .......... .......... .......... .......... .......... 63%  166K 10s
  3350K .......... .......... .......... .......... .......... 64% 1.51M 10s
  3400K .......... .......... .......... .......... .......... 65%  180K 10s
  3450K .......... .......... .......... .......... .......... 65%  165K 9s
  3500K .......... .......... .......... .......... .......... 66%  165K 9s
  3550K .......... .......... .......... .......... .......... 67%  167K 9s
  3600K .......... .......... .......... .......... .......... 68% 1.50M 9s
  3650K .......... .......... .......... .......... .......... 69%  180K 8s
  3700K .......... .......... .......... .......... .......... 70%  165K 8s
  3750K .......... .......... .......... .......... .......... 71%  165K 8s
  3800K .......... .......... .......... .......... .......... 72%  167K 8s
  3850K .......... .......... .......... .......... .......... 73% 5.41M 7s
  3900K .......... .......... .......... .......... .......... 74%  166K 7s
  3950K .......... .......... .......... .......... .......... 75%  165K 7s
  4000K .......... .......... .......... .......... .......... 76%  166K 7s
  4050K .......... .......... .......... .......... .......... 77% 1.50M 6s
  4100K .......... .......... .......... .......... .......... 78%  181K 6s
  4150K .......... .......... .......... .......... .......... 79%  165K 6s
  4200K .......... .......... .......... .......... .......... 80%  165K 5s
  4250K .......... .......... .......... .......... .......... 81%  166K 5s
  4300K .......... .......... .......... .......... .......... 81% 1.46M 5s
  4350K .......... .......... .......... .......... .......... 82%  181K 5s
  4400K .......... .......... .......... .......... .......... 83%  165K 4s
  4450K .......... .......... .......... .......... .......... 84%  166K 4s
  4500K .......... .......... .......... .......... .......... 85%  167K 4s
  4550K .......... .......... .......... .......... .......... 86% 1.49M 4s
  4600K .......... .......... .......... .......... .......... 87%  180K 3s
  4650K .......... .......... .......... .......... .......... 88%  165K 3s
  4700K .......... .......... .......... .......... .......... 89%  166K 3s
  4750K .......... .......... .......... .......... .......... 90%  167K 3s
  4800K .......... .......... .......... .......... .......... 91% 1.43M 2s
  4850K .......... .......... .......... .......... .......... 92%  180K 2s
  4900K .......... .......... .......... .......... .......... 93%  165K 2s
  4950K .......... .......... .......... .......... .......... 94%  166K 2s
  5000K .......... .......... .......... .......... .......... 95% 1.43M 1s
  5050K .......... .......... .......... .......... .......... 96%  181K 1s
  5100K .......... .......... .......... .......... .......... 97%  166K 1s
  5150K .......... .......... .......... .......... .......... 98%  165K 1s
  5200K .......... .......... .......... .......... .......... 98%  167K 0s
  5250K .......... .......... .......... .......... .......... 99% 1.41M 0s
  5300K .....                                                 100% 40.5K=27s

2011-08-29 03:35:51 (197 KB/s) - `./adobe-flashplugin_10.3.183.7.orig.tar.gz' saved [5433328/5433328]

Download done.
Flash Plugin installed.

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 linux-image-2.6.32-31-generic
 linux-image-2.6.32-33-generic
 linux-image-2.6.38-10-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.32-21-generic
 linux-headers-2.6.32-29-generic
 linux-headers-2.6.32-30-generic
 linux-headers-2.6.32-31-generic
 linux-headers-2.6.32-32-generic
 linux-headers-2.6.32-33-generic
 linux-headers-2.6.38-10-generic
 linux-headers-generic
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)
bearcat@bearcat8f:~$ uname -a
Linux bearcat8f 2.6.38-10-generic #46~lucid1-Ubuntu SMP Wed Jul 6 18:41:04 UTC 2011 x86_64 GNU/Linux
bearcat@bearcat8f:~$ 


```


I think the problem is that the new Kernel 2.6.38-10-generic is not compatible with my graphics card. Can you tell me how to roll back? I keep trying but to no avail. Anyway, its getting late. I have to go to bed. I'll for your reply in the morning.

---

### Post by realzippy on 2011-08-28
You seem to have a dpkg/apt problem.
Have you run those common commands eg:

```
sudo dpkg --configure -a
sudo apt-get -f install
```

then again 

```
sudo apt-get update

```

Booted to an older kernel?

---

### Post by darknuts on 2011-08-31
I tried the force install and got the same error messages. The dpkg error was there for a long time so it may not have anything to do with the drivers. I am convinced that this kernel simply does not support my drivers. I need to know how to boot to an older kernel. Can you tell me?

---

### Post by realzippy on 2011-08-31
You already should have a choice when grub screen appears?

If it does not come up for strange reasons:
press "shift" when booting.

The kernel seems not being configured correctly **due** to your dpkg error.
So the graphics driver fails,as it "needs" the kernel...

---

### Post by darknuts on 2011-09-02
I was able to roll back to the previous kernel and my drivers are installed. Thanks for your help zippy!

---

### Post by InHisName on 2011-09-15
> **realzippy said:**
> Something seems to be messed up.pretty.

Run

```
sudo apt-get update
```

errors?If non,then run:

```
sudo apt-get upgrade
```

and please show :

```
uname -a
```

I was having difficulty in building header-kernel for /etc/init.d/vboxdrv setup    it kept failing the check with modprobe.

I had note: depmod....(bad exit status: 1)   in my /var/log/vbox-install.log file

Running the above fixed what ever was bothering my machine also.  Now its running fine.

---

