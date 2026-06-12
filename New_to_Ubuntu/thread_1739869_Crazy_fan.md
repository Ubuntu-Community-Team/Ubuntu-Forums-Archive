---
title: "Crazy fan"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by Ken UK on 2011-04-26
Hi,

So I have a fresh install of Ubuntu 10.10 but I have a problem that is driving me crazy.

As far as I can tell the master graphics card's (a crossfire edition of ATi Xt1900XT) fan runs at full speed until Windows boots but under Ubuntu it doesn't calm down. Im sure when I used Ubuntu years ago when I installed the proper ATi graphics drivers this solved the problem but now due to the fact its so old as far as I can tell the only graphics card drivers I can use are the open source ones, the ATI ones are legacy.

Does anyone know what I can do to solve this problem?

Im very new so I've looked into it but its abit above me.

Thanks,

Ken

---

### Post by calavier62 on 2011-04-26
I found a program related to your issue, and I thought it might help - it's a .deb package, and you might need to search the synaptic package manager or ubuntu software center to download GDebi Package installer, but here's the link: 
[HTML]http://sourceforge.net/projects/amdovdrvctrl/[/HTML]

it allows you to control the fan speed, and performance related settings. You might also try searching for another driver or tuning down your extra graphics settings (f.e. the wobbly windows).

I don't have an ATi graphics card other then the built-in one in my laptop, so this is all of the advice I can give you.

Good Luck!

---

### Post by Ken UK on 2011-04-27
Thanks for the reply!

How do I find other drivers? Is there a collection of well known alternative drivers and is it easy to swap them for a beginner? As far as I can see Ubuntu has installed automatically the 'Additional Drivers' for gnome which I presume is the free drivers, not sure if they have a name other than that.

I dont think turning down graphical settings will do anything because firstly I haven't even customised the GUI at all yet, its all the default gnome look with no sopecial effects or compiz. Secondly there is no connection between fan speed and workload, the fan does this from the point I press the on button (before any loading of anything from the HDD), even in the BIOS :)

Ill have a look at your suggestion, just to make sure Im clear though...
I install this program 'amdovdrvctrl' possibly through the software centre or synaptic but if not I install 'GDebi' first so I can manually download the .deb file and install it with that.

Thanks,

Ken

---

### Post by calavier62 on 2011-04-27
Yep. Those are the additional drivers - very user friendly to install, too :) 

So just to clarify about installing 'amdovdrvctrl'. (sorry about my old instructions those were terrible)

1. You can attempt to install the debian package either via GDebi or dpkg.
2. GDebi is the easiest method (basically a graphical front end to dpkg), so I'd recommend you install it - either via Synaptic or Apt-Get: 'sudo apt-get install gdebi' 
3. Once GDebi is installed, download the AMD Overdrive Control .deb file. 
4. once it's downloaded, right click the file, and choose Open with GDebi Package Installer.
5. The rest is pretty straight forward (as in clicking Install Package) you can close GDebi once AMD Overdrive Control has downloaded. 

The fun part will be finding it in the menus, especially if you upgrade to Nutty Narwhal (11.04) tomorrow!

But it appears that this is a common problem, so I wouldn't worry too much about any damage to the card, though the fglrx driver is known for having the most incompatibilities.

---

### Post by Ken UK on 2011-04-27
Good stuff that seemed to make sense and sounds easy enough.

I might switch to 11.04 tomorrow and then try it.

Is 'fglrx' the name of the default free drivers in 10.10?

Anyway you've explained things well to beginner, thanks alot.
I'm glad its not just me with the problem :D

---

### Post by calavier62 on 2011-04-27
I'm not sure on that one, because I have a different series ATi card. But It probably wouldn't hurt to check what drivers you are using. type or paste this into a terminal:
```
lspci -nn | grep VGA
```

and post your output into a post. I'll look into any known problems with that driver. 

Best of luck to you if you choose to upgrade! :)

---

