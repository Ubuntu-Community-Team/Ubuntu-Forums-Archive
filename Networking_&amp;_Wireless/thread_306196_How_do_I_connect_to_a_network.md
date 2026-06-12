---
title: "How do I connect to a network?"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by somerandomnerd on 2006-11-24
I've got a Compaq Presario V2000 laptop, which I've been trying to connect over wifi to my desktop PC.

The desktop PC is running Windows XP (for now- as I can't even begin to get the wireless card working under Ubuntu), and has connected fine to the laptop when working under Windows XP.

Now, my wireless card shows up fine in System->Administration->Networking. I've entered the ESSID and network password, but it isn't connecting.

The network card shows up if I do an lshw, so drivers etc. appear to be fine.

If I run iwconfig scanning, I can see the network that I've set up from the Windows PC.

So, the network card appears to be fine- it can see the outside world. Now, the big question- how do I actually **connect **to it?

(Please note that as I don't have an internet connection until this is connected, I can't install anything with Synaptic- downloading packages and tranferring with a USB stick is an option though.)

---

### Post by somerandomnerd on 2006-11-26
Just to give a bit more information, I've gone from getting iwconfig to return "unassociated" (before listing the ESSID etc.) to returning "IEEE 802.11g" (before listing the ESSID etc.) by setting the channel to 11 using iwconfig (the same channel that the network shows up as under "iwlist scanning".) Which I suppose is a start (although the network shows up as b- not g. Don't know if that's an issue...)

Still no sign of an actual *connection* though... I'm sure I'm missing something obvious, so any help would be appreciated.

---

### Post by Jamie Jackson on 2006-11-26
What kind of encryption is the network running? You might want to take baby steps and get an unencrypted connection going first.

---

### Post by NetworkGuy on 2006-11-26
Please post the results of running ```
lspci
``` from a terminal.  This is so we can determine exactly what type of wireless card you are running.

---

### Post by somerandomnerd on 2006-11-26
> **Jamie Jackson said:**
> What kind of encryption is the network running? You might want to take baby steps and get an unencrypted connection going first.

I've tried to get an unencrypted network up and running, and did actually get a connection. (Like you say, baby steps...) However, I have no idea exactly what it was that I did to get connected (literally went back to working on the Windows box after giving up, and saw that it was connected- nothing had come up on the laptop to indicate that something somewhere along the line had worked, so I don't know how to reproduce it, let alone save the settings to make it permanent.)

> **NetworkGuy said:**
> Please post the results of running ```
lspci
``` from a terminal.  This is so we can determine exactly what type of wireless card you are running.

lspci gives me the following (that's relevant- please let me know if there's anything else I should add;)

```
06:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```

lshw gives me the following;

```
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 6
                bus info: pci@06:06.0
                logical name: eth1
                version: 05
                serial: 00:16:6f:aa:a5:41
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 multicast=yes wireless=unassociated
                resources: iomemory:b0107000-b0107fff irq:177
```

So the card seems to be OK, drivers installed etc. etc.

iwlist scanning;
```
          Cell 01 - Address: E6:17:41:E6:1C:41
                    ESSID:"ScottFreeNet"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=95/100  Signal level=-31 dBm  
                    Extra: Last beacon: 116ms ago
```

iwconfig returns the following;

```
eth1      unassociated  ESSID:"ScottFreeNet"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Jamie Jackson on 2006-11-26
The normal command-line way to do it is:

sudo iwup eth1

And you ought to be able to do the same thing from System >> Administration >> Networking by clicking "enable" on the wireless device.

I assume you've tried these things?

Also, could you post the contents of your /etc/network/interfaces file? (Change your WEP key to a fake one before posting, if you'd like.)

Jamie

---

### Post by somerandomnerd on 2006-11-26
> **Jamie Jackson said:**
> The normal command-line way to do it is:

sudo iwup eth1

iwup gives me a "command not found."
Not sure if that was a typo, but "ifup" gives me "interface eth1 already configured".

> And you ought to be able to do the same thing from System >> Administration >> Networking by clicking "enable" on the wireless device.

That's already enabled. I've also disabled the wired connection in there, as I've heard that can interfere.

> I assume you've tried these things?

Also, could you post the contents of your /etc/network/interfaces file? (Change your WEP key to a fake one before posting, if you'd like.)

Jamie

Sure;
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface dls0provider inet ppp
provider dsl-provider


iface eth1 inet dhcp
wireless-essid ScottFreeNet
wireless-key s:3woks

auto eth1

```

---

### Post by Jamie Jackson on 2006-11-26
Yeah, iwup was a typo, sorry.

What happens when you bounce the card with an ifdown followed by an ifup? (Or a *sudo dhclient eth1*)

---

### Post by somerandomnerd on 2006-11-26
> **Jamie Jackson said:**
> Yeah, iwup was a typo, sorry.

What happens when you bounce the card with an ifdown followed by an ifup? (Or a *sudo dhclient eth1*)

Now I think I'm getting somewhere- thanks!
:) 

Went through those commands, then tried the ifdown/ifup again and got a connection.

Rebooted to try to replicate it and... well, after a couple of attempts and some more playing around, came up with this routine to connect;

```

1- sudo iwconfig eth1 mode Ad-Hoc
2- sudo dhclient eth1

```

So that was fantastic- thanks very much for the pointers.

To set it up so that it keeps the correct settings on a reboot... I presumed it was something to do with the /etc/networks/interfaces file, so I added "wireless-mode Ad-Hoc" to the other wireless details and rebooted... The network connected during the boot up, but I still needed to to the "sudo dhclient eth1" command to get an internet connection. I noticed that eth0 had reappeared in the Network settings, so I commented out the "eth0" line in /etc/network/interfaces as I'd heard that could cause problems and presto- a working internet connection on boot up!

Easy when you know how...

And now- ah, Synaptic. How I missed you...

:)

---

### Post by Jamie Jackson on 2006-11-26
Great! \\:D/

---

