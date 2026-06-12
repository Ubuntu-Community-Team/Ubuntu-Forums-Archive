---
title: "Error while loading ubuntu"
date: 2004-12-02
forum: Networking &amp; Wireless
---

### Post by Infatuated_iPod on 2004-12-02
After i logged out for the first time and tried to get back in this error came up... " Error inserting shpchp" Then when i got onto ubuntu my network no longer worked... there is an error configuring network, what should i do? :(

---

### Post by adbak on 2004-12-02
Are you talking specifically of "shpchp" and "pciehp"?

If so, here's what I did to skip those FATAL errors:
```
sudo emacs /etc/hotplug/blacklist
```
add "shpchp" and "pciehp" to the bottom of the list, but without the quotation marks and on their own lines.
Save and quit.

That should save some seconds when booting up.

---

### Post by Infatuated_iPod on 2004-12-02
After i got those messages my network no longer work, will that solve this problem too?

---

### Post by Infatuated_iPod on 2004-12-02
Okay, i tried what you said , and then i rebooted ubuntu, the same messages came up twice... plus a new one "hw_random"... the worst part is i cant get any of my networks to work, and ethernet worked before this error. also, when i restart there is an error on the shut down screen that says " Deconfiguring Network Interface (FAIL) ... I have no idea what is going on, but i really miss havin ubuntu.. :(

---

### Post by jdong on 2004-12-02
Hmm, what kind of network card?

Outputs of **ifconfig** **lsmod** **lspci** **cat /etc/networking/interfaces**, please

---

### Post by Infatuated_iPod on 2004-12-02
It worked fine the first time installed it, but now it wont work at all! Do you want me to do that in terminal?

---

### Post by Infatuated_iPod on 2004-12-02
```

lev@lev-88j7rfqf27b:~ $ ifconfig Ismod Ispci cat /etc/networking/interfaces
Ispci: Unknown host
ifconfig: `--help' gives usage information.
lev@lev-88j7rfqf27b:~ $

```

... thats what ahppened.

---

### Post by hndrcks on 2004-12-03
Those are small 'L' not capital 'i'. Small but important difference!

---

### Post by Infatuated_iPod on 2004-12-04
lev@lev-88j7rfqf27b:~ $  ifconfig lsmod lspci cat /etc/networking/interfaces
lspci: Unknown host
ifconfig: `--help' gives usage information.
lev@lev-88j7rfqf27b:~ $


Same thing happens...

---

### Post by Rui Pais on 2004-12-10
No man,
one comand at time:
ifconfig <Enter>
lsmod <Enter>
...
if you want to save a text with the out put, to read more carefully or to post here, do:
ifconfig > ifconfig.txt
lsmod > lsmod.txt
or (note the diferences):
cat /etc/network/interfaces > interfaces.txt

it will show yoy the errors and eventually the causes.

good luck

---

### Post by benkorkor on 2005-01-30
I had this problem also and I fixed it by removing all the information on the interfaces in the /etc/network/interface file except loopback(near the top), then reconfigured the interfaces in "networking configuration," and it worked again. Hope this helps whoever may be having this problem.

---

