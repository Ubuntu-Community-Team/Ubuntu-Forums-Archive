---
title: "How can I ____ on Ubuntu?"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by Pikzilla on 2009-10-23
Hi there, I recently got fed up with my windows XP getting all screwed up by viruses, and just switched altogether to Ubuntu. My friend helped me with most of the process, but even he is rather new to the software. So, I just have a few questions about how to do a few tasks.

First off, I've installed WINE, which works for most .exes I want to open, but I have not been able to use two major ones: Google chrome and Google talk. Chrome refuses to install, and Talk will actually open, but then not display any text and not let me log in (or close it without using the taskkill panel). How (if at all) can I run these programs?

Second, where do I get the plugins required to operate flash stuff, like video hosting sites?

Finally, where can I manage my hard drives' storage? (I want to format one of them)

Sorry if this is posted in the wrong section, and thank you for your time!

EDIT: Also, one more thing: I realise that this is incredibly unimportant, but I **really** like having icons on my windows applications; any way I can do that?

---

### Post by elliotn on 2009-10-23
for formating use gparted, flash u need flash plugins u can get linux flash staff in the repos or in the site. not everything wox with wine

---

### Post by jeremyswalker on 2009-10-23
First off, welcome to the community. Let's see if I can answer some of your questions.

> **Pikzilla said:**
> Google chrome and Google talk.

