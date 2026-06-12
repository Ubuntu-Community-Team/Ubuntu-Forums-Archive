---
title: "Ubuntu 9.10 vs. Windows 7 - A few questions."
date: 2009-10-25
forum: New to Ubuntu
---

### Post by papuccino1 on 2009-10-25
Hi there, as you can see I've been a member here for quite some time and I've always looked at the new Ubuntu releases just ACHING for it to reach a point where I can leave Windows for my general uses.

Three years now, and so far I haven't been pulled away for long.

When I was a Windows XP user, I loved using it. It was fresh, fast, and new. Then someone introduced me to Ubuntu and I was dropped to the floor. Automatic drivers, software manager/downloader, FREE?!?!?! What was this witchcraft?!

I used it but noticed that some things didn't quite work out of the box as I thought it did on my laptop.

Fast forward and I downloaded Windows 7.

It was a new beginning. ABSOLUTELY EVERYTHING I THREW AT THIS BEAST was recognized and installed on the fly. It was so suprising for me. Not even Linux (which I thought was one of it's strong pillars) could match this ease of use.

Even my printer (and let's face it, printers are always a bitch) installed itself with just me pushing in the USB cable.


So, I guess my question is this.

With this new version of Ubuntu coming out in 4 days, has it gotten to the point of turn on the machine with a cable connected to the internet and everything you need (driver-wise) will be installed on the fly?

I need my wifi button on my laptop to work. My Hibernate things to work. My videocard to work. Generally be peachy.

I'm **really** crossing my fingers it has gotten much better since version 8.04.

---

### Post by halitech on 2009-10-25
meh, I tried the windows 7 rc in a VM and on a P4 I had kicking around and I wasn't overly impressed with it at all. Sure it has some nice eye candy if you are into that type of thing but it didn't work with either of my printers (Epson Stylus C60 and a Samsung ML-2510), seemed alot slower then my linux installs, still needed to install antivirus software, video card drivers, NIC drivers and the sound never did work on the P4.

As far as the new 9.10, who knows if it will be any better or worse with your hardware. Wireless is still cranky and may need binary blobs to get working, video cards will probably still need closed source drivers and hibernate, who knows.

What video card and laptop do you have?

---

### Post by papuccino1 on 2009-10-25
> **halitech said:**
> meh, I tried the windows 7 rc in a VM and on a P4 I had kicking around and I wasn't overly impressed with it at all. Sure it has some nice eye candy if you are into that type of thing but it didn't work with either of my printers (Epson Stylus C60 and a Samsung ML-2510), seemed alot slower then my linux installs, still needed to install antivirus software, video card drivers, NIC drivers and the sound never did work on the P4.

As far as the new 9.10, who knows if it will be any better or worse with your hardware. Wireless is still cranky and may need binary blobs to get working, video cards will probably still need closed source drivers and hibernate, who knows.

What video card and laptop do you have?

Thanks for the response. :D Just want to make it **very clear** that it's not my intention to start a flame war of any kind. I'm truly rooting for Ubuntu to work because I want to use it permenantly, but I don't have time to set everything up.

My laptop is a Compaq Presario CQ-50 215NR. It came with Windows Vista, but I formatted my machine from scratch and put Windows 7 on it. It's ridiculously fast and the driver support is my favorite part about it.

Is there some sort of list I can see if my computer is on a 100% functional terms with Ubuntu?

---

### Post by Cybie257 on 2009-10-25
I could start out by saying that with 9.04 you'd probably would've seen quite a change for your "laptop" from 8.04. Linux and Laptops in the beginning were very difficult and nothing to be desired. But, since 9.04, Ubuntu has made laptop installs a piece of cake. 

As for things just working out of the box. Well, you have to realize that you can always set your printer to a generic print mode, but to take advantage of other modes, you need manufacturer-specific drivers. And things like WIFI, that has improved a lot and some cards do require that you go into the hardware drivers menu and activate a proprietary driver. not a big deal, but unles you know it exists, you might fight that issue trying to get some hardware item to work. It boils down to a simple click of a button to get them working, including proprietary drivers for video cards, such as nVidia and ATI. 

When you speak of windows having things just work out of the box, you should also recognise that windows MUST be installed from a DVD, takes forever to install, and uses up a lot of hard drive space for a fresh install. This is because it installs all the available and viable drivers during install, not to mention just a sloppy OS to begin with, so that why more things tend to work with Windows. The price you pay for having everything work out of the box is reduced system performance. in other words, if you want a high performing computer, you have to do away with all the clutter. That's what Linux is all about. you ONLY install what you need, not what you don't, leaving you with a less cluttered, better performing machine. 

The other side of things about drivers for Linux relates to the lame asses (assuming your in the US as I am) that are afraid of change. Here in the US, finding drivers for things like printers are a nightmare for the most part because of the so-called lack of demand. But, when you go to the same manufacturers website from another country, wholla, there's the drivers for your printer. (IE:I have a Canon MX860 MFC. On the American Canon website, you won't find Linux drivers for them. But go to the European website and there they are, in full English language. not my printer is fully functional in Linux as it was with Windows, and it was easy to install.)

My suggestion is to 'try' the latest release and see what sort of new functionality you get. Linux is ever growing and changing day to day, which allows it to have the ability to stay with the times better than Windows. For example, USB 3.0 will first be available via Linux (unless things have changed recently). Having the ability to use a LiveCD version to test out your machine is a big advantage. But, if you are wanting to try that, then I'd wait until the end of this month when the final release of Ubuntu is released as RC versions may have some things that aren't functional until the final release. 

Hope this was able to answer your post to some degree. 

-Cybie

---

### Post by halitech on 2009-10-25
Wasn't taking it as a start to a flame war at all :) 

according to what is online ( [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01555875&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=3795238&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01555875&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=3795238&lang=en) ) you have a pretty nice system, I'm jealous 8-[

It looks like you have an Nvidia video card, it should work well, probably with the 185 drivers.

To check all your system, you can install hardinfo for a gui list or run
```
lshw
``` to get it in a list you can post here.
For a quick list on the wireless card, run```
lspci
```

---

### Post by Shpongle on 2009-10-25
i had both on my laptop and i  exclusively use karmic , its just that good and it doesnt lag iv turned on all the graphics to test it and it runs fine as looks great i also always have a good few apps running too and with all that my ram is never over 400mbs most of the time now i have two gigs and considering windows takes nearly a gig to just run id say thats damn impressive on ubuntus part also ubuntu shuts down nearly instantly and it works with all my stuff outta the box , i have a printer i got with a win xp machiene and vista  doesnt work with it but ubuntu does!! and my phone ipod external hd etc. . .

---

### Post by jmore9 on 2009-10-25
I used windows 7 for about 6 months and did not really see that much of an improvement over winxp pro sp2.  I compared it to winxp pro ( running on seperate machine and ubuntu 9.04 )  . I had to force feed the lan drivers and the sound blaster Ensoniq drivers.

I currently use ubuntu 9.04 for my internet machine and winxp pro for the other machine only because i use an ATI tv wonder 650 pro pci tv tuner card.
It has no support in linux as yet.

If i was going to get rid of the xp os i would spend the 75 to 100 dollars and buy a digital wintv or kworld brand , instead of 600 or 700 dollars per machine for windows 7.

And 9.04 has been here on this machine for about 5 months and no problems at all.

That is my experience with windows compared with ubuntu

---

### Post by servicetech on 2009-10-25
I'm runnign 7 on my HTPC, love the media center.
For desktop use Ubuntu is great for the most part. 

If they got the sleep function fixed on my M3N78-EM, I'm happy.

---

