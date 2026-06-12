---
title: "Wifi password loop"
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by mailfordannym on 2014-05-13
Hi, I have an Netgear WNDA3100 wifi usb adapter. I got it to work with ndiswrapper. The only issue is that when I connect to my network I type in my password, then every 30 seconds it asks for my password again. It dosen't connect to the network. 

Please help

Thanks

---

### Post by squakie on 2014-05-14
There are a couple of things that come to mind based on my personal experience with similar problems.

It's probably obvious to say you must have the exact password/passkey - case is important.  But even more than that:  if you are using network manager then you need to click on the icon on the top bar, click on "Edit Connections".  If there is a definition there for what you are trying to get to work, click it and click delete, then close out of network manager and try connecting again.  I have found that network manager sometimes remembers even a "bad" connection attempt and tries to override with it.  Removing any entries for the connection lets you start over from scratch - and with the exact password/passkey.

---

### Post by mailfordannym on 2014-05-14
What do you mean by "Exact Password"?

---

