---
title: "Building a new computer, have had it with microsoft"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by dicemoon on 2009-09-04
Hi all, I'm a complete linux noob... I've purchased parts for a new computer and I'm hoping you guys can tell me if I can configure linux to run on this system with a beginner's mindset... I've been working on computers for about 10 years now and have wanted to get into linux but just haven't had the gumption. 
I'll list all hardware, not that some of it is relevant but it gives you an idea of the system. I also play WoW and I think I will probably have to run vmware for this, any thoughts?

Anyway, on to the hardware:
Case- Thermaltake VF6000BNS  [http://www.newegg.com/Product/Product.aspx?Item=N82E16811133045](http://www.newegg.com/Product/Product.aspx?Item=N82E16811133045)

Power Supply- Mushkin 550 [http://www.newegg.com/Product/Product.aspx?Item=N82E16817812002&Tpk=mushkin%20550](http://www.newegg.com/Product/Product.aspx?Item=N82E16817812002&Tpk=mushkin%20550)

Motherboard- (I bought this board to unlock dormant cores on the processor) Biostar TA785GE 128m [http://www.newegg.com/Product/Product.aspx?Item=N82E16813138155](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138155)

Processor- AMD Phenom ii x2 550 Black Edition [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103680&Tpk=amd%20phenom%20ii%20x2%20550%20black%20edition](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103680&Tpk=amd%20phenom%20ii%20x2%20550%20black%20edition)

RAM- OCZ Platinum 4gb ddr2 1066 [http://www.newegg.com/Product/Product.aspx?Item=N82E16820227298](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227298)

Vid- (I would REALLY like to use the hdmi port on this vid card, which carries sound with it. Is this a pipe dream or is this a feasible option?) Sapphire 4670 1g ddr3 [http://www.newegg.com/Product/Product.aspx?Item=N82E16814102842](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102842)

Wifi- (I've heard wifi drivers for linux can be... difficult, anyone know if this card will work) Linksys WMP54gs [http://www.newegg.com/Product/Product.aspx?Item=N82E16833124139](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124139)

Hard Drives- will be going dual sata Maxtor drives that I have laying around in a raid 0 setup, does linux support this well and natively?

Optical- Plextor 24x sata dvd burner [http://www.newegg.com/Product/Product.aspx?Item=N82E16827249054](http://www.newegg.com/Product/Product.aspx?Item=N82E16827249054)

I apolgise for the length of my post and my complete linux ignorance, I'm hoping the hardware I have chosen will do what I want it to do under linux. any help is very, very much appreciated.

---

### Post by SuperSonic4 on 2009-09-04
I've not heard of sapphire GPU cards, I would get an nvidia card for they do good drivers which work. NO idea on the wireless card, my atheros works though.

everything else should be ok though, I run 4 sata drives in my pc and there is no issue. 

On a side note be sure to download a 64bit OS to take advantage of all that RAM :p

---

### Post by Jazzy_Jeff on 2009-09-04
I would also recommend using nVidia video cards as well. They are better supported. 

As for WoW, I run that under wine and it runs great. Easy to set up.

---

### Post by hockeytux on 2009-09-04
Lucky you like WoW and not anything else as thats one of the games which work fantastically well in Wine (a Windows emulator).

As for installation, download the .iso burn that to a dvd and youre all set.  Welcome to Linux :KS

---

### Post by QIII on 2009-09-04
Don't know about the video.  Go with nVidia.  I've had good luck.  I've also had good luck with ATI, but others have had nightmares.

As for your wireless, take a look here:

[http://ubuntuforums.org/showthread.php?t=1233448](http://ubuntuforums.org/showthread.php?t=1233448)

Use WPA2 security on your router, unless you want to use WEP and have all of your neighbors hacking your router ten minutes after you start transmitting.

If your router does not support it, buy a new one.

---

### Post by NoaHall on 2009-09-04
Hardware you don't really need to worry - 
1) The PSU (Power Supply Unit)
2) Case
3) Your RAM - I have it on one of my machines :)
4) Wireless card - it should work okay. (Although routers can also cause a little problems)
5) Hard Drives
6) Optical
7) Processor - it'll run fine

Things you need to worry about - 

Video card (I would not use a Raedon if I were you, I would use nvidia, as stated above)

Motherboard - should work fine, as long as you don't enable the on board graphics card

Hoped I helped.

---

### Post by gordintoronto on 2009-09-04
Less than a month ago I built a fairly similar system.  I went with a much bigger case (Cooler Master Centurion 534), which is working out well.  It has fans at front and back, and everything is running nice and cool -- and it's quiet.

I went with a Gigabyte MA770T-UD3P motherboard and 1333 DDR3 memory.  

