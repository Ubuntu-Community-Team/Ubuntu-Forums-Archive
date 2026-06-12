---
title: "Trying to solve an activation failed using solutions from the web make things worse"
date: 2017-05-12
forum: Networking &amp; Wireless
---

### Post by asafyu on 2017-05-12
Hello, I am new to ubuntu.
I installed ubuntu 17.04 via [COLOR=#545454][FONT=arial]USB flash drive [/FONT][/COLOR]to dual boot with WIN10 on my ASUS Zenbook UX303LA(there isn't an RJ-45 Ethernet socket)

I try to connect to my home network with no success.
I got this message:
> connection activation failed "(24) timeout" was reached
I was able to connect to my hotspot(to the smartphone) and connect to another wifi but still wasn't able to connect to my home network.
I searched for solution 
I try:
```
[COLOR=#111111][FONT=Consolas]sudo /etc/init.d/network-manager stop[/FONT][/COLOR]
```
and nothing [COLOR=#202020][FONT=Arial]happened, the cursor blinked for few seconds and nothing else happend.[/FONT]
[/COLOR]I try:
```
[COLOR=#111111][FONT=Consolas]sudo /etc/init.d/network-manager start[/FONT][/COLOR]
```
and still [COLOR=#111111]nothing [/COLOR][COLOR=#202020][FONT=Arial]happened.

I restarted the computer to check if I made changes but the restart took ages so I pressed the shutdown button for few seconds and force it.
Now, the [/FONT][/COLOR]WiFi icon missing on the right side of the upper panel
When I enter to Network through setting, the setting window colors are turned to white and grey color for some seconds and I get a message:
> The system network services are not compatible with this version. 

When I boot up WIN10, the wifi works and I connect successfully to my home network wifi.

Sometimes I connect with a wire using USB Ethernet adapter.
When I connect it while running ubuntu,nothing happens.

How do I fix all these problems.

Thanks.


**Edit:**
I was able to connect, here is my wireless info:
[http://paste.ubuntu.com/24575575/](http://paste.ubuntu.com/24575575/)

---

### Post by wildmanne39 on 2017-05-12
What is DOK, you used some new method to install?

Holding down the power button causes data corruption and hard drive damage quit often.

Please run the wireless script in my signature.
Thanks

---

### Post by asafyu on 2017-05-13
I mean [COLOR=#545454][FONT=arial]USB flash drive.
[/FONT][/COLOR]There isn't an RJ-45 Ethernet socket in my laptop so I can't use a wired internet connection.

I download and ran the wireless info script,nothing happened.

How can I solve this?

Thanks.

---

### Post by wildmanne39 on 2017-05-13
Did you have your computer tethered to a cell phone or something of the like when you ran the wireless script? it should have asked you to place the file on pastebin and it also would have created the file in your home directory, we need to see the file so we can help you.
Thanks

---

### Post by asafyu on 2017-05-13
The WiFi icon missing on the right side of the upper panel so I can't connect it to network.

---

### Post by wildmanne39 on 2017-05-13
>  I download and ran the wireless info script,nothing happened.
How did you download the wireless script then?

You can hook your cell phone if it has a hotspot to your computer through an usb port then turn on tethering on your phone and you should have an internet connection even without the network icon.

---

### Post by asafyu on 2017-05-13
When I turn on the laptop, in the login screen the WiFi icon is exist and and if I use USB tethering with my phone so in the upper panel there is an up/down internet connection symbol(*Network Icon)** but when I log in those icons are missing and I don't have internet connection*[I].

Why?

Thanks.[/I]

---

### Post by wildmanne39 on 2017-05-13
Because you corrupted files when you  held the power button down, let's get the information the long way and see if we can figure it out, but this is going to be very hard if you have no connection at all.

Please do:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
by clicking on new reply and click # then paste the information between the brackets.
Thank you
```

---

### Post by asafyu on 2017-05-13
> **wildmanne39 said:**
> How did you download the wireless script then?


I downloaded it from another pc and copied to external hard drive,connect the hard drive to the laptop and copied the file to ubuntu desktop.
[http://i.imgur.com/8HK36dO.png](http://i.imgur.com/8HK36dO.png)
when I ran [COLOR=#000000][FONT=&quot]iwconfig, the [/FONT][/COLOR]cursor blinked for few seconds and nothing else happend.

---

### Post by wildmanne39 on 2017-05-13
Run the commands one at a time, then copy to a flash drive then paste into one single post here, see I have old man eye syndrome I can not see the writing in the image you supplied no matter how hard I try.
Thanks

---

### Post by asafyu on 2017-05-13
```
asafy@asafy-UX303LAB:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.04
DISTRIB_CODENAME=zesty
DISTRIB_DESCRIPTION="Ubuntu 17.04"
Linux asafy-UX303LAB 4.10.0-20-generic #22-Ubuntu SMP Thu Apr 20 09:22:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

```
asafy@asafy-UX303LAB:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
                Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5110]
                Kernel driver in use: iwlwifi
```

```
asafy@asafy-UX303LAB:~$ lsusb 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 03eb:8b05 Atmel Corp. 
Bus 001 Device 002: ID 064e:9700 Suyin Corp. Asus Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
asafy@asafy-UX303LAB:~$ iwconfig
 

```

```
asafy@asafy-UX303LAB:~$ rfkill list all
0: phy0: Wireless LAN
                Soft blocked: no
                Hard blocked: no
1: asus-wlan: Wireless LAN
                Soft blocked: no
                Hard blocked: no
2: asus-bluetooth: Bluetooth
                Soft blocked: yes
                Hard blocked: no
 
 
asafy@asafy-UX303LAB:~$ lsmod
Module                  Size  Used by
ses                    20480  0
enclosure              16384  1 ses
scsi_transport_sas     40960  1 ses
uas                    24576  0
usb_storage            69632  1 uas
bnep                   20480  2
snd_hda_codec_hdmi     49152  1
nls_iso8859_1          16384  1
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
hid_multitouch         20480  0
hid_generic            16384  0
bluetooth             557056  11 btrtl,btintel,bnep,btbcm,btusb
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             200704  0
kvm                   593920  1 kvm_intel
arc4                   16384  2
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_soc_rt5640        118784  0
ghash_clmulni_intel    16384  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          233472  1 snd_soc_rt5640
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
pcbc                   16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
uvcvideo               90112  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
iwlmvm                368640  0
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_hda_codec_conexant    24576  1
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_hda_codec_generic    73728  1 snd_hda_codec_conexant
mac80211              782336  1 iwlmvm
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
snd_hda_intel          36864  4
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
intel_cstate           20480  0
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_codec_generic
joydev                 20480  0
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
intel_rapl_perf        16384  0
media                  40960  2 uvcvideo,videodev
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec_conexant,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic
input_leds             16384  0
snd_hwdep              16384  1 snd_hda_codec
iwlwifi               229376  1 iwlmvm
serio_raw              16384  0
intel_pch_thermal      16384  0
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
cfg80211              602112  3 iwlmvm,iwlwifi,mac80211
lpc_ich                24576  0
snd_pcm               102400  7 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
usbhid                 53248  0
mei_me                 40960  0
processor_thermal_device    16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
shpchp                 36864  0
mei                   102400  1 mei_me
intel_soc_dts_iosf     16384  1 processor_thermal_device
snd_timer              32768  2 snd_seq,snd_pcm
elan_i2c               36864  0
dw_dmac                16384  0
dw_dmac_core           24576  1 dw_dmac
snd                    77824  21 snd_compress,snd_hda_intel,snd_hwdep,snd_hda_codec_conexant,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_soc_core,snd_pcm
snd_soc_sst_acpi       16384  0
snd_soc_sst_match      16384  1 snd_soc_sst_acpi
soundcore              16384  1 snd
8250_dw                16384  0
i2c_designware_platform    16384  0
int3402_thermal        16384  0
acpi_pad              180224  0
i2c_designware_core    20480  1 i2c_designware_platform
int340x_thermal_zone    16384  2 int3402_thermal,processor_thermal_device
spi_pxa2xx_platform    24576  0
int3406_thermal        16384  0
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
mac_hid                16384  0
int3400_thermal        16384  0
industrialio           69632  2 acpi_als,kfifo_buf
acpi_thermal_rel       16384  1 int3400_thermal
asus_wireless          16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
i915                 1449984  107
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
psmouse               139264  0
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  3
drm                   352256  5 i915,drm_kms_helper
libahci                32768  1 ahci
wmi                    16384  1 asus_wmi
sdhci_acpi             16384  0
sdhci                  45056  1 sdhci_acpi
video                  40960  3 asus_wmi,int3406_thermal,i915
i2c_hid                20480  0
hid                   114688  4 i2c_hid,hid_generic,usbhid,hid_multitouch
fjes                   73728  0

```

when ran this command: ```
iwconfig


```
nothing happens and when I try to exit the terminal, I get this message:
> There is still a process running in this terminal. Closing the terminal will kill it.


So, for this command:```
lsmod


```
I closed Terminal and open a new one.

---

### Post by wildmanne39 on 2017-05-13
I am researching this issue, I helped in the past with the same problem but it was on 14.04 so I need to find the solution that will work with 17.04.
[https://ubuntuforums.org/showthread.php?t=2324504](https://ubuntuforums.org/showthread.php?t=2324504)

Is it a bug in network manager if you reinstalled the older version of network manager before you updated and put a hold on it so it could not be upgraded again that would fix the issue, but I need to see where to get the older version.

---

### Post by wildmanne39 on 2017-05-13
From your installed ubuntu do:
```
sudo apt remove --purge network-manager
```
Then switch to the live ubuntu version, which you sholud have an internet connection and do:
```
sudo apt-get download network-manager*
```
This will download all the network-manager packages to the home directory.

Now copy all the .deb packages to the home folder on your ubuntu drive and then reboot to your system and do:
```
cd /home/username
sudo dpkg -i *.deb
```
watch for errors.
Then do:
```
sudo systemctl restart NetworkManager.service
```
You should have internet back, then we need to lock it so network manager does not update until there is a fix for this issue.


Do:
```
sudo apt-mark hold network-manager-gnome
```

---

### Post by fyfe54 on 2017-05-13
Thanks, I'll try this when I get some free time tomorrow, which is Mothers' Day in this part of the world.  I'll let you know how I make out.

---

### Post by asafyu on 2017-05-14
[QUOTE=wildmanne39;13644867]From your installed ubuntu do:
```
sudo apt remove --purge network-manager
```
Then switch to the live ubuntu version, which you sholud have an internet connection and do:
```
sudo apt-get download network-manager*
```
This will download all the network-manager packages to the home directory.
/QUOTE]

What do you mean when you refer to installed ubuntu and live ubuntu version?

I ran this:```
sudo apt remove --purge network-manager
```
and nothing happens when [COLOR=#000000]I try to exit the terminal, I get this message:[/COLOR]
[COLOR=#000000][I]There is still a process running in this terminal. Closing the terminal will kill it.


[/I]
[/COLOR]

---

### Post by wildmanne39 on 2017-05-14
>  What do you mean when you refer to installed ubuntu and live ubuntu version?
Installed ubuntu is the ubuntu you put on your hard drive, live version is the usb flash drive that you installed ubuntu from, when the live version boots instead of choosing install choose to try ubuntu then you run the commands from the live version of ubuntu.

---

### Post by asafyu on 2017-05-14
I'm not at home right now and I was able to connect to the internet.
What I need to do to assure that at my home I will able to connect to...?

Thanks.

Edit:
Here is my wireless info:
[http://paste.ubuntu.com/24575575/](http://paste.ubuntu.com/24575575/)

---

### Post by wildmanne39 on 2017-05-14
Did you run the script from your home network? that way we can see the settings and have a better idea of what is wrong.

---

### Post by asafyu on 2017-05-15
no.
I ran it from another network.

I understood what causes the problem, at the moment I try to connect to 5GHz network like my home network, my hotspot 5GHz network, etc.
this damages the internet connection capabilities and if I try to shut down/restart the system, it's take ages for doing that.
After the restart, I connect to 2.4GHz network and suddenly it's connects, if I try to shut down/restart the system, it's takes number of seconds to do that.


Why I can't connect to 5GHz network?
Thanks.

---

### Post by wildmanne39 on 2017-05-15
We need to see the output from the wireless script from the network you can not connect to so we can see what might be wrong, since you have already ran the wireless script once you do not have to download it again just run this command:
```
./wireless-info
```
Thanks

---

### Post by asafyu on 2017-05-15
I already tried to connect to several 5GHz networks, with no success.
The WiFi icon is blinking and I can't do nothing, not even disconnect.
If try to run the script, the mouse cursor shows 'busy' status and nothing happens.

The problem is with 5GHz networks, is there specific driver for that?

Thanks.

---

### Post by wildmanne39 on 2017-05-16
The driver is the same, there is only one, if your computer acts up when you run the script then you have something else wrong.

Without that information there is not much we can do, but you can set your router to channel 40, and encryption to just wpa2.

I have no further suggestions.

---

