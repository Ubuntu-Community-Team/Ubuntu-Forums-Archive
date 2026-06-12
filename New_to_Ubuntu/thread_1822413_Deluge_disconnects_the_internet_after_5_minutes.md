---
title: "Deluge disconnects the internet after 5 minutes"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by TheManno1 on 2011-08-10
After renewing my internet connection Deluge stops working after 5 minutes. The internet is still connected but nothing loads. I disconnect the internet and it works and so does deluge and then it stops to work after 5 minutes. Also if I close deluge it doesn't open again until I restart the computer.The deluge forums also won't send my activation email. Using UBUNTU NATTY

---

### Post by TeoBigusGeekus on 2011-08-10
Have you tried with a different torrent client?
Ktorrent, Transmission, etc.

---

### Post by TheManno1 on 2011-08-10
Same

---

### Post by carverj on 2011-08-11
Which service provider are you with? Is it possible that they are stopping these downloads?

---

### Post by TheManno1 on 2011-08-11
It seems to be working right now and also this problem was not happening in windows.Though it could happen again.Why did it suddenly start working all of the sudden.

---

### Post by Grenage on 2011-08-11
When this happens, there's almost always one cause - a throttled router.  Most home routers cannot handle hundreds of NAT connections, they wet themselves.  The easiest thing to do is drop the maximum number of global connections/threads within the client config.

If you're downloading something relatively unpopular ('The Fun of Algebra'), you probably won't encounter a problem.  If you download something popular ('Busty Asians IV'), you likely will.

---

### Post by TheManno1 on 2011-08-11
How do I fix it and what is Busty Asians IV

---

### Post by Grenage on 2011-08-11
> **TheManno1 said:**
> How do I fix it and what is Busty Asians IV

I was just joking.  You can change the maximum global connections in the main configuration, which will be under one of the menu options.  It might be listed under network settings.  If the global limit is 200, try 100; if it's 100 (unlikely), then try 60.

---

### Post by TheManno1 on 2011-08-11
That is Maximum connections right.

---

### Post by Grenage on 2011-08-11
Yup yup.

---

### Post by TheManno1 on 2011-08-12
Setting it to 60 doesn't even work. It is working in Windows.

---

### Post by Grenage on 2011-08-12
> **TheManno1 said:**
> Setting it to 60 doesn't even work. It is working in Windows.

Did you set the maximum connections per-torrent or globally?  It would make no difference if you had one torrent running, but it would if you have a queue of simultaneous downloads.

The torrent client in Windows, what is it?  It will also have a section for network settings, so perhaps you could check what they are set to?

---

### Post by TheManno1 on 2011-08-12
It is utorrent and what setting should I look at. This happened after renewing the internet connecton.

---

### Post by Grenage on 2011-08-12
The maximum connections per torrent, and the global settings.  Does this problem occur while downloading a single torrent?

---

### Post by TheManno1 on 2011-08-13
Yes it does.

---

### Post by TheManno1 on 2011-08-24
Any idea what could be causing this.

---

### Post by TheManno1 on 2011-08-26
Hello Governer what seeems to be thy problem.

---

### Post by Grenage on 2011-08-26
Sorry for the delayed reply.

You said that this only started happening after you renewed your internet connection; what did you mean by that?  Do you have a new ISP/router, or did you just restart the router and get a new IP?

In Deluge, there is an option within network settings to check that the ports are being forwarded correctly.  When you select it, does it come back ok?  I think you get a green tick when it's good, and a red cross when it's not.

I believe that utorrent now has a Linux client, so if we get nowhere in Deluge, you could always give that a whirl.

---

### Post by TheManno1 on 2011-08-26
Can someone summit utorrent to get deb also giftwrap does not install.I think the internet service provider upgraded their technology or something.

---

### Post by TheManno1 on 2011-08-27
I reset ubuntu to factory settings but nothing.I tested active prt and there is an eclamation mark.

---

### Post by TheManno1 on 2011-08-28
What could be the problem.

---

### Post by Grenage on 2011-08-30
> **TheManno1 said:**
> I reset ubuntu to factory settings but nothing.I tested active prt and there is an eclamation mark.

Hi there,

Do you have access to your router configuration?  If so, can you configure the ports deluge (or you) wants to use so that they forward to your PC?  While I've not seen lack of forwarding slow down a connection, and most routers will use UPnP with programs like Deluge - it can't hurt to rule it out.

---

