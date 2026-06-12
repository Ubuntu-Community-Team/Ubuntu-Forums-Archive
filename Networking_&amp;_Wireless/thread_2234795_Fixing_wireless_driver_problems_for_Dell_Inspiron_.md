---
title: "Fixing wireless driver problems for Dell Inspiron 9300"
date: 2014-07-17
forum: Networking &amp; Wireless
---

### Post by richard72 on 2014-07-17
Hi,

I am a new (and inexperienced) LUBUNTU user. I am trying to activate my wireless card.  I have interrogated the system using: 

```
*lspci -nn -d 14e4*
```System responds [I]: ```
03.00.0 Network controller [0280]: Broadcom Corp BCM4309 802.11abg wireless Network Controller [14e4:4324] (rev 03)
```

[/I]Then enter[I]: ```
sudo apt-get update
```

 [/I]System asks for password ?  Upon entering any character system freezes.  I would appreciate any assistance I can get. Thanks

---

### Post by QIII on 2014-07-17
Hello!

When you say that the system freezes, do you mean that no characters appear in the terminal when you start typing your password?

---

### Post by richard72 on 2014-07-17
That's right.

---

### Post by QIII on 2014-07-17
That is a security feature of most Linux distros.

Your keystrokes are being accepted, but nothing is echoed in the terminal.  Just enter your password carefully and press enter.

---

### Post by varunendra on 2014-07-17
..However, a simple update won't fix the wifi problem for this card -
> **richard72 said:**
> ```
03.00.0 Network controller [0280]: Broadcom Corp BCM4309 802.11abg wireless Network Controller **[COLOR="#FF0000"][14e4:4324] (rev 03)[/COLOR]**
```

You will need to install the firmware for this card, the easy and simple method for which is here : [http://ubuntuforums.org/showpost.php?p=13039309](http://ubuntuforums.org/showpost.php?p=13039309)

If the first command "apt-get purge..." suggested in the post returns any errors, you can safely ignore it and move to the next two commands. The driver will work automatically after a reboot.

---

### Post by richard72 on 2014-07-17
Thanks. The driver appears to work OK. Have connected with network after switching hardware on and configuring "hidden network" option. Thanks again for your help.

---

