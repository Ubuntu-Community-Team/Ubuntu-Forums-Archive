---
title: "Where can I find the network?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by TideMan on 2009-03-18
I've installed Samba and Nautilus on Bluefront running Xubuntu.
The Win XP machines on my LAN can see Bluefront and my Ubuntu machine can see Bluefront.
But how can I see these machines from Bluefront?
On Ubuntu, there is a Network tab under Places, but that does not exist in Xubuntu.

---

### Post by OffAxis on 2009-03-18
try this:

[http://ubuntuforums.org/showthread.php?t=304131&highlight=xfce+samba](http://ubuntuforums.org/showthread.php?t=304131&highlight=xfce+samba)

---

### Post by TideMan on 2009-03-18
> try this:

[http://ubuntuforums.org/showthread.p...ght=xfce+samba](http://ubuntuforums.org/showthread.p...ght=xfce+samba)

Well, that's a very long thread dating back to 2006.

For Xubuntu 8.10, what does one need to do to get access to the network?

---

### Post by OffAxis on 2009-03-18
(it's the same)
here's the official FAQ on it:
[http://thunar.xfce.org/pwiki/documentation/faq](http://thunar.xfce.org/pwiki/documentation/faq)
just go all the way to the bottom.


an alternative is to install pyneighborhood and use that instead.

```
sudo apt-get install pyneighborhood
```

---

### Post by achase79 on 2009-03-18
you installed nautilus.  You just have to start it and you can browse the network from the places panel in nautilus.

---

### Post by TideMan on 2009-03-18
How should I start Nautilus?

---

### Post by TideMan on 2009-03-18
> How should I start Nautilus? 

Sorry.  Stupid question.
Opening a terminal window and typing it in worked.
Now I have access to the LAN.
Thanks achase79

---

