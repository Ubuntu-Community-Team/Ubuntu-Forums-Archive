---
title: "How to Install Brother MFC-J430w Wireless Printer"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by Bob_Lade on 2014-03-19
From the printers list, I see the printer I have on my wireless network. Actually the printer appears twice on the list. I think that may be because it is hard-wired to one of my computers and I'm using it as a wireless (WiFi) printer on all the rest of my computers. The two choices I have from the list on Ubuntu 12.04 are:
1. Queue: Binary_P1   and the 2nd gives a description, not a queue as
2. appSocket/JetDirect network printer via DNS-SD

I'm guessing the first one is the one I want. Anyway, I select it and click "forward" and the first dialog box is "searching For Drivers" then I get another dialog box "Additional Drivers" and the system seems to "hang" at this point. Probably because it can't find a driver for the printer???

I get the same results if I try to install the 2nd version on the list.

Any words of wisdom regarding how I can go about to get this printer installed? You guiys have bailed me out on several problems I've had and I'm hoping you can once agqain save the day. TIA...

Dr. Bob

---

### Post by untrustytahr on 2014-03-19
I can't speak to your particular model but I have an early Brother MFC and just used the deb installer from Brother.  Worked fine and saved me from a lot of headaches.

[http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/dlf/000000/006800/dlf006893.html?reg=us&c=us&lang=en&prod=mfcj430w_all&type2=91&os=128&flang=4&dlid=dlf006893](http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/dlf/000000/006800/dlf006893.html?reg=us&c=us&lang=en&prod=mfcj430w_all&type2=91&os=128&flang=4&dlid=dlf006893)

---

### Post by gifford on 2014-03-19
The safest and most reliable way is to go to the Brother site:[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
Download and install all the drivers following the instructions on the site. Read the instructions carefully and make sure to do the pre-requirements.

---

### Post by Bob_Lade on 2014-03-19
[COLOR=#DD4814][COLOR=#000000][untrustytahr]("http://ubuntuforums.org/member.php?u=1895014"):

Thanks! That worked great. Also gave me a chance to re-learn a little command line stuff in the process.

-Dr. Bob[/COLOR][/COLOR]

---

### Post by Bob_Lade on 2014-03-19
Gifford: That's exactly what I did. Thank you for your response! Works great.

-Dr. Bob

---

### Post by gifford on 2014-03-19
Glad you got it solved. 
In my experience, installing following the instructions on the Brother site has always been the best.

---

### Post by Bob_Lade on 2014-03-20
I'd like to mark ths thread as "Solved" but can't find a way to do so. Any advice?

-Dr. Bob

---

### Post by untrustytahr on 2014-03-20
Glad you got it working.  Be careful with the CLI... once you know what it can do you'll never go GUI ;)

Marking solved (et. al):
[http://ubuntuforums.org/showthread.php?t=726150&p=4527051#post4527051](http://ubuntuforums.org/showthread.php?t=726150&p=4527051#post4527051)

---