### Post by wep940 on 2011-04-27
There's also a package called "fancontrol" in synaptic package manager, but I'm not intelligent enough to understand exactly what it does.  I do know that the fans on my laptop were never running until I removed that package, so I can only assume there are some sort of user-settable thresholds that I never did.

---

### Post by Ken UK on 2011-04-28
A question about drivers if I may.

when I searched in the software centre I have the 'Additional Drivers' ticked but also found one called 'ATi binary X.Org driver', what is the second one? is that the official ATi drivers?

My card is an old one so would it be a bad idea to try it with the other drivers? And if not what do I need to do to switch the drivers without messing things up :D

---

### Post by calavier62 on 2011-05-01
Sorry for the late reply - I volunteered at my local linuxfest, and I wasn't available.

the ATi Binary X.Org Drivers are the ATi Sponsored ones. I would recommend at least trying them and you can do so by installing them in the Software Centre, and running this command.

```
sudo dpkg-reconfigure xserver-xorg
```

I'm not sure if they changed the command, so if this doesn't allow you to change your driver settings (make sure to look through all of the tabs, especially when it comes to special effects)

If the command I gave you didn't work, right click your desktop, and click "Change your Desktop Background". And go to the tab entitled something like Visual Effects. It will automatically search for better drivers, and if it doesn't auto install them as well, there should be a button named "Other Drivers" or something around those lines.

Don't hesitate to give me a shout if I'm wrong. You might want to visit this page:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Ken UK on 2011-05-01
Well I've found my page and it says what I thought it did, my gfx card has been moved to legacy drivers so does that mean the ATi binary ones will work or not? I dont understand what its saying:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

Im going to give it ago and see what happens, Im just worried about breaking my system like always when doing these things lol

Thanks for all the help.

EDIT: ok so I installed using the software centre and run your command, it gave no output so not sure if thats good or bad. I also tried to run 'fglrxinfo'
 after reboot but the output I got was 'Segmentation fault'. It also said I couldn&#8217;t tun Unity and everything was switched off, no effects, dual monitor etc.

Im going to try using CCC.

---

### Post by Ken UK on 2011-05-01
Ok using CCC seemed to have failed. I figured out how to get it running but then failed:

```
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.38-8-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.vMycI7

```

The strange thing is that a couple of times when I have made tweaks in the BIOS the fan has calmed down and stayed calm but if I restart it keeps loud again so there doesn’t seem to be any specific setting that is doing the job just purely change setting and letting it load.

I might have a play about with the graphics card until someone else can come up with a better idea.

---

### Post by Ken UK on 2011-05-16
I've been very busy lately so I'e not had much chance to look at this problem but I have descovered a workaround for it. I boot into the BIOS, swap the PCI-E boot priority (I have 2 ATI cards) and then when it boots up no more loud fan! What I have done is plugged one of each of my monitors into a graphics card so each time I do this I don't need to unplug them instead the screen the computer uses switches lol

I might just try taking each of the cards out 1 at a time and see what happens when I boot.

---

### Post by Mark Phelps on 2011-05-16
When your card is relegated to "legacy" status by ATI/AMD, that means that there are no longer any fglrx drivers that will work with it.  Sorry.

Your best bet is to remove any trace of the fglrx drivers and use the default open-source drivers.  AMD dropped fglrx support for your card years ago.

As to the fan, it's running fast because the card is running hot.  If you FORCE the fan to slow down, all you will do is burn out the card.  Your card -- your money.

---

### Post by Ken UK on 2011-05-18
Yes I thought that was the case so yes I have just stuck with the open drivers which isn't ideal but at least most things work for now.

> **Mark Phelps said:**
> 
As to the fan, it's running fast because the card is running hot.  If you FORCE the fan to slow down, all you will do is burn out the card.  Your card -- your money.

Wrong.

It can't be for a number of reasons:
1. Its not even being pushed nevermind laboured.
2. It does this from a cold start constantly all the time.
3. I don't force anything, I simple switch the boot priority of the two cards and it fixes it temporarily, completely bizare.

---

