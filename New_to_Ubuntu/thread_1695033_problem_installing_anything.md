---
title: "problem installing anything"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-02-25
hi everyone
   i am facing a new problem these days whatever i am trying to install whether it be from synaptic or from software center i am getting an error message in the end which is same everytime
here is the message

E: firmware-b43-installer: subprocess installed post-installation script returned error exit status 1

what is it? how to get rid of it?

---

### Post by Kiean on 2011-02-25
What version ru on ? Have u tried reinstall the os?

---

### Post by philinux on 2011-02-25
> **neo_aryan said:**
> hi everyone
   i am facing a new problem these days whatever i am trying to install whether it be from synaptic or from software center i am getting an error message in the end which is same everytime
here is the message

E: firmware-b43-installer: subprocess installed post-installation script returned error exit status 1

what is it? how to get rid of it?

Open a terminal.

```
sudo apt-get purge firmware-b43-installer
```

Then ```
sudo apt-get update && sudo apt-get upgrade
```

Report back any errors.

---

### Post by violinuxer on 2011-02-25
If you do have access to internet, to which I believe this is related (b43 refers to your wireless card) you could try running 

```
sudo apt-get remove --purge firmware-b43-installer
```To clean up you could do:

To clean up:

```
sudo apt-get autoremove
```Hope this helps

If that ends up breaking something:

```
sudo apt-get install firmware-b43-installer
```

Hope this helps!

violinuxer

---

### Post by violinuxer on 2011-02-25
> **philinux said:**
> Open a terminal.

```
sudo apt-get purge firmware-b43-installer
```Then ```
sudo  apt-get update && sudo apt-get upgrade
```Report back any  errors.

Wait a sec- am i missing something or can you use apt-get purge instead of apt-get remove --purge?

violinuxer

---

### Post by philinux on 2011-02-25
> **violinuxer said:**
> Wait a sec- am i missing something or can you use apt-get purge instead of apt-get remove --purge?

violinuxer

Yes indeed. See ```
man apt-get
```

> --purge
           Use purge instead of remove for anything that would be removed. An asterisk ("*") will be displayed next to
           packages which are scheduled to be purged.  **remove --purge** is equivalent to the purge command. Configuration
           Item: APT::Get:: Purge.


---

### Post by violinuxer on 2011-02-25
Ah. Thanks for the clarification. That really could be helpful. :)

Gotta love these forums!

violinuxer

---

### Post by vivek.pandey on 2011-02-25
thanx everyone for your answers
k it seems the problem is solved though not very confident unless things go on well for next few days but anyways what was the reason for such an error being displayed???

---

