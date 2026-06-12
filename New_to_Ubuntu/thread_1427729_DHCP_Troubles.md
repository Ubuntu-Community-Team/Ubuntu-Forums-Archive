---
title: "DHCP Troubles"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by SSRH on 2010-03-11
I recently installed the notebook edition of Ubuntu 9.10, and I'm having some troubles connecting to the internet using DHCP. I'll go to the NetworkManager application, and attempt to connect with DHCP using the default wired connection, "Auth eth0." Once I click connect, the system tray shows a loading symbol and appears to be looking for a connection. However, after a few moments an image comes up showing a message saying "Wired network Disconnected - you are now offline." Nothing is noticeably wrong with my router, as I can connect with every other box in the house, and I'm certain that my ethernet cord is properly connected to my laptop. I've attached a screenshot of the message I'm recieving. Anyone have an idea what may be wrong?

[IMG]http://i56.photobucket.com/albums/g171/ill_willed/Screenshot.png[/IMG]

---

### Post by CharlesA on 2010-03-11
Post the output of ifconfig.

---

### Post by SSRH on 2010-03-11
> **CharlesA said:**
> Post the output of ifconfig.
 [IMG]http://i56.photobucket.com/albums/g171/ill_willed/untitled-26.png[/IMG]

---

### Post by CharlesA on 2010-03-11
What happens if you run this in a terminal?

```
sudo ifconfig eth0 up
```

---

### Post by patchwork on 2010-03-11
eth0 should already be up if it's being recognized by the ifconfig.

Try 
```
sudo dhclient eth0 
```

I suspect that if nm couldn't connect you with dhcp, this won't either....but at least you'll get some feedback with it.

---

### Post by SSRH on 2010-03-11
> **patchwork said:**
> eth0 should already be up if it's being recognized by the ifconfig.
 
Try 
```
sudo dhclient eth0 
```
 
I suspect that if nm couldn't connect you with dhcp, this won't either....but at least you'll get some feedback with it.
 [IMG]http://i56.photobucket.com/albums/g171/ill_willed/Screenshot-2.png[/IMG]

---

### Post by patchwork on 2010-03-11
OK, let's see if we can't get inet initialized

```
sudo ifconfig eth0 inet up
```


As an aside, i was rash to mention eth0 was up...it appears to be up in ivp6 only...

---

### Post by SSRH on 2010-03-12
> **patchwork said:**
> OK, let's see if we can't get inet initialized

```
sudo ifconfig eth0 inet up
```As an aside, i was rash to mention eth0 was up...it appears to be up in ivp6 only...
  It actually started spontaneously working before I entered that; weird. Thanks for the time and help though guys.

---

