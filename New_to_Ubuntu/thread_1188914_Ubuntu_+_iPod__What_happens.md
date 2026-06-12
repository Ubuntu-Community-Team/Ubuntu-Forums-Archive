---
title: "Ubuntu + iPod?  What happens?"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by LinuxFox on 2009-06-16
Using my iPod nano is just making me want to ask a quick question.  What exactly happens when I connect my iPod to Ubuntu?  I remember trying to plug it in once on Ubuntu to charge it a few months ago, and Rhythmbox opened up.  Was it reading it or uploading it?

Please answer my question. Though I use my Windows partition to manage it, I just want to know what happens when it's plugged into Ubuntu.

---

### Post by Jazzy_Jeff on 2009-06-16
It should just open it up. I have an older Ipod and nothing happens with it until I tell it to.

---

### Post by sideffects on 2009-06-16
You can use your iPod with various programs in Ubuntu. For instance Rhythm Box, Songbird, and Amarok. There are others, just do a Google search for an iPod manager in for Ubuntu or Linux.

---

### Post by SOULRiDER on 2009-06-16
Ive used an iPod nano on my Ubuntu machine with Rhythmbox, and basically you can use RB to copy music over etc. just as you would with iTunes.

---

### Post by snakeman21 on 2009-06-16
IMO, the two best programs to use with an iPod are Rhythmbox and GTKpod.  They will both recognize and sync your iPod without a problem. I personally prefer GTKpod, it's what I use with my Nano, but as stated above, there are several programs that can do it.  You may want to look at some reviews, then download a few from the repos and decide which one you like the most.

---

### Post by Simian Man on 2009-06-16
I actually prefer to use Rhythmbox over iTuens for my iPod Nano.  It works perfectly and is a lot simpler.

---

### Post by raymondh on 2009-06-16
As snakeman21 ... I too use gtkpod with no problems for both ipod and touch (touch being the 1st gen and not jailbroken)

---

### Post by snakeman21 on 2009-06-16
> **Simian Man said:**
> I actually prefer to use Rhythmbox over iTuens for my iPod Nano.  It works perfectly and is a lot simpler.

I'm not a Rhythmbox fan, but I'd say the same about GTKpod.  iTunes is just a pain to use.  When I switched to Ubuntu, I was a little worried about finding a simple program for my iPod. But someone told me about GTKpod, so I tried it and was like, "Wow!  This is SO much easier!"

Praise Linus!

---

### Post by Am Elder on 2009-06-16
I'm relatively new to Linux, and you have some practical answers about iTunes alternatives already.  Let me try this more general answer:

**Short answer:** don't worry just plugging your iPod into your computer doesn't change anything on the iPod.  On my computer, with 9.04 Jaunty, I get a dialog that gives me the choice of what program I want to read the iPod with, Rhythmbox or GTKPod or just the file browser.

**Long answer:** When you connect an iPod to a machine running Ubuntu, the operating system does what it does with any other usb device: it mounts the device in the file system.  This means the operating system lists the ipod in an index of all the disks available to the computer.  Ubuntu also creates a file in the file system so it can treat the iPod as part of the file system.  The default location for this file is */media/ipod_name.*  None of this changes what's on the iPod.  Mounting the device is only reading the data already on your iPod.  If you click the "Enable Disk Use" check box in the *Summary* tab in iTunes, you will be able to drag files over to the iPod without using a music manager, otherwise the disk will be read only.

---

### Post by ptn107 on 2009-06-16
Songbird[1] is the winner for me.  It's an open-source clone of iTunes complete with iPod support and the capability to read/import your entire iTunes library.

_[Get Songbird 1.1.2 for Linux 32-bit]("http://download.songbirdnest.com/installer/linux/i686/Songbird_1.1.2-1042_linux-i686.tar.gz")_
_[Get Songbird 1.1.2 for Linux 64-bit]("http://download.songbirdnest.com/installer/linux/x86_64/Songbird_1.1.2-1042_linux-x86_64.tar.gz")_

---

### Post by LinuxFox on 2009-06-16
Thanks for all the answers, it helps clears things up about iPod being connected to Ubuntu.  I was just concerned since Rhythmbox opening up by itself was just too weird.  Though I didn't know there were other programs that work with an iPod.

---

### Post by Am Elder on 2009-06-16
You're right, Rhythmbox opening on it's own is strange.  That's been fixed in more recent versions of Ubuntu.  Now there's a dialog that asks you what you want to do with the device.

---

