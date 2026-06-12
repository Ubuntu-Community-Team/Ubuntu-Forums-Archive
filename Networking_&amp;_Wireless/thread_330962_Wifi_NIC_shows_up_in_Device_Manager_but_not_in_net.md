---
title: "Wifi NIC shows up in Device Manager but not in network connections"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by Five40 on 2007-01-03
Hello everyone, trying to make the switch but this problem is kicking my butt.

The Dlink DWL-G520 card was recognized during the installation process and shows up in the device manager but it does not show up in network connections. I see only my wired connections.

How can I fix this.

Thanks

---

### Post by encompass on 2007-01-04
Device manager shows the hardware in your computer... not what is installed.
Doesn't sound like your card is supported by default with linux.  I reccommend doing a little searching to see if you have support for your card in linux.
[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)
is a great start... I would bookmark that.

---

### Post by Five40 on 2007-01-04
> **encompass said:**
> Device manager shows the hardware in your computer... not what is installed.
Doesn't sound like your card is supported by default with linux.  I reccommend doing a little searching to see if you have support for your card in linux.
[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)
is a great start... I would bookmark that.


It says it's supported, how do I install the card?

---

### Post by spd106 on 2007-01-04
Can you post the output of **lspci** at a terminal. If it says that it is an atheros card then open the Synaptic Package Manager and make sure that the linux-restricted-modules and linux-restricted-modules-generic packages are installed.

---

### Post by encompass on 2007-01-04
If your running dapper...
[http://doc.gwos.org/index.php/MadwifiDriver](http://doc.gwos.org/index.php/MadwifiDriver)
should do it... just do what it says.
IF your running edgy then you should be able to use the instructions above.  Looks pretty simple for ya.
Good luck!

---

### Post by Five40 on 2007-01-04
Forgot to mention that i'm running 6.10

---

### Post by Five40 on 2007-01-04
> **spd106 said:**
> Can you post the output of **lspci** at a terminal. If it says that it is an atheros card then open the Synaptic Package Manager and make sure that the linux-restricted-modules and linux-restricted-modules-generic packages are installed.
How do I get the "lspci" info. 

1st time linux user forgive me fellas

---

### Post by spd106 on 2007-01-04
No problem, go to Applications -> Accessories -> Terminal then type in the command, or copy-paste.
You should see something like this```
spd106@ubuntu-edgy:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:10.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```
The important part is the last line. 

You can also access this information through the System  -> Admin -> Device Manager, but I suggest you gain some familiarity with the terminal, you may need it later.

Synaptic can be found in System -> Admin  -> Synaptic.

---

### Post by Five40 on 2007-01-06
Everything is fine now. 
I installed the restricted modules

---

