---
title: "2 Items fail on boot"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by dabellator on 2009-01-04
Ok, since I am very new to this I think I should post in the beginner forum!  I had some trouble getting 8.04 installed on a system I inherited that was running 6.06 (I think that was the version), but wanted the newer version because it didn't seem to be running right.  I ended up having to upgrade instead of doing a clean install.  After install my monitor wasn't being detected (it's a Lacie CRT) and it was defaulting to a plug and play monitor, so I used the generic driver and know it looks a little better.  I wondered if that would be a sign I was having some driver issues and then I noticed when I boot up I receive two different errors:

Loading Hardware Drivers = failed
Setting Kernel Variable = failed

Then I am having a few little issues as well, for example, when I go to shut down it seems to go through the process, screen goes black, but the system never powers down.  Any ideas what I could start troubleshooting?
-JB

---

### Post by ibizatunes on 2009-01-04
May i suggest you do a clean install of either 8.04 or 8.10 
Backup your date first, you may want to put your home drive on a different partition to your os, 
Also want specs is your machine?

---

### Post by Michael.Godawski on 2009-01-04
I would also suggest a clean install of 8.10.

Upgrading was hit or fail for me. A fresh install did always better.

---

### Post by dabellator on 2009-01-04
Thanks for the quick reply, you guys are going to keep me coming back to Ubuntu, awesome community!

I had a feeling you would recommend a clean install, which is why I mentioned it was an upgrade.  Problem is, when I first started this process I tried installing from a CD I had downloaded.  I selected my language, location and keyboard then got to a status bar, but after it loaded it pooped me out to a command line.  Maybe I should have done more research, but I couldn't find any instruction on what to do at that point.  Is there something wrong with my CD or am I just a complete beginner?
-JB

---

### Post by dabellator on 2009-01-04
Sorry, I forgot you asked about my specs, I just cut and pasted some info from the "lshw" command:

  *-memory
          description: System memory
          physical id: 0
          size: 479MiB
     *-cpu
          product: AMD Duron(tm) processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.7.1
          size: 1300MHz
          width: 32 bits
 *-display
          description: VGA compatible controller
          product: VT8375 [ProSavage8 KM266/KL266]
 *-multimedia
          description: Multimedia audio controller
          product: VT8233/A/8235/8237 AC97 Audio Controller
          vendor: VIA Technologies, Inc.
          physical id: 11.5
          bus info: pci@0000:00:11.5
          version: 50
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
          description: Ethernet interface
          product: VT6102 [Rhine-II]
          vendor: VIA Technologies, Inc.

---

