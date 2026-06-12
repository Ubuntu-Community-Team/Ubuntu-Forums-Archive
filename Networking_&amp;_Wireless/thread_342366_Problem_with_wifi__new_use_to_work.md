---
title: "Problem with wifi  new use to work"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by kent41 on 2007-01-19
When Edgy came out I was so happy that all I had to do to get my DWL-G630 wifi PCMCIA card to work was to go to System> admin> networking and enter my ESSID and Key and I was on the air.

It was that simple it just worked.  For some unknown reason when I tried to bring my wifi up today all looked ok, lites on the card were blinking in the proper sequence but I could not make connection.

I put  my other ( windoz) disk drive in my laptop and had no problems with connection to net.

I next started to look around and found when I ran iwlist all looked ok when I ran  sudo ifup ath0 it looks ok also.

Does anyone have any ideas on what I can check to see why there is no connection to net.

When I try to ping my router I get the message network not available.
[B]
UPDATE
[/B]   Operator error  - key missing one digit  Sorry.

---

### Post by phossal on 2007-01-20
This is a likely case of operator error. I suggest scanning/reviewing your settings to confirm they're as they should be. For example, you might scan your key for a missing digit, or...  :p 

On second thought, this probably calls for a complete re-installation.

---

