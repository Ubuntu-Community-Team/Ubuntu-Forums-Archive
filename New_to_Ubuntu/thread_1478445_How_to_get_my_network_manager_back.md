---
title: "How to get my network manager back?"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by kramer65 on 2010-05-09
I just did a fresh install of 10.04 and it all seems to work pretty nice. By accident however, I took away the network thingy on the top right of the screen.

Does anybody know how I can get it back..?

---

### Post by linuxman94 on 2010-05-09
You need to add the notification area.  Right click on the top panel and click 'Add to Panel'.  Search for notification area and click add.

---

### Post by MrWES on 2010-05-09
> **kramer65 said:**
> I just did a fresh install of 10.04 and it all seems to work pretty nice. By accident however, I took away the network thingy on the top right of the screen.

Does anybody know how I can get it back..?


I believe if you activate the installation CD-ROM in Software Sources, I believe apt-get install will find it.
Either from the terminal:

```
sudo apt-get install network-manager-gnome
```

Or Synaptic Package Manager.

Bill

EDIT: Mis-read that post -- sorry, I thought you uninstalled the network manager. Sigh...

---

### Post by kramer65 on 2010-05-09
The network manager is installed and my network works fine. It's just that I don't see the icon anymore. And since I sometimes need to connect to a vpn I would like to get the icon back.

I attached an image. If I click on the little black space between the bluetooth-sign and the "uu" I get the menu, but I just don't see the icon..  :confused:

---

### Post by linuxman94 on 2010-05-09
Try this command in terminal:

```
sudo apt-get install --reinstall network-manager-gnome
```

---

### Post by kramer65 on 2010-05-09
Ah! Found it!

I just removed the notification area and put it in again, and now it shows.. :-)

Thanks for all the help!

---

