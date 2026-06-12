---
title: "wireless card won't work"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by noob555 on 2009-10-18
So here is the problem. I tried going beyond my comfort level yesterday. I tried to patch my Wireless driver to allow packet injection. I'm not certain what happened, but the moment I restarted the wireless no longer functioned at all.

If I enter "lspci", the computer clearly recognizes that the card is there because it spits out the following:

04:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)

However, if I enter "iwconfig", I get the following:

lo no wireless extensions.
eth0 no wireless extensions.
irda0 no wireless extensions.
pan0 no wireless extensions.

The wireless does not work.  In fact, if you look at the Ubuntu GUI, it's like the wireless doesn't even exist.  

I tried reinstalling a fresh driver from debian.org, but no joy. I really don't know what to do at this point.

Any help would be greatly appreciated.

---

### Post by yeats on 2009-10-18
> So here is the problem. I tried going beyond my comfort level yesterday. I tried to patch my Wireless driver to allow packet injection. I'm not certain what happened, but the moment I restarted the wireless no longer functioned at all.

Can you post what steps you took to patch your driver?

---

### Post by noob555 on 2009-10-18
I did, to the best of my ability, follow the instructions found here:

[URL="http://www.aircrack-ng.org/doku.php?id=ipw2200"]
http://www.aircrack-ng.org/doku.php?id=ipw2200[/URL]

which should have applied the appropriate patch for my wireless card/chipset.  But I was never actually able to turn on the module.




I have tried to post the full set below for your convenience:


ipw2200

At this point in time, this page is far from complete. In the interim, useful information will be included here. Also do a Forum Search for additional information.
ipw2200-1.2.1 how to

The previous version of ipw2200 can't be compiled with the linux headers 2.6.20-16-generic (used by Ubuntu 7.04) so here is the way to get the rtap0 interface working.

    *
      ieee80211-1.2.17.

Make sure that you have this library else ipw2200-1.2.1 drivers won't compile

wget [http://superb-west.dl.sourceforge.net/sourceforge/ieee80211/ieee80211-1.2.17.tar.gz](http://superb-west.dl.sourceforge.net/sourceforge/ieee80211/ieee80211-1.2.17.tar.gz)
tar zxvf ieee80211-1.2.17.tar.gz
cd ieee80211-1.2.17
sudo make
sudo make install

    *
      Get the patch and the driver.

drivers patch link

wget [http://superb-west.dl.sourceforge.net/sourceforge/ipw2200/ipw2200-1.2.1.tgz](http://superb-west.dl.sourceforge.net/sourceforge/ipw2200/ipw2200-1.2.1.tgz)

    *
      Patch the driver.

tar zxvf ipw2200-1.2.1.tgz
tar zxvf ipw2200-1.2.1-inject_patch.tar.gz
patch ipw2200-1.2.1/ipw2200.c ipw2200-1.2.1-inject.patch
patch ipw2200-1.2.1/Makefile ipw2200-1.2.1-inject_Makefile.patch
cd ipw2200-1.2.1
sudo ./remove-old
sudo make
sudo make install

    *
      Turn on the module.

sudo rmmod ipw2200
sudo modprobe ipw2200 rtap_iface=1

At this stage if you see that your module can be loaded, you can load it at boot with the option “rtap_iface=1”. Just edit the file ”/etc/modprobe.d/options” and add the line “options ipw2200 rtap_iface=1”

    *
      Now you should be able to bring up the rtap0 interface and listen with airodump-ng.

sudo ifconfig eth1 up
sudo ifconfig rtap0 up
sudo airodump-ng rtap0 -c 11 --bssid 00:0f:e2:xx:xx:xx --ivs -w dump

---

### Post by noob555 on 2009-10-18
I should also note that I have since tried installing a new driver from intel and removing aircrack-ng.  But it still doesn't work at all.

---

### Post by yeats on 2009-10-18
Thanks for the post....

When you followed these instructions, were you aware of any errors in the output?  Or were you just pasting in the commands and trusting that they worked? (Don't worry, we've all been there :-))

I suspect that there was an error somewhere along the way.

> But I was never actually able to turn on the module.

What sorts of error messages are you getting here?

---

### Post by noob555 on 2009-10-18
As I recall, there may have been some error messages. But so much text was flying my way that I didn't really look to consider it.

I am ashamed to say that I was just cutting and pasting, trusting that it would work.

---

### Post by yeats on 2009-10-18
> I am ashamed to say that I was just cutting and pasting, trusting that it would work. 

Like I said - when I started I did the same thing :-)

