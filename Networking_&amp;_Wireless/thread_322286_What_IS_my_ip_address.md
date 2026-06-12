---
title: "What IS my ip address?"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by navneeth on 2006-12-20
I have currently configured my DSL connection (modem connceted to an ethernet card) with a static IP. I got this IP add from 
```
ifconfig ppp0
```

Everything's fine - I have a working connection. But a problem arose when I tried to post a comment in a blog. The author of the blog has some kind of security software that blocks malicious-looking IP addresses. I contacted him and gave my IP address to add it to the software's whitelist. He has supposedly done that, but I'm still not able to post comments. The thing is, I see the same IP address when I go to System->Admin->Networking->Properties. But if I go to some site that displays the computer's IP (like [this one](http://whatismyipaddress.com/)), I get a totally different number every time. ](*,) 

Please help.

---

### Post by raul_ on 2006-12-20
Does your ISP use a proxy?

---

### Post by navneeth on 2006-12-20
I don't know. :( How can I check if my ISP uses a proxy. 

This doesn't happen in XP (it's a dual boot).

---

### Post by raul_ on 2006-12-20
in firefox try checking Edit->Preferences->Advanced->Networking and under "How Firefox connect to the internet" click Settings and see if it's autodetecting proxies. If it is, try changing to "direct connection to the internet" and see if it works. There must be another way of checking this, but since i'm not familiar with your ISP and probably we're not even on the same country this is all that i can think of :-k

---

### Post by brianh57 on 2006-12-20
Are you sure your ISP isn't assigning your IP address with DHCP?  I know you said you have a Static IP but if your IP changes often, it sounds like you're getting the IP from DHCP.

---

### Post by navneeth on 2006-12-20
Under the network settings in Firefox I already have 'Direct Connection to the Internet' selected. 

And, we're not even on the same continent. :)

---

### Post by navneeth on 2006-12-20
> **brianh57 said:**
> Are you sure your ISP isn't assigning your IP address with DHCP?  I know you said you have a Static IP but if your IP changes often, it sounds like you're getting the IP from DHCP.

By default it was DHCP, but the internet connection sucked big time with that. That's the reason I switched to static.

---

### Post by DarkN00b on 2006-12-20
Go to [this page]("http://whatismyipaddress.com/"). It will give you the IP address that servers see when you visit a web page.

---

### Post by navneeth on 2006-12-20
> **DarkN00b said:**
> Go to [this page]("http://whatismyipaddress.com/"). It will give you the IP address that servers see when you visit a web page.
Thanks, but did you see my first post? ;)

---

### Post by tturrisi on 2006-12-20
access the modem control panel, there should/may be a proxy setting there.

---

### Post by navneeth on 2006-12-21
Where do I find the modem control panel?

If it is System -> Prefs -> Network Proxy, I have 'Direct internet connection' selected.

---

### Post by punx45 on 2006-12-21
what IP address are you assigning to yourself?

if you are connected directly to the modem supplied by the ISP it is likely that their system is designed to dynamically assign you an IP.   you should not be setting a static IP yourself.

so.. more to the point of the question - the IP you get at sites such as whatismyip is an IP from your ISP, and is what the correct IP should be, and as for the blog.. if you arbitrarily chose an IP to configure for yourself statically, it is probably a "suspicious" choice.

---

### Post by navneeth on 2006-12-22
I just noticed that this is also happening in Windows. The problem wasn't there before. I'm SO confused.  :confused:

> what IP address are you assigning to yourself?


After I did a sudo pppoeconf, the last step has something along the lines of "check ifconfig ppp0 for network settings." That's were I got the number from. 

> 
if you are connected directly to the modem supplied by the ISP it is likely that their system is designed to dynamically assign you an IP. you should not be setting a static IP yourself.

There's a wire going from the modem (supplied by the ISP) to the ethernet card. Connecting thru' DHCP was as good as no internet connection at all.

---

### Post by tturrisi on 2006-12-22
If your dsl modem does not also have a router using dhcp, then you cannot use a static ip in your network configs.  You will be using the ip assigned by the isp.  The dsl isp likely uses dhcp and every time you connect (modem dials in to isp) you will be assigned a different ip.  If the modem is also a modem-router that uses dhcp or not, you can then assign a static ip to the comp, but you MUST config the modem-router to be able to do so via it's control panel, accessed via a web browser.  Ask you isp about modem config via the browser or rtfm for the modem, how to do so is contained in it.

---

### Post by navneeth on 2006-12-22
Thanks. The modem I use is the second one on [this page](http://www.utstar.com/Solutions/CPE/ADSL_CPE/).  Now, in an unrelated problem, [I've completely lost access to Ubuntu](http://ubuntuforums.org/showthread.php?t=323065). I'll check with the ISP

---

### Post by MrHorus on 2006-12-22
> **punx45 said:**
> so.. more to the point of the question - the IP you get at sites such as whatismyip is an IP from your ISP, and is what the correct IP should be

I disagree - it all depends on where the site is getting the IP from.

If it's getting it from the user agent i.e. the browser then it *should* detect it as whatever the user sees it as and if it's getting it from where it 'sees' the incoming connection from then if the user's ISP us using a cacheing proxy (many ISPs do this to speed up web access) then it's the IP of the proxy that will show up.

---

### Post by Saverio on 2008-04-29
I wrote a couple of scripts that returns your LOCAL ip, that is the IP your computer has in your local network (that is the one you can easily see from your computer, accessing somehow to your ethernet card or wireless card info), and the EXTERNAL IP, that is the IP that you have towards the rest of internet.

Try here
[http://saverio.bolognani.googlepages.com/backupinlinux2]("http://saverio.bolognani.googlepages.com/backupinlinux2")

Hope it helps!
Ciao!
 Saverio

---

