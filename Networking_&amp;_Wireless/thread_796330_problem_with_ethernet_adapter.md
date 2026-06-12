---
title: "problem with ethernet adapter"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Afif K fiska on 2008-05-16
I have a SIS ethernet adapter, but in the network device in the network tools ubuntu, i can't configure it, it's show an error message that interface doesn't exist. Same problem when i want to use wireshark, it didn't show any network device. I'm installing my hardy heron with wubi. The strange is, my connection to the local network in my place is connected perfectly, even i can connect to the internet through this device, when i check my network interface, it's show that i use loopback interface (lo) in ubuntu. Is there something way that i can use my ethernet device in ubuntu, not without the loopback interface, but by my ethernet device directly? In other way, how to activated my ethernet device in ubuntu?

Really appreciated for your help

---

### Post by Ayuthia on 2008-05-16
> **Afif K fiska said:**
> I have a SIS ethernet adapter, but in the network device in the network tools ubuntu, i can't configure it, it's show an error message that interface doesn't exist. Same problem when i want to use wireshark, it didn't show any network device. I'm installing my hardy heron with wubi. The strange is, my connection to the local network in my place is connected perfectly, even i can connect to the internet through this device, when i check my network interface, it's show that i use loopback interface (lo) in ubuntu. Is there something way that i can use my ethernet device in ubuntu, not without the loopback interface, but by my ethernet device directly? In other way, how to activated my ethernet device in ubuntu?

Really appreciated for your help
From the terminal try:
```
gksu wireshark
```

---

### Post by Afif K fiska on 2008-05-16
Thank u so much, u help me again, maybe you can give me an advice, which program is the best to monitoring network bandwith for local area network in ubuntu?

Regards


Afif K. Fiska

---

### Post by stewart_12 on 2008-05-27
Hi Everyone, 

I am having the same problem as well. I tried putting the words wireshark in the terminal, after which wireshark starts, it cant find any interfaces in the list even though the network connectivity is normal? IS there any way to fix this?

Thanks for the help!

Stewart

---

### Post by Ayuthia on 2008-05-27
> **stewart_12 said:**
> Hi Everyone, 

I am having the same problem as well. I tried putting the words wireshark in the terminal, after which wireshark starts, it cant find any interfaces in the list even though the network connectivity is normal? IS there any way to fix this?

Thanks for the help!

Stewart

Did you try to do the step in Post #2?  I think there is a way to update the menu entry so that you can add gksu at the beginning also, but I am not sure about how to do this because I am in KDE.

---

### Post by stewart_12 on 2008-05-28
Yep

I tried doing the stuff in post # 2, but it still does not show any network card in the interface.

---

