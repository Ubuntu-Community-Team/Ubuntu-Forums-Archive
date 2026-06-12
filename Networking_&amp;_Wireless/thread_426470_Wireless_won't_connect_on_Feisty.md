---
title: "Wireless won't connect on Feisty"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by Chonnawonga on 2007-04-28
Apologies for adding another thread to the growing pile of wireless issues, but after a few hours of trawling the forums, I can't find a solution, so I have to ask for help now.

I'm trying to connect with a Netgear WG511. I had no problems with Edgy: everything worked out of the box. After doing a clean install of Feisty (for various reasons I won't go into here) wired connections are fine, but I can't connect to wireless.

Network-manager can see networks, and when I try to connect to my router, it asks for my WEP key. I plug that in, and it goes on trying to connect. Eventually it gives up and asks again.

Other threads have reports of success with WICD, so I uninstalled network-manager and installed WICD instead. I get the same results, though: it sees the network, starts connecting, but gets stuck on "Obtaining an IP address". If I didn't know better, I'd think I was entering the wrong security key.

As I said, I've searched in vain for a solution. Does anyone have any ideas?

---

### Post by shuttleworthwannabe on 2007-04-28
I have the same problem and I have not been able to resolve it either. It seems that Feisty has broken wireless somewhere; it seems like a hit and miss for some. Here is my [thread ]("http://ubuntuforums.org/showthread.php?t=425422")(same card WG511). In fact I have problem connecting with the built in wireless adpater in my laptop.

if you come right let me know how,

Thanks

---

### Post by Chonnawonga on 2007-04-28
**bump**

Anyboy?

---

### Post by wkwork on 2007-04-28
I've had the same problem with my Linksys WPC54G. I loaded the Windows drivers with Linuxant's DriverLoader and I can see all the networks in the area including mine which has no security at all enabled (for test purposes). I try and connect and it just swirls and swirls - nothing.

---

### Post by mr_economy on 2007-04-28
I'm having the same problem with a Linksys WMP54GS.  Installed FF earlier today and had working wireless Internet for a good 6-8 hours, then all of a sudden it just stopped connecting, with all the same symptoms listed here.  I tried everything from bringing the card down and back up, to completely reinstalling Network Manager, to even formatting and doing a perfectly clean install - still same problem.  Boot into my Windows XP partition and I have a perfect connection.  Frustrating, I tell ya.

---

### Post by wkwork on 2007-05-01
Looks like no one's got a solution on this one. Is there another PCMCIA NIC that we know works 100% of the time?

---

### Post by Sensei_V on 2007-05-01
I had this very same problem.  The NetworkManager applet would swirl and swirl.  Then randomly, on one attempt, I was asked to supply a password to create a keyring called "default".  I did as asked and I was connected to my wireless router.

I tried to recreate this scenario and found that if I first created a keyring called "default" in the Keyring Manager, the NM-applet was much more likely to request access to the keyring.  Adding the key to the keyring was not guaranteed, and I had to try multiple times, either logging out or disabling wireless between attempts.

I had to do this for each user account.  I think what must be going on is NetworkManager needs access to the password more than just at the time you enter it.  By allowing the password into the default keyring and giving NM access to the keyring, you can get full wireless encryption support.  I wish there were a checkbox on the wireless login window asking you if you want to add the password to the keyring.

Please reply as to whether this helps.  I've tested it two or three times on my machine and decided to quit while I was ahead and not break it again, but I haven't had any confirmation on the forums as to whether this works for others.

---

### Post by Indigo7 on 2007-05-01
I guess I'll join the club too! I have a D-Link DWL-G650 that was rock-solid in Edgy. I thought that my upgrade to Feisty didn't go well when I couldn't connect to wi-fi. I did a clean install and have the same  issue. I've used wifi radar with some success, but I constantly need to manually reconnect.

---

### Post by wkwork on 2007-05-02
Well I went out and got a new NIC (NOT a bleeping Broadcom chipset) that connected right out of the box. I'll post the model type when I get home.

My wireless router crapped out on me and I picked up a new router too and discovered that as long as my wireless network is completely open - no security at all, broadcasting to the world - I could connect every time. But as soon as I even stop broadcasting the SSID, it wouldn't connect. Not to mention any WEP or WPA.

So I left the network completely open and just specified the MAC addresses of my home machines in the router config so only they can connect to it and that did it. I figure hard coding the MAC adresses is good enough security for a simple home network. I'm not touching the wireless settings in Linux again. :)

Not a solution, but a workaround...

---

### Post by Chonnawonga on 2007-05-02
Well, this seems to be a major problem on Feisty for people with wireless networking cards of all kinds. I have to say, it's pretty sad. I've been doing a lot of reading on the forums about this, and seen it suggested that the problem is linked to a kernel issue, although with all the people out there reporting (and sometimes solving) different problems, it's hard to tell what issue is where, and which issues are related to The Big Wireless Problem, and which aren't.

To anyone experiencing problems, I suggest completely uninstalling network-manager and replacing it with Wicd: this didn't work for me, but lots of folks have reported success with it.

For me, the options seem to be
1. Downgrade to Edgy (damn)
2. Shell out precious cash for a compatible wireless card (also damn)

As for option 2, I look forward to hearing what make and model you got working, wkwork.

---

### Post by wkwork on 2007-05-02
The card I got is a [Netgear WPN511]("http://castle.pricewatch.com/s/search.asp?s=netgear+wpn511"). It cost more than [my wireless router]("http://castle.pricewatch.com/s/search.asp?s=belkin+F5D7231-4") but it's the only one I saw that said it came with Linux drivers (which I didn't need to install) and as soon as I slapped it in and booted up, it worked like a charm on my Dell Inspiron 5100.

Hope that helps. :)

---

### Post by JakeSpeare on 2007-05-02
I have this problem on two laptops.  One is a Sony with an atheros chipset.  The other an averatec with an RT2500.  Neither works!  Both worked OOB in Edgy.  Very frustrating.  Any tips to solving the problem would be huuuuuuuuuuugely appreciated!

---

### Post by briangig on 2007-05-03
the intel 2200 802.11b card was working fine in my t40 thinkpad, but i just upgraded it to a rt2500 based card...had no idea there was problems with them.  Got it working using the workaround posted here::


[http://ubuntuforums.org/showthread.php?t=420136&highlight=rt2500](http://ubuntuforums.org/showthread.php?t=420136&highlight=rt2500)


of course I have to do this every time I reboot, or run it as a script on startup, but I expect the problem to be fixed soon...hopefully.

---

### Post by Chonnawonga on 2007-05-03
I was on the verge of downgrading--I had literally booted up from the 6.10 CD--when I came across [this post]("http://ubuntuforums.org/showpost.php?p=2585938&postcount=19") which solved all my problems. I am thrilled.

The linked post is directly applicable only to those using the Netgear WG511 v1 card, but the principles are likely the same for similar problems.

To anyone experiencing wireless problems on Feisty (and I know there are many) I would definitely recommend the following:

1. Remove network-manager using Synaptic Package Manager.
2. Download and install Wicd (hopefully you have the means).
3. If it still doesn't work, disable your default drivers, download the Windoze ones, and run them using ndiswrapper.

Good luck!

---

