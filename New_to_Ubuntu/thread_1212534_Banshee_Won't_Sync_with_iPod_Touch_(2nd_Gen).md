---
title: "Banshee Won't Sync with iPod Touch (2nd Gen)"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by iEthan on 2009-07-13
I connect my iPod Touch (2nd generation) to my computer, and it shows up on the Desktop, but it will not show up in Banshee. What is the problem here?

---

### Post by Garrovick on 2009-07-13
Rumor has it that Apple has blocked Linux from newer iPods. Try a site like iLounge.com for some help.

---

### Post by Temposs on 2009-07-13
The ipod touch in particular has been known to not work too well on Linux

---

### Post by Ocxic on 2009-07-13
The iPhone and ipod touches don't work with linux. you'll have to use windows in a vertual machine in order to sync.

---

### Post by iEthan on 2009-07-14
Would running iTunes under WINE work?

---

### Post by CaseSensative on 2009-07-14
No Itunes will not recognize your Ipod even if you use wine.

---

### Post by J.Meador on 2009-08-21
The iPod Touch 2G is definitely usable on Ubuntu with a little elbow grease.
I have a working 2G with firmware 2.2.1 using gtkpod for my transfers. Depending on which route you take, you might want to avoid the update to firmware 3.x.

There's this for starters:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

The only part of it I didn't read somewhere was telling gtkpod that myPod was an iPhone and not an iPod touch. It hadn't been syncing up to that point, but now it works like a charm.

---

### Post by coober85 on 2009-08-21
From the linux mint forums comes....

THE COMPLETE IDIOTS GUIDE TO LINUX TO IPOD TOUCH/PHONE SYNCING (USING VIRTUAL BOX): lots of steps but they are very simple. no jailbreaking, no linux code!

Materials needed.
PC (I'm using a Lenovo T61)
iPod Touch or iPhone (I'm using a 1st Gen touch w/ Firmware 3.0)
Ipod usb connector
Windows XP SP1 or SP2 install disc with Serial Key
Linux Mint 7 or ubuntu 9.04 with all updates as current as april 17th, 2009 (future linux updates should only make this easier)

10 long but easy steps **_(Don't be intimidated I over explain a lot of stuff)_**:

1. go to the package manager and install Virtualbox **2.2**, DON'T UPGRADE to 3.0 it will not work! if you have 3.0 uninstall it and re-install w/ 2.2

2. Put in your xp CD, and set up a windows XP virtual drive in V.box. *I gave myself a 15GB partition. way more than necessary. oh yeah and I have traditionally done the full NFTS install but the (quick) NFTS works fine too. choose the dynamic spacing option. All that's on my XP machine is MS Office 2007, Itunes, Norton Antivirus, Tweak UI, and maybe some adobe video editing software and games later on. *other note when installing XP - "typical network settings" seems to work with no problems for me. turn off automatic updates and DON'T UPGRADE to SP3! I've heard it will not work. find some way to downgrade if you only have an install disc greater than SP2.

3. The tip a lot of people seem to leave out (assuming you have one folder that holds all of your music and you want to share it with both XP and Linux OS's) is to install guest additions. press the right ctrl button to get out of XP and click on the "devices" drop down menu in the windows menu and select install guest additions. 

4. Shut down XP and go into the Virtualbox settings menu (if its grayed out you haven't shut down XP). select "shared folders" and click the folder button with a green plus (add a folder). from the pop up menu select the folder that holds your music. *I think the bigger the folder you select the slower the performance. Don't worry though, its barely noticeable. I have a whole 120GB drive as a shared folder and I don't have any performance issues.*

5. Start XP again, click on the start button, then right click on my computer and select map network drive. (z: drive is default, doesn't matter what letter you select) click browse and expand virtualbox shared folders, click select the folder you want *(it is sometimes glitchy, try it again if you can't initially select the folder you want - it will work eventually).*

6. download itunes. I think you have to download ActiveX in windows explorer, don't sweat it. *be aware of that little yellow bar that stealthy drops down from the address bar asking if you want to proceed by installing things like flash and activeX. I haven't noticed them at times, and then wondered why I can't download things off of windows explorer that I want (like itunes).*  as of this posting the current version of itunes (8.2) seems to work fine for firmware 3.0. but I'm pretty sure Apple is going to update with a version that block it's use in Virtualbox or VM ware. You may have to search [http://www.oldversion.com](http://www.oldversion.com) for this version. add media to itunes through the shared folder

7. Click Menu -> Administration -> users and groups -> hit the unlock button and type in your password. select your user name -> click the properties -> user privileges tab -> at the bottom make sure the one saying "virtualbox *something*" is checked.

8. If you have very important playlists on your ipod that you want to keep, manually write them down, as ******* itunes/ipod is going to wipe all media (apps will be fine) from your iPod once you try to sync it with iTunes in your virtual drive.

9. Connect your iPod to your PC. Click on the Devices drop down menu in your XP SP2 window. go down to USB devices, you should see a non-grayed out "Apple inc. iPod 001" with an empty check box. click it and it should become checked and you should almost instantly hear a generic "du-dun" Microsoft "usb recognized" sound.

10. Go into Itunes again. make a playlist with one song to go into your ipod, select that playist only and hit sync. It's going to ask you if you want to erase and sync and if you want to transfer purchased media (apps and things you've purchased on your iPod). click on both those options and wait a while. when it's done, remake your old playlists sync'em and you're done!

you can find install discs for around 50-60 dollars.

....
i can go from just a linux OS, to itunes open and in the process of syncing in **less than a minute and a half** (Windows XP loads in ~20-25seconds in virtual box)! it's definitely worth the price of a windows disc. you can get XP SP1 for 56 bucks here: [http://www.9software.com/Windows_XP_Home_CD_p/wnxphmcd.htm](http://www.9software.com/Windows_XP_Home_CD_p/wnxphmcd.htm). not to mention, I can use pro video editing and other advanced software for windows with out giving up the joys of linux too. if you're one of those computer wiz's that knows how to trick XP into thinking you have a disk when you really don't (aka getting XP for Free.99)... then more power to ya!

---

### Post by coober85 on 2009-08-21
> **J.Meador said:**
> The iPod Touch 2G is definitely usable on Ubuntu with a little elbow grease.
I have a working 2G with firmware 2.2.1 using gtkpod for my transfers. Depending on which route you take, you might want to avoid the update to firmware 3.x.

There's this for starters:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

The only part of it I didn't read somewhere was telling gtkpod that myPod was an iPhone and not an iPod touch. It hadn't been syncing up to that point, but now it works like a charm.

That is a lot of f*ckin work. and what's worse, when you get to the bottom where it talks about 3.0 (which actually has pretty useful updates and features like copy and paste):

> Firmware 3.0

As of now (22nd of June 2009), there is no alternative to iTunes when it comes to syncing with an iPod Touch or iPhone with Firmware 3.0. The Database Structure is completely new, hence all former methods are now incompatible. (Source: [http://marcansoft.com/blog/2009/06/iphone-os-30-music-totally-incompatible/](http://marcansoft.com/blog/2009/06/iphone-os-30-music-totally-incompatible/))

---

