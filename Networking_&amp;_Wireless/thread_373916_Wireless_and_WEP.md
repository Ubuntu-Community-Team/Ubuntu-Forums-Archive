---
title: "Wireless and WEP"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2007-03-01
I have searched and searched for an answer to this problem and only found 4 posts here about this problem, which none of them worked. At the moment, I opened up my router (no security) and I can connect no problem. I am using Wi-Fi Radar to connect. I am absulutely psitive that I entered the WEP key correctly, but I can not get an IP when I use WEP. I am not to keep on keeping it setup like this.
Has anyone had true success with a Broadcom 4318 and a Linksys WR54G?
What information do you need in order to help me?
I appreciate any help, but I would like to get any instructions in a step by step and why basis. I am a noob and want to learn!
Thanx!

---

### Post by chili555 on 2007-03-01
First, please compare what sudo iwlist <your_wireless_interface> scan says your essid is to what sudo iwconfig <your_wireless_interface> says it is. DINGO is not the same as Dingo is not the same as dingo. In my experience, all lower case seems, for reasons only the kernel and your router manufacturer may understand, works best. Amend as necessary.

Second, are you using a passphrase or a 26-character string of numbers and letters for a 128-bit WEP key? From man iwconfig: ```
Examples :
                   iwconfig eth0 key 0123-4567-89
                   iwconfig eth0 key [3] 0123-4567-89
                   iwconfig eth0 key s:password
```
So, did you prepend your passphrase with s: ? Also, in my experience, the string of numbers and letters is much to be preferred.

Double check and post back if you get stuck.

---

### Post by lsutiger on 2007-03-01
Please forgive my ignorance!
When I go to the terminal and type in sudo iwlist eth1 I get an error:
Unknown command eth1
When I pull up Network from the system menu, the wireless card is known as eth1
What am I doing wrong?
Thanx in advance!

---

### Post by Floppyjoe on 2007-03-01
Should be"
```
sudo iwlist eth1 scan
```

---

### Post by lsutiger on 2007-03-02
With sudo iwlist eth1 scan the name is the exatcly the same as when I  use iwconfig.
Ok I used :
  iwconfig eth1 key s:<my passphrase>
  turned on WEP on the Router. Can not connect or ping the router.

  iwconfig eth1 key 0123-4567-89etc..
Double checked..had the router screen open on my desktop while intputing the key.
 I then turned WEP on on the router. Rebooted Ubuntu, now  cannot connect.
Turned WEP off on the router, reboot Ubuntu. Now I can connect.
...
{update}
I went to [this post]("http://ubuntuforums.org/showthread.php?p=2236152#post2236152") and got me setup. Thanx for everyones help!!
BTW - When is WPA going to be available? Is that coming in the next edition?

---

