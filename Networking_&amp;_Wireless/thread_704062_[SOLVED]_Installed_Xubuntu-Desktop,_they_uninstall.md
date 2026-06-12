---
title: "[SOLVED] Installed Xubuntu-Desktop, they uninstalled, no wireless"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by ace007 on 2008-02-22
So I'm running Feisty, and I decided to give Xubuntu a try.  I installed the package "Xubuntu-Desktop" and all its dependecies.  Then decided I didn't like it, so I uninstalled all Xubuntu and XFCE related packages.  Now I can't find a wireless signal.  The nm-applet wont even tell me there are signals being broadcast.  

Any tips?

---

### Post by agim on 2008-02-22
Post the output of this command:

iwconfig

---

### Post by ace007 on 2008-02-22
I get


lo  no wireless extensions
eth0 no wireless extensions
eth1 radio off ESSID: ""
Mode: managed Channel: 0 Acess Point: Not-Associated
.. and a whole bunch of categories with zeros next to them

So I push the radio power button on the laptop and try it again and I get
...
eth1 unassociated ESSID:""
...

I know the unassociated thing is a problem, I just dont know what to do

Thanks

---

### Post by ace007 on 2008-02-22
So I found the following command for turning on the LED on my laptop's config panel

```

echo options ipw2200 led=1 | sudo tee -a /etc/modprobe.d/ipw2200

```

And now my wireless works...

---

