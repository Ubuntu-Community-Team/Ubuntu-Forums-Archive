---
title: "I wand to convert too linux but..."
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Thelazycomputertech on 2009-03-27
I want to convert to Linux but I have 4 pieces of software that I need to run MS office, Net objects fusion 11,WOW, and adobe acrobat. I have toyed with wine and what not. I don't want to purchase a copy of VM ware and I have already ran dual boot. I just want to convert and move on if its possible. The software I'm referring has to run and run well. I am more than happy to put in the work to make this happen and I am a tech so get as technical as you need. I just need those pieces of software to run and run reasonably well if you can help if would be greatly appreciate

Thanks 

The lazy Tech :)

---

### Post by thehouseofho on 2009-03-27
You don't need to buy VMWare.  VMWare Server and VMWare Player are free downloads.

---

### Post by James_Lochhead on 2009-03-27
Yea VMware free options are good.

Check the virtualization forum for info on the other VMs. I have tried VirtualBox and I do not think it is as good as VMware.

"Not as good" as in it freezes for a minute when the start menu pops up.

---

### Post by SunnyRabbiera on 2009-03-27
Virtualbox is out there too.
MS office and WOW can be run via wine, if you need help with it we can assist you.
Net objects fusion I am unsure of.

Adobe acrobat (at least the PDF reader) can be installed for linux natively, unless you need the PDF creator.
For creating PDF's scribus might come in handy.

---

### Post by Bucky Ball on 2009-03-27
Those things will not run without VM something (or wine, but that is no guarantee depending on the software).

---

### Post by Thelazycomputertech on 2009-03-27
Really? I thought you had to purchase it I got to check that out if thats the case I have got the rest figured out that would be awesome thanks I can finally dump a monkey off my back 

Thanks

---

### Post by Thelazycomputertech on 2009-03-27
Oh I know about compatibility issues its just if someone had a configuration or knew of one that work well with those packages, but if VM ware is free than that I know I can get most if not all to work this is awesome.....if this works out Ill have to check back in and let you all know thanks

The lazy Tech

---

### Post by James_Lochhead on 2009-03-27
> **Thelazycomputertech said:**
> Oh I know about compatibility issues its just if someone had a configuration or knew of one that work well with those packages, but if VM ware is free than that I know I can get most if not all to work this is awesome.....if this works out Ill have to check back in and let you all know thanks

The lazy Tech

VMware Server & VMware Player are free. They are little harder to install but there are easy instructions in the virtualization mega thread in the virtualization forum.

VMware Workstation is the paid one. It is easier to install and has more features (which are generally aimed at software developers).

---

### Post by starcannon on 2009-03-27
Virtual Box is my favorite VM for those occasional Windows XP tasks. I find Virtual Box to be easier and more intuitive than VMware; however, that is likely a subjective opinion, so your mileage may vary.
You can get it here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I have been able to run MS Office with Wine, I had to do a little fiddling about with something; but its been so long I no longer remember what it was. To be honest, I use Open Office about 99% of the time, Open Office has really improved to the point that I rarely require MS Office in order to get a task done; still MS Office is something that must remain in the "getting work done" toolkit. 

I used to play WoW a lot, and I successfully ran it with [Cedega]("http://www.cedega.com/"), and I had several friends that successfully ran it with Wine. I have no advice or anecdotes for Net Objects Fusion 11.

GL and have fun.

---

### Post by HermanAB on 2009-03-27
All of those programs will run on WINE and the best version of Wine is Crossover by Codeweavers: [http://www.codeweavers.com/](http://www.codeweavers.com/)

Installing CrossOver and then installing Windows programs is super easy.  It is well worth the money.

---

### Post by James_Lochhead on 2009-03-27
> **starcannon said:**
> Virtual Box is my favorite VM for those occasional Windows XP tasks. I find Virtual Box to be easier and more intuitive than VMware; however, that is likely a subjective opinion, so your mileage may vary.

Out of interest is your Ubuntu 64 bit or 32? And do you virtualize 64 or 32 bit XP?

I have had trouble using 64 bit Ubuntu with 64 bit XP.

---

### Post by decoherence on 2009-03-27
If you have trouble playing WoW in a virtual machine (perhaps 3D acceleration won't work) there are directions for getting it to run under Wine here

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

But the framerates won't be as good as in native Windows

---

### Post by thehouseofho on 2009-03-27
If you want to create your own VM, you'll need VMWare Server.  VMWare Player can play already existing VMs, but you can download clean XP images from a couple of sources.

VMWare has actually made the installation process for their free options much simpler.  Once you download the compressed file, just extract the files and run the Perl script.

---

### Post by SunnyRabbiera on 2009-03-27
> **HermanAB said:**
> All of those programs will run on WINE and the best version of Wine is Crossover by Codeweavers: [http://www.codeweavers.com/](http://www.codeweavers.com/)

Installing CrossOver and then installing Windows programs is super easy.  It is well worth the money.

Crossover is good but Wine can do a lot on its own,
I would not consider crossover best though as its always a few versions behind in its wine app database...
Granted crossovers money does go to wine development but wine seems to be catching up in the ease of use department.

---

### Post by chrisinspace on 2009-03-27
> **James_Lochhead said:**
> I have tried VirtualBox and I do not think it is as good as VMware.

"Not as good" as in it freezes for a minute when the start menu pops up.

I use VirtualBox to run XP on my laptop for school.  We work out of SharePoint a lot so I need a good, solid implementation of IE and MS Office (can't check Office files in and out of SP with OpenOffice).  VirtualBox works great for me and I've never had the problem described above.  My favorite feature is the seamless mode.  It's easy to install and easy to build VMs.  I messed around with VMWare briefly, but every time Ubuntu pushed out a kernel update, I had to go and re-run a script to get VMWare to work.  VMWare is obviously one of the best choices if you need to run virtual servers that interact with the network cleanly, but if you just want to run a virtual desktop on your machine, I highly recommend VirtualBox.

The one thing that would make me consider switching would be to try [_[COLOR="Blue"]this trick[/COLOR]_]("http://intuitivestrums.blogspot.com/2008/08/boot-into-physical-windows-partition.html").

---

### Post by starcannon on 2009-04-08
> **James_Lochhead said:**
> Out of interest is your Ubuntu 64 bit or 32? And do you virtualize 64 or 32 bit XP?

I have had trouble using 64 bit Ubuntu with 64 bit XP.

Just got back to this thread, sorry for a late reply James:

I am using 32bit for the time being; however, I will be doing a 64bit install for a client soon, and so will be doing a trial by fire. I will also be setting up a 64bit install on its own partition on my machine in order to learn its ins and outs. There is a 64bit version of Virtualbox here [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads). I do not currently own any 64bit versions of Windows, so the windows install will be Windows XP Pro SP3 32bit.

---