My Wifi is an older D-Link DWL-G510.  If you have any grief with the Linksys card, you might consider this one:
[http://www.newegg.com/Product/ProductReview.aspx?Item=33-127-080&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Page=1&Keywords=linux](http://www.newegg.com/Product/ProductReview.aspx?Item=33-127-080&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Page=1&Keywords=linux)

I have a cheap MSI video card based on the nVidia 9400 GT.  It also has HDMI out, which is supposed to include audio, but I have yet to try it.

Most people do not like "Raid 0," which provides no redundancy.

My system is working very nicely with 64-bit Linux Mint, which is a minor variant of Ubuntu.  If you have no Linux experience, Mint will get you up and running a bit quicker.  (It plays MP3s, DVDs and Facebook videos "out of the box" -- unlike Windows or Ubuntu.)  However, Mint comes with no games, and I like to use Freecell and MahJongg as a warmup to the day.

---

### Post by bkratz on 2009-09-04
> **dicemoon said:**
> Hi all, I'm a complete linux noob... I've purchased parts for a new computer and I'm hoping you guys can tell me if I can configure linux to run on this system with a beginner's mindset... I've been working on computers for about 10 years now and have wanted to get into linux but just haven't had the gumption. 
I'll list all hardware, not that some of it is relevant but it gives you an idea of the system. I also play WoW and I think I will probably have to run vmware for this, any thoughts?
[]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227298")

Wifi- (I've heard wifi drivers for linux can be... difficult, anyone know if this card will work) Linksys WMP54gs [http://www.newegg.com/Product/Product.aspx?Item=N82E16833124139](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124139)



I apolgise for the length of my post and my complete linux ignorance, I'm hoping the hardware I have chosen will do what I want it to do under linux. any help is very, very much appreciated.


Do you know which version 1 2 or 3 of the Linksys you have?  I think this is the one which has several versions and some are easier than others.

By the way--- Welcome

---

### Post by carcar1 on 2009-09-04
I really reccomend this wireless card. [http://www.newegg.com/Product/Product.aspx?Item=N82E16833180052]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833180052")

It gets native support and gets much much better wireless reception than any other os.  And if it doesn't work which is like a 1 in 10 chances due to motherboard issues just make a thread and I and many other happy users of this card can help you.  And 9.10 is coming out soon so look forward to ubuntu's plethora of new wireless drivers

---

### Post by mlentink on 2009-09-04
Might I add a personal note? 
If you've come to linux because, as you say, you have had it with Windows, please be prepared for disappointment. Many people with the same motive find out that Ubuntu, or Linux in general, is not, as they would want it, a Windows that works, but rather an entirely different operating system. Please realise that Linux is completely different from Windows, and that you will have to relearn a lot. Been there, done that almost six years ago.

I'm not trying to discourage you, rather the opposite. You will find that the readjustment blues bring many, many benefits that you will appreciate.

Welcome to the free world!

---

### Post by oboedad55 on 2009-09-04
> **dicemoon said:**
> Hi all, I'm a complete linux noob... I've purchased parts for a new computer and I'm hoping you guys can tell me if I can configure linux to run on this system with a beginner's mindset... I've been working on computers for about 10 years now and have wanted to get into linux but just haven't had the gumption. 
I'll list all hardware, not that some of it is relevant but it gives you an idea of the system. I also play WoW and I think I will probably have to run vmware for this, any thoughts?

Anyway, on to the hardware:
Case- Thermaltake VF6000BNS  [http://www.newegg.com/Product/Product.aspx?Item=N82E16811133045](http://www.newegg.com/Product/Product.aspx?Item=N82E16811133045)

Power Supply- Mushkin 550 [http://www.newegg.com/Product/Product.aspx?Item=N82E16817812002&Tpk=mushkin%20550](http://www.newegg.com/Product/Product.aspx?Item=N82E16817812002&Tpk=mushkin%20550)

Motherboard- (I bought this board to unlock dormant cores on the processor) Biostar TA785GE 128m [http://www.newegg.com/Product/Product.aspx?Item=N82E16813138155](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138155)

Processor- AMD Phenom ii x2 550 Black Edition [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103680&Tpk=amd%20phenom%20ii%20x2%20550%20black%20edition](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103680&Tpk=amd%20phenom%20ii%20x2%20550%20black%20edition)

RAM- OCZ Platinum 4gb ddr2 1066 [http://www.newegg.com/Product/Product.aspx?Item=N82E16820227298](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227298)

Vid- (I would REALLY like to use the hdmi port on this vid card, which carries sound with it. Is this a pipe dream or is this a feasible option?) Sapphire 4670 1g ddr3 [http://www.newegg.com/Product/Product.aspx?Item=N82E16814102842](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102842)

Wifi- (I've heard wifi drivers for linux can be... difficult, anyone know if this card will work) Linksys WMP54gs [http://www.newegg.com/Product/Product.aspx?Item=N82E16833124139](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124139)

Hard Drives- will be going dual sata Maxtor drives that I have laying around in a raid 0 setup, does linux support this well and natively?

Optical- Plextor 24x sata dvd burner [http://www.newegg.com/Product/Product.aspx?Item=N82E16827249054](http://www.newegg.com/Product/Product.aspx?Item=N82E16827249054)

I apolgise for the length of my post and my complete linux ignorance, I'm hoping the hardware I have chosen will do what I want it to do under 
Ditto to the other posxtslinux. any help is very, very much appreciated.

Ditto to the other posts regarding nvidia. I have had awful luck over the years with maxtor drives. WD and Seagate have been much better for my money.

---

### Post by pedro3005 on 2009-09-04
> **hockeytux said:**
> Lucky you like WoW and not anything else as thats one of the games which work fantastically well in Wine (a Windows emulator).
Actually, WINE stands for "Wine is not an emulator". So it's not an emulator. It's just a layer.

---

### Post by dicemoon on 2009-09-04
> **mlentink said:**
> Might I add a personal note? 
If you've come to linux because, as you say, you have had it with Windows, please be prepared for disappointment. Many people with the same motive find out that Ubuntu, or Linux in general, is not, as they would want it, a Windows that works, but rather an entirely different operating system. Please realise that Linux is completely different from Windows, and that you will have to relearn a lot. Been there, done that almost six years ago.

I'm not trying to discourage you, rather the opposite. You will find that the readjustment blues bring many, many benefits that you will appreciate.

Welcome to the free world!

Well I have indeed had it with windows, I'm no stranger to learning different operating systems, as I used to be a HUGE fan of beos (if anyone even remembers be). I have played with ubuntu before and liked it, I haven't gone to it yet successfully as the HP laptop I have currently will not work under ubuntu for love or money (yes, I even bribed it) I'm not overly attached to microsoft only reason I will want wine is for WoW. Thanks for the advice on the linksys wifi's I think I'm gonna go Dlink, as for the vid it's already purchased and the wife had a big enough fit with me ordering new hardware, I'm not even gonna bring up yet MORE hardware to her at this point, I'm really hoping I can configure the hdmi port successfully to use on our 46" lcd tv if I can I'll truly be thrilled.
As for the poster that mentioned having problems with Maxtors. I used to be a huge fan of WD drives but after having not one but seven go bad within 6 months (all 320 gigs) and I have yet to have a problem with a maxtor drive... I'll keep my maxtor's lol

---

### Post by eriktheblu on 2009-09-04
Yet another vote for Nvidia. I play WoW as well, the ATI card I had worked perfectly in Windows, and hardly at all in Ubuntu. Switching to Nvidia improved performance greatly (The only thing you'll miss out on is shadow quality which is not supported in OpenGL mode)

Do yourself a favor: Copy your entire WoW folder to an external drive (EULA allowed a backup copy last time I read it) before you rid yourself of Windows. This will save you a lot of time and heartache.

---

### Post by donkyhotay on 2009-09-04
I had a radeon X750 card for a number of years and it worked pretty well with ubuntu for me. That said I eventually bought a new computer and ended up with an nvidia card the second time around. Having used both I will admit installation/configuration of the nvidia card is much easier then the ATI card ever was. The nvidia pretty much 'just works' while the ATI drivers involved using an installation program designed for 1024x768 resolution while the computer was only capable of showing 800x600 due to the ATI drivers not being installed...

---

### Post by misterfixit on 2009-09-04
[QUOTE=dicemoon;7898305] ....  I'm no stranger to learning different operating systems, as I used to be a HUGE fan of beos (if anyone even remembers be)....

If you worked with BeOS you will have few if any problems other than ones which can be sorted out here on this forum.  

Heed the advice given above reference the nvidia and radeon cards.

RAID 0 is OK, and I use it, but I also have two separate 200GB drives which I rsynch to on an hourly basis for complete redundantcy.  You won't have a problem with RAID since you will see the RAID driver suite in your Synaptic list.  Just remember that you most likely have to mount the RAID Array, which I do automatically upin boot.  The RAID array will show up as two individual HD's and as "separate" drive with the same size as the RAID drives combined .. in my case, I have 2 x 1 TB drives and the RAID shows as a single 1 TB drive.  Don't worry about the fine print .. just set it up and then use "MountManager" (avialable via Synaptic and which will show up in your System ---> Administration drop-down menu.  As for MountMnager, it works great, but remember to save your settings every time you do anything.  It will forget your settings is you don't.

Your hardware lloks great to me with exception as mentioned above on the video cards.  I use an nvidia GEFORCE card and have a 23" Dell monitor in full native mode.  Man, the pron .. errrrr I mean .. the movies ... look great.
HTH, YMMV

Dave

---

