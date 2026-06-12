---
title: "How do I make windos boot first using Grube"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Kevi Stubbs on 2009-01-23
I have installed Ubuntu on a windows Xp system using the grub duel boot utility.
The problem is my family use windows xp and when they boot up unattended the computer boots into Ubuntu.
Can I change the firt option on the list to Windows xp
Kevin Stubbs

---

### Post by taurus on 2009-01-23
Edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and change the **default 0** (near the top) to whichever entry for windows.  Remember, each _title_ is counted as 1 and you start counting the first entry a 0.

In other words, if windows is the fifth entry, then change the 0 to 4.

```
default 4
```

---

### Post by philinux on 2009-01-23
Install startupmanager. It's a real easy gui to change all sorts of grub stuff.

Either install from synaptic or 

terminal

sudo apt-get install startupmanager

The menu item appears in system>admin

---

### Post by whoop on 2009-01-23
in terminal
```

gksudo gedit /boot/grub/menu.lst

```
Find the line that says: default		0
Change the 0 to the desired value. Note the 0 indicates the first entry in the list, so 1 will be the second etc.

---

### Post by Kevi Stubbs on 2009-01-24
> **taurus said:**
> Edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and change the **default 0** (near the top) to whichever entry for windows.  Remember, each _title_ is counted as 1 and you start counting the first entry a 0.

In other words, if windows is the fifth entry, then change the 0 to 4.

```
default 4
```

No luck with that
A page opened with heading on it"menu.1st (boot/grub)-gedit:
Near the top left there was a tab "menu 1st" wiyh an x next to it.
Nothin about "defaault 4"

---

### Post by Kevi Stubbs on 2009-01-24
Re: Startup manager
It asks me for "sudo password"

---

### Post by chamber on 2009-01-24
> **Kevi Stubbs said:**
> Re: Startup manager
It asks me for "sudo password"

And what happens when you put  your password in?

---

### Post by Elfy on 2009-01-24
> **Kevi Stubbs said:**
> No luck with that
A page opened with heading on it"menu.1st (boot/grub)-gedit:
Near the top left there was a tab "menu 1st" wiyh an x next to it.
Nothin about "defaault 4"

It's not menu.1st - it's a lower case L

> It asks me for "sudo password" do you mean the apt-get install asks for password?

The password you need is your own normal one - ina aterrminal it won't look like you're typing - but it's there.

---

### Post by Kevi Stubbs on 2009-01-24
> **forestpixie said:**
> It's not menu.1st - it's a lower case L

do you mean the apt-get install asks for password?

The password you need is your own normal one - ina aterrminal it won't look like you're typing - but it's there.
Thank you problem solved by spelling lst with a lower case L instead of one.

---

