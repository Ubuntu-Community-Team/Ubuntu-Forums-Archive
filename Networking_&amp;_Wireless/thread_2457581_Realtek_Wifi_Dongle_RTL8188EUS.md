---
title: "Realtek Wifi Dongle RTL8188EUS"
date: 2021-02-05
forum: Networking &amp; Wireless
---

### Post by drjdmartin on 2021-02-05
Hi,

I'm running Ubuntu 20.10. I have a realtek wifi dongle, lsusb:
```

Bus 003 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter

```
It didn't work out of the box (no wifi option in gui), so I blacklisted the in-built r8188eu and tried to install the one from lwfinger at [https://github.com/lwfinger/rtl8188eu](https://github.com/lwfinger/rtl8188eu). Now wifi is an option in the gui but I see no networks. sudo dmesg | grep 8188:
```

[    4.609546] 8188eu: loading out-of-tree module taints kernel.
[    4.609796] 8188eu: module verification failed: signature and/or required key missing - tainting kernel
[    4.611947] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_UNKNOWN_CUT(10)_1T1R_RomVer(0)
[    4.646007] usbcore: registered new interface driver r8188eu
[    5.077610] r8188eu 3-1:1.0 wlx28f366942c60: renamed from wlan0
[   10.775359] R8188EU: Firmware Version 11, SubVersion 1, Signature 0x88e1
[   12.561851] R8188EU: INFO indicate disassoc

```
So I thought the module signing was probably the problem, but the confusion is that I'm not running secure boot so I can't sign the modules on my system, and surely module signing shouldn't be a problem in the first place? I thought maybe it would work if I installed via DKMS so I wrote a simple dkms.conf and installed the lwfinger driver that way instead. But I still have this error message. Here is the output of iwconfig:
```

lo        no wireless extensions.


eno1      no wireless extensions.


wlx28f366942c60  unassociated  ESSID:""  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I've read around a bit and people are suggesting I'd have to recompile the kernel to turn off the module signing as I'm not on a UEFI system. Seems a bit drastic but I probably could have a stab. Do you think this error the source of the problem? Is there another way to fix it?

Thanks,

James

---

### Post by drjdmartin on 2021-02-07
I bought one of these which works out of the box and is cheap!

[https://www.amazon.co.uk/Wireless-802-11n-Adapter-Compatible-Raspberry/dp/B0012E2BKA/ref=sr_1_5?dchild=1&keywords=USB+wifi+linux&qid=1612710802&s=computers&sr=1-5](https://www.amazon.co.uk/Wireless-802-11n-Adapter-Compatible-Raspberry/dp/B0012E2BKA/ref=sr_1_5?dchild=1&keywords=USB+wifi+linux&qid=1612710802&s=computers&sr=1-5)

Still interested in working out whether I could get the realtek ones working though.

---

### Post by CelticWarrior on 2021-02-07
[https://askubuntu.com/questions/1170202/how-to-install-rtl8188eus-driver-on-ubuntu-18-04](https://askubuntu.com/questions/1170202/how-to-install-rtl8188eus-driver-on-ubuntu-18-04)

---

### Post by drjdmartin on 2021-02-08
Thanks - but unfortunately that's basically what I already did (and the dkms instructions don't work anymore for that driver unless you do it yourself, which I did).

I have another realtek dongle using the RTL8188FU driver and that shows me networks on my Debian 10 install but won't connect. I'm forced to conclude realtek are a pain in the neck and not to be recommended!

Re the module signing issue suggested by my earlier post is this a bug in Ubuntu? As I say I am not using secure boot - I'm using bios boot and grub.

---

### Post by slickymaster on 2021-02-08
*Thread moved to **Networking & Wireless**.*

---

### Post by drjdmartin on 2021-02-08
Thanks for moving to the correct part of the forum. I think the following question is still open. From the dmesg output I think the module signing is preventing the lwfinger driver working. Is this a bug given my system is not secure boot? Is there any way around it given I can't sign the module on my system?
```

[    4.609546] 8188eu: loading out-of-tree module taints kernel.
[    4.609796] 8188eu: module verification failed: signature and/or required key missing - tainting kernel
[    4.611947] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_UNKNOWN_CUT(10)_1T1R_RomVer(0)
[    4.646007] usbcore: registered new interface driver r8188eu
[    5.077610] r8188eu 3-1:1.0 wlx28f366942c60: renamed from wlan0
[   10.775359] R8188EU: Firmware Version 11, SubVersion 1, Signature 0x88e1
[   12.561851] R8188EU: INFO indicate disassoc

