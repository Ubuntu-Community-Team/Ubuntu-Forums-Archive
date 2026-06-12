---
title: "Linksys router"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by denethor101 on 2008-04-26
I just put Xubuntu version 7.1 on my computer. I am running a Linksys Wireless-G Broadband Router (Model WRT54G) from Windows XP. I am trying to get my Wireless G Receiver (Model WUSB54GC) on my Xubuntu computer to pick up the internet from my router. When I tried to install my receiver, I found out that xubuntu doesnt run .exe files, but runs .deb files instead. I tried to do some research, and found on linksys' website that their products only work with vista and xp. However I have heard of people using linksys products with xubuntu. I was just wondering how I could get this to work. Do I have to somehow convert .exe files to .deb? Or can I not use Linksys products.

I am new to xubuntu and Linux OS....I dont understand a lot of stuff so please be patient with me if i dont get it the first time (or three)...Im pretty experienced with XP but wanted xubuntu so i could get to know other OS's before i enter the real world of college....anyhow...any help is appreciated... Once i get internet on that computer Im good.

Thanks

---

### Post by pparks1 on 2008-04-26
Ummm...linksys products work just fine on systems other than windows.  they work just fine on Mac's, PC's, Linux, game consoles (Xbox360's, PS3's, Wii's).

There really is no need to run any software to get a Linksys router to work.   There might be a need to install a driver for a linksys wireless card...but you aren't going to be able to use the Windows based .exe.  Rather you have to find a suitable Linux driver.

However, you kept saying router, so I assume you are talking about the router.   I have a WRT54G that I am currently using from my Ubuntu 8.04 machine running wireless.

---

### Post by kai60 on 2008-04-26
One of the keys to installing and troubleshooting anything in Linux is to Google the problem that you are having.

Some of the key things that you want to find out for your issue is the chipset that your Wireless G Receiver is running, such as broadcom or prism. With that information, we are then able to help you to troubleshoot your connection problem. Don't worry, most devices can be made to work in Linux. 

In regards to your exe files, they are a Windows native executable and a deb file is an installer in Debian based Linux, such as Ubuntu. I hope this helps, don't hesitate to post back once you have some more data and we'll see what we can do to help.

---

### Post by denethor101 on 2008-04-26
well, i have my receiver on my xubuntu and my wireless router on my XP...

and i have no idea why the linksys site said it only worked with XP and vista products...maybe i read it wrong...

okay thanks for the help...all i could find was a .exe driver....I will look for one that will work with linux. Thanks.

---

### Post by kai60 on 2008-04-26
You will find that Linux doesn't work quite the way that Windows does and the odds of you finding a driver out there for your Receiver are almost zero, I really do suggest that you find out what chipset the Receiver is using and then post that back here and we'll be able to help you run it. 

The router is irrelevant for this exercise mate. It has to do with your Linux driver and firmware for your Receiver.

---

### Post by denethor101 on 2008-04-26
I figured the router didnt matter....but wasnt sure....

I really really really really hate to sound stupid, but here goes...um..whats a chipset? okay its over...sry about that...

---

### Post by bribri124 on 2008-04-26
In a nutshell, the chipset will determine what driver you need in order to have your wireless adapter working.  I looked it up for you, and and it uses 'rt73usb'.  According to the Ubuntu Wiki, it should work with Hardy "out of the box."  You can find this at **[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)**.

I hope this helps you out a little bit, although I didn't explain about the chipset very well.  Keep on asking questions, and everyone will keep on giving you good answers.

---

### Post by denethor101 on 2008-04-26
wow...thank you so much.......this place is actually really helpful.....I think I'll wait till tm to get it goin, but I think I can figure it out from here.......Again, thanks a lot.....this really helps

---

