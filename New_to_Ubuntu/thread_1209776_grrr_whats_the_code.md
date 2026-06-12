---
title: "grrr whats the code?"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by Darkoblivion2 on 2009-07-10
im sorry, i have searched and cannot find it...

whats the sudo code in terminal to be able to play flash and stuff?

something about unrestricted or unregistered...

thanx in advance!

---

### Post by credobyte on 2009-07-10
```
sudo apt-get install ubuntu-restricted-extras

```

---

### Post by Darkoblivion2 on 2009-07-10
yup thats the one! tyvm

now... when i when i run terminal, it asks me for my password, i put in my username's password, and it says sorry incorrect... whats the deal with that?

---

### Post by credobyte on 2009-07-10
> **Darkoblivion2 said:**
> yup thats the one! tyvm

now... when i when i run terminal, it asks me for my password, i put in my username's password, and it says sorry incorrect... whats the deal with that?

Hm, then enter it until "accepted" message ( there's no such a message :D ) appears. Oh, and .. are you a sudoer ( [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers) ) ?

---

### Post by porchrat on 2009-07-10
As was mentioned previously if you aren't a sudoer you can't use sudo.

Also, if you can't figure out how to do it through the terminal then just use the synaptic package manager (you'll find it under the "System" --> "Administration" menu). Synaptic package manager is vasically a graphical version of the apt-get program. Meaning that you can merely open synaptic package manager and do a search for the "ubuntu-restricted-extras" package (use the find/search function I forget the actual name) and then click the checkbox next to it and select "install".

Keep in mind that you will need an internet connection because synaptic and apt-get actually retrieve the package from the internet and install it for you (probably not a problem considering you are posting on ubuntuforums but I thought I should point it out).

---

### Post by kostkon on 2009-07-10
This [how-to]("http://www.psychocats.net/ubuntu/installingsoftware") may help.

---

