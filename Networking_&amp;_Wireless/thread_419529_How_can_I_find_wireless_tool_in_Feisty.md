---
title: "How can I find wireless tool in Feisty?"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by O-pos on 2007-04-23
Hello,

I reinstalled my Ubuntu. I had 6.10 and I reistalled 7.04. I didn't touch home partition, it's the same old one, and it works ok, after installation old familiar settings were automatically used, but the problem is I can't find this advanced wireless tool of Feisty, where you could just click once and see what wireless networks were available (I mean this: [https://wiki.ubuntu.com/7%2e04Tour?action=AttachFile&do=get&target=NetworkManager.png)](https://wiki.ubuntu.com/7%2e04Tour?action=AttachFile&do=get&target=NetworkManager.png)). Where can I find that and how can I add it to panel? when I right-click on the panel and then add to panel, there's only network monitor, which looks exaclty as primitive as the one of 6.04.

Any ideas?

---

### Post by Kobalt on 2007-04-23
You need to install the package *network-manager-gnome* with Synaptic, then you can launch it at startup by putting *nm-applet --disable* in System > Pref. > Session

---

### Post by O-pos on 2007-04-23
there is already network manager in System > Pref. > Session, with amove mentioned "nm-applet --disable", but I don't see it in panel, even after restarting.

I think that can be because of there's no applet by default in the panel, however, when I right-click it, there is no option "add the applet". However, in ubuntu 6.10 there was. What should I do?

---

### Post by Kobalt on 2007-04-23
You should see Network-Manager in the notification area of your panel, at the right top of your screen (if you didn't modify it). It's a classical network icon, two screens or a signal level if you're connected to a wireless network. 
If you don't see it yet, try to launch it in a Terminal with this command line ```
nm-applet
``` and post here the error messages if any. 
Also check in System > Admin. > System Monitor if it's not running already.

---

### Post by jester805 on 2007-04-23
I'm having wireless problems in Feisty as well.  I've been reading the forums where people install WICD so I tried that.  I still keep getting a 169.254.x.x IP address.  I'm using a Dell B130 laptop with Broadcom 1370 wireless NIC.

---

### Post by Kobalt on 2007-04-23
> **jester805 said:**
> I'm having wireless problems in Feisty as well.  I've been reading the forums where people install WICD so I tried that.  I still keep getting a 169.254.x.x IP address.  I'm using a Dell B130 laptop with Broadcom 1370 wireless NIC.
If you're looking for help on your specific problem (different from the one treated in this thread) you should open and post a new thread (and not double posting).

---

### Post by O-pos on 2007-04-23
I tried nm-applet in terminal, but nothing happened, there was no error message, nothing, The cursor just moved to next line without writing my name "name@laptop:~$" again.

I tried to install it, but I got the message that already the newest version is installed.

Strange, isn't it? But i think that with network manager everything's ok but there's problem in displaying applet. there is none of these left three icons from this picture ([http://www.debianadmin.com/images/wpa/2.png)](http://www.debianadmin.com/images/wpa/2.png)). The applet is missing and I can't it add by right-clicking the panel.

---

### Post by Kobalt on 2007-04-24
Unfortunately I'm struggling with Network-Manager myself... And I don't know much about that app : I'll be digging this further more by the end of the week I guess.

---

### Post by O-pos on 2007-04-24
OK, thanks.

---

### Post by chili555 on 2007-04-24
I suggest you go to System -> Preferences -> Sessions In the Startup Programs tab, click Add type "nm-applet", click OK. log out of your gnome session, and log back in again.

Also, NetworkManager will not be able to control interfaces you have configured in System -> Administration -> Network. So select your wireless interface and check 'Enable roaming mode.' If the tray icon for NetworkManager has appeared, you should be able to configure your connection now.

Post back and let us know.

---

