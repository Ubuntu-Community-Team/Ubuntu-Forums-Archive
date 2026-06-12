---
title: "Creating a Boot disk on an external HDD"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by guwar on 2009-02-15
Hi,

I'm a total beginner to Ubuntu but want to check out it's possibilities (or rather MY possibilities in adapting to another OS - I hate to admit to being a Microsft formatted drone, but he, I'm trying to break free right ?).

I've looked around on the existing threads and I've looked in the help documentary - but not found answers to this particular question.

What I wanted to know is, is it possible to install Ubuntu onto a completely clean external hard disk drive and thus create a bootable portable Ubuntu alternative to discover little by little at home and at work.
Until a replace Vista for good.
I hate Vista - I've always hated Windows, but Vista sucks even more than most. But then you all know that anyway !

Is it possible to just mount the iso file I've downloaded today from the Ubuntu downloads page, onto a virtual drive on my computer and then copy and paste that onto the NTFS formatted external hard disk drive.
Would that work.

I could just give it a try - but is there a better way, or a more complete way to install Ubuntu onto an external HDD - as I gather the bootable CD installation possibility isn't a complete Ubuntu install.

Thanks a lot for any help or suggestions.

Guy

---

### Post by malusdomestica314 on 2009-02-15
Here is a link to instructions for installing the latest Ubuntu (8.10) onto your harddrive:
[http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/)

It should work just fine, although the options mentioned in that article are not available for 8.04 so make sure your using the latest release. It's a fairly easy process and afterward you should be able to boot from your external USB harddrive, provided your BIOS is able to let you boot from USB (I think if your computer was built from '05-'06 on up you shouldn't have to worry about that)

Have fun! Hope you enjoy Ubuntu!

---

### Post by guwar on 2009-02-15
Well I nearly figured it out.
I didn't do things the way you suggested simply because I have no blanck CD's at the moment. I mounted the CD onto a virtual drive and went as if to install parallel to Windows on my C drive. When prompted for the drive I chose my HDD and installation was aborted half way through. I then went into the disk managemùent and made my HDD a live drive and the install went without a problem. I chose boot from an external device as the first in my boot list in Bios.
OK so far. I boot up. Get the choice of Ubuntu or Windows. Coose Ubuntu and it begins to boot from my HDD.
Still OK.
I get to the username and password screen and no longer have mouse or keyboard !
I'm using a cordless, bluetooth Logitech MX 5500 (cost me a bundle) but is there a problem with configuring peripheral hardware ?
I've as yet to start-up Ubuntu and can't because it doesn't seem to recognise my keypad and mouse, necessary in order to start-up.
So close yet so far.
Any ideas?
Does the method you mention by-pass this problem?

Thanks for your time.

---

### Post by malusdomestica314 on 2009-02-15
Do you have a regular USB or PS/2 mouse and keyboard you can hook up? I'm thinking your problem might just be that Ubuntu hasn't automatically picked up on your keyboard and mouse, so if you have some regular, wired ones to use just so that you can login, we can start on getting your keyboard and mouse to work.

