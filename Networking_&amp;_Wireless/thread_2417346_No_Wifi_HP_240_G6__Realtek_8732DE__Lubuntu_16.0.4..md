---
title: "No Wifi HP 240 G6 / Realtek 8732DE / Lubuntu 16.0.4.2 / 4.15.0-47"
date: 2019-04-22
forum: Networking &amp; Wireless
---

### Post by georgieboy on 2019-04-22
Hi there !


Here is the result from the script :
[http://paste.ubuntu.com/p/Pv9QpWKKjX/](http://paste.ubuntu.com/p/Pv9QpWKKjX/)

So basically this was a freshly reinstalled HP laptop with Windows 10 in it (reinstalled with system restore partition). I then installed Lubuntu 16.0.4.2 on a dual boot, installed it directly from the hard drive after extracting it there with Unetbootin on Windows. I had no problem during the  installation (and no wifi also). Wifi is working on Windows but it seems this wireless card still has issues with Linux. 

After the install I plugged in my phone as a USB modem, and ran

```
sudo apt update
sudo apt dist-upgrade
```

rebooted and still no wifi.

Then I went online and scrolled through a few forum posts, found this [https://ubuntuforums.org/showthread.php?t=2367405&page=3](https://ubuntuforums.org/showthread.php?t=2367405&page=3)

I tried stuff without reading through all the thread and so first I tried something which was apparently not suitable as explained later in the thread, which is this :

> **jeremy31 said:**
> 
```
sudo apt-get install git build-essential dkms
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```
Reboot

Which I undid after reading this, along with performing the following fix :
> **jeremy31 said:**
> I think it is time to give up on that source code
```
sudo dkms uninstall rtlwifi-new/0.6
sudo dkms remove rtlwifi-new/0.6 --all
```

Then install another source
```
cd
sudo apt-get install build-essential git dkms
git clone https://github.com/jeremyb31/rtl8723de.git
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
```
Reboot


It's been a few reboots since, but still no wifi.

Also I checked if secure-boot was on and it's not.

Any thoughts on which direction to take now ? 8-[

---

### Post by jeremy31 on 2019-04-22
Post results for ```
dkms status
```

---

### Post by georgieboy on 2019-04-25
Hi Jeremy thanks !
Here is the result

```

rtl8723de, 5.1.1.8_21285.20171026_COEX20170111-1414: added


```

Sorry for the late reply

---

### Post by jeremy31 on 2019-04-25
I would do ```
sudo dkms remove rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414 --all
rm -rf rtlwifi_new
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
Reboot

---

### Post by georgieboy on 2019-04-25
Thanks, I ran all of these commands and the results are here.
[https://paste.ubuntu.com/p/z6FTkh37g3/](https://paste.ubuntu.com/p/z6FTkh37g3/)

Rebooted, still no wifi :/

dkms status returns
```
rtlwifi-new, 0.6, 4.15.0-47-generic, x86_64: installed
```

---

### Post by jeremy31 on 2019-04-25
See the wireless script link in my signature and post results

---

### Post by georgieboy on 2019-04-25
Here they are :)

[http://paste.ubuntu.com/p/WSgzS3j3dM/](http://paste.ubuntu.com/p/WSgzS3j3dM/)

---

### Post by jeremy31 on 2019-04-25
Ok, do ```
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
```
Reboot if no errors

---

### Post by georgieboy on 2019-04-26
no error, reboot, no wifi !
Thanks for your perseverance, I'm still up to try anything you might think of :idea:

---

### Post by jeremy31 on 2019-04-26
Run the script again and post results
Might need
```
cd /lib/firmware/rtlwifi
sudo wget https://github.com/lwfinger/rtlwifi_new/raw/extended/firmware/rtlwifi/rtl8723defw.bin
```
Reboot

---

### Post by georgieboy on 2019-04-26
Yay! That worked :) Many thanks!
I'm pretty impressed by your troubleshooting skills I must say !
Anyway, I seem to get the same speed tests as what my phone gets on this wifi (~10Mbps down/1Mbps up), let me know if you want to finetune that but I think it's pretty decent :)

---

### Post by georgieboy on 2019-04-26
[http://paste.ubuntu.com/p/rcBSRHkHbD/](http://paste.ubuntu.com/p/rcBSRHkHbD/)

---

