---
title: "Problems with (wired) connection through Belkin router"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by Veracon on 2007-03-24
Hi all,

I've recently set up a wireless home network using a Belkin 802.11g router. I have a laptop running through it wirelessly (not running Ubuntu) as well as a desktop computer dual-booting Windows XP and Ubuntu, connected to the router through the "old-style" Ethernet port (wired). 

Now, it all works perfectly in Windows XP; it's speedy and works like you'd expect it to. However, under Ubuntu (remember, on the same computer), it's EXTREMELY slow. An HTTP request may take up to a minute to complete. I can confirm it isn't a DNS problem since it doesn't work with connecting directly to IPs either.

Inside the router configuration web interface (the router's at 192.168.2.1), I can see that the computer isn't listed in the DHCP client list, even though I've told it to use DHCP. I'm really baffled as to why this is the case, and I have a feeling it's related to my problem.

Further information: I'm actually running through two routers; one supplies Internet through a broadband connection, and this is connected as a modem to the other (Belkin) router. However, I'm fairly certain the "Internet router" (a ZyXEL Prestige one) isn't the problem, since it works just fine through a regular switch - just not through the Belkin router.

Anyone have the slightest idea what could be wrong? I'd greatly appreciate any assistance.

Thanks in advance!

---

### Post by insane_alien on 2007-03-24
disabled IPv6 yet? that slows everything down just now since almost nowhere in the internet is IPv6 enabled yet. although when its mainstream everything would work peachy. roll on that day.

---

### Post by Veracon on 2007-03-24
Do you mean within Ubuntu or in the router settings? If the former, where would I do that? If the latter, I'll try to find a setting; however I somewhat doubt this is the problem, seeing how I can get it working perfectly both within Windows XP and Vista (on the laptop).

---

### Post by Veracon on 2007-03-24
I found a guide on disabling it within Ubuntu, yet I don't see a difference at all.

By the way, to further elaborate on the problem, it appears to be fast as ever once a connection has been established; then, however, when that connection is terminated (typically within a minute) it's slow again. And, like I said, it never appears to appear in the DHCP client list.

---

### Post by Veracon on 2007-03-25
I hate to triple post, but I'm really getting quite desperate. If anyone has the slightest clue on this, please do post.

Again, thanks.

---

### Post by HereInOz on 2007-03-25
What happens if you leave your Belkin router happily handling the wireless traffic only , then connect the Belkin and the desktop through the switch to the ZyXEL?

That would be my first step.   Any improvement.  If so, can you leave it like that?

---

### Post by Veracon on 2007-03-25
I wish I could do that, however the ZyXEL router only has one LAN port to which I connect the Belkin router directly. I only know it works with a switch because I used one prior to setting up the wireless network.

On second thought, maybe I could plug in a siwtch and then use one of the switch' ports for the Belkin router. I'll go ahead and try that. (Edit: Oh, that's what you meant! :))

---

### Post by SactoBob on 2007-03-25
I am not sure, but I think that you are running a similar setup to mine, which works perfectly.  I run a DSL line into a DSL modem which feeds into my Belkin Pre-N wireless router.  The Belkin router has four wired ethernet outlets, one of which is connected by cable to my main computer.  The other computers connect wirelessly.

It sounds like your setup works fine on windows, and intermittently fine on Ubuntu (Edgy like me?)  You say that your wired computer does not show up on the DCHP client list when you check the Belkin  router - it should (you know that you have to "refresh" that client list in the Belkin firmware?)

I think that the above pretty much eliminates any type of hardware problem, so I would carefully check your Ubuntu setup.

Which network manager are you running, and how is it set up.
Is there a chance that you have a wireless card in that computer and that Ubuntu is confused about whether to connect by wire or wirelessly?  Remove any wireless card, at least temporarily.  What does ifconfig report, heck even check iwconfig.

How did you set up your wired connection, or did you just leave the default.  If you set it up yourself, I would suspect an error there.  You might also try to boot with a live CD and see if that works, which would confirm some sort of setup error.

What does lsmod and lspci report for your board.  Is it possible that you have a board with flaky support?  What if you plug that wire into another computer running Ubuntu?  That might give you some info.  Are you sure that the connection is running SLOWLY when it is off, rather than running ok but just connecting intermittently.  I once had a connection that appeared slow, but it was just ndiswrapper with a flaky driver that could not maintain a wireless connection.  I think that you are correct that if the computer is missing from the DCHP client list, and is set for DCHP, that it is the problem.  That is not a poor or slow connection, but no connection at all.

During the brief times when the connection is functioning, can you see it on the DCHP client list?  You might try installing network-manager-gnome, which might give you some more info on what your computer is doing  trying to connect.

---

### Post by Veracon on 2007-03-25
Alright, I'll try to answer some of those questions.

First, here's a somewhat pathetic attempt at illustrating my setup (the wired computer [with === as a symbol of the connection] is dual-booting Ubuntu and Windows):
```
			     Internet
				||
				\/
			       ZyXEL
				||
"PLinux" (Ubuntu Edgy)	====\	\/
"Pavilion" (Windows XP) ====/ Belkin <---- "Aspire" (Windows Vista, wireless)
```

The two Windows boots work absolutely flawlessly. They register and show up in the DHCP client list. I have tried refreshing it several times. Assigned IPs are set to have an infinite lifetime, hence Aspire and Pavilion (the two Windows boots) always show up there. PLinux never has.

I'm certain there's no wireless card; the computer is relatively old, and I'm sure I would've noticed (and used) it if there was one. There's only a plain old Ethernet 100 Mbit card. I'm not sure which network manager I'm using (?), I just told it to use DHCP on eth0 via Administration => Network. Apart from this, I haven't changed anything in the settings.

Also, quite importantly, I've tried this on two wired computers, one of which died recently. Here I had the same problem under Ubuntu (never tried it under Windows), though only after switching from a switch (no pun intended) to the Belkin router.

I'll try the things you told me to, hang on.

(Though, currently, I think using a switch is my best bet. Now if only I can find it!)

E: Okay, found the switch. I'm setting it up now; the wireless still definitely works.
E2: **Yep, this appears to be the solution!** It's now snappy as ever. Of course I'm still interested as to why the problem exists with the Belkin.

---

### Post by SactoBob on 2007-03-25
One more thought -
Could this be a problem with the Belkin's MAC address filtering?
I think that the Belkin Wireless unit has a number of security settings.
One of them is MAC address filtering.  If you had that operating, it might keep kicking you off the connection.

Why don't you save your current Belkin profile to a file you can later restore, and temporarily reset the Belkin to factory defaults.  Alternately, you could carefully go over your Belkin's security settings      - something could be wrong there either with encryption, MAC address filtering, WEP or WPA keys (e.g. mismatch of WPA encryption).

Bob

---

### Post by SactoBob on 2007-03-25
One more thing to check would be the security log of your router.
That will give a record of whether you were trying to connect to your machine, and the result.

---

### Post by zba78 on 2007-04-16
The answer to your problem is to make sure that the DNS servers at the top of you /etc/resolve.conf file are something other the the belkin router's one (I have the same problem)

the easiest way to do this is to use openDNS by following the instructions at [http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)

Of course, if you don't want to use openDNS's DNS server then just replace the IP addresses on the line that says ```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
``` with the IP addresses that your ISP uses

---

