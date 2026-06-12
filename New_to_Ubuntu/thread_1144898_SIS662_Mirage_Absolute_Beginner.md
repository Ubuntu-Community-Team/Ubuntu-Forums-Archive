---
title: "SIS662 Mirage Absolute Beginner"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by cbanakis on 2009-05-01
I have been struggleing for about a year now trying to solve this problem.
 
I'm trying to get Ubuntu up and running on a Shuttle XPC SS30G2.
 
I would like to switch all my computers over to Linux, but if I cant solve a problem as simple as this, I fear I may only be qualified to deal with MS Windows and their BS.
 
The problem I am facing is with the onboard SIS Mirage 1 graphics card.
 
I have spent years building windows based systems, and thought I knew quite abit about computers.  But now that I'm attempting to make the switch to Linux, I feel like a complete moron.
 
My issue is that I have several distorted vertical lines going accross my screen.
 
I have spent hours upon hours viewing forums relating to this exact same issue.
 
they all seem to have solutions, but being the moron that I am, these solutions mean nothing to me.
 
As it stands, I know how to "install" Ubuntu...
 
thats about as far as my knowlege goes.
 
Can someone please help.
 
Thanks

---

### Post by coffeeaddict22 on 2009-05-01
Dunno.  If you can keep a windows PC going for more than a few months without reinstalling you may be smarter than us all...

Not sure what you've done or not, so I'd start basic.  Can you get a picture without the lines ever?  During booting up?  What happens if you attach a second monitor?  PC or laptop?  Primary monitor, or a fancy setup?

Open a terminal (Applications/Accessories/Terminal), type in ```
lspci -v |grep VGA -A10
```
That should give you some more detailed info about your display.

---

### Post by y_garti on 2009-05-01
like everything good in life if you want to Succeed you need to study there are plenty of ways to learn Linux

there is a good book for beginners here [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
and if you don't mind pay there is a good video tutorials from cbt nuggets or test out

believe me when i start with ubuntu i didn't know nothing (Maybe ls and rm but thats about it) after i start to learn i solve quite a lot of problem for my self and my friend computer 
its a good way to ask on the ubuntu forums question but if you want to truly be capable of moving from windows to Linux you need to learn how this amazing OS works (and of course if you have problem feel free to ask on the forums)

---

### Post by 3rdalbum on 2009-05-01
Any chance you can fit a real graphics card into that PC? Preferably something Nvidia. The truth is, SiS graphics chips are not renouned for anything and they typically don't have very good Linux support.

---

### Post by cbanakis on 2009-05-01
> **coffeeaddict22 said:**
> Dunno.  If you can keep a windows PC going for more than a few months without reinstalling you may be smarter than us all...

Not sure what you've done or not, so I'd start basic.  Can you get a picture without the lines ever?  During booting up?  What happens if you attach a second monitor?  PC or laptop?  Primary monitor, or a fancy setup?

Open a terminal (Applications/Accessories/Terminal), type in ```
lspci -v |grep VGA -A10
```That should give you some more detailed info about your display.

I cannot get a picture ever without the lines except at the loading screen.
It seems to be fine during boot up, it only has the lines after, like right now I can barely read what I'm typing. 

I have tried different monitors and same problem.

This is what I got from terminal.

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 04)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3079
    Flags: 66MHz, medium devsel, IRQ 10
    BIST result: 00
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    Memory at fdce0000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at df00 [size=128]
    Capabilities: <access denied>
    Kernel modules: sisfb

---

### Post by cbanakis on 2009-05-01
> **y_garti said:**
> like everything good in life if you want to Succeed you need to study there are plenty of ways to learn Linux
 
