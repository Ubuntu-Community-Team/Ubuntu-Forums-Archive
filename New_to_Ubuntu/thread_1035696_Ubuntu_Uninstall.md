---
title: "Ubuntu Uninstall"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by simapex on 2009-01-10
Hi somebody!!
I mysteriously lost 22GB out of my 45GB Primary HDD, because I installed Ubuntu on my Machine. Problem is ubuntu isn’t even running. At boot up stage, it says firmware needs to be downloaded. Now, I have tried to locate Ubuntu on my hard disk space, just so I could uninstall it. 
Another important info is that I actually followed the demo and installation process. Could anyone advise what I have to do, first to recover my lost hdd space and to reinstall Ubuntu?
Your advice will be appreciated.

---

### Post by zvacet on 2009-01-10
Download [Gparted live Cd]("http://gparted.sourceforge.net/") and find your Ubuntu partition.How to unistall Ubuntu you can read [here.]("http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_uninstall_Ubuntu")

---

### Post by ugm6hr on 2009-01-10
> **simapex said:**
> At boot up stage, it says firmware needs to be downloaded. 

Where did you get Ubuntu from?

Ubuntu will never ask you to download firmware before logging into the OS.

Did the LiveCD work?

---

### Post by simapex on 2009-01-12
Ugm6hr and zvacet,

I must thank you two for your interests in my problem. 
Here is exactly what happened. Ubuntu Live Installation CD was sent to me, by my request, free of charge. I popped the live CD into my CD/DVD ROM while I was running win XP. The CD loaded up and a message popped up with three options in the following order;

1. Demo and Installation
2. Install within Windows
3. Learn more about Ubuntu.

Because I didn’t want to make any mistake, not knowing what lay ahead, and thinking I would get help with installation, I clicked on the first, Demo and Installation. This took me to a second stage where I was asked whether to reboot my computer or to reboot later. I clicked to reboot, and then it started up with Ubuntu, with several options, which included install Ubuntu without changing your computer setting, et cetera. I clicked on this and it takes me yet again to another stage, this time with what appeared to be Ubuntu OS, the real thing. Here I clicked on install and followed the prompt and values. At a point I was asked to partition/ select a partition with a set of options. I did manual. And then I followed up through with the partitioning. 

Presently I rebooted my computer, and after the usual stage, instead of booting windows XP directly, these options showed up.
1.Ubuntu 8.04.1, Kernel 2.6.24-19 generic 
2. Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)
3. Ubuntu 8.04.1, memtest86+ 
4. Other Operating System
5.Microsoft Windows XP professional.

