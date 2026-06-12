---
title: "Yet another Hardy wireless issue..."
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by CynicX on 2008-05-13
I've been searching for a couple hours on here and jotting down notes but heres the deal.  I recently upgraded to Hardy (today) via online download from Gutsy...I've been trying to learn Ubuntu but havent put much effort into it, just using the web...

Anyway the install went fine but now in network settings I dont have a wireless selection.  I've been reading on here different things to try or do...

Here is the real problem.  I dont have another computer and I cant use a wire, it HAS to be a wireless connection.  I'm currently at the local library and I figured I'd ask while I have access to a computer...

Cliff Notes :

-No wireless network selection

-Computer can not be hooked up to the internet via any means other then wireless

-Dont have install disk because I downloaded Hardy in an upgrade

---

### Post by ugm6hr on 2008-05-13
Did wifi work in Gutsy?

If so, how did you get it to work?

Is your wifi device USB or internal?

What device is it?

If possible, the output of this command would be helpful:
```
lshw -C network
```

If that doesn't list any driver, then:
```
lspci
```

If wifi worked in Gutsy, it may be easier to just reinstall that.

---

### Post by CynicX on 2008-05-13
Yep Wifi worked fine.  All I did was select wireless network in the network setting area and entered all router info SSID, WPA blah blah that old chestnut...

Now I dont have "wireless network".  Just Wired, and Modem.

I'll get you that info you need but you'll have to bare with me because its at my house then I'll need to find a friend with a computer to get back too you...

Thanks for the quick reply though....

---

### Post by CynicX on 2008-05-13
ugm6hr, I did your those commands you had me type and my wireless device was detected

But it says:

-network : UNCLAIMED
description : ethernet controller
blah blah...

What do you think....?

---

### Post by CynicX on 2008-05-13
I also made a mistake.  In network settings it says wired connection and point to point connection not modem (same difference I believe)....This is where it used to say wireless....

---

### Post by Ayuthia on 2008-05-13
Can you check your lspci -nn?  Look for something that has Network Controller or Ethernet Controller.  We need some help in identifying your wireless card so that we can point you in the right direction.

---

### Post by CynicX on 2008-05-13
The network car is made by Antheros Communications Inc.  AR5212/AR5213 Multiprotocol MAC/baseband processor

Thanks for baring with me, I'm a real newb to anything thats not windows...

---

### Post by ugm6hr on 2008-05-14
This card seems to be bit hit and miss in Ubuntu.

[http://ubuntuforums.org/showthread.php?p=4950369#post4950369](http://ubuntuforums.org/showthread.php?p=4950369#post4950369)

---

### Post by CynicX on 2008-05-15
I really appreciate the help guys.  Unfortunately I'm going to need the internet to make this work, so my options are to buy/obtain another computer or goto Windows temporarily to obtain everything I need.

In either case it would be silly for me to stick with Ubuntu if I need to buy something to make something free work OR go with another OS that does work to make one that doesnt work work right...if that makes any sense...

I'm sure a Ubuntu/linux pro could get this thing up and running in seconds but I have no where near the education and experience with it to accomplish this...

Regardless thanks again for the help maybe one day I'll actually have time to dedicate to learning Linux.  But at this point in my life with work, hobbies, and my social life time is stretched to thin....

---

### Post by ugm6hr on 2008-05-16
If it worked in Gutsy - why not go back to Gutsy?

It is unusual that madwifi drivers have stepped backwards...  Hopefully it won't be too long til it gets fixed.

---

