---
title: "my synaptic is ill :]"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by sedoyksa on 2011-08-14
when i try to install any packedges i have msg from synaptic 
> Failed to change! 
You must first correct the errors in the packets.

why? what packedges? how

---

### Post by Rex Bouwense on 2011-08-14
What are you trying to install from the Synaptic Package Manager?  I have never seen that particular message before but lets make sure your OS is up to date first.  Go to your terminal and enter:
sudo apt-get update
sudo apt-get upgrade
You will of course be asked for your password so just enter it and hit enter.  When it is finished go back to Synaptic and use Custom Filters - Broken to see if there are broken packages.

---

### Post by sedoyksa on 2011-08-14
my ubuntu 10.10 maverick
i did sudo update
if i do sudo upgrade it will update to 11.10 but i dont want it
i dislake 11.10
> What are you trying to install from the Synaptic Package Manager?
if i try to install wine 1.3 i get this message
if i try some else, for example dreamchess, it install ok

---

### Post by Rex Bouwense on 2011-08-14
No.  sudo apt-get update and sudo apt-get upgrade do not do a disto upgrade.  They merely update the packages that are already on your computer.
To install wine from the terminal:
sudo apt-get install wine
After it installs you should be ready to go.

---

### Post by sedoyksa on 2011-08-14
no way..
after sudo apt-get upgrade

sudo apt-get install wine 1.2
show error 
The following packages have unmet dependencies:
  libc6-dev: Breaks: gcc-4.4 (<4.4.6-4) but 4.4.4-14ubuntu5 will be installed
 E: Broken packages

---

### Post by Brushstroke on 2011-08-14
Try running: 

```
sudo apt-get install -f
```

That may fix some dependency problems with your packages.

---

### Post by sedoyksa on 2011-08-14
sudo apt-get install -f

its dont help me
after apt-get install wine1.2 i have error again

---

