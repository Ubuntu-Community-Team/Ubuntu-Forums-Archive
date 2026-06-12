---
title: "Ubuntu without a commitment"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by smorton on 2009-12-15
I was very interested in ubuntu and then I got distracted.  Now I am interested again.  I seem to remember that you can use ubuntu without doing much of anything if you have the disc which I have.  

I have Windows XP.  Is there some way  to boot ubuntu up with no commitment.  

Sorry if this is a dumb question or if I should have done a big search.

Thanks

SM

---

### Post by Diametric on 2009-12-15
Yes, if you have a .iso cd you can set your bios to boot from cd and it will run/load as a "live cd"...giving you the ability to check it out and play around.  It loads the OS into RAM instead of installing anything so there is no file issue to worry about.  Have fun and good luck!

---

### Post by wojox on 2009-12-15
Sure just put your CD in the drive and reboot making sure you do what ever you need to to boot from CD first. Choose your Language and select Try without installing.

---

### Post by raymondh on 2009-12-15
> **smorton said:**
> I was very interested in ubuntu and then I got distracted.  Now I am interested again.  I seem to remember that you can use ubuntu without doing much of anything if you have the disc which I have.  

I have Windows XP.  Is there some way  to boot ubuntu up with no commitment.  

Sorry if this is a dumb question or if I should have done a big search.

Thanks

SM


-  In a live CD ... select TRY UBUNTU WITHOUT ANY CHANGES
-  You can also make a [persistent liveUSB]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")
-  You can install via WUBI and treat it like a windows program.

Regards,

---

### Post by doas777 on 2009-12-15
the live cd is a great way to get a taste of ubuntu, but remember, it's a good bit better when installed to hardware. 

good luck, and post back if you have any questions.

---

### Post by smorton on 2009-12-15
I must be doing something wrong.  I inserted the disc and rebooted twice now.  It keeps rebooting to Windows.  How do I change my bios?  

Thanks for all the help. 


SM

---

### Post by nmaster on 2009-12-15
i would highly suggest wubi.  its a super easy way to dual-boot and there is no commitment.
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Merk42 on 2009-12-15
> **smorton said:**
> I must be doing something wrong.  I inserted the disc and rebooted twice now.  It keeps rebooting to Windows.  How do I change my bios?  

Thanks for all the help. 


SM

It depends on the motherboard sadly.
Sometimes it's DEL, other times F2, or F12 or F6.

Just have to figure out through trial and error (or if you see a message that says "Press to start setup mode").

Once in the BIOS you change your boot order to check the CD first, then the harddrive.

---

### Post by smorton on 2009-12-15
WUBI looks very interesting.  It appears that you can remove ubuntu easily if you choose to.

I think I will explore that.

I would like to know how to get the Windows to reboot from a CD though.

SM

---

### Post by Merk42 on 2009-12-15
> **smorton said:**
> WUBI looks very interesting.  It appears that you can remove ubuntu easily if you choose to.

I think I will explore that.

I would like to know how to get the Windows to reboot from a CD though.

SM

I'm not sure what you mean.

If you change your boot order to be CD then Harddrive, and have nothing in the CD, your computer will check the harddrive and boot windows normally.

---

### Post by LegendarySandwich on 2009-12-15
> **smorton said:**
> I must be doing something wrong.  I inserted the disc and rebooted twice now.  It keeps rebooting to Windows.  How do I change my bios?  

Thanks for all the help. 


SM
When your computer is starting, press F2 until a list comes up. Select your CD drive. Ubuntu should start to load in under ten seconds; if not, then your disc may have been burned improperly. Try burning it again. 

(Remember, it has to be saved as an .iso disc, not a data disc.)

---

### Post by b1lancer on 2009-12-15
What you need to do is as the computer is starting up (usually displaying a picture of the brand), press F12 or F2 to get the BOOT MENU. you might have to strike it repeatedly. As it starts with the first screen display, pay close attention to all the little computer type phrases that appear--- one might tell you exactly how to access the boot menu. From there you select 'CD' and you're off to the Live Ubuntu.

