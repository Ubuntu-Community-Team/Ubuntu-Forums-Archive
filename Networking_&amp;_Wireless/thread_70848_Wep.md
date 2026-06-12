---
title: "Wep"
date: 2005-10-01
forum: Networking &amp; Wireless
---

### Post by mit on 2005-10-01
Hi,

I am pleased to say that Hoary is using my Centrino wireless perfectly as i can connect to my router without any security. :) 
I am hoping to install the relevant WPA stuff so i can use that but in the meantime will stick with WEP as it looks like it can handle it by default (as in the network connections for etho).

Say my WEP key for the router is 24AD67H34N then do i type S:24AD67H34N. Because if i do,  it doesn't work. Is it wise do re-start the machine, as i haven't tried this yet. If i should install something to get this to work i appologise but as it is there in the default install i assumed it would work.

oh, by the way it wouldn't hook up to the router during set-up either. 

Thanks for looking.

---

### Post by mlomker on 2005-10-01
You can edit the /etc/network/interfaces file and add a line under your wireless card.

Run **gksudo gedit** and open the file.  There should be an entry similar to the one below.  Add a line underneath it with your WEP key.

```

iface wlan0 inet dhcp
wireless-key XXXXXXX

```


Edit: Edited for clarity.

---

