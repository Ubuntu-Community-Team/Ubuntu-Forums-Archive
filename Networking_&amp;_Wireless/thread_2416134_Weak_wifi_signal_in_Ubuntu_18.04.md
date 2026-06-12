---
title: "Weak wifi signal in Ubuntu 18.04"
date: 2019-04-05
forum: Networking &amp; Wireless
---

### Post by saikiransripada on 2019-04-05
Hello, I've had weak wifi signal problems in the past when I was using Ubuntu 16.04. So, I've upgraded to Ubuntu 18.04. My other laptop which has a Windows OS installed shows a strong wifi signal strength whereas Ubuntu 18.04 shows a weak wifi signal strength. Can someone help me fix this issue? Thanks.

---

### Post by jeremy31 on 2019-04-05
See the wireless script link in my signature and post results

---

### Post by saikiransripada on 2019-04-05
Please see the attached file for the wireless information results.

---

### Post by chili555 on 2019-04-06
> 
SSS's  <MAC 'SSS's' [AN1]>  Infra  7     2442 MHz  130 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  yes     *      
Channel 7?? Did you set that explicitely or is your router set to auto channel select; or, as I like to call it, 'As soon as we agree on a suitable channel, I'll move it! Good luck finding me!'

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

We also see many failed attempts to set probably needless module parameters. Let's do some spring housecleaning. From the terminal:```
sudo rm /etc/modprobe.d/50-rtl8723be.conf
sudo rm /etc/modprobe.d/iwlagn.conf
sudo rm /etc/modprobe.d/iwlwifi-opt.conf
```Next, you have improperly overwritten the crucial file /etc/modprobe.d/iwlwifi.conf. Let's fix it:```

sudo nano /etc/modprobe.d/iwlwifi.conf


```Remove everything there and replace it with:```

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


```Save (Ctrl+o followed by Enter) and exit (Ctrl+x) the text editor.

Reboot and tell us if there is any improvement.

---

### Post by saikiransripada on 2019-04-06
Hey, chili555. First off, thanks for taking time to post this. I believe this problem is not router specific as I've problems connecting various wireless networks. However, I've set router encryption to WPA2, channel to 11 (fixed), band to 20M. 
> **chili555 said:**
> Channel 7?? Did you set that explicitely or is your router set to auto channel select; or, as I like to call it, 'As soon as we agree on a suitable channel, I'll move it! Good luck finding me!'

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

I've set my country code.
> **chili555 said:**
> Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Removed the below files.
> **chili555 said:**
> We also see many failed attempts to set probably needless module parameters. Let's do some spring housecleaning. From the terminal:```
sudo rm /etc/modprobe.d/50-rtl8723be.conf
sudo rm /etc/modprobe.d/iwlagn.conf
sudo rm /etc/modprobe.d/iwlwifi-opt.conf
```

Fixed the configuration and rebooted.
> **chili555 said:**
> Next, you have improperly overwritten the crucial file /etc/modprobe.d/iwlwifi.conf. Let's fix it:```

sudo nano /etc/modprobe.d/iwlwifi.conf


```Remove everything there and replace it with:```

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


```Save (Ctrl+o followed by Enter) and exit (Ctrl+x) the text editor.

Reboot and tell us if there is any improvement.

Sorry, but I don't see any improvement.

---

### Post by chili555 on 2019-04-06
What does the signal strength show here?

```
nmcli dev wifi list
```Is it possible that one of the antenna connections is not firmly snapped in place?

[https://blog.syddel.uk/wp-content/uploads/2017/07/Intel8260-720x340.jpg](https://blog.syddel.uk/wp-content/uploads/2017/07/Intel8260-720x340.jpg)

---

### Post by saikiransripada on 2019-04-06
> **chili555 said:**
> What does the signal strength show here?
```
nmcli dev wifi list
```

Here's the signal strength when I sit in the same room as wifi.
```

user@ubuntu:~$ nmcli dev wifi list
IN-USE  SSID        MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
*       SSS's       Infra  11    130 Mbit/s  30      &#9602;___  WPA2     
user@ubuntu:~$ nmcli dev wifi list
IN-USE  SSID        MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
*       SSS's       Infra  11    130 Mbit/s  32      &#9602;&#9604;__  WPA2     
user@ubuntu:~$ nmcli dev wifi list
IN-USE  SSID        MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
*       SSS's       Infra  11    130 Mbit/s  31      &#9602;&#9604;__  WPA2     
user@ubuntu:~$ nmcli dev wifi list
IN-USE  SSID        MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
*       SSS's       Infra  11    130 Mbit/s  30      &#9602;___  WPA2 

```

Here's the signal strength when I sit near to my router.
```

user@ubuntu:~$ nmcli dev wifi list
IN-USE  SSID        MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
*       SSS's       Infra  11    130 Mbit/s  54      &#9602;&#9604;__  WPA2

