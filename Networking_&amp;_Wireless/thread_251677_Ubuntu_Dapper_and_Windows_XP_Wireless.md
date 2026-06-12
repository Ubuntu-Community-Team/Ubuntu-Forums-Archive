---
title: "Ubuntu Dapper and Windows XP Wireless"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by BCRailrodder on 2006-09-05
Hi All,

This is probably not Ubuntu related but any help would be appreciated.

Over the weekend, I did a fresh install on my brothers xp box - worked like a hot .. well, you know :) .  However, I was not able to double check my newphews machine as he as gone for the weekend and my brother did not have his password.

You know what's coming don't you??  Sure enough, when my newphew came home and went to use the net, he couldn't get a wireless connection.  Of course, this is now all my fault ](*,) .

Anyways, enough of story time.

As I said the linux box is working fine and can access the net with no problem.  I did nothing to touch the router settings during the install and had planned to install Samba soon.

Both machines use DCHP from the router (a wireless Linksys), the standard gateway (192.168.1.1) and DNS from the ISP.  The windows box is not able to obtain an IP from the router (from what I can tell) though I am able to ping localhost on it.  The strange thing (to me) is that the wireless NIC can see the router but will not connect to it.  I did double check the SSID and the WEP Key to make sure that they are the same.  I did find that the key was not being accepted by the nic settings as they would change back everytime I tried to connect.  I would have to manually enter the key when I would try to connect. As well, we did try the original setting of trying to get the key from the router automatically.

When I am in the router, it does not see to see the windows box as I am not able to get a MAC registered automatically.  I did not have time to try to manually set the IP, Gateway, DNS, MAC and Key on the box and the same on the router though I may do so tomorrow.

Like I said, I am 95% sure that this has nothing to do with my installing Dapper but since this is the only change (they tell me), I am trying to clean it up so they get a good impression of Ubuntu.

Any help is greatly appreciated before I go back tomorrow.

Thanks in advance,

Kent

---

### Post by tbonius on 2006-09-06
Temporarily disable WEP on the Linksys router to make sure Windows can attach to it.  After you have verified this.. re-enable WEP and make sure you are using the right length WEP key.. some Windows SP2 boxes have issues with Alpha vs. HEX WEP keys of invalid lengths.

T

---

### Post by BCRailrodder on 2006-09-06
Yep, tried this today with no luck.  The XP box can see the SSID but can not connect yet the router seems to be picking up a wireless connection (according to the front panel).  The just don't want to talk to each other.

I did manage to increase the signal strength by moving the antenna on the XP box but this did not solve the problem.

According to my inexperienced eyes, I can see nothing wrong with either item so I am pretty sure that it is something simple that you can overlook 10 times before it clicks :}.

The good news is that I did manage to convince both my brother and nephew that Ubuntu (and I) are not to blame :}.  I have set both up as users and while they do not like to share, they are getting along and playing nice :}.

Now back to the net to try and figure this pain in the derreraire out.

By the way, helpful suggestions are still appreciated <G>.

Kent

---

### Post by tbonius on 2006-09-06
I am happy that you convinced them that Ubuntu does not appear to be the issue.  The sure way to prove that is simply disconnect the Linux computer from the Wireless Hub/AP and try to connect with the Windows laptop.  

I dont really know what to tell you.. maybe one of the two wireless interfaces crapped out.  Try a different wireless NIC in the laptop.. and maybe a different driver (I had to upgrade my SMC wireless driver after updating Xp to SP2).

T

---

### Post by BCRailrodder on 2006-09-06
Hee, that's pretty much what I did.

I've been doing some more research and have come across a couple of items to try - hopefully they will work.

Kent

---

### Post by BCRailrodder on 2006-09-08
Well, I've pretty much given up for the next day or two.  We ended up running a cable to the XP Box and it worked right away.

I am going to give it a rest for a couple of days to think about other issues and maybe the answer will come to me :}.

Kent

---