I tried to run the first value Ubuntu 8.04.1, Kernel 2.6.24-19 generic, with the hope it would boot me into Ubuntu, instead it brought series of values and then says error, no firmware found, followed by a link to download the firmware from this site [www.linuxwireless.org/en/users/drivers/b43#devicefirmware](www.linuxwireless.org/en/users/drivers/b43#devicefirmware)

The second and third options did exactly the same thing. 
This is the problem, because I can’t even run Ubuntu and then I can’t delete or uninstall it. I was however able to run windows. Meanwhile, on my windows, I had two partitions, C and D. I had 40GB on my C and 45GB on C. But right now, I observed that I only had 23.2, with 17GB gone. Gone to where, I am not able to understand. I will like to recover the missing HDD space, as that was taken from off my primary partition. And then I will install Ubuntu properly if it would be possible to use my secondary disk space.
Many thanks.

---

### Post by 3rdalbum on 2009-01-12
Ubuntu has to create a partition for itself when it installs, and when you are installing as a "dual-boot" it will take that space from your Windows partition. By default, I believe Ubuntu suggests half of your Windows partition's free space unless you change it.

This is where your 17 gigabytes has gone. Windows doesn't read Linux partitions, by the way, so that's why Windows can't see it.

I have not had my bootup interrupted because of missing wireless firmware - I didn't think that would happen. Can anyone else shed some light on this?

---

### Post by ugm6hr on 2009-01-12
As 3rdalbum explained, during the "partitioning" phase of installation, you have clearly reduced the Windows partition and created a new Linux partition to install in.  This (presumably) ext3 partition (and swap) will not be seen by Windows; it is not "missing".

From reading your description, you have done a proper dual-boot rather than installing with Wubi (within Windows).

This makes less sense:
> I tried to run the first value Ubuntu 8.04.1, Kernel 2.6.24-19 generic, with the hope it would boot me into Ubuntu, instead it brought series of values and then says error, no firmware found, followed by a link to download the firmware from this site [http://www.linuxwireless.org/en/user...devicefirmware](http://www.linuxwireless.org/en/user...devicefirmware)

That link appears to be suggesting you get the b43-fwcutter, which is the Broadcom wifi firmware for the b43 opensource driver.  However, Ubuntu does not require this to boot.  Perhaps during the install, it installed the b43 driver, but not the firmware?  Maybe if you connected to an ethernet connection while booting, it might be able to access the firmware?

And the error... is that still on a black screen with white typescript?  And what happens after it presents the link - does it return a prompt, or what?  Can you type commands there?  Can you login?  If not, try Ctrl-Alt-F1 or Ctrl-Alt-F2 - does that return you to a prompt?

---

### Post by simapex on 2009-01-12
Here is what came up, all on black screen with typescript. 
“B43/ucode5.fw” you must go to [http://www.linuxwireless.org/en/user.devicefirmware](http://www.linuxwireless.org/en/user.devicefirmware) and download the correct firmware (version 4).

And then, it appears to want to boot, with the following on the page: Ubuntu is running in low-graphics mode, together with options to configure, cancel or continue. At the click of CONTINUE, these words appear on still the black screen…

Starting up.. MP-BIOS bug: 8254 timer not connected to I0-APIC
Trying to resume from dev/disk/by-uunid/c2bdae59-125d-402d-8b68-918606679 b6d
No resume image, doing normal boot…

Ubuntu 8.04.1 Apex (which is my username) laptop tty1
Apex-laptop login: [155.746931]

B43-phy0 ERROR: firmware file “b43/ucode5.fw not found or load failed..
To answer your questions, yes, my internet is connected the whole time.

No it does not return to prompt; instead it remained that way, or brings up the same message all over again at intervals.

Yes, I can type command there. But I can’t login.
Ctrl+alt+del reboots me.

---

### Post by ugm6hr on 2009-01-12
Ctrl-Alt-F1 returns you to the Terminal (not Ctrl-Alt-Del).

At the "Apex-laptop login:" you should be able to login.

Just type your username and press Enter.  Then type password and Enter.

But it sounds like your installation is corrupt.

Did you check the md5sum or run the "Check CD integrity" before installing?

---

### Post by simapex on 2009-01-15
Thanks everyone for your help, Ubuntu is now running on my computer, with no internet connection though. Even though I followed the process for connecting to the internet, I seem unable to get connection. Perhaps I am doing it the wrong way. I use wireless network. 
On the Ubuntu interface, I followed the simple procedure of going through:
System-administration-network, and then the configuration. My problem though is figuring out what my network name and password is supposed to be. Would this have to be the same as I used in windows? I also do not know where to find ESSID. I can’t find where network key is either, nor could I find network manager. 
I was also wondering if it would be possible for me to access all ubuntu features via windows, without having to turn off my win XP and reboot into ubuntu.

---

### Post by ugm6hr on 2009-01-15
You should be able to find your Network / SSID using Network Manager - click on some of the icons in the top right corner - it brings a drop-down list as here:

[IMG]http://projects.gnome.org/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

Password will be the same as in Windows (since the password is set by your router, not your computer).

And no, you can't access Ubuntu in Windows (unless you install it in a VM).

---

### Post by simapex on 2009-01-25
Thank you ugm6hr.
But all the connection icon could really show is the ENABLING CONNECTION or manual configuration, which doesnt help much. My confiured the setting to automatic (DHCP)configuration. yet, nothing seems to change with the connection icon. 
Now I tried to edit the terminal, with the following command, suso:gedit /etc/init.d/alsa-utils
I got stuck because a message that says the command not available appears.
I am wondering if there was a problem at the point of installing ubuntu, and if this is the case, could i uninstall completely, and then install wubi? 
Will have still have the HDD space occupied by ubuntu available for this purpose, and what are the proper procedure to uninstall ubuntu. my primary goal however is to be able to use the installed ubuntu the way it is right now, with of course, the internet connection. Tons of thanks in advance.

---

### Post by ugm6hr on 2009-01-25
Wubi is not a good idea - you have already created a separate partition - using Wubi will simply complicate things.

As for your wifi - try to avoid editing config files for the time being.  If you have done any edits, make sure you keep a note of them, so that you can return them to default later - since if someone tries to help, the problem may be an edit you have made in the past to try and "fix" the problem.

Lets start at the beginning:

Do you have a wired connection you can use temporarily, or would you have to boot into Windows to download files?

What kind of wifi device do you have - internal, externall, USB, laptop etc?

Give the outputs from the following commands:

```
lshw -class network
lspci
lsusb
ifconfig
iwconfig
```

These may not all be necessary, but if you have to copy and paste, and transfer to a USB stick to get them here, may as well do them all at once.

---

### Post by anewguy on 2009-01-25
We will need all the above information to get started, but also please be sure roaming is enabled under network.

Dave :)

---

### Post by simapex on 2009-01-25
Internet connection on my ubuntu is now accessable. Thanks to you all.
There seems to be some issue with applications, as I could get to run exe. programmes which I had downloaded, such as yahoo messenger, and the rest of it. 

Would I require special application to get such programmes to work?

---

### Post by ugm6hr on 2009-01-25
> **simapex said:**
> There seems to be some issue with applications, as I could get to run exe. programmes which I had downloaded, such as yahoo messenger, and the rest of it. 

Would I require special application to get such programmes to work?

Unfortunately, most .exe programs will not work.

.exe programs are for **Windows**.  You have installed Ubuntu **Linux**.

There are ways to make a few .exe programs work, but it is not straightforward.  Certainly, Yahoo Messenger will not work.

---

### Post by anewguy on 2009-01-25
do keep in mind that ubuntu has many programs to take the place of Windows programs, and things like Yahoo messenger can be replaced with kopete (may have a different name now) pigin (sp?), etc..  Search the forum and the net for more info on what people are using, then go to synaptic package manager and install the one(s) you want.

Dave :)

---

### Post by simapex on 2009-01-26
Thank you

---

