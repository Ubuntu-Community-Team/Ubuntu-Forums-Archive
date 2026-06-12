---
title: "Network Manager wont let me set a static address 14.04"
date: 2016-04-17
forum: Networking &amp; Wireless
---

### Post by MadMax2 on 2016-04-17
I have all the settings from the internet provider but as soon as I select *Manual* the save button greys out.

I configured the modem via Windows and I have a connection.

I have reinstalled Ubuntu but is no internet connection. Previous reinstalls worked ok?

---

### Post by chili555 on 2016-04-17
Typically, the 'Save' button will be greyed out if Network Manager believes you have entered insufficient or maybe incorrect information. At a minimum, you will need the address, netmask, gateway and DNS nameservers. Do you have all of them?

Click 'Add' and fill in the blanks.

---

### Post by MadMax2 on 2016-04-17
Yes, the settings are correct but the save button greys as soon as I select *manual* (before entering the settings).

Same hardware; same distro on dvd: worked last time for months and months 
Max@ox:~$ lspci -nnk | grep net -A2 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06) 
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000] 
	Kernel driver in use: r8169 
Max@ox:~$

---

### Post by chili555 on 2016-04-17
After you select 'Manual', you must click 'Add' in order to add the settings. Did you try that?

---

### Post by MadMax2 on 2016-04-17
Yes, I have put in all the settings [select Address > Add ;Select Net mask >Add ; Select Gateway> Add then DNS and alternate DNS separated by a comma].
Just tried it again: *Save* is greyed throughout. The cable works on laptop.

---

### Post by steeldriver on 2016-04-17
What values are you entering, exactly? I think it does some basic validation e.g. it won't save if the netmask doesn't make sense

---

### Post by MadMax2 on 2016-04-17
Address given by provider xxx.xx.xxx.204
Netmask 255.255.255.0
Gateway xxx.xx.xxx.1
DNS 203.97.78.43,203.97.78.44

---

### Post by chili555 on 2016-04-17
Did you try the DNS without a comma? Please see my example. As you can see, 'Save' is available.

[ATTACH=CONFIG]268439[/ATTACH]

---

### Post by MadMax2 on 2016-04-17
[QUOTE=chili555;13471683]Did you try the DNS without a comma? Please see my example. As you can see, 'Save' is available.

Yes Save remains greyed.

---

### Post by MadMax2 on 2016-04-17
Screenshot

---

### Post by chili555 on 2016-04-17
It has been a loooonnngg time since I ran 14.04 but I'm wondering why the entered numbers all line up under 'Address' instead of aligning as in my attachment. After you enter the address, doesn't the space to enter data, the netmask,  move over?

Please see: [https://www.youtube.com/watch?v=Hvi2cTMmTq0](https://www.youtube.com/watch?v=Hvi2cTMmTq0)

---

### Post by steeldriver on 2016-04-17
I agree with Dr Chili - it looks to me like you've 'Add'ed 3 addresses, rather than 1 address + 1 netmask + 1 gateway

---

### Post by MadMax2 on 2016-04-18
When I did previous installs the network was up and running attached to the router and so needed no setting up so the PC is at a lower level?
I don't understand that bit but maybe that static setting only applies to the router and the router applies DHCP?
Original issue is Internet stopped working: maybe it is the router?
I'm trying to set up the router: Cable from broadband modem to WLAN on router > Ethernet to laptop. Windows 10 fault analyser says *Default Gateway is not available*. Only *on* light active on router.

---

### Post by MadMax2 on 2016-04-18
My settings were wrong [all in Address column]. I fixed that but *still* wont let me save.

---

### Post by chili555 on 2016-04-18
> **MadMax2 said:**
> My settings were wrong [all in Address column]. I fixed that but *still* wont let me save.Do you have address, netmask, gateway *and* DNS as in my YouTube? You need all four and in a format that Network Manager thinks is credible; for instance, it will accept a netmask of 255.255.255.0 but not 256.255.255.0 and so forth.

---

### Post by MadMax2 on 2016-04-18
Yes the settings are correct as I have used them in the laptop.

---

### Post by MadMax2 on 2016-04-19
I bought a new router and connected it without any problems (the static setting is on the router).

---

