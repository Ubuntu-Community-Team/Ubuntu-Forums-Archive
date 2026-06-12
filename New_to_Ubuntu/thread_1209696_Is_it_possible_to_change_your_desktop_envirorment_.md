---
title: "Is it possible to change your desktop envirorment? Like switch from Gnome to KDE?"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by FoxFireX on 2009-07-10
Possible?

---

### Post by csabo2 on 2009-07-10
FoxFire,

Yes it is, when you goto login the login manager has a little dropdown in the bottom corner (dont remember if its left or right) and you can choose from there.

---

### Post by David Ostrom on 2009-07-10
Yes, you can change the session when you restart your computer at login, at the lower left corner. Assuming you have KDE installed, It will ask if you went to set as the default or just the current session.

---

### Post by Xero Xenith on 2009-07-10
Yes. A good guide for installing KDE when GNOME is installed can be found here:

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)



I can't find a similar tutorial for if you have only KDE installed and want GNOME - however if you're confident in the command line this command will do just that, and should work fine.

```
sudo aptitude install ubuntu-desktop
```


To switch between the two, log out - there should be an option to switch somewhere in the login screen, though it depends which one you're using. In GDM it's in the lower-left corner, as David Ostrom described.

---

### Post by QIII on 2009-07-10
> **David Ostrom said:**
> Assuming you have KDE installed, It will ask if you went to set as the default or just the current session.

Exactly.

You have to have KDE installed.  It's not there by default in Ubuntu, but is there by default in Kubuntu.

---

### Post by FoxFireX on 2009-07-10
EDIT: Gotcha, thanks. So all I would have to do is open synaptic package manager and just look for KDE, and uninstall gnome and then install KDE?

Just out of curiosity. ^^

---

### Post by csabo2 on 2009-07-10
> **FoxFireX said:**
> I don't see an option for KDE?

You will have to install KDE first

---

### Post by QIII on 2009-07-10
You have to install KDE.

I'm not at my Ubuntu machine, so I can't walk you through the steps.

I know it can be done from the Synaptic Package Manger.

---

### Post by QIII on 2009-07-10
> **FoxFireX said:**
> EDIT: Gotcha, thanks. So all I would have to do is open synaptic package manager and just look for KDE, and uninstall gnome and then install KDE?

Just out of curiosity. ^^

No need to uninstall GNOME.

With both installed, you can choose at login.

---

### Post by FoxFireX on 2009-07-10
Ahh right.. I wasn't thinking about that when I mode the post but now I realise I don't have to uninstall gnome I could have multiple envirorments or whatever the hell you wanna call em?

---

### Post by David Ostrom on 2009-07-10
Open up the terminal and enter (sudo apt-get install KDE) then enter your password.

---

### Post by David Ostrom on 2009-07-10
> **FoxFireX said:**
> Ahh right.. I wasn't thinking about that when I mode the post but now I realise I don't have to uninstall gnome I could have multiple envirorments or whatever the hell you wanna call em?

Yes, you can have as many environments as you want.

---

### Post by oldos2er on 2009-07-10
Probably the simplest way to accomplish this is to install the *buntu-desktop packages.

 **sudo apt-get install kubuntu-desktop** gives you KDE.

 **sudo apt-get install xubuntu-desktop** gives you xfce.

 **sudo apt-get install ubuntu-desktop** gives you Gnome.

 Log out, change session, log back in.

---

### Post by David Ostrom on 2009-07-10
> **oldos2er said:**
> Probably the simplest way to accomplish this is to install the *buntu-desktop packages.

 **sudo apt-get install kubuntu-desktop** gives you KDE.

 **sudo apt-get install xubuntu-desktop** gives you xfce.

 **sudo apt-get install ubuntu-desktop** gives you Gnome.

 Log out, change session, log back in.

oldos2er,
I couldn't have said it better. 
Thanks!

---

### Post by FoxFireX on 2009-07-10
> **oldos2er said:**
> Probably the simplest way to accomplish this is to install the *buntu-desktop packages.

 **sudo apt-get install kubuntu-desktop** gives you KDE.

 **sudo apt-get install xubuntu-desktop** gives you xfce.

 **sudo apt-get install ubuntu-desktop** gives you Gnome.

 Log out, change session, log back in.


That like made it say kubuntu when my pc booted, it gave me everything kubuntu has, which I didn't want. It also didn't even give me the KDE interface.. like when I change the session to KDE it loads and still comes up at gnome..

How can I undo this?

I just want the KDE desktop interface..

---

