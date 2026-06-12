---
title: "Wi-Fi is disabled by hardware switch and I have Fn+F2 mis-mapped too"
date: 2014-05-04
forum: Networking &amp; Wireless
---

### Post by mmelzalabany on 2014-05-04
I know this is like the millionth post of some wireless adapter that doesn't work, but I lost all hope in reading forums and answers that were meant to specific devices, with no general answer that works on all devices.

Of course, after 3 days of investigation, and after I changed my driver to b43, and removed the battery, and unblocked all the rfkill tens of times, and searched the support site to update the bios (couldn't find one), and restored the default values of the bios, and looked for a wireless menu in the bios, I tried almost everything. Of course I am not as lucky as the ones who had their devices work after a reboot or a after a suspend. Now what? :)


My device is a netbook: BenQ Joybook Lite U102 running Ubuntu Trusty Tahr 14.04 and the Wi-Fi adapter is some Broadcom adapter.

---

### Post by chili555 on 2014-05-04
Let's gather some diagnostics first. Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
sudo rfkill unblock all
rfkill list all
```How is Fn+F2 mis-mapped? What happens or doesn't as you press it?

What is the position of switch #1 here?

---

### Post by mmelzalabany on 2014-05-04
> **chili555 said:**
> Let's gather some diagnostics first. Please open a terminal and run and post:```
lspci -nn | grep 0280 
rfkill list all 
sudo rfkill unblock all 
rfkill list all
```How is Fn+F2 mis-mapped? What happens or doesn't as you press it? 
 
What is the position of switch #1 here? 
 
Here is the output of the requested commands: 
```
sofy@joybook:~$ lspci -nn | grep 0280 
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 
sofy@joybook:~$ rfkill list all 
0: hci0: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
1: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: yes  
sofy@joybook:~$ rfkill unblock all 
sofy@joybook:~$ rfkill list all 
0: hci0: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
1: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: yes
```  
 
And regarding Fn+F2 mis-mapping, it's actually not functioning, not mis-mapping. Here is what I have: 
Fn+F1: Sleep (working) 
Fn+F2: Wi-Fi software block (not working) 
Fn+F4,F5: Brightness buttons (working) 
Fn+F6: Mute (not working) 
Fn+F7: Volume down (not working) 
Fn+F8: Volume up (working) 
So, according to some other post, sometimes the Wi-Fi worked after trying several combination of the buttons Alt, Ctrl, Fn with the Fn keys from 1 to 12, single and combined. I tried them all. That didn't help. Actually the Fn+F2 is a software block switch, which is not my case. Right? 
 
And regarding the switch #1, I actually tried that, but it only affected the blutooth adapter alone, as follows: 
 
While on: 
```
sofy@joybook:~$ rfkill list all 
0: hci0: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
1: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: yes 
``` 
 
While off: 
```
sofy@joybook:~$ rfkill list all 
1: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: yes 
```

---

### Post by chili555 on 2014-05-04
> Actually the Fn+F2 is a software block switch,Correct.

Usually, there is a laptop-mode or wmi module that translates key presses into action; in this case, Fn+F2 is supposed to translate to 'turn on the wireless, please.' Let's see what is loaded now:```
lsmod
```Also, is there any recognition of the key presses at all?```
tail -f /var/log/syslog
```Now press Fn+F2. What does syslog report?

Get out of 'tail' with Ctrl+c.

---

### Post by mmelzalabany on 2014-05-04
> **chili555 said:**
> Correct.

Usually, there is a laptop-mode or wmi module that translates key presses into action; in this case, Fn+F2 is supposed to translate to 'turn on the wireless, please.' Let's see what is loaded now:```
lsmod
```Also, is there any recognition of the key presses at all?```
tail -f /var/log/syslog
```Now press Fn+F2. What does syslog report?

Get out of 'tail' with Ctrl+c.

Here is the lsmod output:
```
sofy@joybook:~$ lsmod
Module                  Size  Used by
hid_generic            12492  0 
usbhid                 47035  0 
hid                    87604  2 hid_generic,usbhid
snd_hda_codec_realtek    51029  1 
joydev                 17101  0 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12536  2 
snd_rawmidi            25135  1 snd_seq_midi
uvcvideo               71309  0 
b43                   356470  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
bcma                   42043  1 b43
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
coretemp               13195  0 
videobuf2_core         39258  1 uvcvideo
i915                  705396  3 
psmouse                91033  0 
serio_raw              13230  0 
mac80211              545990  1 b43
drm_kms_helper         46907  1 i915
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
videodev              108503  2 uvcvideo,videobuf2_core
drm                   243792  4 i915,drm_kms_helper
rfcomm                 53664  8 
cfg80211              409394  2 b43,mac80211
btusb                  27580  0 
bnep                   18895  2 
snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_p
cm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
bluetooth             342263  22 bnep,btusb,rfcomm
lpc_ich                16864  0 
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
binfmt_misc            13140  1 
video                  18903  1 i915
mac_hid                13037  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
ahci                   25579  2 
libahci                26754  1 ahci
r8169                  61562  0 
ssb                    51854  1 b43
mii                    13654  1 r8169
```

And, ummm, well, this is not the output you requested. The Fn+F2 keys did not trigger any output what so ever in the tail output, I tried other working functions keys, like volume up and brightness control, they were functioning but without output in the tail command. Finally, to send you some output, I switched the bluetooth switch off (switch #1), and here is what I got:
```
May  4 17:17:00 joybook kernel: [ 8256.729388] atkbd serio0: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
May  4 17:17:00 joybook kernel: [ 8256.729412] atkbd serio0: Use 'setkeycodes e071 <keycode>' to make it known.
May  4 17:17:00 joybook kernel: [ 8256.739752] atkbd serio0: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
May  4 17:17:00 joybook kernel: [ 8256.739771] atkbd serio0: Use 'setkeycodes e071 <keycode>' to make it known.
May  4 17:17:00 joybook kernel: [ 8256.832313] usb 5-1: USB disconnect, device number 3
May  4 17:17:00 joybook bluetoothd[430]: Adapter /org/bluez/430/hci0 has been disabled
May  4 17:17:00 joybook bluetoothd[430]: Unregister path: /org/bluez/430/hci0
May  4 17:17:00 joybook bluetoothd[430]: Endpoint unregistered: sender=:1.66 path=/MediaEndpoint/A2DPSink
May  4 17:17:00 joybook bluetoothd[430]: Endpoint unregistered: sender=:1.66 path=/MediaEndpoint/A2DPSource
May  4 17:17:00 joybook bluetoothd[430]: Endpoint unregistered: sender=:1.66 path=/MediaEndpoint/HFPAG
May  4 17:17:00 joybook bluetoothd[430]: Endpoint unregistered: sender=:1.66 path=/MediaEndpoint/HFPHS
May  4 17:17:01 joybook kernel: [ 8257.746424] atkbd serio0: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
May  4 17:17:01 joybook kernel: [ 8257.746445] atkbd serio0: Use 'setkeycodes e071 <keycode>' to make it known.
May  4 17:17:01 joybook kernel: [ 8257.756549] atkbd serio0: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
May  4 17:17:01 joybook kernel: [ 8257.756563] atkbd serio0: Use 'setkeycodes e071 <keycode>' to make it known.
May  4 17:17:02 joybook kernel: [ 8258.616231] usb 5-1: new full-speed USB device number 4 using uhci_hcd
May  4 17:17:02 joybook kernel: [ 8258.792210] usb 5-1: New USB device found, idVendor=0a5c, idProduct=2151
May  4 17:17:02 joybook kernel: [ 8258.792225] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May  4 17:17:02 joybook kernel: [ 8258.792236] usb 5-1: Product: BCM2046 Bluetooth Device
May  4 17:17:02 joybook kernel: [ 8258.792244] usb 5-1: Manufacturer: Broadcom Corp
May  4 17:17:02 joybook kernel: [ 8258.792251] usb 5-1: SerialNumber: 0C6076FE31F5
May  4 17:17:02 joybook CRON[7121]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  4 17:17:03 joybook bluetoothd[430]: hci0: Load Long Term Keys (0x0013) failed: Not Supported (0x0c)
May  4 17:17:03 joybook bluetoothd[430]: Adapter /org/bluez/430/hci0 has been enabled
May  4 17:17:03 joybook bluetoothd[430]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/HFPAG
May  4 17:17:03 joybook bluetoothd[430]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/HFPHS
May  4 17:17:03 joybook bluetoothd[430]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/A2DPSource
May  4 17:17:03 joybook bluetoothd[430]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/A2DPSink
^C

```

---

### Post by chili555 on 2014-05-11
We are very quickly running out of available options. What does this tell us?```
cat /sys/class/rfkill/rfkill0/hard
```I suspect the result is 1. If so, please try:
```
sudo -i
echo 0  >  /sys/class/rfkill/rfkill0/hard
exit
rfkill list all
```
If that works, we'll write a quick file to make it persistent.

Also, let us see:```
cat /sys/class/rfkill/rfkill0/state
```

---

### Post by mmelzalabany on 2014-05-13
> **chili555 said:**
> We are very quickly running out of available options. What does this tell us?```
cat /sys/class/rfkill/rfkill0/hard
```I suspect the result is 1. If so, please try:
```
sudo -i
echo 0  >  /sys/class/rfkill/rfkill0/hard
exit
rfkill list all
```
If that works, we'll write a quick file to make it persistent.

Also, let us see:```
cat /sys/class/rfkill/rfkill0/state
```

Well. The result is 1 indeed but not for rfkill0, but for rfkill1, the wlan. I double checked by catting the type of each one of them.
```
sofy@joybook:~$ cat /sys/class/rfkill/rfkill0/type 
bluetooth
sofy@joybook:~$ cat /sys/class/rfkill/rfkill1/type 
wlan
sofy@joybook:~$ cat /sys/class/rfkill/rfkill0/hard 
0
sofy@joybook:~$ cat /sys/class/rfkill/rfkill1/hard 
1
```


And it gave me permission denied when I tried to echo 0 in the hard of rfkill1, check:
```
sofy@joybook:~$ sudo -i
[sudo] password for sofy: 
root@joybook:~# echo 0 > /sys/class/rfkill/rfkill1/hard 
-bash: /sys/class/rfkill/rfkill1/hard: Permission denied
root@joybook:~# exit
logout
sofy@joybook:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```


Finally, the state for the wlan:
```
sofy@joybook:~$ cat /sys/class/rfkill/rfkill1/state 
2
```
And I added the state of the bluetooth, just for fun:
```
sofy@joybook:~$ cat /sys/class/rfkill/rfkill0/state 
1
```

Now I wanna say that I really appreciate your help, though I know it might be a dead end after all :) Thanks.

---

### Post by chili555 on 2014-05-13
> Finally, the state for the wlan:
Code:
sofy@joybook:~$ cat /sys/class/rfkill/rfkill1/state 
2Did you try:```
sudo -i
echo 1 > /sys/class/rfkill/rfkill1/state
rfkill list all
exit
```> Usually, there is a laptop-mode or wmi module that translates key presses into action; in this case, Fn+F2 is supposed to translate to 'turn on the wireless, please.' I have searched and searched and have been unable to find anything for your BenQ.

---

### Post by mmelzalabany on 2014-05-15
> **chili555 said:**
> Did you try:```
sudo -i
echo 1 > /sys/class/rfkill/rfkill1/state
rfkill list all
exit
```I have searched and searched and have been unable to find anything for your BenQ.

Well. Yeah I tried. But it did not change. And neither gave me a deny message. It just silently failed. Check:
```
sofy@joybook:~$ sudo -i
[sudo] password for sofy:
root@joybook:~# echo 1 > /sys/class/rfkill/rfkill1/state
root@joybook:~# cat /sys/class/rfkill/rfkill1/state
2
root@joybook:~# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@joybook:~# exit
logout
```

And regarding the function keys, it's a minor problem when compared to the Wi-Fi problem, and I only mentioned it when I thought it may be relevant.

I think we narrowed down the problem to one byte: "state".

I searched Google for the words: wifi hard switch "state 2" linux, and I got some really interesting results, but as always the solutions are not generic. They are module-specific. So I couldn't benefit from it. I don't have Atheros adpater, and so. So if you could help me with this one, I would be very thankful.

Note: I mean this post for example: [https://bbs.archlinux.org/viewtopic.php?id=68935](https://bbs.archlinux.org/viewtopic.php?id=68935)

---

### Post by chili555 on 2014-05-16
> I got some really interesting results, but as always the solutions are not generic. They are module-specific. So I couldn't benefit from it. I don't have Atheros adpater, and so. So if you could help me with this one, I would be very thankful.In your case, it would be:```
sudo -i
rmmod b43
rfkill block 1
rfkill unblock 1
modprobe b43
rfkill list all
exit

```We specify 1 here because:> root@joybook:~# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[COLOR="#FF0000"]1[/COLOR]: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yesYou might also try with *b43*s dependency *bcma*:```
sudo -i
rmmod bcma
rfkill block 1
rfkill unblock 1
modprobe b43
rfkill list all
exit
```Finally, in a very few cases I have seen, perhaps three or four, the proprietary driver actually works for this device. If all the above is ineffective, hook up the ethernet and do:```
sudo apt-get install bcmwl-kernel-source
```Reboot and tell us if you connect and let us see:```
rfkill list all
```

---

### Post by mmelzalabany on 2014-05-28
> **chili555 said:**
> In your case, it would be:```
sudo -i
rmmod b43
rfkill block 1
rfkill unblock 1
modprobe b43
rfkill list all
exit

```We specify 1 here because:You might also try with *b43*s dependency *bcma*:```
sudo -i
rmmod bcma
rfkill block 1
rfkill unblock 1
modprobe b43
rfkill list all
exit
```Finally, in a very few cases I have seen, perhaps three or four, the proprietary driver actually works for this device. If all the above is ineffective, hook up the ethernet and do:```
sudo apt-get install bcmwl-kernel-source
```Reboot and tell us if you connect and let us see:```
rfkill list all
```

Well. Thanks again for the professional help :)
I tried all the above once. And nothing worked out. So, I repeated it all again and took the output and pasted it here in this reply. Please tell me if I had done anything wrong.

```
sofy@joybook:~$ sudo -i
[sudo] password for safy: 
root@joybook:~# rmmod b43
rmmod: ERROR: Module b43 is not currently loaded
root@joybook:~# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@joybook:~# rfkill block 1
root@joybook:~# rfkill unblock 1
root@joybook:~# modprobe b43
root@joybook:~# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@joybook:~# rmmod bcma 
rmmod: ERROR: Module bcma is in use by: b43
root@joybook:~# rmmod b43
root@joybook:~# rmmod bcma 
root@joybook:~# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@joybook:~# rfkill block 1
root@joybook:~# rfkill unblock 1
root@joybook:~# modprobe b43
root@joybook:~# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@joybook:~# exit
logout
sofy@joybook:~$ sudo apt-get install bcmwl-kernel-source 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 182 not upgraded.
sofy@joybook:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
sofy@joybook:~$ 

```

I have just one thing to mention: In the first try when I removed the b43 module, you asked me to block/unblock rfkill 1 based on the rfkill list all output. I found that request starnge! Cuz when I removed the module, the rfkill list all output was only having one item which is the bluetooth adapter with number 0, with no sight whatsoever to any Wi-Fi adapters. So, actually the block/unblock had no effect cuz they were targeting something that does not exist.

---

### Post by chili555 on 2014-05-28
> **mmelzalabany said:**
> Well. Thanks again for the professional help :)
I tried all the above once. And nothing worked out. So, I repeated it all again and took the output and pasted it here in this reply. Please tell me if I had done anything wrong.

<snip>Let's try this from a different angle:```
sudo apt-get purge bcmwl-kernel-source
```Reboot and then:```
rfkill list all
```

---

### Post by mmelzalabany on 2014-05-28
> **chili555 said:**
> Let's try this from a different angle:```
sudo apt-get purge bcmwl-kernel-source
```Reboot and then:```
rfkill list all
```

Here is the purge output:
```
sofy@joybook:~$ sudo apt-get purge bcmwl-kernel-source 
[sudo] password for sofy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 13 not upgraded.
After this operation, 4,944 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 204103 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2
) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.1) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-27-generic
sofy@joybook:~$ 
```

And the rfkill list all output after a reboot:
```
sofy@joybook:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
sofy@joybook:~$ 
```

And we're back to square one :)

---

### Post by chili555 on 2014-05-28
> **mmelzalabany said:**
> <snip>

And we're back to square one :)Now let's see the sequence:```

