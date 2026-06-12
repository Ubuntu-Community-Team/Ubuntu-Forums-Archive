---
title: "Equivalent of FreeCap on Windows?"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by aashay on 2007-04-23
Is there any application which can tunnel all the traffic off a program through a socks5 proxy? The program in question does not have an inbuilt option to use a socks. The windows app to do this was freecap, but i cant find anything in linux which does so.. I've also heard of ssh tunneling but have no idea how to work it.
Also, ive tried the "network proxy" in system->prefs but i think it doesnt work for all the programs

---

### Post by tachibana on 2008-06-15
first install Proxychains;
```
sudo apt-get install proxychains
```

after configure the file;

```
sudo gedit /etc/proxychains.conf
```

you can execute the programs by typing;

```
proxychains [program_name]
```

---

### Post by aashay on 2008-06-15
thanks a lot. i'll try it out and post the results

---

