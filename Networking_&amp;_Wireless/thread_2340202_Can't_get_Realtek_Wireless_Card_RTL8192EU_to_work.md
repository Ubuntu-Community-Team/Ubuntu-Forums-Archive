---
title: "Can't get Realtek Wireless Card RTL8192EU to work"
date: 2016-10-16
forum: Networking &amp; Wireless
---

### Post by linux-admirer on 2016-10-16
I just dual booted my system with Windows 7 and Ubuntu 14.04. I cannot get my wireless card to work with Ubuntu although it works fine for Windows. Where is the proper driver I need to install or what should I do to get this to work on the Ubuntu?

---

### Post by jeremy31 on 2016-10-16
Welcome to the forums.  Open terminal (CTRL + t) and post the results for ```
lsusb
```

---

### Post by linux-admirer on 2016-10-16
There's a lot of results and I'm using my phone to type right now. It's essentially bus ### device ###: ID (4 hex characters:4 more hex) then on each line:

Broadcom corp mouse
Broadcom corp keyboard
Broadcom Corp usb 2.0 hub
Realtek semiconductor Corp
Intel Corp integrated rate matching hub
Linux foundation 2.0 root hub 
Dell computer Corp  (it's a Dell computer)
Primax electronics mouse
Canon (printer)
Intel Corp irmh
Linux foundation 2.0 root hub.

The Realtek adapter is bus 002 device 004 Id 0bda:818b Realtek semiconductor corp

---

### Post by jeremy31 on 2016-10-16
So you have no internet access to the computer?  Can you USB tether to the phone?  As there is a driver that works [https://github.com/Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver) but you need to install some packages to use it and that requires internet access

---

### Post by linux-admirer on 2016-10-16
I can attach my phone to it and it sees it but not for the internet yet just files

---

### Post by linux-admirer on 2016-10-16
OK so the tethering works. Now I can get on the Web. Now what

---

### Post by jeremy31 on 2016-10-16
Ok, post result for ```
uname -a
```
As I have the source code on my computer for your device but compiled modules are kernel specific.  You should be able to download it on your phone and be able to use it

---

### Post by linux-admirer on 2016-10-16
Linux master-OptiPlex-390 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:27 UTC 2016 i686 i686 i686 GNU/Linux

---

### Post by jeremy31 on 2016-10-16
> **linux-admirer said:**
> OK so the tethering works. Now I can get on the Web. Now what

Here it goes, in terminal ```
sudo apt-get install linux-headers-generic git build-essential
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
cd rtl8192eu-linux-driver
make
sudo make install
```

The only downside is that wireless will need to be reinstalled after kernel updates and you will need to
```
cd rtl8192eu-linux-driver
make clean
make
sudo make install
```

Reboot

---

### Post by linux-admirer on 2016-10-16
So that is like this:

sudo apt-get install linux-headers-generic git build-essential

git clone [https://github.com/Mange/rtl8192eu-linux-driver.git](https://github.com/Mange/rtl8192eu-linux-driver.git)

cd rtl8192eu-linux-driver

make

sudo make install

Because the first command resulted in:

E: Unable to locate package linux-headers-generic
E: Unable to locate package git
E: Unable to locate package build-essential

Then the other commands don't work because of that

---

### Post by jeremy31 on 2016-10-16
Does it work if you do ```
sudo apt-get update
``` first

---

### Post by linux-admirer on 2016-10-16
It goes to a Do you want to continue? [Y/n]. I enter in either choice and it says Abort. on the next line

---

### Post by jeremy31 on 2016-10-16
Press y not Y and it will continue

---

### Post by linux-admirer on 2016-10-16
Ok it went through now. Still doing its thing, hold on

---

### Post by linux-admirer on 2016-10-16
Ok so that all went through. The Cd/Make/Make/Sudo commands you mentioned happen after the reboot correct?

---

### Post by jeremy31 on 2016-10-16
Do all the commands then reboot and wireless should function

---

### Post by linux-admirer on 2016-10-16
Ok so enter those before the reboot? I tried the 

cd rtl8192eu-linux-driver

command and it says no such file or directory

---

### Post by jeremy31 on 2016-10-16
Is there an error when you ```
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
```

---

### Post by linux-admirer on 2016-10-16
No there wasn't. Let me try again.

Ok, It's doing the second make command at the moment. Ok, it did the sudo command. I'll reboot and let you know how it goes.

---

### Post by linux-admirer on 2016-10-16
You, sir, are a godsend. Thank you very much for your help, it's working perfectly now.

---

### Post by jeremy31 on 2016-10-16
Please use the forum tools menu at the top of the page to Mark as Solved

---

