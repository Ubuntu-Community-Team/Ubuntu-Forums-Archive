---
title: "How to connect through wifi in recovery mode"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by ZombiekE on 2006-10-24
Hi:

I need to use aptitude to fix one problem in the recovery mode, however I won't resolve the domain names, since I am not connected to the Internet (I think it is so by default in recovery mode, right?). How can I connect to the Internet? (wirelessly)

Thank you.

---

### Post by az on 2006-10-24
It depends on how you connect in the first place.

If your connection is made using the standard networking tools, you should be online in recovery mode.

How did you configure your wireless?

---

### Post by ZombiekE on 2006-10-24
Thank you very much for replying.

Well, I use a hotspot where I live (student dorm). No WPA/WEP, dynamic IP and DNS's.

I was online in Dapper. However I seem to be offline in Edgy. If I try to install something via aptitude it says that it cannot resolve the names. I don't know if it was properly configured in Edgy since I haven't been able to start the X server (I need the Internet in fact to download a driver that is missing).

I have tried also using the normal mode, without X. Maybe it is more useful there, but still have the same problem.

I have seen I have 2 interfaces when I type ifconfig... eth0 and lo. I think it was the same in Dapper.

I hope this is useful enough. Don't hesitate to ask any more details.

---

### Post by az on 2006-10-25
What is the output of 

iwconfig

---

### Post by ZombiekE on 2006-10-25
Thanks.

It says:

lo no wireless extensions
eth0 no wireless extensions

](*,) 

If it helps, my wifi card is one of those Broadcoms... but it was up and running in Dapper. Maybe I should try the HOW TO again, and check if it's solved. I will try it now.

---

### Post by ZombiekE on 2006-10-25
It seems that when you update the kernel you have to type a command again, loading the driver. But to me it says:

Cannot open input file 2.6.17-10-386

If I can't load the driver, I guess I can't have wireless, and if I don't have wireless I can't install the i810 driver to have the X server. I hope you can help me with this! :)

---

### Post by ZombiekE on 2006-10-25
I had to change the command, deleting `uname -r` but it still doesn't work... I don't see anything in iwconfig or ipconfig.

---

