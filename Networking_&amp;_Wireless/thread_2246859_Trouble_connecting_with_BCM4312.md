---
title: "Trouble connecting with BCM4312"
date: 2014-10-03
forum: Networking &amp; Wireless
---

### Post by rego2 on 2014-10-03
Good afternoon Really need some assistance recently put:
Ubuntu 14.04 LTS
on a hp mini 311 with nvidia ion 
My wireless network card  a (BCM4312 802.11b/g LP-PHY)
I know I can go with a wl or b43 driver
so how to do such with all this in mind
1.when my computer boots I get :the disk drive /dev/mapper/cryptswap1
2.do not have wifi (how can I get wifi)*
3.do not know how to use an ethernet wire to get the drivers that I need. computer that I am connecting it to is a hp pavilion with windows 8
4.how to get the drivers from one computer to the next then apply to receive wifi.



*I am connecting to a free wifi spot so I don't have access to wiring directly to router.

I've tried this for the ethernet connection [https://www.youtube.com/watch?v=srpTtvWkAi4](https://www.youtube.com/watch?v=srpTtvWkAi4)
I got everything running on the hp pavilion but the hp mini with ubuntu wouldn't surf the net...firefox wouldn't connect....The computer informed me that ethernet was connected.

So as you now know I don't know what to really do in my specific situation
Assistance would be appreciated.
Rego

---

### Post by Bucky Ball on 2014-10-03
*Thread moved to **Networking & Wireless**.*

Welcome. You may have better luck here. I have also changed the thread title to something more specific to give you a better chance (generic titles that don't state the issue can often be overlooked).

You can't connect with an ethernet cable? You should be able to simply plug it in and you're on. That is not happening?

Point #3 in your first post:

> 3.do not know how to use an ethernet wire to get the drivers that I need. computer that I am connecting it to is a hp pavilion with windows 8

... gives me the impression you are trying to connect to the internet by plugging in to another machine that IS connected to the internet. Is that correct, or am I missing something? If this is the case, what happens when you take the ethernet cable out of the connected machine and plug that directly into the one that is not connecting?

---

### Post by Hadaka on 2014-10-03
Hi, try this, post #7
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)

---

### Post by rego2 on 2014-10-06
Hadaka, 
I tried 
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

In the terminal after I extracted the b43 file on my desk top....
I pasted it in...buttt.......  if you don't paste, you know just type it in would one do the first line press enter put password in then type the second etc etc (in the terminal)

SO THIS IS WHAT CAME OUT OF THE PROCESS:

 sudo mkdir /lib/firmware/b43
mkdir: cannot create directory &#8216;/lib/firmware/b43&#8217;: File exists
My info:~$ 
My info:~$ sudo cp Desktop/b43/* /lib/firmware/b43
My info:~$ 
My info:~$ sudo rmmod -f b43
My info:~$ 
My info:~$ sudo rmmod -f ssb
My info:~$ 
My info:~$ sudo modprobe b43

---

### Post by rego2 on 2014-10-06
Bucky Ball,
I appreciate the welcome. The title change is much better. 
When I plug in my orange crossover cable my hp mini 311 with ubuntu 14.04lts internet bar starts lighting up. I go to ethernet connection. Its shows that ethernet is connected (two arrows north south arrows).

Ok so I just tried it: ethernet. Fire fox is not working but I can go to the ubuntu software center. When I press turn on recomendations. Its says there was a problem getting the captcha, reloading: so I cant set up an account for the moment.

---

### Post by Bucky Ball on 2014-10-06
> wl - Proprietary Broadcom STA Wireless driver

    For Chip ID BCM4311, BCM4312, BCM4313, BCM43142, BCM4321, BCM4322, BCM43224, BCM43225, BCM43227 and BCM43228.

        Install either bcmwl-kernel-source (instructions below) OR the broadcom-sta (instructions at [http://wiki.debian.org/wl](http://wiki.debian.org/wl)) packages. 

From [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx").

The fact that the computer is connecting to the network but not the WAN (the internet) points to a missing or wrong DNS address. Do you have a static IP setup in Network Manager for this connection or you are using Auto DHCP and getting one served from the router?

Perhaps compare the setup for this connection in Network Manager with the setup on the computer that is connecting fine.

---

### Post by varunendra on 2014-10-08
Hello Rego,

Can we see a detailed diagnostics report? Please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