sudo -i
rmmod b43
rfkill block 1
rfkill unblock 1
modprobe b43
rfkill list all
exit
```
You might also try with b43's dependency bcma:
```

sudo -i
rmmod bcma
rfkill block 1
rfkill unblock 1
modprobe b43
rfkill list all
exit
```

---

### Post by mmelzalabany on 2014-05-29
> **chili555 said:**
> Now let's see the sequence:```

sudo -i
rmmod b43
rfkill block 1
rfkill unblock 1
modprobe b43
rfkill list all
exit
```
You might also try with b43's dependency bcma:
```

sudo -i
rmmod bcma
rfkill block 1
rfkill unblock 1
modprobe b43
rfkill list all
exit
```

The first set of commands. Here you see what I mentioned in the last post. You lose the interface totally when you remove the module. I added a bunch of rfkill list all statements to make you see the state before and after:
```
sofy@joybook:~$ sudo -i
[sudo] password for sofy: 
root@joybook:~# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@joybook:~# rmmod b43
root@joybook:~# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@joybook:~# rfkill block 1
root@joybook:~# rfkill unblock 1
root@joybook:~# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@joybook:~# modprobe b43
root@joybook:~# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@joybook:~# exit
logout
sofy@joybook:~$ 
```

And here is the second set of commands:
```
sofy@joybook:~$ sudo -i
root@joybook:~# rmmod bcma 
rmmod: ERROR: Module bcma is in use by: b43
root@joybook:~# rmmod b43
root@joybook:~# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@joybook:~# rmmod bcma 
root@joybook:~# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@joybook:~# rfkill block 1
root@joybook:~# rfkill block 2
root@joybook:~# rfkill unblock 1
root@joybook:~# rfkill unblock 2
root@joybook:~# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
root@joybook:~# modprobe b43
root@joybook:~# rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@joybook:~# exit
logout
sofy@joybook:~$ 
```

---

### Post by praseodym on 2014-05-29
Have you tried to press Fn+F2 repeatedly or permanently during boot-up?

---

### Post by mmelzalabany on 2014-05-29
> **praseodym said:**
> Have you tried to press Fn+F2 repeatedly or permanently during boot-up?

Yes I did. But any ways, this is the software switch, not the hardware one. I also tried a Wi-Fi USB stick and got the same message. Wi-Fi is blocked by hardware switch.

---

### Post by praseodym on 2014-05-29
Is this BenQ Netbook manufactured by another company, e.g. HP or Dell? Do you know that? Tried to update the BIOS?

---

### Post by mmelzalabany on 2014-05-29
> **praseodym said:**
> Is this BenQ Netbook manufactured by another company, e.g. HP or Dell? Do you know that? Tried to update the BIOS?

There is nothing to tell that it was manufactured by HP or Dell or any other third party. I guess it's BenQ made. And yes, I tried to locate a newer bios but couldn't find any.

---

### Post by jeremy31 on 2014-05-29
Is there a switch on the right side next to the USB ports?

---

### Post by praseodym on 2014-05-29
Are you technically skilled? If yes, mask pin 13 of the card.

---

### Post by mmelzalabany on 2014-05-29
> **jeremy31 said:**
> Is there a switch on the right side next to the USB ports?

Yes there is a switch. And we already tried this in previous replies.

---

### Post by mmelzalabany on 2014-05-29
> **praseodym said:**
> Are you technically skilled? If yes, mask pin 13 of the card.

Didn't get that. I guess I am not skilled :) Do you have an easy way to do it?

---

### Post by jeremy31 on 2014-05-29
> **mmelzalabany said:**
> Yes there is a switch. And we already tried this in previous replies.

Sorry, I forgot that.  Found something interesting.  Let us see if yours is similar ```
modinfo b43
```

---

### Post by praseodym on 2014-05-29
> **mmelzalabany said:**
> Didn't get that. I guess I am not skilled :) Do you have an easy way to do it?

[http://www.ulrich-roehr.de/elektronik/laptopumbau/index.html](http://www.ulrich-roehr.de/elektronik/laptopumbau/index.html)

Here's an example (in German) of a Fujitsu notebook. Pin 13 for miniPCI cards, Pin 20 for miniPCIE cards

Absolutely no warranty ;)

---

### Post by jeremy31 on 2014-05-29
Try ```
sudo rmmod b43
``` and then ```
sudo modprobe b43  hwpctl=1
```  And actually I would try it with the switch on the right side in the off position-with BT hard blocked and after using the sudo modprobe turn the switch back to the on position after a few seconds

---

### Post by mmelzalabany on 2014-06-04
> **praseodym said:**
> [http://www.ulrich-roehr.de/elektronik/laptopumbau/index.html](http://www.ulrich-roehr.de/elektronik/laptopumbau/index.html)

Here's an example (in German) of a Fujitsu notebook. Pin 13 for miniPCI cards, Pin 20 for miniPCIE cards

Absolutely no warranty ;)

I don't know if the problem is really with the hardware card. I used a D-Link USB Wi-Fi stick and it didn't work because it was hard blocked too. What do you think?

---

### Post by mmelzalabany on 2014-06-04
> **jeremy31 said:**
> Sorry, I forgot that.  Found something interesting.  Let us see if yours is similar ```
modinfo b43
```

Again I emphasize that I have tried a D-Link USB Wi-Fi stick and it didn't work for the same reason (hardware blocked). So do you think it's the driver that causes this problem?

```
sofy@joybook:~$ modinfo b43
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     BED87D210887FFC71A4BDE0
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        DB:15:81:F7:71:08:A8:FF:59:12:F3:A2:46:DD:ED:FB:AE:7E:AB:8D
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)
sofy@joybook:~$
```

---

### Post by mmelzalabany on 2014-06-04
> **jeremy31 said:**
> Try ```
sudo rmmod b43
``` and then ```
sudo modprobe b43  hwpctl=1
```  And actually I would try it with the switch on the right side in the off position-with BT hard blocked and after using the sudo modprobe turn the switch back to the on position after a few seconds

Well I did exactly the same as you asked. The problem is the bluetooth adapter was not hard blocked when I switched the switch off. It was gone entirely :) . Check the rfkill list all before the switch off and after the switch off, and finally after the switch on after a few seconds.

```
sofy@joybook:~$ sudo rmmod b43
[sudo] password for sofy: 
sofy@joybook:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
sofy@joybook:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
safy@joybook:~$ sudo modprobe b43 hwpctl=1
[sudo] password for sofy: 
sofy@joybook:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
sofy@joybook:~$ 
```

---

### Post by jeremy31 on 2014-06-04
Dang I missed something from your original post, you have the LP-PHY version so you need **firmware-b43-lpphy-installer**

---

### Post by mmelzalabany on 2014-06-05
> **jeremy31 said:**
> Dang I missed something from your original post, you have the LP-PHY version so you need **firmware-b43-lpphy-installer**

Can you tell me what I should do in command-format, please? :) sudo do this - sudo do that :)

---

### Post by praseodym on 2014-06-06
Try it via
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

### Post by mmelzalabany on 2014-06-08
> **praseodym said:**
> Try it via
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

I did both commands. Now what?
```
sofy@joybook:~$ wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480
236-Broadcom_Firmware.tar.gz 
--2014-06-08 12:10:25--  http://media.cdn.ubuntu-de.org/forum/attachments/04/32/
2480236-Broadcom_Firmware.tar.gz
Resolving media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)... 213.95.41.4, 2001
:780:0:25:dead:beef:cafe:1
Connecting to media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)|213.95.41.4|:80.
.. connected.
HTTP request sent, awaiting response... 200 OK
Length: 99011 (97K) [application/octet-stream]
Saving to: ‘2480236-Broadcom_Firmware.tar.gz’

