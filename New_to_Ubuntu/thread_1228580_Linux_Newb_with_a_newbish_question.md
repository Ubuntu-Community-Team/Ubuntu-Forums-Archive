---
title: "Linux Newb with a newbish question"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by virtualsamana on 2009-08-01
I love ubuntu and i am very greatful that there is this forum. I am having trouble with being unable to connect to my wireless home network after I suspend Ubuntu. I found a solution on the Ubuntu release notes but have no idea how to execute it. 


"Wireless devices that use the ath_pci kernel driver, such as the Atheros AR5212 wireless card, will be unable to connect to the network after using suspend and resume. To work around this issue, users can create a file /etc/pm/config.d/madwifi containing the single line:  
 SUSPEND_MODULES=ath_pci  This will cause the module to be unloaded before suspend and reloaded on resume."

---

### Post by Nburnes on 2009-08-01
All you have to do is create a file that says exactly that?

---

### Post by Buce on 2009-08-01
Pull up a terminal: Applications -> Accessories -> Terminal

Then type

```
sudo echo 'SUSPEND_MODULES=ath_pci' >> /etc/pm/config.d/madwifi
```

Hope that works.

---

### Post by Buce on 2009-08-01
Oh wait, that won't work.

Try:

```
 gksu gedit /etc/pm/config.d/madwifi
```

After entering your password, this should open up a blank text file. Paste

```
SUSPEND_MODULES=ath_pci
``` into it.

---

### Post by Nburnes on 2009-08-01
^^Much better help than me:KS

---

### Post by Buce on 2009-08-01
Didn't mean to step on your toes. You posted as I was typing.

---

### Post by virtualsamana on 2009-08-01
Thanks so much for the help. Unfortunately, it didn't seem to solve the problem. Does anyone know how I can check which driver I am using for my wireless card. I forget which one I installed.

---

### Post by jacklinux on 2009-08-01
Should be in the hardware device manager. Least all mine was.
i am also on a laptop/wireless and i had the problem as you, i just booted the update manager and it said there was a new realease so i downloaded installed and poof, i was wireless however when i went back to MAC it didn't work. so i had to remove ubuntu and put it on my Windows machine to work correctly.

---

### Post by colau on 2009-08-01
> **virtualsamana said:**
> Thanks so much for the help. Unfortunately, it didn't seem to solve the problem. Does anyone know how I can check which driver I am using for my wireless card. I forget which one I installed.
Do you find anything with this?
```

lspci | grep net

```

---

### Post by wojox on 2009-08-01
```
sudo lshw -businfo
```

This may help as well:
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by virtualsamana on 2009-08-01
Thanks for the help guys. I will keep trying. It appears that I am having some additional issues with suspend also not saving mouse and power preferences.

---

