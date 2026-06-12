---
title: "Completely lost Flash sound after update just now"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by myromance123 on 2009-02-25
Hey there. I don't know what happened but after installing an update just now I have no more sound for any flash videos on the net.
I put the thread here because I think this hasn't happened before.
 I googled quite a bit and no one with anything similar yet.

 The update was adobe-flashplugin .

I tried removing it and to no avail. Still no sound and the format for viewing flash videos has changed as well...

 Instead of the video on youtube coming up as normal, a big play sorta button appears and you have to press that before you get back to the normal video.
 
 I've noticed that even though the sound on youtube videos is up, its red. I'm guessing its telling me somethings wrong with the sound.

I tried reinstalling nonfree-flashplugin, and adobe-flashplugin.

Nothing. What do I do?

I've included what the red sound button and new format look like.

 Theres no problem with sound for anything else. I can play games and listen to music from my desktop no prob.

---

### Post by jaminux on 2009-02-25
Are you running 32 or 64 bit Ubuntu?

---

### Post by jaminux on 2009-02-25
If you are running 64 bit flash is notoriously dodgy.

Try:

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

This might fix your problems

---

### Post by myromance123 on 2009-02-25
Hey thanks for the fast reply. I'm running 32-bit.

 I'm worried if I follow that I'll mess up my system because I run a 32-bit .

---

### Post by jaminux on 2009-02-25
Yea it is meant for 64 bit. No need if you're 32 bit.

---

### Post by rasmus91 on 2009-02-25
> I'm worried if I follow that I'll mess up my system because I run a 32-bit .

May sound stupid but: have you tried rebooting?

My sound disappeared in flash, i did a reboot and it worked... i could also listen to music from the desktop

