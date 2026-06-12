---
title: "Wireless works until logging off / restarting"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by smorris on 2007-10-27
I can access the internet after logging in, system>>network, changing the security to WPA2, reentering password. If I log out, settings seem to be lost. Any ideas? This is the behaviour on two different ubuntu 7.10 installs, One is a laptop with inrel PRO/set and the other is a desktop with netgear wireless PCI.

---

### Post by smorris on 2007-10-27
To be clear: the wireless works great, just does not work after restarting or logging off. Help!

---

### Post by smorris on 2007-10-27
Hey, folks, if this is obvious, can someone just post a link? I did not see anything that addressed this specifically in the stickys. Thanks.

---

### Post by smorris on 2007-10-27
Hey, someone here? Pretty straightforward question.

---

### Post by Tonohono on 2007-10-28
Bump for great justice!
And because my wireless problem seems similar.

If I set my router to use WPA (AES), Gutsy has no problem connectic via manual configuration in the Network Manager. During the same session, I can configure my router to use WPA2 (AES) and configure my connection in the Network Manager to follow suit. All is well.

Until...
I restart. 
Upon restarting, the Network Manager reverts to WPA, and my wireless connection is lost. Changing this setting back to WPA2 has no effect. I must once again set my router to use WPA, connect, set it to WPA2, reconnect... Only to repeat the process upon next boot.

I should also note, once setting the wireless to use WPA2, subsequent opening of the configuration interface shows reverts the drop-down box to WPA.

Unless I'm mistaken, this seems like and issue with the Network Manager, and not my wireless card (ipw3945) or router (Linksys WRT54GL). I imagine it's possible to manually configure my wireless connection without the Network Manager, though I'm unsure as how to proceed. Some enlightenment would be much appreciated!

---

### Post by dogafro on 2008-06-21
Having the same problem in Hardy. Every time I reboot it goes crazy trying to connect with WPA. I have to go reconfigure the network to use WPA2 manually. Any ideas? :confused:

---

### Post by fiddledeedee on 2008-07-10
Any solutions yet? I've had the same problem for a while now.  It is absolutely annoying to have to manually re-enter my wpa2 network key each time my laptop reboots.

---

### Post by Le-Froid on 2008-07-10
Same thing (sort of) with me..I configure ndiswrapper and set everything up, and when shutting off / restarting I have to do it all over again :s

---

### Post by vineas on 2008-07-13
Same here ... looks to be a common problem.  I was just searching around the forums for an answer to this issue.

---