there is a good book for beginners here [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
and if you don't mind pay there is a good video tutorials from cbt nuggets or test out
 
believe me when i start with ubuntu i didn't know nothing (Maybe ls and rm but thats about it) after i start to learn i solve quite a lot of problem for my self and my friend computer 
its a good way to ask on the ubuntu forums question but if you want to truly be capable of moving from windows to Linux you need to learn how this amazing OS works (and of course if you have problem feel free to ask on the forums)
 
Well I am cetainly willing, Its just been a very long time since I have been this frustrated with computer problems.

---

### Post by cbanakis on 2009-05-01
> **3rdalbum said:**
> Any chance you can fit a real graphics card into that PC? Preferably something Nvidia. The truth is, SiS graphics chips are not renouned for anything and they typically don't have very good Linux support.
 
Unfortunately, since I'm trying to set this up as a file server, the 1 PCI slot I have is needed for a gigabit network card, and the 1 PCI Express slot I have is needed for a ESATA RAID controller.
 
Not sure how I'll get the RAID controller working, havent tried yet, but I'll cross that bridge when I come to it.

---

### Post by cbanakis on 2009-05-01
I just made my situation worse.
I was trying to use one of the solutions I found on forums, then rebooted, and now I have no display at all.
 
I'm reinstalling Ubuntu right now. I'm sure there is a much better way, but for now I'm going to stick to what I know, And I know how to install Ubuntu. LOL
 
I try to push everyone I know into trying Ubuntu.
 
But right now, if they do try it, and something doesnt work, I frown and send them back to Mr Gates.
 
In my limited experience, if you install Ubuntu, and know nothing about it, but all your hardware happens to work, your better off with Ubuntu.
 
And I am definitely sick and tired of windows.
 
Of course OS X is the biggest load of crap ever.
 
Mac suport is the only place I can imagine that will tell you to not do something if it causes a problem.
 
"Everytime I save to this folder, my computer crashes"  -  "Why don't you save it somewhere else?"
 
I can only imagine if Apple made cars...
 
"Everytime I turn left, my F'n wheel falls off"  -  "Why dont you just make 3 rights?"

---

### Post by overdrank on 2009-05-01
> **cbanakis said:**
> I just made my situation worse.
I was trying to use one of the solutions I found on forums, then rebooted, and now I have no display at all.
 
I'm reinstalling Ubuntu right now. I'm sure there is a much better way, but for now I'm going to stick to what I know, And I know how to install Ubuntu. LOL
 
"

Hi and no need to reinstall, just boot into recovery mode and choose xfix to correct graphical issues. :)

---

### Post by cbanakis on 2009-05-01
> **overdrank said:**
> Hi and no need to reinstall, just boot into recovery mode and choose xfix to correct graphical issues. :)
 
Yeah, I assumed as much.
But look at it from my angle, I reinstalled in less time that it took to get a response, But now I know how it fix it next time.
 
thanks for the post.

---

### Post by mgmiller on 2009-05-01
> Not sure how I'll get the RAID controller working, havent tried yet, but I'll cross that bridge when I come to it.

The RAID controller is very easy if you buy the right one.  I am using a 3ware 9650SE.  It is totally supported by Linux.  No drivers, no nothing, plug and play, it just works.

Generally 3ware controllers have excellent support, mine is just a simple RAID1 with 2 SATA II hdds.  It is also true hardware raid, not "fake raid" or software raid that many cheaper cards do.  If you're not familiar with this topic try reading more here:  [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

As far as your video problem is concerned, are you using a flat panel monitor or a CRT?  Are you sure your refresh rate is correct?

SIS video definitly sucks goats, you'll probably never get compiz desktop effects working with one, but I have 4 SIS machines in my office and they work ok with normal graphics stuff.  

For future builds, definitly consider nvidia based graphics either onboard or discreet.

---

### Post by cbanakis on 2009-05-01
> **mgmiller said:**
> The RAID controller is very easy if you buy the right one.  I am using a 3ware 9650SE.  It is totally supported by Linux.  No drivers, no nothing, plug and play, it just works.

Generally 3ware controllers have excellent support, mine is just a simple RAID1 with 2 SATA II hdds.  It is also true hardware raid, not "fake raid" or software raid that many cheaper cards do.  If you're not familiar with this topic try reading more here:  [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

As far as your video problem is concerned, are you using a flat panel monitor or a CRT?  Are you sure your refresh rate is correct?

SIS video definitly sucks goats, you'll probably never get compiz desktop effects working with one, but I have 4 SIS machines in my office and they work ok with normal graphics stuff.  

For future builds, definitly consider nvidia based graphics either onboard or discreet.

-----Video-----

I am using a flat panel wide screen (HP w19)

I am using HPs recommended refresh rates, and resolutions.

