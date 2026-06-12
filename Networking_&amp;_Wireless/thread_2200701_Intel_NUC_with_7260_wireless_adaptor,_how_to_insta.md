---
title: "Intel NUC with 7260 wireless adaptor, how to install driver?"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by hugh4 on 2014-01-20
I have a new i5 Intel NUC with an Intel dual band wireless AC 7260 PCI-E adaptor, 30GB internal SSD. I can't get any wireless in mythbuntu. I tried installing openelec/xmbc and wireless works fine so the adaptor works.
I have tried the following in mythbuntu:
Copying file "iwlwifi-7260-7.ucode" into "/lib/firmware" which I downloaded from wireless.kernel.org. Then I rebooted... nothing.

Tried running the following code:
sudo sh ./iwlwifi-7260-7.ucode.run
sudo sh ./iwlwifi-7260-7.ucode
lspci -vnn | grep network
lspci (gave 00:1c.0 PCI Bridge: Intel Device 9c10 (rev e4), 00:1c.3 PCI Bridge: Intel Device 9c16 (rev e4), 02:00.0 Network controller intel corp device 08b1 (rev 73))
ifconf (gave Link encap:local loopback)
iwconf (gave eth0 no wireless extension, lo no wireless extension)

Using settings -> additional drivers I could not load anything (no option to load).

What am I missing?
Could it be UEFI/legacy boot?
Cheers,
Hugh

---

### Post by chili555 on 2014-01-20
I love my NUC! 

Which Ubuntu version are you running? What does this tell us?```
modinfo iwlwifi | grep 08B1
uname -r
```

---

### Post by hugh4 on 2014-01-20
Thanks for the reply. Have 12.04.3 64 bit installed.
I'll run the code when I get home (in Aus).
Hugh

---

### Post by chili555 on 2014-01-20
The short answer is that the kernel in 12.04.3, 3.8.0-xx, I believe, doesn't cover your device. You can compile a later driver like this: [http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63/](http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63/) or you can simply install a 3.12 kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/)  Make sure to get all three pieces.

There is also a better ucode available here: [https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode](https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode)

You seem pretty adept so I'll assume you can handle all this. Obviously, if you need a step-by-step, I'm happy to assist.

---

### Post by hugh4 on 2014-01-21
Thanks chili555 but still need your help! New to linux/ubuntu.

Output from modinfo iwlwifi | grep 08B1:
alias: pci:v0008086d00008B1sv*sd0000C070bc*sc*i*
alias: pci:v0008086d00008B1sv*sd00004070bc*sc*i*
 
uname -r
3.8.0-29 generic
 
I tried the first link to compile the driver, had some errors from
sudo make install
"Can't read private key" on six things (saw one of your posts that said disregard)
"make[1]: execvp: ./scripts/blacklist.sh: Premission denied"
"make[1]: *** [install] error 127"
"make: *** [install] error 2"

I don't know which files to download from your 3.12 kernel link or what to do with them.

Think I need step-by-step! Many thanks.

---

### Post by hugh4 on 2014-01-21
Ok did a google search on the install errors. Did the following, don't know what it does but it worked!
chmod 777 ./scripts/blacklist.sh
repeated make and make install and replaced blacklist.sh with the other file errors obtained. 
All is good, now I have wifi. Thank you chili555 otherwise I would have given up.
cheers
Hugh

---

### Post by chili555 on 2014-01-21
Awesome! Glad it's working.

---

