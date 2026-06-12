---
title: "Wvdial conf and setup"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by elliotn on 2009-01-07
Guy I manage to install wvdial, i connected my samsung j750 and rund wvdialconf then I notice that my fone is detected, but when i try to edit etc/wvdial.conf to write my phone namba, username and password but I get the popup saying I dont have the rigths to edit it. What shall me do

---

### Post by stanz on 2009-01-10
Hummm....I don't recall needing special privileges to do that.
Open your terminal and try:
```
sudo nano /etc/wvdial.conf
```
or
```
sudo gedit /etc/wvdial.conf
```
type the root password- when asked,
either one should do it for ya, it's just different editors.

What version of Ubuntu you have installed?
Your own pc? or shared & other users?

Hope it helps....  :)

---

