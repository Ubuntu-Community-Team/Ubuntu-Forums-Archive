---
title: "Networking Xubuntu and XP"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by coasat on 2009-06-02
How can I transfer data wirelesly between my Xubuntu laptop and my windows XP laptop. They are both connected to the internet with wifi but I want to transfer the data direct. 

I've searched loads of places, perhaps I'm using the wrong terminology. 

I think I need to set up a wireless LAN. Do I do this through my wireless router? Could you refer me to a "how to" page?

Thanks

coasat

---

### Post by MichaelSammels on 2009-06-02
You will need to install a Samba Server. This can be done via Synaptic.

---

### Post by appier on 2009-06-02
Once Samba has been installed, you will want to set the permissions on the folder so that it will be shared over the network.  From there, make sure that any firewall or antivirus software you may have on the XP machine is not excluding your Xubuntu machine.

---

### Post by achase79 on 2009-06-02
xfce does not have a native network browser to look at shares on the network.  After installing samba, you may want to use another window manager other than Thunar (such as nautilus from gnome or dolphin from kde) for seeing the shared folders on the XP computer or you can use another program such as pyneiborhood to locate shares.

---

### Post by gn2 on 2009-06-02
As mentioned, Thunar does not have native network file browsing, but this can be manually configured easily enough.

[Here's how]("http://ubuntuforums.org/showthread.php?t=304131").

---

### Post by coasat on 2009-06-03
[LEFT]MichaelSammels, I checked synapitic manager and Samba is already installed. 

appier, I'm still trying to figure out how to change permissions. I sudo nautilus, then navigated to the folder I wanted to change the permission of, right clicked and then properties. Under Permissions tab, I didn't find anything to change. There wasn't a yes/no option to allow/disallow permissions. Any ideas? 

Can anyone find a tutorial on this? I haven't been able to find one.

Thanks,

Coasat


[/LEFT]

---

### Post by gn2 on 2009-06-03
> **coasat said:**
> Can anyone find a tutorial on this? I haven't been able to find one.

How to enable network file browsing in Xubuntu is in the "here's how" link in my last post.

---

