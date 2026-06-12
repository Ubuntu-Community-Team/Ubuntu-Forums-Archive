---
title: "Really strange network behaviour"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by tommaddox on 2006-10-17
Hi folks!

I have a really strange problem. My network is working for some period of time, ususally one to two hours, and then I am loosing network connection. I thought taht this is the fault of the driver. To solve it I tried reloading the driver module in the kernel:
```

modprobe -r 8139too
modprobe 8139too
```

Well, the result when the network is working is that when I remove the module I have no net connection, and on loading it again I have the net back, so this is usual situation. 
But on the other hand, when the network is down "by itself" before reloading the module it looks that the ping time is infinite, (NIC still has it's IP address). After reloading the module I get a message:

Temporary problem in name resolution

So I guess that it is not the driver problem, but problem of something working on top of the driver. I am not an expert in Linux networking, so I ask you what could it be. DNS maybe? IRQ ? 

Addidtional information:
Laptop Asus A6R
Ubuntu Dapper Drake 6.06, kernel 2.6.15-25
NIC: Realtek 8139
Driver: 8139too , mii
Chipset: ATI 200M, integrateg with graphics

---

### Post by wieman01 on 2006-10-17
This is an ethernet card, right? Not wireless.

BTW: After reloading you also need to restart your network:
> sudo /etc/init.d/networking restart

---

### Post by tommaddox on 2006-10-17
Hi! 

Yes, this is an ethernet card. BTW the strange thing is that as soon everthing is fine the network works fine after reinserting the module. As soon I will have the situation with network I will try your advice. 

BR
Tommaddox

---

