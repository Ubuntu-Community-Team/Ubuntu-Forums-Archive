---
title: "Dell Mini 10"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by beeguy on 2010-06-10
I have ubuntu on my old dell desktop and have been using it for over a year now. It's wonderful. I now am looking into getting a netbook to use and wondered if anyone has any advice about the Dell Mini 10 (1010). Since I'm still not real granular with ubuntu now - rely on my son for some things with it - I wanted a netbook where all of its features would reliably work with ubuntu and the Dell has it preinstalled. I just downloaded the free pocket guide to ubuntu offered by this site and I'm committed to learning more about it. Is this a good choice for a netbook for someone like me? Thanks for any insight and advice.

---

### Post by snowpine on 2010-06-10
Be aware that the Dell netbooks with Ubuntu pre-installed do not use "regular" Ubuntu. They use an outdated and somewhat strange "Ubuntu Dell Remix." The first thing I did when I received my Dell Mini 9 netbook was to replace this "Dellbuntu" with the current release.

I would avoid any netbook using the Intel GMA500 "Poulsbo" graphic card. This card is not well-supported by current Linux distros. 

Also, Dell netbooks typically use Broadcom wireless cards. These do not work "out of the box" but are easy to fix: [http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

Other than those concerns, Dell makes great products. I have 3. :)

ps if you are looking for a netbook with the *current* Ubuntu release factory pre-installed, I have heard good things about system76.com

---

### Post by sb5551 on 2010-06-10
I have the Dell Mini 1010. I also upgraded the ram on it to 2 gb, but thats a whole other monster. I never really played around with the ubuntu version that came with it. I automatically upgraded to the netbook version 10.04 that just came out. Everything worked fine for me. I had a small problem where the wireless wouldn't work, but I just reloaded OS and everything worked great.

---

### Post by mikewhatever on 2010-06-10
A direct link to the model you have in mind would have been nice. There are several models all commonly related to and mini 10, and, as snowpine mentioned above, should be avoided. A quick look on Dell-USA shows the only mini 10 available with Ubuntu is the new model with N450 CPU and gma3150, which is ok. Unfortunately it is bundled with an experimental release of Ubuntu Moblin Remix rather then the standard netbook one.
[http://configure.us.dell.com/dellstore/config.aspx?oc=dndoan1&c=us&l=en&s=dhs&cs=19](http://configure.us.dell.com/dellstore/config.aspx?oc=dndoan1&c=us&l=en&s=dhs&cs=19)

---

### Post by Citadel1980 on 2010-06-10
I had a Dell Mini 1010 with Intel GMA 500 graphics, 1GB RAM, 160GB hard drive and the HD screen. It had WinXP on but I installed the Dell version of 9.04 that is on Dell's website.

I had to use the guide from this forum to tweak the GMA 500 graphics: [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

This forum thread has now been extended to try and tweak the GMA 500 for 10.04 but it still is only a partial solution to the problem.

My Mini 1010 worked ok with Ubuntu 9.04/9.10 but worked better with XP. Make sure the Dell Mini 1010 you have does not have the GMA 500 or else you are in for a lot of tweaking to get it to work at an acceptable level.

If the Mini 1010 doesn't have a GMA 500 you should be OK.

Stay away from anything with a GMA 500. The work put into trying to get it to work just isn't worth all the effort.

If you have a Mini 1010 with the GMA 500 you may want to look at Jolicloud. They use an older kernel and have supposedly tweaked it to use the GMA 500. When I tried Jolicloud in April I had limited success and returned to my tweaked Ubuntu 9.04.

Just my two cents worth.

---

### Post by mnoyes on 2010-06-12
> **sb5551 said:**
> I have the Dell Mini 1010. I automatically upgraded to the netbook version 10.04 that just came out. ...

How did you upgrade? I have been having trouble figuring this out on my Mini 1010 with Dell-installed 8.0.4LTS lpia -- I can't upgrade using update manager, nor from the command line. I also can't boot from a USB stick (can't change BIOS boot order -- USB stick doesn't show up as an option)...

What did you do?:confused:

---

### Post by wirah on 2010-06-14
Just to let you know I've been using Ubuntu 9.10 Netbook Remix for a long time now, with a Dell Mini 1010, GMA500.

I upgraded from 9.04 and used lucazade's video driver script to install the GMA500 drivers. Nothing more complex than that.

If you look at the thread above, they seem to have something quite nice working on 10.04 now too, I am just reading through the thread to figure out what!

---

### Post by anewguy on 2010-06-14
I haven't backed up the hard drive yet (gasp!), so I've only tried it from a USB flash drive, and I have an Acer Aspire One not the Dell, but I have to tell you I kinda like the different flavor that the netbook remix provides - it seems that by default there are a series of menus on the screen that give you access to everything.  I don't remember even seeing a bottom task bar.  As soon as I have it backed up I plan to repartition it and install the netbook remix there.

I know that doesn't answer anything specific to the Dell Mini 10, but I *HAD* ;) to comment on the neat look that the netbook remix seems to have.

Good luck!

Dave ;)

---

