---
title: "Help Connecting to the Internet"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by jaykndl on 2011-06-17
Hello,
I just downloaded Ubuntu 11.04, and I don't have a clue how to connect to the internet. It can't search and find my router. I click on Wireless, then "Add" and put in my router settings, but how do I connect? It says firmware missing or something too and it grays out Internet Connections.
Please help.

---

### Post by FormatSeize on 2011-06-17
Go to System -> Administration -> Hardware (or it might be called something like Devices depending on what version you are using).
There, you should see a list of devices on your computer and you can enable them. Devices like your wireless card has to be enabled before you can use them.

---

### Post by candtalan on 2011-06-17
> **jaykndl said:**
> Hello,
I just downloaded Ubuntu 11.04, and I don't have a clue how to connect to the internet. It can't search and find my router. I click on Wireless, then "Add" and put in my router settings, but how do I connect? It says firmware missing or something too and it grays out Internet Connections.
Please help.
Sounds like your wireless chips are not yet recognised. If you have a chance to connect initially using an ethernet cable to your router, then that would be useful at this stage. Cabled connections will not usually need to be set up.

I think the facility to run is probably the 'additional drivers' app. It can be found either by using the dash (note 1) (windows key, or click the Ubuntu Icon in top left of display, or click the applications '+' launcher and then type
additional drivers
You should soon then see name/s of drivers  for items in your machine, almost certainly including wireless. However, it is likely that the easiest way of then getting it/them will be an ethernet cable from your router.......

Note 1:
if you are not seeing the launcher down the left hand side of the display, then it is likely that your graphics is such as to run Ubuntu classic. If this is the case, then additional drivers  can be found in 
System>Administration>Additional Drivers

hth

---

### Post by candtalan on 2011-06-17
Which computer are you using? Desktop, laptop , type, model etc??

---

### Post by wildmanne39 on 2011-06-17
> **jaykndl said:**
> Hello,
I just downloaded Ubuntu 11.04, and I don't have a clue how to connect to the internet. It can't search and find my router. I click on Wireless, then "Add" and put in my router settings, but how do I connect? It says firmware missing or something too and it grays out Internet Connections.
Please help.
Hi, if you have tried the other method and your card still wont connect run these commands in a terminal
```
sudo lshw -C network 
```lspci
```

```
```
lsmod
```and post it back here by clicking on new reply and click # and paste the information between the brackets.

---

