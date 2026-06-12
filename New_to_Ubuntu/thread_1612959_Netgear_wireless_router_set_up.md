---
title: "Netgear wireless router set up"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by melinda on 2010-11-03
I am sooooo frustrated...just bought a Netgear wireless router from Walmart...called to set it up and Netgear says they don't know how to set it up with Linux even though it should work fine...so I have been trying to figure it out on my own and am stuck!  HelP!!!!!

---

### Post by yeats on 2010-11-03
Have you tried plugging your computer into the router and trying to go to a default IP using a browser?  The most common default would be 192.168.0.1 or 192.168.1.1

---

### Post by melinda on 2010-11-03
I already had Netgear help me set up the router on my laptop which has windows...I am really technically stupid so where exactly do I do to choose the default ip address?

---

### Post by melinda on 2010-11-03
I have experimented and tried right clicking the wireless network icon and "edit connections" but I don't know it that is even the place I need to be...Please help if you know how to do this

---

### Post by yeats on 2010-11-03
Okay.  Are you getting any sort of network connection when you plug an Ethernet cable in when running Ubuntu?  If so, you can right click on the Network Manager icon and select Connection Information (I'm running Ubuntu 10.04 - don't recall if other versions would be different).  Type the Default Route IP into your browser address bar.  Does that bring up the router interface?

---

### Post by melinda on 2010-11-03
There is no connection at all...I am actually running Lucid as well, just haven't changed my info.

---

### Post by yeats on 2010-11-03
Can you boot into Windows and set up the router to be a DHCP server?  (This means it will automatically grant a network connection to any computer that connects to it).

---

### Post by melinda on 2010-11-03
I only have linux on my desktop...the laptop is actually not even mine...Netgear just didn't want to do the setup with me unless it was in Windows...they said that it should be set up correctly and that they didn't know why it would'nt work and that I should "contact" linux for help.  Idiots sell the thing saying it is compatibel right on the package so it should work...

---

### Post by melinda on 2010-11-03
oops "compatible"...anyway everything is disconnectec now so that I could come here and fine help

---

### Post by yeats on 2010-11-03
Can you share what model router this is?

---

### Post by melinda on 2010-11-03
yeah its the WNR2000

---

### Post by sandyd on 2010-11-03
nvm

---

### Post by yeats on 2010-11-03
Okay, I'm looking at the manual at [this link]("http://www.google.com/url?sa=t&source=web&cd=1&sqi=2&ved=0CBgQFjAA&url=http%3A%2F%2Fkb.netgear.com%2Fapp%2Fanswers%2Fdetail%2Fa_id%2F1903&rct=j&q=WNR2000%20manual&ei=IBzSTKfGAoP78AamkoHDDw&usg=AFQjCNH137QK6nQXlQQgR-uZ181b1H8VnA&sig2=Ze8c7j1mB6X5BbzUBDu7mg") (PDF download).  I'm assuming this is what you're working from?

---

### Post by melinda on 2010-11-03
apparently I can't spell when I'm frustrated :)

---

### Post by melinda on 2010-11-03
yes...but its a bit technical toward the end under (manual set up) and i get lost eventually.  I'm not even sure what the problem is.

---

### Post by yeats on 2010-11-03
Okay, so confirm this for me:

1. You have a Windows laptop available.

2. You called Netgear and they "set it up" for you (or walked you through some steps).  If so do you remember what they had you do?

3. You were able to connect to the router using a Windows computer but cannot do so using Ubuntu.

---

### Post by melinda on 2010-11-03
yes, yes, and yes.  I pretty much remember the steps

---

### Post by sandyd on 2010-11-03
> **melinda said:**
> yes...but its a bit technical toward the end under (manual set up) and i get lost eventually.  I'm not even sure what the problem is.

what isp do you have?
and are you using DSL, or Cable internet?

---

### Post by melinda on 2010-11-03
i am sure that there is some really easy answer to all this, but like I said...sometimes I need someone to literally spell it out for me 
(ie: i never considered hitting the "re-fresh" button to see new replies on the forum until my sister told me to, but now that she did I think to myself "duh" why am I such an idiot...get me?)  if i am told how, then I can usually figure it out

---

### Post by melinda on 2010-11-03
high speed dsl through comcast

---

