---
title: "A few quetsions..."
date: 2010-03-14
forum: New to Ubuntu
---

### Post by bigseb on 2010-03-14
Right, so I want to try out Ubuntu but am really confused, mainly 'cos its so different from Windows. So I downloaded the guide that's linked in the sticky but it doesn't give me answers to a few crucial questions. Could someone please answer the following:
 
1) My software isn't useless (surely) if I make the switch... how about all my drivers? Can I use my windows drivers? 
 
2) Will the performance of my hardware be less than with windows? By that I mean will for eg. my graphics card not perform as well with Linux drivers as with windows drivers?
 
3) Compatibility... any thing I need to know?
 
4) My windows is Windows 7 x64. Is there an equivalent Ubuntu?
 
I should point out that the guide I downloaded is in PDF format but the Ubuntu install disc I have has no PDF reader on it. Bit of an over-sight that, meaning that once Ubuntu is installed I can't read the guide. Will Adobe install? 
 
More to come...
 
Thanks!

---

### Post by bigseb on 2010-03-14
I see I made poo-poo with the title... sometimes I dyslexic am

---

### Post by crlang13 on 2010-03-14
In response to one of your questions... :p

Ubuntu 9.10 has a 64 bit option.  10.04 is coming out towards the end of April as well and is going to be pretty whiz bang.

The guide you refer to is the Ubuntu Pocket Guide found here? [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

I haven't had any problems with PDFs, but I didn't attempt to view any until after I installed and updated...  What version of Ubuntu was your live CD?

---

### Post by n0dix on 2010-03-14
1) No, your Windows driver don't be use in Ubuntu. Maybe the wireless driver yes.
2) This is not for GNU/Linux or Ubuntu problem but for manufacturers who don't support Linux systems.
3) You have to provide your system spec, but in general you shouldn't have any problem.
4) Yes, Ubuntu/Kubuntu/Xubuntu 64bits.

---

### Post by carlosgs91 on 2010-03-14
.

---

### Post by BrockStrongo on 2010-03-14
1) My software isn't useless (surely) if I make the switch... how about all my drivers? Can I use my windows drivers? 
A) Most of your software will be useless. Some apps will run using wine, others will need vmware player or virtual box running some windows version. You will not be using the windows drivers. 
 
2) Will the performance of my hardware be less than with windows? By that I mean will for eg. my graphics card not perform as well with Linux drivers as with windows drivers?
 A) Most graphics cards have an open source driver for linux, or a proprietary linux driver developed by the company that made the graphics card. Google it and see what comes back.  

3) Compatibility... any thing I need to know?
    You will need to download "ubuntu restriced extras" for mp3, avi, mpg, mp4, flash. etc etc
You will also need to download the linux flash player from adobe. Itunes will not run in linux. It will run in a virtual machine. however rhythmbox can handle your ipod quite nicely. Some printers have difficulty running in linux. Cannon especially. But, with a little patience and CUPS (common unix printing system) you can get pretty much any printer running.
 
4) My windows is Windows 7 x64. Is there an equivalent Ubuntu?
   Like everyone else said ubuntu 64.

Why don't you post your hardware specs here and I or someone else will be able to give you an idea of what you will have to do. I  installed it in place of vista on an acer intel core2 duo, with intel graphics and everything worked out of the box.
I don't want to scare you off, but this is stuff that I would have liked to know prior to switching. However switching was the best thing I ever did. My computer now does what I want, when I want without the worry of viruses, a hell of a lot faster, more stable, and for free.

---

### Post by J V on 2010-03-14
> **bigseb said:**
> 1) My software isn't useless (surely) if I make the switch... how about all my drivers? Can I use my windows drivers? You can't use windows drivers. There are plenty of linux drivers and they are almost all built in. Wireless drivers and some windows programs can be made to work on linux though...
 
> 2) Will the performance of my hardware be less than with windows? By that I mean will for eg. my graphics card not perform as well with Linux drivers as with windows drivers?It has less to do with drivers and more with software. Vista probably has better drivers than karmic, but compiz is so much better written that visual effects are 50 times faster and smoother than in vista.
 
> 3) Compatibility... any thing I need to know?Applications: Need lots of work (Install playonlinux)
Filesystems/network: Will work perfectly
Hardware: Depends, wireless and ATI cards are the main agressors, but the rest should work
> **BrockStrongo said:**
> You will need to download "ubuntu restriced extras" for mp3, avi, mpg, mp4, flash. etc etc
You will also need to download the linux flash player from adobe. **64-bit is in alpha, but still better than the 32 bit, so use that one** Itunes will not run in linux. **Itunes 7 will in wine (again, playonlinux)** It will run in a virtual machine. however rhythmbox can handle your ipod quite nicely. Some printers have difficulty running in linux. Cannon especially. But, with a little patience and CUPS (common unix printing system) you can get pretty much any printer running.
 
