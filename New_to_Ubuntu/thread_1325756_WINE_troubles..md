---
title: "WINE troubles."
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Azatos on 2009-11-13
On 9.10 no problems until I tried to get WINE.

Followed the directions on the website added it to my software source.  I clicked the link that the wine site gave ```
apt://wine
``` and when I go to install it gives me the error.

"Could not apply changes!  Fix broken packages first."

What packages?

---

### Post by durand on 2009-11-13
Open a terminal (Applications > Accessories > Terminal) and type in:
```
sudo dpkg --configure -a 
```

Copy and paste the errors if there are any.

---

### Post by Azatos on 2009-11-13
```
dpkg: status database area is locked by another process
```

---

### Post by coldReactive on 2009-11-13
> **Azatos said:**
> ```
dpkg: status database area is locked by another process
```

Open system monitor and kill anything like synaptic, etc.

---

### Post by durand on 2009-11-13
You have another application installer program running. Something like Synaptic Package Manager, Add/Remove programs, Ubuntu Software Center. You need to close them before running this command.

---

### Post by Azatos on 2009-11-13
I didn't find any of those running on system monitor so I restarted and used the same command.

This time there was no output, trying to install again gave me the same error however. checked the command again and there was still no output.

---

### Post by durand on 2009-11-13
Try ```
sudo apt-get -f install 
```

---

### Post by Azatos on 2009-11-13
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 libnss3-dev linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Did nothing running the command mentioned in the output gave me.
```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

I made myself root and it is still same result.

---

### Post by durand on 2009-11-13
Sorry, I'm not sure I understand what you mean. It looks like you don't have any errors anymore. Try installing wine now.
```
sudo aptitude install wine
```

---

### Post by Azatos on 2009-11-13
Thanks installed perfectly!

---