Try that first. It will most likely work. If that doesn't work, you might need to do some BIOS changes so that it checks the CD first, but this could be messy if you don't do it right. So check back if you still can't do it.


BTW. The best student is the one that asks all the questions in his head!            ;)

---

### Post by nmaster on 2009-12-15
when you boot up, look very carefully at the screen.  there should be some options about which keys to push.  usually there are just a couple, if you have a bunch of options taking a picture might help.

---

### Post by smorton on 2009-12-15
You are not sure what I mean because I am not sure of what I mean.  I am going to try WUBI in the morning.

Many thanks

SM

---

### Post by nmaster on 2009-12-15
> **LegendarySandwich said:**
> 
(Remember, it has to be saved as an .iso disc, not a data disc.)


i feel like this is probably the issue.  i lot of people make this mistake.

---

### Post by raymondh on 2009-12-15
@ smorton,

If you decide to investigate Ubuntu using wubi, note that wubi will install a 'boot line' in your boot.ini file which will allow you to choose an OS at start-up.

To remove ubuntu later on will be a 2-step process;

-  use the add/remove function in XP to remove Ubuntu
-  locate and open the boot.ini file in c:drive and manually remove the wubi-related line.  ONLY THE WUBI RELATED LINE or you risk not booting into XP.

Lastly, remember that the performance of a wubi-installed Ubuntu is **very dependent** on a clean, healthy and defragged windows.

Good luck.  Always have a working/tested back-up of your files.  Have fun re-discovering ubuntu :)

---

### Post by smorton on 2009-12-15
Thanks again.  I think I now how to do the reboot now.  F2 or F12.  Will try in the morning.

SM

---

### Post by smorton on 2009-12-16
Wubi is great. Love it.

Thanks much

SM

---

### Post by raymondh on 2009-12-16
> **smorton said:**
> Wubi is great. Love it.

Thanks much

SM

Glad you're enjoying your re-discovery of Ubuntu.

Keep windows defragged and healthy (virus/malware-free) because if windows crashes, so does your ubuntu. That is one main concern with a wubi-install. 

When you're ready, post back and we can assist in putting Ubuntu in its' own partition instead of it (currently) being a "file" within windows..... which would be a safer bet as neither OS is dependent on the other.

Happy ubuntu-ing :)

---

### Post by doas777 on 2009-12-16
agreed. wubi causes trouble for long term use, but is helpful in getting people started.

---

### Post by smorton on 2009-12-16
I have noticed that the monitor resolution isn't as clear with ubuntu.  Is this common.  I have a Samsung 22 inch monitor.

thanks

SM

---

### Post by doas777 on 2009-12-16
have you installed a video card driver? what kind of card do you have?

some of the cleartype stuff that vista/win7 has are patented (why this was allow no one knows) so it may not be quite as clear, but I never have a problem unless I'm using a virtual machine to host ubu

---

### Post by smorton on 2009-12-16
(have you installed a video card driver? what kind of card do you have?)

I am able to watch videos very clear on my Windows OS which is used by ubuntu via WUBI.  Do I  need to get something else?  The resolution isn't terrible but not as good as when Windows XP is running.  I don't know what kind of video card I have.  Is there a place to look?

SM

---

### Post by doas777 on 2009-12-16
> **smorton said:**
> (have you installed a video card driver? what kind of card do you have?)

I am able to watch videos very clear on my Windows OS which is used by ubuntu via WUBI.  Do I  need to get something else?  The resolution isn't terrible but not as good as when Windows XP is running.  I don't know what kind of video card I have.  Is there a place to look?

SM

