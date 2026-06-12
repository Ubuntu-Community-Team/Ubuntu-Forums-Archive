---
title: "Securing Wireless Router from Puppy..."
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by TheThinker on 2008-04-06
Howdy everyone! It's been a while, and I now have a new challenge for you. I'm currently using Puppy (seamonkey) to go online via direct cable connection :). The issue is my brother recently bought a Linksys (Cisco Systems) wireless router and directly connected it properly to the computer and Windows XP on the host computer is currently unable to run the security software for the router itself. Huh, very weird. So far, with the router connected Puppy is still able to cruise the internet and it still treats the connection as Eth0. Even better, my brother successfully used Virtual Box on Ubuntu, while running his own down-scaled XP, to connect to the router with a Belkien wireless adaptor! Impressive. The problem, of course, is that the wireless router has to be on for me to connect via cable on the host computer and we want secure this wireless capability from outsiders.

Here's my question:

Can Puppy secure the router from outsiders through some sort of login program? If so, which program do I need? If I have to install it, I would appreciate a list of dependencies.

One more question: Any other tips to securing this router from Puppy? I don't want outsiders to use the cable connection.

Thanks!

---

### Post by superprash2003 on 2008-04-06
to protect your wifi network.. you need to login to your router's settings([http://192.168.1.1](http://192.168.1.1) or 192.168.0.1 depending on your model) and you will find a wireless tab.. there you can enter a WEP key which is like a password to your network

---

### Post by kutjara on 2008-04-06
> **superprash2003 said:**
> to protect your wifi network.. you need to login to your router's settings([http://192.168.1.1](http://192.168.1.1) or 192.168.0.1 depending on your model) and you will find a wireless tab.. there you can enter a WEP key which is like a password to your network

Better yet, use WPA or WPA2 if your wifi card drivers support it. WEP is about as hard to crack as as the secret decoder rings you get in cereal boxes. WPA (or, better, WPA2) will give you a very good level of security. If you set this up, you won't need to mess around with security features on your linux boxes.

---

### Post by TheThinker on 2008-04-06
I got the tab up from superprash's help, but how do I use WPA or WPA2 encryption kutjara?

---

### Post by kutjara on 2008-04-06
> **TheThinker said:**
> I got the tab up from superprash's help, but how do I use WPA or WPA2 encryption kutjara?

Your router will have a dropdown menu under "wireless settings" or "security settings" (or whatever it's called) that allows you to select your security type. WPA and WPA2 will be two of the choices. There'll usually be a choice between TKIP and AES encryption. AES is the best, but TKIP is perfectly ok if your wireless card doesn't do AES for any reason.

You can then set up your network connection manually using Network Manager (or WICD, if you prefer). Both programs have forms or dialog boxes that allow you to choose your security settings and encryption type, so just select the same ones you configured on your router, enter your password - which you should also have previously set up on your router - and (with a favorable wind) you should be good to go.

---

### Post by TheThinker on 2008-04-07
Thanks kutjara. I just realized that the tab that opened up is actually some sort of login tab. I input a random username and password, and nothing happens after I press OK. Is this the security tab you were talking about?

---

### Post by doobydave on 2008-04-07
You will need the correct username and password to access the router's setup pages.

Quite often it is admin/admin or admin/1234 but if you cant guess, check with the instructions or on internet.

Once logged in the interface should be fairly self-explanatory and you can set up the wireless to be encrypted. If you do this, you will need to setup the connection again from your clients as they will need a password to join the wireless LAN.

---

### Post by TheThinker on 2008-04-07
Thanks doobydave! I'll let you guys all know how this all pans out.

---

### Post by kutjara on 2008-04-07
> **TheThinker said:**
> Thanks doobydave! I'll let you guys all know how this all pans out.

Just to clarify, you'll be dealing with two sets of passwords. The first password is the one you need to access your router's setup screens. You'll typically have to input this when you log into the router's web interface with your browser (on my Linksys WRT600, for example, I type 192.168.1.1into my browser's URL bar, whereupon I'm presented with a username/password dialog). The instructions that came with your router will tell you what the precise username/password combo is for your model, but I suspect all Linksys routers just use admin/admin.

The second password is the one I was talking about before. It's the password your router will request from your PC whenever it connects via wifi (my WRT600 has a feature to automatically generate a "hard" password for me, or I can input my own). Typically, when you choose WPA or WPA2 on your router's setup screen, a new field will become available, asking you to input a password for the wireless connection. Enter whatever password you want, then make a note of it. Then go to your computer and set up its wireless card using the same security settings as you just configured on your router, including the password.

You want to end up with the same security protocol on both devices (WPA or WPA2), the same encryption scheme (AES or TKIP) and the same password. Under normal circumstances, that should be all you need to do.

Good luck!

---

### Post by TheThinker on 2008-05-16
Sorry for being late, but after me and my brother switched to Hardy, we were able to use Belkien wireless adaptors to go online as well as to just put the security settings of the Linksys router on hold for now. I don't think the range is that great (100ft maybe), and we do live in an acre of property so we feel it's unlikely that securing the router is necessary. Still, I'll let everyone know how this goes; it's best to be secure than sorry.

By the way, Puppy seamonkey rocks! Thanks for everyone for contributing to this thread; I'm sure I can get the router secured soon. I'll let you know hot this goes.

---