```

Here's the signal strength when I sit right next (literally) to my router.
```

user@ubuntu:~$ nmcli dev wifi list
IN-USE  SSID        MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
*       SSS's       Infra  11    130 Mbit/s  63      &#9602;&#9604;&#9606;_  WPA2     
user@ubuntu:~$ nmcli dev wifi list
IN-USE  SSID        MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
*       SSS's       Infra  11    130 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2

```

> **chili555 said:**
> Is it possible that one of the antenna connections is not firmly snapped in place?

[https://blog.syddel.uk/wp-content/uploads/2017/07/Intel8260-720x340.jpg](https://blog.syddel.uk/wp-content/uploads/2017/07/Intel8260-720x340.jpg)

I'm not sure about this one though. Because I've never disassembled my laptop before.

---

### Post by chili555 on 2019-04-06
I am about 6.5 meters from my wireless router and it is in a closet. I get:```

        GBR1                   Infra  1     195 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA2      
[COLOR="#FF0000"]*       GBR5                   Infra  149   405 Mbit/s  **79**      &#9602;&#9604;&#9606;_  WPA2      [/COLOR]
        nx2.4                  Infra  11    195 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1 WPA2 
        MC5                    Infra  153   195 Mbit/s  39      &#9602;&#9604;__  WPA2      
        MC1                    Infra  11    130 Mbit/s  30      &#9602;___  WPA2      
        Portal                 Infra  1     195 Mbit/s  29      &#9602;___  WPA2      
        --                     Infra  153   130 Mbit/s  24      &#9602;___  WPA2      
        --                     Infra  1     65 Mbit/s   20      &#9602;___  --        
        DIRECT-X7-FireTV_69ab  Infra  153   130 Mbit/s  17      &#9602;___  WPA2      
        MySpectrumWiFi2b-2G    Infra  6     540 Mbit/s  10      &#9602;___  WPA2    



```I know that both of the antenna wires are connected because I put them there! For what it's worth, I have a similar Intel 7260.

Does your router have a signal strength setting? What is it set to? [https://ejquo23388.i.lithium.com/t5/image/serverpage/image-id/8134iED047E6B87C72E09?v=1.0](https://ejquo23388.i.lithium.com/t5/image/serverpage/image-id/8134iED047E6B87C72E09?v=1.0)

---

### Post by saikiransripada on 2019-04-06
> **chili555 said:**
> I am about 6.5 meters from my wireless router and it is in a closet. I get:```

        GBR1                   Infra  1     195 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA2      