100%[======================================>] 99,011       341KB/s   in 0.3s   

2014-06-08 12:10:26 (341 KB/s) - ‘2480236-Broadcom_Firmware.tar.gz’ saved [99011
/99011]

sofy@joybook:~$ sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
[sudo] password for sofy: 
b43/
b43legacy/
b43/b0g0initvals5.fw
b43/b0g0bsinitvals5.fw
b43/a0g0initvals5.fw
b43/a0g1initvals5.fw
b43/a0g0bsinitvals5.fw
b43/a0g1bsinitvals5.fw
b43/b0g0initvals9.fw
b43/b0g0bsinitvals9.fw
b43/a0g0initvals9.fw
b43/a0g1initvals9.fw
b43/a0g0bsinitvals9.fw
b43/a0g1bsinitvals9.fw
b43/n0initvals11.fw
b43/n0bsinitvals11.fw
b43/n0absinitvals11.fw
b43/lp0initvals13.fw
b43/lp0bsinitvals13.fw
b43/b0g0initvals13.fw
b43/b0g0bsinitvals13.fw
b43/a0g1initvals13.fw
b43/a0g1bsinitvals13.fw
b43/lp0initvals14.fw
b43/lp0bsinitvals14.fw
b43/lp0initvals15.fw
b43/lp0bsinitvals15.fw
b43/ucode5.fw
b43/ucode9.fw
b43/ucode11.fw
b43/ucode13.fw
b43/ucode14.fw
b43/ucode15.fw
b43/pcm5.fw
b43legacy/a0g0bsinitvals5.fw
b43legacy/b0g0initvals2.fw
b43legacy/b0g0initvals5.fw
b43legacy/b0g0bsinitvals2.fw
b43legacy/a0g1initvals5.fw
b43legacy/a0g0initvals2.fw
b43legacy/a0g1bsinitvals5.fw
b43legacy/a0g0initvals5.fw
b43legacy/b0g0bsinitvals5.fw
b43legacy/a0g0bsinitvals2.fw
b43legacy/pcm5.fw
b43legacy/pcm4.fw
b43legacy/ucode11.fw
b43legacy/ucode5.fw
b43legacy/ucode4.fw
b43legacy/ucode2.fw
sofy@joybook:~$ 
```

---

### Post by praseodym on 2014-06-08
Reboot or reload the driver:
```

sudo modprobe -rfv b43
sudo modprobe -v b43
```

---

### Post by mmelzalabany on 2014-06-08
> **praseodym said:**
> Reboot or reload the driver:
```

sudo modprobe -rfv b43
sudo modprobe -v b43
```

Of course I did a reboot. Nothing changed. Now what?

---

### Post by jeremy31 on 2014-06-08
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install linux-firmware-nonfree
```
```
sudo modprobe b43
```[/FONT][/COLOR]

---

### Post by praseodym on 2014-06-08
Lets try
```

sudo modprobe -rfv b43
sudo rfkill unblock all
sudo modprobe -v b43
rfkill list
```
Try also to remove the battery for 10 minutes.

---

