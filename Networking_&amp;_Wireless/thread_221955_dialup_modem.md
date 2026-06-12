---
title: "dialup modem"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by paul555 on 2006-07-24
Hi all i just installed ubuntu dapper 6.06 and i want to connect to the internet throw an external dialup modem.I checked the networking settings from system menu and i find there the modem.I edit the properties writing the phone number and the account username and password tried then to activate it but no luck.In windows i can connect but i also must have unchecked the waiting for dialtone button.Any suggestions?

---

### Post by shultzjr on 2006-07-24
Hi all i just installed ubuntu dapper 6.06 and i want to connect to the internet throw an external dialup modem.I checked the networking settings from system menu and i find there the modem.I edit the properties writing the phone number and the account username and password tried then to activate it but no luck.In windows i can connect but i also must have unchecked the waiting for dialtone button.Any suggestions? 
================================================================
Several questions:
1. What brand/model is the modem?
2. How are you physically connecting the modem to the computer?
3. Did you go through pppconfig
4. Did you use pon/poff to do the dialing/disconnecting?

later,
charles.....

---

### Post by paul555 on 2006-07-24
1)The modem is an external microcom serial modem 
2)It is attached to first serial port (/dev/tty/S0)
3)I didn't use pppconfig
4)I didn't use pon/poff for dialing/disconnecting

I just went to Desktop -> Adminisration -> Networking and there i configured the modem.I entered the right settings but with no success.Then i find wvdial i configure it but when i tried to connect i get that :
```
wvdial : disconnect no dial tone detected
``` 
so as i suppose i have to configure to not looking for dialtone.Any ideas?

---

