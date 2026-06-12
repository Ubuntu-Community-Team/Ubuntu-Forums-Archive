---
title: "No DHCP Offers - Not encryption problem"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by Crash90 on 2008-03-01
I have been trying to configure my wireless using the guide provided in this forum. I am using WEP 128 bit w/ passphrase on an open connection. Here is what I have done so far:

sudo ifconfig eth1 down  (works fine)

sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig <interface> essid "JLWIRELESS"
sudo iwconfig <interface> key  4d6f6e616432393031666f786d
sudo iwconfig <interface> mode Managed




my problems come @
    sudo dhclient eth1

returns:

```
NO DHCP Offers received
```


I know that this is not an encryption problem. I have entered both the Essid correctly and my passphrase converted to Hex correctly.

Should I go for a static IP address? Am I missing something simple.

What I am using:

Logical drive: eth1

Driver: IPW2200

Open WEP style 128 Bit encryption

Passphrase =  Monad2901foxm

Hex conversion = 4d6f6e616432393031666f786d

ESSID = JLWIRELESS

---

### Post by MikeyXX on 2008-03-01
May I suggest that you remove any extras and try it again? By extras, I mean take the router, reset it to defaults. Then don't set up the wep/wap, just go straight. See if you are getting an ip then. At least you remove any of the things that may affect it. If you don't get an ip then, try going static and see if you get connectivity. If so, add the wep/wap etc and keep the static entry.

btw do you get an ip when you plug directly into that router?
and what happens when you plug into another network source, do you get an ip then?

---

### Post by Crash90 on 2008-03-02
Mikey 

If I plug direct into the router my IP is:   192.168.0.5


If I connect to a different wireless network (unencrypted) : 192.168.10.5


Strange note - The unencrypted network worked like a charm yesterday (it's a neighbors) now today, I can connect for about 20 seconds and it gets dropped.


Going "straight" on my router is not an option. it is my roomie's router andhe is paranoid about leaving it open - he won't for even 15 minutes =(

---

### Post by MikeyXX on 2008-04-16
Ok, just a shot in the dark here....

Can you borrow another wireless card and give it a shot? Perhaps a newer one. Maybe yours hardware is corrupt and it can't do the encryption properly. Perhaps the neighbour next door is using  WPA instead of WPA2 or something like that.

---

