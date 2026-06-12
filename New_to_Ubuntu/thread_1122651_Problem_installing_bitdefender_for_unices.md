---
title: "Problem installing bitdefender for unices?"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-11
I'm trying to install bitdefender for unices in ubuntu but I keep getting the error

```
carl@carl-desktop:~$ sudo sh BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
sh: Can't open BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run

```

what am I doing wrong?

---

### Post by kamitsukai on 2009-04-11
Ok discoverd that I hadnt selected "Allow _e_xecuting file as a program" but now I get this error:

```
carl@carl-desktop:~$ sudo sh carl@carl-desktop:~$ sudo sh BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
sh: Can't open carl@carl-desktop:~$
carl@carl-desktop:~$ sh: Can't open BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
>

```

---

### Post by kamitsukai on 2009-04-11
Silly me....
 
Didn't go to the directory where the file was =]

```
cd /home/carl/Desktop
```

---

