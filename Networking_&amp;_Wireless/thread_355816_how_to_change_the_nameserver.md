---
title: "how to change the nameserver?"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by checho on 2007-02-07
Hi, i don't know why my computer got automatically this nameserver adress 192.168.1.1 instead of 196.40.31.205 that is the one that actually works. I change it in the "resolv.conf" , specifically ask for it in "/etc/dhcp3/dhclient.conf" and in System>Administration>Networking>DNS
Can someone help me please? I thought it was a common problem, but there is nothing simmilar in the forum.

---

### Post by kidders on 2007-02-07
Hi there,

When you acquire a network address by DHCP, the server usually sends you all the other information you might need to set up a workable network connection, including a DNS server address, so you can look things up.

In your case, it looks as though you might have a router/modem combo or a similar piece of hardware, on which the DHCP server is running, and that it's deliberately sending you its own IP address in place of 196.40.31.205 ... which gives it better control over name resolution.

Am I on the right track?

Also...[LIST]
[*]Is your DNS resolution working?
[*]Is it slow?
[/LIST]If I've guessed your configuration correctly, overriding your DNS server settings is easy. Let me know, and I'll explain.

---

### Post by checho on 2007-02-07
Yes you are right! I got a CNet Broadband Router CNIG-914 and a Motorola SB5101 modem. I'm not sure what you mean with resolution but, after changing the nameserver it works fine (internet and other networking aplications) until it resets and the connection falls

---

### Post by checho on 2007-02-07
Do you think that uncommenting the line "#reject 192.168.1.1;" in /etc/dhcp3/dhclient.conf will work?

---

### Post by checho on 2007-02-07
It didn't

---

### Post by kidders on 2007-02-07
> **checho said:**
> Do you think that uncommenting the line "#reject 192.168.1.1;" in /etc/dhcp3/dhclient.conf will work?

No, but you're on the right track. I could've explained this in my first post, but I was distracted and had to stop typing! Sorry about that.

One thing I wanted to mention is that taking DNS resolution (the process of translating a name into an IP) out of the hands of your broadband gizmo can have undesirable side-effects, where you're relying on it to know about certain things. You may not be, in which case, you won't need to worry. For instance, it may have NetBIOS-related capabilities (which can be useful on networks using Windows filesharing), that you would no longer benefit from.

Anyhow, afaik the setting you're looking for is **supersede domain-name-servers**. That will allow you to replace a setting provided by your DHCP server with one you define locally, which would have the following effects:

[LIST]
[*]DNS lookups will speed up slightly, because "Ubuntu -> Router -> ISP" turns into "Ubuntu -> ISP".
[*]Should your ISP's DNS server settings change at some point, you will have to take care of that manually.
[*]Any special magic your router knows that can help your network do interesting things will be lost.
[/LIST]

---

### Post by checho on 2007-02-08
Hi, thanks for your time! You know something really strange is happening here. I did what you told me and the connection felt. I tried "dig www.pcuser.com.au" and received the message:
root@sergio:/home/sergio# dig [www.pcuser.com.au](www.pcuser.com.au)

; <<>> DiG 9.3.2 <<>> [www.pcuser.com.au](www.pcuser.com.au)
;; global options:  printcmd
;; connection timed out; no servers could be reached

So I unplugged the router and executed "dhclient eth0", I got a new ip, checked the /etc/resolv.conf and there was nameserver 196.40.31.205. but got no connection. Then again I tried with "dig www.pcuser.com.au" and received a new number: 63.203.35.55. So then again changed manually in /etc/resolv.conf and got again online. But after a time it falls and for my surprise when I check /etc7resolv.conf is nameserver 196.40.31.205. In other words now I have the same problem but with new nameserver numbers!!! Again thanks for your time and help!

---

### Post by kidders on 2007-02-08
Yikes!

The first thing to watch is that you're not running multiple copies of your DHCP client at the same time, and that you restart it whenever you make changes to its configuration.

Secondly, it looks as though the change I suggested may have had no effect (which is why I mentioned the first thing). I once noticed the same behaviour on a box of mine, and had to resort to deleting the section of the network management scripts that dealt with rewriting resolv.conf! (At the time, I just couldn't be bothered spending time trying to figure out what was going on.) Although it's the wrong thing to do, it would certainly solve your problem quickly!

Have you tried taking a look at your router configuration, by the way? The ideal solution (in my opinion) would be to have it send you the right DNS server address the way it's supposed to.

If you want to, you could hack /etc/dhcp3/dhclient-script temporarily, so you could play around with dhclient's configuration some more or check out your router, without being interrupted by annoying DNS problems. You could probably short-circuit the function that rewrites resolv.conf by adding something like **return 0** immediately after **make_resolv_conf() {** (the function declaration).

Everything you ever wanted to know about dhclient.conf is in its man page, by the way. I was pretty sure I'd found the right option for you though. :confused:

---

### Post by checho on 2007-02-10
Hi, I found a solution inspired by **from_beyond** in a thread of last year. After running "dig" in the console and check for the right nameserver, write it manually in /etc/resolv.conf and execute in console "chattr +i /etc/resolv.conf". That keeps the file unaltered. Sorry for not writing it before but I want to be sure it worked before posting it. Even though it solves the problem I agree with you that the ideal solution is changing something in /etc/dhcp3/dhclient-script, because the nameserver can change and I also have to restart the modem everytime after running windows (I have both on the computer). But maybe in the future because I don't really understand this srcipt, first of all I'm not sure in what language is written, seems to be perl, I'm not sure.
Again thanks for your help and time;
[I]Muchas gracias por todo,
saludos,
sergio[/I]

---

