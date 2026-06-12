---
title: "network cable"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by alishoojaa on 2010-05-23
hi for any one
please can any one help me their is something
incredible happened with my computer
i have windows xp on my pc and i have install ubuntu 
9.04 and then 10.4
the problem when i log in ubuntu it's work very well
but when i try to go back to xp 
the network cable give me a cut singe
it's mean no cable plunged in  
when i remove the bios battery the xp work again
this problem happened every time i log in to ubuntu 
i try to upgrade the bios and nothing happened
my mainboard is asus P5LD2-X
if any one can help me please do it 
thanks in advance

---

### Post by spikoley on 2010-05-24
Does this happen when you reboot?  What happens when you completely shut down from Ubuntu then reboot into Windows?

---

### Post by alishoojaa on 2010-05-24
> **spikoley said:**
> Does this happen when you reboot?  What happens when you completely shut down from Ubuntu then reboot into Windows?

Thank you 
this happened when i rebootand when i completely shut down from Ubuntu then reboot into Windows
it is what you need to get a loosen cable to login one time
to ubuntu and every ting you do it no network cable until
i must to remove the bios battery when the computer is plunged out
form ac outlet 
its too strange i have an other computer and every tinge ok
thank you again

---

### Post by 3rdalbum on 2010-05-24
You know when you open up a terminal and it prints something like:

```
chris@chris-desktop:~$
```

The first part is the username, the bit after the @ symbol is the **host name**.

If you boot up an Ubuntu live CD, the terminal should print:

```
ubuntu@ubuntu:~$ 
```

If the bit after the @ is the same as what it is when you're using your ordinary installed system, then I think I know what your problem is.

Your router is remembering your Ubuntu's hostname, and delivering it back to the Windows computer (which has its own hostname that does not get sent to the router).

The solution would be to change the Windows hostname to match the Ubuntu one, or vice-versa. I don't know how to see Windows' hostname or change it, but you can change the Ubuntu hostname by modifying these files:

```
/etc/hostname
/etc/hosts
```

The first file is self-explanatory. But with the second file, it will read something like this to begin with:

```
127.0.0.1	localhost
127.0.1.1	chris-desktop

```

The bit after "127.0.1.1" (in my example, it's chris-desktop) is the hostname too. You must change this to the new hostname otherwise Things Will Break.

---

### Post by Detonate on 2010-05-24
What would happen if he set up his Ubuntu to use a static IP, and left his windows with DHCP or set up a different static IP?  Would that fix his problem?

---

### Post by alishoojaa on 2010-05-25
Hi 
thanks for any one try to help me
the user name doesn't have any strange character 
and i am install the ubuntu from windows (inside it)
and i have an other computer "older" one and i have
install ubuntu inside windows and every thing ok
it is only when i login ubuntu and go back to windows
the network cable (like) unplugged 
and i cant solve the problem until remove the bios battery 
thanks for all
Ali

---

