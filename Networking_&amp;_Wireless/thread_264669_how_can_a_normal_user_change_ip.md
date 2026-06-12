---
title: "how can a normal user change ip"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by monkeymartin on 2006-09-25
ifconfig eth0 10.10.1.5

I would like to be able to do this as a normal user how do I chang the permmissions so I can do this 


thanks

---

### Post by bikeboy on 2006-09-25
Simple, as with all admin tasks in Ubuntu, use sudo.
```
sudo ifconfig eth0 10.10.1.5
```

---

### Post by monkeymartin on 2006-09-25
I would like to do this without sudo I am using a launcher to run this program.

I would like to change the permmission or add my user to a group

---

### Post by bikeboy on 2006-09-25
Ah sorry I missed that bit :)
I've had a go but haven't had success so far in finding how to do what you want.

---

### Post by daschl on 2006-09-25
well, for security reasons this would be not a good idea.

as a workaround, you may change your sudoers file (with visudo) and add "nopasswd" at the end. then you'll be able to run the sudo command without typing any password...

---

