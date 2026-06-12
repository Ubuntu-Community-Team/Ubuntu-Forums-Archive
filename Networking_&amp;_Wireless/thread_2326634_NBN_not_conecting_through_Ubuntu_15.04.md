---
title: "NBN not conecting through Ubuntu 15.04"
date: 2016-06-03
forum: Networking &amp; Wireless
---

### Post by paulravin on 2016-06-03
I am trying to get an NBN (National Broadband Network Australia) satellite internet connection working. The connection works with windows but I am not having any luck with the technical team at my clear networks ISP. The error message I am getting is:

(1) Creating object for path '/org/freedesktop/NetworkManager/ActiveConnection/28' failed in libnm-glib.

Any ideas how I can get connected?

Thanks in advance!

---

### Post by Bucky Ball on 2016-06-03
You might try installing a supported release and seeing if the problem persists. 15.04 hasn't been supported since January. No updates, and that includes security updates, since that time, so your system is well out of date.

If the connection works with Windows then all is well at the NBN end and doubtful there's anything they can help you with. As far as they're concerned your connection is up and operational. It would be down to the configuration in Ubuntu and they would consider that your problem, not theirs. Perhaps different if it was Windows or Mac. They might help you with the config. They probably don't know how to help you with a Ubuntu internet setup even if they were willing.  

Good luck.

---

### Post by paulravin on 2016-06-03
Yes the big turn off to using linux based systems, you don't get support. When signing onto NBN they asked if you use Ubuntu so they recognise it. I will update my system and try again.

---

### Post by paulravin on 2016-06-04
So I have upgraded my Ubuntu to 16.04, still no joy, I am not getting a connection with NBN. The NBN saterlite box is showing the right colours but the icon at the top right of my screen just continues to search.

Any ideas? Australia has spent 1 billion on this technology and I can't get it working...

---

### Post by Bucky Ball on 2016-06-05
> **paulravin said:**
> Any ideas? Australia has spent 1 billion on this technology and I can't get it working ...

Let's not go there. How much Australia has spent on the NBN has got nothing to do with this and it's working fine on Windows so you know it's working. Enough said. The issue is down to the configuration in Ubuntu, nothing more by the sounds of it so let's stay focused on that rather than supplying an opportunity for the thread to drift. ;) 

My suggestion would be to log in to Windows, write down the exact details you have for wireless in there, boot back in to Ubuntu and set the connection up manually (click Network Icon and 'Edit') using the exact details you copied down from Windows.

---

### Post by paulravin on 2016-06-06
Attempts by 3 people on 4 computers with 4 diff operating systems, the ISP help desk and this forum failed to get it working. 

BUT it is now working, here are some tips for Australians using Ubuntu to who want to connect to the new sky muster satellite.

Hear is how it is supposed to be done: [https://www.youtube.com/watch?v=Dx-G-Sn6IhY](https://www.youtube.com/watch?v=Dx-G-Sn6IhY)

Alan who did a remote fix on my computer said: 

"i just ran ppoeconf again" (in terminal) 

So I have NBN working with my Ubuntu 16.04 OS.

---

### Post by Bucky Ball on 2016-06-06
> **paulravin said:**
> "i just ran ppoeconf again" (in terminal)

And there you go. Thanks for sharing and marking as solved. If and when the NBN ever gets to where I am I'll keep it in mind. Good luck.

---

### Post by paulravin on 2016-06-15
Update after 2 weeks using NBN. 

The connection is good when I can get it, the problem I have is a sporadic connection, sometimes I can get on sometimes not. Just fantastic for work not. It really ****s your ability to work or use the net. Checks show the connection is fine it is Ubuntu and who cairs what pppe, pppoe it is frustrating and I would not recommend Ubuntu for using the NBN unless your a programmer and can be asked to constantly troubleshoot an internet connection. I am told that when my wireless router arrives that it will work (herd that before) if it does great when I am using wireless, too bad I will not be able to use my office any more as wireless does not reach it. 

I am a fan of Linux systems and remember the frustration of using windows but Ubuntu and compatibility issues with everything just makes it difficult to use, no help line will help you, your left with friends or this forum which people have really helped me on before but other times no one knows or people just commentate in an un helpful way as above. I feel embarrassed to keep asking people for help and with Ubuntu you do have to keep asking for help with the same old problems because the problems are never really solved just patched over to come back and cause trouble again. 

I have stopped recommending Ubuntu to people and can only hope artificial intelligence one day gets computer systems working consistently because humans have not been able to, we have just spawned a massive expensive industry of technicians to keep fixing it but never actually solving problems and make it stable.

---

