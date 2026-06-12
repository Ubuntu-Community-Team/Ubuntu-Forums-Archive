---
title: "Can Ubuntu switch automatically between two different network configs as needed?"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by fdejuan on 2007-05-02
Hi, I would thank some help on the following, I am sure there must be other people having the same issue, I just couldn't find anything related in the forums:

I use both Windows and Ubuntu (Edgy). Like many people I connect to the internet in two different places (home and work). In System->Administration->Network I have been able to set up two different locations (called "ubicacion" in my spanish ubuntu) so that I can choose the config for home or for my workplace (they are different, home is dinamic IP whereas work is static).

I used to have the same problem back in windows, which can be easily solved because windows allows an alternative network config, so that it tries one, and if it doesn't work, goes for the second. The good thing about this is that you don't have to keep going to Network to change the place, it's automatic. 

My obvious question is: Is there such an automatic alternative config in ubuntu? It's boring to change manually all the time... thank you very much for your help, 

Fernando

---

### Post by macabro22 on 2007-05-19
Here's my similar problem:

I have two locations - one setup as dhcp (home) and a second one as static ip (lab). Switching between them only works after reboot.

Nope. /etc/init.d/networking restart won't do.

Surprise, surprise =P

---

