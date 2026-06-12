---
title: "Wireless password problems"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by ThuribleBoy on 2009-02-23
I am new to Ubuntu (using 8.10) and hope someone might have an answer

I use an IBM Thinkpad X31 with an external wireless card (Netgear WG511 v2). The card works fine and detects various networks, but will not connect to my home network as it does not accept the password. I use WPA/WPA2 security

I used Network Manager to set up the connection to my home router, using a password (12 digits). It tries to connect but each time fails and presents "Wireless Network Authentication required" box. When I check the password it is using, it has converted it into a much longer alphanumeric code, which maybe hexadecimal. I don't know why it does this and I can't stop it 

I found a thread a few days ago which suggested using the Config Editor to change the network settings, but this only worked temporarily.

Does anyone know why the password is being changed and how I can stop it doing this? Any help gratefully received.

---

### Post by ptn107 on 2009-02-23
Check your router to make sure you have set up WPA/WPA2 correctly.  If your configuration is correct it should pop up a box similar to the attached 'wpa.png'.  If your getting a box that looks like the attached 'wep.png' then your not configured for WPA/WPA2.  (WPA/WPA2 passphrases *should [but don't have to]* be 63 characters long).

I like _[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)_ because it will generate new pass-phrases every time the page gets refreshed.

Edit: You should also get rid of any saved/attempted passwords for the wireless connection by right-clicking the network manager applet in the panel, clicking 'Edit Connections...', selecting wireless, and deleting your access point from the list.

---

### Post by ThuribleBoy on 2009-02-24
Thanks for your reply.

I do get the same screen as the wpa.png that you included. I can't get rid of the security as other computers use the network. However, every time I clear the password and over write the new once, it converts within Ubuntu (or somewhere) into hexdecimal which my router does not recognise.

I have deleted the conenction several times and replace dit and it still does this.

Any other ideas?

---

### Post by ptn107 on 2009-02-24
My WPA2 passphrase is a 63 characters/504 bits.  In Ubuntu it is also stored as a hex passphrase just like yours is.  This would lead me to double check the passphrase entered into the router settings.  I would also clear out any saved passwords from network manager as above, but also this time removing any saved passwords from Accessories -> Encryption and Keyrings (then click the password tab and remove them).  Other than that it's beyond me.

---

### Post by Peter09 on 2009-02-24
Note that although you enter a clear text password the system converts it to what appears to be a random string, this is normal. You do not see your password again as clear text.

This could be a wireless driver problem.

Can you post the output of

```
lshw -C network
```

---

### Post by carml on 2009-02-24
I don't know if it may help, I saved the configuration profile for my wireless card,so I have only to select which profile (which connection either cable or lan) I want to use.
Try to go to System->Administration->Network and edit the tab wlan,hen save the configuration by clicking on the floppy icon.

---

### Post by ThuribleBoy on 2009-02-25
Thanks very much ptn107. Clearing out the password and encryption keys did the trick. It must have been reading an old verion or one that had been corrupted.

If nothing else, I now know how to resolve if it recurs.

Much appreciated.

---

### Post by ThuribleBoy on 2009-02-25
Thanks for the offer of help, Peter09. As you will see from my previous note, I seem to have resolved by deleting all passwords and encryption keys.

This is a screen shot of the resulst of the command line you asked for, in case it is of interest.

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:0d:60:cb:63:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 03
       serial: 00:14:6c:87:b7:cd
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg511v2 driverversion=1.53+NETGEAR,09/17/2004,3.1.0.19 ip=192.168.0.4 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:2c:6f:9d:17:60
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by ThuribleBoy on 2009-02-27
Well, it would seem that my relief was short-lived. Nothing I can do seems to get me back into the world of wireless. I have tried all the above and a few other things from various forums. My password remains resolutely hexadecimal despite all my efforts. 

I am afraid I am just not technically proficient enough for Ubuntu. Back to Windows, I fear, which is such a pity as Ubuntu has so much to offer (except wireless)! Either that, or I just remain connected by wire. Somehow that seems so retrograde.

---

### Post by arm-c on 2009-02-28
Is the network broadcasting the wireless ID (SSID)?  If not, that will prevent NetworkManager from connecting (in my experience).  If that is the case, install wicd -- note it will remove network manager from ubuntu, but it works.  Did it on my wife's computer (her school network is hidden) and it had excellent results.  Also fixed another problem of wireless not reconnecting after hybernate/suspend recovery.

---

