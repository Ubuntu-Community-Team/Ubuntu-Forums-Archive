---
title: "The pesky RTL8723be issue"
date: 2018-10-24
forum: Networking &amp; Wireless
---

### Post by itspblazeyo on 2018-10-24
Greetings all, complete Linux noob here. Unfortunately don't have very many Linux savvy friends so I apologize in advance if any of my questions now (and in the future) are duplicates.

So as the title suggests, I'm having issues with the wifi signal. On Mint 19 Tara (which was a bit problematic for me, hence switching to Ubuntu 18.0.4) I was able to temporarily fix it with :

sudo modprobe -r rtl8723be 

sudo modprobe -v rtl8723be ant_sel=2 

These commands work in Ubuntu (as they do disconnect the driver, then load it back up with the proper ant input) however the signal does NOT improve. 

I've downloaded drivers, followed tons of script, and all to no avail. Any suggestions? TIA

---

### Post by jeremy31 on 2018-10-24
This is a kernel bug, so you can either use a kernel older than 4.15.0-33 or try 
```
sudo apt-get install dkms git build-essential
git clone https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

Reboot disable Secure Boot in BIOS


Moved to Networking and Wireless

---

### Post by chili555 on 2018-10-24
Or you could try a kernel *newer *than 4.15: [https://askubuntu.com/questions/1084979/wifi-signal-strength-weak-on-ubuntu-18-04-with-rtl8723be/](https://askubuntu.com/questions/1084979/wifi-signal-strength-weak-on-ubuntu-18-04-with-rtl8723be/)

---

### Post by itspblazeyo on 2018-10-24
Thanks for the script Jeremy. Everything seemed to work fine, I rebooted and disabled the Secure Boot in BIOS. However, now there is no wifi signal at all.

---

### Post by itspblazeyo on 2018-10-24
Thanks for the reply chili. I have a very limited knowledge of how to run open source and this is a pretty rude awakening. I tried to follow that thread and into the linked thread but most of it went over my head. I saw that a certain kernel worked, however after clicking on the link provided, there was more links and didn't want to just start clicking random things. Anything a bit more guided?

---

### Post by chili555 on 2018-10-24
I suggest that you upgrade to Ubuntu 18.10. Can you get a temporary internet connection by tethereing or ethernet?

---

### Post by itspblazeyo on 2018-10-24
Yes, I'm connecting via ethernet at the moment. will upgrade to 18.10 and get back.

---

### Post by itspblazeyo on 2018-10-24
Updated to Ubuntu 18.10. When I access settings it says no wifi adapter found.

---

### Post by chili555 on 2018-10-24
What is the result of:```
sudo modprobe rtl8723be ant_sel=1
dmesg | grep rtl
```

---

### Post by itspblazeyo on 2018-10-24
paul@paul-HP-Notebook:~$ sudo modprobe rtl8723be ant_sel=1
[sudo] password for paul: 
modprobe: ERROR: could not insert 'rtl8723be': Unknown symbol in module, or unknown parameter (see dmesg)
paul@paul-HP-Notebook:~$ dmesg | grep rtl
[   15.974349] rtlwifi: loading out-of-tree module taints kernel.
[   15.974469] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   16.587077] rtl8723_common: Unknown symbol rtl_fw_page_write (err 0)
[   16.587106] rtl8723_common: Unknown symbol rtl_fill_dummy (err 0)
[   16.925173] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   16.925180] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[   16.954882] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   16.954890] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[ 1256.420265] rtl8723_common: Unknown symbol show_it_bb (err 0)
[ 1256.420408] rtl8723_common: Unknown symbol rtl_fw_page_write (err 0)
[ 1256.420504] rtl8723_common: Unknown symbol _rtl_dbg_trace (err 0)
[ 1256.420541] rtl8723_common: Unknown symbol show_it_mac (err 0)
[ 1256.420578] rtl8723_common: Unknown symbol rtl_fill_dummy (err 0)
[ 1303.796543] rtl8723_common: Unknown symbol show_it_bb (err 0)
[ 1303.796607] rtl8723_common: Unknown symbol rtl_fw_page_write (err 0)
[ 1303.796673] rtl8723_common: Unknown symbol _rtl_dbg_trace (err 0)
[ 1303.796717] rtl8723_common: Unknown symbol show_it_mac (err 0)
[ 1303.796765] rtl8723_common: Unknown symbol rtl_fill_dummy (err 0)
[ 1527.682221] rtl8723_common: Unknown symbol show_it_bb (err 0)
[ 1527.682297] rtl8723_common: Unknown symbol rtl_fw_page_write (err 0)
[ 1527.682374] rtl8723_common: Unknown symbol _rtl_dbg_trace (err 0)
[ 1527.682456] rtl8723_common: Unknown symbol show_it_mac (err 0)
[ 1527.682496] rtl8723_common: Unknown symbol rtl_fill_dummy (err 0)
[ 2123.337299] rtl8723_common: Unknown symbol show_it_bb (err 0)
[ 2123.337352] rtl8723_common: Unknown symbol rtl_fw_page_write (err 0)
[ 2123.337408] rtl8723_common: Unknown symbol _rtl_dbg_trace (err 0)
[ 2123.337438] rtl8723_common: Unknown symbol show_it_mac (err 0)
[ 2123.337473] rtl8723_common: Unknown symbol rtl_fill_dummy (err 0)
[ 2520.317769] rtl8723_common: Unknown symbol show_it_bb (err 0)
[ 2520.317824] rtl8723_common: Unknown symbol rtl_fw_page_write (err 0)
[ 2520.317879] rtl8723_common: Unknown symbol _rtl_dbg_trace (err 0)
[ 2520.317910] rtl8723_common: Unknown symbol show_it_mac (err 0)
[ 2520.317942] rtl8723_common: Unknown symbol rtl_fill_dummy (err 0)

---

### Post by chili555 on 2018-10-24
Did you recompile the rtlwifi_new package? We hope not.

If so, please uninstall it and reboot.

---

### Post by itspblazeyo on 2018-10-25
I don't believe so. I've only followed the instructions on here since posting. Regardless, went ahead and ran

cd ./rtlwifi_new

sudo make uninstall

which was successful. I rebooted. Still getting the "no wifi adapter found" message in the settings.

---

### Post by chili555 on 2018-10-25
Let’s have a look at:

```
sudo dkms status
```

---

### Post by itspblazeyo on 2018-10-25
rtlwifi-new, 0.6, 4.15.0-38-generic, x86_64: installed
rtlwifi-new, 0.6, 4.18.0-10-generic, x86_64: installed

---

### Post by chili555 on 2018-10-25
It appears that the handy dkms process did, indeed, install rtlwifi_new. It isn't needed in Ubuntu 18.10 as a working rtl8723be is already included.

Let's remove the dkms version:```
sudo dkms remove rtlwifi-new/0.6 --all
sudo depmod -a
```Reboot and check:```
sudo dkms status
```It should be blank.

Did the in-kernel rtl8723be load?```
lsmod | grep rtl
```Is your wireless now working?

---

### Post by itspblazeyo on 2018-10-25
Chili we're back in business! I do have wifi, however the strength is very low. I'm legit right next to it and it appears to only be at half strength. Any suggestions for this last bit? 

Also, here's what populated for the lsmod | grep rtl (in case it's relevant) 

paul@paul-HP-Notebook:~$ lsmod | grep rtl
btrtl                  16384  1 btusb
bluetooth             548864  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
rtl8723be              98304  0
btcoexist             155648  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                86016  4 rtl_pci,rtl8723be,btcoexist,rtl8723_common
mac80211              794624  3 rtl_pci,rtl8723be,rtlwifi
cfg80211              663552  2 rtlwifi,mac80211

---

### Post by chili555 on 2018-10-25
Almost done! Please go back to your original post and try ant_sel=1. If it doesn't help, then ant_sel=2. When you find the one that works well, we'll make it persistent.

---

### Post by itspblazeyo on 2018-10-25
ant_sel=1 is the stronger signal.

---

### Post by chili555 on 2018-10-25
> **itspblazeyo said:**
> ant_sel=1 is the stronger signal.Let's make it permanent:```
sudo -i
echo "options rtl8723be ant_sel=1"  >  /etc/modprobe.d/rtl8723be.conf
exit
```Have we tamed it? Are you ready to mark this case Solved?

---

### Post by itspblazeyo on 2018-10-25
Everything is working perfectly. Thank you so much for your time and help! Solved indeed!

---

