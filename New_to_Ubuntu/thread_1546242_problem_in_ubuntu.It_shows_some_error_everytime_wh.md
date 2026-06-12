---
title: "problem in ubuntu.It shows some error everytime while installin' something"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-08-05
hi
recently i have updated my system, but after that some errors were encountered.When i tried the command..."sudo apt-get -f install"..
the folloein were the error that my terminal was showing....
.
.
.

amit@ubuntu:~$ sudo apt-get -f install
[sudo] password for amit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-23-generic (2.6.32-23.37) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
This kernel does not seem to support TuxOnIce user interface, skipping...
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found Windows 7 (loader) on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: failed to exec /etc/kernel/postinst.d/dkms: Exec format error
run-parts: /etc/kernel/postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-23-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-24-generic (2.6.32-24.39) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
This kernel does not seem to support TuxOnIce user interface, skipping...
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found Windows 7 (loader) on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: failed to exec /etc/kernel/postinst.d/dkms: Exec format error
run-parts: /etc/kernel/postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-24-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.24.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.32-23-generic (2.6.32-23.37) ...
No apport report written because the error message indicates its a followup error from a previous failure.
              No apport report written because MaxReports is reached already
                                                                            Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-23-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.32-24-generic (2.6.32-24.39) ...
No apport report written because MaxReports is reached already
                                                              Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-24-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-24-generic; however:
  Package linux-headers-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                Errors were encountered while processing:
 linux-image-2.6.32-23-generic
 linux-image-2.6.32-24-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.32-23-generic
 linux-headers-2.6.32-24-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
amit@ubuntu:~$ 
;
;
;
;
what does this all mean?

---

### Post by Neobuntu on 2010-08-05
I think it means it could not finish because of dependency problems.

Maybe the dependencies were in transition, and will soon be fixed, upon the next upgrade. 

That's just my guess. Any further details would be the playground of the updater's.

All I can say to them, is try not to pull the foundation out from under the house while you're painting it. :)

---

