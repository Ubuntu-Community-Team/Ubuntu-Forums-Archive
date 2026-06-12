---
title: "Q: How to re-purpose a computer to be a  N.A.S Device using ubuntu"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by Brolyfanatic777 on 2011-04-29
Hello All! I am relatively new to Ubuntu, updated to 11.04 just  yesterday. It's nice and snappy.  I have a couple of computers that, if  possible, I would like to re-purpose as NAS devices using Ubuntu.  Complete with a web interface and everything. My problem  is................. I know not how!!!!!!! lol that is why I am here!!  but of course you knew that just by reading the title of this part of  the forum. Anyways, I could use a good reliable point in the right  direction, a good tutorial perhaps? I would like to get started asap.  I've looked into two ways already, one was mediatome. Configuring it was  a real pain and it wasn't quite what I was looking for. two was of  course freeNAS. I couldn't even get off the ground with this one as none  of the chipsets in the machines I want to use are supported. Then I  heard that it is possible to do this on ubuntu relatively easily by  getting some additional packages from the Ubuntu software center. 

Here are the specs of one of the computers I want to re-purpose:

Sony Vaio VGN-NR160E:

CPU: Intel core 2 duo @ 1.5GHZ
GPU: Intel GM 965 Express chipset
RAM: 1GB
HDD: 160GB Hitachi something-or-other
Ports: 4 USB 2.0 ports; 1 firewire port; some kind of express card slot; vga port


Many thanks for visiting my little thread here!!

Regards

Jim

---

### Post by madjr on 2011-04-29
i think this might help:

[http://askubuntu.com/questions/1266/how-to-set-up-ubuntu-server-as-a-nas](http://askubuntu.com/questions/1266/how-to-set-up-ubuntu-server-as-a-nas)

[http://www.sohoadvisers.com/tutorials/ubuntu-linux/create-a-nas-using-ubuntu-linux](http://www.sohoadvisers.com/tutorials/ubuntu-linux/create-a-nas-using-ubuntu-linux)

[http://ubuntuforums.org/showthread.php?t=980224](http://ubuntuforums.org/showthread.php?t=980224)

---

### Post by lkraemer on 2011-04-29
Looking for a NAS and possibly a print server.........Look at FREENAS....
WONDERFUL......And you can make it Embedded running it from a Compact Flash card.

**NAS:**
[http://freenas.org/FreeNAS](http://freenas.org/FreeNAS)

**Documentation & User Guide:**
[http://freenas.org/documentation:setup_and_user_guide](http://freenas.org/documentation:setup_and_user_guide)

**FAQ:**
[http://freenas.org/documentation:faq](http://freenas.org/documentation:faq)

**FORUM:**
[http://sourceforge.net/apps/phpbb/freenas/index.php](http://sourceforge.net/apps/phpbb/freenas/index.php)

**PRINTSERVER:**
[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=13&t=2116](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=13&t=2116)

**Embedded FreeNAS w/IDE Adapter & CF:**
[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=7493&p=36592&hilit=Compact#p36592](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=7493&p=36592&hilit=Compact#p36592)

**Install Embedded wo/CDROM to CF w/Linux & gparted:**
[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=7317&p=35555&hilit=Compact#p35555](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=7317&p=35555&hilit=Compact#p35555)

**FreeNAS Print Server Setup Guide:**
[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=13&t=2116&p=35692&hilit=Compact#p35692](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=13&t=2116&p=35692&hilit=Compact#p35692)

**Setup Ubuntu to use the FreeNAS Print Server:**
[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=7413&p=36216&hilit=Compact#p36216](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=94&t=7413&p=36216&hilit=Compact#p36216)

Enjoy!

lk

---

### Post by Brolyfanatic777 on 2011-04-30
@madjr I decided to use your link to the tutorial at [www.sohoadvisers.com](www.sohoadvisers.com), I'm at a bit of a road block. I've got samba, $wget, and webmin installed but every time I request the needed key it gives me a "404 not found" the key url: [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc)

what should I do to get around this and finish set-up?

---

### Post by madjr on 2011-04-30
> **Brolyfanatic777 said:**
> @madjr I decided to use your link to the tutorial at [www.sohoadvisers.com](www.sohoadvisers.com), I'm at a bit of a road block. I've got samba, $wget, and webmin installed but every time I request the needed key it gives me a "404 not found" the key url: [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc)

what should I do to get around this and finish set-up?

sorry i haven't setup a nas server in a long time and it was with a different tutorial that i couldnt find, so i would be almost as lost as you are.

check out the askubuntu link.

if you keep running into problems, you can ask there also.

---

### Post by crispy_420 on 2011-04-30
I also vote for FreeNAS. It is not Ubuntu as you requested but it will get you up and running in minutes. The network servers are present and ready to go, they just need to be turned on. If you have a PS3, it will even act as a UPnP media streaming server.

---

### Post by Brolyfanatic777 on 2011-05-01
ok, here's an update on my progress. I've got samba installed, did so without a hitch, when I go to its webpage it asks me for a password, I've got a program to configure samba but when I add users or do anything with it for that matter it doesn't seem to do anything. I believe all a I need to do now is add users and shares. How do I do this?

---

### Post by madjr on 2011-05-01
> **Brolyfanatic777 said:**
> ok, here's an update on my progress. I've got samba installed, did so without a hitch, when I go to its webpage it asks me for a password, I've got a program to configure samba but when I add users or do anything with it for that matter it doesn't seem to do anything. I believe all a I need to do now is add users and shares. How do I do this?

you might find what you need here:

[http://www.unixmen.com/component/tag/samba](http://www.unixmen.com/component/tag/samba)

---

