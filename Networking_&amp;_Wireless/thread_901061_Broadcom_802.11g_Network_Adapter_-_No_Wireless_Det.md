---
title: "Broadcom 802.11g Network Adapter - No Wireless Detection"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by A4orce84 on 2008-08-26
Hey Everyone,


I finally was able to install Ubuntu on to my Dell Inspiron E1405, but my wireless card isn't working.

I have the Broadcom 802.11g Network Adapter according to Windows, and did some searching but got really confused with the wrappers and "edgy" comments.

If anyone can help a total newbie step-by-step, or refer me to a good writeup on how to get it working, I would appreciate it GREATLY. Thanks! =)


--A4orce84

---

### Post by nickdbliss on 2008-08-26
you will need to have your windows drivers handy for this method to work. Get them and have them extracted in a folder.

[http://ubuntuforums.org/showthread.php?t=827799](http://ubuntuforums.org/showthread.php?t=827799)

---

### Post by A4orce84 on 2008-08-26
Does anyone know the correct driver to use for a Dell Inspiron E1405?

It says Broadcom driver, but not sure which one to grab

---

### Post by nickdbliss on 2008-08-26
> **A4orce84 said:**
> Does anyone know the correct driver to use for a Dell Inspiron E1405?

It says Broadcom driver, but not sure which one to grab

Go to application>accessories and open the terminal.
In terminal type:
lshw -C network

give the output.You will know which card you have.

---