```

---

### Post by CelticWarrior on 2021-02-08
Systems aren't "Secure Boot". Secure Boot is a UEFI feature that may or may not be enabled and if using an old BIOS system or a UEFI one in Legacy/CSM mode, not applicable.

I suggest you check which one you have and confirm that Secure Boot, if applicable, is really disabled.

---

### Post by drjdmartin on 2021-02-08
Thanks - so checking the BIOS it says UEFI enabled, legacy mode. This is on a Dell Optiplex 7010. So I think secure boot is at least disabled in the BIOS - is there anywhere else I should check?

When I tried to use mokutil to sign the 8188eu module as suggested in a few other posts I browsed I also got the error "EFI variables are not supported on this system". So I can't sign the module to fix the verification error.

---

### Post by jeremy31 on 2021-02-08
How far away from the router are you and what manufacturer/model is the dongle?  I have a small TP-Link one and it works on Ubuntu 18.04 with the 5.4 kernels but it doesn't have much range

The EFI variables not supported means that Secure Boot has nothing to do with the problem and the module doesn't need to be signed, if that was the issue, you would not see a wireless interface in iwconfig results as the kernel wouldn't load the driver

---

### Post by chili555 on 2021-02-08
> From the dmesg output I think the module signing is preventing the lwfinger driver working.Not really. This message:> 
module verification failed: signature and/or required key missing - tainting kernel
...simply means that there was no provided verification that the driver is well and truly verified and free and open source. The driver code simply lacks a signature key. The kernel is no longer pure and verified open source.

Actually it is, you just can't prove it!

Secure boot, mokutil, etc. have nothing to say here.

Of greater interest is that you seem to have *both *the lwfinger 8188eu compiled version *and* the in-tree verified r8188eu version loaded. Verify:

```
lsmod | grep 8188
```Two possibly conflicting drivers won't help here.

Let's look a bit further:

```
rfkill list all
dmesg | grep wlx
nmcli device wifi list
```

> The EFI variables not supported means that Secure Boot has nothing to do with the problem and the module doesn't need to be signed, if that was the issue, you would not see a wireless interface in iwconfig results as the kernel wouldn't load the driverAmen, my friend!!!

---

### Post by drjdmartin on 2021-02-09
Thanks for this

@ Jeremy31 I'm very close to a wireless access point so the signal is definitely high where I'm testing it.

@chili555 tapped in your commands:

lsmod | grep 8188
```
8188eu                729088  0
```

rfkill list all is blank
dmesg | grep wlx
```
[    4.472236] r8188eu 3-1:1.0 wlx28f366942c60: renamed from wlan0
```
nmcli device wifi list
```
IN-USE  BSSID  SSID  MODE  CHAN  RATE  SIGNAL  BARS  SECURITY
```

Re the conflict I have tried to blacklist the r8188eu driver in \etc\modprobe.d\blacklist.conf

---

### Post by chili555 on 2021-02-09
> Re the conflict I have tried to blacklist the r8188eu driver in \etc\modprobe.d\blacklist.confAs you see, the lwfinger compiled version is not working at all for reasons we don't yet understand. I suggest that you change the blacklist to blacklist 8188eu and remove from blacklist r8188eu and reboot. Then show us again:

```
rfkill list all
dmesg | grep -e wlx -e 8188
lsmod | grep 8188
```

---

### Post by drjdmartin on 2021-02-09
Ok - blacklisted 8188eu rather than r8188eu

rfkill list all remains blank

dmesg | grep -e wlx -e 8188
```

[    4.889619] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[    4.890857] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_UNKNOWN_CUT(10)_1T1R_RomVer(0)
[    4.916550] usbcore: registered new interface driver r8188eu
[    5.428585] r8188eu 3-1:1.0 wlx28f366942c60: renamed from wlan0

```
lsmod | grep 8188
```

r8188eu               438272  0
lib80211               16384  1 r8188eu
cfg80211              782336  1 r8188eu

```


In the network manager I can see wifi not connected, and selecting network has no options similar to the situation with the 8188eu module.

---

### Post by chili555 on 2021-02-09
> selecting network has no options similar to the situation with the 8188eu module.Meaning that you *do *see networks from which to connect but that clicking one does nothing? Or what? How about:

```
nmcli device wifi list
sudo updatedb && locate rtl8188eufw.bin
dmesg | grep -i rtl

```

---

### Post by jeremy31 on 2021-02-09
This must be the key ```
[    4.890857] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_UNKNOWN_CUT(10)_1T1R_RomVer(0)
```

As I installed the 5.8.0-41 kernel on my laptop and the dmesg shows
```
[  125.947563] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[  125.949334] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
[  125.976432] usbcore: registered new interface driver r8188eu
[  125.995181] r8188eu 3-2:1.0 wlxc46e1f171424: renamed from wlan0
[  129.246598] R8188EU: assoc success
[  143.709606] R8188EU: indicate disassoc
[  152.225020] R8188EU: assoc succes
```
I will try to find where this chip version info comes from, the fix might be in the newest kernel from mainline

---

### Post by drjdmartin on 2021-02-10
Thanks again both

@chili555 Sorry, I wasn't clear - I don't see any networks in the wifi menu in the gui
nmcli device wifi list
```
IN-USE  BSSID  SSID  MODE  CHAN  RATE  SIGNAL  BARS  SECURITY
```
sudo updatedb && locate rtl8188eufw.bin
```

