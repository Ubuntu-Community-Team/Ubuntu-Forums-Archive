---
title: "Can't get on internet with Netgear NIC"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by Metalica77 on 2007-08-16
Ok guys today I finally got another computer from a friend and i've installed ubuntu on it and i can't seem to get online.

I've already talked to my linux buddy and he also can't seem to help me get online.

Sadly this new computer doesn't have an onboard motherboard eithernet port so it is much harder for ubuntu to make drivers for it.

Although i have a Netgear card inside and it still can't seem to work. We've gone through many things and it just doesn't work. I would like much if someone can help me out.

Thx in advanced

The main reason i need a linux box is for my parents and visitors so they can't screw up my main machine.  I would really like to see what the hype is about and this is the only thing stoping me:(

---

### Post by noob12 on 2007-08-16
It sounds like you have an internal PCI network card.  We need to know the details of what device you have.  Posting the output of these commands will tell us what you've got and how far along the setup is:
```

lspci -nn

sudo lshw -C network

ifconfig -a

```

---

### Post by Metalica77 on 2007-08-16
Ok i wasn't sure which one you wanted.  

[http://img248.imageshack.us/my.php?image=otherscreenshotbu1.png](http://img248.imageshack.us/my.php?image=otherscreenshotbu1.png)

is that it.  I went through hell connecting stuff together i must have moved my mouse and keyboard and VGA cable like 15 times:mad:

---

### Post by noob12 on 2007-08-16
If you can find a USB flash drive, you can use that to transfer files between the disconnected computer and another one that you can use to connect.

That screenshot only shows the output of the first command.  I did see you have a Realtek 8169 based ethernet card.

The driver for this normally does ship with Ubuntu and should claim the device automatically.

---

### Post by Metalica77 on 2007-08-16
I honestly have no idea why it says realtek because the motherboard has no onboard eithernet it's my netgear NIC so i don't know why it says that

---

### Post by noob12 on 2007-08-16
Oh.  That's no surprise.  Netgear is the overall board manufacturer.  On that board there's a chipset that's the real ethernet device and that determines what driver is needed.   That Netgear board has a Realtek 8169 chipset.

I can try to walk you through the diagnostics sight unseen but that seems less than likely to succeed.  If you have a flash drive, you can transfer text file output from the box to your other computer and send the output of those commands back.  That would be best.

If you can't do that, we can try to walk through this with you being the eyes.  It is probably going to be slow and we may not spot something that is the clue.

---

### Post by noob12 on 2007-08-16
Let me know which way you want to go.

---

### Post by Metalica77 on 2007-08-17
> **noob12 said:**
> Oh.  That's no surprise.  Netgear is the overall board manufacturer.  On that board there's a chipset that's the real ethernet device and that determines what driver is needed.   That Netgear board has a Realtek 8169 chipset.

I can try to walk you through the diagnostics sight unseen but that seems less than likely to succeed.  If you have a flash drive, you can transfer text file output from the box to your other computer and send the output of those commands back.  That would be best.

If you can't do that, we can try to walk through this with you being the eyes.  It is probably going to be slow and we may not spot something that is the clue.



Ok yes i have a flash drive.  I think i wana do that idea because it is less idiot proof ](*,)

Ok what do you mean "output from the box"  and "send the output of those commands back"

I understand it like this.  You tell me what code i need to put into the terminal and i take a screen shoot of the reaction and then we relay information right? If so sounds good i'm in


One more question is the netgear problem raised all the time?

Thx for your help

---

### Post by noob12 on 2007-08-17
No screen shots.  Text files.  Just cut and paste the output into  text files.  You can transfer them to your other computer and post.

Run the commands
```

sudo lshw -C network

ifconfig -a

```

Note that when you type anything with "sudo", you may be asked for a password.  You need to type your own password to have it proceed.  This lets you run commands as the admin (root) user on your box.  It seems like you were confused about this the last time.

The command **gedit** will bring up an editor window that you can use to paste into.
Finally save the file to your flash disk and you can move that to your other computer to post to the forum.

---

### Post by praxis22 on 2007-08-19
>I can't get my Netgear Card to work under linux it's bullshit
>
>[http://ubuntuforums.org/showthread.php?p=3197478#post3197478](http://ubuntuforums.org/showthread.php?p=3197478#post3197478)
>
>
>come there and HELP ME

Do like the man says, and provide the output for the commands in question.

When it asks you for a password, it wants **your** password, the one you login with.

To copy and paste you place the mouse at the start of the text, press the right mouse button and drag to the end of the text. Then in gedit, just hit the left mouse button and it will past the text you just copied.

If you feel uncomfortable about doing this, you can use the copy and paste commands from the terminals edit menu, then use the same in gedit, just like in windows. 

Since people have other things to do beside helping you, patience is a virtue.

---

### Post by praxis22 on 2007-08-19
Noob12,

Don't mean to step on your toes but I  had a quick google and I found the following:
---

it is already in the kernel

networking drivers -> 1000 -> realtek 8169

---

I've installed it using ACPI-Off mode and then loaded grub using the following boot options:
acpi=noirq
acpi=off
noapic
noapm
pci=noapic

Simply turning off all power management in linux works, it now easily detected my mouse, network, bluetooth, sound, usb hard drive, 
flash drive, and probably more, but I haven't had the time to check that yet...

Linux drivers from realtek:
[http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110S-32/RTL8110SB(L)/RTL8169SB(L)/RTL8169SC(L)/RTL8169](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110S-32/RTL8110SB(L)/RTL8169SB(L)/RTL8169SC(L)/RTL8169)
"Linux driver for kernel 2.6.x (support x86 and x64)	6.002.00	2007/7/20"

---

### Post by noob12 on 2007-08-19
No toes damaged.  That's why it's a forum and not a series of PMs.   One of the problems in this area is that many user's symptoms look superficially similar but have different causes;  users can lose patience providing the diagnostics; in cases where they have no networking at all it does get quite painful.  In cases where a one or more PCI devices aren't working, disabling ACPI, particularly for PCI routing on boot can definitely help.  Typically one sees indications of issues in the dmesg / kern.log .  It's not a bad suggestion though.  In this case you'll probably need to include instructions on how to set flags during boot.

I'm going to be away from the forum for a week, and I won't be able to respond during this time.  I hope praxis22 can help you out metallica77.

---