> 4) My windows is Windows 7 x64. Is there an equivalent Ubuntu?Yeah, ubuntu x64 :P Latest version is karmic koala, you download it by default
 
> I should point out that the guide I downloaded is in PDF format but the Ubuntu install disc I have has no PDF reader on it. Bit of an over-sight that, meaning that once Ubuntu is installed I can't read the guide. Will Adobe install?There is a pdf reader by default... I don't know why its not working for you... Try opening it in firefox next time?

---

### Post by dyingsun on 2010-03-14
There are pdf readers in the repos. Evince, I think is one of them.

Also, OpenOffice. A must have on any linux system!

---

### Post by bigseb on 2010-03-18
Wow!!! Thanks for all your replies!!!
 
Ok you have answered a LOT! So, just to fill you in:
 
Windows/general software: Workwise its your basic CADCAM software ie Solidworks, Rhino (Iknow those definitely won't work), EZCam and Powermill. Playwise its games, mainly FPS and RTS. Never thought of using Virtualbox (or whatever its called) to run software. Must try that.
 
I really need my modem to work. Its a Hauwei E220. Its seems the net is a MUST for Linux. Any tips and tricks on that?
 
My system specs currently: Core 2 Duo 1,5 GHz, 4Gb RAM, running Windows 7 Ultimate x64. The Ubuntu version I have here is the 9.10 x64 (it says 2.4 Ultimate Edition when I start it up).
 
Driver-wise: I found the driver for Graphics Card (Geforce 8400) on the Nvidia website. I downloaded it but have no idea how to install the silly thing. Grrrrrrr....
 
Keep the ideas flowing. I REALLY appreciate all your help!
 
PS: does one have to know code for Linux? That is my weak point at the moment.
 
One last thing: how does this wubi business work ? It says to restart so I do that and it runs from the disc. When done there is a 'install Ubuntu' desktop icon. This totally overwrote my window installation on Friday evening (GRRRRRRRRR). I thought wubi was some kind of dual boot?!?!

---

### Post by howefield on 2010-03-18
> **bigseb said:**
> I found the driver for Graphics Card (Geforce 8400) on the Nvidia website.

You'll get a driver from System > Administration > Hardware drivers, I have the same card and it works perfectly. No need for downloading drivers from Nvidia, unless you have a specific reason for it.
 
> PS: does one have to know code for Linux? That is my weak point at the moment.

You won't need to code anything and you won't need to use the terminal either which is what I suspect you mean, if you don't want to. At least, the need for the terminal will be very minimal, although it is often the quickest way of getting something done.

---

### Post by Calash on 2010-03-18
For the Nvidia card, try the built-in drivers first.  It should show up under System->Administration->Hardware Drivers

While they will not be as new as the ones you download from the website you will avoid the issue of having to recompile the drivers when you get a kernel update.  Not a huge deal to do with NVIDIA, but to start out it is safer to stick with what is available.


You do not need to know code.  You don't even need to touch a terminal if you stick with what is available in the Software Center (Applications->Software Center).  Over time you will want to learn the terminal as it is a great tool and lets you really experience the Operating System.

---

### Post by MelDJ on 2010-03-18
> **bigseb said:**
> 
One last thing: how does this wubi business work ? It says to restart so I do that and it runs from the disc. When done there is a 'install Ubuntu' desktop icon. This totally overwrote my window installation on Friday evening (GRRRRRRRRR). I thought wubi was some kind of dual boot?!?!

wubi installs ubuntu as an application inside windows. you can pick between them at startup.
i dont know how you overwrote your windows though because no partitioning is involved

---

### Post by J V on 2010-03-18
> **bigseb said:**
> Playwise its games, mainly FPS and RTS.TONS of them for linux, don't bother trying to get the windows ones working... (Nexuis is being ported to ps3 and xbox, cool huh?)

> Never thought of using Virtualbox (or whatever its called) to run software. Must try that.Don't bother, have to buy professional or higher license which means pay 300 bucks and get shafted with slow non-3d games... If you install playonlinux it will let you play games in 3d, sometimes even faster than windows, but the question is, will it work? Theres a 50/50 chance nowadays...
 
> I really need my modem to work. Its a Hauwei E220. Its seems the net is a MUST for Linux. Any tips and tricks on that?Its external (In its own box?)? Then its easy, just configure it through the browser like you would do with windows...
 
> My system specs currently: Core 2 Duo 1,5 GHz, 4Gb RAM, running Windows 7 Ultimate x64. The Ubuntu version I have here is the 9.10 x64 (it says 2.4 Ultimate Edition when I start it up).Ultimate edition isn't strictly ubuntu, its a derivative...
 
> Driver-wise: I found the driver for Graphics Card (Geforce 8400) on the Nvidia website. I downloaded it but have no idea how to install the silly thing. Grrrrrrr....Stop thinking windows, you never have to download something from a website on linux... if the driver will work, it is in geany (system > administration > hardware drivers), that will do it for you automatically (download AND install ;))
 
