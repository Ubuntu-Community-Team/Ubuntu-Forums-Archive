---
title: "LAN, Graphics Cards 2D and 3D acceleration, Sound, Flash Player won't work"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by auroraa9420 on 2010-10-23
Since i upgraded to Maverick nothing works from above...

i cant scan the PC connected to my router and i cant transfere software or even play some simple games on wine (LAN)

Speaking of Wine, my ATI Radeon 5830 card wont give no acceleration nether compiz effects, + wine wont even run some simple windows program (not games), can any one tell me how to install the drivers for this card here...Yes i know...the catalyst driver 10.10 came out and i should try it, im not shure...is it stable and will it work :P

SOUND...after 2-3 reboots from maverick i lost my sound...cant listen to music because it runs very fast...that includes watching videos...

speaking of videos...ever since i installed Maverick firefox cant recognize the flash player, iv tryed to download the new version from adobe, Sympathic, even software center and still no result

PS: Im not ready to reinstall ubuntu because i have a lot of files and i dont have anywere to make a backup :S

---

### Post by Perfect Storm on 2010-10-23
That does sound like an upgrade that completely messed up. When so many things went wrong it is recommendable to make a fresh install. Do you have access to Ubuntu One? You get 2 GB free storage to backup.
Also do you have seperate /home partition?

---

### Post by auroraa9420 on 2010-10-23
> **Artificial Intelligence said:**
> That does sound like an upgrade that completely messed up. When so many things went wrong it is recommendable to make a fresh install. Do you have access to Ubuntu One? You get 2 GB free storage to backup.
Also do you have seperate /home partition?

yes i have both but i dont know how to use this "Ubuntu One", can you help me :)

---

### Post by Perfect Storm on 2010-10-23
There's diffrent ways, but if your /home partitions a seperated you can just reinstall the system and make sure you do not reformat your home partition. But set it up to use it instead.

For Ubuntu One, make sure you have an account:
[img]http://www.imageviper.com/displayimage/158880/0/1.png[/img]

[IMG]http://www.imageviper.com/displayimage/158881/0/2.png[/IMG]

You can sycronizing the Document folder

[IMG]http://www.imageviper.com/displayimage/158882/0/3.png[/IMG]


Or upload the files via ubuntu one homepage

---

### Post by auroraa9420 on 2010-10-23
> **Artificial Intelligence said:**
> There's diffrent ways, but if your /home partitions a seperated you can just reinstall the system and make sure you do not reformat your home partition. But set it up to use it instead.

For Ubuntu One, make sure you have an account:
[IMG]http://www.imageviper.com/displayimage/158880/0/1.png[/IMG]

[IMG]http://www.imageviper.com/displayimage/158881/0/2.png[/IMG]

You can sycronizing the Document folder

[IMG]http://www.imageviper.com/displayimage/158882/0/3.png[/IMG]


Or upload the files via ubuntu one homepage

too bad :O

my home partition isn't separated but i will keep in mind that the next time i install a linux system to make it all into a separate home partition :P

what to do if all of my files are on 1 partition :S

---

### Post by Perfect Storm on 2010-10-23
If all your stuff is on 1 partition of its own, you can re-install ubuntu. Just make sure you don't reformat that partition.

---

### Post by auroraa9420 on 2010-10-23
> **Artificial Intelligence said:**
> If all your stuff is on 1 partition of its own, you can re-install ubuntu. Just make sure you don't reformat that partition.

how is this posible :S

---

### Post by Perfect Storm on 2010-10-23
Are you sure you know what partition is?

When you installed Ubuntu you had the options to automatically letting Ubuntu set the partitions up or do it manually. By doing so you split your HDD into "Zones".

Here's how mine looks like

/boot
/swap
/ (root - where the system is installed)
/home (all users information and stuff are stored)
/storage (extra backup - I manually made this)
/multimedia (manually made this to keep them seperated)

When re-installing the system will be installed on / (root) partition, but I can tell it to keep and use the /home. So all my stuff is still there.

---

