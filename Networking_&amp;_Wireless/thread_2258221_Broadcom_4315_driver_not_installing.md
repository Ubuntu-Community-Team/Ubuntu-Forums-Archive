---
title: "Broadcom 4315 driver not installing"
date: 2014-12-25
forum: Networking &amp; Wireless
---

### Post by joshua_bankhead on 2014-12-25
I have a Dell Inspirion 1545
2g ram
intel celeron

when i check the command prompt

[quote=code]
          lspci -nn -d 14e4:[/quote]

i get
> 

network controller [o280]: broadcom corporation bcm4312 802.11b/g 

[41e4:4315] 
I followed the directions on the sticky trying to install the firmware-b43-lhppy-installer.

when i enter this i get a message that

> package firmware-b43-lpphy-installer is not available, but is refered to ther package

then it refers me to firmware-b4-installer.

i have installed this and am not able to see the drivers in the settings window nor can i detect wifi in the network settings

does any one have an idea of what i can do to repair this i'd greatly appreciate it.

i am a noob at using command prompts in the terminal. so please be patient with me.

josh

---

### Post by Hadaka on 2014-12-25
Hi, open a terminal and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rf b43
sudo modprobe b43
```
boot
is it working now?

---

### Post by binchunsu on 2014-12-26
I am also using Dell Inspiron and when I first installed Ubuntu, the  wireless was also not working. I fixed it by plugging in the ethernet  cable and running this command in the terminal: "sudo apt-get  install firmware-b43-installer". After rebooting wireless was working.

---

### Post by Hadaka on 2014-12-26
@binchunsu
you should also do..
```
sudo apt-get update
```
and please post your own thread next time
thanks

---

### Post by joshua_bankhead on 2014-12-26
Thank you guys for the help.

The laptop belngs to my Mother in law and i convinced her to make the switch. I will get to his by the end of the week and reply back.

Thanks a ton!

Josh

---

### Post by praseodym on 2014-12-27
Same as here:

[http://ubuntuforums.org/showthread.php?t=2258229&p=13195161#post13195161](http://ubuntuforums.org/showthread.php?t=2258229&p=13195161#post13195161)

---

### Post by joshua_bankhead on 2014-12-28
> **Hadaka said:**
> Hi, open a terminal and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rf b43
sudo modprobe b43
```
boot
is it working now?
i tried this and the update and still no luck.

when i go Into the settings menu, under networking, i can now see the wireless option.  But, i cannot turn the device/option on.

I attempted and update - Sudo apt-get update- in teminal and nothing.

thanks

Josh

---

### Post by joshua_bankhead on 2014-12-28
> **praseodym said:**
> Same as here:

[http://ubuntuforums.org/showthread.php?t=2258229&p=13195161#post13195161](http://ubuntuforums.org/showthread.php?t=2258229&p=13195161#post13195161)

i am getting a 404 not found error code with the attachment/ web link

*update*

i just figured out i can copy-paste into terminal.  I must have mistyped the code the first time i  entered it.

the second time i entered it it did DL, but i am still not able to use the wireless connection.

the wireless network option shows on the settings window but i cannot turn it on

---

### Post by chili555 on 2015-02-23
Let's get this Broadcom working. First, see if you have the required firmware:```
sudo ls /lib/firmware/b43
```We needn't see the entire output; just tell us if it is missing or empty or if you have dozens of firmware files like this:```
a0g0bsinitvals5.fw     lcn400initvals33.fw    sslpn1bsinitvals20.fw
a0g0bsinitvals9.fw     lp0bsinitvals13.fw     sslpn1bsinitvals27.fw
a0g0initvals5.fw       lp0bsinitvals14.fw     sslpn1initvals20.fw
a0g0initvals9.fw       lp0bsinitvals15.fw     sslpn1initvals27.fw
a0g1bsinitvals13.fw    lp0bsinitvals16.fw     sslpn2bsinitvals19.fw
<snip>
```Second,is the wireless blocked by the hardware switch or key combination?```
rfkill list all
```If you see 'Hard Blocked: yes,' then find the switch and enable the wireless.

Is the driver loaded?```
lsmod | grep b43
```If not, load it:```
sudo modprobe b43
```Finally, are there any errors in the message logs?```
dmesg | grep -e b43 -e wlan
```My rent money is bet on rfkill.

---

### Post by DCO on 2015-02-23
This site helped me figure out which way and what driver to configure my broadcom driver with:

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

The third or fourth post down it has a table of model and which driver(s) it uses. Hope it helps.

---

### Post by joshua_bankhead on 2015-02-23
> **chili555 said:**
> Let's get this Broadcom working. First, see if you have the required firmware:```
sudo ls /lib/firmware/b43
```We needn't see the entire output; just tell us if it is missing or empty or if you have dozens of firmware files like this:

Yes dozens listed.
> **chili555 said:**
> Second,is the wireless blocked by the hardware switch or key combination?```
rfkill list all
```If you see 'Hard Blocked: yes,' then find the switch and enable the wireless.
 when i run ```
rfkill list all
``` this comes up.
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```
> 
Is the driver loaded? ]My rent money is bet on rfkill.
when i run ```
lsmod | grep b43
```

