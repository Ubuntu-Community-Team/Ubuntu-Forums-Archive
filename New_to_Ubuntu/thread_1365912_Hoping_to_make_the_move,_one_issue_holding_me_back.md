---
title: "Hoping to make the move, one issue holding me back"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Timjh on 2009-12-27
I've been playing with the Live CD, and am quite anxious to make the move to Ubuntu. I have one concern, and that has to do with screen resolution. My preferred screen resolution is 1280 x 1024, and which is not an option when I run from the Live CD.

I have the Radeon X300 video processor, which I've read might not be compatible with the most recent release of Ubuntu. I've also read that it might be possible to tweak the xorg.conf file to add the 1280 x 1024 resolution. Any advice would be much appreciated!

---

### Post by 3rdalbum on 2009-12-27
> **Timjh said:**
> I've been playing with the Live CD, and am quite anxious to make the move to Ubuntu. I have one concern, and that has to do with screen resolution. My preferred screen resolution is 1280 x 1024, and which is not an option when I run from the Live CD.

I have the Radeon X300 video processor, which I've read might not be compatible with the most recent release of Ubuntu.

That's not quite true. ATI no longer makes a driver for the X300, so you can't use the official ATI driver. However, Ubuntu includes an open-source driver, so your card is supported.

> I've also read that it might be possible to tweak the xorg.conf file to add the 1280 x 1024 resolution. Any advice would be much appreciated!

Yes, this can be done. You'll need to generate an xorg.conf file, and then add the resolution into it.

But frankly, if your machine supports it you should get a modern Nvidia graphics card; one that is supported by the "185.xx" Nvidia driver. You're likely to get the correct resolution out-of-the-box, have good 3D acceleration, and video decode acceleration on certain cards. Much less hassle.

---

### Post by Timjh on 2009-12-28
Thank you for your reply. Sounds like getting a new video card is the best option. I wonder if there are any Dell Dimension 4700 owners out there who can recommend a compatible Nvidia graphics card?

---

### Post by 3rdalbum on 2009-12-28
> **Timjh said:**
> Thank you for your reply. Sounds like getting a new video card is the best option. I wonder if there are any Dell Dimension 4700 owners out there who can recommend a compatible Nvidia graphics card?

Apparently it uses PCIe for graphics cards - this is good.

An Nvidia GT210 will do fine, it will get all its power from the PCIe port and they're quite cheap too. Not the best performance, but better than the X300 by a country mile.

Note that no graphics cards are actually branded Nvidia - they all have other manufacturer's names on it. Any brand will do as long as it says GT210 on the box.

---

### Post by Timjh on 2009-12-28
I just took a look at the Parts and Upgrades page for the Dimension 4700 on the Dell website, and I don't see the GT210 listed. Do you think this:
[http://accessories.us.dell.com/sna/products/Graphics_Cards/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=A2388448&mfgpid=166539&chassisid=8225](http://accessories.us.dell.com/sna/products/Graphics_Cards/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=A2388448&mfgpid=166539&chassisid=8225)

or this:

[http://accessories.us.dell.com/sna/products/Graphics_Cards/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=A1527316&mfgpid=166539&chassisid=8225](http://accessories.us.dell.com/sna/products/Graphics_Cards/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=A1527316&mfgpid=166539&chassisid=8225)

would work?

---

### Post by ibuclaw on 2009-12-28
Any PCI-Express card will do, from any store - not just what Dell recommend. ;)
The 9500GT is nice though... (I use an 8500GT myself)

---

### Post by iMisspell on 2009-12-28
> **Timjh said:**
> ...Sounds like getting a new video card is the best option...
Do you really need it though ?
If you can tweak your current card why get something that's not needed ?

Personally i would give it a shot with what you have now, try tweaking and if that dont work, get a new card. If you find out you cant get the res you want, whats the worst that can happen, your stuck with a low res for three days tops if you order from newegg, if you buy from a walk-in store, you only have to wait a few hours.

Not to be rude, but with that card im sure your not playing Crysis or anything like that ;) so why get something if your not gonna utilize it ?

Best of luck eather way.

About three or four months ago i finally installed Ubuntu Desktop (been running a server for alittle while now) as a dual boot with XP (so i can still play games if i ever want to) and im loving it. I tried a RedHat Dis about 8 years ago - rpm this and type that - was too much for me to handle at the time, now looking back i which i had stuck with it.

Anyway...

_

---

### Post by Timjh on 2009-12-30
I went ahead a got a GeForce 210 ($29 after rebate), installed it, and installed Ubuntu. After installing Ubuntu, I grabbed the proprietary Nvidia driver. Unfortunately, with all that accomplished, the range of available screen resolutions still falls short of expectations. Before switching to Ubuntu, I confirmed that the new video card worked and was able to drive my display to higher resolutions than my old Radeon card.

So, I know that from a hardware point of view, I can get higher resolutions. The question is, how do I do it now that I'm running Ubuntu?

---

### Post by Tahakki on 2009-12-30
System > Administration > NVIDIA X Server Settings.

Open that, and go to X Server Display Configuration. You can change the resolution there.

---

### Post by Timjh on 2009-12-30
The problem is that the resolution I want is not listed. I want to use 1280 x 1024, which is what I had it set to under Windows XP. In fact, my video card is capable of much higher resolutions that the options that are shown.

Also, when I change from the default resolution that Ubuntu starts up with, and click the Save to X Configuration File button, I get the following error: Failed to parse existing x config file '/etc/X11/xorg.conf'!

---

### Post by danastasio on 2009-12-30
Hrm, its odd that you are not getting that resolution with the live CD, I have never had trouble getting that res. Live. What I would do (and this is JUST me) is partition your HD so that you have a small partition for ubuntu, (very small, 15 or so gigs) and install it to that partition (choose "use largest continuous free space during install") Once it is installed, install all updates and the driver, if it works, BAM back up and wipe out the rest of your hard drive! :lolflag: If not, i think it will make the problem easier to diagnose.

---

### Post by Tahakki on 2009-12-31
Hmm, try using the default GNOME tool instead of the NVidia one. Preferences > Display, I think.

It's odd you're getting that error. Try runninng the nvidia program as root - "gksudo /usr/bin/nvidia-settings".

---

### Post by Swagman on 2009-12-31
You probably should have told him to copy & paste that into a terminal

---

### Post by Timjh on 2009-12-31
I tried your suggestions, unfortunately it still didn't work. I'm wondering whether, in regard to the screen resolution problem, this fragment from the Xorg.0.log file is relevant:

(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-1's EDID.

---

### Post by Timjh on 2009-12-31
fyi, I've posted my issue on the Ubuntu Questions forum, and included my Xorg.0.log file and other relevant data.

---

