---
title: "I can't connect to any wireless network"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by TrueWater on 2007-07-17
Hello all,

I'm new to this forum, I used Ubuntu on a older computer for a while and everything was working fine. But yesterday I installed Ubuntu (Feisty Fawn) on my new computer by using dual-boot. Installation went fine and I tried to set up a connection to my wireless router and there it goes wrong.
It shows connections, let's me enter WEP keys but when I connect it hangs at "Waiting for network key" and after a few minutes it stops.
To connect to the internet I use a 'Sitecom WL-172 USB'. Which is based on the RT73/RT2500 chipset.

So I spend hours trying every solution on the internet I could find and I just can't get them working. The first solution, was installing a new driver. Which I found here:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)
Well, I did a 'make', 'make install' placed in the the interfaces file etc. Till I found out that the file never was compiled right because I missed the build-essential. So, I booted into Windows and downloaded it, then downloaded libc6-dev and that one required libc6. I downloaded all 3 files and started out with libc6 but it tells me the package is already installed. Then I load up lib6c-dev and it tells me that libc6 wasn't satisfieable. Didn't it just tell me that it was already installed? :confused: I couldn't even compile the driver. :(

Then I tried ndiswrapper, didn't work either. It tells me everyting is working when I "ndiswrapper -l" but no connection.

Then I removed network-manager and installed WICD ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)). It tells me that the signal strength is 0%, whilst it's a nice 75% under Windows. Anyways, I enter my WEP key and stuff and press connect. It hangs at 'Requesting IP', so I just boot into Windows and wrote down my IP, Gateway, DNS etc. And entered in WICD. Now it connect's and it still tells me 0% signal strenght, so I open up Firefox and try it out, and It just starts loading a page it till it times-out (before I got this working It just immediatly told me 'server not found').

I hope I gave you enough information, if you need more just ask. Please note that wireless is the only way I can get onto the internet from this computer.

Thanks,
TrueWater

---

### Post by imdano on 2007-07-17
Try removing encryption from the network and see if you can connect.  There's an issue with RT* cards that keeps encryption from working with most GUI network managers (although wicd has a fix coming out for this).  If you can't connect without encryption, there's a chance that your drivers have gotten a bit messed up with all the changes you've tried to make (installing serialmonkey drivers, ndiswrapper).  Those serialmonkey drivers would be your best bet most likely.  Try uninstalling the existing libc6, then installing from what you downloaded and see if that works.

When you enter a static ip in wicd you'll always show a connection, but the 0% strength means you aren't *really* connected.  You could purposely enter the wrong password and it would still show a 0% connection.

---

### Post by TrueWater on 2007-07-17
> **imdano said:**
> Try removing encryption from the network and see if you can connect.  There's an issue with RT* cards that keeps encryption from working with most GUI network managers (although wicd has a fix coming out for this).  If you can't connect without encryption, there's a chance that your drivers have gotten a bit messed up with all the changes you've tried to make (installing serialmonkey drivers, ndiswrapper).  Those serialmonkey drivers would be your best bet most likely.  Try uninstalling the existing libc6, then installing from what you downloaded and see if that works.

When you enter a static ip in wicd you'll always show a connection, but the 0% strength means you aren't *really* connected.  You could purposely enter the wrong password and it would still show a 0% connection.

Thanks for the reply, I tried reinstalling the libc6 but then it gives me a message that it is conflicted with 'tzdata'. Which has something to do with the timezone as I understand. Anyways, when I tried to remove tzdata it tells me that 'some' other packages MUST be removed then too. But it aren't some, it are nearly all packages in Ubuntu (over 1.7GB of packages) so I got no idea what to do now. :confused:
Oh and about the driver changes, I already reinstalled Ubuntu 3 times in one day. Because I already knew everything got messed up. But well, how do I get away the conflict with tzdata message  so I can install libc6?

---

### Post by imdano on 2007-07-17
Is there any way for you to use an ethernet connection so you could get the packages you need with apt?  Otherwise it seems like you're in for a nightmare of a time trying to get dependencies squared away.  If you can't use ethernet, try removing the encryption on your network and see if you can connect that way (you should really try this anyways).

---

### Post by TrueWater on 2007-07-17
Taking away the encryption doesn't work. And I can get ethernet access by moving my computer down the stairs next to the router. But this isn't 3-2-1 done, but I'll give it a try. If I would do that, can I just use Sypnatic to download and install the build-essential package and his dependecies?

Thanks,
TrueWater :)

---

### Post by kevdog on 2007-07-17
Somehow this crucial piece of information was never included in any forums.  Here is how to install the build-essential package without an internet connection.  You must have the Ubuntu installation CD however.

All commands typed at command prompt:
1. Put ubuntu cd in drive (after ubuntu has started -- do not want to use the cd as a startup disk)
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build-essential

That should do it for you!

---

### Post by TrueWater on 2007-07-17
> **kevdog said:**
> Somehow this crucial piece of information was never included in any forums.  Here is how to install the build-essential package without an internet connection.  You must have the Ubuntu installation CD however.

All commands typed at command prompt:
1. Put ubuntu cd in drive (after ubuntu has started -- do not want to use the cd as a startup disk)
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build-essential

That should do it for you!
Thanks for your post, but does it also install the dependecies libc6 and libc6-dev? Since that's the thing I can't get working. Sorry for the question, but I need to redownload the Ubuntu ISO for that (what ISO contains all of that stuff?) and don't want to do that and end up that I wasted my time on downloading and burning it to then discover it isn't working.

Thanks,
TrueWater

---

### Post by kevdog on 2007-07-17
If you already have an internet connection you could skip to step #4.

As far as dependencies, aptitude always installs all the dependencies needed.  Rest assured Ive had many users use these instructions and they have all been able to compile if both the build-essential package and linux header files have been installed (these also on the cd).

---

### Post by TrueWater on 2007-07-17
> **kevdog said:**
> If you already have an internet connection you could skip to step #4.

As far as dependencies, aptitude always installs all the dependencies needed.  Rest assured Ive had many users use these instructions and they have all been able to compile if both the build-essential package and linux header files have been installed (these also on the cd).
Thankyou, I'm going to burn it right now. Still found the ISO on my harddrive. I'll post if it worked.

Thanks,
TrueWater

---

### Post by TrueWater on 2007-08-08
I'm really sorry for answering 3 weeks later, lol. The reason is that I couldn't get into the forums and after a couple of 100 times trying I stopped and after a 3 week holiday I try again, getting in immediatly :)
Anyways, I still can't get it working. When I do a 'sudo apt-cdrom add' it tells me It can't find the cdrom, so I do a 'mount -t iso9660 /dev/cdrom /cdrom', it says me that everything was succesfull.
So I try the 'sudo apt-cdrom add' again and, the same error :(.
Now what :confused:

Thanks,
TrueWater

---

### Post by sweetcancer on 2007-08-08
i had the same problem with sitecom wl-535 usb device, got it working by dong this --->  [http://ubuntuforums.org/showthread.php?t=520413&highlight=sitecom+wl-535](http://ubuntuforums.org/showthread.php?t=520413&highlight=sitecom+wl-535)

---

