---
title: "Wifi Slows,then stops,then SOMETIMES restarts"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by SlackLagg on 2006-09-22
I am having some problems on my new install of Ubuntu. My network card (Dlink WDA-2320, which uses the Atheros chipset apparently) is detected and with a quick entry of my network stats into the Ubuntu Network Settings , I was up and running. Awesome. 

Unfortunately, I have a problem when it comes to downloading files. The file will download at a good speed (I'm stuck at 30kbs, so anything over 20 kps is "good") for approx. 30 seconds to a minute, then the the connection speed will slow down, and eventually stop. Sometimes it will restart within 10 seconds, sometimes within 30 seconds, sometimes within 5 minutes or sometimes it just flat out stops. This happends with Firefox, Synaptic and Wget, however I've noticed that if I continue surfing the web, and clicking links, that downloads will continue to download normally like in Windows. 

I haven't done anything to this installation of Ubuntu so I'm really my head about this one. Any savvy folks care to drop some advice on this issue? 

Thank you for your time

---

### Post by sharkcohen on 2006-09-22
How is your link quality?  I was having some random slowdown/disconnect issues, and after some walking around the house I found my refridgerator compressor was running during these times.  I horizontally polarized my antennas, which nearly doubled the link quality and seems to have resolved interference from the fridge.

---

### Post by SlackLagg on 2006-09-23
Yes, at first, I thought link quality had something to do with it as well, but my connection is fine in Windows (three out of 4 bars if that means anything)

---

### Post by sharkcohen on 2006-09-23
The next time it happens, do a dmesg.  Look to see if you have a message that says something like "ath0: ath_chan_set: unable to reset channel 12 (2467Mhz) hal status 3".  If so, try:

modprobe ath_pci xchanmode=0

And then:

ifdown ath0
ifup ath0

See if that helps.  I'm trying this out myself right now.  In my case, the message referenced channel 6, the channel I am using.

[http://madwifi.org/wiki/UserDocs/Troubleshooting#Mylogssayath0:ath_chan_set:unabletoresetchannel122467Mhzhalstatus3andnothingworkswhatcanIdo](http://madwifi.org/wiki/UserDocs/Troubleshooting#Mylogssayath0:ath_chan_set:unabletoresetchannel122467Mhzhalstatus3andnothingworkswhatcanIdo)

---

### Post by happy-and-lost on 2006-09-23
I had that problem once. The only solution I found was to reinstall Ubuntu.

---

### Post by sharkcohen on 2006-09-23
LOL, don't say that.  I refuse to reinstall, everything is fixable.

---

### Post by happy-and-lost on 2006-09-23
Which driver is it using?

You can find out by going... System-->Administration-->Device Manager--->[Card Name]--->Advanced and it's next to "info.linux.driver"

---

### Post by sharkcohen on 2006-09-23
I'm using madwifi, I can only assume the thread starter is, as well.

---

### Post by happy-and-lost on 2006-09-23
```
sudo apt-get install hostapd
``` *may* be the solution

---

### Post by SlackLagg on 2006-09-23
Okay all, false alarm. 

Sorry about that folks :oops: 

I forgot that the interface for my router is very picky. It only works in IE. (bad coding on Dlink's part I must say). Earlier this week (before I installed Ubuntu) I had tried to do something on the router, but it was after I had already tried to change the setting ,I remembered "wait, I should have done that in IE , it doens't like FireFox" , but then I got distracted and forgot to do the change in IE.

I remebered this last night after I had tried to download something using Windows and the same problem that has been plaguing me all week in Ubuntu  occurred. After doing a :-s  :confused:  :|  :idea:  process, I remembered what I had done earlier in the week, and then performed the router setting change in IE like I should have done in the first place.  

Thank you for your time. Sorry about this. Feel free to delete this entire thread.

---

### Post by sharkcohen on 2006-09-27
Just to add to the thread for those who might be searching in the future, it seems my difficulty with my connection dropping was from attempting to use the 'Turbo G' mode on my Netgear WG311T.  I've disabled it on my card as well as on the access point (Netgear WGT624) and my wireless has since been stable.

---

### Post by showty on 2007-04-20
How do you disable said 'Turbo G' mode on the card? I am suffering the same problem.

---

