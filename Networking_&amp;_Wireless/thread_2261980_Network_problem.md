---
title: "Network problem"
date: 2015-01-22
forum: Networking &amp; Wireless
---

### Post by Robert_Victor on 2015-01-22
Hello everyone, let me start by thanking anyone and everyone for any help.  I have just installed my first Linux OS (Ubuntu 14.04) and am having some networking issues.  I am able to connect to multiple wireless networks (home and hotspot through my phone), with ease, but when attempting to connect to my work wireless the connection simply times out and give me the message that I have been disconnected.  When I boot into Windows it connects just fine so I am sure that it is a relatively simple setting or some step that I am missing that is nunique to this OS.  

  For a little backgroud, I work in a hospital that has a guest/visitor wireless that has open access.  No username or password is needed but upon opening a browser you are automatically redirected to an authentication page which has you click on a user agreement before full access is granted.  In Windows the connection will show as limited until this is done.  With Ubuntu it won't even get to this point.  I have tried browsing while it is connecting in an attempt to get the authentication page to load but no dice.  I have attached screen shots to an ODT file file regarding some of the settings in Windows in the hope that it may help.  If there is any other info that I could include just let me know & I will get it.  Again thanks for any help, this newb appreciates it.  

[ATTACH]259421[/ATTACH]

---

### Post by steeldriver on 2015-01-22
Hello and welcome to the forums

Have you tried a different browser (Chromium for example)? those kinds of "captive portal" authentications rely on browser capabilities, I think

---

### Post by chili555 on 2015-01-22
Please notice that neither of these questions resulted in a satisfactory answer:  [http://askubuntu.com/questions/65001/how-to-connect-wirelessly-in-a-cafe-with-11-04/302083#302083](http://askubuntu.com/questions/65001/how-to-connect-wirelessly-in-a-cafe-with-11-04/302083#302083)

[http://askubuntu.com/questions/496669/ubuntu-12-04-cannot-connect-to-starbucks-free-attn-wifi-dns-issue](http://askubuntu.com/questions/496669/ubuntu-12-04-cannot-connect-to-starbucks-free-attn-wifi-dns-issue)

I haven't been able to do so myself.

---

### Post by Robert_Victor on 2015-01-22
Chili555 - yea those look pretty similar to my/our issue.  It seems hard to believe that this isn't something fairly simple, but who knows I guess.

Steeldriver - I have not as of yet.  It didn't occur to me to try that as the connection has never even partially established but it is definately worth a try.  

  Thanks guys I appreciate the input.

---

### Post by Robert_Victor on 2015-01-22
So I ran ifconfig to see the current settings and found that the IP address for the eth0 was not populating.  Could this be part of the issue and if so what is the current set of commands to rectify this?

[ATTACH=CONFIG]259426[/ATTACH]

---

### Post by chili555 on 2015-01-23
> **Robert_Victor said:**
> So I ran ifconfig to see the current settings and found that the IP address for the eth0 was not populating.  Could this be part of the issue and if so what is the current set of commands to rectify this?

Aren't you trying to connect with wireless and not ethernet? If the ethernet cable is detached, you will not be assigned an IP address.

---

### Post by kpatz on 2015-01-23
> **Robert_Victor said:**
> So I ran ifconfig to see the current settings and found that the IP address for the eth0 was not populating.  Could this be part of the issue and if so what is the current set of commands to rectify this?wlan0 has an IP of 10.0.0.7; if you're connecting wirelessly that's the interface to look at, not eth0.  Is that IP correct?  What's the output of **route -ne**?  What's in /etc/resolv.conf after connecting?  I'm wondering if you're not getting a gateway or DNS servers.  Can you ping the gateway, once you get its IP from route -ne?

You're getting real IPv6 addresses as well, but if IPv6 isn't working through the hospital's gateway, that could be causing your issues as well.  Post the output of **route -6ne** as well.

---

### Post by Robert_Victor on 2015-01-30
as kpatz mentioned, it looks like the problem was with the gateway and DNS.  We have multiple sites and while at each I copied all of the information that both my android phone and Windows laptop were using and manually entered them into network manager.  I was then able to get connected to the wifi.  I am still having issues getting redirected to the proper "redirect and acknowledgement" page, but at least I am connected so hopefully that part wont be too much harder.  Thanks all.

---

