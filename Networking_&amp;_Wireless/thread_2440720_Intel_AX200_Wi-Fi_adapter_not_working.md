---
title: "Intel AX200 Wi-Fi adapter not working"
date: 2020-04-14
forum: Networking &amp; Wireless
---

### Post by schoolbusesc2 on 2020-04-14
After installing Ubuntu 18.04 LTS, in settings it says Wi-Fi adapter  not found. However, bluetooth still works. My Wi-Fi card is an Intel  AX200. I have installed the firmware from Intel's website (by copying it  into /lib/firmware). According to the instructions, after copying the  file I should load the driver which I did by doing *[FONT=courier new]sudo modprobe iwlwifi[/FONT]*. Also I am running kernal 5.6.0 which is above the minimum kernal on the Intel website, and Wi-Fi works in Windows 10 (which I have in dual boot right now).

After runnning dmesg | grep iwlwifi I get the following:

  ```
[    4.126373] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)
[    4.206832] iwlwifi: probe of 0000:0f:00.0 failed with error -110

```  Does anyone know how to fix this? If there is anything else I need to run please tell me. Thanks!

  **Update:**
This is what I get when running lspci -nnk | grep 0280 -A3:
  ```
06:00.0 Network controller [0280]: Intel Corporation Device [8086:0084] (rev 1a)
        Subsystem: Intel Corporation Device [8086:0084]
        Kernel modules: iwlwifi

```

---

### Post by chili555 on 2020-04-14
> [    4.126373] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)
[    4.206832] iwlwifi: probe of 0000:0f:00.0 failed with error -110There must be more than this. Please try: ```
sudo modprobe iwlwifi && dmesg | grep iwl
```

---

### Post by schoolbusesc2 on 2020-04-14
I ran it again and this is what I got:
```

schoolbusesc2@Desktop:~$ sudo modprobe iwlwifi && dmesg | grep iwl
[sudo] password for schoolbusesc2: 
[    4.081060] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)
[    4.197146] iwlwifi: probe of 0000:06:00.0 failed with error -110
schoolbusesc2@Desktop:~$ 

```
[ATTACH=CONFIG]285524[/ATTACH]

---

### Post by chili555 on 2020-04-14
Let's see which firmware files you have:

```
ls /lib/firmware | grep iwlwifi-cc-a0-46

```
If it is not found, update the firmware:

```
wget http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.183.2_all.deb
sudo dpkg -i linux*.deb
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi

```
Any improvement?

If not, let's dig deeper:

```
dmesg | grep 06:00
```

-----

Reference: [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html)

---

### Post by schoolbusesc2 on 2020-04-14
The firmware was found. I will run grep 06:00 later

[B]UPDATE:
[/B]dmesg | grep 06:00 returns this:
```

schoolbusesc2@Desktop:~$ dmesg | grep 06:00
[    0.652372] pci 0000:06:00.0: [8086:2723] type 00 class 0x028000
[    0.652415] pci 0000:06:00.0: reg 0x10: [mem 0xf6e00000-0xf6e03fff 64bit]
[    0.652579] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    1.016423] pci 0000:06:00.0: Adding to iommu group 22
[    4.084947] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)
[    4.171239] iwlwifi: probe of 0000:06:00.0 failed with error -110
schoolbusesc2@Desktop:~$ 

```

---

### Post by chili555 on 2020-04-14
> 
Wi-Fi works in Windows 10 (which I have in dual boot right now).

Ah, haaaa!

Please see comment #3 here: [https://bugzilla.kernel.org/show_bug.cgi?id=205299](https://bugzilla.kernel.org/show_bug.cgi?id=205299)

---

### Post by schoolbusesc2 on 2020-04-14
Oh, ha. Lets see if that works.

---

### Post by schoolbusesc2 on 2020-04-14
Ok, so after turning off fast startup and restarting the Wi-Fi card is detected but I get "connection failed"

---

### Post by chili555 on 2020-04-14
Awesome! Glad it's working.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by schoolbusesc2 on 2020-04-14
The Wi-Fi still is not connecting. I am getting connection failed

---

### Post by schoolbusesc2 on 2020-04-15
Hmm.... That is weird. The Wi-Fi adapter is working but every time I try to connect to my Wi-Fi it always says connection failed. Does anyone know why?

---

### Post by schoolbusesc2 on 2020-04-15
Hmm... The Wi-Fi adapter is found but every time I try to connect it always says connection failed.

---

### Post by chili555 on 2020-04-15
Will you please try a driver parameter? From the terminal:

```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi disable_11ax=Y

```
If it is helpful, we'll make it permanent:

