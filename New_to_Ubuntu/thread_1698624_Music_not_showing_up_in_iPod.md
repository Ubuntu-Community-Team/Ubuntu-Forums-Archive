---
title: "Music not showing up in iPod"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by lou002 on 2011-03-02
So I'm able to get my iPod Touch 4th gen to mount in 10.10, and to show up in Rhythmbox. I've tried gtkpod or w/e it's called. Also tried Banshee already. I can't get my music onto the product. All say it successful syncs, but when I go to the music, there's nothing there. I also get the error in the screen shot that I attached.

Here's what I get when I type ```
lsusb
``` : 

> Bus 002 Device 005: ID 05ac:129e Apple, Inc. 
Bus 002 Device 004: ID 04f2:b1d8 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 046d:c05a Logitech, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


All I want is to sync my music without having to use the parental units machine all the time. Any simple help because I'm admittable new to Ubuntu, having just switched full time.

---

### Post by ironic.demise on 2011-03-02
If you've just switched here's my suggestion:
Download Virtualbox from their site (The open source one isn't as featured as their closed source one, so get the closed source one)
Install it
Install Windows onto it
Install an ipod manager in Windows
Get your music onto the windows OS via USB or shared folders...
mount the IPOD in Windows.

---

### Post by lou002 on 2011-03-02
> **ironic.demise said:**
> If you've just switched here's my suggestion:
Download Virtualbox from their site (The open source one isn't as featured as their closed source one, so get the closed source one)
Install it
Install Windows onto it
Install an ipod manager in Windows
Get your music onto the windows OS via USB or shared folders...
mount the IPOD in Windows.


While I appreciate that idea, I do not have a Windows OS CD at my home and I'm not about to pirate it.

Thank you for your constructive help though.

---

### Post by Th3W1z4rD on 2011-03-02
I don't have an iPod to test this on but I was able to find this [help article]("https://help.ubuntu.com/community/PortableDevices/iPhone") on ubuntus website. It seems the newest iOS requires an updated file. 

Hope this helps.

---

### Post by lou002 on 2011-03-02
So I just opened my iPod up as a file folder and found out that there IS music on it, but it's simply not showing up on the physical device.

And some of the music is named "libgpod284497.mp3" for example. 

I hope that new information helps!

---

### Post by Th3W1z4rD on 2011-03-02
Ah I see. It's using the iPod as external storage device. kinda like a flash drive. Unfortunately the only other method I know of syncing the device to actually be able to see the music on the device is to use iTunes or Winamp. both of which we don't have access to lol. 

If you do figure it out please let us know.

---

### Post by panderohit on 2011-03-02
> Download Virtualbox from their site (The open source one isn't as  featured as their closed source one, so get the closed source one)
 Install it
 Install Windows onto it
 Install an ipod manager in Windows
 Get your music onto the windows OS via USB or shared folders...
 mount the IPOD in Windows.in support of ironic.demise (post #2 in this thread). I installed Windows 7 in a Virtualbox downloaded from their website. Then I had to tinker a bit to enable the usb-connections. Once set, I downloaded iTunes and synced my iPod from there and it works *perfectly*.

I tried using Rhythmbox and gtkpod but received limited success from all. In the case of Rhythmbox, only the .mp3 files and the .mov files would sync but none of the others.

The problem was the same with gtkpod. However most of my music and video files were in .m4a and .mp4 format and none of these software would recognise it. However through iTunes it worked beautifully. The only hitch was that it was extremely slow. It took more than double the time it normally takes on Windows Vista, but I am not complaining. It saves me the trouble of dual booting and being unable to use Ubuntu while managing my iPod.

However, it is necessary to have a Windows Installation Disk ready for installing the OS in virtualbox. I was lucky as I got Windows 7 pre-installed in my laptop and received the disks alongwith it; however I am aware that an installation disk can be created through windows. I would recommend that you ask someone or google it to find out how. You may need the dreaded Windows Registration Key. :(

I recommend giving it atleast 20 GB of your hard drive space. Also, I'd recommend downloading an anti-virus into this virtual machine for your protection and try not to use it for downloading anything other than from the iTunes store if you wish to avoid the windows viruses from playing havoc on your ubuntu machine.

All the best.

---

### Post by ironic.demise on 2011-03-04
> **panderohit said:**
> in support of ironic.demise (post #2 in this thread). I installed Windows 7 in a Virtualbox downloaded from their website. Then I had to tinker a bit to enable the usb-connections. Once set, I downloaded iTunes and synced my iPod from there and it works *perfectly*.

I tried using Rhythmbox and gtkpod but received limited success from all. In the case of Rhythmbox, only the .mp3 files and the .mov files would sync but none of the others.

The problem was the same with gtkpod. However most of my music and video files were in .m4a and .mp4 format and none of these software would recognise it. However through iTunes it worked beautifully. The only hitch was that it was extremely slow. It took more than double the time it normally takes on Windows Vista, but I am not complaining. It saves me the trouble of dual booting and being unable to use Ubuntu while managing my iPod.

However, it is necessary to have a Windows Installation Disk ready for installing the OS in virtualbox. I was lucky as I got Windows 7 pre-installed in my laptop and received the disks alongwith it; however I am aware that an installation disk can be created through windows. I would recommend that you ask someone or google it to find out how. You may need the dreaded Windows Registration Key. :(

I recommend giving it atleast 20 GB of your hard drive space. Also, I'd recommend downloading an anti-virus into this virtual machine for your protection and try not to use it for downloading anything other than from the iTunes store if you wish to avoid the windows viruses from playing havoc on your ubuntu machine.

All the best.

AVG is a good free anti-virus for a Windows machine, though the virus on a "virtual machine" have a very very limited effect on the Ubuntu host.
I still recommend using it as an exclusive ITunes machine.

In ALL of my efforts, IPods just don't work very well in Linux for obvious reasons.

I have a virtual WinXP just for a FlashDrive and a few programs on it (You know how smart flash drives are getting nowadays)

Honestly, GTKPod and RythmBox are your best bet other than a Windows VM.

XP is cheap, and without knowing it you probably already have a key if you have owned or bought a PC before.

Or take the IPod to a friends house and use their Win machine, or dual boot a windows... though if you don't have access to windows I'm afraid that gtkpod and rythmbox are about as close as you will get in my opinion.

you don't need to give 20gb space, set it as 20 but also set it to "auto grow", that way if you need 20gb space you have it but it won't deduct any more than it needs from the host machine.

---

### Post by madmarx on 2011-03-05
I had a similar problem with my ipod nano 5G.
For some time, I could add music and see it in the ipod, then some day my ipod would not show it anymore.
Comparing to another one that was working, i found a difference in the "iTunes" folder: 3 files were there in the broken ipod that were not in the working ipod: CurrentOnTheGoPlaylist.plist, iTunesCDB.ext and iTunesSD.
I made a backup of the directory first, then removed the 3 files.
I do not know why, but my ipod 5G is back: I can add files using gtkpod and they show on the ipod !

---