/home/james/DriverBuild/rtl8188eu/rtl8188eufw.bin
/usr/lib/firmware/rtl8188eufw.bin
/usr/lib/firmware/rtlwifi/rtl8188eufw.bin
/usr/src/8818eu-1.0/rtl8188eufw.bin

```
sudo dmesg | grep -i rtl returns a blank

---

### Post by chili555 on 2021-02-10
Let's try a newer version of the driver. First, please note:

```
modinfo r8188eu | grep version
version:        v4.1.4_6773.20130222

```
I strongly suspect that means that this is a heavily adapted circa-2013 version of the driver. 2013 is like 50 years ago in Linux years! Also, I suspect that the version you compiled is exactly the same. Let's try to fix it:

```
cd ~/DriverBuild/rtl8188eu
sudo make uninstall
```

I assume this was not installed by dkms. Check:

```
sudo dkms status
```

If it was installed by dkms, we'll need an additional step.

```
cd ..
sudo rm -r rtl8188eu
git clone -b v5.2.2.4 https://github.com/lwfinger/rtl8188eu.git
cd rtl8188eu
make
sudo make install
```

Now, change the blacklist to blacklist the ancient circa-2013 driver r8188eu and reboot.

Any improvement?

```
nmcli device wifi list
```

---

### Post by drjdmartin on 2021-02-10
Fantastic - this has solved the problem with the networks not showing up. Maybe I didn't use the git download path when I installed 8188eu previously, or I had a duff version.

But it looks as if it is struggling to connect and then has no internet access when it looks to have connected.

My network is VM8573713:

nmcli device wifi list
```

IN-USE  BSSID              SSID       MODE   CHAN  RATE        SIGNAL  BARS  SECURITY
        EC:08:6B:79:2C:12  VM8573713  Infra  1     270 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2 
        4C:38:D8:29:64:01  VM8573713  Infra  6     130 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2 
        10:7B:44:44:D2:00  llama24    Infra  8     540 Mbit/s  49      &#9602;&#9604;__  WPA2      
        62:B1:B5:11:AC:F9  BTWi-fi    Infra  11    195 Mbit/s  29      &#9602;___  --  

```

dmesg | grep -e wlx -e 8188
```

[    4.559239] 8188eu: loading out-of-tree module taints kernel.
[    4.559723] 8188eu: module verification failed: signature and/or required key missing - tainting kernel
[    4.563578] RTW: rtl8188eu v5.2.2.4_25483.20171222
[    4.591312] usbcore: registered new interface driver rtl8188eu
[    5.073905] rtl8188eu 3-1:1.0 wlx28f366942c60: renamed from wlan0
[   10.406738] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000000
[   12.956753] IPv6: ADDRCONF(NETDEV_CHANGE): wlx28f366942c60: link becomes ready
[   58.034807] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000009
[   65.520168] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[   68.200137] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[   72.495866] RTW: OnDisassoc(wlx28f366942c60) reason=8, ta=4c:38:d8:29:64:01
[   75.911552] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[   94.898331] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[   95.411452] RTW: OnDisassoc(wlx28f366942c60) reason=8, ta=4c:38:d8:29:64:01
[  101.872365] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  114.346400] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  114.663436] RTW: OnDisassoc(wlx28f366942c60) reason=8, ta=4c:38:d8:29:64:01
[  126.566404] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  143.950455] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  149.556105] RTW: OnDisassoc(wlx28f366942c60) reason=2, ta=4c:38:d8:29:64:01
[  171.909199] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  189.264455] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  189.936931] RTW: OnDisassoc(wlx28f366942c60) reason=8, ta=4c:38:d8:29:64:01
[  207.701048] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  210.888778] IPv6: ADDRCONF(NETDEV_CHANGE): wlx28f366942c60: link becomes ready
[  385.792764] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000009
[  393.512180] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  403.228346] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  419.553782] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  428.696313] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  429.140314] RTW: OnDisassoc(wlx28f366942c60) reason=8, ta=4c:38:d8:29:64:01
[  441.047976] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  454.699492] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  455.060860] RTW: OnDisassoc(wlx28f366942c60) reason=8, ta=4c:38:d8:29:64:01
[  466.239282] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008

```

lsmod | grep 8188
```

8188eu               1482752  0
cfg80211              782336  1 8188eu