```
sudo -i
echo "options iwlwifi disable_11ax=Y"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```If the parameter is not helpful, provide logs and we'll troubleshoot further:

```
dmesg | grep wl
```

---

### Post by schoolbusesc2 on 2020-04-15
No still does not work...
Here is dmesg:
```
schoolbusesc2@Desktop:~$ dmesg | grep wl
[  227.429712] wlp6s0: authenticate with 00:25:9c:5c:b2:3e
[  227.432570] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 1/3)
[  227.432674] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 2/3)
[  227.432690] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 3/3)
[  227.432699] wlp6s0: authentication with 00:25:9c:5c:b2:3e timed out
[  248.659355] wlp6s0: authenticate with 48:5d:36:f5:ed:f4
[  248.661469] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 1/3)
[  248.661605] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 2/3)
[  248.661620] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 3/3)
[  248.661625] wlp6s0: authentication with 48:5d:36:f5:ed:f4 timed out
[  255.000048] wlp6s0: authenticate with 48:5d:36:f5:ed:f4
[  255.002798] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 1/3)
[  255.003590] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 2/3)
[  255.003598] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 3/3)
[  255.003600] wlp6s0: authentication with 48:5d:36:f5:ed:f4 timed out
[  275.376618] wlp6s0: authenticate with 00:25:9c:5c:b2:3e
[  275.378652] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 1/3)
[  275.378815] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 2/3)
[  275.378822] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 3/3)
[  275.378824] wlp6s0: authentication with 00:25:9c:5c:b2:3e timed out
[  282.017253] wlp6s0: authenticate with 48:5d:36:f5:ed:f4
[  282.019201] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 1/3)
[  282.019344] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 2/3)
[  282.019359] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 3/3)
[  282.019363] wlp6s0: authentication with 48:5d:36:f5:ed:f4 timed out
[  302.284830] wlp6s0: authenticate with 00:25:9c:5c:b2:3e
[  302.286973] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 1/3)
[  302.287541] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 2/3)
[  302.287553] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 3/3)
[  302.287554] wlp6s0: authentication with 00:25:9c:5c:b2:3e timed out
[  321.975819] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-cc-a0-52.ucode failed with error -2
[  321.975834] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-cc-a0-51.ucode failed with error -2
[  321.975844] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-cc-a0-50.ucode failed with error -2
[  321.975854] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-cc-a0-49.ucode failed with error -2
[  321.976094] iwlwifi 0000:06:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17
[  321.976096] iwlwifi 0000:06:00.0: Found debug destination: EXTERNAL_DRAM
[  321.976097] iwlwifi 0000:06:00.0: Found debug configuration: 0
[  321.976337] iwlwifi 0000:06:00.0: loaded firmware version 48.4fa0041f.0 cc-a0-48.ucode op_mode iwlmvm
[  321.990970] iwlwifi 0000:06:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[  322.003194] iwlwifi 0000:06:00.0: Applying debug destination EXTERNAL_DRAM
[  322.003598] iwlwifi 0000:06:00.0: Allocated 0x00400000 bytes for firmware monitor.
[  322.151540] iwlwifi 0000:06:00.0: base HW address: 3c:f0:11:3c:25:da
[  322.168261] iwlwifi 0000:06:00.0 wlp6s0: renamed from wlan0
[  322.218207] iwlwifi 0000:06:00.0: Applying debug destination EXTERNAL_DRAM
[  322.366246] iwlwifi 0000:06:00.0: FW already configured (0) - re-configuring
[  322.396603] iwlwifi 0000:06:00.0: Applying debug destination EXTERNAL_DRAM
[  322.543529] iwlwifi 0000:06:00.0: FW already configured (0) - re-configuring
[  329.072369] wlp6s0: authenticate with 48:5d:36:f5:ed:f4
[  329.075272] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 1/3)
[  329.075364] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 2/3)
[  329.075376] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 3/3)
[  329.075378] wlp6s0: authentication with 48:5d:36:f5:ed:f4 timed out
[  339.693267] iwlwifi 0000:06:00.0: Applying debug destination EXTERNAL_DRAM
[  339.842117] iwlwifi 0000:06:00.0: FW already configured (0) - re-configuring
[  339.873629] iwlwifi 0000:06:00.0: Applying debug destination EXTERNAL_DRAM
[  340.021786] iwlwifi 0000:06:00.0: FW already configured (0) - re-configuring
schoolbusesc2@Desktop:~$ 
```

---

### Post by chili555 on 2020-04-15
Your device and driver combination are loading the -48 version of the firmware:

