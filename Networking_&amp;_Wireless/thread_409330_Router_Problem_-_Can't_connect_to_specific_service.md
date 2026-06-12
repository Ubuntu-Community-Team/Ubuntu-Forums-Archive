---
title: "Router Problem - Can't connect to specific services."
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by SpongeBob SquarePants on 2007-04-14
Evening ladies and gents.

Recently I replaced my speedtouch 330 USB modem with a D-Link Wireless/ADSL router. I don't actually run any networks, nor use the wireless aspect of it, but am more interested in being able to use live distros without all that arsing about installing software etc.

Anyway, at the time I was running Feisty, plugged in the modem, and it all worked just fine. Feisty worked fine (connection wise anyway), as did various live distros. 

At the time however my version of Feisty was a  bit troublesome, so I decided to do a format and reinstall of Edgy. After reinstall I had this problem that only Konqueror would access the net. Firefox would just say it was connecting to the web page, but never actually did. Anyway, I decided to try Dapper (don't ask why, I just did). Same problem. Konqueror seems to work fine, but for whatever reason Firefox won't connect. It just stays in a perpetual state of connecting (although it does time out eventually).

I also noticed that after enabling the basic repos in Synaptic, on trying to load them I get the message.....

"Could not download all repository indexes
 
 The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences".

I suspect it is a network problem of sorts. However, I have no idea where to even start resolving the problem. In a nutshell, some programs that need to access the internet do, and some don't. Konqueror does, Firefox and Synaptic don't, and I have no idea why that is.

Any pointers?


Bob.

---

### Post by TheWizzard on 2007-04-14
can be your dns settings.

go to 
- system settings -> network settings -> domai name system
- are there any domain name servers here?
- if not, try 194.109.104.104 and 194.109.6.66
- save settings and reboot

---

### Post by dbott67 on 2007-04-14
Further to what TheWizzard posted, you can read up on the DNS issue & IPv6 issue here:

[http://ubuntuforums.org/showthread.php?t=323747](http://ubuntuforums.org/showthread.php?t=323747)

post #3 and #5 offer to common solutions to the problem.

-Dave

---

### Post by SpongeBob SquarePants on 2007-04-14
Superb advice Dave and Wizzard. A combination of both approaches got me sorted and things are now running smoothly again. Much obliged to you both :D

---