Go to this site --> [http://dev.chromium.org/getting-involved/dev-channel]("http://dev.chromium.org/getting-involved/dev-channel"). Scroll down to the Linux section. Click on the link corresponding to your PC architecture. Select to open with Gdebi Package Installer. I don't know about Google Talk.


> **Pikzilla said:**
> Second, where do I get the plugins required to operate flash stuff, like video hosting sites.

Make sure you have installed the "ubuntu-restricted-extras" package. You can find it in "System > Administration > Synaptic". You may also want to install "sun-java6-jre" and "sun-java6-plugin". Also, have a look at --> [https://help.ubuntu.com/community/Multimedia]("https://help.ubuntu.com/community/Multimedia").


> **Pikzilla said:**
> Finally, where can I manage my hard drives' storage? (I want to format one of them)

If you are referring to the management of your partitions, install the package "gparted". Be careful though.

---

### Post by jeremyswalker on 2009-10-23
> **Pikzilla said:**
> EDIT: Also, one more thing: I realise that this is incredibly unimportant, but I **really** like having icons on my windows applications; any way I can do that?

What do you mean by this?

---

### Post by Flingarrows on 2009-10-23
>  					Originally Posted by **Pikzilla** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8155509#post8155509") 				
 				*Second, where do I get the plugins required to operate flash stuff, like video hosting sites.*


 I had real good luck here:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by jbrown96 on 2009-10-23
> **jeremyswalker said:**
> What do you mean by this?

I think he means desktop shortcuts to programs installed by wine. If you go into your home folder and show hidden file (crtl+h) you will find a folder called .wine. Go into that and then drive_c. You should be able to find the .exes to launch your programs. Right click and create a shortcut, then you can move them to the desktop.

Chrome on Linux is still a ways off. You can try the chromium site. There's also a browser called arora that's pretty new. It uses webkit like Chrome and is really fast. Still not as stable as firefox, but probably way more than chrome/chromium will be. You can install it with ```
sudo apt-get install arora
```

---

### Post by Pikzilla on 2009-10-23
Sorry, I wasn't very clear. By icons, I meant the icons corresponding to their respective applications. Do I just need to download the image from the net and assign it to every shortcut I make?
EDIT:
Sorry, I realise how dumb this question sounds, but I really don't know; I see that a lot of solutions involve code. Exactly where is the code typed?

---

### Post by jeremyswalker on 2009-10-23
> **jbrown96 said:**
> Chrome on Linux is still a ways off.

I didn't really care for Chrome the first time I used it (quite awhile ago). However, I tried it again about two weeks ago. I've been using it ever since. I'm quite happy with it. I haven't had any issues. I don't consider it to be "a ways off" at all. IMHO.

---

### Post by eriqjaffe on 2009-10-23
> **jeremyswalker said:**
> I don't know about Google Talk.Pidgin 2.6.x supports Google Talk natively.  IIRC, Jaunty comes with a now-outdated version of Pidgin (2.5.something), but you can keep it up-to-date fairly easily by adding the Pidgin Developers PPA (Personal Package Archive):

[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

That page also has information about how to go about setting the PPA up, as well.

---

### Post by Pikzilla on 2009-10-23
Also, Jememyswalker, I tried the link for Chrome you gave me, but I Ubuntu won't open it, claiming that another software application is running[URL="http://ubuntuforums.org/member.php?u=573956"] (one isn't)
[/URL]

Yay! Fixed!

---

### Post by Pikzilla on 2009-10-23
> **eriqjaffe said:**
> Pidgin 2.6.x supports Google Talk natively.  IIRC, Jaunty comes with a now-outdated version of Pidgin (2.5.something), but you can keep it up-to-date fairly easily by adding the Pidgin Developers PPA (Personal Package Archive):

[https://launchpad.net/~pidgin-developers/+archive/ppa]("https://launchpad.net/%7Epidgin-developers/+archive/ppa")

That page also has information about how to go about setting the PPA up, as well.

Yeah, I saw pidgin, but the reason I need Google talk is for audiochat.
EDIT:
Hey, I hate to be piling on more and more questions, but exactly where do I install Windows applications from a CD directory-wise?

---

### Post by fancypiper on 2009-10-24
> **Pikzilla said:**
> Sorry, I wasn't very clear. By icons, I meant the icons corresponding to their respective applications. Do I just need to download the image from the net and assign it to every shortcut I make?

Right click on the desktop and create a launcher, change the icon with the top left hand button.

---

### Post by shae on 2009-10-24
I have used Empathy for voice chat over google talk and it works fine.  It will also be default in the next version of ubuntu, 9.10.  That will be out really soon (29th of October I believe.)

---

### Post by Pikzilla on 2009-10-24
Hey, I've installed both the flash and java bits which were reccomended, but I can still only see youtube videos.

---

### Post by Pikzilla on 2009-10-24
Bleh... sorry to bump, but...

---

### Post by nothingspecial on 2009-10-24
In your menus go system administration > software sources.

Add these to lines to the sources list.

```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```

Then open a terminal and type
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
```

 then in a terminal type ```
sudo apt-get update && sudo apt-get install chromium-browser flashplugin-nonfree
```

---

### Post by steveneddy on 2009-10-24
I have read the thread up to this point and I think you need to understand one very important part of this equation:

Ubuntu and Linux are NOT Windows. I you need to run Windows applications, then install Windows in a virtual machine (like VirtualBox) and install Linux applications on your Ubuntu box.

I feel that you are going down the wrong path by using Wine for everything Windows when there are Linux variants out there.

You may find with a little education that you really don't need to install your old, buggy Windows applications.

Spend some time learning the strengths and limitations of your new operating system instead of installing everything Windows in Wine.

If you just have to have the Windows application, open it up in the VM.

EDIT:

And please read the links in my sig. They will help you very much.

---

### Post by skompier on 2009-10-24
> **steveneddy said:**
> 
Ubuntu and Linux are NOT Windows. I you need to run Windows applications, then install Windows in a virtual machine (like VirtualBox) and install Linux applications on your Ubuntu box.


I thought the same thing as you. This s a good place to start.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by steveneddy on 2009-10-24
> **skompier said:**
> I thought the same thing as you. This s a good place to start.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Which is the Ubuntu Resources link in my sig.

Great minds.....right?

---

### Post by skompier on 2009-10-24
> **steveneddy said:**
> Which is the Ubuntu Resources link in my sig.

Great minds.....right?

I thought I saw it somewhere..:)

---

### Post by Pikzilla on 2009-10-24
Thanks, I'll start using VirtualBox!
Still, though, I've installed the plugins, but can't use any flash (in FireFox), except for Youtube.

---

### Post by jrox717 on 2009-10-24
did you install the ubuntu-restricted-extras package?

---

### Post by Pikzilla on 2009-10-24
Yup.
UPDATE:
I seem to be able to use some players, like spike TV's, but not others, like Screwattack.com's.

---

### Post by Pikzilla on 2009-10-24
Heh. Sorry to constantly introduce new problems, but gpartition will not recognize one of my hard drives (one that I have not yet formatted). It is set to "on" in the BIOS settings, and is plugged into SATA-2 correctly.

---

### Post by steveneddy on 2009-10-25
> **Pikzilla said:**
> Heh. Sorry to constantly introduce new problems, but gpartition will not recognize one of my hard drives (one that I have not yet formatted). It is set to "on" in the BIOS settings, and is plugged into SATA-2 correctly.

I recommend starting a new thread in the hardware section of the forums for this new issue.

---

### Post by Pikzilla on 2009-10-25
Done, but the flash players are all but broken. Just to elaborate, many players do not work at all, and those which do have various problems, such as a nonmoving slider (the little thing you use to choose which part of the video to go to), and little to no fullscreen support.

---

### Post by fancypiper on 2009-10-25
Have you seen the [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)?

---

### Post by Shpongle on 2009-10-25
to quote linux wizard


Have you installed any codecs ? 


[https://help.ubuntu.com/9.04/musicvideophotos/C/video-playback.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-playback.html)


Use the individual packages to install libdvdcss2 and w32codecs

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


Do you have Flash Player installed ? Go here to check if it is installed and what version
[http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)

---

### Post by Pikzilla on 2009-10-25
> **DillByrne said:**
> to quote linux wizard


Have you installed any codecs ? 


[https://help.ubuntu.com/9.04/musicvideophotos/C/video-playback.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-playback.html)

[COLOR=Red]Yup.[/COLOR]


Use the individual packages to install libdvdcss2 and w32codecs

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[COLOR=Red]Terminal gives me the message:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: You may want to run apt-get update to correct these problems
[/COLOR]


Do you have Flash Player installed ? Go here to check if it is installed and what version
[http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)

[COLOR=Red]Again, yes.[/COLOR]

---

### Post by Pikzilla on 2009-10-25
Just out of wonder, is it even possible to do full screen videos on linux?

---

### Post by sandyd on 2009-10-25
> **Pikzilla said:**
> Just out of wonder, is it even possible to do full screen videos on linux?
just curious.
are you using x64 bit linux or x32 bit

p.s.
installed video drivers yet?
if not, post the output of
```

lspci

```

---

### Post by Pikzilla on 2009-10-25
Wait, video drivers? as in the drivers for my video card? (This just goes to show how much stuff I know about this)

Anyhow, I'm on 32 bit, and the output is:
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)

---

### Post by fancypiper on 2009-10-25
I can play videos full screen.  I use the VLC for all my video, audio and streaming audio.  I am using an nVidia video card.

I haven't read many favorable comments concerning the Intel Corporation Integrated Graphics Controller, though.

---

### Post by Pikzilla on 2009-10-25
Huh, can you use all players?
Also, what's the VLC?

---

### Post by fancypiper on 2009-10-25
All my installed players will play videos full screen.  However, the plugins for firefox embeded players won't play full screen.

[VLC media player]("http://www.videolan.org/vlc/")

---

### Post by Pikzilla on 2009-10-25
Wait, so for instance, would you be able to get fullscreen on, say, Youtube?

---

### Post by sandyd on 2009-10-25
> **Pikzilla said:**
> Wait, video drivers? as in the drivers for my video card? (This just goes to show how much stuff I know about this)

Anyhow, I'm on 32 bit, and the output is:
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
[B]00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)[/B]
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
ive bolded the problem
ubuntu seems to be having some problems with intel cards for the 9.04 release.
a lot of people have been having problems with it for some time now....

read here for possible workarounds. However, you can also just live with no full screen for a few days, until karmic comes out
[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)


however, i strongly advise you to go get either an ATI or Nvidia card. their avalible for pretty cheap these days and can improve your computing experience greatly.

p.s. you can upgrade to karmic right now, but its not recommended cause its currently in beta. but ill still reccomend it because theirs only a few days left to go and download speeds (via web) will be slow due to the large amount of people leaching off the ubuntu download servers.

p.p.s. if your having that slow download problem on release date, try downloading with bittorent.

---

### Post by fancypiper on 2009-10-25
I have to download the flv file and then play it full screen.  As I stated before, I can't play Youtube or any other videos fullscreen from a web browser (yet).

I have played them full screen in the past, but I haven't yet figured out the combination of things I need installed/running in order to do so.

I do think it's probably possible.

---

### Post by sandyd on 2009-10-25
> **fancypiper said:**
> I have to download the flv file and then play it full screen.  As I stated before, I can't play Youtube or any other videos fullscreen from a web browser (yet).

I have played them full screen in the past, but I haven't yet figured out the combination of things I need installed/running in order to do so.

I do think it's probably possible.
p.s. 
you can download them using an firefox extension called flashgot

[http://flashgot.org](http://flashgot.org)

when you go to the youtube page, a "film strip" icon will appear on the right hand buttom corner of the screen.

p.s. seen this many times before, make sure you set the flashgot "download with" settings properly. seen many people wondering why flashgot wasn't working.

---

### Post by Pikzilla on 2009-10-26
Wait, is Karmic the 9.10 version of Ubuntu? How will
it change things in relation to players?

---

### Post by DrugCoder on 2009-10-26
i have a  question of the same kind as the title of the thread.

How can i start my own software or launch files without going to there dir?
EG:
1)i have a file "1.dat"
how can i launch it being a root...(from the root dir)?

2)i have a software, that starts like this: firstly, i have to go to the dir of that soft and then print smth like "./utm5_blabla"
is it possible to make it start from the root? (avoiding going to any other dir.)

Thank you.

---

### Post by nothingspecial on 2009-10-26
Put them in /usr/bin

---

### Post by deancasino on 2009-10-26
> **Pikzilla said:**
> Hi there, I recently got fed up with my windows XP getting all screwed up by viruses, and just switched altogether to Ubuntu.

Good move

> **Pikzilla said:**
> First off, I've installed WINE, which works for most .exes I want to open, but I have not been able to use two major ones: Google chrome and Google talk. 

Pidgin does all of the things that you can do with Google talk and more, set that up for your chatting

---

### Post by sandy8925 on 2009-10-26
I have an Intel card too. To improve performance try this :   

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)


Also, as someone said earlier follow the Comprehensive Multimedia & Video Howto . Most of your problems will be solved. The link is:  

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


You can use pidgin for chatting. Much better than using google talk through wine. In the case of google chrome there's no stable version yet. You can download the beta from the google chrome website. Just go to chrome.google.com in ubuntu and it will give you instructions for installing google chrome. It works well and flash support is also available. 

Yes fullscreen flash video is possible. I find that it works best on firefox 3.5 though. In opera and google chrome it goes slow and the browser is jerky and unresponsive. For best performance TURN OFF COMPIZ. Right click on the desktop select "Change Desktop Background". Then go to the last tab. Select the first option and click OK.

---

### Post by sandy8925 on 2009-10-26
One more thing: the best way to play whatever media files you want is to install mplayer. You can do that through Synaptic or by the following commands :

sudo apt-get update
sudo apt-get install mplayer

The commands have to be typed in a terminal which you can open by:

Applications->Accessories->Terminals

(I typed this in google chrome in ubuntu)

---

### Post by fancypiper on 2009-10-26
I just checked youtube and I can view full screen videos now!

I installed the plugin with

apt-get install flashplugin-nonfree

---

### Post by Pikzilla on 2009-10-26
> **sandy8925 said:**
> One more thing: the best way to play whatever media files you want is to install mplayer. You can do that through Synaptic or by the following commands :

sudo apt-get update
sudo apt-get install mplayer

The commands have to be typed in a terminal which you can open by:

Applications->Accessories->Terminals

(I typed this in google chrome in ubuntu)


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A5F29D81AC9980


I've been getting this a lot lately when I try to do things in terminal. Any suggestions?

---

### Post by Rayve on 2009-10-26
Not certain if this will fix the pubkey issue, but you can also go to System > Administration > Synaptic Package.  Enter your password, then search for the package you'd like, "mplayer" in this instance.  When you find it, click on the box next to it and "Mark for install".  Synaptic will let you know of any other dependencies mplayer needs which you don't yet have, allow it to mark those for install as well, and then "Apply".  

I believe that is the same as "apt-get" from the terminal.

---

### Post by Pikzilla on 2009-10-26
Huh. any idea why it wouldn't let me in Terminal?

---

### Post by Pikzilla on 2009-10-26
Okay, I just read up on Karmic. So will Ubuntu 9.10 resolve my video card issues and let me use flash?

---

### Post by fancypiper on 2009-10-26
I don't know as I don't have your hardware. You will have a better chance of having more hardware support.  mplayer is currently broken, but I am waiting for the final release before I submit a bug on it.

---

### Post by jeremyswalker on 2009-10-27
Your GPG error is because you didn't add the signing key for one of your PPA sources. Go to the site of the PPA you added. Expand the technical details section. Note the signing key (i.e. 1024R/4E5E17B5). Open a terminal (Applications > Accessories > Terminal). Enter the following: (Replace 4E5E17B5 with that associated with the proper PPA)
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com **4E5E17B5**
```
That should stop that error.

---

### Post by Pikzilla on 2009-10-28
I'm sorry, _how_ do you find the site of the PPA source? Yeah, I realize that the answer is probably gonna end up being really obvious and easy...

---

### Post by jeremyswalker on 2009-10-29
One way that I can think of would be to look at the file **/etc/apt/sources.list**. You will be looking for an entry with [http://ppa.launchpad.net/](http://ppa.launchpad.net/) in it. Once you find it, note the first sub-directory of the link (i.e. [http://ppa.launchpad.net/](http://ppa.launchpad.net/)**some-name**/ppa/ubuntu). Then, go to [https://launchpad.net/ubuntu/+ppas]("https://launchpad.net/ubuntu/+ppas") and search for it.

---

### Post by Pikzilla on 2009-10-29
Alright, y'now what? I started this thread with a crapload of issues, and Karmic Koala has fixed _every single one of them!_
Thank you all so much for all your help.

---