> PS: does one have to know code for Linux? That is my weak point at the moment.Nah, if someone gives you something and tells you to type it into a terminal, you just copy paste (and its much easier than explaining a GUI), but bash scripting is really fun and easy, and you can get into all sorts of stuff with that :)
 
> One last thing: how does this wubi business work ? It says to restart so I do that and it runs from the disc. When done there is a 'install Ubuntu' desktop icon. This totally overwrote my window installation on Friday evening (GRRRRRRRRR). I thought wubi was some kind of dual boot?!?!It is... was... you needed to take the CD out of the drive... but if you already wiped your windows out, so it installed the "Real" ubuntu now.

---

### Post by bigseb on 2010-03-19
Re-installed Ubuntu... overwrote everything. This time on purpose though. Currently surfing the web on my brand new linux OS and felling mightily chuffed

*smug grin*

---

### Post by 3rdalbum on 2010-03-19
As you've already guessed, the E220 mobile broadband modem works out-of-the-box :-)

---

### Post by bigseb on 2010-03-19
Well... kinda. My connection is real slow so it seems as if its defaulted to GPRS rather than 3G/HSDPA. How do I fix that?

Plus, How do install this graphics card driver?!?! File name is 'NVIDIA-Linux-x86_64-190.53-pkg2.run'. It is pasted on my desktop.

Thanks

---

### Post by MelDJ on 2010-03-19
go to applications-accesories-terminal and type:
```
sudo sh
```

then drag and drop the file into the terminal and press enter

---

### Post by bigseb on 2010-03-19
I'll try that right now. Ta.

---

### Post by 3rdalbum on 2010-03-19
> **bigseb said:**
> Well... kinda. My connection is real slow so it seems as if its defaulted to GPRS rather than 3G/HSDPA. How do I fix that?

It will switch between the two methods based on connection quality. Unfortunately mobile broadband isn't very good, you will often see dropouts and dropbacks if you're in an area of low signal strength. Regardless of operating system, I might add.

> Plus, How do install this graphics card driver?!?! File name is 'NVIDIA-Linux-x86_64-190.53-pkg2.run'. It is pasted on my desktop.

It can be done, but you don't want to do it that way. Nvidia's engineers are good at writing drivers, but useless at writing installers. The Nvidia driver installer is pretty horrid, requires you to turn off your graphical mode before running the installer, and doesn't use DKMS so you need to reinstall the driver every time you recieve a kernel update.

There are two good ways of installing the Nvidia driver.

1. Go to System > Administration > Hardware Drivers. Ubuntu will detect your Nvidia graphics card and offer to download and install an Nvidia driver for you. This driver has been tested on Ubuntu and is as well supported as you can expect. Once installed, it will **never need to be reinstalled after a kernel update**. Only thing is that this driver is a little bit older - its version is 185.

2. If you want the latest drivers (190 and 195), you can add a *PPA*, which is a small repository that offers more packages for you to install from your package manager. If you ever want more up-to-date software than is available in your package manager, go and look on Google for a PPA.

You can add the unofficial Nvidia driver PPA by going into the terminal and typing this command*:

```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update
```

When that's done, you'll be able to use Synaptic to install the "nvidia-graphics-drivers-190" package, which **will keep in sync with your kernel updates** and never need to be reinstalled.

EDIT: MelDJ's suggestion is good, but it doesn't work for the Nvidia driver installer because of what I said about how horrid the installer is ;-)

*I usually give instructions using the GUI, but it's much quicker and neater to use the terminal for this.

---

### Post by bigseb on 2010-03-19
> **3rdalbum said:**
> It will switch between the two methods based on connection quality. Unfortunately mobile broadband isn't very good, you will often see dropouts and dropbacks if you're in an area of low signal strength. Regardless of operating system, I might add.



It can be done, but you don't want to do it that way. Nvidia's engineers are good at writing drivers, but useless at writing installers. The Nvidia driver installer is pretty horrid, requires you to turn off your graphical mode before running the installer, and doesn't use DKMS so you need to reinstall the driver every time you recieve a kernel update.

