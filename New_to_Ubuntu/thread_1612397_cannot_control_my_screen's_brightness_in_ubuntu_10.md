---
title: "cannot control my screen's brightness in ubuntu 10.10"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by amitpokhrel on 2010-11-03
Hello everyone!!
I have samsung r580 system with intell core i5 processor (64-bit).When I installed ubuntu 10.10, the maximum brightness of the display was so dim that I could barely see ( though I could control it). Then I installed the graphics driver and the problem disappeared. But now the brightness of my display is very bright and I also can not control it...
any help???

---

### Post by Peter09 on 2010-11-03
Hi,
install samsung-tools.
 
There is a ppa for it, but I am at work so cannot provide it - you should be able to find it with a search on google.

---

### Post by amitpokhrel on 2010-11-03
sorry!! I am very new at ubuntu so i on't know what to look for to install samsung tools..can you please help me out??

---

### Post by migs73 on 2010-11-03
Follow the steps here;

[http://ubuntu-tweak.com/app/samsung-tools/](http://ubuntu-tweak.com/app/samsung-tools/)

---

### Post by Peter09 on 2010-11-03
Go here
 
> [http://ubuntu-tweak.com/app/samsung-tools/](http://ubuntu-tweak.com/app/samsung-tools/)
 
and read the instructions to install it.
 
You may find it worth while installing Ubuntu-Tweak as well.

---

### Post by amitpokhrel on 2010-11-03
I did as said above and i also have ubuntu tweek installed. I rebooted the system after completing as said above but nothing happened. I still cannot decrease the brightness of my screen.
If this may help..
my system is: samsung r580, intel core i5 processor, Ubuntu 10.10, 64 bit. I have windows 7 as well on my system. 

on command:sudo add-apt-repository ppa:voria/ppa, I got following in my terminal. I am not sure if this means repository is added or not.. all other commands given after this command in the link worked fine..

[I]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv A6E348801F28F6B59D308A6036960FC31E5F36F0
gpg: requesting key 1E5F36F0 from hkp server keyserver.ubuntu.com
gpg: key 1E5F36F0: "Launchpad PPA for Fortunato Ventre" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1[/I]

---

### Post by amitpokhrel on 2010-11-03
I another website I found this as a solution for the problem... can anybody tell how to enable it..
Samsung backlight module fixes backlight-related bugs in acpi for Samsung laptops. [B]To enable it, boot kernel with acpi_backlight=vendor option.
The module can work in two modes: direct PCI programming and brighness control via SABI. The mode is chosen by module option use_sabi (could be 0 or 1); by default SABI support is enabled. SABI provides support for larger number of laptop models, but allows for less number of brightness levels.[/B]

---

### Post by amitpokhrel on 2010-11-03
I another website I found this as a solution for the problem... can anybody tell how to enable it..
Samsung backlight module fixes backlight-related bugs in acpi for Samsung laptops. [B]To enable it, boot kernel with acpi_backlight=vendor option.
The module can work in two modes: direct PCI programming and brighness control via SABI. The mode is chosen by module option use_sabi (could be 0 or 1); by default SABI support is enabled. SABI provides support for larger number of laptop models, but allows for less number of brightness levels.[/B]

---

### Post by Peter09 on 2010-11-03
Did you do

```
sudo apt-get update && sudo apt-get upgrade
```

and

```
sudo apt-get install samsung-tools
```

---

### Post by amitpokhrel on 2010-11-04
ya I did that and finished it completly. I also added samsung backlight from synaptic. I then rebooted my system but I still can not control the brightness of my screen..

---

### Post by P4man on 2010-11-04
See the link in my signature:

---

