---
title: "Bringing up wireless automatically"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by Yeuclid on 2007-05-02
I am running 7.04, my 4th excursion into Ubuntu and I must say it gets better all the time.

Just one gripe I have is that I have to manually start my wireless network by doing a "sudo ifup wlan0" from the terminal window each time I boot the system so that I get the wireless extensions loaded and DHCP fired up from my router. 

I have a cheap and cheerful Prism 11B USB wireless adapter which Ubuntu recognises as a native device so I don't have to resort to Ndiswrapper. so it should all be very simple in theory.

I have tried the admin Network application, and nm-applet, and wifi radar but they are ineffective.

Is there something I am missing here? How do I configure it to just start up by itself?

Surely it should be an automatic process, just like that other operating system which does it so well.

---

### Post by jfinkels on 2007-05-02
> **Yeuclid said:**
> I am running 7.04, my 4th excursion into Ubuntu and I must say it gets better all the time.

Just one gripe I have is that I have to manually start my wireless network by doing a "sudo ifup wlan0" from the terminal window each time I boot the system so that I get the wireless extensions loaded and DHCP fired up from my router. 

I have a cheap and cheerful Prism 11B USB wireless adapter which Ubuntu recognises as a native device so I don't have to resort to Ndiswrapper. so it should all be very simple in theory.

I have tried the admin Network application, and nm-applet, and wifi radar but they are ineffective.

Is there something I am missing here? How do I configure it to just start up by itself?

Surely it should be an automatic process, just like that other operating system which does it so well.

If you don't find an answer, you can make a script and then add that to your startup programs in "System > Preferences > Sessions". It would look something like this:```
#!/bin/bash
gksudo ifup wlan0
```
This will prompt you for your password everytime you log in, of course.

---

### Post by Yeuclid on 2007-05-02
Thanks, I had considered that option, but would rather persevere to fund a "purer" solution, i.e. how to make it work properly in the first place, as it should.

Although I can cope to some extent with the CLI approach, it reminds me of the old DOS prompt, ah, nostalgia, seems a long time ago now though.

But I'm grateful for your suggestion nevertheless. Help is always appreciated.

---

### Post by jfinkels on 2007-05-02
> **Yeuclid said:**
> 
Although I can cope to some extent with the CLI approach, it reminds me of the old DOS prompt, ah, nostalgia, seems a long time ago now though.


If you want to stick with Linux, better get used to the command line...it's your friend! :D

I hope you find a solution.

---

