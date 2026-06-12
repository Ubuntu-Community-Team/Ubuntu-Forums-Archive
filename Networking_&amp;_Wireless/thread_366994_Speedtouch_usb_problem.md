---
title: "Speedtouch usb problem"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by celticbhoy on 2007-02-21
Hi looking for some help to finish setting up my internet conection. I normally connect using an orange livebox and an ethernet card and all works well, but becuase of a problem with my livebox I will have to use my old speedtouch usb modem to connect for a couple of weeks. The problem is this I have followed all the tut's I can find and searched the forums and so far I can get the modem to connect, the system log shows that I have a connection and the upload & download speeds, but whenI start firefox I cant get on-line. I dont know if the problem is the ethernet card was the defualt conection before I tried to set the speedtouch modem up, but if anyone can help I would be most grateful, as I am stuck to using XP in the meantime.

---

### Post by samadams on 2007-02-22
celticbhoy,

I have the same problem.  After much frustration I finally can get my Alcatel dialed in via pppoatm (though not yet automatically)  but I too cannot connect to anything.  Firefox, Evolution, apt-get, etc. etc. do not work.  I've posted this question several times here with no response. (a few of them seemed to disappear too.)  Hope you have better luck.

---

### Post by slayerboy on 2007-02-24
This might help...

[The Linux Kernel SpeedTouch Driver And Ubuntu]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")

---

### Post by samadams on 2007-02-26
Thanks but I already went through that page.  I used it to set up my connection from the start.  It didn't work.  I had to get help from Alcatel for a work around.  Now the modem dials in (though I have to do this manually every session), and is connected - but nothing in linux will communicate with it.  I'm not sure about the original poster, but I think he's having the same problem.  As I understand it the problem is with DNS - but I don't have the foggiest idea of how to solve it or where to begin.

---

### Post by Bert the Button on 2007-03-04
I just posted this to samadams thread... Check your VPI and VCI settings.  After these are correct the logs will show not only your line speeds but your IP address and that of your ISP.

> Hello there! I've just managed to connect for the first time under linux after the same sort of symptoms as yourself. My error was in the VPI and VCI settings. These are displayed as 0.00 in the tuts for you to edit. After reading all the lit that came with the modem mine turned out to be 0.38, and absolutely nothing to do with the modem firmware version. (what a complete windows muppet I am...)

Hope this helps :) 

---

