---
title: "Running Windows 7 and Ubuntu on one PC and two monitors"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by smiller85 on 2011-05-23
Okay I am very new to Ubuntu, but I plan on using it for various research.

I have downloaded and installed Ubuntu 11.04 onto an external hard drive (ehd) that I pulled from a second laptop where the motherboard fried up on.  I can easily press F9 on my laptop and boot from the ehd. 

What I would like to do is have the windows 7 on my internal hard drive load up and then have ubuntu boot from the ehd on a second monitor and just use one mouse and keyboard between both of them.  The idea is that I can still use windows 7 on my laptop monitor, but then scroll the mouse over to an extra monitor and be able to use ubuntu.  

Is this possible? If buying an extra keyboard and mouse is needed I could do that, but buying another computer at the moment is out of the question as I don't have the money to buy another computer. :(

---

### Post by mikewhatever on 2011-05-23
No, you can't boot two OSs on the same computer at the same time. That said, check out Virtual Box. Installing Ubuntu is a virtual environment will let you run the two OSs at the same time.

---

### Post by heyandy889 on 2011-05-23
Hello! Welcome to the forums. :-D

I'm not sure that what you're proposing is possible. You would be sharing memory and the CPU between two operating systems. Seems complicated.

Simpler would be installing VirtualBox, installing Windows on the VirtualBox, and dragging the virtual box over to the right monitor. The host operating system would be Ubuntu, and the "guest" operating system would be Windows.

Maybe that would work?

edit: Here's a video, illustrating the use of VirtualBox
[http://www.youtube.com/watch?v=aMtt83piRdo](http://www.youtube.com/watch?v=aMtt83piRdo)

---

### Post by Mark Phelps on 2011-05-24
Understand ... that in order to have a Virtual installation of Win7, you will required full installation media (i.e., a DVD) -- which you probably do NOT have if your PC came preinstalled with Win7.

So, the OTHER approach you might consider is installing Virtualbox in Win7 and installing Ubuntu as the virtual OS.

You'll end up with much the same results -- two OSs that you can use.

---

### Post by smiller85 on 2011-05-26
So I have windows 7 on my internal hard drive.  I installed ubuntu on my external hard drive.  Will the Virtual box work with starting windows 7 and having ubuntu as the virtual OS running from the external hard drive?  Is that what you mean by "full installation media"?  

If not I have no problem just switching back and forth by rebooting from the USB connected external hard drive, just thought it would be a bit easier if I could have both at the same time.

Also, sorta unrelated to this is the fact that my touchpad works almost fine in Ubuntu on my laptop.  I can right and left click and two finger scroll, I just cant drag anything unless I use the very very bottom part of the touchpad where the the mouse buttons are located.  It is all combined into one area, it is not separate buttons.  I was hoping that running them at the same time would just solve the problem as well.  (this is a completely different problem, I tried searching for an answer, but can't seem to find one that has been confirmed to still have right and left click, two finger scrolling and a click and drag feature.  Ill keep looking on the forum).

---

### Post by heyandy889 on 2011-05-26
"Full installation media" means the CD and license number for Windows. If you buy Windows from the store or from the Internet, you get this license number. You won't have the number if Windows was pre-installed on your laptop. Maybe that helps?

Here's what I would try. Boot into Windows 7 on your internal hard drive. Visit [http://www.virtualbox.org/](http://www.virtualbox.org/) and download VirtualBox for Windows. The .exe is 79.5MB, so might take a few minutes to download. Once the download is finished, double click the .exe to install VirtualBox.

Once VirtualBox is opened, you can create a new "virtual machine" that runs inside of Windows. A guide for that is here [http://www.virtualbox.org/manual/ch01.html#gui-createvm](http://www.virtualbox.org/manual/ch01.html#gui-createvm)

Good luck, dude!

---

### Post by gamendorf on 2011-05-26
I'm running a similar setup, and found that the best situation (for me at least) is to install Ubuntu on my laptop, and then run Windows Vista in VMWare.  I can maximize Vista on Desktop two, and then display it on my external monitor.  It is also a nice set-up on the go because it is so easy to switch between desktops in Ubuntu.  I chose VMWare over VirtualBox because it passes hardware/network better (at least it does on my laptop).

Many computer manufacturers install a recovery program inside windows.  From it, you can burn bootable DVDs.  The name and location of the program depend on the manufacturer.  
Here are the steps I used:
1. Use a good key-finder program for windows 7 to find you Product Key. [This article]("http://pcsupport.about.com/od/productkeysactivation/tp/topkeyfinder.htm") has a list of them.
2. Create you Windows 7 boot discs using the built in recovery program. (If it exists)  Google your machine to find out more.
3.  Use an Ubuntu live-cd and install Ubuntu.
4.  Download [VM-Ware Player]("http://downloads.vmware.com/d/info/desktop_downloads/vmware_player/3_0") and install. (You will have to register to download it. It could also be available via the Software Manager. I'm on a Windows box at work and can't check right now.)
5.  Start VMWare an use your DVD's to install Windows.
6.  Send VMWare to desktop 2, maximize it, and project it on your external monitor

Violia! Two OS on two monitors running off the same machine.

---

