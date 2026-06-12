---
title: "Weird DNS issue"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by kitty500cat on 2007-07-14
Before I say anything else, keep in mind I'm new to Linux. :wink:  Also, I'm using Feisty.

Now here's the issue:

Up until this morning my wireless network was working fine. I had configured my wireless access point to use WPA Personal wireless security, and had configured Ubuntu to support it.  This morning when I started my laptop, it wouldn't connect properly.  I forget what the exact issue was, but I couldn't get DNS to work no matter what I tried. After a lot of messing around with settings, including disabling and re-enabling WPA, DNS finally works in Firefox and in the Ubuntu terminal (ping, traceroute, nslookup), but not in Opera or my Gmail checker (checkgmail).

I know that the DNS server is working properly, 'cause DNS works fine in Firefox and the terminal, but why won't it work in other programs?

Thanks.

---

### Post by starsky on 2007-07-14
> **kitty500cat said:**
> Before I say anything else, keep in mind I'm new to Linux. :wink:  Also, I'm using Feisty.

Now here's the issue:

Up until this morning my wireless network was working fine. I had configured my wireless access point to use WPA Personal wireless security, and had configured Ubuntu to support it.  This morning when I started my laptop, it wouldn't connect properly.  I forget what the exact issue was, but I couldn't get DNS to work no matter what I tried. After a lot of messing around with settings, including disabling and re-enabling WPA, DNS finally works in Firefox and in the Ubuntu terminal (ping, traceroute, nslookup), but not in Opera or my Gmail checker (checkgmail).

I know that the DNS server is working properly, 'cause DNS works fine in Firefox and the terminal, but why won't it work in other programs?

Thanks.

hi there :)

couple of things first
check your
/etc/resolv.conf and enter the primary & secondary dns server there.
for e.g.,

nameserver x.x.x.2 
nameserver x.x.x.3
namserver your.router.should_be.here

After doing that,
restart your networking
sudo invoke-rc.d networking restart

post back :)

---

### Post by kitty500cat on 2007-07-14
Thanks for the reply.

My /etc/resolv.conf file was like this:

```
nameserver xx.xx.xx.xx
nameserver xx.xx.xx.xx
```

I did add two more nameservers and then saved the file.

My router wasn't in the file.  How should I add it?
[quote=starsky]namserver your.router.should_be.here[/quote]
When you say *namserver*, do you mean *nameserver*?

Regards :)

---

### Post by kitty500cat on 2007-07-14
Hey, never mind, I got it working!

Somehow the location in the network configuration was a bit screwed up, but I managed to get it working now.

Thanks a lot for your help.

Regards :)

---

### Post by starsky on 2007-07-14
> **kitty500cat said:**
> Hey, never mind, I got it working!

Somehow the location in the network configuration was a bit screwed up, but I managed to get it working now.

Thanks a lot for your help.

Regards :)

hi there :)
sorry for getting late to your reply. yes it is "nameserver" & not "namserver". :)

Glad you made it work! :)
That's the spirit of being a free software user. You do it on your own and you feel the pleasure. isn't it? or am i generalizing geeks with normal user ?
hehe.. nevermind. :)

---

### Post by kitty500cat on 2007-07-14
Now I'm torqued (not at you, but at my computer) because the problem's back!

I did what you said earlier, but it didn't work...thanks for your help so far.

---

### Post by Mr. C. on 2007-07-14
Your DNS and WPA or other wireless settings are not related.  Either you have a TCP/IP connection that works, or you don't.  Either DNS works for the entire system, or it does not.  Individual programs do not use various means to perform name translation - they all go through the system's resolver library.

What you are likely seeing are issues with your poorly implemented local DNS cache on your commodity router.

Change your configuration (Network Manager, or whatever you use) to not use your router as a DNS; use those provided by either your ISP or some free service such as DynDNS.

MrC

---

### Post by kitty500cat on 2007-07-14
I have set my Network Manager to use the DNS addresses 66.133.170.2 and 4.2.2.3; the first belongs to my ISP; the second, I think, is a public DNS server.

But the problem is just as I have described.  In Opera, I can connect to [http://72.14.253.99/](http://72.14.253.99/), but not [http://www.google.com/](http://www.google.com/).

It seems to be a problem with Network Manager; is there a way I could wipe all of the saved network settings and start from scratch?

Also, is there any way to set a default Network Manager location?  It keeps using an unnamed location, which contains a DNS server address that doesn't work, even if I change it.

Thanks for your help.

---

### Post by Mr. C. on 2007-07-14
One doesn't test DNS with a browser.  Use the dig command:

$ dig [www.google.com](www.google.com)

If you get an answer to the query, then DNS worked at that moment.  If it fails in some browser but not others, there are other problems here that are not DNS-related.

How have you configured your network manager ?

Lets see the command line output from:
```

ifconfig -a
netstat -rn
cat /etc/resolv.conf
```

Also, have you disabled IPv6 ?

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

MrC

---

### Post by kitty500cat on 2007-07-16
Thanks for your replies.

I hadn't had Ubuntu installed for very long, so I just reformatted and reinstalled.

DNS is working fine now.

Regards :)

---

