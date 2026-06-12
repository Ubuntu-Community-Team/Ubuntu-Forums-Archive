---
title: "ubuntu 18.10 realtek 8723de not working"
date: 2019-05-15
forum: Networking &amp; Wireless
---

### Post by elsurfero22 on 2019-05-15
Hi!
i&#7743; kind of new to ubuntu, i have read and tried different forums and topics on how to get this wireless card to work.
now i'm afraid i have installed and uninstalled so many things that i dont know where i'm at.
laptop is hp  and the card in question is realtek 8723de.
is there anyone online to be able to guide me trough the procces of fixing this??


Thanks 
Leandro

---

### Post by jeremy31 on 2019-05-15
Something like
```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
Then check results for ```
mokutil --sb-state
```
Secure Boot needs to be disabled, if it says mokutil not installed, just reboot, otherwise Secure Boot will need to be disabled in BIOS

---

### Post by elsurfero22 on 2019-05-15
this is what i get from command line 2 nad 3 


:~$ git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
fatal: destination path 'rtlwifi_new' already exists and is not an empty directory.
:~$ sudo dkms add ./rtlwifi_new
Error! Could not find module source directory.
Directory: /usr/src/.-rtlwifi_new does not exist.

---

### Post by jeremy31 on 2019-05-15
```
cd ~/rtlwifi_new
git checkout extended
cd
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```

---

### Post by elsurfero22 on 2019-05-15
sorry another error 

~/rtlwifi_new$ git checkout extended
fatal: not a git repository (or any of the parent directories): .git

---

### Post by jeremy31 on 2019-05-15
Ok, try
```
cd Desktop
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```

---

### Post by elsurfero22 on 2019-05-15
~/Desktop$ sudo dkms add ./rtlwifi_new
Error! DKMS tree already contains: rtlwifi-new-0.6
You cannot add the same module/version combo more than once.

---

### Post by jeremy31 on 2019-05-16
```
sudo dkms remove rtlwifi-new/0.6 --all
cd Desktop
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```

---