i get
```

b43                   387371  0 
bcma                   52096  1 b43
mac80211              630669  1 b43
cfg80211              484040  2 b43,mac80211
ssb                    62379  1 b43

```

when trying to install the edimax usb device i disabled the drivers in the "software and drivers" icon in the settings menu.

when i attempt to re enable them now it tells me the device is not working and automatically goes to the "disable" option.

---

### Post by chili555 on 2015-02-23
> 0: phy0: Wireless LAN
    Soft blocked: no
   [COLOR="#FF0000"] Hard blocked: yes[/COLOR]Please find the wireless switch or key combination, Fn+F4 or some such, and move it to enable wireless.

What brand and model laptop is it? May we see:```
lsmod
```

---

### Post by joshua_bankhead on 2015-02-23
this is a Dell inspirion 1545
i googled the function to activate wireless and it is FN F2 i tried this then tried enabling the drivers for broadcom and it still doesnt work.

lsmod=
```
Module                  Size  Used by
arc4                   12608  2 
b43                   387371  0 
bcma                   52096  1 b43
mac80211              630669  1 b43
cfg80211              484040  2 b43,mac80211
snd_hda_codec_idt      54762  1 
rfcomm                 69160  0 
bnep                   19624  2 
snd_hda_intel          56531  6 
bluetooth             391136  10 bnep,rfcomm
snd_hda_codec         192906  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
i915                  784111  4 
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
drm_kms_helper         55071  1 i915
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
dell_wmi               12761  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
sparse_keymap          13948  1 dell_wmi
gpio_ich               13476  0 
drm                   303102  5 i915,drm_kms_helper
snd                    69322  22 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
coretemp               13435  0 
i2c_algo_bit           13413  1 i915
joydev                 17381  0 
wmi                    19177  1 dell_wmi
serio_raw              13462  0 
parport_pc             32701  0 
soundcore              12680  1 snd
video                  19476  1 i915
ppdev                  17671  0 
lpc_ich                21080  0 
mac_hid                13205  0 de]
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ums_realtek            18029  0 
usb_storage            62209  1 ums_realtek
psmouse               106714  0 
ahci                   29915  2 
ssb                    62379  1 b43
libahci                32716  1 ahci
sky2                   58191  0 


```

i went into the boot menu and made sure it was enabled there as well.  still no change

---

### Post by chili555 on 2015-02-23
It appears to be a dedicated wireless button. Do you have that? Does it change this?```
rfkill list all
```

[ATTACH=CONFIG]260185[/ATTACH]

---

### Post by joshua_bankhead on 2015-02-23
> **chili555 said:**
> It appears to be a dedicated wireless button. Do you have that? Does it change this?```
rfkill list all
```

[ATTACH=CONFIG]260185[/ATTACH]

yes that is the fn+f2 button

nothing is happening when i use it

when i run "rfkill list all" i get nothing

---

### Post by chili555 on 2015-02-23
It appears to me that the wireless is activated by pressing that button alone and not in combination with Fn. Is that what you meant?> when i run "rfkill list all" i get nothing A few posts back, you did.> when i run
```
rfkill list all

```
this comes up.
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
``` Are you saying the command returns nothing now or that it returns no change from 'Hardblocked: yes' after you press F2?

---

### Post by joshua_bankhead on 2015-02-23
when i enter the command nothing happens

it was working earlier

now ```
norma@norma-Inspiron-1545:~$ rfkill list all
norma@norma-Inspiron-1545:~$ 


```

---

### Post by joshua_bankhead on 2015-02-23
the command returns nothing

---

### Post by joshua_bankhead on 2015-02-24
Chili

i went back through the steps you gave me and re did everything and it worked.
somehow i purged the firm ware or drivers and i had to start over from the begining.

Thanks a ton for all of your help.

i am messaging now from the laptop using its wifif card.

yours 
Josh

---

### Post by chili555 on 2015-02-24
Awesome! Glad it's working!

---

### Post by joshua_bankhead on 2015-02-24
I just got a call from my Mother in law that the wifi card is not working anymore.

Any suggestions as to why this card would turn itself off? 

I had my daughter (over the phone) try to enable the card using the FN F2 option and tried running the command rfkill list all in terminal

She says nothing came from the rfkill command, which makes me think the card is disabled.

Is this a bug?

---

### Post by praseodym on 2015-02-25
Driver is loaded?
```

sudo modprobe -rfv brcmsmac b43
sudo modprobe -v b43
```

---