### Post by yeats on 2010-11-03
Can you follow the instructions to reset the router to factory settings (page 39 in the instructions, page 43 of the PDF)?  Then try connecting your desktop computer to the router and see if you can get a network connection?

---

### Post by anewguy on 2010-11-03
Also, please understand that at this setup phase, it is best to hard-wire the PC to the router.  So, even if you can connect using wireless with Windows, for setup use a hard-wired connection.  Things can happen whereby the router is reset, etc., and you can lose the wireless connection during setup.

Next we need to clarify - are you able to hard-wire and use Ubuntu as the Os on the PC that is connected?  If so, you should only need to open Firefox (the browser - no need for network manager at this point unless something has greatly changed).  Once that is up, type the following in as the address:

[http://192.168.1.1](http://192.168.1.1)

It should come up with a login screen to the router.  You need to check your documentation for the router to be sure, but I think Netgear uses admin as the default userid and password as the default password.  This should then get you to the setup screen(s) for the router.

Once you are to the setup screens, what exactly are you trying to set up?

Dave ;)

---

### Post by yeats on 2010-11-03
> **anewguy said:**
> 
Once you are to the setup screens, what exactly are you trying to set up?


I know she'll need to spoof the MAC address:

From the manual:

"Your service provider might only allow one Ethernet MAC address to connect to the Internet, and check for your computer&#8217;s MAC address. If this is the case:
"[...]"
&#8211; Configure your router to spoof your computer&#8217;s MAC address. On the Basic Settings screen in the Router MAC Address section, select &#8220;Use this Computer&#8217;s MAC Address&#8221; and click Apply. Then restart your network in the correct sequence (see &#8220;Basic Setup Checklist&#8221; on page 29)."

---

### Post by anewguy on 2010-11-03
Which ISP is she using that she'll need to do that?  Almost any that I know of now, especially any high speed, allow multiple computers, just a single physical connection (the router/modem acting as the access point).

Just curious ;)

Dave ;)

---

### Post by melinda on 2010-11-03
Ok...so i will try these things but I have to disconnect now to do so...thank you all for your help.  I will let you know what happens.

---

### Post by yeats on 2010-11-03
> Which ISP is she using that she'll need to do that? Almost any that I know of now, especially any high speed, allow multiple computers, just a single physical connection (the router/modem acting as the access point).

Comcast.  She could also contact Comcast and let them know to allow the MAC for the router, but that's an extra phone call ;-)

Melinda - signing off for the night - I'm sure others will jump in to assist like Dave.

---

### Post by anewguy on 2010-11-03
Okay, it's been a a few years ago, but I had Comcast high speed for a couple of years in Illinois.  I had their cable modem, then my wireless router.  Never had to do any MAC spoofing in the router no matter how many computers connected.  Have they changed something?
EDIT:  to expand on the above:  Comcast came out and made sure everything was working starting at their cable modem backward - my router and none of my computers were ever connected.  When they finished and left, I just hooked up my router, hard-wired a laptop to it so I could configure things like encryption and MAC filtering (yeah, I know it can be hacked, but you need a packet sniffer, and I've got to tell you I never had any neighbors smart enough to know more than just turning on the power switch).  After that, all of my computers connected wirelessly to the router, the router to the cable modem, and, well, you get the picture.  Never had to configure anything in the router for MAC spoofing - filtering yes, spoofing no.

Dave ;)


BTW Melinda - I posted in your thread about getting help in general, and as I pointed out there many of us have tons of stuff to learn yet.  I used to do systems programming and systems administration on large scale, then mini and then micro (what we now call "PC's") computers.  Back in the 80's we did some work with Unix, and I had my first exposure to Linux in 1994 or 1995.  I'm still lost on a lot of stuff in Linux yet, as you can note by my latest post, which has to be the dumbest question ever asked on the forum ;)

---

### Post by anewguy on 2010-11-04
I just remembered something that may be of use to you:

If you have the Comcast cable modem with only 1 network port (e.g., it's not a router) and then connect your router, the 192.168.1.1 address should work.

However, if you're like me and the cable modem also has 3 or 4 network ports (e.g., it's a router as well), then the address will probably be 10.0.0.1.  This is because the cable modem/router would probably use the 192.168.1.1 addresss (that's what mine does, and my Netgear wireless router connected to the cable modem/router I have to use 10.0.0.1 to connect to the configuration screen for the Netgear router.

Dave ;)

---