[COLOR=#FF0000]*       GBR5                   Infra  149   405 Mbit/s  **79**      &#9602;&#9604;&#9606;_  WPA2      [/COLOR]
        nx2.4                  Infra  11    195 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1 WPA2 
        MC5                    Infra  153   195 Mbit/s  39      &#9602;&#9604;__  WPA2      
        MC1                    Infra  11    130 Mbit/s  30      &#9602;___  WPA2      
        Portal                 Infra  1     195 Mbit/s  29      &#9602;___  WPA2      
        --                     Infra  153   130 Mbit/s  24      &#9602;___  WPA2      
        --                     Infra  1     65 Mbit/s   20      &#9602;___  --        
        DIRECT-X7-FireTV_69ab  Infra  153   130 Mbit/s  17      &#9602;___  WPA2      
        MySpectrumWiFi2b-2G    Infra  6     540 Mbit/s  10      &#9602;___  WPA2    



```I know that both of the antenna wires are connected because I put them there! For what it's worth, I have a similar Intel 7260.

Does your router have a signal strength setting? What is it set to? [https://ejquo23388.i.lithium.com/t5/image/serverpage/image-id/8134iED047E6B87C72E09?v=1.0](https://ejquo23388.i.lithium.com/t5/image/serverpage/image-id/8134iED047E6B87C72E09?v=1.0)

Yup! I set the signal strength to strongest. Please see the attached screenshot.

---

### Post by chili555 on 2019-04-06
If there is no improvement, then check the antenna wires, please.

---

### Post by saikiransripada on 2019-04-06
> **chili555 said:**
> If there is no improvement, then check the antenna wires, please.
Sorry, but this is not happening with the Windows PC. Can I upgrade my kernel and see if that works?

Here's my current kernel version:
```

user@ubuntu:~$ uname -r
4.15.0-47-generic

```

---

### Post by chili555 on 2019-04-06
I suggest that you download the iso for Ubuntu 18.10, which uses kernel version 4.18.0-xx and try a live session. If it works as expected, install it.

---

### Post by saikiransripada on 2019-04-07
> **chili555 said:**
> I suggest that you download the iso for Ubuntu 18.10, which uses kernel version 4.18.0-xx and try a live session. If it works as expected, install it.

Can I update the kernel version using Ukuu without the hassale of re-installing the Ubuntu?

---

### Post by jeremy31 on 2019-04-07
You can install the 4.18 kernel in 18.04 see [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop)

---

### Post by saikiransripada on 2019-04-07
> **jeremy31 said:**
> You can install the 4.18 kernel in 18.04 see [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop)

Updated but the issue still remains the same. :(
```
user@ubuntu:~$ uname -r
4.18.0-17-generic
```

---

### Post by saikiransripada on 2019-04-08
Will updating the wireless network drivers help? If so, how can I update the wireless network device drivers?

---

### Post by chili555 on 2019-04-08
> **saikiransripada said:**
> Will updating the wireless network drivers help? If so, how can I update the wireless network device drivers?You could certainly try, however, I am skeptical. 

Here is the process: [https://askubuntu.com/questions/1046589/backport-for-iwlwifi](https://askubuntu.com/questions/1046589/backport-for-iwlwifi)

---

### Post by saikiransripada on 2019-04-08
> **chili555 said:**
> You could certainly try, however, I am skeptical. 

Here is the process: [https://askubuntu.com/questions/1046589/backport-for-iwlwifi](https://askubuntu.com/questions/1046589/backport-for-iwlwifi)

Thanks, chili555. I ran all commands specified by Jeremy31. However, the last one gave me a series of errors. :(

At this point, I cannot decide whether this is a software issue or hardware. Is there any way to check if it is a hardware issue without installing a new OS?

---

### Post by chili555 on 2019-04-08
> **saikiransripada said:**
> Thanks, chili555. I ran all commands specified by Jeremy31. However, the last one gave me a series of errors. :(

At this point, I cannot decide whether this is a software issue or hardware. Is there any way to check if it is a hardware issue without installing a new OS?Perhaps Jeremy can comment as to the compile errors.

I am sorry, I still suspect the antenna connections. Again, perhaps Jeremy will have another opinion.

---

### Post by jeremy31 on 2019-04-08
> **saikiransripada said:**
> Thanks, chili555. I ran all commands specified by Jeremy31. However, the last one gave me a series of errors. :(

At this point, I cannot decide whether this is a software issue or hardware. Is there any way to check if it is a hardware issue without installing a new OS?

I think those errors can be ignored, reboot.  Most of it has to do with Secure Boot and it isn't enabled on your computer

---

### Post by saikiransripada on 2019-04-09
> **chili555 said:**
> Perhaps Jeremy can comment as to the compile errors.

I am sorry, I still suspect the antenna connections. Again, perhaps Jeremy will have another opinion.

Thanks, Chili555.

> **jeremy31 said:**
> I think those errors can be ignored, reboot.  Most of it has to do with Secure Boot and it isn't enabled on your computer

Thanks, Jeremy.

I see something wrong with the iwlwifi logs.
```
dmesg | grep iwlwifi [    7.519786] Loading modules backported from iwlwifi
[    7.519786] iwlwifi-stack-public:master:7684:f0e8b34c
[    7.853562] iwlwifi 0000:02:00.0: Direct firmware load for iwl-dbg-cfg.ini failed with error -2
[    8.032220] iwlwifi 0000:02:00.0: loaded firmware version 36.9f0a2d68.0 op_mode iwlmvm
[    8.107090] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[    8.184771] iwlwifi 0000:02:00.0: base HW address: e4:b3:18:18:5b:69
[    8.403243] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[   78.886678] iwlwifi 0000:02:00.0: No beacon heard and the time event is over already...

```

Is there any way to fix the below errors?
```
[ 7.853562] iwlwifi 0000:02:00.0: Direct firmware load for iwl-dbg-cfg.ini failed with error -2
```

```
[   78.886678] iwlwifi 0000:02:00.0: No beacon heard and the time event is over already...
```

---

### Post by chili555 on 2019-04-09
> [ 7.853562] iwlwifi 0000:02:00.0: Direct firmware load for iwl-dbg-cfg.ini failed with error -2I doubt that this is of any significance. First, the firmware isn't even called for in the driver, as far as I can see. Check:```
modinfo iwlwifi | grep ini
```Second, a Google search for 'iwl-dbg-cfg.ini' doesn't even suggest that the file is available anywhere. It is certainly not here, the usual canonical resource: [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/)

Second, linux drivers often look for firmware files and, not finding one particular version, go down the list to the next candidate. Once it finds a suitable file, it loads and proceeds. That is exactly what happens in your case:> loaded firmware version 36.9f0a2d68.0 op_mode iwlmvm

> [   78.886678] iwlwifi 0000:02:00.0: No beacon heard and the time event is over already...That simply means that the signal strength is so low, the wireless device can't detect, or hear, the beacon ("HI! I'm a wireless router. If you have my password, we can connect. I'll give you internet access.") It appears that updating the iwlwifi driver didn't help at all.

---

