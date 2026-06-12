---
title: "[SOLVED] I'm getting contradicting advice on security. Opinions wanted."
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by BlocknBleed on 2008-01-07
I've visited 2 different websites recently about making a secure wireless network. One site says to do a bunch of stuff and the other says don't bother, its futile. These sites are just the result of a quick google search. No particular reason I chose them.

[http://www.practicallynetworked.com/support/wireless_secure.htm]("http://www.practicallynetworked.com/support/wireless_secure.htm")
This site says to do things like:
Don't broadcast SSID
Use MAC filtering
Reduce WAN transmitting power

And then this site basically refutes most of what seems to me to be good ideas. If nothing else they would be better than nothing wouldn't they?

The Six Dumbest Ways To Secure A Wireless LAN
[http://blogs.zdnet.com/Ou/?p=43]("http://blogs.zdnet.com/Ou/?p=43")

The biggest concern I have is about the MAC filtering because I'm using it right now. I will soon change my passwords to something unguessable and I'm using WPA-AES. I've also got SSID still being broadcast but only to show off my clever network name.:rolleyes:

So is the guy in the second website full of it?
Any advice is appreciated.

---

### Post by kevdog on 2008-01-07
The absolute best way is to use WPA.  WPA2 is a more efficient cipher than WPA1, so hence it should theoretically be faster. 

All the other stuff doesnt matter (unless you just want to stop novices trying to hack your network)

1. ESSID Broadcast -- Even if your ESSID is not broadcast, it can be seen, although additional detection software is necessary
2. MAC cloning - An additional security feature, however MAC addresses can be cloned.  Its ok to use this in conjuction with WPA
3. Turn down Tx power - Yes I guess this is true since it decreases your range, however I found when I do this, Im always dropping my own signal, hence I tend to turn up the Tx power.

---

### Post by Nrbelex on 2008-01-07
If you have no complications from using WPA why *wouldn't* you simply leave it on? Even if it's not completely secure, it will tell potential attackers that they're better off trying the wireless in the house next-door. 

Just my 2¢. :)

~ Brett

---

### Post by BlocknBleed on 2008-01-07
> **Nrbelex said:**
>  Even if it's not completely secure, it will tell potential attackers that they're better off trying the wireless in the house next-door. 


~ Brett

Yeah. One of my neighbors is using WEP. :lolflag: 
I guess its like the old saying. You don't have to outrun the tiger, you just have to outrun the guy beside you.

---

### Post by kevdog on 2008-01-07
> I guess its like the old saying. You don't have to outrun the tiger, you just have to outrun the guy beside you.

Not trying to make light out of it -- but didn't this just happen -- and I mean in a real tiger attack at the zoo involving the 3 (now 2) boys?!

---

### Post by HermanAB on 2008-01-07
Ancient Chinese proverb: "If you have a tiger by the tail and it wants to run away, then you should let it."

---

### Post by madsmaddad on 2008-01-07
There is no such thing as perfect security. There are only levels of insecurity. 

Use WPA, Hidden ESSID, and MAC filtering - all good and will slow down an intruder. 
Also have a good firewall. 
And be careful what you are sharing on the network. 

Then, Unless you are really paranoic, you can relax. 

Madsmaddad.

---

### Post by techstop on 2008-01-07
> **madsmaddad said:**
> There is no such thing as perfect security. There are only levels of insecurity. 

Use WPA, Hidden ESSID, and MAC filtering - all good and will slow down an intruder. 
Also have a good firewall. 
And be careful what you are sharing on the network. 

Then, Unless you are really paranoic, you can relax. 

Madsmaddad.

I know the OP has marked the thread "solved", but I it wasn't in response to the post above as it contains a couple of misconceptions. Hiding the SSID and applying MAC filtering only goes to make your life more difficult, not the attackers.

Here are three simple recommendations for home wireless network security.

1. Use WPA (or upgrade your equipment if it only support WEP) or WPA2 if available.
2. Use a strong, long, random key. (The WPA protocol is cryptographically sound so that successful attacks can more or less only be carried out on strong random keys by brute force, ie trying every possible key. If you make your key long enough and strong enough, an attacker will not have enough hours in the day to guess your key by brute force)
3. Protect your strong, long, random key by not writing it down anywhere that attackers can read it and change it regularly.

If you do the above, then the SSID broadcast disabling and MAC filtering is utterly pointless. If you use WEP, then nothing will save you.

---

### Post by madsmaddad on 2008-01-07
> **techstop said:**
> I know the OP has marked the thread "solved", but I it wasn't in response to the post above as it contains a couple of misconceptions. Hiding the SSID and applying MAC filtering only goes to make your life more difficult, not the attackers.

Here are three simple recommendations for home wireless network security.

1. Use WPA (or upgrade your equipment if it only support WEP) or WPA2 if available.
2. Use a strong, long, random key. (The WPA protocol is cryptographically sound so that successful attacks can more or less only be carried out on strong random keys by brute force, ie trying every possible key. If you make your key long enough and strong enough, an attacker will not have enough hours in the day to guess your key by brute force)
3. Protect your strong, long, random key by not writing it down anywhere that attackers can read it and change it regularly.

If you do the above, then the SSID broadcast disabling and MAC filtering is utterly pointless. If you use WEP, then nothing will save you.

My Response to that:
I support your points to use WPA2, and make the key as long as possible- I think my unit allows 8 to 63 characters (Not verified).  But would you write it down anywhere public? It will get stored with all configuration items for my PC  - securely. And  though changing it periodically is advisable, That is not easy under Ubuntu Gutsy, (or please tell me if it is). 

On the basis that you are only using your wireless connection for a few hours a day, when a bad guy can pick up your communications and attempt to hack them, I recommend  Hidden SSID and MAC Filtering for those times when your PC is not in use, but your wireless network is up.  They do not hinder you once set up, and help to make your network less obvious and less accessible. 

Of course, you should initially consider what you are afraid of - Someone using your bandwidth, or accessing things on your network, or monitoring your transmissions and 'viewing' your data. Depends on the number of Computers on your network too. 

End of my contribution

---

### Post by techstop on 2008-01-07
Why would you recommend steps that don't actually do anything?

1. Hiding the SSID *does not* hide your network.
2. MAC filtering is utterly ineffective.

If you are using WPA / WPA2 with a long random key, then why make your life complicated by adding steps that don't do anything other than to make your life complicated? MAC filtering requires you to obtain the MAC of every legit wireless device on your network and then plug in the values to your wireless AP / router etc. This takes time, but doesn't actually do anything.

I liken it to putting a sign next to the front door of your house "Alarm system in use" but then leaving the front door open and unlocked. Why not just lock the door?

> So there you have it, simple SSID discovery. The old axiom remains true: security by obscurity is no security at all. Hiding an SSID will not hide a wireless network, so ignore any such advice -- and it's amazing how often I continue to see this. By the way, also ignore any advice that says to use MAC address filtering. It's amazingly trivial to spoof the MAC address of an allowed supplicant -- simply sniff the traffic, look at the MAC addresses, and use the neat little SMAC utility to change your MAC to one that's permitted.

[http://blogs.technet.com/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx](http://blogs.technet.com/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx)

---