well, as I understand it (I've never used wubi), you have to reboot into it, so XP isn't technically running when ubuntu is up, so no, the windows drivers have no impact on what you see.

as for your vidcard, go to Applications -> Accessories and select Terminal. then enter:
```

sudo lshw -C display

```

that will tell us the kind of card and the driver installed.

just FYI, you will find that most linux support is done via command line, which is hard for some users to adjust to, but it really simplifies the support process. otherwise I would have to spend time to capture, crop, and upload images (which I am not likely to do) and since everyones desktop is differant, it's hard to give click-by-click instructions.

---

### Post by smorton on 2009-12-16
"as for your vidcard, go to Applications -> Accessories and select Terminal. then enter:
```

sudo lshw -C display

```that will tell us the kind of card and the driver installed."

I am unfamiliar with how to find what video card and driver I have.  Do I do that through the control panel?  What is the "command line"?

Thanks

SM

---

### Post by raymondh on 2009-12-16
> **smorton said:**
> "as for your vidcard, go to Applications -> Accessories and select Terminal. then enter:
```

sudo lshw -C display

```that will tell us the kind of card and the driver installed."

I am unfamiliar with how to find what video card and driver I have.  Do I do that through the control panel?  What is the "command line"?

Thanks

SM


- go/open Ubuntu
- access a TERMINAL (accessories > applications)
- type

```
sudo lshw -C display
```

* you will be prompted for your password which when you type will be invisible.

-  copy the results and post back here.

The command line is another way to interact with your computer.  We have gotten used to ;)  a graphical interface .... *that little window that pops up asking us what we want to do or the next step we ought to take* .... that the command line has been relegated to the backstage.  Do you remember during the early days of IT, any command we gave the computer had to be typed out? That's the command line.

Which is better? Both are.  It depends on many things and on the level of the operator.  Personally, I believe (as an old forum friend would "lecture" us) .... 

"learn the command line and you can make a commodore64 run".

Said by Merlinus.

Regards,

---

### Post by 3rdalbum on 2009-12-16
Actually a better command to use in the terminal would be:

```
lspci
```

It's more likely to tell us exactly what card you are using.

If it's ATI or Nvidia, you should be able to go to System > Administration > Hardware Drivers and it will offer to download and install a driver for you. If it doesn't offer this, either you're not using an ATI or Nvidia graphics card, or you need to reload your package list (which you can do by clicking the Reload button in System > Administration > Synaptic Package Manager).

---

### Post by smorton on 2009-12-16
It states the following, which I understand may be way too much:

administrator@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
02:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem


SM

---

### Post by 3rdalbum on 2009-12-16
> **smorton said:**
> It states the following, which I understand may be way too much:

01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

Congratulations, you've got an Nvidia GeForce 8400 as your graphics card.

You should be able to go to System > Administration > Hardware Drivers and it will offer to download and install a driver for you. If it doesn't offer this, you need to reload your package list (which you can do by clicking the Reload button in System > Administration > Synaptic Package Manager).

You will need a reboot after installing the driver. It might have the correct resolution straight away, or if it doesn't you can set it by running the Nvidia-settings program as root. Hit Alt-F2 and type the following:

```
gksudo nvidia-settings
```

Use this program to set your resolution to the monitor's native resolution.

---

### Post by smorton on 2009-12-16
Many thanks.

Maybe this should be another thread, but what if one had a new computer make with ubuntu as the main OS and then have Windows XP installed via a virtual OS.  I need to use Windows XP, but like to keep it speedy.  To do this I reformat it from time to time.  If it were a virtual OS could I reformat it easier?

SM

---

### Post by Merk42 on 2009-12-16
> **smorton said:**
> Many thanks.

Maybe this should be another thread, but what if one had a new computer make with ubuntu as the main OS and then have Windows XP installed via a virtual OS.  I need to use Windows XP, but like to keep it speedy.  To do this I reformat it from time to time.  If it were a virtual OS could I reformat it easier?

SM

Yes, given you've currently installed via WUBI, reformatting Windows would also erase Ubuntu.

There is a bit of a performance hit in terms of running in a virtual OS.  You need enough ram for Ubuntu AND Windows at the same time, plus 3D support is very very limited.

What do you still use Windows for?

---

### Post by LegendarySandwich on 2009-12-18
As you can probably tell by now, installing Ubuntu as an independent operating system is probably the easiest way to use it. It's more of a "commitment", but it's a better option in the long run.

---

