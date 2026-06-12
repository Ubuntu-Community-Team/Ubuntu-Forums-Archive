---
title: "[SOLVED] Can't connect to internet."
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by Canikeo on 2008-08-20
I'm completely new to this, I installed Ubuntu on my windows xp system and started it up and all, everything was going fine until it came to connecting to the internet. Both Ubuntu and Windows can't connect anymore, on ubuntu it doesn't even see an ethernet connection or whatever and on windows in Network Connections my Local Area Connection has disappeared completely and in my drivers the only thing that shows up under my network is Hamachi.

I'm currently on a friends PC which is connected to my router and it obviously can still connect.

Any help? What information do you need?

---

### Post by bitninja on 2008-08-20
You know how there are those little lights that blink right next to your ethernet port usually? One of them should be on solid, and with network activity the other one should blink. If neither of these are on, turn of the computer completely, then switch off the power supply. Wait a few seconds and turn everything back on, it should work again in Windows. When you next start up Ubuntu, it may or may not work. I had that issue with a machine of mine, although with the latest kernel and updates it seems to have been fixed after a reinstall. What motherboard/chipset/LAN chipset are you using in this particular machine?

---

### Post by prshah on 2008-08-20
> **Canikeo said:**
>  Both Ubuntu and Windows can't connect anymore, on ubuntu it doesn't even see an ethernet connection or whatever and on windows in Network Connections my Local Area Connection has disappeared 


Seems like an IRQ conflict; there is almost no other situation in which the ethernet port will not be seen.

Post the outputs to the following commands from Ubuntu's terminal (Application-Accessories-Terminal)

```

dmesg | grep -i ethernet
dmesg | grep -i eth0
dmesg | grep -i conflict
sudo lshw -C network
lspci -v | grep -i -A 5 -B 2 ethernet

```

---

### Post by Canikeo on 2008-08-20
Thanks for the help guys, but we got it working. Flashed the bios and all is well now :D

---

### Post by prshah on 2008-08-20
> **Canikeo said:**
> Thanks for the help guys, but we got it working. Flashed the bios and all is well now :D

OK! Please mark the thread solved; click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

