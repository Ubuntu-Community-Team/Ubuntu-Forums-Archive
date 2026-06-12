---
title: "tally erp9 does not work under wine"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-07-12
HI!
I am using ubuntu 10.04 and have wine installed in it.
I tried to run tally 7.2 through wine and it worked, but later when I tried to run the latest version of tally i.e. tally erp9, it does not worked. A message is flagged somewhat like this..."Tally erp9 has encountered a serious problem and needs to be closed."

Tell me please if I can run Tally erp9 under wine or not...

Thanks!!

---

### Post by diablo75 on 2010-07-12
According to the Wine application database, it doesn't look good:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18517](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18517)

It lists "Silver" but it's an old result that was probably done on an outdated version of Tally, which doesn't run as well on Wine as it used it.  So for the time being... it doesn't look like there are any tricks you can use to get the software to work.

The best alternative would be to install Windows in a virtual machine and run Tally on top of that until Wine is one day able to run this software.

In a perfect world, Tallysolutions would offer a Linux version of their software, but for now we'll just have to wait.  Perhaps even complain a little, but we'll still have to wait.

---

### Post by amityadav9314 on 2010-07-12
hey thanks for the information.
i downloaded oracle vm virtual box(latest) as a .deb package and tried to install, but error occured.
when i tried to run "sudo apt-get -f install", then the following error is coming.....


"amit@ubuntu:~$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-23-generic (2.6.32-23.37) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
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
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-23-generic; however:
  Package linux-image-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.23.24); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.32-23-generic (2.6.32-23.37) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-23-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-23-generic; however:
  Package linux-headers-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 linux-image-2.6.32-23-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.32-23-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
amit@ubuntu:~$ 
""



tell me what to do..

---

### Post by diablo75 on 2010-07-12
Open a terminal windows and paste in:

```
sudo dpkg --configure -a
```

Then press Enter.  Try to install the deb package next by double-clicking on it.

---

### Post by amityadav9314 on 2010-07-12
I have done that but again the following error is displayed...




amit@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for amit: 
Setting up linux-headers-2.6.32-23-generic (2.6.32-23.37) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-23-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-23-generic (2.6.32-23.37) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
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
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-23-generic; however:
  Package linux-image-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.23.24); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-23-generic; however:
  Package linux-headers-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.32-23-generic
 linux-image-2.6.32-23-generic
 linux-image-generic
 linux-generic
 linux-headers-generic
amit@ubuntu:~$ 





now tell me what i should do?

---

### Post by amityadav9314 on 2010-07-12
but after doing this my virtual box is installed

---

