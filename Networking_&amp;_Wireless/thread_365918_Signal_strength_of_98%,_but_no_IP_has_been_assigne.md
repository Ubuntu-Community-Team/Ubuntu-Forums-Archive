---
title: "Signal strength of 98%, but no IP has been assigned to my wireless interface"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by Andrea_44 on 2007-02-20
Hi,

The ESSID and WEP are correctly configured for my wireless adpater.  The Connection Properties indicates a signal strength of 98%. but I duno why no ip address is being assigned to the interface.

Any help will be greatly appreciated!

Cheers~
Andrea

---

### Post by renzokuken on 2007-02-20
have you tried running the command

```
sudo dhclient wlan0
```

(replace wlan0 with the name of your wireless device)

---

### Post by Andrea_44 on 2007-02-20
Thanks for the reply.

I have just tried "sudo dhclient rausb0", but it went on forever.

I also tried "sudo ifdown rausb0" and "ifup rausb0". After I restarted the interface, the essid field in iwconfig has suddenly been left empty (ESSID:""), but i can still see the correct essid in "/etc/network/interface" & in the Networking applet.

How can I set the essid for iwconfig?

The signal strength is still very strong and I am able to do a "iwlist scan" with all the avaiable network listed

Cheers~
Andrea

---

### Post by renzokuken on 2007-02-20
i think you can just run 

```
sudo iwconfig ssid <your_essid_here>
```

---

### Post by chili555 on 2007-02-20
Actually, it's ```
sudo iwconfig rausb0 essid <your_essid_here>
```

essid, not ssid

---

### Post by Andrea_44 on 2007-02-20
Thanks so much guys, it now works! O:)

Cheers~
Andrea

---

### Post by renzokuken on 2007-02-20
lol, thanks chili.

---

