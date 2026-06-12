---
title: "Battery Life"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by GapToothedGypsy on 2009-10-14
Hi Guys,

Sorry, but one more newbie post for you.

I a have an eeepc Netbook 1005HA, came with Windows :o( so immediately installed my first copy of Unbuntu Remix 9.04, sorted out the networking stuff thanks to the forum and very happy with the result. Have since tried xuntu, eeebuntu, and now running the beta of remix 9.10. With all these I have the same problem, why does my battery life halve with Ubuntu compared to XP?

With Windows installed my battery life says 9 hours remaining (and the eeepc is sold as 10.5 hours battery life), boot from a usb stick and the battery life is given as only 4 hours remaining!

This is very frustrating as I bought the eeepc for its long battery llife to use in the field to store my pictures on trips away. I don't want to go back to XP --- ever, so am I missing something or can this problem be fixed?

So that's two questions I know :o)

Regards


The GapToothedGypsy

---

### Post by 3rdalbum on 2009-10-14
Try running the Powertop utility to identify programs that are using a lot of battery power.

Windows XP is an old operating system anyway, so it demands less of your resources than Ubuntu (which is certainly not designed to be lightweight, at least not compared to other Linux systems).

---

### Post by GapToothedGypsy on 2009-10-14
Thanks for the reply 3rdalbum,

I am very new to linux, so I've obviuosly got this very wrong! I was under the impression that I could build a small footprint, minimal OS on a netbook using linux. I was informed that ubuntu was cuurently the best distribution so I gave it a go. I have had a lot of problems getting it to work on the eeepc I bought for the job in many of its different flavours. So now I find that XP is better for the task than ubuntu? surely not!:confused:

Very Sad GTG

---

### Post by getaceres on 2009-10-14
The remaining battery time shown in the applets is an estimation and it depends on the use that you are giving. Also, it's not fair to compare a system running from hard disk with a system running from a USB drive. The USB drive tends to spend more energy than the hard disk. 
To get better results:
- Dim the screen brightness to the half or less than a half.
- Deactivate desktop effects.
- Turn off the Wireless switch when you are not using it.
- Run powertop and see what's consuming power. It gives hints also and can execute some commands for you if you want. It also estimates battery life by his own, so you can compare it to the GNOME battery applet.

---

### Post by GapToothedGypsy on 2009-10-14
Thanks for the Reply,

I did test Ubuntu from the USB Drive, however I now have it installed on the hard drive. It does seem that whichever distro I use the result is the same. I will play with the PowerTop later today and see what it gives me. Certainly, I can turn off the Bluetooth and Wireless connections, however XP was running with them on.

I'm not trying to whine about this, it's just very frustrating that I don't have enough experience with the product to sort it out!

Once again thanks for your help


GTG.

---

### Post by getaceres on 2009-10-14
I don't have a huge battery on my laptop but my experience is that it last almost the same in XP and Ubuntu (It's slightly shorter in Ubuntu but barely noticeable). Anyway, the best way to test it is to let the system running until it shuts off in both systems and compare the time, because relying in the stimations of an applet is not an accurate measure.

---

### Post by GapToothedGypsy on 2009-10-14
Excellent advice, thanks for coming back. I guess it's having confidence in the product and experience is everything, I'll go and play some more.

GTG

---

### Post by yossell on 2009-10-14
+1 for earlier suggestions.

There have been some complaints that battery life is shorter under ubuntu - in my own experience, after running powertop as root, following its recommendations, and after some playing around with my Nvidia settings, my battery life is, as far as my unscientific tests of letting the computer run until the battery dies, exactly the same under Ubuntu and Vista. 

If you want something light then Xfce, Lxde and Openbox might be worth experimenting with - Ubuntu's not that light these days - I'm intending some day to see if the battery lasts appreciably longer.

---

### Post by muteXe on 2009-10-14
Is powertop in the repo's?
Cheers,
mute

---

### Post by Paul41 on 2009-10-14
> **muteXe said:**
> Is powertop in the repo's?
Cheers,
mute

Yes
```

sudo apt-get install powertop
```

---

### Post by Mighty_Joe on 2009-10-14
> **GapToothedGypsy said:**
>  I was under the impression that I could build a small footprint, minimal OS on a netbook using linux. I was informed that ubuntu was cuurently the best distribution so I gave it a go.

It is possible to create a minimal OS with Linux. Ubuntu is not a minimal OS.  It is intended to compete with the likes of Windows Vista.  Ubuntu runs fine on recent hardware and has a dedicated [netbook version]("https://wiki.ubuntu.com/UNR").
There are minimal Linux Distros that use the Ubuntu repositories, for example, [Masonx]("http://ubuntuforums.org/showthread.php?p=7837059") or [Crunchbang lite]("http://www.crunchbanglinux.org/wiki/downloads#lite_edition_-_32-bit").  Of course, to get a small footprint, they sacrifice a lot of functionality.

---

### Post by imaqt55 on 2009-10-14
I also have the Asus 1005HA and have had the same exact problem.  I am just a beginner to Linux, but an experienced friend helped out with no success.  My battery life in Ubuntu is a little over half what it is in XP (after actual testing, not just according to the battery remaining meter).  Turning off things like wireless, camera, etc. when not in use has helped, but it is still nowhere near the battery life when running XP.  Frustrating.

One other thing that helped is in the power management settings, for "when laptop lid is closed" I set it to "blank screen" rather than "do nothing."  In both cases, the screen goes black when you close it, but for some reason, it stays cooler and the battery lasts longer when "blank screen" is selected.  Though, perhaps mine is unique because I am having a problem where it won't sleep when idle if the screen is closed (even though it will if the screen is open).  Not sure if that is related.

---

### Post by phidia on 2009-10-14
[AntiX]("http://antix.mepis.org/index.php/Main_Page") might be a good distro to try. In my experience some laptop hardware is better supported than others in linux with power management, suspend and resume being frequently reported issues.

---