(I'm running 64 bit, But it might do the trick...)

---

### Post by jaminux on 2009-02-25
Try the Hardy Heron version at:

[http://packages.ubuntu.com/hardy/i386/flashplugin-nonfree/download](http://packages.ubuntu.com/hardy/i386/flashplugin-nonfree/download)

It is a deb file so Ubuntu will annoy you about updating it, but if it does not work either it should be easy enough to update and get your system back to its previous state.

---

### Post by myromance123 on 2009-02-25
Okeh thanks for your answers.
 
 I hope theres a solution to this problem. Anyone any ideas?

Anyone else experienced this?

---

### Post by myromance123 on 2009-02-25
Yes I rebooted already. Okeh Jaminux I'm gonna give that a shot right now.

---

### Post by myromance123 on 2009-02-25
No luck Jaminux.

 I removed the nonfree-flashplugin I had (ver 10) and installed the one you mentioned (ver 9) . 

 The format is still the same (even flash ads have the play button, very annoying).

The videos play no prob but theres still no sound and the sound button is still red as above. 

 nothings changed..

Anymore ideas?

---

### Post by johnjohn2 on 2009-02-25
> **jaminux said:**
> If you are running 64 bit flash is notoriously dodgy.

Try:

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

This might fix your problems

Never had a problem on 6 bit

---

### Post by jaminux on 2009-02-25
Na, I am out of ideas.

---

### Post by myromance123 on 2009-02-25
No ideas on how to fix my prob johnjohn?

---

### Post by myromance123 on 2009-02-25
Bump.

 I really dont want to have to reformat my computer just to get it working again...

 I still have no sound from flash videos. Its driving me nutz!

---

### Post by halovivek on 2009-02-26
i had the same problem with my system. They told me to remove all the flash player installed in my system and try to reinstall again. now it is working fine.
could you post this one also lspci from terminal

---

### Post by myromance123 on 2009-02-26
Ok remove all flash players eh? I'll give that a shot.

I'm not too familiar yet with terminal commands so I just typed lspci in the terminal and heres what I got:
```
yusuf@yusuf-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600/X1650 PRO]
01:00.1 Display controller: ATI Technologies Inc RV530LE [Radeon X1650 PRO] (Secondary)
06:02.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
yusuf@yusuf-desktop:~$ 

```

What am I looking at here? It looks related to my hardware.

Please guide me as to what you removed because I believe I removed all the flash players I had (or do you mean something else?) from synaptic package manager.

 I went to installed and searched "flash" and removed everything there and reinstalled it all, that was one of my first moves to see what was wrong. Is there anything specific that must go?

---

### Post by myromance123 on 2009-02-26
Bump Again.

 I'm still in the dark as to how to solve this.
I kind of really need the sound since I was self teaching myself through vids on the net bout how to worka certain program.

Please, any ideas I'm willing to try as long as its sane and safe!

---

### Post by kansasnoob on 2009-02-26
OK, first go to Synaptic Package Manager, then click on "Search", then type "flash" without the quotation marks. Be sure you have adobe-flashplugin installed (in fact mark it for reinstallation), and make sure that "flashplugin-nonfree" is NOT installed!

Then, still in synaptic, search for sun-java6 ..... and:

Mark for installation all sun-java6-* (* is a wild card) except sun-java6-source and sun-java6-doc.

Then install the Mozilla build of Firefox using Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

And when you're done disable all "Add-ons" but install Flashblock 1.5.8 - that is one.five.eight!

---

### Post by myromance123 on 2009-02-27
thanks for the reply kansasnoob.

 Did everything you said. Firefox crashes when I go to youtube.com because of Flashblock 1.5.8, so I disabled it.

 Things are still messed up. No sound and Some videos won't load.

I got ubuntuzilla up and running no prob. Installed the mozilla build as well.

 ....Nothings changed...Still that stupid annoying flash play thing that waits for me to press it before it starts the vid....
Still NO sound...

 How do I revert to before this retarded update?
Its all because of adobeflash-plugin. 

I need help. Anything , and I mean anything please help.

Removing it does nothing!

---

### Post by myromance123 on 2009-02-28
Bump (more like a skid then violently crashes into a wall. A near death experience)

---

### Post by RomeReactor on 2009-02-28
Hi. In Firefox, go to 'Tools->Add-ons' and post which plugins and extensions you have installed.

---

### Post by myromance123 on 2009-02-28
Hey thanks for replying.

 Okeh here goes.

Extensions:

FlashBlock 1.5.8 (status:installed but not enabled)

Plugins:

Default Plugin
Demo Print Plugin for unix/linux
DivX Web Player (ver 1.4.0.233)
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
iTunes Application Detector
Java(TM) Plug-In 1.6.0_07-b06
QuickTime Plug-In 7.2.0
Shockwave Flash (9.0 r100)
Totem Web Browser Plugin 2.22.1
VLC Multimedia Plugin (compatible Totem 2.22.1)
Windows Media Player Plug-In 10(compatible; Totem)

  Thats everthing in Extensions and Plugins.
Please reply asap.

---

### Post by arm-c on 2009-02-28
Well,

I haven't read all responses, but I would start by reinstalling the flash plugin and the flash player.  Also may want to do a search for flash and pulse audio and see if it is something with that.  

I'd also check the PulseAudio Volume control applet.  Run that little app and check the playback tab.  When you play the video (firefox or the .flv file) you should see the application listed in the playback area.  Perhaps you have lost your pulse audio plugin for alsa.  Try reinstalling those also.

Check your volume?  I also had a problem initially with the volume settings for pulse being low, so no matter what I did, it remained a 1/4 of what it was.  The fix ended up being something stupid and not apparent -- through the Pulse Audio Manager, click on the Devices tab.  Then click the alsa_output source, goto properties, increase volume setting to 480 (note that reopening it will be 100 again).  After that, volume worked perfectly.

I didn't have that problem and flash still works for me and has not quit.  So, these are rambling musings. :)

---

### Post by RomeReactor on 2009-02-28
In case you have swfdec and/or gnash installed, purge them (close Firefox first):
```
sudo aptitude purge swfdec-mozilla mozilla-plugin-gnash gnash gnash-common
```
Then open Firefox again and see if you can play Flash properly now.

---

### Post by myromance123 on 2009-03-01
I thank you greatly RomeReactor, that one post worked wonders!!

 Everything is back to normal now :)

Theres sound, no annoying big grey play button, and it plays as per normal.

I greatly thank you :D

arm-c thanks for replying too :)

Btw, how'd you know how to fix it so easily ?

  Its ok if you don't want to tell me :)
I'm truly grateful~   :lolflag:

---

### Post by RomeReactor on 2009-03-01
Glad to help.

It's just a common occurrence that Flash related problems are due to having installed more than one plugin to handle Flash; usually the open-source plugins (Gnash, SWFdec) conflict with the proprietary Flash plugin.

---

### Post by Desktop_n00b on 2009-09-14
I've done all that and even installed a different flash player and I still can't get sound. I have Ubuntu Studios 9.04. Can anyone suggest things to try?

---

