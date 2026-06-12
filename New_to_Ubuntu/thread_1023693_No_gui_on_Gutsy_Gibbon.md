---
title: "No gui on Gutsy Gibbon"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by webmiester on 2008-12-28
Hi guys,

I was an Ubuntu Gutsy Gibbon user until my windows partition crashed and destroyed my ubuntu :(

Ive been trying to install Ubuntu 8.1 (Hardy Hebron), but my computer couldnt finish it apparently because my computer lacked the memory requirement for it.  Ive searched near and far for additional memory on my computer (my computer is an old model), but couldnt find anything.  I also entertained getting a new unit, but it turns out to be too expensive.

Anyway, in the end, I decided to go back to Gutsy Gibbon (Ubuntu 7).  I downloaded an installer ISO, burned it and installed it.  At first I was very happy that the installer did it really fast because it didnt use a graphical user installer.  But when I loaded into the my new ubuntu system, it only gave me a text user interface, no GUI :(

Going through the net, I realized that what I downloaded was the Server version which does not install the GUI.  Aside from downloading a new ISO, what else can I do?

---

### Post by zvacet on 2008-12-28
```
sudo apt-get install ubuntu-desktop gdm
```

---

### Post by albinootje on 2008-12-28
> **zvacet said:**
> ```
sudo apt-get install ubuntu-desktop gdm
```

Indeed.
But for your machine it could be nicer to install xfce4, which is a more light-weight desktop.

What are the specifications of your machine ?
```

cat /proc/cpuinfo
free -m

```

---

### Post by webmiester on 2009-01-27
Hi, thanks so much.  Ive purchased a new machine altogether so I junked the old one.

I tried the apt-get command however, I realized that the text-only mode of ubuntu didnt automatically connect to the LAN internet like what the gnome usually does on start-up, so the apt-get command failed.  I got so frustrated that I just bought a new computer.

However, just for me to know, how to you connect the text-only server ubuntu to the LAN?  What commands should I use?

---

### Post by albinootje on 2009-01-28
> **webmiester said:**
>  However, just for me to know, how to you connect the text-only server ubuntu to the LAN?  What commands should I use?

If your routers hands out ip addresses automatically :
```

sudo dhclient

```

---

