---
title: "[resolved] Unable to connect through Gaim, X-Chat.."
date: 2004-11-18
forum: Networking &amp; Wireless
---

### Post by dataw0lf on 2004-11-18
Hey guys.  I seem to be having a problem connecting through Gaim and X-Chat.  On Gaim, I am unable to connect to the AIM network, yet MSN and Jabber both work.  X-Chat is unable to connect as well.  Both timeout on me.  I've checked my dsl modem and NAT settings, they are fine.  Any ideas?
dataw0lf

---

### Post by jdong on 2004-11-18
these really sound like networking issues. Can you ping login.oscar.aol.com? Can you connect to AIM's network with telnet? Try: telnet  login.oscar.aol.com 5190

---

### Post by dataw0lf on 2004-11-18
Very strange... I tried pinging login.oscar.aol.com earlier, it didn't work.  However, I went into prefs.xml in .gaim from my home directory, and changed some port ranges they had in there.  When I went back out, I had read your post, so for giggles I tried pinging them again.. voila!  ?!?!?!  I logged into AIM with ease.  Very, very strange indeed... X-Chat works now too.  I'm attributing this to coincidence, of course, but still.... weird.
dataw0lf

---

### Post by jdong on 2004-11-19
*very* strange!

---

### Post by dataw0lf on 2004-11-19
I've been trying to troubleshoot the problem.  My boss has the same modem (Actiontec 701) and he mentioned that Linux, when setup as DHCP from it, will set the primary DNS as the actual modem, and the ISP's DNS as the secondary.. this could be part of the problem.  But, just an update, now, when I login, I have to ping and telnet to the AOL login server before AIM will work.  IE, when I login GAIM will sit, apparently trying to resolve it on 'Connecting' and timeout after a while.  But once I grab a shell and issue a ping login.oscar.aol.com and a telnet login.oscar.aol.com 5190, and try to login again through AIM, it pops right up.  I'm going to see if changing the port that GAIM connects to login.oscar.aol.com works when I get home.  But I'm still weirded out by the whole business.  ](*,) 
dataw0lf

---

### Post by costoa on 2004-11-19
[QUOTE=dataw0lf]... But, just an update, now, when I login, I have to ping and telnet to the AOL login server before AIM will work.  IE, when I login GAIM will sit, apparently trying to resolve it on 'Connecting' and timeout after a while.  But once I grab a shell and issue a ping login.oscar.aol.com and a telnet login.oscar.aol.com 5190, and try to login again through AIM, it pops right up.  I'm going to see if changing the port that GAIM connects to login.oscar.aol.com works when I get home.  But I'm still weirded out by the whole business.  ](*,) 
dataw0lf[/QUOTE]

Could there be a inactivity time out setting on the dsl modem or a very short lease life on the dhcp address? Either one could account for this problem. If that's the case then a cron job sending a single packet ping somewhere (like two hops upstream) every  10 or 20 minutes might fix it.

---

### Post by billputer on 2005-01-08
I had the same problem with the same modem, but when I took the ip of my modem off the dns list everything worked perfectly.

---

