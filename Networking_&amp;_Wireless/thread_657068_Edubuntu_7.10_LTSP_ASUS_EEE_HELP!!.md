---
title: "Edubuntu 7.10 LTSP ASUS EEE HELP!!"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by linxonline on 2008-01-03
Hello Guys,

Im trying to get the new Asus eee laptop to work with edubuntu on an ltsp boot. However everytime it boots up it finds dhcp get its IP settings then downloads the linux kernel. Then  you get the splash screen and the laptop hangs. I have looked at the error message just before it hangs and its something like this,

can't open /tmp/net-eth0.conf
Device doesn't exist.

I have found out that the network cards id is 0x1969 0x2048 and I have looked through the pci module list and its in there and it says it uses the atl2 module. However im not to sure if its actually using the atl2 module I'm just assuming that it is but its still not finding the network cards device settings?

Im also using kernel 2.6.22-14-386 

If anyone else has had this problem and found a way to resolve it i would be very grateful if they could help.

---

### Post by mor22 on 2008-01-04
try looking for eeexubuntu as they've done lots of work in getting ubuntu to work on the eee.  

[http://wiki.eeeuser.com/ubuntu:eeexubuntu:home](http://wiki.eeeuser.com/ubuntu:eeexubuntu:home)

I'm running it now and it works fine.

There are a few issues with the atl2 driver, you may have to download the lastest release to get it to work with the eee.

good luck!

---

### Post by linxonline on 2008-01-04
Thank you very much for you're help.

I have read the eeeXubuntu site and it seems that its just dealing with running ubuntu as a standalone machine and I'm trying to get it to work as a thin client but it made good reading and I'm still going to give it a try.

Do u know where I can track down the latest release of the alt2 driver though?

---

### Post by mor22 on 2008-01-06
Sorry i don't know. I suggest you try messaging the maintiner of the eeexubuntu livecd.  he must have got it from somewhere :)

you could also ask on the eeeuser forums 
[http://forum.eeeuser.com/](http://forum.eeeuser.com/)

---

### Post by linxonline on 2008-02-13
I still cant get it to load I still get the same error and iv compiled and recompiled every kernel and atl2 source there is. I'm starting to think I'm looking in the wrong place.

I NEED HELP!!

---

### Post by Lapinou on 2008-02-22
Hi all,

thanks to an indonesian web page (!) I managed to let my EEEpc boot as a thin client with Edubuntu 7.10. In fact, I didn't understand anything from what I read, but this saved my life since I did not find any other documentation !

So, the problem when trying to start the EEE is that the stock initrd included in ltsp with edubuntu 7.10 doesn't know the Atheros lan card.

Solving this problem is just a matter of including the good module (atl2.ko) in the initrd.

Open a shell in your edubuntu server, become root (sudo -s) then :

chroot /opt/ltsp/i386     ...     to start working "in" the ltsp tree.

vi /etc/initramfs-tools/modules     ...     and add at the end of the file the name of the module you want to add. In our case, you just need to add a line with "atl2", nothing more, nothing less.

update-initramfs -k 2.6.22-14-386 -c     ...     will create in /boot a file named initrd.img-2.6.22-14-386 after having renamed the previous one with .bak at the end. This new file contains the atl2 driver.

exit    ...     to leave the chrooted environment. From now on, we must consider that our newly created file is in /opt/ltsp/i386/boot.

We must place this new initrd file at the right place for the thin clients to download it at boot time, wich is /var/lib/tftpboot/ltsp/i386, after having renamed the existing one, for backup :

mv /var/lib/tftpboot/ltsp/i386/initrd.img-2.6.22-14-386 /var/lib/tftpboot/ltsp/i386/initrd.img-2.6.22-14-386.bak

cp /opt/ltsp/i386/boot/initrd.img-2.6.22-14-386 /var/lib/tftpboot/ltsp/i386/

At this point, your EEEpc should (must ?) be able to boot as a thin client with your edubuntu server ; at least mine is !

In case you are using edubuntu 7.04 : I have good reasons to think it doesn't contain the atl2 module (in fact I wasn't able to find it ...).

Hope this helps ! Hoplà !

---

### Post by Lapinou on 2008-02-22
Well, I must add one thing : after logout, the EEEpc is not able to completely shutdown ; it appears to have, but the little green led still shines. One must push the power button for 5 seconds to get it off.

Hoplà !

---

### Post by Lapinou on 2008-02-23
The indonesian webpage with the original information is [http://linux.or.id/node/2026](http://linux.or.id/node/2026) , thanks to the person who wrote it !

---

