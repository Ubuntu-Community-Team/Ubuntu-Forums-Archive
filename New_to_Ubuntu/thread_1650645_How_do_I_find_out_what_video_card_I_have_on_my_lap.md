---
title: "How do I find out what video card I have on my laptop?"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2010-12-22
Also, how do I find out the video card's amount of RAM?

---

### Post by bodhi.zazen on 2010-12-22
```
lspci -v -s `lspci | grep VGA | awk '{print $1}'`
```

If you wish you can grep the output of that a bit

```
lspci -v -s `lspci | grep VGA | awk '{print $1}'` | grep --color=always size
```
:twisted:

For a bit of information in english see:

[http://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/](http://www.cyberciti.biz/faq/howto-find-linux-vga-video-card-ram/)

There used to be a menu option to show this information, was under

System -> Preferences -> Hardware

[http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/](http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/)

but I do not see that option any longer in the menu.

---

### Post by brawnypandora0 on 2010-12-22
Why was this menu removed? I don't like using and memorization all the terminal commands.

---

### Post by karthick87 on 2010-12-22
```
sudo lshw -C display
```

---

### Post by brawnypandora0 on 2010-12-22
After I put in the commands, I get this:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
    Subsystem: Acer Incorporated [ALI] Device 0083
    Flags: 66MHz, medium devsel, IRQ 7
    BIST result: 00
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at e2100000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at a000 [size=128]
    Capabilities: <access denied>
    Kernel modules: sisfb

george@george-laptop ~ $ lspci -v -s `lspci | grep VGA | awk '{print $1}'` | grep --color=always size
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at e2100000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at a000 [size=128]

I don't understand what any of that means. Does it mean I have a 128 MB video card?

---

### Post by bodhi.zazen on 2010-12-22
> **karthick87 said:**
> ```
sudo lshw -C display
```

That shows the card, but not the details ....

> **brawnypandora0 said:**
> After I put in the commands, I get this:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
    Subsystem: Acer Incorporated [ALI] Device 0083
    Flags: 66MHz, medium devsel, IRQ 7
    BIST result: 00
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at e2100000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at a000 [size=128]
    Capabilities: <access denied>
    Kernel modules: sisfb

george@george-laptop ~ $ lspci -v -s `lspci | grep VGA | awk '{print $1}'` | grep --color=always size
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at e2100000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at a000 [size=128]

I don't understand what any of that means. Does it mean I have a 128 MB video card?

yes you have 128 mb ram.

Rather then memorizing command most people use google to search for this information.

What problem ae you having ?

---

### Post by brawnypandora0 on 2010-12-22
I'm just really puzzled. My laptop has Ubuntu and 512 MB DDR RAM with a 128 MB video card and watching 360p youtube videos is fine. My desktop has Windows XP and 1 GB DDR RAM with a 128 MB video card, yet watching 360p videos is VERY choppy and sometimes makes my computer freeze. Does this mean my desktop video card, despite having the same video card memory, is too old and faulty?

Would installing Ubuntu on my desktop make watching 360p youtube videos possible?

---

### Post by karthick87 on 2010-12-22
If you are confused with the command line result,you can install sysinfo..It has a GUI
```
sudo aptitude install sysinfo
```  
[IMG]http://imgur.com/nxnlh.pnghttp://imgur.com/nxnlh.png[/IMG]

---

### Post by mastablasta on 2010-12-22
> **brawnypandora0 said:**
>  
Would installing Ubuntu on my desktop make watching 360p youtube videos possible?
 
 
it's not all about memmory. it also depends what chip is on the card as well as how good drivers are there. it can also depend on CPU if the card is not a dedicated one.
 
To answer your question the easiest way is to run ubuntu live session on your desktop and see how it performs with your tube videos. 
 
on the side note for winXP check if:
 
- your directX is up to date
- flash is up to date
- card drivers are up to date

---

### Post by qyot27 on 2010-12-22
The performance problems on Windows may also be due to other things (like anti-virus software, most obviously, or actual malware issues) taking up resources and preventing the playback from going well.  Making sure everything - Flash, video drivers, browser, etc. - is up-to-date helps too.  Since Ubuntu doesn't have those overhead or malware problems, and updates are handled far better, it seems more transparent than it does on Windows.

(One test on Windows would be to download the actual base file and see if it still has issues when played by Media Player Classic or SMPlayer - if the issues disappear, then you know it's more than likely because Flash just sucks in general, and things are interfering with it.)

Also, video card memory is not directly comparable to system memory, and memory types between cards can (and does) differ just like the GPU on the cards themselves can.  So it's not an accurate view without knowing all the minute differences in spec.

On Windows you can use Speccy to find out this info. CPU-Z and GPU-Z also work, but those are separate apps.  Speccy is also made by Piriform, and I would strongly suggest using two of their other programs - CCleaner and Defraggler - to keep the OS clean and running smoothly.

---

