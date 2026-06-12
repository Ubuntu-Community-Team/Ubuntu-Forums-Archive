---
title: "Shields Up-failed?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by D1Knight on 2009-11-08
[COLOR=Purple]**How do I get rid of ping? Thanks.:DP.**[/COLOR]

---

### Post by CJ Master on 2009-11-08
Ping is the time it takes for information you send to a server to bounce back to you. You can't "get rid of it" but you can lower it by getting a faster internet connection.

---

### Post by D1Knight on 2009-11-08
> **CJ Master said:**
> Ping is the time it takes for information you send to a server to bounce back to you. You can't "get rid of it" but you can lower it by getting a faster internet connection.

[COLOR=Purple][B]OK. I must be missing something there.  :confused:All right,  what I was attempting to do was pass the shields up test at  [http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)

The test says it failed only because of ping. :sad:Help, anyone....anyone?  Thank you.:DP.

How can I block ping?
[/B][/COLOR]

---

### Post by fatcrab on 2009-11-08
Why would you want to get rid of ping?

---

### Post by D1Knight on 2009-11-08
> **fatcrab said:**
> Why would you want to get rid of ping?

[COLOR=Purple]**Fatcrab, when I run the firewall test (see above link), the test concludes I fail because of ping? So if I want to pass firewall test=block ping, stop ping!?P;)**[/COLOR]

---

### Post by Tyke91 on 2009-11-08
err. I'm thinking that you mean your firewall is letting you return packets when you are pinged instead of denying them or just dropping them silently...

if you're really interested in hardening your security, check out a program called bastille. I don't know if it's current for ubuntu 9.10 tho...

errm. you really shouldn't be worried if someone can ping your computer. you should be more worried if they can... i dunno... gain root access? :)

---

### Post by Hilgo on 2009-11-08
> **D1Knight said:**
> [COLOR=Purple]**Fatcrab, when I run the firewall test (see above link), the test concludes I fail because of ping? So if I want to pass firewall test=block ping, stop ping!?P;)**[/COLOR]

In that case you want to block ICMP traffic in your firewall. More info [here]("http://www.cyberciti.biz/tips/linux-iptables-9-allow-icmp-ping.html").

---

### Post by D1Knight on 2009-11-08
> **Tyke91 said:**
> err. I'm thinking that you mean your firewall is letting you return packets when you are pinged instead of denying them or just dropping them silently...

if you're really interested in hardening your security, check out a program called bastille. I don't know if it's current for ubuntu 9.10 tho...

errm. you really shouldn't be worried if someone can ping your computer. you should be more worried if they can... i dunno... gain root access? :)

Tyke91, yes bout the firewall, you said it better than I could explain-for sure (I am new to this, but learning), thank you.

Bastille, huh!? :-k Yes, if it is available for U-9.10 repositories, I do want to try it.

OK, gaining root access, how do I protect against this?:-?

Thanks for all your kind help and advice.:D

---

### Post by The Funkbomb on 2009-11-08
What port are they saying failed?

---

### Post by Paqman on 2009-11-08
> **D1Knight said:**
> 
OK, gaining root access, how do I protect against this?:-?


Use a strong password, only install software from trusted sources, and keep your system up to date.

---

### Post by D1Knight on 2009-11-08
> **Hilgo said:**
> In that case you want to block ICMP traffic in your firewall. More info [here]("http://www.cyberciti.biz/tips/linux-iptables-9-allow-icmp-ping.html").


Thank you for the link.:)

---

### Post by D1Knight on 2009-11-08
> **Paqman said:**
> Use a strong password, only install software from trusted sources, and keep your system up to date.

Thank you for the sound advice.:)

---

### Post by D1Knight on 2009-11-08
> **The Funkbomb said:**
> What port are they saying failed?

No port number is listed for failure, just this:

"[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=1][COLOR=#000060]**Ping Reply: [FONT=Arial][COLOR=#cc0000]RECEIVED (FAILED)[/COLOR][/FONT]** — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation."


Thank you for responding.:)
[/COLOR][/SIZE][/FONT]

---

### Post by The Funkbomb on 2009-11-08
The first time I ran the common port scan, I failed due to port 113.

Enable UFW and block all ports.

```
sudo ufw enable
sudo ufw default deny
```

This will block all incoming traffic.

You will need to update rules for samba, remote desktop, torrent programs, etc if you use them.

Then go into your router's configuration.  On my router, a Linksys WRT54GS, it allows me to block Anonymous connections from the internet and filter port 113.

I ran the the common ports scan again and success.  Stealth on all of them.

---

### Post by D1Knight on 2009-11-08
> **The Funkbomb said:**
> The first time I ran the common port scan, I failed due to port 113.

Enable UFW and block all ports.

```
sudo ufw enable
sudo ufw default deny
```This will block all incoming traffic.

You will need to update rules for samba, remote desktop, torrent programs, etc if you use them.

Then go into your router's configuration.  On my router, a Linksys WRT54GS, it allows me to block Anonymous connections from the internet and filter port 113.

I ran the the common ports scan again and success.  Stealth on all of them.

The Funkbomb, ok it looks like I am set on your suggestions (UFW-I used Gufw instead, checked deny and Update rules, those programs I don't use). I have to go run the test again. Thanks.:)

---

### Post by D1Knight on 2009-11-09
Aarrrrgh. :confused:Still a no go/failed (pinging away?). I even tried what the second poster said at this link [http://ubuntuforums.org/showthread.php?t=1178988](http://ubuntuforums.org/showthread.php?t=1178988)

I starting to wonder if the "Shields Up" program is not necessarily set up for Linux firewall, but tweaked only for a Windows OS?

---

