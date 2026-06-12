---
title: "no internet connection"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by richard.blastland on 2010-10-01
i just got this laptop with ubuntu os on it.
i cannot connect to the internet wirelessly
please can anyone help

many thanks
kind regards

rich:(

---

### Post by Legendary_Bibo on 2010-10-01
Could you be more specific on what issues you're having like is your router not showing up, is it not remembering your WEP password, or something.

---

### Post by richard.blastland on 2010-10-01
> **Legendary_Bibo said:**
> Could you be more specific on what issues you're having like is your router not showing up, is it not remembering your WEP password, or something.

i turn the laptop on and go into mozilla.it says page not found.i then look into connections and there is nothing there.i have a wireless card,but nothing else.i have no other os software only ubuntu.i have tried to connect to a new wireless connection but nothing happens.many weeks ago it automatically came on on a auto linksys connection
many thanks for trying to help
kind regards
rich

---

### Post by Hippytaff on 2010-10-01
copy and paste the results of this command from the terminal

```

lspci

```

---

### Post by Legendary_Bibo on 2010-10-01
Sounds like the driver for your wireless card isn't installed. Go into System->Administration-> Hardware Drivers and check to see if it can find any proprietary drivers for your wireless card.

---

### Post by richard.blastland on 2010-10-02
> **Legendary_Bibo said:**
> Sounds like the driver for your wireless card isn't installed. Go into System->Administration-> Hardware Drivers and check to see if it can find any proprietary drivers for your wireless card.



it says there are no proprietary drivers are in use on  this system.

---

### Post by wojox on 2010-10-02
> **richard.blastland said:**
> it says there are no proprietary drivers are in use on  this system.

What does this output? Run it from the terminal

```
lspci | grep -i net
```

---

### Post by richard.blastland on 2010-10-02
> **wojox said:**
> What does this output? Run it from the terminal

```
lspci | grep -i net
```

i have typed that in and i keep getting a message saying 

syntax error near newline?

---

### Post by wojox on 2010-10-02
> **richard.blastland said:**
> i have typed that in and i keep getting a message saying 

syntax error near newline?

Is it a USB device?


```
lsusb
```

---

### Post by richard.blastland on 2010-10-02
> **wojox said:**
> Is it a USB device?


```
lsusb
```

yes it is a usb

---

### Post by gandaran on 2010-10-02
post the full output of these two commands, run them in terminal
```
lsusb
lspci
```
we cant help you without checking what wireless card you have.

---

