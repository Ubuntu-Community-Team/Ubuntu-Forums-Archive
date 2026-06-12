---
title: "EXTREMELY newb...  In need of wireless help."
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by haemphyst on 2007-04-01
OK, I am in LOVE with Ubuntu so far.  It is the first distro of Linux that I felt reached out a hand to rescue me from the sinking ship that we all know as Micro$oft.  I really like it.  I am using Edgy, and after I get this issue worked out, I'll be asking for help with WINE, so be on the lookout... [-o<

I have a Averatec laptop - the 5428HX - AMD 2800+, 1G, 100G, RealTek 10/100, RaLink 2500, (apparently FULLY supported (whew)) modem.  Upon installation, EVERY device is identified, AFAICT.  I even get the wireless indicator at the top right corner.  When I click on it, I get the menu with the name of my router in it, but it'll never connect.  It goes through the little "swirl" when I ask it to connect...  it'll do that for about 40 seconds or so, but never acquire an address for wireless connectivity.

The wireless network is "unsecured".  (The WAP has ALL MAC addresses locked out, except for my two wireless computers - one desktop, one laptop.)  With XP installed it will connect with no issues.  Any suggestions?  The DHCP Server sees the laptop when using the wired connection, and connects perfectly that way.  As I said, with XP the wireless works perfectly as well.

Ubuntu (and Linux in general) Noob, hoping not to be laughed at TOO hard...
-david

---

### Post by Floppyjoe on 2007-04-02
I am assuming you have network-manager installed.
You say you are using edgy?
Can you post the output of :
```
lsmod
```
and
```
dmesg
```

You can open a terminal by clicking on Applications/Accessories/Terminal to enter these commands.

---

### Post by haemphyst on 2007-04-02
I guess I was confused.  I am using 7.04 Feisty Fawn.  I have both images, I guess I burned the later of the two.  Would one of the 6.xx's be easier to configure, then update to Feisty?  And if so, do you recommend 6.04 or 6.10?  I could easily go back to the earlier version, if necessary.  I have NOTHING installed, so reverting would be no effort, other than an install.  I have burned DVDs, now, for both.  6.10 and 7.04...  I didn't know.  :)  6.04LTS? - I would be HAPPY to buy (the DVD)  from Amazon for the $9.95 it costs,  Otherwise I have 6.10 (the system I am on right now is a 6.10 Live DVD).  Now the CD CAN be downloaded, what would I NOT get if I were to download a CD image, vs a DVD image (if I can find it or buy it)?  I would like to be able to have either a purchased or DL'd version, and be able to help as much as I have seen you be/do already...

Under Synaptic Package Manager, EVERY available package is installed. This DOES include:

**Network-Manager, version 0.6.4-6ubuntu2 Network Management Framework Daemon**

Installed and latest are identical versions, so it's the latest.

**::::::EDIT::::::I might also mention, that if I statically assign address and subnet, the server IP's on the other side of the router are seen, but still no internet access...**

Otherwise, below are the outputs you asked for:


** ::::: (EDIT)  output listings yanked by haemphyst in the interest of space, and by virtue of no longer being necessary...  (END EDIT) :::::**

---

### Post by Floppyjoe on 2007-04-02
You have two lsmod outputs shown on your previous post.
I thought maybe you could blacklist a conflicting driver but that does not appear to be the case.
I'm not sure how well it works to get wifi working using a Live CD or DVD because you can't save any changes properly. This is my experience anyway. There may be some other person who knows how to get it working though. 
I myself would stay away from Feisty because it still is in the testing stages and probably still needs a bunch of work.

---

### Post by haemphyst on 2007-04-02
I do, don't I...  I thought I had copied and pasted both...  Do you need both, or should I just not worry about it for right now?  (read on...)

No, the live DVD is on my desktop machine with a wired network connection.  I am having no issues at all there...  The actual install, where I am having issues, is on the laptop with the RaLink wireless card.  I can't remember if I have ever used the 6.xx version(s) on the laptop, I guess I went right to the 7.04.

As far as avoiding the 7.04, that's what I was wondering.  Like I said, I have a 6.10 DVD all burned, and I can easily install that.  I'll do so, and get back with the forum!  THANKS!!!

--david

---

### Post by sabi on 2007-04-02
Well, we need to find out what version of Ubuntu you have installed on your laptop.

Try this, click on the Firefox icon in the upper left section of the menu bar at the top. The resulting page will identify your installed version. (Welcome to ..l..)

---

### Post by haemphyst on 2007-04-03
Hi kids!  Waxed the 7.04 (Feisty) install, and put 6.10 (Edgy) back on!  WiFi works like a champ now!  (Once i rermember to actually turn it ON  :)  )  So, 7.04 - still buggy with RaLink wireless cards...  6.10 - not so much!  I'm getting happier with Ubuntu all the time.

Next, I tackle WINE...  Suggestions from anybody?  Anything i need to keep in mind?

---

