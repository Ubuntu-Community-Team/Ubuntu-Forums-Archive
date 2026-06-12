---
title: "No ethernet frustrations"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Stella123 on 2010-03-01
working on setting up a new netbook to run Ubuntu. laptop has broadcom netlink bcm57780 etherlink pci controller built in. (confirmed using lspci).

ifconfig shows no eth0 or eth1. I tried /etc/init.d/networking start and neither come up. i also try ifconfig eth0 up and ifconfig eth1 up and also don't work-- no such device.

so i figure i didnt have the right driver. go to broadcom, find the driver, package comes back with an rpm package i download. after a while i figure out rpm doesnt work on debian so i run alien to convert the rpm. so i run "sudo alien -k tg3-3.99k-1.src.rpm" and when i do that i get some errors-- 

"dpkg-gencontrol: error: current host architecture 'i386' does not appear in package's architecture list (amd64)
dh_gencontrol:  command returned error code 65280
make: *** [binary-arch] Error 1
find: 'tg3-3.99k': No such file or directory"

now I am at a bit of a loss for moving this forward. i am very new to linux/ubuntu and have been googling my heart out to find this, but i just can't seem to work this one out.  I wish drivers could be installed using the synaptic package manager.

would really appreciate some sage advice on what to try next.

---

### Post by Peter09 on 2010-03-01
Think this link contains the solution:
 
> [http://help.lockergnome.com/linux/Bug-553024-linux-image-30-amd64-tg3-module-work-broadcom-mod--ftopict508628.html](http://help.lockergnome.com/linux/Bug-553024-linux-image-30-amd64-tg3-module-work-broadcom-mod--ftopict508628.html)
 
Does not look elegant.

---

### Post by Stella123 on 2010-03-01
No elegant indeed.  Ok, so reading it through, its just this chunk that i needed to do

[INDENT]The workaround is to do this: 
 add tg3 to /etc/modprobe.d/blacklist 
 run update-initramfs to copy that into the initramfs to prevent early 
 loading of tg3. 
 Add tg3 to /etc/modules so it gets explicitly loaded later 
 Add /etc/modprobe.d/tg3.conf containing: 
 install tg3 /sbin/modprobe broadcom; /sbin/modprobe --ignore-install tg3
[/INDENT]
So being somewhat new to all of this, I did the following:
1.  add a line at the end of the blacklist file that says "blacklist tg3"
2. run update-initramfd -u (since apparently it needed an option.  didnt have any issues reported back.
3. opened /etc/modules and added in "tg3" in the loop bit-- before the final lp.
4. created the tg3.conf file using kate and added in that install line and saved it.
5. rebooted.

I did all that and no dice.  may be user error-- this is all very new to me.

am i missing something still?  ifconfig still shows no eth0 or eth1 and networking start shows both as no such device.

this is quite a crash course for a newbie!

---

### Post by Stella123 on 2010-03-01
ok, i am wrong-- something has changed.  boot process now displays the following error:  "tg3: problem fetching invariants of chip, aborting"

so i guess that means its trying to load now, which is good.  now i just need to figure that next chunk out.

---

