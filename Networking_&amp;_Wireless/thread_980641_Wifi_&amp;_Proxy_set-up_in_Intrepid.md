---
title: "Wifi &amp; Proxy set-up in Intrepid"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by anhhung on 2008-11-13
Hello,

We're holding a Barcamp event at RMIT Vietnam.

Due to security concerns, the university only allows us to connect to the Internet through a proxy.

Basically, when at the university, I can immediately log in to a separate wireless network that requires no password.

However, in order to connect to the Internet, I will need to log in to a proxy server with a username and password.

I'm a bit clueless as I've never used a proxy before. Do you know how this works out? Need advice as to what I should do and which tools to install. I'm using Firefox. Thanks

---

### Post by iponeverything on 2008-11-13
Go to:

System -> Preferences -> Network Proxy

or configure it via firefox:

Edit -> Preferences -> Advanced -> Network -> Settings

---

### Post by AndyCee on 2008-11-13
iponeverything's post is exactly right. Personally I use the 1st option at my uni.

I'll just add that if you want to use synaptic/run updates, you may also need to open

System -> Administration -> Synaptic Package Manager -> Settings -> Preferences -> Network.

Phew.

---

### Post by Gumm on 2008-11-14
Jip, all of the above, and if you want to run apt from the console, then I set the environmental variable http_proxy as well:

```
export http_proxy=http://username:password@192.168.0.1:1234
```

Where username, password, the ip address and port will be the University's proxy server details and login name and password.

---

