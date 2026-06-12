---
title: "VNC screen update problem"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by bav150n on 2006-12-21
I've been trying to get remote desktop working with an Ubuntu Dapper AMD64 machine as a VNC server (standard vino VNC package), and a Windows PC as the VNC viewer. I've had no problems getting the two machines to talk to each other, but I'm seeing selective failure to send framebuffer updates across.

In particular, whenever I drag windows around the screen, or scroll a window, only the newly-uncovered bits of the screen are updated (at least until I hover the mouse over any widgets in the window, which causes them to be redrawn in a slightly different colour and in the correct position). But there are some other peculiarities too, for example, the Applications and System menus always draw correctly, but the Places menu doesn't.

The symptoms are the same with either RealVNC or TightVNC as the viewer on the PC, or indeed using xvncviewer on the Ubuntu box itself, so I suspect the problems are at the server end. But web searches have all drawn blanks. Can anyone suggest anything to help?

---

### Post by RobNY on 2007-01-06
I'm having the same problem on a new Ubuntu install to a machine with an ATI integrated graphics card.  Getting that to work was somewhat of a nightmare, and now I'm having the problems you described with VNC/Vino.  VNC/Vino combo works fine on my other Ubuntu installs.

Running Ubuntu 6.06 fully updated
ASUS A8R-MX Mobo
North ATI RS482
South ULI M1573
ATI Radeon Xpress 200 Onboard Video with ATI (not repository fglrx) driver

---

### Post by achillez on 2007-01-07
I may also be seeing the same problem. I have a ATI Radeon 800XL. I can connect to remote desktop without an issue but when I scroll or/and move a window the window does not refresh. This is a problem that cropped up just recently and I'm not sure what I can do to fix it... any suggestions would be greatly appreciated.

---

### Post by achillez on 2007-01-07
After some searching I think I found the problem. The ATI drivers (fglrx?) are pretty shoddy and don't work well with VNC/vino. The solution is to go back to the xorg OSS drivers. I did this by using: 

sudo dpkg-reconfigure xserver-xorg

You might want to backup your /etc/X11/xorg.conf file first before you do that in case you'd like to go back to the proprietary ATI driver. 

The detailed install information for either driver is at: 

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

and another website link that described the same "ATI" problem with VNC/vino is at: 

[https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/57156](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/57156)

I'm sure glad my new computer has a NVIDIA card and doesn't experience any of these issues. ATI sure seems to be going downhill after AMD's acquisition... or perhaps they always were at the bottom of the hill?

---

### Post by RobNY on 2007-01-07
Well, the dpkg-reconfigure seems to have worked, but I have to say that I'm now very confused.

When I first installed Dapper, the video would not go better than 640x480.  I researched all the ATI stuff and installed the fglrx driver from the repository as shown in the link you supplied.  This driver, however, introduced the "can't reboot/shutdown" problem outlined in other threads.

So, I downloaded the linux drivers from the ATI site and installed it using their installation routine.  That fixed the reboot/shutdown problem, but then vino didn't work.

Now, I ran the dpkg-reconfigure xserver-xorg and selected the ATI drive (which one it actually uses I have no clue) and everything seems to work just fine.

Are three three drivers?   What the heck did I do here?

---

### Post by WinterWeaver on 2007-01-07
I might be flawed in my understanding, so if anyone reads my post and I'm horribly mistaken, please feel free to correct me :)

As I understand there are 3:
1 - The OSS Drivers
2 - The Proprietory Drivers (Official ATI drivers recompiled by the ubuntu developers, for ubuntu)
3 - the ATI Official Drivers

... as I mentioned... I might be mistaken ... awaiting someone with more knowledge to fill us in :)

---

### Post by lukemack on 2007-01-24
I am having the same problem - is anyone aware of a fix for this - other than to uninstall the ATI drivers? has anyone installed vnc-server proper and used that instead of remote desktop sharing?

---

### Post by xaoslaad on 2007-02-11
Try downloading, compiling, and using (or use a package if ubuntu provides one...) x11vnc

I came across this same problem using Fedora Core 6, and it was absolutely horrible to the point of being almost unusable. 

I ended up downloading the source for x11vnc here:
[http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)
doing a ./configure and make to get it working.

You can basically get the same effect as Remote Desktop by entering a line in the Start Up Programs in Sessions under Preferences (give or take; I am using Fedora, so my icons may be in a bit of a different place) to the effect of:
 /usr/local/bin/x11vnc -forever -passwd <your-passwd-to-connect>

x11vnc is working a 100 times better for me in this setup than vino...  hope it gets you some results too, as your post was one of the ones that led me on my merry way to a workaround.

And x11vnc has about as many commandline options as I've ever seen in a program, so if there is an option you want, it probably has it; it's actually what I use on my Sun workstations as Solaris 10 is lacking vino/Remote Desktop in Gnome.

---

### Post by enderox on 2007-02-14
Cheers for the outlining the alternatives. Got the same problem here with the fglrx drivers.

I saw another thread about this issue complaining about ATI drivers. I couldn't win - I'm now ATI, as I couldn't resolve gdm lock up issues with an Nvidia card.


I'm curious to know if anyone has played with FreeNX? I cant remember if that is the name of the free or commercial version - i know there was too forks  one open source, one commercial, utilising the same technology. I'm about to do some seaching now.

---

### Post by lukemack on 2007-02-18
many thanks - x11vnc resolved this problem.

---

### Post by martinitime1975 on 2007-03-26
I also have a resolution, take a look at my response here:  [http://ubuntuforums.org/showthread.php?p=2272306#post2272306](http://ubuntuforums.org/showthread.php?p=2272306#post2272306)

and let me know what you think.

---

