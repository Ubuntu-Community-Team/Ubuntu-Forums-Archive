---
title: "no internet, but it pings"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by rui_pedro on 2014-04-25
I have just installed lattest LUBUNTU, and my pc runs now in dual boot with windows.
1st problem the installation took several hours, with no errors, but a real long time.
2nd problem I have no internet access

I can run Lubuntu with no problems, open all applications, but firefox cannot open any page, it keeps connecting but nothing.
In windows I have no problems, so I believe this is only related to Lubuntu.
After a few days I came back to Lubuntu, I can now open google, and 1 or 2 more websites. All other sites dont oopen, like for example this one or ubuntu.com.
In Xterminal I executed command ping and I can ping most sites that are not opened by firefox.
The software updates from Lubunto also cant connect
I am almost sure the installation took several hours because of this internet issue.

Only thing I ve done untill now was changing MTU values from automatico to random numbers. Didnt help. 

Any tips?

---

### Post by praseodym on 2014-04-25
Hi,

please open a terminal and show these outputs (copy them into a txt file):
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
rfkill list
route -n
cat /etc/resolv.conf
```

---

### Post by rui_pedro on 2014-04-25
on Xterm I cannot copy the output, CTRL+C dont works and I also cant find any menu with copy option.
I also cant make a print screen

could you please help me doing that?

---

### Post by praseodym on 2014-04-25
Run the commands like this in each line:
```

lspci -nnk | grep -iA2 net [COLOR="#FF0000"]>> config.txt[/COLOR]
```
Afterwards you will find a textfile named config.txt in your /home folder

---

### Post by rui_pedro on 2014-04-25
Thanks!
please check here [https://drive.google.com/file/d/0B9FWORL5p3UzQjZhR1lvV0s2eGs/edit?usp=sharing](https://drive.google.com/file/d/0B9FWORL5p3UzQjZhR1lvV0s2eGs/edit?usp=sharing)

---

### Post by praseodym on 2014-04-25
The driver is loaded and an IP address is received. Please edit your cable profile in the network-manager and replace "Automatic" with "1500" (without "") as mtu value. Also "ignore" the IPv6 settings. Save and close. Reconnect via
```

sudo service network-manager restart
```

---

### Post by rui_pedro on 2014-04-26
It didnt work with 1500 MTU, but with 1350 yes. So now I think I have internet ok in my Lubuntu. Thank you for help!
Should I try with different MTU values to get the most optimized connectiion? 
Any place where I can find the correct and exact MTU setting?

---

### Post by steeldriver on 2014-04-26
I think generally you want to use the largest MTU that works

---

### Post by praseodym on 2014-04-26
Check the web for the mtu of your ISP

---

