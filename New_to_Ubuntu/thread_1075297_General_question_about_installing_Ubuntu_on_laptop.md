---
title: "General question about installing Ubuntu on laptops"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Charlie Chick on 2009-02-20
Hello Everybody,

What has happened to the Ubuntu installer? Increasingly, I'm finding that I can't install on some laptops using 8.10. I have to go back to previous versions, sometimes as far back as 6.06. Why is this?

At present, I'm trying to install Ubuntu on a brand new HP Mini which normally comes with Vista. Shouldn't be a problem for Ubuntu, should it? Yet, it crashes in the middle of the install. Why?

Much to my chagrin and amusement of my Linux hating colleagues, the Windoze XP installer works everytime!

I'd be grateful if anybody could shed some light on this matter for me.

Thanks, as always,

Charlie

---

### Post by Doug11 on 2009-02-20
Has this disc installed completely before? At the boot,,before choosing to install,,try a disc check to see if your cd is ok.

---

### Post by fuzzyk.k on 2009-02-20
Many problems during the installation are caused by a problem with the cd, try writing another disk slower

---

### Post by theozzlives on 2009-02-20
Windows uses pressed CDs less apt to have errors, try ordering an Ubuntu CD. I've never had a problem with my Dell Inspiron 1525 burned or pressed.

PS. a mini isn't a laptop, it's a netbook.

---

### Post by Charlie Chick on 2009-02-20
Thank you all for your replies. There doesn't seem to be a check disk function, but I put the disk (a pressed Linux Format CD) in another machine and it works perfectly. So I'm back to square 1.

Charlie

---

### Post by 3rdalbum on 2009-02-20
Try the Alternate Installer disc. I'm surprised 6.06 can even boot up a netbook.

---

### Post by Zeedok on 2009-02-20
> **Charlie Chick said:**
> Thank you all for your replies. There doesn't seem to be a check disk function, but I put the disk (a pressed Linux Format CD) in another machine and it works perfectly. So I'm back to square 1.

Charlie

When you boot from the live CD this will come up as an option (from memory along with boot from CD and bot from hard drive).  I have never had a problem installing various distros (including Ubuntu 8.10) on a couple of laptops.  Sometimes the installation can take ages (like > 1 hour if it is an old laptop) so if your disc is truly OK, then I would persist - or try burning another disc.

---

### Post by Charlie Chick on 2009-02-20
> **3rdalbum said:**
> Try the Alternate Installer disc. I'm surprised 6.06 can even boot up a netbook.

What does the alternate CD do?

---

### Post by Charlie Chick on 2009-02-20
I've tried again and can report that the brown 8.10 installer bar gets around 70% of the way when it goes yellow/green and in vertical stripes. The screen than goes dark with a flashing cursor in the top left hand corner and it stays like that. Permanently. Nothing short of switching off will remove it. I thought I saw error messages about firmware at some point.

The 8.04 install goes the same way but without the firmware error messages. After the 80% mark, the screen goes a funny pattern and the Ubuntu music plays as if everything were normal. But I'm left with a blank screen. The only alternative is to switch off. Nothing else works.

What's wrong? The 8.10 disk is pressed Linux format DVD and the 8.04 disk is a HHB CD-R home burnt that has worked on other machines.

Thanks,

Charlie

---

### Post by Michael.Godawski on 2009-02-20
hi,

might be some graphic card related issue.

Try to install via the alternate installer, which installs in text mode, so all this "unnecessary" stuff like live options is removed.

Text-mode is as easy as the graphical way.

Perhaps you will be able to end the installation in this way.

---

### Post by edwardLS on 2009-02-20
Both my son and I have installed various releases of Ubuntu on both laptops, desktops, and now a Mini.  The one brand name in all of these that has presented a problem is the HP brand.  
My son had to disable ACPI to get Ubuntu installed on his HP laptop. I can not tell you how he did that, but he indicated that some of the Power Management did not perform properly.  Sorry I can provide more details, but hopefully this my get you some additional information.

---

### Post by Charlie Chick on 2009-02-20
> **edwardLS said:**
> Both my son and I have installed various releases of Ubuntu on both laptops, desktops, and now a Mini.  The one brand name in all of these that has presented a problem is the HP brand.  
My son had to disable ACPI to get Ubuntu installed on his HP laptop. I can not tell you how he did that, but he indicated that some of the Power Management did not perform properly.  Sorry I can provide more details, but hopefully this my get you some additional information.

Interesting, as I'm trying to install ubuntu on an HP Mini. I looked in the BIOS, but there's very little there and certainly no acpi settings.

Next, I tried the 8.10 alternate, text based install CD. After taking twice as long to install, it came up with the same result after rebooting!

I'm now experimenting with various discs to see what works and what doesn't.

Charlie

---

### Post by Charlie Chick on 2009-02-23
I have now &#8220;solved&#8221; this problem. I typed &#8220;Ubuntu&#8221; and &#8220;HP 2133&#8221; into a search engine and came up with the following helpful sites:

[https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

[http://www.hp2133guide.com/ubuntu-distro-for-the-mini-note-minbuntu/](http://www.hp2133guide.com/ubuntu-distro-for-the-mini-note-minbuntu/)

[http://wiki.mininoteuser.com/doku.php?id=howto:installubuntu8.04](http://wiki.mininoteuser.com/doku.php?id=howto:installubuntu8.04)

The key to successfully installing Ubuntu on this netbook is to hit F6 after the CD installation menu appears and add &#8220;xforcevesa&#8221; to the end of the line and hit enter. That made everything but 8.10 install properly. After installing 8.04, running a full update and enabling the Broadcom restricted wireless driver, everything but the internal microphone worked. To try and get the mic to work, I followed the instructions on the Ubuntu 2133 wiki to update the ALSA sound, but unfortunately, it didn&#8217;t work.

I tried installing both Minbuntu and Ubuntu Netbook Remix, but without success. However, I now have 99% working netbook with 8.04 and I&#8217;m pleased with the result.

What I can&#8217;t understand is that under no circumstances could I get 8.10 to install, whether directly from the installation CD or by installing 8.04 and then upgrading. After re-booting, I was always left with a blank screen. In the end, I decided to leave 8.04 on it and just get updates for that.

Thank you, as always, to all you helpful people on this forum.

Charlie

---

### Post by Charlie Chick on 2009-02-23
I'm trying to mark this thread as solved, but I cannot find the 'solved' marker anywhere. I thought that it was under the Thread Tools menu, but it doesn't appear. 

Would a moderator kindly close this thread for me?

Thanks,

Charlie.

---

