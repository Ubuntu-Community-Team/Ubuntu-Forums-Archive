---
title: "wireless card driver needed"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by norbert26 on 2009-11-17
i have an acer 5517-9779 and installed ubunto 9x latest version (i forgot the extact number). i can connect to the internet fine using cat 5 eithernet but i need a driver for my wireless card. where can i get a driver ?

---

### Post by fooman on 2009-11-17
did you check in system > administration > hardware drivers?

if nothing there,  open up a terminal and type the following into it:

```
lspci
```

then post the output back here.  that will give us the info needed to help you further.

---

### Post by t0p on 2009-11-17
> **norbert26 said:**
> i have an acer 5517-9779 and installed ubunto 9x latest version (i forgot the extact number). i can connect to the internet fine using cat 5 eithernet but i need a driver for my wireless card. where can i get a driver ?

1. What is the make and model of your wireless card?

2. What exactly makes you think you need a driver?

---

### Post by norbert26 on 2009-11-18
> **fooman said:**
> did you check in system > administration > hardware drivers?
 
if nothing there, open up a terminal and type the following into it:
 
```
lspci
```
 
then post the output back here. that will give us the info needed to help you further.

OK i have opened the terminal. the computer running ubunto is not connected to the internet so i have to type in what i see on the pen terminal and i beleive this what you want to see. 

02:00.0 Network controller : Broadcom Corporation BCM4312 802.11B/G (REV 01)

if you need anything else from that terminal derscribe it and ill open it again and cross type it over.

---

### Post by 3rdalbum on 2009-11-18
Either run the command:

```
sudo apt-get update
```

or click the Reload button in Synaptic Package Manager (this will get a complete list of packages available from the Ubuntu online repositories, including any drivers available). Now check your Hardware Drivers program.

---

### Post by norbert26 on 2009-11-18
> **3rdalbum said:**
> Either run the command:
 
```
sudo apt-get update
```
 
or click the Reload button in Synaptic Package Manager (this will get a complete list of packages available from the Ubuntu online repositories, including any drivers available). Now check your Hardware Drivers program. 

ok I assume i need to be connected to the internet so i need to swap the CAT 5 into that machine. will post results after this proceedure.

---

### Post by norbert26 on 2009-11-18
THANK YOU !!!!!!! it works like a champ !!!!!!!

---

