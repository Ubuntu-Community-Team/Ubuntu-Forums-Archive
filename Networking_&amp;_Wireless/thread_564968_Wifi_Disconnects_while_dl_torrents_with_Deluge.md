---
title: "Wifi Disconnects while d/l torrents with Deluge"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by mhenry35 on 2007-10-01
I am having trouble staying connected with Wifi when I'm downloading torrents with Deluge.  I get connected, have a good connection and signal strength, but after around 10-15 minutes, all of a sudden my d/l and u/l speed drops to 0, and if I open a browser and try to navigate to a web page, I can't even get a response from DNS.

I'm using the wifi at Borders, it's a T-Mobile hotspot internet connection.

Some nights everything is fine, but most of the time, I get a connection for a while, then I get dumped.  

The next part of the story is that if I click on the network icon to disconnect and reconnect, sometimes it will, sometimes it won't.

Any ideas on this?  The only way to solve so far is a reboot (that reminds me of Windows too much.)

---

### Post by mhenry35 on 2007-10-19
I think I know what's going on - Do a google search on the phrase "Traffic Shaping".  That would describe what's been happening to me.

Certain ISP's are sending fake TCP/IP Packets with an RST (reset) instruction when the upload speed goes up too high.

Doesn't look like a Linux problem at all.  Although in my case, it does completely knock me off the internet and I have to reboot.

---

### Post by mptpro on 2008-03-10
I have the exact same problem, and this is the first time I seen someone with the same problem.  I thought I was going crazy.

Dell Lappy, Vostro 1500 with Intel 465AGN wifi card.
t-mobile hotspot, always at Starbucks

I am not, however, downloading any torrent or uploading lots of data, so I don't know if "traffic shaping" applies.

My behavior is the same.  I lose connection, but my signal is still connected to the tmobile router, but I can't surf.  Must disconnect, then reconnect.

I have had this problem for over a year and submitted numerous trouble ticket to tmobile, and no one can help.

Also, this is the third lappy this is happening on (all Dells).

thanks for any idea - its good to know I'm not alone!

---

