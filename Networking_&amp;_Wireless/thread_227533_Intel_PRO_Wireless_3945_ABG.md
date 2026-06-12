---
title: "Intel PRO Wireless 3945 ABG"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by aam-aadmi on 2006-08-01
I can't get my wireless card (Intel PRO Wireless 3945 ABG) to work on my new Dell Inspiron E1405. I am using Dapper Drake 6.06. I have been trying to search the forum threads but have not yet come across any helpful thread. Could anyone help?

---

### Post by MarkSheely on 2006-08-02
Hi,

I replied to you in your other thread - but just in case you aren't watching that thread anymore, I'll post again here.

The IPW3945 should work out of the box on a E1405.  What specific problems are you encountering?  Is it just a matter of you aren't sure what to do to connect to the internet?

Let me know, and we'll get to the bottom of this (hopefully)
--Mark

---

### Post by aam-aadmi on 2006-08-02
Mark,

Thanks for your reply. Yes, I am not sure how to go about connecting to the internet using the wireless card. Your help will be greatly appreciated.

Thanks.

---

### Post by 5-HT on 2006-08-02
For a really easy way to configure your wireless (incl. WPA, WEP) have a look at either network-manager-gnome or network-manager-kde.

Once installed, after a reboot you should see the network-manager applet icon in the notification area. Clicking on the icon should yeild the available networks you can connect to, as well as the option to create your own connection.

It's a really great app!

---

### Post by aam-aadmi on 2006-08-02
Thanks for the information; I will install network-manager-gnome and try to set up my wireless connection.

---

### Post by Liam on 2006-08-02
Make sure you turn on the wireless card, too: FN+F2

I bought the same machine (did you get the $350 off?) and got stuck for a good half hour on that one.

#-o

---

### Post by aam-aadmi on 2006-08-02
Liam,

Yes, I got the $350 off. And it is good to know that someone else with the same machine has got the wireless working! I have lost almost a whole day trying to get it to work.

So, do you just turn on the wireless card with Fn+F2 and then use the Network Manager to set up your wireless? Or is there anything else that needs to be done? If you have the time do put in a few lines explaining exactly how you went about it. That would of great help.

Thanks in advance.

---

### Post by aam-aadmi on 2006-08-02
I have finally been able to get the wireless connection working! Actually, Mark was absolutely correct. The Intel Pro Wireless 3945 ABG on Inspiron E1405 works out of the box. One just has to get the wireless card working (FN+F2), check the name of the wireless card by using
```
iwconfig
``` 
putting the correct gateway in the System-> Administration-> Networking window and then choosing the desired network.

One can look at the following helpful HowTo link for related details:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Thanks for all the help guys.

---

### Post by MarkSheely on 2006-08-03
That's great!  

Enjoy your new laptop -

-Mark

---

### Post by Schnoidz on 2006-08-29
My e1405 connects easily at work on an open network, works great and never drops connection.  My problem is at home where my Linksys WRT54G (V5) uses WPA.  It will only connect if I boot into XP, not Dapper.  Have any of you been able to get WPA working with the IPW3945ABG yet?  Could you please point me to some instructions that worked for you?  Any help would be greatly appreciated!

---

### Post by domib on 2006-08-30
I have the same card in my hp dv8000, and it is recognised fine by dapper, and network-manager-gnome sees it and looks like it will connect with WPA, it lets me put all the params in, but then it can't do it. 

if I iwlist eth1 scan, i can see the network i'm trying to connect to. it just won't connect. I have a desktop in the next room running breezy that's connecting just fine, it's an rt2500 configured using iwpriv.

---

### Post by rsk on 2006-09-07
I don't know who else fell into this boat, but it took me 6 hours to figure out I was a moron. I had my router setup to do WAP, and kept using the gnome network manager to setup my WEP key, not realizing the difference until 10mins ago.

I changed my router to WEP, and viola, everything works out of the box.
BTW I'm on a ThinkPad T60, I've been reading these threads for hours, following up incase *anyone*, even one person had the same problem I did. (More details [here]("http://www.breakitdownblog.com/2006/09/07/ubuntu-606-thinkpad-t60-wifi-ipw3945-wepwap/"))