Edit: Your keyboard seems to have a track record of not playing well with Linux, especially on 64-bit, is the Ubuntu you're using 64-bit or 32-bit? Also, from what I've read [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291269/comments/2"), the alternate-install CD doesn't seem to have that issue. I'm thinking that if you do the same thing you did the first time to get Ubuntu onto your hardrive, but with the alternate install instead of the live CD, all you'll need to do is reset the bluetooth connector that came with your keyboard and mouse when you boot into Ubuntu. Of course, you may want to try simply resetting your bluetooth connector before going through everything else with the alternate-install CD.

---

### Post by guwar on 2009-02-15
Thanks for your suggestions.
I'll pick-up a blank CD and give a reinstall that way a try.
I'm kind of wary of installing on my hard drive as I've had previous bad experiences with hard drive failures and also with dual installs.
Most probably not connected - but still. An external HDD gives me a greater feeling of security.
I'll let you know how I get on !

Thanks again.

---

### Post by malusdomestica314 on 2009-02-15
You're most welcome! I hope all works out well for you, but I'll be glad to help if things don't quite work out.

By the way, I noticed you're a new user, so if anyone else hasn't yet, let me be the first to say Welcome to the Ubuntu Forums and Welcome to Ubuntu!

---

### Post by guwar on 2009-02-17
Thanks - yes I'm a totally new user.
Or at least I would be - only I can't get it installed.
I've burnt a bootable CD, tried installing on my external drive, but it doesn't boot up (the boot sequence is fine, but it just doesn't load the mouse and keyboard).
OK - atwork I installed the CD Ubuntu next to my Windows and tried bootingup. I choose Ubuntu at the beginning and I block at the beginning. A black screen with several choices and a prompt, but no Ubuntu boot-up. I didn't note down the exact message. I'll try booting again and note down the messge this time.
But it's kind of frustrating.
For all my criticisms - I've never had a problem installing Windows !

Any help would be appreciated.
What could I be doing wrong.
Installation on the internal hard drive, alongside windows should be easy, No ?

---

### Post by guwar on 2009-02-17
So I'm back already !
I tried booting from the external drive - error message ntldr error.
Which means that somehow the drive isn't bootable right. Don't know why the install on the external drive didn't work, but I'll try and install again.
From the CD - the boot-up goes fine - I get the Ubuintu loader. When it's finished loading I get a black screen with a blue box in the middle. In the blue box a grey text zone with the error "video mode not supported).

I'm beginning to think that Ubuntu just isn't for me !

---

### Post by malusdomestica314 on 2009-02-17
Hey, don't worry! My first Linux install didn't go quite well either, but I've had my share of nightmare Windows installs, too. I'm sure we'll get this fixed.

NTLDR is the Windows bootloader, so I would expect that you'd be getting that error trying to boot Windows, not Ubuntu. You're getting this error when you try to boot Ubuntu from your external drive, right?
What filesystem is your Ubuntu partition on? Ext2, Ext3, something else?

Anyway, what I would try to do is download the alternate-install CD for Ubuntu and install that to your external HD. Based on the issues your having, I don't think we should be comfortable putting in on the internal HD until we know how to fix this. You're going to need a regular mouse and keyboard, do you have the ones that came with your computer originally? Those should be just a couple of generic (although branded) mice and keyboards, and those will work just fine. Your bluetooth keyboard and mouse seem to need to be specially configured once you boot into Ubuntu, so you'll need the generic ones for getting to that step, it seems.

Once you get the alternate-install CD, I would just install right over the Ubuntu install you previously had on your external HD, just format the whole partition (or the whole disk if your using the entire drive for it right now). If it asks you what filesystem you want just pick ext2 or ext3, but which one is a rather irrelavent detail at the moment, if you want my advice, I'd go with ext3 though. But just go with whatever is default if it chooses one for you.

Anyway, I'm thinking your problems may be part of an issue that occured during the first install, we'll see though. If reinstalling Ubuntu isn't something you're quite looking forward to at the moment then I'll try to come up with a different method, but this seems the most straightforward at the moment. I have to leave now, but I'll be back later if you run into more trouble.

---

### Post by guwar on 2009-02-18
OK - I'l try reinstalling and using a generic keyboard and mouse.
When formating the drive, I only had one choice for the file system, NTFS.
No possibility to choose ext2 or ext3. I reformatted as an active disc whereas my C: drive is a system disc; Is this the source of the problelm. Does the External drive have to be a system disc too, in order to boot from ?

---

### Post by malusdomestica314 on 2009-02-20
Um, I don't think it matters, active or system disk, however, I may be a little rusty on my Windows, so I'm not sure. NTFS should be fine if it was the only option you were given during the install.

Let me know how it goes and good luck!
BTW, sorry for taking two days to answer, schooling has eaten up a lot more time than I expected it too this week.

---

