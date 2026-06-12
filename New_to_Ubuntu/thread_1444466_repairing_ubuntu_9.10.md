---
title: "repairing ubuntu 9.10"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by farchumbre on 2010-04-01
hi
i removed metacity and compiz using synaptic, and i can only use the terminal now.
i tried to reinstall them but with terminal alone i don't know how to connect to the internet.
i am trying to repair the damage using the cd image but i have no clue how to do it
any idea?

thanks

---

### Post by oldfred on 2010-04-01
In the list of things uninstalled was the desktop removed?

I would try reinstalling the desktop:

apt-get update
apt-get upgrade
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

### Post by farchumbre on 2010-04-01
hi
as far as i know the desktop was not removed, but the problem is that i can't connect to the internet via the terminal, so i can't install any packages.
do you know how to connect from the terminal?

thanks

---

### Post by Calash on 2010-04-01
Unless you have a special setup or are in a recovery console you should have the same internet access from the terminal that you do from the guy.  Try the first sudo apt-get update and see if it returns errors or not.  That will tell you if you have internet.

---

### Post by Martje_001 on 2010-04-01
Do you connect to the Internet using a wireless connection? If so, it's pretty hard to get a wireless connection up and running from within the terminal (my experience).

Try connection your laptop with a cable (temporary).

---

### Post by achase79 on 2010-04-01
when you had the desktop did you have to do something special to connect to the internet or did it do it for you?

---

### Post by farchumbre on 2010-04-01
i tried with the cable and wireless but even if i type sudo apt-get update it fails
before i could connect to the internet via wireless or wired very easily
is there any way to install the missing packages via the cd, rather than doing a fresh complete install?

---

### Post by mikewhatever on 2010-04-01
You can try adding the installation cd to your sources:

sudo apt-cdrom add

if that works, try reinstalling the previously removed packages.

---

### Post by undecim on 2010-04-01
Often times, packages will remain in your package cache so you can access them even when you aren't connected to the internet. Try "sudo aptitude install ubuntu-desktop" and see if that works.

---

### Post by kokkus on 2010-04-01
Seems to me that you have broken package since you can't install even with cable internet. Open synaptic and click on Repair Broken Packages, then you can use synaptic or the terminal to reinstall the missing packages.

---

### Post by mikewhatever on 2010-04-01
> **kokkus said:**
> Seems to me that you have broken package since you can't install even with cable internet. Open synaptic and click on Repair Broken Packages, then you can use synaptic or the terminal to reinstall the missing packages.

But there is no window managing program to display the GUI. Remember, the OP had removed metacity and compiz.

---

