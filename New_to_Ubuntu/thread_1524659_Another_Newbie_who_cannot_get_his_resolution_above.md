---
title: "Another Newbie who cannot get his resolution above 800x600"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by ZaphodFJ on 2010-07-05
Resolution

Hello.

I've recently installed 10.04 LTS on my old PC - I have a clean install of nothing else but Lucid.

Hardware - Intel Celeron, in-built graphics chip that has no branding obvious.  Unbranded 15" monitor with model number 'L151' written on the back (though it's probably not the Lenovo L151).  Tiny (UK manufacturer who I should have had the sense to avoid) buit the lot around 5-6 years ago.

System/Preferences/Monitors gives me a choice of 800x600 and 640x480.  I would like 1024x768, which my 14" (unbranded) monitor supports and which WinXP displayed on the same system.  It possibly supports better, but at 14" diagonal, my eyesight isn't up to anything tinier!

I've had a read about this problem in various places, and done damage in the process.  This included hasty changes to xorg.conf that left me seeing nothing but the Ubuntu logo on the boot screen!  I resolved this with a re-install (drastic, I know, but I hadn't done anything except install the OS at that point).

I've read [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) which gives a good description, but I'm still a little confused (and wary).  This seems to be something that depends a little on the idiosyncracies of your own system.  Nothing I have found fully matches my cheap-skate manufacturer's choice of hardware.  So, lest I leave myself unable to see any display, can someone please explain this to me like I'm a 4 year-old.

(On the bright side, 10.04 picked up all my other hardware and stuff, which 9.x did not do, when I last dabbled on this machine!)

Many thanks in advance!

---

### Post by 4Orbs on 2010-07-05
I'm assuming you are able to log in to your system and reach the desktop, but at an unacceptable screen resolution.

If that is correct then the first step is to see if there are any proprietary drivers available for your graphics chip. Look in your system menu at System>> Administration>> Hardware Drivers and see if there is a recommended driver available... it will be shown at the top of the window and highlighted in black. If there is one available take note of whether it is nvidia. Then click the button at the bottom of the window to activate the driver. After a minute or so the driver will finish it's installation and you'll be asked to reboot. Now this is important; if it was an nvidia driver... after rebooting you'll probably be greeted by the Ubuntu splash screen in a very ugly, messed-up resolution. That's a good indication that the driver installation was successful, unfortunately it's also a quirk in Ubuntu 10.04 that has yet to be fixed. But after the splash screen, you should get a normal login screen and a normal desktop after logging in. If you make it this far, in order to change screen resolution hereafter use the nvidia settings manager rather than the Preferences>> Monitor option. There is currently nothing you can do that will fix the ugly splash screen.

EDIT: and if there is no proprietary driver available, or if your video chip is ATI then you will be best off waiting for someone else to post a solution... I have no experience with anything except nvidia.

---

### Post by ZaphodFJ on 2010-07-06
Thank you for replying, however:

I go to: System>> Administration>> Hardware Drivers 
A dialogue appears, "Searching for available drivers".
It then says: "No proprietary drivers are in use on this system"

Any other ideas?

---

### Post by ZaphodFJ on 2010-07-07
Further to the previous post, I came across a suggestion to use 'lspci' from the command line.  The output is shown below - can someone point me in the right direction.  Is this something to do with OpenChrome (which package manager says is installed)

TIA.
---

00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:05.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
00:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

---

### Post by hhh on 2010-07-07
> **ZaphodFJ said:**
> Is this something to do with OpenChrome (which package manager says is installed)
I'd say no.

> 01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
I'd say that's the integrated card. You can verify by running...
```
lspci | grep VGA
```... and get even more info by running...```
lspci | grep VGA
```(source...
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto) )

So I'd say this is the driver...
[https://launchpad.net/ubuntu/lucid/+package/xserver-xorg-video-savage](https://launchpad.net/ubuntu/lucid/+package/xserver-xorg-video-savage)
[http://manpages.ubuntu.com/manpages/lucid/man4/savage.4.html](http://manpages.ubuntu.com/manpages/lucid/man4/savage.4.html)
... and to install it I'd try
```
sudo apt-get update
```
```
sudo apt-get install xserver-xorg-video-savage
```
and then either reboot or at least log out/in for it to be recognized.

HTH

---

### Post by ZaphodFJ on 2010-07-07
Thanks...

...did all of that, rebooted - still stuck with a choice of 640x480 or 800x600.

any thoughts?

---

### Post by QLee on 2010-07-07
> **ZaphodFJ said:**
> Thanks...

...did all of that, rebooted - still stuck with a choice of 640x480 or 800x600.

any thoughts?

 Open a terminal window and enter the command xrandr. That will give you an idea of what the system thinks your monitor is capable of. This is a common issue, there are lots of posts so a search of the archive will probably help you sort out the problem if it isn't identifying correctly.

---

### Post by ZaphodFJ on 2010-07-08
xrandr did not give me anything above 800x600.

However, this was fixed by following the advice at: [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9562852](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9562852)

Thanks,

Z

---

