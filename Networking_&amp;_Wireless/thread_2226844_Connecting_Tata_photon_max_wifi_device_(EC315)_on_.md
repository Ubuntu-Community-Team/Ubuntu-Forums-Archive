---
title: "Connecting Tata photon max wifi device (EC315) on ubuntu 12.04"
date: 2014-05-29
forum: Networking &amp; Wireless
---

### Post by Arjun_Mayilvaganan on 2014-05-29
I've searched everywhere and yet have not found a solution for connecting the above mentioned devices on ubuntu 12.04.
The predecessor of the device all worked perfectly well with ubuntu. So, i guess this too should. The matter is that only windows and mac drivers came along with the device on plug and play. Someone please help me on the connection.

---

### Post by praseodym on 2014-05-29
Please show the terminal outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
pccardctl info
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
rfkill list
```

---

### Post by anj2 on 2014-08-28
[h=1][SIZE=2][hey i am also trying to connect Tata photon max wifi device (EC315) on ubuntu. were you able to do it?]("http://ubuntuforums.org/showthread.php?t=2226844")[/SIZE][/h]

---

### Post by Arjun_Mayilvaganan on 2014-08-30
Very much thank you for your instantaneous response. I'm sorry that i couldn't respond immediately inorder for you to help me.
Anyhow, the problem has been solved now. :)

---

### Post by QIII on 2014-08-30
Hello!

Would you be so kind as to share how you solved this so that others with the same problem can find the answer?

Thanks!

---

### Post by Arjun_Mayilvaganan on 2014-08-30
> **anj2 said:**
> **[SIZE=2][hey i am also trying to connect Tata photon max wifi device (EC315) on ubuntu. were you able to do it?]("http://ubuntuforums.org/showthread.php?t=2226844")[/SIZE]**


Yes, the Tata Photon max wifi device (EC315) works fine on my ubuntu now.
Make sure your ubuntu is upto date. But, one thing i'm experiencing now is, if i connect the device after i turn on the laptop/Desktop, internet gets connected via wifi.
But, if the device is connected even before turning the computer ON, and then i turn it on. Voila! I could use the device in an ethernet form. :)
Good Luck.

---

### Post by Arjun_Mayilvaganan on 2014-08-30
> **QIII said:**
> Hello!

Would you be so kind as to share how you solved this so that others with the same problem can find the answer?

Thanks!
Actually i didn't take extra effort in solving the problem. I just made a software update on my Ubuntu computer and that's it. The problem got solved itself. :)

---

### Post by anj2 on 2014-08-30
What software update did you make?

---