The problem seems to be reduced when I use extremely low resolutions, but it does not go away no matter how low I go.  Also, once it gets so low, windows open way too large for the display.  (cant click on ok/cancel/save/ect because its off the screen

I know the video card sucks, but I'm not concerned about that because my goal is to basically use this setup as a NAS device.  But I still need to be able to see what I'm doing on it from time to time.

-----RAID-----

well, the problem is that I really only have 1 choice for a RAID controller.
High Point - Rocket RAID 2314
I already have it for one, but more importantly, it has 4 ESATA ports, and has a port multiplier that allows for 5 drives per port, totaling 20 drives.  I already have 4 5-drive enclosures, and 20 1.5TB seagates. (currently all setup in Vista)
And I want to switch it over to Ubuntu.

---

### Post by mgmiller on 2009-05-01
Here's what I can find about rocket raid.

([link]("http://linuxmafia.com/faq/Hardware/sata.html#highpoint2240")) **HighPoint RocketRAID 2240 (16-port SATA-II PCI-X), 2220 (8-port SATA-II PCI-X), 2320 (8-port SATA-II PCI Express), 2224 (4-port SATA-II PCI-X) cards** — fakeraid.  Proprietary binary drivers ([2240]("http://www.highpoint-tech.com/USA/bios_rr2240.htm"), [2220]("http://www.highpoint-tech.com/USA/bios_rr2220.htm"), [2320]("http://www.highpoint-tech.com/USA/bios_rr2320.htm"), [2224]("http://www.highpoint-tech.com/USA/bios_rr2224.htm")) can be downloaded from the manufacturer. Correspondent Berkley Shands notes that these cards and proprietary drivers are quite CPU-intensive, even pushing a quad-Opteron system a bit. He also recommended tweaking hpt_reset routine to fix IRQ spinlocks, on 2.6.14/2.6.15 kernels. He achieved a maximum initial read speed of 870MB/sec. on RAID0, using 50% of CPU power. Note that models 2220 and 2240 both try to use (different) proprietary drivers named "hptmv6". Use command-line rather than GUI RAID setup utility, if there will be more than 8 drives per array. Shands adds: "Just FYI, to get those nice performance numbers, you *must* set the read-ahead value for the drive *and* use the POSIX_WILL_NEED function of fadvise(). The default read-ahead is 8 sectors. I use 1024; otherwise, you won't come anywhere near those numbers."

It seems all of the rocket raids I could see were all fake raid.  If you are using a pci-e card, you can stick anything in.  To use a fakeraid card, you would use the dmraid package, but I have no experience using it.  I have alway tried to use a true hardware raid whenever possible, as there is much lower system overhead and everything runs smoother / faster.

As far as your display problem, have you tried changing your color depth from 24 to 16?

---

### Post by cbanakis on 2009-05-01
> **mgmiller said:**
> Here's what I can find about rocket raid.

([link]("http://linuxmafia.com/faq/Hardware/sata.html#highpoint2240")) **HighPoint RocketRAID 2240 (16-port SATA-II PCI-X), 2220 (8-port SATA-II PCI-X), 2320 (8-port SATA-II PCI Express), 2224 (4-port SATA-II PCI-X) cards** — fakeraid.  Proprietary binary drivers ([2240]("http://www.highpoint-tech.com/USA/bios_rr2240.htm"), [2220]("http://www.highpoint-tech.com/USA/bios_rr2220.htm"), [2320]("http://www.highpoint-tech.com/USA/bios_rr2320.htm"), [2224]("http://www.highpoint-tech.com/USA/bios_rr2224.htm")) can be downloaded from the manufacturer. Correspondent Berkley Shands notes that these cards and proprietary drivers are quite CPU-intensive, even pushing a quad-Opteron system a bit. He also recommended tweaking hpt_reset routine to fix IRQ spinlocks, on 2.6.14/2.6.15 kernels. He achieved a maximum initial read speed of 870MB/sec. on RAID0, using 50% of CPU power. Note that models 2220 and 2240 both try to use (different) proprietary drivers named "hptmv6". Use command-line rather than GUI RAID setup utility, if there will be more than 8 drives per array. Shands adds: "Just FYI, to get those nice performance numbers, you *must* set the read-ahead value for the drive *and* use the POSIX_WILL_NEED function of fadvise(). The default read-ahead is 8 sectors. I use 1024; otherwise, you won't come anywhere near those numbers."

It seems all of the rocket raids I could see were all fake raid.  If you are using a pci-e card, you can stick anything in.  To use a fakeraid card, you would use the dmraid package, but I have no experience using it.  I have alway tried to use a true hardware raid whenever possible, as there is much lower system overhead and everything runs smoother / faster.

As far as your display problem, have you tried changing your color depth from 24 to 16?

Wow, thank you very much for the info.  I was under the impression that the Rocket Raid 2314 was hardware RAID, but even if its not, it does not change the facts.  Its my only option, plus I have been using it in Vista for a long time, and I'm happy with the performance.

And if I'm happy with the performance in an OS as bloated as Vista, I'm sure it will work just fine in Ubuntu, provided I can get it to work.

I have not tried changing from 24bit to 16bit.

Where can I find that option?  

I dont remember seeing under the screen resolution options.

Again, Thank you very much

---

### Post by mgmiller on 2009-05-02
> I have not tried changing from 24bit to 16bit.

Where can I find that option?  With an Nvidia card, it can be changed from the gui, but with an SIS, I think you will have to manually edit xorg.conf.

Open a terminal:
Applications > Accessories > Terminal

First, lets make a backup copy of your xorg.conf, just to be safe.
Copy and paste the following command into the terminal:
```
sudo cp /etc/X11/xorg.conf xorg.backup
```Give it your regular log in password when prompted, you will not see anything echo to the screen when you do this, just hit enter when done.

Next, make the changes.
Copy and paste the following command:
```
gksu gedit /etc/X11/xorg.conf
```Scroll down to where you see:
```
Section "Screen"    
Identifier    "Default Screen"    
Monitor        "Configured Monitor"    
Device        "Configured Video Device"
EndSection
```Add the following line so it looks like this:
```
Section "Screen"    
Identifier    "Default Screen"    
Monitor        "Configured Monitor"    
Device        "Configured Video Device"
DefaultDepth       16
EndSection
```
Click the "Save" button at the top of the window and close the editor.
You will need to log off and back on to see the changes.  If is still looks wrong, try rebooting.

If something goes horribly wrong and you end up at a command prompt, use the following code to restore the original:
```
sudo cp /etc/X11/xorg.backup xorg.conf
```Then reboot.

Good luck.

---

### Post by mgmiller on 2009-05-02
> Wow, thank you very much for the info. I was under the impression that the Rocket Raid 2314 was hardware RAID, but even if its not, it does not change the facts. Its my only option, plus I have been using it in Vista for a long time, and I'm happy with the performance.

I was browsing the manufacturers web site for your specific RAID card and their description does not specifically say it's hardware RAID, and I have found other sources that say the Marvell controller used by your card is fakeraid as well.  The 3000 series Rocket raid cards are true hardware raid, but the 2000 series are not.
On a lighter note, they have Linux support for it and provide a driver.  It's on this page:
[http://www.highpoint-tech.com/USA/bios_rr2314.htm](http://www.highpoint-tech.com/USA/bios_rr2314.htm)

It will require you to compile and install a patch for your kernel.  This means you will have to install the linux headers before you are able to do anything else.  You can search in Synaptic to make sure the linux-headers-generic package and it's associated other linux-headers packages are installed.

There is a readme included with the driver that tells you how to install the driver after you have installed the headers for your kernel.  It may be necessary to recompile the kernel every time there is a kernel upgrade.

At some point in the future, this driver may become built into the kernel and then it becomes "plug and play", but until then, you need to do a little extra work.

Your motherboard must have PCIe x4, x8 or x16 slot for this card to work properly.  It won't fit a x1 slot unless it's a universal slot and it then functions at greatly reduced speed.


Good Luck.

---

### Post by mgmiller on 2009-05-02
One final thought about the RAID.  You may find that simply using the dmraid package is all you need to do to get your RAID going.  If that's the case, then you won't need their driver and there is no kernel compiling to do.  I have no experience using dmraid, but you can search these forums for explicit instructions on setting it up and using it.

---

### Post by ocelot6 on 2009-05-02
Just as a point of reference, changing the color depth to 16 worked for me, after hours of unsuccessfully trying the vesa driver and messing around with the drivers from [http://ncc-1701a.homelinux.net/~linux-sis/](http://ncc-1701a.homelinux.net/~linux-sis/), which I'd been using with success in Intrepid prior to upgrading. 

Thanks!

(Ditching this horrid card ASAP!)

---

### Post by cbanakis on 2009-05-02
Changing to 16bit did not completely fix the problem, but it did drastically reduce it to the point where I almost cant tell its messed up.
 
Since I'm just using this sytem as a file server anyway, this will do just fine.
 
Thank you all very much for your patience.
 
And it looks like I will definitely need help getting my RAID controller working soon.
 
After that, I can easily buy specific hardware from now on to avoid these issues, but like I said, this setup is what it is, and there is no practical way for me to change it.

---

