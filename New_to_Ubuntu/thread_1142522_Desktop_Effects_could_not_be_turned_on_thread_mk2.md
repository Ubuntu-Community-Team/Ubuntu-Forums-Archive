---
title: "Desktop Effects could not be turned on thread mk2"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Kattnip on 2009-04-29
Howdy guys, 

I'm completely new to this, a few of my friends are running ubuntu and I was going to reinstall XP  today when I realised I'm no longer running any programs that I couldn't use on  linux so, I borrowed and installed ubuntu.

Version history:
The install CD I used installed 7.something, I think it was called Gutsy Gibbon.
I used the auto update thing I now have the Hardy Heron (great names eh?)

I was told one of the things I might like to play round with for starters was the desktop effects, when I try to put anything on, I get the error msg: effects could not be turned on.

I trawled he forum for a while and looked but my lack of familiarity with the jargon's got me pretty lost.



This seems like it might help in advance:
"Could you tell us what video card you have? If you don't know, type the following into a terminal:
Code:
lspci
and paste the output here."


Output: 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
killkat@HalKat:~$ 


The computer I'm using has an integrated video card on the motherboard, but it also has a Nvidia GeForce 7300 as well.

Cheers guys, any help much appreciated in advance.

---

### Post by 3rdalbum on 2009-04-29
Go to System > Administration > Hardware Drivers and tell us what it says. It should offer to install a graphics card driver; if it doesn't, you might need to go into Synaptic Package Manager and click the Reload button first.

---

### Post by Kattnip on 2009-04-29
> **3rdalbum said:**
> Go to System > Administration > Hardware Drivers and tell us what it says. It should offer to install a graphics card driver; if it doesn't, you might need to go into Synaptic Package Manager and click the Reload button first.

I went into the synapic packages manager and reloaded. 

System > Administration > Hardware Drivers
I still get :
"no proprietry drivers ae in use on this sytem"

cheers

---

### Post by 3rdalbum on 2009-04-29
Okay, that's odd. Try going to the hardware drivers manager after going to System > Administration > Software Sources and checking that main, universe, restricted and multiverse repositories are all ticked.

If that doesn't work, you can download your graphics card driver from [www.nvidia.com](www.nvidia.com). That will unfortunately require some raw command-line use (Nvidia's engineers don't make a nice easy installer).

There is a howto here: ([http://tuxicity.wordpress.com/2008/06/04/howto-install-nvidia-manually-in-ubuntu-and-debian/](http://tuxicity.wordpress.com/2008/06/04/howto-install-nvidia-manually-in-ubuntu-and-debian/))

Bear in mind whenever it tells you to use "sudo" with a command, you put the word "sudo" in front of it, like this:

```
sudo gdm
```

The driver linked to in that post is rather old, so grab the latest one for your card from the Nvidia website.

---

### Post by tarps87 on 2009-04-29
> **Kattnip said:**
> 
The computer I'm using has an integrated video card on the motherboard, but it also has a Nvidia GeForce 7300 as well.


3rdalbum's post should solve it, but just to be clear which card is the monitor plugged into?

> **Kattnip said:**
> 
I used the auto update thing I now have the Hardy Heron (great names eh?)


Don't forget the next two, Intrepid Ibex and Jaunty Jackalope.
And the next release Karmic Koala, I wanted Killer Koala ;)

Edit: Just see the last two posts, if it doesn't tell you it needs to update the package list try typing this in the terminal
```
sudo apt-get update
```
I'm quite sure the 7 series cards are supported

---

### Post by Kattnip on 2009-04-29
Cheers bro, am trying this now, its all taking me ages and it's a little bit frustrating (I'm having trouble figuring out how to install dl'd software... :p) but quite fun playing round with something completely new.

---

### Post by Kattnip on 2009-04-29
> **tarps87 said:**
> 3rdalbum's post should solve it, but just to be clear which card is the monitor plugged into?


Its plugged into the Nvidia card.

> **tarps87 said:**
> 
Edit: Just see the last two posts, if it doesn't tell you it needs to update the package list try typing this in the terminal
```
sudo apt-get update
```I'm quite sure the 7 series cards are supported

I've done that and there still seems to be no change (desktop effects cannot be enabled)

Am I right in thinking with my current video card I should be able to enable video effects and that something (the viedo card driver) isnt installed correctly?

---

### Post by Kattnip on 2009-04-29
I've been trying to work through this ([http://tuxicity.wordpress.com/2008/06/04/howto-install-nvidia-manually-in-ubuntu-and-debian/](http://tuxicity.wordpress.com/2008/06/04/howto-install-nvidia-manually-in-ubuntu-and-debian/)) for the last 20 min or so (have successfully DL'd driver) and I honestly have no idea what any of this means . . . 

fail?

---

### Post by tarps87 on 2009-04-29
> **Kattnip said:**
> I've done that and there still seems to be no change (desktop effects cannot be enabled)

Am I right in thinking with my current video card I should be able to enable video effects and that something (the viedo card driver) isnt installed correctly?

The desktop effects should work with your card, after doing this do you go to System -> administration -> restricted drivers?

If there is nothing there there try installing the downloaded driver.

> **Kattnip said:**
> I've been trying to work through this ([http://tuxicity.wordpress.com/2008/06/04/howto-install-nvidia-manually-in-ubuntu-and-debian/](http://tuxicity.wordpress.com/2008/06/04/howto-install-nvidia-manually-in-ubuntu-and-debian/)) for the last 15 min or so (have successfully DL'd driver) and I honestly have no idea what any of this means . . . 

fail?

I have tried to edit the tutorial so it make more seance, or I hope it does:

Type the following in the terminal:
This will install the need tools
```
apt-get install build-essential linux-headers-`uname -r` 
```

*Assuming you have not installed any restricted drivers (I believe that you haven't) you don't need to do the middles step so I have removed it*

Press ctrl+alt+F1

now login using you username and password

Type the following, this will kill the x session (Graphical session)
```

sudo killall gdm
```

backup xorg.conf (note that Linux is case sensitive)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bck
```

now type this to install the driver. The example assumes you have downloaded the file to your Desktop
```

sudo chmod a+x ~/Desktop/NVIDIA-Linux-x86-173.14.05.pkg1.run
sudo sh ~/Desktop/NVIDIA-Linux-x86-173.14.05.pkg1.run

```

When the installer asks if it should edit your xorg.conf choose yes (make sure you have your xorg.conf backed up!! (Done above))

```
sudo gdm
```
or if this doesn't work
```
sudo reboot
```

If you do not get a graphical session any more
```
sudo cp /etc/X11/xorg.conf.bck /etc/X11/xorg.conf
```
followed by
```
sudo reboot
```
This will remove the Nivdia driver from the confg

---

### Post by ajgreeny on 2009-04-29
Just a quick thought;  do you need to disable the onbpard graphics in your BIOS to get the nvidia card working properly?  I seem to remember reading something about this in the past.  Try it out and see if it makes any difference.

---

