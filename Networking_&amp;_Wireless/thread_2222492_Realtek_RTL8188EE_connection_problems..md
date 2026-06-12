---
title: "Realtek RTL8188EE connection problems."
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by Unanimated on 2014-05-06
So I installed Ubuntu 14.04 on my laptop today, and I've been having some issues with the wireless connection. When I was running the Live CD, nothing wrong seemed to be happening, but after a full install, the connection will vary from being fast (as usual) to being incredibly slow and it will drop for minutes at a time before the internet connection is restored. I've restarted the router, restarted the wireless card numerous times, updated all the software on the computer since installing, and restarted the computer about three times and it's still happening. Running apt-get update over the connection took 11 minutes because the internet kept dropping, and I couldn't update the software over that connection because it kept dropping.

Trouble is, I haven't found a more recent tutorial for fixing problems with this wireless adapter - all of the ones I've found are for rather outdated versions of Ubuntu and imply that everything should be fixed. I'm also having troulbe finding a driver. The card is a Realtek RTL8188EE.

Here's the relevant section of my lspci output:
```
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)

```

---

### Post by squakie on 2014-05-06
Had the same trouble - see [http://ubuntuforums.org/showthread.php?t=2219952](http://ubuntuforums.org/showthread.php?t=2219952) for the solution.

---

### Post by Unanimated on 2014-05-06
That seems to have worked, to an extent - I'm getting faster data speeds, but only after I disabled WPA2 and dropped it down to WPA on my router. Does that have anything to do with it too?

---

### Post by squakie on 2014-05-07
Well,, not with my connection.  Comcast "all-in-one" (TV, phone, internet gateway) - wpa2, connect at 150mps consistently with no problems.

---

### Post by Unanimated on 2014-05-07
I'll try it later tonight on a fresh install of Xubuntu. I saw some errors when using make, would you recommend running make with sudo? Or running make before updating the kernel and everything?

---

### Post by squakie on 2014-05-07
Make should be fine without sudo.  make install, however, must be run with sudo in order to have the permissions to write to the corresponding system folder.

As far as errors in the make - there are several warnings the compiler issues in the code.  We have to trust the programmer(s) to know that they have seen those and know they are ok (sometimes you get warnings on various things - data types, etc.).  As long as the make completes and doesn't have a summary at the end that has three asterisks - those would would indicate the compilation was not successful.  Be sure you have installed the dependencies, etc., as mentioned in the thread.  With running xubuntu, there may be some things missing that might need to additionally installed.

If you code post back the final 20 lines or so from your terminal when you run the make I can take a look and see if it completed ok.  Please post those back between code /code statements - each surrounded by brackets.

BTW - where in Iowa?  My family was from the Audubon/Exira/Hamlin/Elk Horn/Kimbalton areas after coming from Denmark.

---

### Post by Unanimated on 2014-05-07
Alright, I'll do that. Just to make sure, what distro did you use that made it work well? I tried it in Lubuntu after updating the kernel and everything and it didn't quite work, although make and make install didn't seem to spit out any visible errors. 

I'm from the Iowa City/Cedar Rapids area and I'll be moving to Cedar Falls soon. After being a member here for several years I've never had anybody notice the Iowa thing!

---

### Post by squakie on 2014-05-07
I'm running "regular" Ubuntu 14.04 64-bit.  I suspect you've been trying xubuntu and lubuntu because your computer is a little older and you are trying to maximize it?  I've done that myself on a couple of others I have and on some I've bought, fixed up, and either sold real cheap to someone who needs it or just given it away.  However, if your hardware can handle "regular" ubuntu - especially the Unity interface, then you could also try just "regular" Ubuntu.

I used to live in Sterling, IL., about 1/2 way between the quad cities and Rockford, IL.  When my family was still in western Iowa, I used to go through Iowa City all the time.  i've also gone there to the big library (can't remember if it's an on-campus library or a state library) to do family history research.  Fun town!

---

### Post by Unanimated on 2014-05-07
Yeah, that's definitely something about Iowa City - you don't know where the city ends and the university begins. It is a good place though, I like it quite a bit!

Anyway, I finally got a chance to do the commands on an install of Ubuntu 14.04. I've installed all the updates it wanted (so kernel updates and the like) and have started the process for the driver, but after running make this is what happens:

```
/home/sam/rtl8188ce-linux-driver/rc.c:298:2: warning: (near initialization for &#8216;rtl_rate_ops.rate_update&#8217;) [enabled by default]
  CC [M]  /home/sam/rtl8188ce-linux-driver/debug.o
  CC [M]  /home/sam/rtl8188ce-linux-driver/regd.o
  CC [M]  /home/sam/rtl8188ce-linux-driver/efuse.o
  CC [M]  /home/sam/rtl8188ce-linux-driver/cam.o
  CC [M]  /home/sam/rtl8188ce-linux-driver/ps.o
  CC [M]  /home/sam/rtl8188ce-linux-driver/core.o
  CC [M]  /home/sam/rtl8188ce-linux-driver/stats.o
  CC [M]  /home/sam/rtl8188ce-linux-driver/pci.o
  LD [M]  /home/sam/rtl8188ce-linux-driver/rtlwifi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/sam/rtl8188ce-linux-driver/rtlwifi.mod.o
  LD [M]  /home/sam/rtl8188ce-linux-driver/rtlwifi.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
cp: cannot create regular file &#8216;rtl8192c/&#8217;: Not a directory
make: *** [all] Error 1

```

EDIT: I ran the command again, and this time it worked (not really sure what happened differently but I'm not complaining), and I finished the rest of the commands. I restarted my computer, and nothing was different. I'm not sure if the driver has loaded or anything like that or what driver is currently loaded for my card (if anything), and I'm not sure how to go about checking that.

---

### Post by Unanimated on 2014-05-08
I also upgraded the kernel to 3.14.1, something that other people said worked for them - but to no avail. After upgrading the kernel I tried recompiling and installing the driver again, and it didn't work. Again.

---

### Post by squakie on 2014-05-09
At this point you are beyond what I know - I hope someone else can help you out.  As far as the WPA versus WPA2 thing, that has me a little baffled.  I *thought* the WPA2 thing was negotiated at the time the connection is made to the wireless network.  However, the driver obviously has to interact with what I assume is what wpa-supplicant is doing.  At that point you're way beyond me.  Perhaps a post back in the place where this driver source is downloaded from would help.

I should note - I haven't recompiled the driver since some updates I received last week and since then my connection is terrible again.  I'll try to capture what I do when I recompile it and install it so you can see if it is the steps you have followed as well.

---

### Post by Unanimated on 2014-05-09
Sounds good. Thanks a lot for all your help - I'm going to try again on another fresh install tonight. With all this stuff I've been doing to it it's been a little difficult to undo what I've done, so I'll give it another whirl tonight. Hopefully this problem will be fixed for good sometime in the near future, I know these chips are somewhat common and I've noticed tons of people having this problem since I started looking around for it.

At least I have a long Ethernet cord!

---

### Post by squakie on 2014-05-09
I rebuilt everything today.  Note that if your folder where everything went from the git (rtl8???? something), then you can go straight to the make.  However, if you completely reinstalled again, you'll need to do everything in the link over again.  I didn't remember it from before, but I had to use sudo make as I got a permissions error.  Maybe you need to do the same?

---

### Post by Unanimated on 2014-05-11
Not really sure what happened, but my problem seems to be solved now. I booted into a fresh install, installed all updates over Ethernet, in addition to downloading kernel version 3.14.1 - even though my speeds weren't too horrible before I restarted, they were just inconsistent. Rebooted after installing the updates, installed 3.14.1, rebooted again, and now everything is fine. I'm a bit confused but hey, not going to complain.

This may also be relevant - I changed my router's settings to WPA2-Personal (WPA2 only, not WPA/WPA2) and the encryption method to TKIP.

---

### Post by squakie on 2014-05-11
Yes - sometimes setting the router to "just" a specific encryption does help.  I don't know if this is one of those cases, but I have read threads before about mixed-mode causing problems.

Also - be aware that whenever the kernel is updated, or for that mater some other updates, the kernel may get rebuilt and have new headers.  In those instances you will probably need to re-make and re-make install the driver.  I just wait for things to start acting weird again and then just rebuild the driver.

---

