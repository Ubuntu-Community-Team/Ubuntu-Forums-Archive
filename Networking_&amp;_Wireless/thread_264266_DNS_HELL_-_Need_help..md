---
title: "DNS HELL - Need help."
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by Marquis_Dain on 2006-09-24
Ok, after mucking around in the terminal for 3 hours myself and a friend of mine can still not fix a most annoying problem I am experiencing with my net connection.

I'm using a standard Netcomm modem connected via ethranet - And I'm having this strange problem where if I ping websites through the terminal I get a big pause before any activity.

And If I type in any URL in FireFox it will respond, althoug it wont actually do anything for about 30 seconds - then suddenly "kick into" action and start loading the page.

We found that if we try to acsess the sites directly using their IP's through Firefox it responds instantly. Gaim also takes an extremely long time to log-in and respond to the internet initially.

He claims its a DNS problem and I only installed linux for the first time today - I'm almost completely ubuntu-illiterate.

Can anybody help me, has anybody experienced or IS experiencing this problem?! It's very frustration and disrupting my use of the internet alot.

Any information you need to help me will gladly be given.


ps. I am dual-booting with windows XP and I dont have this problem on that

---

### Post by goatflyer on 2006-09-24
Sounds like you're hitting a non-existent dns server for all name lookups.  Check /etc/resolv.conf and fix it, or else:

cat /etc/resolv.conf

and post the result.  We'll suggest changes if something seems obvious.

---

### Post by Marquis_Dain on 2006-09-24
nameserver 192.168.1.1

hmm, thats all thats there.

Thats the IP I would type in FF to acsess my modems webbased GUI
So I should change this to my DNS? I'm not sure what to do :\

---

### Post by mips on 2006-09-25
Go to your ISP's website or call them and find out the IP Addresses for their primary & secondary DNS servers.

Edit your /etc/resolv.conf file to have these entries:
>  nameserver *(Insert Primary Address here!)*
nameserver *(Insert Secondary Address here!)*
nameserver 192.168.1.1 *(Leave this one at the bottom or hash it out)*[I]

Also look at disabling IPv6.
[/I]

---

### Post by Iowan on 2006-09-25
> **mips said:**
> Go to your ISP's website or call them and find out the IP Addresses for their primary & secondary DNS servers.
Or...
You might see what DNS servers XP is set to use.

---

### Post by mips on 2006-09-25
> **Iowan said:**
> Or...
You might see what DNS servers XP is set to use.

I'm pretty sure it's going to point to the router address but i could be wrong...

---

### Post by dannyboy79 on 2006-09-25
Do you have a modem and then a router? I can tell you that when I was using DHCP through the router I didn't have to configure any dns settings within Ubuntu cause the DNS servers were defined within the Router config auto detected from my ISP. I had the same DNS server (your router or in this, your modem IP address in my resolv.conf) and I never had a problem with any slowness as what you are saying but I can tell that when I went to Static I did have to add the DNS servers IP address into the resolv.conf. Like I said I was able to figure out the IP's of the dns servers by simply logging into my router web based configuration using Firefox or IE. Sounds strange to me, wish I could you. I thought I would simply inform you of my situation incase it might help you.

---

### Post by dannyboy79 on 2006-09-28
why is that people ask for help and then when people try to help, they go away, even if they solved there issue they really need to come back and right the solution so that others in the future can have answers!!! i am a newbie and hate it when I look for hours for that 1 thread and then when I finally find it, the answer isn't there after another hours of reading!

---

### Post by penguinman007 on 2006-09-29
Yes changing the entry in etc\resolv.conf from the modem address to the actual dns address has helped me.

However, this entry is automatically modified back to the wrong address.

How do I prevent resolv.conf from automatically being re-written with the wrong address ?.

Is it something to do with Java ?, I am using java URL classes, maybe they are overwriting this file.
Is there someone I can blame and punish for this ?

---

### Post by handy on 2006-09-29
> **penguinman007 said:**
> Yes changing the entry in etc\resolv.conf from the modem address to the actual dns address has helped me.

However, this entry is automatically modified back to the wrong address.

How do I prevent resolv.conf from automatically being re-written with the wrong address ?.

Is it something to do with Java ?, I am using java URL classes, maybe they are overwriting this file.
Is there someone I can blame and punish for this ?

I've been on this problem for many months on & off, have a [look here]("http://ubuntuforums.org/showthread.php?t=188551"), we are getting very close to the ***proper*** solution now I believe.

There is a way to work around it too, have a look at [post #14]("http://ubuntuforums.org/showthread.php?t=188551&page=2") in the above thread.

---

### Post by handy on 2006-09-30
Try this:

**Option 3** from [http://www.ubuntuforums.org/showthread.php?t=128254&page=2]("http://www.ubuntuforums.org/showthread.php?t=128254&page=2") **Post# 13**.

***[Edit:] Repaired link, it is correct now...***

---

