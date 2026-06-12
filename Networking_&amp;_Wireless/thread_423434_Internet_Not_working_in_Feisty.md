---
title: "Internet Not working in Feisty"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by NYIslander on 2007-04-25
I made the upgrade today from Edgy to Feisty today and for the most part, it went smoothly. However the NIC in the computer won't allow me to connect to the Internet and I cannot pull up any web pages. It managed to see some updates I need but can't download them and I'm connected into a WRT54GS router that I've been able to use without any problems prior to this. What do I have to do to correct this problem?

---

### Post by PhotoJoe on 2007-04-25
I did the upgrade this afternoon (from Edgy to Feisty) with the exact same router you've got,  and I've had no problems...well, no Internet problems, anyway.

This sounds more like a connectivity problem versus Feisty problem. Are any other systems on the router and are they working? Cables and NIC lights okay? Have you tried loopback, ping, tracert, netstat and ifconfig (terminal)? Let me know how you make out or if you need more help.

---

### Post by PhotoJoe on 2007-04-28
Any luck? I'm curious to know how you made out. Since I have the same router, I'm wondering if I have a potential problem they may rear its ugly head and bite me.

Good Luck!

---

### Post by NYIslander on 2007-05-01
> **PhotoJoe said:**
> Any luck? I'm curious to know how you made out. Since I have the same router, I'm wondering if I have a potential problem they may rear its ugly head and bite me.

Good Luck!
Sorry for the late reply, it's been a busy few days and I couldn't do much troubleshooting

I kept getting error messages in ifconfig regarding the connection and ping got me nowhere since it wouldn't allow me to test a IP address, I don't think it has anything to do with the router since I was able to use the Internet in Edgy as well as in other operating systems so I think something in the current release broke the connection in my NIC (standard card you get for getting cable internet service)  but I can't say that with certainity plus the fact that it could see updates indicted that the connection was working but disabled in some way.

I'm trying to duplicate the results in other distros as well using Live CD's, Linux Mint 2.2 couldn't connect either but its been the only one so far (I'm installing Debian 4 to see if it's a overall problem for just in Ubuntu based distros). Once I test Debian, I might be able to narrow the problem. Hopefully I can try to fix this problem soon.

---

### Post by Toadmund on 2007-05-02
Here is a page that may be of help, wether you use DSL or not:
[http://www.wikihow.com/Configure-Home-DSL-for-Use-in-Ubuntu-Linux]("http://www.wikihow.com/Configure-Home-DSL-for-Use-in-Ubuntu-Linux")

My brother can't connect either to his DSL phone line service, we tried taking out the router, still no connection, so we know it's not the router. Today I called him on the phone to ask him to run the live CD and see if he gets the net, (in the link) and to write down the settings in System-->Administration-->Network, but he was tired and his computer didn't boot it, we went to BIOS, to switch to 'Boot from CD', but I don't know he was to tired at the time to bother much with it.

So try The CD thing (see link), or bypass the router to rule out a router problem.

Good luck :)

---

### Post by NYIslander on 2007-05-02
> **Toadmund said:**
> Here is a page that may be of help, wether you use DSL or not:
[http://www.wikihow.com/Configure-Home-DSL-for-Use-in-Ubuntu-Linux]("http://www.wikihow.com/Configure-Home-DSL-for-Use-in-Ubuntu-Linux")

My brother can't connect either to his DSL phone line service, we tried taking out the router, still no connection, so we know it's not the router. Today I called him on the phone to ask him to run the live CD and see if he gets the net, (in the link) and to write down the settings in System-->Administration-->Network, but he was tired and his computer didn't boot it, we went to BIOS, to switch to 'Boot from CD', but I don't know he was to tired at the time to bother much with it.

So try The CD thing (see link), or bypass the router to rule out a router problem.

Good luck :)

bypassed router, no luck. However, The problem seems to be with Debian since it won't connect to the Internet either so whoever took care of networking there probably deleted or changed something in order for it to break. I do like Ubuntu, especially since it was the first linux OS to get my sound card working but if I can't connect to the Internet with it, it's useless to me

---

### Post by Toadmund on 2007-05-02
Did you try the live CD thing, to see if you can get online with that?
Then if it does, write down the info and compare to the downloaded version.

Some people can get net with CD, but not with installed.

I will let you know how I make out with my brother if I get him at a co-operative time.

---

### Post by NYIslander on 2007-05-02
> **Toadmund said:**
> Did you try the live CD thing, to see if you can get online with that?
Then if it does, write down the info and compare to the downloaded version.

Some people can get net with CD, but not with installed.

I will let you know how I make out with my brother if I get him at a co-operative time.

Tried live CD, didn't work (I had already considered the idea that a Live CD's internet would work after install but that didn't help after a install)

---

### Post by Toadmund on 2007-05-02
Hmmm, I'd like to try the live CD thing, but alas, my bro can't get it to boot, It booted up for him to install it, but not now. Don't know if his BIOS is right or not.
I hate helping with computer problems over the phone!

---

### Post by PhotoJoe on 2007-05-03
> **NYIslander said:**
> bypassed router, no luck. However, The problem seems to be with Debian since it won't connect to the Internet either so whoever took care of networking there probably deleted or changed something in order for it to break. I do like Ubuntu, especially since it was the first linux OS to get my sound card working but if I can't connect to the Internet with it, it's useless to me

Right now, I'm fresh out of ideas...I'll keep pondering, though. I just can't understand why I'm problem free (other than the self-inflicted ones) and you can't even connect, given our similar situations.

Don't give up on the Linux, though. I've had a lot of frustration with both Fedora (box I'm on right now) and Ubuntu but I've found the  effort and study on my part was worth it in the end. Stay with it and keep coimng back to the froums. Sooner or later someone will figure this out!!

By the way, can you post your 'ifconfig' results in here? Maybe someone can make heads or tails out of the error messages.

---

