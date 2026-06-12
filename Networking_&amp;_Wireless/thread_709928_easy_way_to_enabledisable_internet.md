---
title: "easy way to enable/disable internet?"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by davesec on 2008-02-27
hi!

my work pays for my internet at home, i have a regular ethernet connection and get 300 hours a month; if i use any more i have to pay for it. anyway while that's plenty of time, i tend to leave my computer on a lot and just switched to ubuntu. is there an easy way to disconnect the internet (short of unplugging the ethernet cable or typing in a wrong ip address or something)?

thanks!
dave

---

### Post by Mr. C. on 2008-02-27
You have to bring down the network interface.  Right click the networking icon in the upper right, near the sound icon at the top of the menu bar.  Deselect Enable Networking.

MrC

---

### Post by davesec on 2008-02-28
thank you very much!

---

### Post by davesec on 2008-02-28
actually deselecting 'enable networking' doesn't work at all - i can still surf the internet when it's deselected. anything else?!

---

### Post by The Cog on 2008-02-28
How do they know you're using it? If they're looking for electrical activity like Ethernet link test signals, you may have no alternative other than to unplug the cable.

If they're just counting IP packets, this command (assuming you have no other firewall configuration) should do the trick:
**sudo ifdown eth0**
and 
**sudo ifup eth0**

---

### Post by Mr. C. on 2008-02-28
> **davesec said:**
> actually deselecting 'enable networking' doesn't work at all - i can still surf the internet when it's deselected. anything else?!

Hmmm, it works just peachy for me.  But let me explain what it is doing.  It is removing the routes for networking, so packets have nowhere to go.  The interface is still up, but without routes, there is no network activity that can occur.

Disable the network as I suggested.  Then, open a command window, and type:

```
ping www.google.com
netstat -rn
```

You should see an unknown host error, and no packets will be transmitted.
You should see not route table entries.

If you are not comfortable with this approach, unplug the cable, or in a terminal window, type:

```
ifdown eth0
```

(replace eth0 with the name of your interface, perhaps its wlan0).

MrC

---

### Post by Mr. C. on 2008-02-28
> **The Cog said:**
> How do they know you're using it? If they're looking for electrical activity like Ethernet link test signals, you may have no alternative other than to unplug the cable.[/B]

That isn't happening, I can assure you.

---

