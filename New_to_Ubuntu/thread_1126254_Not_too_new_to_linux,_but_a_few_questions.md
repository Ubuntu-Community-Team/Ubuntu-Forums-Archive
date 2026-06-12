---
title: "Not too new to linux, but a few questions"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Atallicus on 2009-04-15
Hello everyone, been a long time since I've been around here.  Usually in the past I've used a dual boot of linux and windows.  Now with raided hard drives that is pretty much impossible and I'm thinking of making the big jump to just a linux install.  I have a couple of questions before doing so.

1) My Zune mp3 player is very important to me :D  Will I be able to use the software on linux?

2) I used to run world of warcraft using wine.  Has that process gotten any easier and if so, does it still have the mouse issues with opengl that it did before?

Beyond that, I'm pretty sure everything else I own will work fine.  Thanks for taking the time to answer.

---

### Post by Jakey_TheSnake on 2009-04-15
As far as I'm aware, you can't sync to your Zune from linux without installing VMWare, then the software. According to: [http://gizmodo.com/gadgets/portable-media/zune-on-linux-done-kinda-219657.php](http://gizmodo.com/gadgets/portable-media/zune-on-linux-done-kinda-219657.php) you have to remove your USB 2.0 drivers as well. 

Microsoft just hate being compatible. 

Check out the Wine apps database.

---

### Post by aktiwers on 2009-04-15
I think both Wine-doors and PlayonLinux can install and configure wine to run WOW fine for you.

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)
[http://wddb.wine-doors.org/](http://wddb.wine-doors.org/)

---

### Post by Atallicus on 2009-04-15
> **Jakey_TheSnake said:**
> As far as I'm aware, you can't sync to your Zune from linux without installing VMWare, then the software. According to: [http://gizmodo.com/gadgets/portable-media/zune-on-linux-done-kinda-219657.php](http://gizmodo.com/gadgets/portable-media/zune-on-linux-done-kinda-219657.php) you have to remove your USB 2.0 drivers as well. 

Microsoft just hate being compatible. 

Check out the Wine apps database.

I'll take a read of that article.  It seems weird that I'd have to uninstall USB drivers to use a USB device, so I better read it.  Thanks for your help so far.

---

### Post by Atallicus on 2009-04-15
That sounds kind of....icky ha ha.  An unforeseen issue my husband just realized also is that I won't be able to transfer music from his pc to mine over the network either.  That's kind of a road block for me.

The biggest issue why I stopped running linux in the first place was a dual boot with raided drives just didn't work.  I have 2 250gigs raided for windows, then I had a 160 drive with linux on it.  Every time we tried to install linux, grub blew up the raid.  If we unplugged the raid drive, it still didn't work.

---

### Post by Nostalos on 2009-04-15
Zune works under VirtualBox at USB 2.0.  Zune Software has a few quirks though.   It's really not happy about no direct x and has issues with delay when storing your music on a shared folder.

I created a virtual disk to store my music on and a filter in the USB settings so my zune goes straight to the Vbox instance.  If you don't add the filter you have a 50/50 shot of your system actually seeing the zune.

---

### Post by Jakey_TheSnake on 2009-04-15
^ Why don't you create a thread about that, instead then? 

And I'm pretty sure you could still network them :)

> **Atallicus said:**
> I'll take a read of that article.  It seems weird that I'd have to uninstall USB drivers to use a USB device, so I better read it.  Thanks for your help so far.

I thought that too, but it's only the USB2.0 drivers, so 1.1 would still work ;)

---

### Post by gali98 on 2009-04-15
You could always buy a usb hard drive and install ubuntu there. Then just set your bios to let you choose what device you wanted to boot from.
Kory

---

### Post by Atallicus on 2009-04-15
I wasn't aware I had to create a new thread to explain something about why I was posting the topic in the first place.  Sorry for that.

As for the network thing.  I usually access his music drives from my computer, but I'm not sure how that would work in linux.  I know that I can view my own windows drives on a dual boot, but how does that work over the network?

---

### Post by Nostalos on 2009-04-15
I assume his box is a windows box?  Accessing it from linux is no harder than from windows.   Also if you install VMware or Virtualbox you will attache to it the same as you do no.    Regular network shares seem to work fine for my zune software. it just doesnt seem to like the Folder sharing Vbox does.



On another note.  Why does having a RAID'd drive keep you from dual booting???

---

### Post by Atallicus on 2009-04-15
Yes his box is a windows box.  I'll have to do some research into the stuff you've talked about, I'm not too familiar with those kind of programs.

The problem with the raid drives was that when linux would try to install grub, it would break apart the raid.  We tried to install it by unplugging the raid drives, and I don't remember what happened with that, but that didn't work either.  So then we tried unraiding the drives, using 2 for windows and the 160 for linux.  That worked....sort of.  The second windows drive was my music drive, so I had that set up to use from linux.  But when I would go to the windows drive, the music drive would disappear until went back over to linux and viewed it.  It didn't make any sense to me.

---

