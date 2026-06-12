---
title: "Repositories - &quot;Unable to locate package&quot; for all packages"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by amx401 on 2011-02-20
I have just loaded 10.10 onto a Toshiba laptop with an i-7 processor to dual boot with Windows 7.  The driver for the wireless card was not in the basic Ubuntu package, but Realtek's website had a tar.gz file which I extracted and long story short, I have internet with Ubuntu.  (P.S. Thank you Realtek for looking out for us.)  

When I open terminal, this happens:
```
kendrick@leiter:~$ feh
The program 'feh' is currently not installed.  You can install it by typing:
sudo apt-get install feh
kendrick@leiter:~$ sudo apt-get install feh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package feh
```feh and cmus are basic packages, and I've installed them on 2 other computers through the repositories.  I am not sure if it is part of a wireless driver problem, a Toshiba problem, something I'm not even thinking about???  Any help would be greatly appreciated.  Thank you.

---

### Post by whatthefunk on 2011-02-20
Have you updated lately?  

```
sudo apt-get update
```

---

### Post by Hakunka-Matata on 2011-02-20
Do you have the 'universe' repository enabled?

---

### Post by amx401 on 2011-02-20
Okay, I'm retarded.  Or my computer is???  I downloaded IDLE using the Ubuntu Software Center under Applications, and after that went through, I re-tried the exact same lines in terminal, and it went right through.  

I did not reboot.  I'm not sure if this is a common problem, or not, but thank you guys for your help.

---

### Post by fabricator4 on 2011-02-20
> **amx401 said:**
> , something I'm not even thinking about???  Any help would be greatly appreciated.  Thank you.

They are definitely there, and installable through Software Center.  Maybe they are in the restricted repositories, make sure you have them enabled.

Chris

---

### Post by amx401 on 2011-02-20
For reference though, how do I check to see if Universe is enabled?  Or get the restricted repositories?  Thank you.  I'm trying to learn as much as possible, but still only been a linux user for a few months.

---

### Post by thefasterblueone on 2011-02-20
This will list all universe repositories.

```
sudo cat /etc/apt/sources.list | grep universe

```

Repositories with "#" (without the qoutation marks) are commented and are disabled. To enable them remove the "#" infront of the deb http and deb-src only.

To edit your sources.list insert this in terminal.

```
sudo gedit /etc/apt/sources.list
```

Then save the file and run,

```
sudo get-apt update
```

---

