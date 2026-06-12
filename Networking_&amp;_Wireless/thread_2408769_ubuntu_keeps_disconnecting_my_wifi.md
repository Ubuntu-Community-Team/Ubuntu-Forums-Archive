---
title: "ubuntu keeps disconnecting my wifi"
date: 2018-12-22
forum: Networking &amp; Wireless
---

### Post by kingofswords on 2018-12-22
im getting sick and tired of having to log back in

its a realtek 8273au

can anyone tell me what the problem is? its a fresh insall a couple of days ago.

---

### Post by wildmanne39 on 2018-12-26
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by jeremy31 on 2018-12-26
Please see the wireless script link in my signature and post results

---

### Post by kingofswords on 2019-01-17
[http://paste.ubuntu.com/p/g7wHwrJqjs/](http://paste.ubuntu.com/p/g7wHwrJqjs/)

ive been trying to sort this for a month and have read hundreds of posts with same problem. ubuntu seems to be a joke these days.

---

### Post by QIII on 2019-01-17
Canonical does not make drivers for hardware.  If they are not in the kernel, they aren't.  If they aren't, then you have to install one.  If it doesn't work, that's on the OEM's developers.  The Linux kernel developers aren't going to do that for them.  That's not their job.

It's no different in Windows.  OEMs write drivers, not Microsoft.  The OEMs have to go through flaming hoops to get their drivers into the Windows driver base.  If they don't, the driver has to be installed.  If the OEM botches the driver, it's on them.  Microsoft doesn't lift a finger to make drivers work.  That's not their job.

Purveyors of distros don't write drivers, so Ubuntu is not at fault here.

Just bear that in mind when asking for support.  There are many things one can find with Canonical to complain about.  But hardware drivers are not one of them.

---

### Post by jeremy31 on 2019-01-17
If you want to use the driver you installed, do the following to disable wifi power management
```
echo "options 8723au rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/8723au.conf
```
Then we should blacklist the kernel module so they don't conflict
```
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
```
Reboot, if the wifi refuses to work using the 8723au you installed, you can load the kernel module with
```
sudo modprobe rtl8xxxu
```

---

### Post by kingofswords on 2019-01-27
> **jeremy31 said:**
> If you want to use the driver you installed, do the following to disable wifi power management
```
echo "options 8723au rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/8723au.conf
```
Then we should blacklist the kernel module so they don't conflict
```
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
```
Reboot, if the wifi refuses to work using the 8723au you installed, you can load the kernel module with
```
sudo modprobe rtl8xxxu
```


sorry for late reply i wanted to test for a few days to make sure it had solved my problem then i forgot to reply.

thats solved my problem jeremy31 thank you very much.
it still disconnects every now and then but only after a few hrs so is much more user able now .

---

### Post by kingofswords on 2019-01-30
i take it back now im getting disconnects every few seconds after a software update.

---

### Post by jeremy31 on 2019-01-31
Please post new results for the wireless script

---

### Post by kingofswords on 2019-01-31
[http://paste.ubuntu.com/p/jZVVjfzSgP/](http://paste.ubuntu.com/p/jZVVjfzSgP/)

thanks

---

### Post by jeremy31 on 2019-02-01
What happened to the 8723au module?  You did have a kernel update, so the module will need to be compiled again

---

### Post by agklimit on 2019-02-01
Just posted this elsewhere minutes ago... hope it helps.

[http://seyferseed.ru/en/life-en/ubuntu-realtek-rtl8723ae-driver-fix-slow-wifi-speed-fix.html#sthash.UxI93rDK.dpbs](http://seyferseed.ru/en/life-en/ubuntu-realtek-rtl8723ae-driver-fix-slow-wifi-speed-fix.html#sthash.UxI93rDK.dpbs)

---

### Post by kingofswords on 2019-02-01
> **jeremy31 said:**
> What happened to the 8723au module?  You did have a kernel update, so the module will need to be compiled again

no idea about module but why would a kernel update delete it?

---

### Post by kingofswords on 2019-02-01
> **agklimit said:**
> Just posted this elsewhere minutes ago... hope it helps.

[http://seyferseed.ru/en/life-en/ubuntu-realtek-rtl8723ae-driver-fix-slow-wifi-speed-fix.html#sthash.UxI93rDK.dpbs](http://seyferseed.ru/en/life-en/ubuntu-realtek-rtl8723ae-driver-fix-slow-wifi-speed-fix.html#sthash.UxI93rDK.dpbs)

no that wasnt any help that site wont let me copy any of the code.

---

### Post by jeremy31 on 2019-02-01
Just do ```
ls ~/ | egrep 'rtl|8723'
```
Post results

---

### Post by kingofswords on 2019-02-03
james@james-Lenovo-IdeaPad-Yoga-11S:~$ ls ~/ | egrep 'rtl|8723'
rtl8723au
rtl8723de
rtlwifi_new

---

### Post by jeremy31 on 2019-02-03
Ok do ```
cd rtl8723au
make clean
make
sudo make install
```
Reboot
Any results for ```
ls ~/rtl8723au | grep dkms
```

---

### Post by kingofswords on 2019-02-03
> **jeremy31 said:**
> Ok do ```
cd rtl8723au
make clean
make
sudo make install
```
Reboot


yeh i already did this(2nd time) and then the previous code([COLOR=#000000]disable wifi power management,blacklist kernel module)
[/COLOR]then reboot and problem presists.
ill try again though thx

> Any results for ```
ls ~/rtl8723au | grep dkms
```

james@james-Lenovo-IdeaPad-Yoga-11S:~$ ls ~/rtl8723au | grep dkms
dkms.conf
README.dkms

---

### Post by jeremy31 on 2019-02-03
So what happens when you ```
sudo modprobe -v 8723au
```
I can forget about having you install with dkms as it won't work since the Secure Boot keys were deleted

---

### Post by kingofswords on 2019-02-03
> **jeremy31 said:**
> So what happens when you ```
sudo modprobe -v 8723au
```
I can forget about having you install with dkms as it won't work since the Secure Boot keys were deleted
 
nothing happens now. before 3rd install it said faulty.....

so i always used 'sudo modprobe rtl8xxxu'but last reboot wifi loaded itself.

---

### Post by jeremy31 on 2019-02-03
Is there an option in BIOS to reload default Secure Boot keys, or anything about loading default keys?  Then we can try dkms

---

### Post by kingofswords on 2019-02-03
theres 

'restore factory keys'?

---

### Post by jeremy31 on 2019-02-03
Yes, do that and reboot, post results for ```
mokutil --sb-state; dkms status
```

---

### Post by kingofswords on 2019-02-03
james@james-Lenovo-IdeaPad-Yoga-11S:~$ mokutil --sb-state; dkms status
SecureBoot enabled
anbox, 1, 4.15.0-44-generic, x86_64: installed
anbox, 1, 4.15.0-45-generic, x86_64: installed
rtl8723de, 5.1.1.8_21285.20171026_COEX20170111-1414, 4.15.0-44-generic, x86_64: installed
rtl8723de, 5.1.1.8_21285.20171026_COEX20170111-1414, 4.15.0-45-generic, x86_64: installed



also when i rebooted 
sudo modprobe -v 8723au


gave 

insmod /lib/modules/4.15.0-45-generic/kernel/drivers/net/wireless/8723au.ko rtw_power_mgnt=0 rtw_enusbss=0 
modprobe: ERROR: could not insert '8723au': Required key not available

so i used sudo modprobe rtl8xxxu

---

### Post by jeremy31 on 2019-02-03
Go into BIOS and disable Secure Boot, don't remove/delete the keys

---

### Post by kingofswords on 2019-02-03
ive already done [COLOR=#000000]restore factory keys[/COLOR]

---

### Post by jeremy31 on 2019-02-03
```
rm -rf rtl8723au
git clone https://github.com/lwfinger/rtl8723au.git
sudo dkms add ./rtl8723au
sudo dkms install 8723au/0.1
```

Reboot and it should work if Secure Boot is disabled

---

### Post by kingofswords on 2019-02-03
thank you for all your help.
ive done the above  so only time will  tell.

in future shall i avoid updating kernel or wifi in software updates?

---

### Post by jeremy31 on 2019-02-03
If it works now, it should work in future 4.15 kernels, I am not sure if that source code from github will build on newer kernels like 4.18

---

### Post by aaguillon on 2019-05-04
I have the rtl8723ae wireless card and always disconnect... Any clue?

---

