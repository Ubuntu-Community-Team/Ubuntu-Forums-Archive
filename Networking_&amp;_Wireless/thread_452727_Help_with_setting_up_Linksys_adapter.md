---
title: "Help with setting up Linksys adapter"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by flippo0784 on 2007-05-23
I have a Linksys WUSB54G router (I read the sticky but I don't get the internet at all in the first place)

I'm a complete noob when it comes to Linux and I'm eager to learn about it but I can't set up the adapter because I'm new to the software. I have an x86 running 32-bit Windows. 

Any help much appreciated

---

### Post by Super Carp on 2007-05-23
What are you trying to do?  What model or type of router do you have?  Have you tried using an ethernet cable from your router to the laptop first, to make sure Ubuntu is getting a wired signal?

---

### Post by stchman on 2007-05-23
> **flippo0784 said:**
> I have a Linksys WUSB54G router (I read the sticky but I don't get the internet at all in the first place)

I'm a complete noob when it comes to Linux and I'm eager to learn about it but I can't set up the adapter because I'm new to the software. I have an x86 running 32-bit Windows. 

Any help much appreciated

Are you cable or DSL?

I recommend using Ethernet over USB.  I have the WRT54G router and it works great with cable modem.  I am going to assume you also want wireless connectivity.

---

### Post by introspectif on 2007-05-24
Press Alt+F2 and enter

```
gksudo network-admin
```

then press OK. 

You'll be prompted for a password, so enter your own password. 

Then see if there is a "Wireless Connection". If there is, then Ubuntu has detected your device -- most probably it has, because I use the same device. 

If everything's ok so far, make sure the connection is enabled (there's a check/tick beside it).

The next step is to click on "Properties" and see if you can view your wireless network from there.

---

