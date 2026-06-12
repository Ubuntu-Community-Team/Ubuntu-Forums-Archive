---
title: "[SOLVED] Ubuntu freezes when connecting to WEP wireless network"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by foo fah on 2008-02-17
I apologize if this has been addressed elsewhere, but after extensive searching, I haven't been able to find any solutions to my issue.

I just installed 7.10 on my Dell Latitude 610 laptop this weekend (I'm a total noob, by the way), and - to make a long story short - my only problem right now is getting my wireless internet card to work.

Everything works perfectly if I turn off encryption in my wireless router. However, if I turn on the WEP encryption that our household has been using (and that I used the same wireless card with previously), then when I enter the HEX code to connect, everything freezes. No mouse, no keyboard...the caps lock light blinks, and I have to do a hard reboot.

I tried changing the wireless router's encryption to WPA, but it looks like the wireless card only supports WEP. I'm considering just trying a new wireless card, but in the meantime, I'd love to hear if anyone had any ideas as to how to fix this, as I feel like I'm so close to successfully replacing Windows!

Any suggestions would be greatly appreciated! Thanks.

---

### Post by jhetrick62 on 2008-02-17
Just a guess, but it may be the network manager daemon.  It has many issues.  Install wifi-radar and try that to see if that makes any difference.  Log onto the network with that application.  You will find manual if you google wifi-radar, it's pretty straightforward.

sudo apt-get install wifi-radar

Jeff

---

### Post by wrongdave on 2008-02-18
I had a similar problem on my laptop (not a Dell). I solved it by getting another card. Here is my post describing what I did
[http://ubuntuforums.org/showthread.php?t=700472]("http://ubuntuforums.org/showthread.php?t=700472")

---

### Post by foo fah on 2008-02-18
Thanks very much for the wifi-radar suggestion, Jeff, although unfortunately it doesn't look like it fixes my issue.

wrongdave - that all sounds VERY familiar. I'm glad to hear the new card worked for you! I've been starting to feel pretty strongly that that's what I need to try next, and reading your post makes me feel that much more ready to give it a go. I'll post my results - thanks very much for the reply.

---

### Post by foo fah on 2008-02-20
Success! Replaced my laptop's wireless adapter card with the D-Link WNA-2330. Works like a charm with WEP, as well as with WPA! Network Manager found it out of the box. A few minor quirks, but nothing a re-boot didn't resolve. Smooth sailing....[This list]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") turned out to be very helpful in picking out a card.

Cheers!

---

