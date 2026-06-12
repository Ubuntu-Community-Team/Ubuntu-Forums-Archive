---
title: "When SSID not broadcasting, Ubuntu won't connect to my network"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by novafluxx on 2009-01-20
So I decided to take one small step towards security, and set my router to not broadcast the SSID. Nothing out of the ordinary right?

Last night I turned on my Dell 1318 that I've installed Ubuntu on, and it wasn't connecting. I knew what the issue was, and easily figure out how to have it connect to my network (I think!). Yet I only saw two dots and the circle kept going around and around, never connecting. At one point I waited about 5 minutes.

Is there something special I need to do to connect to a network thats not broadcasting?

Its a Netgear router as well, and when I booted the same computer into Vista, I was able to set it up and connect.

---

### Post by stderr on 2009-01-20
Have you already configured the network in NetworkManager (you would have had to if you had security enabled)?

If not, I would imagine you would need to open up the network config (System -> Preferences -> Network Configuration), click on the wireless tab, then click Add, and enter your SSID, & click OK.

If it was already configured in NM, we could try using the interfaces file... but as you say I'd expect it to work.

---

### Post by novafluxx on 2009-01-20
Thank you for the reply. I've used Ubuntu before when I had my router set to broadcast SSID. So the connection was already setup. I'll try deleting all the connections I have setup, and restart, and then recreate it to see if that works.

---

### Post by novafluxx on 2009-01-20
Anyone have any idea?

---

### Post by 0004tom on 2009-01-20
if your using, 8.10, and using the NetworkManager Applet (default network app), right click on it, in the upper left corner, and it should say "connect to hidden wireless network" tried that?

---

### Post by novafluxx on 2009-01-20
> **0004tom said:**
> if your using, 8.10, and using the NetworkManager Applet (default network app), right click on it, in the upper left corner, and it should say "connect to hidden wireless network" tried that?

Yes I tried that, and selected my network, and it had all the information saved.

---

### Post by PiEp on 2009-02-18
This seems to be a real bug, because I have seen many other posts of users with the same problem.

I am using Linux Mint 6, but it has the same issue. And yes, I have tried every option, including the Connect to Hidden Wireless Network option.

One way to make it work for me is to define the connection manually, then after rebooting when it won't connect, set the connection from Infrastructure to Ad Hoc, try to connect (which it won't), set it back to Infrastructure and... Voila!

BTW, the network I am connecting to is a public WiFi network without encryption, but with a hidden SSID.

Here's hoping this helps some of you while others recognize this as a bug and try to solve it...

---

### Post by novafluxx on 2009-03-10
I ended up just turning on the SSID...oh well...

Not to worried really just wanted to be as secure as possible

---

### Post by m2006h on 2009-09-11
I know this is months later, but I can confirm this behavior as well. With the SSID broadcast, connects fine. When I don't broadcast the SSID, even when I try the "connect to hidden network" it will not connect. Keeps asking for the passphrase.

My solution was the same, broadcast the SSID, but this does suck.

---

### Post by rjhakkesteegt on 2010-02-17
I am using Xubuntu 9.04 on an IBM Thinkpad T30 and my SSID is hidden.

When I connect to Hidden network using Ad-Hoc mode it works fine, but nothing happens when I set it to Infrastructure mode. It is just irritating, because the simple workaround is to manually connect every time I turn on my laptop, but still.

---

### Post by Rytron on 2011-04-03
> **rjhakkesteegt said:**
> I am using Xubuntu 9.04 on an IBM Thinkpad T30 and my SSID is hidden.

When I connect to Hidden network using Ad-Hoc mode it works fine, but nothing happens when I set it to Infrastructure mode. It is just irritating, because the simple workaround is to manually connect every time I turn on my laptop, but still.

Hi rjhakkesteegt. Do you leave [COLOR="Indigo"]Band[/COLOR] and [COLOR="Indigo"]Channel[/COLOR] settings to default when you choose Ad-Hoc?

---

### Post by walt.smith1960 on 2011-04-03
Definitely a bug.  I've not had a problem on several installations 9.04 and later.  On initial setup I do the "connect to hidden wireless network" routine and away we go.  I wonder if this occurs with all routers and adapters?  Some sort of firmware glitch?

---

### Post by nowifi on 2012-02-06
Same problem again, ref: 
[http://ubuntuforums.org/showthread.php?t=1919987](http://ubuntuforums.org/showthread.php?t=1919987)

Can anyone explain why connections to hidden SSID routers fail with some   hardware? and even better provide information to provide a fix?

---

### Post by philinux on 2012-02-06
Please dont cross post. You have a thread for the problem. Since it is 24 hours since your last post it is quite alright to bump it.
[edit] I gave it a bump with a link.
This old thread is now closed. The OP has not posted since 2009.

---

