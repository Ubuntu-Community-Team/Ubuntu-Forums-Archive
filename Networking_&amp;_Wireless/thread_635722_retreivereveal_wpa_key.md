---
title: "retreive/reveal wpa key"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by dirty_CDrom on 2007-12-09
Hey Hey, I need help!

I am going to reinstall Ubuntu on a desktop that gets onto the Internet thru a wifi router.

I can't find where I wrote down the WPA key. I am not the admin of the ROUTER, so I can't just logon to the router and have it tell me what the key is.  

The sys admin doesn't work here either, he is a subcontractor of sorts (this is a small company so the owner doesn't have an IT dept) so I can't ask him for the key until he comes in for something else or he'll charge  :roll: he is somebody the owner calls when there is a problem or she wants to upgrade something, then he comes in. Believe it or not, they are still using netware 4.11 and windows 95 workstations! ](*,):lolflag: I am trying to get her to let me upgrade everything and be the "sys admin", I won't touch the stuff she has running now though, or I'll get blamed when something goes wrong, and its a weird setup anyway, with third party links between old telemagic and account databases, half the stuff from third party companies that no longer exist  #-o 

I could do something with vmware maybe if nothing else, so she can run her archaic system on newer hardware thats not falling apart (vmware would give me a chance to learn how the crap is setup through trial and error,  without destroying what she has running now)


So anyway, my ADD is showing, going way off the topic of my support request ....  I am the "admin" of the sole desktop here that runs linux (everything else is windbloze), so thats not a problem insofar as permissions, if needed to get the key in plaintext so I can write it down again and do the reinstall.

How do I do this?

Thanks!

---

### Post by Lostincyberspace on 2007-12-09
Could you ask some one else? That would be the easiest way

By the way were are you. You still use 95 even die hard windows people agree it sucks.

---

### Post by dirty_CDrom on 2007-12-09
> **Lostincyberspace said:**
> Could you ask some one else? That would be the easiest way

Nope, there are 14 workstations here, only three go on the Internet. All the employees use a windows 2000 box that's set up in a public area if they have to use the Internet. I'm an exception, as most of the employees don't need  Internet for their jobs much, so she took it away after there were problems with people downloading porn (which almost resulted in a sex harassment suit after another employee inadvertently saw some weird bondage stuff on another employees screen) and getting viruses, gambling online, etc :lolflag:  Those two computers go directly to the wifi router with Ethernet cable, only mine uses the wifi cuz of the logistics of running the cable to the other side of the building where my office is. And the sys admin consultant/contractor uses it with his laptop when he has to come in and fix something. 

> **Lostincyberspace said:**
> 
By the way were are you. You still use 95 even die hard windows people agree it sucks.

Everybody thinks it sucks, but some of the apps here bug out and crash when trying to use anything newer, for various reasons (32 bit drivers even if backward compatible with 16 bit, etc). She has been afraid of the "learning curve"  with her employees, she had to send them to training way back when, to get them to understand what they are using. Only way I'll get her to upgrade everything is if I can do it cheap (lots of open source stuff would fit the bill), and keep her legacy system running with vmware as a security blanket until she felt it was safe to cut the umbilical cord to Bill Gates' living abortions

---

### Post by Lostincyberspace on 2007-12-09
You would have to talk to the admin then. I would write the pass on the back of something that you keep in your wallet like a picture just to keep it safe once you find it. If there were more people connect then you could crack the pass off their transmissions but that is illegal.

---

### Post by dirty_CDrom on 2007-12-09
> **Lostincyberspace said:**
> You would have to talk to the admin then. I would write the pass on the back of something that you keep in your wallet like a picture just to keep it safe once you find it. If there were more people connect then you could crack the pass off their transmissions but that is illegal.

You  can crack WPA that way? I've heard of cracking WEP, but thought WPA was pretty tough.

