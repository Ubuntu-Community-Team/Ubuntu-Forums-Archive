---
title: "Netbook UNR Jaunty and the Black Screen of Death?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by stargirl51 on 2009-04-24
Hey guys, I've just attempted to update my Ibex to Jaunty. It downloaded all the packages and yadda yadda yadda. But when it was installing, my screen suddenly went black and flashed on and off before finally resorting to off.

Like a smart person, I restarted the machine. Now when I log into ubuntu, it's nothing but coding blurb that I don't understand.

I'm running a dual boot on an Acer Aspire One.

First question: Anyone else experience this?

Second question: How do I fix it?

---

### Post by Peter09 on 2009-04-24
Do you get a command prompt at the end, if so then try the following commands

```
apt-get update
apt-get upgrade
```

see if that continues your upgrade.

---

### Post by stargirl51 on 2009-04-24
If I click on Recovery mode, it takes me through (I'm assuming) the code version of ubuntu.

The Recovery menu has the following options:
resume normal boot
clean to make free space
dpkg to repair broken packages
fsck for file system check
root to drop to the root shell prompt
xfix to fix X server

Usually, I click resume.

It then asks for my login name and password. When my name and password are entered, it returns:

```
-bash: /dev/null: Permission denied
```


K Rebooted now I go into recovery again and run "dpkg to repair broken packages" Lots of coding went by. there's a lot of lines that repeat:

```

WARNING: node <gettext_domain> not understood below <schema>
```


Ok after running that, I'm able log in again. But it's still Ibex. Should I attempt at another upgrade again?

---

### Post by Peter09 on 2009-04-24
Go for it

---

### Post by stargirl51 on 2009-04-24
Repairing the broken packages definitely help and it updated. BUT

Now my update tool doesn't work. Not even when I go into terminal and update. It returns with

```

E: Could not open llock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

When I try to run update manager, it seems to freeze or take forever to process. And the only thing listed is: Distribution updates: brasero

---

### Post by LowSky on 2009-04-24
try to do updates from terminal

```
sudo apt-get update & sudo apt-get upgrade
```

---

### Post by durand on 2009-04-24
> **stargirl51 said:**
> Repairing the broken packages definitely help and it updated. BUT

Now my update tool doesn't work. Not even when I go into terminal and update. It returns with

```

E: Could not open llock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

When I try to run update manager, it seems to freeze or take forever to process. And the only thing listed is: Distribution updates: brasero

That error is because there is some other installation program open as well. You should close them first. (Synaptic, Upgrade Manager, apt-get, aptitiude (The last two are commandline programs so you probably don't have them open))

---

### Post by stargirl51 on 2009-04-24
> **durand said:**
> That error is because there is some other installation program open as well. You should close them first. (Synaptic, Upgrade Manager, apt-get, aptitiude (The last two are commandline programs so you probably don't have them open))


No other installation program was open. Just Terminal. The first line I entered was the apt-get.

---

### Post by durand on 2009-04-24
Thats pretty strange. You should try rebooting and then do what LowSky said in a terminal (Applications > Accessories > Terminal).

---

