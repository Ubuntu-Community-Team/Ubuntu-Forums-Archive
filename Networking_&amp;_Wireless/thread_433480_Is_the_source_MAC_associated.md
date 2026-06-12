---
title: "Is the source MAC associated?"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by mrchrisblau on 2007-05-05
I'm trying to get more IVs to go over the network for various reasons. I run this command:

```
sudo aireplay-ng -3 -b 00:09:5B:E5:F9:6A -h 00:90:96:91:D8:96 ath1
```

and get this result:

```
Saving ARP requests in replay_arp-0504-230853.cap
You should also start airodump-ng to capture replies.
Notice: got a deauth/disassoc packet. Is the source MAC associated ?
Notice: got a deauth/disassoc packet. Is the source MAC associated ?
Read 16545 packets (got 4 ARP requests), sent 5511 packets...

```

My questions are these: 

what is a "deauth/disassoc packet"? 
How do I make my source MAC addr. associated?

Currently my wifi card is running in Monitor mode (as airodump-ng is running).. not sure if this makes a difference.

---

### Post by Floppyjoe on 2007-05-05
> **mrchrisblau said:**
> I'm trying to get more IVs to go over the network for various reasons. I run this command:

```
sudo aireplay-ng -3 -b 00:09:5B:E5:F9:6A -h 00:90:96:91:D8:96 ath1
```

and get this result:

```
Saving ARP requests in replay_arp-0504-230853.cap
You should also start airodump-ng to capture replies.
Notice: got a deauth/disassoc packet. Is the source MAC associated ?
Notice: got a deauth/disassoc packet. Is the source MAC associated ?
Read 16545 packets (got 4 ARP requests), sent 5511 packets...

```

My questions are these: 

what is a "deauth/disassoc packet"? 
How do I make my source MAC addr. associated?

Currently my wifi card is running in Monitor mode (as airodump-ng is running).. not sure if this makes a difference.

Have you had a look at this little guide?
[http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack)

That means that if the AP has Mac Address filtering on(only allowing specific mac addresses to authenticate) then you will not be able to do fake authentication unless you know a valid mac address.

Also if you don't have a valid form of a mac address(ie. the first three sections//00:90:00) then you might get something like that too.

---