---

### Post by hepkat63 on 2006-09-08
Hi All,
I have been reading the forum with interest as I just cannot get my wireless to connect.  I too have a Dell Inspiron 6400 with the Intel Wireless chip.  I can certainly see my access point - 5/5 signal, but it just will not connect no matter what I do.
I have tried WEP 64 bit, 128 bit - no luck. Open system, shared key - even no passwords at all - but it just will not connect up.
So, I cracked it and rebuilt the laptop back to windows spec (yuk) and of course it worked perfectly @#$$#!
so, rebuilt the laptop again with latest ubuntu 6.06 , downloaded all the updates and patches and tried again - still the same.
Stupid thing is, i bought the laptop to use wireless and it is the only thing not working.
Can some one please point me in the right direction as I am going crazy here.  If the wireless card can see the access point, there must be something really silly and simple I can do to connect.  I am just using gnome interface.  I did download the kde wireless assistant and tried to connect using that - but same ' connection failed ' error.  Is there a log or something in ubuntu that you can view to see WHY it is not connecting?
thanks
Steve

---

### Post by rsk on 2006-09-08
Ok for folks that had this problem I've read that you may need to:

modprobe -r ipw3945

then wait a sec and modprobe ipw3945

then see if you can connect. Also try typing iwconfig and see if any wireless networks are detected. Additionally you can install wifi-radar to see if it can tell any networks around you.

If you see ANY wireless networks with iwconfig or wifi-radar, then your driver is fine, if you don't see any networks, then it can be your driver. While you are troubleshooting this, be sure to turn off all the security settings of your router so it's the easiest to setup.

---

### Post by hepkat63 on 2006-09-08
thanks for the reply - but have already done this.  My problem is not that I cannot see the Wireless network - but cannot CONNECT.  Any other ideas?

---

### Post by rsk on 2006-09-08
> **hepkat63 said:**
> thanks for the reply - but have already done this.  My problem is not that I cannot see the Wireless network - but cannot CONNECT.  Any other ideas?

This sounds exactly like what happened to me, in which case I would say disable ALL the security on your router, just forget about it totally, turn it all off so it's completely open, then reboot it. Then reboot your computer and fire up wifi-radar, do you see your network? Now try and connect to it.

As I mentioned, it tooks me 6 hours... 6 HOURS, before I realized I was trying to connect to a WAP network using WEP settings, I wanted to commit suicide.

The good news is that since you "see" the network, your drivers/hardware are fine, it's just some stupid setting somewhere.

If you have mucked up your networking too much on your computer by playing with it, try rebooting with the LiveCD to have a "fresh start" and see if you can get it working from there.

---

### Post by hepkat63 on 2006-09-08
Hi, thanks for the reply.
Actually, if you read my thread, I have tried this already - but thanks anyway.
It makes no difference, I just cannot connect - if I use Windows, it works just fine.  I have two other appliances connected to the router as well -  (one workstation - windows, and one notebook, windows) that work just fine, so it is not the router.
As mentioned, I have put the router in 'open' mode - no passwords or anything and restarted ubuntu, but no good either.  yes, you are correct, the drivers APPEAR to be working, but perhaps not as they will not connect.  Any other ideas?  i THINK that i read somewhere that the latest driver does not work properly and you need a previous one or something???

---

### Post by drubulvr on 2006-09-26
> **Liam said:**
> Make sure you turn on the wireless card, too: FN+F2

I bought the same machine (did you get the $350 off?) and got stuck for a good half hour on that one.

#-o

oh, I'm going to shoot myself after this bluff!!  I was stupidly giddly laughing that I didn't catch this one!  I felt so stupid...lol  Spend about a week with this issue and finally found out why my Dell D520 wasn't working with wireless.

Thanks a _bunch_ for pointing the obvious to me :p  LOL!!  Finally got this 3945abg card to work! yay!!!

---