I don't get along with the sys admin guy, I think he suspects am trying to get the owner to let me have a crack at upgrading everything, and taking over the responsibility. of keeping it running (thereby causing him to lose a client). So hate to ask him for that reason, on top of the fact he'll probably bill for the service call.  

THere isn't a way to retrieve the key from where its stored on my computer? In the past, I've used utilities to get back passwords stored in Windows pwl and sam files. Or what if I make a copy of the file storing the password, then just restore it in the new install? Reason I want to do a fresh reinstall is for various reasons BTW, putting in a new drive, and I want to try a better partition scheme

---

### Post by Lostincyberspace on 2007-12-09
I didn't say it wasn't hard to get the key, which it is; takes a couple of days on a fast system, just able to be done. Oh it is not gotten rid of totaly I thought it was gone for good. I will have to think about it to figure it though.

---

### Post by dirty_CDrom on 2007-12-09
Okay, thanks for the replies Lost.  I'll check back later. 

Here is a thread I found by searching before I decided to post a question:

[http://ubuntuforums.org/showthread.php?t=614771&highlight=show+wpa+key](http://ubuntuforums.org/showthread.php?t=614771&highlight=show+wpa+key)

A couple posts show some paths to where the key file might be stored?

If you or anybody else thinks that I can make a backup of a specific file (or files) and then restore them after the new install, please lemme know.

---

### Post by ekravche on 2007-12-09
I think your safest bet is to reset the router, and then reconfigure it with a new password. Or even better, expand your network by getting another wireless router and install it closer to your office

---

### Post by dirty_CDrom on 2007-12-09
Eh, just noticed I misspelled "retrieve" in title :oops: Wouldn't be so bad if it wasn't my first post! :D


Anyhooo, is it possible to put a linksys router behind a linksys router that's the gateway? Will it act like a switch and let me have wifi that I configure?

---

### Post by dirty_CDrom on 2007-12-09
> **ekravche said:**
> I think your safest bet is to reset the router, and then reconfigure it with a new password. Or even better, expand your network by getting another wireless router and install it closer to your office

ekravche, that's what I'll do, I found the answer to my previous question, it should work so long as I make the "LAN within the LAN" a different subnet.


> Linksys router address 192.168.1.1 mask 255.255.255.0
Linksys LAN addressing 192.168.1.X subnet mask 255.255.255.0
Netgear router WAN address. Must be on the linksys LAN subnet mask 255.255.255.0
gateway address is the Linksys router address.
Netgear router address 192.168.2.1 mask 255.255.255.0 [note: must be different subnet than Linksys]
Netgear router LAN addressing 192.168.2.X mask 255.255.255.0
default gateway Netgear router address.

DNS is ISP DNS servers for both routers and all clients.


[http://techrepublic.com.com/5208-6230-0.html?forumID=101&threadID=208647&messageID=2153008](http://techrepublic.com.com/5208-6230-0.html?forumID=101&threadID=208647&messageID=2153008)



I have an older linksys wifi router at home that I'm not using, I have been wanting to try this hack, now is my excuse! 
> 
Of all the great DIY projects at this year's Maker Faire, the one project that really caught my eye involved converting a regular old $60 router into a powerful, highly configurable $600 router. The router has an interesting history, but all you really need to know is that the special sauce lies in embedding Linux in your router. I found this project especially attractive because: 1) It's easy, and 2) it's totally free


[http://lifehacker.com/software/router/hack-attack-turn-your-60-router-into-a-600-router-178132.php](http://lifehacker.com/software/router/hack-attack-turn-your-60-router-into-a-600-router-178132.php)
.

Heh, if that hack works, I won't have to put it all that close to my office :D

edit: I thought about resetting the router, but a certain person gets really territorial if anybody changes anything he set up, even if its something inconsequential. So your "even better" suggestion is the way2go. Why didn't I think of that? *slaps forehead*. If I lose the key again, no hassles this way :D

---

### Post by Lostincyberspace on 2007-12-09
Its been done. I think they actualy have instructions on their site some where.

---

