---
title: "Boot up Ubuntu under command line and copy files from it?"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by PreciousBodilyFluids on 2011-04-05
I was running Ubuntu on a laptop (with the encrypted home directory option) when it suddenly died. I'm thinking that it's a problem with the video card, because both Ubuntu and WinXP (I was dual-booting) showed the same incomprehensible graphics when I tried to boot them up, but memtest runs just fine (though some of the characters are weird colors). No matter, the most important stuff was backed up, it was an old laptop anyway, and I took the opportunity to build a new desktop system.

Now I'm trying to pull my music collection (which wasn't backed up, stupid me) off the laptop's hard drive before I junk it. I don't have another laptop to put the hard drive into, but I think the old laptop would work fine if I could get Ubuntu running under the command line only. Then I could connect my desktop to it and just copy things over.

So, two questions:

#1. How do I get Ubuntu running under the command line? I've searched on this, but all the solutions I find assume that you can first do some setup in the usual graphical mode, which I can't.

#2. Once I get it running under the command line, how do I access the (encrypted) contents of its hard drive from my desktop?

Thank you so much!

---

### Post by nothingspecial on 2011-04-05
After boot, press Ctrl-Alt-F1 will bring up a console.

How do you want to copy the music, via usb or over your lan?

---

### Post by PreciousBodilyFluids on 2011-04-05
Thanks nothingspecial - Ctrl-Alt-F1 didn't work, but while I was experimenting I chose one of the recovery kernels in GRUB and it let me choose a command prompt with networking. So now I'm logged in as root at the command line.

I was planning on doing it over my LAN, but it looks like I'll have to unencrypt the home directory. Or log in under my own account somehow?

Thanks!

---

### Post by PreciousBodilyFluids on 2011-04-05
Ok, I figured out how to login as myself, and I can browse through the directories in my home directory. Now to just figure out how to transfer them through the LAN.

I'm trying to use the "Connect to server" app from my desktop PC, but all I'm getting is "Cannot display location sftp://chris@192.168.1.111/home Connection refused by server". I think I've been able to use that in the past to transfer files, but it's not working now...

---

### Post by nothingspecial on 2011-04-05
Install openssh-server

Then choose ssh from the connect to server menu

---

### Post by PreciousBodilyFluids on 2011-04-05
That did it! Turned out I already had it installed, it just wasn't running for some reason.

Thanks!

---

### Post by Daniel0108 on 2011-04-05
> **PreciousBodilyFluids said:**
> That did it! Turned out I already had it installed, it just wasn't running for some reason.

Thanks!

Please mark this thread as solved,

Daniel

---

