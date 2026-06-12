---
title: "NetworkManager Issues .. help please"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by ebike on 2007-03-10
Hi All,

I am trying to get NetworkManager running. I have installed it, and had to restart dbus to get it to see my networks.

However, it only sees my wired network, it does not see my wireless network wlan0.
They are both working in "Networks" if I change between them, but when I de-select them so that NetworkManager can see them, I cannot get it to auto start my wlan0 by just pulling out the ethernet cable ... as is meant to happen.

Any idea's anyone?

Some docs say remove all reference to wlan0 and eth0 in /etc/networks/interfaces, but I don't undersand how that can work, as all the details about WEP keys etc are in that file.

Thanks.

PS: Is there a button on this forum to see all your own posts?? I have recently moved here from Gentoo ):P

---

### Post by RomeReactor on 2007-03-10
Hi. Please post your interfaces file:

```
gedit /etc/network/intefaces
```

To see your posts, click on your username on the page and select **Find all posts by ebike**

---

### Post by ebike on 2007-03-10
Ok, I got a little further. It seems Network manager doesn't use the info out of /etc/network/interfaces for the connections.

I got rid of all entries for eth0 and wlan0, left just lo. Now the applet has wireless enabled and since I cannot see my Network in the list, I go and create a new network and put in the WEP key etc, finish the dialog and it cannot connect :(  I then go into the newly created connection and try to update the WEP key (hex) as I thought it was entered incorrectly, but it will not let me, it has the connect button grayed out in all modes except PassPhrase ... it seems to think that I need a passPhrase ... but I don't.

What sort of rubbish is this......?? I can't even delete my newly created network and start over ...:cry:

---

### Post by RomeReactor on 2007-03-10
Network-Manager hasn't worked all that well for my wireless connection; most of the times i've installed it, it refused to connect to my router, and the times it did work, the connection timed out after about an hour. So, perhaps you could try uninstalling it and editing the /etc/network/interfaces file (or use **System-->Administration-->Networking**) to enter your card's configuration and get your wireless working.

---

### Post by ebike on 2007-03-10
Yep, sure I can do that. But that's not the point. I should be able to get it network manager working ... if not, it shouldn't be in the repository !!

---

### Post by jacksonz123z on 2007-03-12
Networkmanager has managed to waste a lot of my time.  Perhaps it will be right when Fiesty is released.  Initially NM could not see my working wireless connection. This was fixed by commenting out  eth0 wlan0 in /network/interfaces etc.  However, now after entering my keyring password (annoying step) it will not connect even though it can "see" the router.
I deleted the applet from the panel, I will try again in a few months.:mad:

---

### Post by ebike on 2007-03-12
Me too !

---

