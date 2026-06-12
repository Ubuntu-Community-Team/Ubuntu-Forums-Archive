---
title: "Ubuntu is blocking my port"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by Kimm on 2006-11-29
I'm having problems with BitTorrent on Edgy.
I can open a port for outbound connections for BitTorrent, I've tried forwarding it in our router (I even tried to completely dissabling the Router Firewall for my computer), but whenever I check the port with the uTorrent Port Checker it is still closed.

I can point out that my father (who is using windows), is using the same program and has forwarded a different port, which works wounderfully.

I have not tinkered with iptables :/ and I dont believe it is being blocked by my ISP since I have tried several others.

Helt anyone? :confused: ](*,)

---

### Post by frodon on 2006-11-29
Your issue seems non-ubuntu related because ports are not blocked by default, so if you didn't install any firewall programs or scripst on your ubuntu box then it comes from your router IMO.

---

### Post by trubblemaker on 2006-11-29
Recently I ran into another guy with this issue, try this, run it as root. if it runs without issue you might need to change the ports it runs on.  otherwise it's usually a port forwarding issue.  

the signs it's port forwarding issues, is that you can connect, get seeders and leachers, starts to download then stalls, goes to 1kb/sec or 0kb/sec.  if your not even getting that far I agree it's another issue.

---

### Post by trubblemaker on 2006-11-29
oh yeah also the same program may use different ports switching from windows to linux, because root, reserves the first thousand or so ports.

---

### Post by Kimm on 2006-11-29
> **trubblemaker said:**
> Recently I ran into another guy with this issue, try this, run it as root. if it runs without issue you might need to change the ports it runs on.  otherwise it's usually a port forwarding issue.  

the signs it's port forwarding issues, is that you can connect, get seeders and leachers, starts to download then stalls, goes to 1kb/sec or 0kb/sec.  if your not even getting that far I agree it's another issue.

I can connect, get seeders and leachers and it does start to download at an average of 10 kb/s (sometimes, very seldom, it goes up too 400-700 kb/s). But at times when the port has been open it used to go faster.

I tried checking the port as root, with no change. And I set the port myself, it is way above 1000

This is a screenshot of the portforwarding page of our router:

[[IMG]http://img166.imageshack.us/img166/1500/linksysor9.th.png[/IMG]](http://img166.imageshack.us/my.php?image=linksysor9.png)

I am 192.168.1.11 and my father is 192.168.1.13.
My fathers port works perfectly ](*,)

Edit:

> 
Welcome to the µTorrent Port Checker.
A test will be performed on your computer to check if the specified port is opened.

Checking port 65410 on <IP>...

**[color=red]Error![/color]** Port 65410 does not appear to be open.


---

### Post by trubblemaker on 2006-11-29
well i'm totally with you that your port forwarding is correct.  and it does look like it's being blocked by something but I'm not hip on my port checking.  are you running any other software that would grab the port?  I assume your not, as you seem like you know what your doing but it's worth a shot.

---

### Post by Kimm on 2006-11-30
> **trubblemaker said:**
> well i'm totally with you that your port forwarding is correct.  and it does look like it's being blocked by something but I'm not hip on my port checking.  are you running any other software that would grab the port?  I assume your not, as you seem like you know what your doing but it's worth a shot.

I dont think I am... how would I tell?

---

### Post by HeSh on 2006-11-30
Same thing is happening to me. If i run as root or not, ALL ports are blocked. I connect throught router and i tried forwarding single, multiple and all ports to the machine and still nothing. From WinXP installed on same machine everything works fine.

I'm really clueless on what to do right now.

---

### Post by milton1 on 2006-11-30
This may seem overly simple, but have you considered running firestarter and allowing that port for all traffic? It is essentially just modifying iptables for you, but with a nice, friendly interface.

---

### Post by HeSh on 2006-12-01
I have. And it didn't help.

However, somehow problem fixed itself. Azureus is still telling me he can't bind on port (and NAT test fails on any port), but when i put some torrents, they work without a problem. And i can see that selected port is used without a problem.

---

### Post by trubblemaker on 2006-12-01
ok Kimm what happens if you try to start multiple torrents?  If you leave them over night do they work? 

*grasping at straws*

1) the port checker is it linux savy? it it a real simple test or something that relies on a windows response?

2) is it possible that it's a slow torrent? (hoping but not believing it's true)

---

### Post by trubblemaker on 2006-12-01
just saw another post that said.... rebooting the router fixed the issue, even though it shouldn't have 'cause he'd already forwarded it.  Worth a shot though eh?

---

### Post by Kimm on 2006-12-02
> **trubblemaker said:**
> ok Kimm what happens if you try to start multiple torrents?  If you leave them over night do they work? 

*grasping at straws*

1) the port checker is it linux savy? it it a real simple test or something that relies on a windows response?

2) is it possible that it's a slow torrent? (hoping but not believing it's true)

If I start multiple torrents most of them will download at about 5 kb/s and some will sitt still. Nothing changes if I leave them over night...

1) The port checker is for uTorrent (windows clinent), but I have used it in Linux before and it has told me that the port is open.

2) Well, most of them arnt super-fast torrents, but they used to go faster and torrents from trackers that I know will go fast (like Dattebayo) dont. :/

---

### Post by Kimm on 2006-12-02
> **trubblemaker said:**
> just saw another post that said.... rebooting the router fixed the issue, even though it shouldn't have 'cause he'd already forwarded it.  Worth a shot though eh?

I've allredy tried that ](*,)

---

### Post by trubblemaker on 2006-12-02
k, here's another thing that might be messing you up is uPnp, apparently sometimes it gets messed up if you leave it on and port forward, try turning off **u**niversal **p**lug a**n**d **p**lay. and see if that works for you.

---

### Post by Tekovro on 2006-12-14
> **trubblemaker said:**
> just saw another post that said.... rebooting the router fixed the issue, even though it shouldn't have 'cause he'd already forwarded it.  Worth a shot though eh?

Yup. That did it for me. I love you.

---

### Post by zazen666 on 2006-12-28
nevermind

---

