---
title: "Why is ping command not resolving names?"
date: 2021-02-02
forum: Networking &amp; Wireless
---

### Post by username2758 on 2021-02-02
Hey,

Why is the ping command not resolving the name of a server?

[[IMG]https://i.ibb.co/qkJ5BNB/ping-2021-02-02-12-58-34.jpg[/IMG]]("https://ibb.co/qkJ5BNB")

Thanks!

---

### Post by The Cog on 2021-02-02
That looks resolved to me. What's the problem?

---

### Post by username2758 on 2021-02-02
Is it? I don't know.

Let me ping a different server:

[[img]https://i.ibb.co/V9rhHwW/ping-Screenshot-from-2021-02-02-17-10-29.png[/img]](https://ibb.co/V9rhHwW)

[[img]https://i.ibb.co/tcRcRzr/pping-screen-2021-02-02-17-13-27.jpg[/img]](https://ibb.co/tcRcRzr)to

Why are these two screenshots showing different values when pinging the same server?

---

### Post by CelticWarrior on 2021-02-02
The first is IPv4, the second IPv6.
Both are resolved. What's the problem?

---

### Post by The Cog on 2021-02-02
Given a choice, IPv6 should be preferred over IPv4, so I guess the purple screenshot doesn't have a working IPv6 internet connection.
Try the command:
```
host uol.com.br
```
and it will tell you the IP addresses for that name.

---

### Post by chili555 on 2021-02-02
> Why is the ping command not resolving the name of a server?
The *name* of the server was given in the command: uol.com.br. Resolving involves a DNS nameserver (or dnsmasq) looking up and supplying the *numbers*; that is, the IP address of the given server name. In all of your illustrations, the process went perfectly.

The process by which a given server replies by IPv4 or IPv6 is unknown to me and is generally transparent. As an example, when you select a bookmark in your browser, ubuntuforums.org, for one, we haven't any clue as to whether the answer, the web page, that is, is transmitted via IPv4 or IPv6. All we know is that it got to our browser quickly.

Your results look entireley as expected.

---

### Post by username2758 on 2021-02-02
> **The Cog said:**
> Given a choice, IPv6 should be preferred over IPv4, so I guess the purple screenshot doesn't have a working IPv6 internet connection.
Try the command:
```
host uol.com.br
```
and it will tell you the IP addresses for that name.

@**The Cog, chili555**.

Yeah, I didn't know IPv6 addresses looked that weird. It almost got me confused with a MAC address?

That purple screenshot is running Ubuntu 16.04 LTS (Unity) and the other is running Lubuntu 20.04 LTS (LXQt).

I still don't know what's the difference between browsing a website with IPv4 and IPv6. 

Like are they running on separate servers? Latency is different between the two.

```
host uol.com.br
uol.com.br has address 200.147.3.157
uol.com.br has IPv6 address 2804:49c:3102:401:ffff:ffff:ffff:36
uol.com.br has IPv6 address 2804:49c:3101:401:ffff:ffff:ffff:45
uol.com.br mail is handled by 10 mx.uol.com.br.
```

---

### Post by The Cog on 2021-02-03
You have no way of knowing if they are the same server, except that it is unlikely that on server has two IPv6 addresses. In practice there is probably a server farm behind each address.
That doesn't matter though: the host command has told you what addresses you could use for that name.
As I say, IPv6 addresses should be preferred if both are reachable (i.e. if the destination has both IPv4 and IPv6 addresses, and the caller has both IPv4 and IPv6 routes available). 
There should be no difference visible whichever protocol is used, purely because the user should expect the same result whichever protocol is used. Giving different results for the same service name depending on which protocol happens to be used to connect would be very disrespectful to the users - in general, users should not be aware of which protocol is in use, just as (I guess) you weren't.

Out of curiosity, how does the latency compare? Although that will depend very much on the ISP infrastructure, not the protocol itself.

---

### Post by username2758 on 2021-02-03
> **The Cog said:**
> Out of curiosity, how does the latency compare? Although that will depend very much on the ISP infrastructure, not the protocol itself.
Not much, just some ~6ms delta. But the difference is consistent between IPv4 and IPv6, not something to worry about though. I only asked out of curiosity since it's something new to me.

Thanks everyone for the help! (:

---

### Post by The Cog on 2021-02-03
Incidentally, on a machine with both protocols available, you can use "ping -4" or "ping -6" to choose which protocol to use.

---

### Post by username2758 on 2021-02-05
> **The Cog said:**
> Incidentally, on a machine with both protocols available, you can use "ping -4" or "ping -6" to choose which protocol to use.

Didn't know that. Will test it when I can.

Thanks!

---

