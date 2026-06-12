---
title: "WEP key doesn't work"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by ameade on 2007-07-23
Hi there.

When my wireless service requests an encription key, I have tried entering my WEP key (public and hex, like my documentation says), but this isn't accepted.  I have Verizon DSL service, which uses a VersaLink wireless adapter.  I have a dell computer dual booted with Vista, and Vista sees the wireless just fine, also after some effort ubuntu recognizes my WLAN card and works with other wireless networks.  I'm a Linux beginner by the way, so be gentle if I sound ignorant.

The wireless network I set up has a alpha-numeric password as well, but I tried that as a "passphrase" and that didn't work either.  Let me know if you have any suggestions, Verizon has no Linux tech support, the person I talked to couldn't even tell me if the WEP key was hex or ascii, which I found out on my own.

Thanks,
Andrew

---

### Post by lisati on 2007-07-23
Are you using a 64-bit key or 128 bit key?

---

### Post by ameade on 2007-07-23
[RIGHT]
My documentation from Verizon says its a 64 bit key, but when ubuntu asks you for a key, the choice I pick is 64/128 bit hex key.
[/RIGHT]

---

### Post by jdrietz on 2007-07-23
I am having the same problem.  No issue with unsecure connections (actually, have better signal strength than under Windows) but when I try to connect to a WEP-protected network and enter the key (hex 64) it doesn't seem to take.

Hardware:  IBM T42 and 2200BG wireless
Software:  Ubuntu Feisty and Network Manager

---

### Post by kevdog on 2007-07-24
Where are you guys entering this network key??  On a network manager GUI, or in the /etc/network/interfaces file??

---

### Post by ameade on 2007-07-24
I'm entering the key when I click on the upper right icon for wireless networks.  I'm promted for a passphrase or key when I click on my network.  I'm just starting to get used to terminal programs and commands, so let me know if theres something else I should be using (and where to go to learn how to use it if possible).

Thanks alot,
Andrew

---

### Post by kevdog on 2007-07-24
Here is a another way you to do it

Determine your interface name (like eth0, eth1, wlan0, ath0, etc):
```
lshw -C network
```

Find your network card and then look for the section titled logical name

Then 

Backup current configuration
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

```
gksu gedit /etc/network/interfaces
```

Do something similar to the following:
```
auto *interface_name*
iface *interface_name* inet dhcp
wireless_mode managed
wireless_essid *Router_ESSID*
wireless_key *64_bit_hex_key*

```
Save the file and then

```
sudo /etc/init.d/networking restart
```

You might need to reboot
```
sudo shutdown -r now
```

You can try substituting the last command with
```
wireless_key *s:ASCII_key*
```

If you want to try the ascii version of the key

---

### Post by str8line on 2007-08-23
For the Versalink 327W modem/router combination the default WEP key is printed on the bottom of the modem (it is a 10 digit Hex), if you created a WEP Key in the modem GUI, you should use a true hex key as key one in Wireless Security an example would be 6d7964736c....ensure both match at the wireless card in the computer and in the modem.

---

