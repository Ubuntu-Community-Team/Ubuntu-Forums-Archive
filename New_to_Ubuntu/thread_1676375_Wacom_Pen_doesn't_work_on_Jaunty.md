---
title: "Wacom Pen doesn't work on Jaunty"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by juditk on 2011-01-27
My Wacom Pen tablet isn't working with Jaunty. When I plug it in the light turns on but it doesn't work. Can I have some help please? :-?

I bought this among others because [here]("https://help.ubuntu.com/community/Wacom") it said that "Most Wacom tablets should work out of the box in Jaunty, including full hotplugging support, without the need for additional configuration." Well it doesn't. At least not for me. What's killing me is that that page has a detailed description for every other version except Jaunty. :cry:

So far: 
1. I Installed: wacom-tools and xserver-xorg-input-wacom from Synaptic. 
2. I copied xorg.conf into /etc/X11 and that made the whole computer crash. 
3. Then I installed the drivers that came with the tablet on another computer with windows xp and everything worked within 10 minutes, ...so the tablet is fine it just doesn't work with Ubuntu. 

Also I keep finding this solution:

> 1. Open GIMP (I have GIMP 2.6.6)
2. In the Edit menu, click on preferences
3. Click on Input Devices
4. Click on Configure Extended Input Devices
5. For the devices; stylus, eraser and cursor, set the Mode to 'Screen'
6. Click Save, then Ok and you're done!

The tablet doesn't appear in the Input Devices. I only have the following:
Macintosh mouse button emulation
PS/2 Mouse
AlpsPS/2 ALPS Glide Point
another mouse (this is what I'm using). 

I had Ubuntu for a few years now but I'm still a newbie regarding stuff like this, so please can someone explain it to me step by step? [-o<

---

### Post by Favux on 2011-01-27
Hi juditk,

I answered your other post.  But let's use this new thread you've started.

Jaunty is no longer supported so you won't get updates, not even security updates.  Karmic will be supported through April.  Are you sure you want to use Jaunty?

If so we can get your tablet working in Jaunty.  What tablet is it?  Is it a Wacom Bamboo Pen?  On the bottom of the tablet does it say CTL460?  If not please post the model #.  In a terminal enter:
```
lsusb
```
In the output we're looking for the Wacom line.  Please post it.  That will give us the product ID.

---

### Post by Favux on 2011-01-27
> Yes it's Wacom Bamboo Pen. On the bottom it says CTL-460.

And I don't mind if it's not supported anymore as long as I can use it.
Alright.  First you need to install linuxwacom 0.8.8-10.  That's because it has your model in it, which is relatively new.  I forget the default linuxwacom in Jaunty, you can check it by using wacom in Search in Synaptics Package Manager.  Something like 0.8.2-x?  So anyway that needs to be updated.

You can either follow Section 1 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") or perhaps the simpler Part I. in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  Except in the Bamboo HOW TO you would use:
```
make

sudo make install
```
after
```
./configure --enable-wacom --prefix=/usr
```
and before
```
sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

```
Because you want all of linuxwacom and do not need or want xf86-input-wacom.  Copy and paste each command (some are long, get the whole thing) into a terminal and hit enter after each.

After a reboot your stylus should work.  To get your touch and pad (tablet buttons) to work we'll need to use a modified 10-wacom.fdi.

---

### Post by juditk on 2011-01-28
As it turns out I installed 2 older drivers and that's why it didn't work. With a little help I managed to solve it. Once we changed it, it started working. :)

This is what solved it for me:
I needed the [8.8 driver]("http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.8-10.tar.bz2"), a search in Synaptic for the word "wacom" only gave the 2.2 version. 
After that I followed "[I. Install LinuxWacom's 0.8.8-10 wacom.ko]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1")"
until the "get libx11-dev" part. 
For that I needed libxcb1, which at first gave the following error:
"Depends: libxcb1 (= 1.1.93-0ubuntu3.1) but 1.1.93-0ubuntu4 is to be installed"

To [solve this]("http://ubuntuforums.org/archive/index.php/t-1220447.html"), I had to switch updates on in the source list. 
After that I changed the fdi file because it was also an older version and was no good and X11 died twice untill we figured it out. 
I copied the example text from section 2 [URL="http://ubuntuforums.org/showpost.php?p=7093065&postcount=104
into the fdi file"]of[/URL]. 

I also used [this]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") the part referring to Karmic. 
And that's it. 
Now it works fine, thanks Favux!

---

