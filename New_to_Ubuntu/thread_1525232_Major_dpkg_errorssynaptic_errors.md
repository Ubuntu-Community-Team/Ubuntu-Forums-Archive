---
title: "Major dpkg errors/synaptic errors"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by TwiztidChef on 2010-07-06
Ok, so I woke up today and logged onto my ubuntu. I tried to open firefox, it said firefox loading but never did. I tried several times, then shutdown and tried again. No luck. So I figured I'd remove and reinstall. Whenever I go into the terminal and use sudo-apt get remove firefox I get this error:

(Reading database ... 70%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `localepurge': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


Everytime I get it, and the database gets stuck at 70%. I can't open synaptic because it says the same error. I tried update manager and I get the same error, everything gets stuck at 70%. 

Something else, weird. I tried to shut down my laptop from the button on the task bar, and it wouldn't, it would reboot everytime. I had to go through the terminal. 

Any ideas? I've searched all through google. This is kind of a system breaker. I can't install, remove, or update anything. I've got over 150 gigs, of files saved that I don't want to lose, so a fresh install isn't really an option.

Please some help?
(running Ubuntu 10.04 64 bit)

---

### Post by Temposs on 2010-07-06
First, you shouldn't need to reinstall firefox in order to get it to work. That will usually do basically nothing, even if there is a problem with firefox.

Can you open System->Admin->Software Sources, and tell me what is checked in the "Ubuntu Software" tab, and also what is listed in the "Other Software". Also, in System->Admin->Synaptic Package Manager, try Edit->Fix Broken Packages. You can also try to open Apps->Accessories->Terminal and type:

```
sudo dpkg-reconfigure -a
```

See if any of that helps.

---

### Post by TwiztidChef on 2010-07-06
Using the fix broken packages did nothing. I've been using sudo dpkg-reconfigure -a. I was finally able to get back into synaptic. Everything I try and update/download/remove gets stuck at 70%. I've been able to get fire fox to start, but I had to use the terminal and I had to start a new profile. Which didn't let me access any of my add ons/bookmarks.

The main problem is this dpkg error. I can't do anything without it.

My software sources from the other tab are:

[http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) feisty
[http://packages.dfreer.org](http://packages.dfreer.org) gusty
Mediabuntu - Ubuntu 10.04 "lucid lynx"
Mediabuntu (source) Ubuntu 10.04 "lucid lynx"
[http://ppa.launchpad.net/jinto/mediatomb-js/ubuntu](http://ppa.launchpad.net/jinto/mediatomb-js/ubuntu) lucid
Ubuntu Tweak Stable Source

I had no problems last night, then I get up this mourning and my system is broken, I don't get it.

---

### Post by TwiztidChef on 2010-07-06
bump. 

I can't do anything, every process stops when it goes to read the database and gets stuck at 70%

---

### Post by TwiztidChef on 2010-07-07
It seems maybe that my dpkg is broken. I see no way to fix it. I'm thinking of running FCSK. I've used it in the pass after an improper shutdown corrupted my system. Its warning me that is could have disasterous consequences. So I guess I need to buy an external hard drive first.

Any thoughts or ideas? this is a really annoying bug.

---

### Post by hansdown on 2010-07-07
Hi TwiztidChef.

When you click System> administration> software sources, it should not contain references to;
                     1:feisty
                     2:gutsy

Uncheck those boxes, and, open a terminal.

applications> accessories> terminal.

Copy and paste this, into the terminal

```
sudo apt-get updates
```

---

### Post by TwiztidChef on 2010-07-08
That didn't work. I think I had those check for working with Mediatomb.

Everything I run though the terminal stalls at 70%. To even open Synaptic I have to run Sudo dpkg --configure -a. Then if I make a change it halts at 70%, and I get the error I described in my first post. 

It seems that when I was removing some programs the system halted and it has locked dpkg in the process. auto-remove gets halted, I can't manually remove a program. Synaptic, the terminal and software center all return the same errors.

This is really annoying. I rarely have problems with Linux, but when I do its always a ****ing doozy. I plan on try fcsk this weekend. I have to go buy a 1TB external with eSata first though. I really don't want to do it, but If I can't update, or add/remove programs then thats kinda of a big deal.

Any more ideas are greatly appreciated.

---

### Post by TwiztidChef on 2010-07-08
bump

---

### Post by hansdown on 2010-07-08
Sorry to take so long,TwiztidChef.

I've been searching for an answer, but haven't found much.

Just a long shot, since you were installing a package, when this started.

```
sudo apt-get install -f 
```

And to clean some old files,

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

---

### Post by TwiztidChef on 2010-07-08
Tried those already. Same problem, have to run sudo dpkg --configure -a, then when I retry it stops at 70%.

I'm gonna buy that hard drive tomorrow, then try the fcsk. If that doesnt work I'll reinstall. 

At least this time I'll be able to back up everything.

Thanks for trying, if you find anything else out post it, I wont do the wipe till tomorrow night or maybe wait till sunday.

---

### Post by hansdown on 2010-07-09
Let us know how things work.

Wish There was more info.

---

### Post by TwiztidChef on 2010-07-11
Well fcsk seemed to only break packages even further. I bought my new hard drive, and Iomega 1TB external for 80 bucks. Backed everything up and reformatted. System is running smoother and I've got almost everything back in order now. 

Only annoying thing is the transfer speed to my HD, I only got speeds up to 30 mb/s. The drive is supposed to be around 400. All my USBs are 2.0, and I have an eSata/USB port, but ubuntu wouldn't detect that one. But an hour to transfer 120 gigs isn't so bad.

---

### Post by hansdown on 2010-07-11
I'm glad you're getting things sorted, TwiztidChef.

---

### Post by TwiztidChef on 2010-07-12
So get this. Now my internal hard drive is failing. I reformatted, and then my hard drive starts clicking alot, and normally mine is absolutely silent. Then I noticed, I didn't add a swap partition, and wasn't sure of how to do is, so I reformatted again, same day. Its still doing it. Ran a disk scan and have like 300 bad sectors. Now I have to replace the hard drive.

Luckily, I have an accidental damage warranty. Called, told them it fell, I'm supposed to get a call tomorrow about shipping.(plus they are fixing my volume knob and the esata port.)

I'd figure I'd ask here, instead of a new thread. I think I'm gonna out my old system restore disk, so they don't try and give me **** saying ubuntu is the problem. Is this gonna securely wipe my HD? I don't want the whoever gets this laptop for repair, to be able to see any of my data/info.

Damn, I've had a crappy week for my computer.

---

### Post by hansdown on 2010-07-13
Ouch! Well, at least they are going to replace the drive.

You could use a live ubuntu install disk, to reformat the drive to ntsf. It's a lot faster than d-ban, which can take hours, but is also very good.

[http://www.dban.org/download](http://www.dban.org/download)

Post back if you need more info, TwiztidChef.

---

### Post by TwiztidChef on 2010-07-13
Ah cool, I was looking for something like this, but could only find windows/mac versions.

I can't wait to get this done with. They didn't call me today, so I'm hoping they call tomorrow. I just hope they don't give me some **** about it not being working. 

Its working now, but if I run Devede, or anything labor intensive, or even Vuse, it shuts down.

Thanks for the help hansdown, I'll post if I have any more problems.

---

### Post by NO_oB on 2010-07-13
I get the same error :( 
When i try to run sudo apt-get autoclean i get this:"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

And sudo apt-get update:"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."


And sudo dpkg-reconfigure -a:
   * Disabling power management...                                         [ OK ] 
  update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
  update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
   * Checking battery state...                                                    
  /dev/sda:
   setting Advanced Power Management level to 0xfe (254)
                                                                           [ OK ]
   * Stopping ACPI services...                                             [ OK ] 
   * Stopping Hardware abstraction layer hald                              [ OK ] 
   * Loading ACPI modules...                                               [ OK ] 
   * Starting ACPI services...                                             [ OK ] 
   * Starting Hardware abstraction layer hald                              [ OK ] 
  pycentral: pycentral pkginstall: error byte-compiling files (6)
  pycentral pkginstall: error byte-compiling files (6)



before that fsck forced verification of hdd and gived me alot of errors :icon_frown:

Maybe my hard drive is failing too? :cry:

---

### Post by TwiztidChef on 2010-07-14
I found out by : System/Administration/Disk Utility. Clicked on my main hard drive, and ran a smart scan. The status says, Disk has a few bad sectors. I googled this, and this is a major problem. My HD is clicking alot, and when it gets really busy it made a screeching sound. I have around 400 bad sectors. I keep getting more every day. 

If you have a way to back it up, I'd advise you to do so in case something goes really wrong.

---

### Post by NO_oB on 2010-07-14
Thats the problem..i dont have another hard drive to make a backup :cry:

---

### Post by TwiztidChef on 2010-07-14
I don't know how things are in Portugal. But here I got a 1TB for 80bucks. You can get a similar price on TigerDirect.com, I've seen 250 gigs for around 40 or 50 bucks too. Or you can always burn some essentials on data disk DVD-r's. Flash drives are cheap, as are SD memory cards.

Good luck dude

---