There are two good ways of installing the Nvidia driver.

1. Go to System > Administration > Hardware Drivers. Ubuntu will detect your Nvidia graphics card and offer to download and install an Nvidia driver for you. This driver has been tested on Ubuntu and is as well supported as you can expect. Once installed, it will **never need to be reinstalled after a kernel update**. Only thing is that this driver is a little bit older - its version is 185.

2. If you want the latest drivers (190 and 195), you can add a *PPA*, which is a small repository that offers more packages for you to install from your package manager. If you ever want more up-to-date software than is available in your package manager, go and look on Google for a PPA.

You can add the unofficial Nvidia driver PPA by going into the terminal and typing this command*:

```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update
```When that's done, you'll be able to use Synaptic to install the "nvidia-graphics-drivers-190" package, which **will keep in sync with your kernel updates** and never need to be reinstalled.

EDIT: MelDJ's suggestion is good, but it doesn't work for the Nvidia driver installer because of what I said about how horrid the installer is ;-)

*I usually give instructions using the GUI, but it's much quicker and neater to use the terminal for this.

Thanks 3rdalbum.

The signal here is great. I'm flip flopping between my PC (Ubuntu) and my wife's (Windows 7)... on her PC the modem is mighty quick. Very decent speeds. On mine its really slow. I thought maybe there's a setting to tweak. Ho hum...

Re the drivers: System ---> Admin ---> Hardware drivers show no entries!? I hope to use your other method later. Hopefully I can cut and paste (and hopefully its really straight forward) cause I'm a-itchin' for some CnC3...

Gotta fetch wifey now. I'll update later.

TTFN

---

### Post by MelDJ on 2010-03-19
> **3rdalbum said:**
> 
EDIT: MelDJ's suggestion is good, but it doesn't work for the Nvidia driver installer because of what I said about how horrid the installer is ;-)

.

ati user here ;)

---

### Post by bigseb on 2010-03-19
> **3rdalbum said:**
> It will switch between the two methods based on connection quality. Unfortunately mobile broadband isn't very good, you will often see dropouts and dropbacks if you're in an area of low signal strength. Regardless of operating system, I might add.



It can be done, but you don't want to do it that way. Nvidia's engineers are good at writing drivers, but useless at writing installers. The Nvidia driver installer is pretty horrid, requires you to turn off your graphical mode before running the installer, and doesn't use DKMS so you need to reinstall the driver every time you recieve a kernel update.

There are two good ways of installing the Nvidia driver.

1. Go to System > Administration > Hardware Drivers. Ubuntu will detect your Nvidia graphics card and offer to download and install an Nvidia driver for you. This driver has been tested on Ubuntu and is as well supported as you can expect. Once installed, it will **never need to be reinstalled after a kernel update**. Only thing is that this driver is a little bit older - its version is 185.

2. If you want the latest drivers (190 and 195), you can add a *PPA*, which is a small repository that offers more packages for you to install from your package manager. If you ever want more up-to-date software than is available in your package manager, go and look on Google for a PPA.

You can add the unofficial Nvidia driver PPA by going into the terminal and typing this command*:

```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update
```When that's done, you'll be able to use Synaptic to install the "nvidia-graphics-drivers-190" package, which **will keep in sync with your kernel updates** and never need to be reinstalled.

EDIT: MelDJ's suggestion is good, but it doesn't work for the Nvidia driver installer because of what I said about how horrid the installer is ;-)

*I usually give instructions using the GUI, but it's much quicker and neater to use the terminal for this.

Tried that code business. Copied the code into the terminal, then it asks me for my Password but when I type nothing happens :(

---

### Post by MelDJ on 2010-03-19
> **bigseb said:**
> Tried that code business. Copied the code into the terminal, then it asks me for my Password but when I type nothing happens :(

thats normal. as you type, the password will be invisible. just type the password and press enter

---

### Post by bigseb on 2010-03-19
> **MelDJ said:**
> thats normal. as you type, the password will be invisible. just type the password and press enter
My bad, got it now. Now to the synaptic thing, there are plenty options starting with Nvidia... do I just click on them all? There is no option titled 'nvidia-graphics-drivers-190' as suggested by 3rdalbum.

---

### Post by bobin on 2010-03-19
download nvidia-185-kernel-source. That should be enough for the graphics drivers.

---

### Post by bigseb on 2010-03-19
IT WORKED!! 

Thanks to all you guys n gals that chipped in!! Y'all have won my eternal love and devotion.

The Seb, he like!!

---

