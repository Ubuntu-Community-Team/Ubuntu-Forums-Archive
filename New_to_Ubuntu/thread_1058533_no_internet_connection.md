---
title: "no internet connection"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by shadowlands on 2009-02-02
Just got computer back from the shop. DC port went out.  Know my problem is my computer will not connect to the net.  I have a laptop and it used to connect to the net without a problem, but now my laptop will not connect to my dsl nor will it connect to the net and it is wired in with a internet cable.

---

### Post by 7mkgw7q on 2009-02-02
Possibly a hardware issue? I know you said you just got it back from the shop, but this throws up more hardware flags for me than software. Are your drivers still installed?

---

### Post by shadowlands on 2009-02-02
how do i check to see if the drivers are still in place?
> **7mkgw7q said:**
> Possibly a hardware issue? I know you said you just got it back from the shop, but this throws up more hardware flags for me than software. Are your drivers still installed?

---

### Post by 7mkgw7q on 2009-02-02
The easiest way is System > Administration > Hardware Drivers. Activated drivers will have a green dot by them. This would probably be more for wireless than for being plugged in. Also, if you can tell me what wireless card you have, I can do some research for you.

---

### Post by shadowlands on 2009-02-02
How do I check for the type of card  have?  "it reads that there are no proprietary drivers in use on this system." " Support for atheros 802.11 wirless LAN cards."
> **7mkgw7q said:**
> The easiest way is System > Administration > Hardware Drivers. Activated drivers will have a green dot by them. This would probably be more for wireless than for being plugged in. Also, if you can tell me what wireless card you have, I can do some research for you.

---

### Post by 7mkgw7q on 2009-02-02
In the terminal, type "sudo lshw -C network" without the quotation marks. there will be a line near the top that says "product." Give me the readout for that line. It is the info we will need for this.

---

### Post by shadowlands on 2009-02-02
it reads that lshw-cnetwork : command can not be found.> **7mkgw7q said:**
> In the terminal, type "sudo lshw -C network" without the quotation marks. there will be a line near the top that says "product." Give me the readout for that line. It is the info we will need for this.

---

### Post by 7mkgw7q on 2009-02-02
It needs to be typed in the way I typed it:

sudo lshw -C network

the spaces need to be there and the -C needs to be capital.

---

### Post by shadowlands on 2009-02-02
AR242X 802.11abgwirless PCI Express Adapter> **7mkgw7q said:**
> It needs to be typed in the way I typed it:

sudo lshw -C network

the spaces need to be there and the -C needs to be capital.

---

### Post by shadowlands on 2009-02-02
Strange it is now working but, i still think that some type of trouble shooting needs to be done.. Do you have any suggestions as to why my laptop would not read the wireless?

---

### Post by 7mkgw7q on 2009-02-02
So is everything working now? I am looking for a resource.

---

### Post by shadowlands on 2009-02-03
-laptop:~$ ifconfig wlan0:1 192.168.2.41 netmask 255.255.255.0
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
> **pontanias said:**
> do ```
ifconfig wlan0:1 192.168.2.41 netmask 255.255.255.0
```

to set your WirelessLan to the right netmask and it should work.

---

### Post by halovivek on 2009-02-03
could you post some more details below.
code
1. sudo lshw -C network
2. ethtool eth0
3. ping -c 4 [www.google.com](www.google.com)
ping -c 4 74.125.43.104
4. cat /etc/resolv.conf
5. cat /etc/network/interfaces
6. route -n

---

### Post by yeats on 2009-02-03
Resource:

[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html")

This happened to my wife's computer too, and it's because of the kernel update that happened over the weekend.  You have to compile the madwifi driver each time it seems, though I used "Method 2" in this guide that has you install linux-backports, so possibly that will avoid this issue in the future.

---

### Post by nothingspecial on 2009-02-03
Recompiling madwifi is actually very easy if you still have the madwifi directory

```
cd madwifi*
```

```
make clean
```

```
make
```
```

sudo make install
```

reboot

If you choose to use the backports method above remember to comment (put a # infront of) ath_pci while adding ath5k to /etc/modules.

I find the madwifi drivers work best but that may just be my machine.

---

### Post by shadowlands on 2009-02-03
I do not understand this? Can you please explain?> **halovivek said:**
> could you post some more details below.
code
1. sudo lshw -C network
2. ethtool eth0
3. ping -c 4 [www.google.com](www.google.com)
ping -c 4 74.125.43.104
4. cat /etc/resolv.conf
5. cat /etc/network/interfaces
6. route -n

---

