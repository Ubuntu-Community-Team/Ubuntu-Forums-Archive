---
title: "[SOLVED] Internet suddenly stops working (but works on Windows XP)"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by argie on 2007-09-05
I have one wireless router and two computers behind it. I get to the internet through that router. It's been working fine without any interference from me for about a week now. Today I was just browsing digg and flickr and suddenly all pages stop loading with firefox stuck at showing 'Looking up blahblah.com...' . This is a dual-boot and when I booted into Windows XP, I can access the internet (that's how I'm typing this) though the 'Looking up' part takes much longer than usual. It's still only 1-2 seconds but previously I wouldn't even be able to see that showing in the bar.

Curiously, I can't ping the DNS servers that are set in the connection settings in Windows XP (they were provided by the ISP, the IPs are 203.145.184.42 and 203.145.184.32). In Ubuntu, I never had to set the DNS servers, my wireless is on 'Roaming Mode', I connected to my home wireless network, entered my WEP key and it all just automagically worked. Anyone know why it stopped all of a sudden? 

My ISP doesn't do support for Linux either, and if it works somewhat on Windows XP they'll declare that 'it works' so I won't get any help from there.

In addition, the wireless router is connected to a DSL line. 
The wireless part is working, I can ping the router and share files. 
If I try to enter the DNS settings manually in the Network program (network-admin, I think) those settings disappear as soon as I connect.
If I turn off 'Roaming Mode' and set all the settings manually in the Network program I have no connection whatsoever.
When I do the above and then try to recover by setting all the settings back to what they were, nothing happens.
Sometimes a 'changing interface something' dialog box comes up and then there's a change but I can't seem to figure out how to make this box appear.
I haven't installed any updates in the past few days and I was neither downloading anything in the background nor running P2P software when this funny business started.

Thanks for reading.

Update: I can access websites from Ubuntu if I type in the IP address. Does this mean the DNS servers are the problem? How does Windows get around this? (just questions, I'm curious)
Update: It suddenly started working. And now there's this animation in the panel applet while it connects to the network. Previously that was never there, it would just show 0% signal. Ah well. Weird. Thanks! :)

---

### Post by noob12 on 2007-09-05
It sounds to me like a DNS issue with flaky DNS service from your ISP.  

The difference may be explained by caching of addresses under XP, which could be masking the flakiness of the ISP's servers.

Here's a HOWTO with some pointers I recently posted to get around this: [http://ubuntuforums.org/showthread.php?p=3314484](http://ubuntuforums.org/showthread.php?p=3314484)

---

### Post by argie on 2007-09-09
> **noob12 said:**
> It sounds to me like a DNS issue with flaky DNS service from your ISP.  

The difference may be explained by caching of addresses under XP, which could be masking the flakiness of the ISP's servers.

Here's a HOWTO with some pointers I recently posted to get around this: [http://ubuntuforums.org/showthread.php?p=3314484](http://ubuntuforums.org/showthread.php?p=3314484)

Thanks lots! That local cache tip in the other thread is precisely what I'd be happy with (the OpenDNS servers are some 200-300ms away).

---