```

---

### Post by chili555 on 2021-02-10
>  EC:08:6B:79:2C:12  VM8573713  Infra  1     270 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2 
        4C:38:D8:29:64:01  VM8573713  Infra  6     130 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2 Are these your router and extender respectively? I have no doubt whatever that your device is struggling to select from among two SSIDs named the same with good signal strength.

I suggest that you either rename one, someting like VM8573713ext or some such or, if this is not feasible, then bind to the strongest by its MAC address, also known as BSSID, like this: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

As well, I'd make some changes in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router.

We have the patient breathing and its heart is beating. Now we just need to teach it to walk and speak!

---

### Post by drjdmartin on 2021-02-10
OK weird - this looks to have now completely resolved itself

I installed the rtl8188fu driver for my other wireless dongle from the git source and this worked much better. Then I plugged the original 8188eu dongle back in and suddenly it connected and worked! Basically whatever we did there was a universal fix for all my realtek wifi issues as the rtl8188fu dongle wasn't working on this computer either.

Noted your comments about WPA verification - I'll get on this.

Thanks for all your help!

---

### Post by drjdmartin on 2021-02-19
Apologies - went a bit mad and confused my working Ralink dongle with the Realtek one. The RTL8188EUS dongle is showing networks but does not seem to be able to connect still. My previous comment about the rtl8188fu dongle was correct though - this is working well.

For the RTL8188EUS dongle I've tried to clarify the BSSID in the connection as per the suggestion, and have switched to WPA2 as you can see below. It looks like it is struggling to authenticate as it keeps prompting for the password, but this has definitely been entered correctly. Any ideas what to look at next?

nmcli device wifi list
```
IN-USE  BSSID              SSID                      MODE   CHAN  RATE        SIGNAL  BARS  SECURITY
        EC:08:6B:79:2C:12  VM8573713                 Infra  1     270 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2     
        4C:38:D8:29:64:01  VM8573713                 Infra  6     130 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2     
        F6:A9:97:3F:19:75  DIRECT-F375-TS6100series  Infra  1     65 Mbit/s   60      &#9602;&#9604;&#9606;_  WPA2     
        40:3F:8C:85:3B:16  VM8573713                 Infra  11    130 Mbit/s  39      &#9602;&#9604;__  WPA2  
```

---

### Post by chili555 on 2021-02-19
Did you bind Network Manager to the strongest as I suggested above? You obviously didn't rename some of them.

---

### Post by drjdmartin on 2021-02-20
I tried to bind the BSSID and MAC address but that didn't seem to work. But I should have followed your advice to rule out other issues, so I've bitten the bullet and changed the extender SSID as per below:

```

IN-USE  BSSID              SSID                              MODE   CHAN  RATE        SIGNAL  BARS  SECURITY
         EC:08:6B:79:2C:12  VM8573713ext                      Infra  1     270 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2     
        4C:38:D8:29:64:01  VM8573713                         Infra  6     130 Mbit/s  55      &#9602;&#9604;__  WPA2     
        10:7B:44:44:D2:00  llama24                           Infra  8     540 Mbit/s  45      &#9602;&#9604;__  WPA2     
        AC:E2:D3:2C:27:E1  DIRECT-E0-HP DeskJet 2600 series  Infra  8     65 Mbit/s   39      &#9602;&#9604;__  WPA2     
        40:3F:8C:85:3B:16  VM8573713                         Infra  11    130 Mbit/s  39      &#9602;&#9604;__  WPA2    

```

Attached is the config in network manager. Still no dice - still seems to be struggling with authentication? Or at least it spins for a while and then asks for the password again.

---

### Post by chili555 on 2021-02-20
Are there any interesting clues in:

```
sudo dmesg | grep -e 8188 -e wlx
```

---

### Post by drjdmartin on 2021-02-21
sudo dmesg | grep -e 8188 -e wlx
```

[    4.454028] 8188eu: loading out-of-tree module taints kernel.
[    4.454512] 8188eu: module verification failed: signature and/or required key missing - tainting kernel
[    4.459173] RTW: rtl8188eu v5.2.2.4_25483.20171222
[    4.488397] usbcore: registered new interface driver rtl8188eu
[    4.759469] rtl8188eu 3-1:1.0 wlx28f366942c60: renamed from wlan0
[   14.488752] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000000
[   22.020292] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[   29.622214] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  387.614316] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008
[  404.247060] RTW: rtw_set_802_11_connect(wlx28f366942c60)  fw_state=0x00000008

```

I googled fw_state=0x00000008 and there were some references for people fixing a problem with wifi mac address randomisation, but it looks like this is already disabled:
cat /etc/NetworkManager/NetworkManager.conf
```

[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


[device]
wifi.scan-rand-mac-address=no

```

---

