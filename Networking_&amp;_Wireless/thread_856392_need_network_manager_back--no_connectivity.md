---
title: "need network manager back--no connectivity"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by scholzilla on 2008-07-11
Hi,

I made the mistake of installing wicd on my box, which removed the network manager package. Where network manager was dropping wireless connections but always stable with wired connections, wicd won't connect wirelessly or wired. That means I can't reinstall network manager from my machine. I went to the gnome site to download network manager onto another machine so I could burn a disk and transfer it to my machine, but the file won't copy to disk. I keep getting a message saying that there is additional information attached to the download that won't be copied, and then the copy fails. PLEASE help me restore network manager. I promise I won't use wicd again.

Is there a way to reinstall just network manager from the ubuntu cd? I don't want to reinstall the whole OS.

---

### Post by james_vanb on 2008-07-11
I think you can set your Software sources to load from the install cd and then reinstall the network manager through Synaptic.

---

### Post by scholzilla on 2008-07-13
Unfortunately, I wasn't able to get this to work. Synaptic doesn't see a network manager package that it can install from disk even after adding the disk to software sources (it does see other packages). So I can't copy the version of network manager from the gnome site to disk on another computer and transfer it to my laptop, and I have no connectivity on my laptop. Am I screwed or is there some fix? I really don't want to reinstall the OS for the 3rd time.

---

### Post by imdano on 2008-07-13
You can probably just make sure your ethernet wire is plugged in, then open up a console and type ```
sudo ifconfig <wired interface> up
sudo dhclient <wired interface>
```And get connected.

---

### Post by scholzilla on 2008-07-13
you're a beautiful human being. I'm almost there. I did:

sudo ifconfig eth0 up
sudo dhclient eth0

to get online, then ran:

sudo apt-get install network-manager-gnome

Install went fine, except a launcher icon was not created. I tried doing this by right-clicking my desktop to add launcher, but I can't figure out what file I want to connect this to. Is there an easier way?

---

### Post by james_vanb on 2008-07-13
I think it's located at /usr/bin/nm-applet

---

