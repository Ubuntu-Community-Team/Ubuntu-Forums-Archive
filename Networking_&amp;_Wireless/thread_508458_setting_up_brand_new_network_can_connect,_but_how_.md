---
title: "setting up brand new network: can connect, but how to set up ESSID and encryption?"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by shadowfax on 2007-07-24
I've just got a new internet connection this morning and can connect easily, ye! 

But there is no encryption, and the network name is "Untitled". Apparently on WinPCs a dialogue would appear that could set up the name, password, etc. How do I do it on ubuntu? I have tried 'create new netwrok' on netwrokmanager, but that doesnt work. I guess I would need to rename the network, not create a new one, and set a key. Any guides on how to do this?

---

### Post by moore.bryan on 2007-07-24
*i think [wicd]("http://wicd.sourceforge.net/") is far-superior to network-manager... perhaps that will help you out.*

---

### Post by sfarber53 on 2007-07-24
You need to talk to your router to set-up the ESSID and encryption.  The ESSID is easy.  A bit harder and well worth it is to bypass encryption and setup an access control list based on machine MAC addresses.

I was using WPA-PSK on my network before M$ broke it.  I've been using the MAC ACLs for a couple of weeks now and am very happy with the results.  The access control list prevents access to your wireless network by any one not listed in the MAC ACL.  I think it gets you some extra speed to since the encryption overhead is eliminated.

Have fun!

- Steve

---

### Post by moore.bryan on 2007-07-25
> **sfarber53 said:**
> You need to talk to your router to set-up the ESSID and encryption.  The ESSID is easy.  A bit harder and well worth it is to bypass encryption and setup an access control list based on machine MAC addresses.

I was using WPA-PSK on my network before M$ broke it.  I've been using the MAC ACLs for a couple of weeks now and am very happy with the results.  The access control list prevents access to your wireless network by any one not listed in the MAC ACL.  I think it gets you some extra speed to since the encryption overhead is eliminated.

Have fun!

- Steve

[I]an howto?  :-)
--------
EDIT:
--------
nevermind... my router had a howto!
[/I]

---

