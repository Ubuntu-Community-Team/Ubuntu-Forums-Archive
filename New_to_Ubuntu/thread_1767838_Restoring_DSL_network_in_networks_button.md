---
title: "Restoring DSL network in networks button"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by Channi on 2011-05-26
Hi everyone!!
I tried connecting to ADSL PPPOE connection from terminal using ```
pppoeconf
```
and then killed them all with ```
poff -a
```
but it also has removed the DSL connections from the Graphical networks button (first on top right of screen) and I have to use pppoeconf everytime I log in. 
I couldn't find a way to get the option back. I tried making new connection using GUI, but nothing work.......Can anybody help to get the options back again.

---

### Post by dineshs on 2011-05-26
Run```
gksudo gedit /etc/network/interfaces
```
Let the file contain only the following lines (please backup the existing file before editing)
```
auto lo
iface lo inet loopback

```
Restart PC

---

