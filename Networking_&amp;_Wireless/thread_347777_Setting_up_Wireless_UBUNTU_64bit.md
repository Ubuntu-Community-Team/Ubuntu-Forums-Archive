---
title: "Setting up Wireless UBUNTU 64bit"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by kingleer on 2007-01-27
Okay, I'm trying to set up my wireless card on Ubuntu 64 bit 6.10. The Wireless card I have in my pc is DWL-G520. I have ALREADY installed ndiswrapper. I am positive that ndiswrapper is working perfectly. This isn't something that's new to me by the way. I already got the wireless on my laptop working perfectly. 

I go to download the wireless driver for my card here: 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Question 1: Does using 64 bit ubuntu change things (ie do I have to get a 64 windows driver?)

I think my problem is that I may not be using the right windows driver. I have a 64 bit driver for windows for my wireless card that I can try - but its not listed in the ndiswrapper card list. 

Anyway, I download the first dwl-g520 driver I find and try installing it. I install it correctly. 

I check to see that its installed 

sudo ndiswrapper  -l gives me 

neta3ab: driver installed 
            device (168c:0013) present 

I then load ndiswrapper 

sudo modprobe ndiswrapper 

And I think everything is okay.  

I type iwconfig and I get: 


lo                 no wireless extensions 

eth0            no wireless extensions 

eth1            no wireless extensions 

sit0             no wireless extensions



Did i use the wrong driver? I think I need help finding the right driver. Should I try the 64 bit driver I have for my card even though its not in the ndiswrapper list? Also, I didn't know wether I should put this thread here or in the 64 bit section. 

Any help you can give would be appreaciated.

---

### Post by phossal on 2007-01-27
64Bit *buntu doesn't play well with ndiswrapper. Probably not what you want to hear, but you may need to use the 32Bit version for full support. A lot of us with 64 Bit architectures use the 32Bit OS.

---

### Post by kingleer on 2007-01-27
SUCCESS!!! 

I got my wireless working. I just used the 64 bit driver for my wireless card that I found on the net for win xp x64 (had trouble getting my wireless card to work when I first insatlled xp x64but was finally able to find a driver some on made for win xp x64 for my wireless card). That was a close one. I had decided to ditch windows and had almost thrown this driver out. 

Everything works fine. Don't need any help, but I'll upload the 64 bit driver if anyone needs it. 

Actually I kinda feel like giving back. I notice that this is what a lot of link users use to get drivers for their cards: 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) 

I notice that the driver I used is not on there for 64 bit oses. How can I let people now that the driver I have is the one you ought to use?  also were could I upload it if people needed it?

---

### Post by phossal on 2007-01-27
One of the first things I did as a new member of the forums is create a tutorial in the FAQ, HOW-TO section for my wireless hardware. There was a lot of voodoo surrounding it.

I recommend doing the same for your hardware. A lot of people will be grateful! Congratulations, by the way.

---

### Post by kingleer on 2007-01-27
Thanks. But where would be the appropriate place to create this faq? Is there a special forum you are suppossed to post faqs. Also, there is a small problem of how to make the driver available to others. I have it saved on a dvd - the website is long gone.  

I notice that the forum allows us to send zip attachments. If I put the driver in an archive and upload it, will the file still be available for download a couple of months from now?

---

### Post by phossal on 2007-01-27
You probably want to post it here: [Other Support Categories -> Tutorials and Tips]("http://ubuntuforums.org/forumdisplay.php?f=100"). You can host the driver yourself, which is *very cool*. Or you can zip it, yeah. It's almost a guarantee that it's available *some*where on the web already though. Find it and post a link. I recommend viewing a bunch of hardware tutorials, too. Find a format you like, and imitate it. Here is one of mine: [How to record streaming net radio]("http://ubuntuforums.org/showthread.php?t=335642")

---

