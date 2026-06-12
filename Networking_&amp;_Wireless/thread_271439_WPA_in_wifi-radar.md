---
title: "WPA in wifi-radar"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by Melcar on 2006-10-04
I already did a search but found no real answer to this.  How do you go about enabeling WPA with wifi-radar?  Network manager does no work on my Xubuntu laptop (it does not detect the card:-? ).  There is this entry under WPA which requires you to enter a driver, but which one?

---

### Post by jimbob on 2006-11-13
Having same problem.

How do I tell it to use WPA-PSK and TKIP encryption which I use on my router?

There doesn't seem to be a lot of usage expertise out there.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by littletinman on 2008-02-22
Same here. I can't connect to WPA-PSK or any other secure networks. I have an atheros chipset and can only connect to non secure networks in Wifi Radar. WICD won't work.

---

### Post by wieman01 on 2008-02-23
Then it is most likely a problem relating to the Atheros driver. It should not have anything to do with WICD or Wifi-Radar. You might have to use "ndiswrapper" instead or find another driver for your card. Post here if you need more advice.

---

