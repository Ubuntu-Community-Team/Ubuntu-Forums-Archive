---
title: "network problems"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by hexagondun on 2009-01-04
complete noob here

when I go to configure my wifi connection in system>admin>network I change it to wep ascii from wpa personal and everything works fine.  Then, out of nowhere, 3 minutes later it automatically changes itself back to wpa personal and I lose my connection.  It seems simple enough, I don't know what I could possibly be doing wrong.  Any insight would be greatly appreciated, thanks in advance!:D

---

### Post by Captain_tux on 2009-01-04
It seems that the router (or Wireless Access Point) is forcing you to use WPA, which whilst giving you a headache, is actually a good thing... check your router's wireless settings.

You **don't** want to use WEP - its encryption is weak and easily sniffed and hacked.

---

### Post by Vantrax on 2009-01-04
> **Captain_tux said:**
> It seems that the router (or Wireless Access Point) is forcing you to use WPA, which whilst giving you a headache, is actually a good thing... check your router's wireless settings.

You **don't** want to use WEP - its encryption is weak and easily sniffed and hacked.

This is exactly right, it is a major risk to use WEP, it takes someone running an automated tool less than 10 min to have access to your network. The tools are a simple button click that anyone can use.

---

### Post by hexagondun on 2009-01-04
wow, I had no idea.  This would be good, but the internet doesn't seem to want to work with the wpa.  Well, sometimes it will, but it usually seems to fail.  any ideas on how I can fix this?

---

### Post by Captain_tux on 2009-01-04
Different manufacturers have different ways to go about the same thing, but what kind of router are you using? Netgear, Linksys...?

Personally, I have a Netgear WNR3500 that I'm getting ready to return to Best Buy as the N signal keeps cutting out on me.

---

### Post by hexagondun on 2009-01-04
linksys.. thanks for the responses.

---

### Post by hexagondun on 2009-01-04
It seems to be working better now for some reason, Im going ot install some updates and see what happens. still, any input would be great.

---

### Post by Captain_tux on 2009-01-04
Ok.

I'm not too familiar with Linksys' menus, but find your way to your router's Wireless Settings and manually set it to use WPA (with TKIP, AES, etc.)... use a good, strong password (something that won't be easily guessed). You should be able to do that following the instruction manual. If you don't have it, Google for it or go to the manufacturer's website and see if you can download one.

I'm getting tired and gotta get up early, so I'm gonna go before I stop making sense. Give it a shot and if it doesn't work, keep posting and someone here will help.

Buena suerte!

---

### Post by Miljet on 2009-01-04
There should be a file named Users Guide.Ink.pdf on the install disk that came with the router. I copied that file into my Home folder. You can then open it to find out how to access the router and change settings.

---

### Post by Captain_tux on 2009-01-05
Hex -

Any luck?

---

### Post by hexagondun on 2009-01-06
It's quite odd actually.  No luck in completely solving the problem per se, but it has been kicking me much less frequently- so much so that I haven't  been motivated enough to try anything as of yet. At first I was getting booted frequently but at this point it's seldom, It's 5:03 in the morning here and I haven't slept yet, so if I wake tomorrow and things still aren't running perfectly I'll definitely find the linskys user manual online and work with it a bit.  I really appreciate your help guys; this forum has been absolutely great.  If the problems proceed and I fix it I'll be sure to let you know... if not I'm sure I'll be nagging you all for help :D  thanks again    -Hex

---

### Post by Captain_tux on 2009-01-06
One thing that comes to mind after reading your last post is the channel that the signal is being transmitted on. In your router's wireless settings, see if you can change the channel to a middle or upper channel (as opposed to 1 or 2). The problem could be that because the Linksys is so common (like the Netgear), all the signals transmitting in your area are conflicting and cancelling each other out.

Hope things work out for you!

---

### Post by dduehning on 2009-01-06
Hex,

I know this is simple and probably you've already thought of it, but it should be asked anyway... are you using any kind of cordless phone when you're on the computer?  Often times, depending on the phone, it can interfere with your wifi router if they use the same frequency (typically the 2.4ghz phones).  This was a problem for me until I bought a new phone (Dect6.0).

---

