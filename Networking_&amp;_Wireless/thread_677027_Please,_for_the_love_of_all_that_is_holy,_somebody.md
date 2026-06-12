---
title: "Please, for the love of all that is holy, somebody help with my EVDO card!"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by boriquajake on 2008-01-24
Please, I am begging, could someone with experience in dealing with EVDO cards in Ubuntu could please help me get my Kyocera kpc650 card working? The card is active with centennial wireless and it works fine in Windows so all I need is some help. I have tried to follow several of the other how-tos out there with no luck. I am willing to pay someone for their time if they can help me get this working.

---

### Post by jeffus_il on 2008-01-24
Have you looked at this:
[http://ubuntuforums.org/archive/index.php/t-77364.html](http://ubuntuforums.org/archive/index.php/t-77364.html)

and this:
[http://www.linuxquestions.org/questions/linux-hardware-18/verizon-wireless-kyocera-kpc650-broadband-card-501686/](http://www.linuxquestions.org/questions/linux-hardware-18/verizon-wireless-kyocera-kpc650-broadband-card-501686/)

and this:
[ http://64.233.183.104/search?q=cache:YDO_FcxAZxkJ:wireless-internet-broadband-service.com/evdo-linux-kpc650-v650-driver.doc+Kyocera+kpc650+linux&hl=en&ct=clnk&cd=6&gl=il&lr=lang_en|lang_iw&client=firefox-a]("http://64.233.183.104/search?q=cache:YDO_FcxAZxkJ:wireless-internet-broadband-service.com/evdo-linux-kpc650-v650-driver.doc+Kyocera+kpc650+linux&hl=en&ct=clnk&cd=6&gl=il&lr=lang_en%7Clang_iw&client=firefox-a")

---

### Post by boriquajake on 2008-01-24
Yes, I have seen that. The problem is that I am not adept enough at using linux to be able to understand bare instructions like that. I spent who knows how many hours trying to follow that guide with no luck. I really need someone to sort of walk me through it. As I said I would be happy to pay.

---

### Post by yellowbread on 2008-01-24
I don't have a Kyocera kpc650 card, but have set up evdo on ubuntu. If there's someone else having direct experience with this card, feel free to jump in and take over.

First, what is the result of the command in a terminal: lsusb

If none of the devices listed are clearly your evdo card, try it with the device removed, and then attached. Post the results here and then we'll move on to the next step.

---

### Post by Mach1US on 2008-01-24
> **boriquajake said:**
> Yes, I have seen that. The problem is that I am not adept enough at using linux to be able to understand bare instructions like that. I spent who knows how many hours trying to follow that guide with no luck. I really need someone to sort of walk me through it. As I said I would be happy to pay.

You really look desperate:wink: i posted hopefully final sugestion on my EVDO  thread.
[http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo](http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo)

---

### Post by boriquajake on 2008-01-24
> **yellowbread said:**
> I don't have a Kyocera kpc650 card, but have set up evdo on ubuntu. If there's someone else having direct experience with this card, feel free to jump in and take over.

First, what is the result of the command in a terminal: lsusb

If none of the devices listed are clearly your evdo card, try it with the device removed, and then attached. Post the results here and then we'll move on to the next step.

Wow, I just reread the title of this thread and I really sound like a whiny little bi-atch. I am sorry if my tone sounds ungrateful, or, well, whiny. :)

Here are the results of lsusb:

> Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0c88:17da Kyocera Wireless Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


As you can see, my card is a least now being seen by the system somehow.

---

### Post by yellowbread on 2008-01-24
You didn't sound whiny or bitchy, just frustrated and starting to get desperate. 

On the possibility that most of your work is already done, try:

 ls /dev/ttyUSB*

 and

 ls /dev/ttyACM*

 with and without the device plugged in and see if there is a difference. With my modem, simply connecting it is enough for  the driver to recognize it and set it up on /dev/ttyACM0. From what I've read, the usbserial driver works with your modem and should set it up on /dev/ttyUSB* for some value of *, probably * = 0.

---