> loaded firmware version [COLOR="#FF0000"]48.[/COLOR]4fa0041f.0 cc-a0-48.ucode op_mode iwlmvmThis post lists the same errors but suggests that you should be loading -46: [https://forum.manjaro.org/t/intel-ax200-wifi-card-unstable-after-firmware-update/127904](https://forum.manjaro.org/t/intel-ax200-wifi-card-unstable-after-firmware-update/127904)

Let's first be certain that you have -46:

```
ls /lib/firmware | grep iwlwifi-cc-a0
```If you have both -46 and -48, we'll rename -48 to force -46 to load and see if it helps:

```
cd /lib/firmware
sudo mv iwlwifi-cc-a0-48.ucode  iwlwifi-cc-a0-48.bak
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi

```
Any improvement?

If not, please show us:

```
dmesg | grep wl
nmcli device wifi list
```

---

### Post by schoolbusesc2 on 2020-04-15
No difference, thought I forgot to mention that what happens is that it keeps going back to the authentication popup "Please enter password." But it still does not work. Both firmwares are there and I tried to force it to use the 46 but still does not work.
Here is dmesg | grep wl:
```

schoolbusesc2@Desktop:~$ dmesg | grep wl
[10140.654643] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-cc-a0-52.ucode failed with error -2
[10140.654660] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-cc-a0-51.ucode failed with error -2
[10140.654671] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-cc-a0-50.ucode failed with error -2
[10140.654681] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-cc-a0-49.ucode failed with error -2
[10140.654703] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-cc-a0-48.ucode failed with error -2
[10140.654717] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-cc-a0-47.ucode failed with error -2
[10140.670252] iwlwifi 0000:06:00.0: loaded firmware version 46.3cfab8da.0 cc-a0-46.ucode op_mode iwlmvm
[10140.686684] iwlwifi 0000:06:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[10140.842486] iwlwifi 0000:06:00.0: base HW address: 3c:f0:11:3c:25:da
[10140.858969] iwlwifi 0000:06:00.0 wlp6s0: renamed from wlan0
[10163.564568] wlp6s0: authenticate with 48:5d:36:f5:ed:f4
[10163.567098] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 1/3)
[10163.567249] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 2/3)
[10163.567255] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 3/3)
[10163.567257] wlp6s0: authentication with 48:5d:36:f5:ed:f4 timed out
[10173.672007] wlp6s0: authenticate with 00:25:9c:5c:b2:3e
[10173.674754] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 1/3)
[10173.674912] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 2/3)
[10173.674931] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 3/3)
[10173.674933] wlp6s0: authentication with 00:25:9c:5c:b2:3e timed out
[10183.779879] wlp6s0: authenticate with 48:5d:36:f5:ed:f4
[10183.781826] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 1/3)
[10183.781951] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 2/3)
[10183.781966] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 3/3)
[10183.781968] wlp6s0: authentication with 48:5d:36:f5:ed:f4 timed out
[10192.839565] wlp6s0: authenticate with 48:5d:36:f5:ed:f4
[10192.842040] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 1/3)
[10192.842145] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 2/3)
[10192.842152] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 3/3)
[10192.842154] wlp6s0: authentication with 48:5d:36:f5:ed:f4 timed out
[10213.141458] wlp6s0: authenticate with 00:25:9c:5c:b2:3e
[10213.143516] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 1/3)
[10213.144670] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 2/3)
[10213.144691] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 3/3)
[10213.144697] wlp6s0: authentication with 00:25:9c:5c:b2:3e timed out
[10221.091495] wlp6s0: authenticate with 48:5d:36:f5:ed:f4
[10221.093117] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 1/3)
[10221.094192] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 2/3)
[10221.094207] wlp6s0: send auth to 48:5d:36:f5:ed:f4 (try 3/3)
[10221.094210] wlp6s0: authentication with 48:5d:36:f5:ed:f4 timed out
[10241.419762] wlp6s0: authenticate with 00:25:9c:5c:b2:3e
[10241.422164] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 1/3)
[10241.423361] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 2/3)
[10241.423372] wlp6s0: send auth to 00:25:9c:5c:b2:3e (try 3/3)
[10241.423376] wlp6s0: authentication with 00:25:9c:5c:b2:3e timed out
schoolbusesc2@Desktop:~$ 

```
And here is nmcli device wifi list (I am trying to connect to Owen 2.4 GHz):
```

schoolbusesc2@Desktop:~$ nmcli device wifi list
IN-USE  SSID                           MODE   CHAN  RATE        SIGNAL  BARS  SE
        Owen Guest                     Infra  11    195 Mbit/s  69      &#9602;&#9604;&#9606;_  WP
        Owen 2.4 GHz                   Infra  11    195 Mbit/s  67      &#9602;&#9604;&#9606;_  WP
        Owen 2.4 GHz                   Infra  1     130 Mbit/s  65      &#9602;&#9604;&#9606;_  WP
        NETGEAR43                      Infra  1     54 Mbit/s   64      &#9602;&#9604;&#9606;_  WP
        Owen 5 GHz                     Infra  149   405 Mbit/s  52      &#9602;&#9604;__  WP
        DIRECT-Ij-FireTV_f428          Infra  149   130 Mbit/s  37      &#9602;&#9604;__  WP
        NETGEAR59                      Infra  6     405 Mbit/s  30      &#9602;___  WP
        Fios-Y67Y5_EXT_2               Infra  1     130 Mbit/s  27      &#9602;___  WP
        DIRECT-97-HP ENVY 7640 series  Infra  1     65 Mbit/s   22      &#9602;___  WP
lines 1-10/10 (END)

```

---

### Post by chili555 on 2020-04-15
> 
Owen 2.4 GHz                   Infra  11    195 Mbit/s  67      &#9602;&#9604;&#9606;_  [COLOR="#FF0000"]WP[/COLOR]
Owen 2.4 GHz                   Infra  1     130 Mbit/s  65      &#9602;&#9604;&#9606;_  WP


WPA WPA2 or WPA2?

We wonder why there are two access ponts with the same name. We clearly see your device trying first one and then the other and failing. If these (this??) is a router for which you have administration priveleges, I'd rename them, perhaps something like Owen1 and Owen2.

Next, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

---

### Post by schoolbusesc2 on 2020-04-16
I do not know why there are two Owen 2.4GHzs. And it is set to use WPA2. So I do not know what that is happening... And after setting the country, it still does not work.

---

### Post by chili555 on 2020-04-17
> I do not know why there are two Owen 2.4GHzs.Your system is definitely attemting to connect to first one and then the other:

> wlp6s0: send auth to [COLOR="#FF0000"]48:5d:36:f5:ed:f4[/COLOR] (try 1/3)

And later:

> wlp6s0: send auth to [COLOR="#FF0000"]00:25:9c:5c:b2:3e[/COLOR] (try 1/3)Perhaps we can find out why the association fails:

```
cat /var/log/syslog | grep etwork
```

As the result may be lengthy, paste the output here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by schoolbusesc2 on 2020-04-17
Here is the output of "cat /var/log/syslog | grep etwork": [https://paste.ubuntu.com/p/dZdg5SRJS2/](https://paste.ubuntu.com/p/dZdg5SRJS2/)

---

### Post by chili555 on 2020-04-18
> Apr 17 11:46:24 Desktop NetworkManager[987]: <info>  [1587138384.4619] device (p2p-dev-wlp6s0): supplicant management interface state: scanning -> authenticating
Apr 17 11:46:24 Desktop NetworkManager[987]: <info>  [1587138384.4968] device (wlp6s0): supplicant interface state: authenticating -> disconnected
Apr 17 11:46:24 Desktop NetworkManager[987]: <info>  [1587138384.4969] device (p2p-dev-wlp6s0): supplicant management interface state: [COLOR="#FF0000"]authenticating -> disconnected[/COLOR]
Apr 17 11:46:24 Desktop NetworkManager[987]: <info>  [1587138384.5969] device (wlp6s0): supplicant interface state: disconnected -> scanning
Apr 17 11:46:24 Desktop NetworkManager[987]: <info>  [1587138384.5969] device (p2p-dev-wlp6s0): supplicant management interface state: disconnected -> scanning
Apr 17 11:46:24 Desktop NetworkManager[987]: <info>  [1587138384.6368] device (wlp6s0): supplicant interface state: scanning -> authenticating
Apr 17 11:46:24 Desktop NetworkManager[987]: <info>  [1587138384.6369] device (p2p-dev-wlp6s0): supplicant management interface state: scanning ->[COLOR="#FF0000"] authenticating[/COLOR]
Apr 17 11:46:24 Desktop NetworkManager[987]: <info>  [1587138384.6798] device (wlp6s0): supplicant interface state: authenticating -> [COLOR="#FF0000"]disconnected[/COLOR]Is your router on a fixed channel as I recommended? Is the password triple verified as correct? Is the behavior changed at all if the router is rebooted? Did you make the 802.11ax parameter permanent?

I regeret that I haven't any other useful suggestions.

---

