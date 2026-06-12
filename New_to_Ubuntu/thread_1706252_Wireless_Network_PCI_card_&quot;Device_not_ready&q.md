---
title: "Wireless Network PCI card &quot;Device not ready&quot;"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by peterbug on 2011-03-13
Hello!

I am having an issue with the wireless on my laptop. It says the device is not ready, I assumed this was a result of incompatibility with the avalible drivers! But this morning it worked perfectly till I shut my laptop down, now it's gone back to not working. I'm assuming the problem is with the control switch for enabling the networking card! But pressing the physical button does nothing, is there a way to enable it using the CLI? I've tried looking around google but never found anything! This is my net work card:

> 03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev ff)

---

### Post by bkratz on 2011-03-13
> **peterbug said:**
> Hello!

I am having an issue with the wireless on my laptop. It says the device is not ready, I assumed this was a result of incompatibility with the avalible drivers! But this morning it worked perfectly till I shut my laptop down, now it's gone back to not working. I'm assuming the problem is with the control switch for enabling the networking card! But pressing the physical button does nothing, is there a way to enable it using the CLI? I've tried looking around google but never found anything! This is my net work card:



What, if anything, does this tell us?


```
rfkill list all
```

---

### Post by peterbug on 2011-03-13
Thank you for your speedy reply!

```
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

So the game now is to turn off that block?

---

### Post by bkratz on 2011-03-13
> **peterbug said:**
> Thank you for your speedy reply!

```
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

So the game now is to turn off that block?

May not solve the whole problem but worth a shot

```
sudo rfkill unblock all
```

Then see what the previous command says.

---

### Post by peterbug on 2011-03-13
```
peter@peter-Etna-GM:~$ sudo rfkill unblock 0
peter@peter-Etna-GM:~$ rfkill list 0
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

```

doesn't look like that worked.

---

### Post by bkratz on 2011-03-13
Post 4 of this thread looks like it may be useful. Still looking.

[http://ubuntuforums.org/showthread.php?t=1469799](http://ubuntuforums.org/showthread.php?t=1469799)

---

### Post by peterbug on 2011-03-13
> **bkratz said:**
> Post 4 of this thread looks like it may be useful. Still looking.

[http://ubuntuforums.org/showthread.php?t=1469799](http://ubuntuforums.org/showthread.php?t=1469799)

This worked perfectly! Thank you very much for your help!

---