> As I recall, there may have been some error messages. But so much text was flying my way that I didn't really look to consider it.

You don't happen to still have the terminal window open with the scrollback still in place (wishful thinking, I know)?  For future reference, Linux error messages are extremely useful (as opposed to the gibberish on other systems), and usually point you to the exact cause of something not working.

If you don't have anything else, there are logs in /var/log that record pretty much everything you do (or that your system does).  Reading here:
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

The best advice I have for you, under the circumstances is to try to reverse, step by step, the instructions you followed.  Others may have a better way to get this working, but wireless card drivers make me want to throw my laptop out the window :-).

---

### Post by noob555 on 2009-10-18
> **chrissharp123 said:**
> Like I said - when I started I did the same thing :-)

You don't happen to still have the terminal window open with the scrollback still in place (wishful thinking, I know)?  

...

The best advice I have for you, under the circumstances is to try to reverse, step by step, the instructions you followed.  Others may have a better way to get this working, but wireless card drivers make me want to throw my laptop out the window :-).

Unforuntately, no I don't as it was yesterday.  And I am quickly learning of the importance of my error message.

Another forum recommended simply reinstalling the kernel as that would have all of the stock drivers with it.  What do you think?

And thank you.  I don't know how I could possibly manage on ubuntu without the assistance of so many people contributing their time to this forum.  :)

---

### Post by yeats on 2009-10-18
> Another forum recommended simply reinstalling the kernel as that would have all of the stock drivers with it. What do you think?

I think that's probably a good idea.  Worth a try, I would think.

---

### Post by noob555 on 2009-10-18
Cool.  I'll give it a try.  Thank you.

---

### Post by la3875 on 2009-10-18
Worst case is you could try a clean install. You don't mention which Ubuntu flavor you are working with? I have the same card in my laptop and it was a hassle to get functioning prior to 8.04. Good luck!!!

---

### Post by noob555 on 2009-10-18
So I reinstalled the generic kernel meta package, the headers and the kernel itself (2.6.28-15.generic).

I am using Jaunty.

The wireless is working now, but the display has gone all screwy.  Everything is larger, a bit out of focus, out of place.  And when I go to System --> Preferences --> Display, it says my monitor is not recognized and that my monitor is "unknown" and it won't allow me to alter the resolution, refresh rate, etc.

I am using an Intel Mobile 915GM/GMS/910GML Express Graphics Controller

I don't know what happened because this is a completely new problem.

---

### Post by la3875 on 2009-10-18
...Ahhh the joys of learning and experimentation! I'm sorry I cant help you there as I have an ATI card in my laptop. My inclination is there is a conflict as a result of doing only a kernel install. You might want to try a live disc and see if your graphics work properly again. If so a clean install might be required to resolve.

---

### Post by noob555 on 2009-10-18
Ugh!  Well, Thank you for the the assistance.  I think you may be right.  At least a clean install has the benefit of bringing some closure to this matter.

---

### Post by yeats on 2009-10-18
> Ugh! Well, Thank you for the the assistance. I think you may be right. At least a clean install has the benefit of bringing some closure to this matter.

This is the way you learn how to manage your system.  Soon enough you'll be helping others get through this sort of crisis yourself :-).

---

### Post by rhythmiccycle on 2009-10-18
i don't know if you already tried this or not (i just skimmed through what people wrote)

but did you try...

with the computer hardwired to the Internet go to:

system->Administration->Hardware Drivers->and then activating the Broadcom.

I remember I was doing all this complicated stuff to get my wireless working, and then once I activated Broadcom everything worked

---

