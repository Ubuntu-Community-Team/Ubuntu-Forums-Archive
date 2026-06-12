---
title: "Nortel Contivity VPN connectivity"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by hickninja on 2007-01-31
I noticed that Novell has support for Nortel Contivity VPN access through a Network Manager plugin[1], but I have not seen it in any other distro, including Ubuntu. Is it Free Software? I'm using Edgy now, and I'm in the ironic situation of using Linux at work and Windows at home because I can't VPN in with Ubuntu.

My question is: is there any way to use the NetworkManager-novellvpn package in Ubuntu? If not, is it planned to add support for the Nortel Contivity VPN to Ubuntu at some point, possibly by leveraging the code from Novell? I noticed on the forums some other posts about people wanting this.

Thanks!

[1] - [http://www.novell.com/coolsolutions/feature/18321.html]("http://www.novell.com/coolsolutions/feature/18321.html")

---

### Post by Subabooba on 2007-02-18
I'd be very interested to hear if you found anything out about this?

Being able to do this is about the last thing holding me back from blowing windows away all together.

I'd always assumed I could use any VPN app, hadn't tried any in Ubuntu yet, but from your post I take it if work is setup to use the Nortel app, you have to use it?

---

### Post by Tridion2000 on 2007-04-12
This is also the one thing holding me back from getting rid of Windows. Is there any news on a Contivity client for Ubuntu?

---

### Post by gcostanzo on 2007-04-21
Hopefully the Contivity IPSec VPN client will soon come to apt-get but for now try using the Contivity SSL VPN client (this does have to be enabled by your Contivity administrator)

---

### Post by haxor999 on 2007-05-13
Support for Nortel Contivity is being added to the vpnc client. Right now you have to manually checkout the sources and build it. Also it doesn't seem to work for everyone yet (myself included). For more info see: [http://ubuntuforums.org/showthread.php?t=441042]("http://ubuntuforums.org/showthread.php?t=441042")

I also came across the SuSE client via searching Google, but can find only the one meager link to it that you have posted above - seems it's probably only for paying customers and not included in the free distribution. What do you mean with "Contivity SSL VPN client" mentioned above? I don't find any references to it on Google.

---

### Post by Astro96 on 2007-06-09
I am also very interested in seeing this client (preferably added to network manager).  Are there any plans to implement this?

---

