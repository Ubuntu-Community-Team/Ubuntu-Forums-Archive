---
title: "ATI raedon card  800x600 only"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by Septuagenarian on 2010-11-29
My ATI raedon 9250 card seems to only work in 800x600 format. When I click on ATI Catalyst to change the screen size I'm told the driver isn't installed. I've looked in restricted drivers and not sure about fglrx which may need updating but not sure how to do this. I have read the suggestions in previous threads , but am hesitant in case I get no display at all. Problem with 800x600 is that some webpages put tick boxes in the bottom right hand corner which I can't see , even with the slider bar. If you can help , please keep it simple , thanks.

---

### Post by Ceyx on 2010-11-29
I use an ATI 9200 @ 1024*786 - I am sure we can figure it out.  Starting from the basics - is your monitor capable of anything higher than 800*600 ?

---

### Post by madjr on 2010-11-29
try the open drivers

what version of ubuntu are you using?

---

### Post by Mark Phelps on 2010-11-29
> I've looked in restricted drivers and not sure about fglrx which may need updating but not sure how to do this. 

There are no restricted drivers that will work with your card and current versions of Ubuntu.  The open-source drivers, the ones you already have installed, are the only drivers available.  If you download or force the installation of other drivers, you will only trash your display and have a LOT of work needed to clean up the resulting mess.

---

### Post by cavalier911 on 2010-11-30
Lubuntu Lucid 10.04 livecd on computer with Radeon 9550
and a 17" emachines/kds CRT monitor.
Boots with Radeon driver to 1024x768 with the option to go to 1360x768

/var/log/Xorg.0.log: [http://paste.ubuntu.com/538204/](http://paste.ubuntu.com/538204/)
Line 191-> ATI Radeon 9250 5960 (AGP)

Look at /var/log/Xorg.0.log for (EE),see what xrandr says,maybe a monitor configuration that will require an /etc/X11/xorg.conf

Post the link here to your /var/log/Xorg.0.log @ [http://paste.ubuntu.com](http://paste.ubuntu.com)
Give us the model,specs,etc. on your monitor.

```
ubuntu@ubuntu:~$ sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: RV350 AS [Radeon 9550]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm bus_master cap_list rom
       configuration: driver=radeon latency=32 mingnt=8
       resources: irq:19 memory:d0000000-d7ffffff(prefetchable) ioport:c000(size=256) memory:e5000000-e500ffff memory:e4000000-e401ffff(prefetchable)
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV350 AS [Radeon 9550] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=32 mingnt=8
       resources: memory:d8000000-dfffffff(prefetchable) memory:e5010000-e501ffff

```
```
ubuntu@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 310mm x 230mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)

```

---

### Post by mastablasta on 2010-11-30
> **Septuagenarian said:**
>  When I click on ATI Catalyst to change the screen size I'm told the driver isn't installed. I've looked in restricted drivers and not sure about fglrx which may need updating but not sure how to do this.
 
If you have Catalyst and latest Ubuntu versions (or higher than 8.10 i belive)... something is wrong as you shouldn't use proprietary drivers. Did you maybe upgrade your sytem? if so you should have removed the drivers before upgrade. somehow oyu will have to clean the system from ATI proprietary drivers and load the open source ones.

---

### Post by Septuagenarian on 2010-11-30
Many thanks for your suggestions gentlemen , as I suspected , and confirmed by some of you , changing the drivers is not within my capabilities . I am not using a "monitor" as such , I am using a TV which has a PC function and worked perfectly with Lucid, 1024x768 no problem , it's only since the upgrade to 10.10 I have had this lo-res screen. Think I will leave well alone, or risk getting no display at all. Thanks again.

---

