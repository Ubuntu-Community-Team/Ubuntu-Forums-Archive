---
title: "lenovo flex 3 15&quot; atheros not working."
date: 2015-12-05
forum: Networking &amp; Wireless
---

### Post by ben188 on 2015-12-05
hello, 
ive working on a lenovo flex3 15. im having trouble geting the wifi working. ive attached the original wireless info scan as "origWI.txt"
ive attempted to follow the instruction in other threads to install backports and download new firmwares but it looks like the firmware files crash the card. 
ref:[http://ubuntuforums.org/showthread.php?t=2305201&page=2&p=13401303#post13401303](http://ubuntuforums.org/showthread.php?t=2305201&page=2&p=13401303#post13401303)


ive also included what my system looks like now (wireless-info.txt)

the information that seems most relevant to others with similar problems is 
the device im trying to make work (lspci)
-Qualcomm Atheros Device [168c:0041] (rev 20)
the relevant error from dmesg
-[    5.235417] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw SW_RM.1.1.1-00157-QCARMSWPZ-1 fwapi 5 bdapi 1 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
the state of my firmware directory (ls -r /lib/firmware/ath10k/QCA6174/hw2.1/)
firmware-5.bin  firmware-4.bin  board.bin

ive been in circles for a few hours and rather than wandering in the dark, i thought it might be time to ask for help

thanks in advance,
ben

---

### Post by praseodym on 2015-12-05
```
modprobe -c | grep -i "168c.*0041"
alias pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i* [COLOR="#FF0000"]ath9k[/COLOR]
```
Wrong driver. Deactivate the hardware encryption:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by ben188 on 2015-12-05
thanks for the quick response

i did as you suggested adding nohwcrypt and rebooted.

however the output of modprobe is still the same. 
```

alias pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i* ath9k
alias pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i* ath9k
alias pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i* ath9k
alias pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i* ath9k
alias pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i* ath9k
alias pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i* ath9k
alias pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i* ath9k
alias pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i* ath9k
alias pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i* ath9k
alias pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i* ath9k
alias pci:v0000168Cd00000041sv*sd*bc*sc*i* ath10k_pci
```

i think the other devices with the ath9k driver are bluetooth and the like?

the last line shows the device with the ath10k driver.

im still getting the following in dmesg

```

dmesg | grep ath10k
[    3.683014] ath10k_pci 0000:02:00.0: irq 65 for MSI/MSI-X
[    3.683019] ath10k_pci 0000:02:00.0: irq 66 for MSI/MSI-X
[    3.683022] ath10k_pci 0000:02:00.0: irq 67 for MSI/MSI-X
[    3.683026] ath10k_pci 0000:02:00.0: irq 68 for MSI/MSI-X
[    3.683029] ath10k_pci 0000:02:00.0: irq 69 for MSI/MSI-X
[    3.683032] ath10k_pci 0000:02:00.0: irq 70 for MSI/MSI-X
[    3.683035] ath10k_pci 0000:02:00.0: irq 71 for MSI/MSI-X
[    3.683039] ath10k_pci 0000:02:00.0: irq 72 for MSI/MSI-X
[    3.683283] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    3.967588] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[    3.967591] ath10k_pci 0000:02:00.0: Falling back to user helper
[    4.040392] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[    4.040396] ath10k_pci 0000:02:00.0: Falling back to user helper
[    5.242575] ath10k_pci 0000:02:00.0: firmware crashed! (uuid bb47e77b-e683-4270-b161-6474c895ca4a)
[    5.242589] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw SW_RM.1.1.1-00157-QCARMSWPZ-1 fwapi 5 bdapi 1 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[    5.242592] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    5.244901] ath10k_pci 0000:02:00.0: firmware register dump:
[    5.244902] ath10k_pci 0000:02:00.0: [00]: 0x05010000 0x000015B3 0x000A012D 0x00955B31
[    5.244904] ath10k_pci 0000:02:00.0: [04]: 0x000A012D 0x00060330 0x00000016 0x89785006
[    5.244905] ath10k_pci 0000:02:00.0: [08]: 0x00000000 0x00400000 0x00400600 0x00000001
[    5.244906] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00931C61 0x00931C7D
[    5.244907] ath10k_pci 0000:02:00.0: [16]: 0x0096BDBC 0x009286B6 0x00000000 0x00000000
[    5.244909] ath10k_pci 0000:02:00.0: [20]: 0x400A012D 0x0040E2B0 0x00955A00 0x00404590
[    5.244910] ath10k_pci 0000:02:00.0: [24]: 0x809287D9 0x0040E310 0x7A5089F8 0xC00A012D
[    5.244911] ath10k_pci 0000:02:00.0: [28]: 0x809288D7 0x0040E340 0x00000000 0xFFF08040
[    5.244912] ath10k_pci 0000:02:00.0: [32]: 0x809290FE 0x0040E360 0x00400000 0x00400600
[    5.244913] ath10k_pci 0000:02:00.0: [36]: 0x80929205 0x0040E380 0x00000000 0x00400600
[    5.244914] ath10k_pci 0000:02:00.0: [40]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[    5.244916] ath10k_pci 0000:02:00.0: [44]: 0x00000000 0x0040E3D0 0x009BB001 0x00040020
[    5.244917] ath10k_pci 0000:02:00.0: [48]: 0x00401BF0 0x00000001 0x00404B9C 0x00400000
[    5.244918] ath10k_pci 0000:02:00.0: [52]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[    5.244919] ath10k_pci 0000:02:00.0: [56]: 0x13EF6D00 0xC6EE5BA8 0x288FBF5E 0x2FFEC9BF
[    6.239180] ath10k_pci 0000:02:00.0: failed to receive control response completion, polling..
[    7.240066] ath10k_pci 0000:02:00.0: ctl_resp never came in (-110)
[    7.240070] ath10k_pci 0000:02:00.0: failed to connect to HTC: -110
[    7.316865] ath10k_pci 0000:02:00.0: could not init core (-110)
[    7.316885] ath10k_pci 0000:02:00.0: could not probe fw (-110)
[    7.324072] ath10k_pci 0000:02:00.0: cannot restart a device that hasn't been started


```

any additional suggestions?

---

### Post by praseodym on 2015-12-05
You were right, I was wrong. Please try

```
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
sudo mv /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
```
Reboot

---

### Post by ben188 on 2015-12-05
just to be sure i did the following:
```

>cat /etc/modprobe.d/ath10k_core.conf 
options ath10k_core skip_otp=Y
 
``` 

so that was already there.

but i repeated it just in case?


your second and thrid instructions i modified to make it fit with the directory structure
```

 sudo cp -r ath10k-firmware/* /lib/firmware/ath10k/

```

i modified the files in the QCA9377/hw1.0 directory, as well as the QCA6174/2.1 directory to be just .bin

i then 
```

modprobe -r ath10k_pci
modprobe  ath10k_pci
dmesg | grep ath10

```
it still gives the following 
```

[ 2700.055592] ath10k_pci 0000:02:00.0: irq 65 for MSI/MSI-X
[ 2700.055596] ath10k_pci 0000:02:00.0: irq 66 for MSI/MSI-X
[ 2700.055598] ath10k_pci 0000:02:00.0: irq 67 for MSI/MSI-X
[ 2700.055601] ath10k_pci 0000:02:00.0: irq 68 for MSI/MSI-X
[ 2700.055603] ath10k_pci 0000:02:00.0: irq 69 for MSI/MSI-X
[ 2700.055605] ath10k_pci 0000:02:00.0: irq 70 for MSI/MSI-X
[ 2700.055608] ath10k_pci 0000:02:00.0: irq 71 for MSI/MSI-X
[ 2700.055610] ath10k_pci 0000:02:00.0: irq 72 for MSI/MSI-X
[ 2700.055730] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[ 2700.292823] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[ 2700.292825] ath10k_pci 0000:02:00.0: Falling back to user helper
[ 2700.356242] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[ 2700.356244] ath10k_pci 0000:02:00.0: Falling back to user helper
[ 2701.533066] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 88c4f7a8-777a-4d46-98bb-429d5c406436)
[ 2701.533080] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw SW_RM.1.1.1-00157-QCARMSWPZ-1 fwapi 5 bdapi 1 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[ 2701.533082] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[ 2701.535303] ath10k_pci 0000:02:00.0: firmware register dump:
[ 2701.535307] ath10k_pci 0000:02:00.0: [00]: 0x05010000 0x000015B3 0x000A012D 0x00955B31
[ 2701.535309] ath10k_pci 0000:02:00.0: [04]: 0x000A012D 0x00060330 0x00000016 0x89785006
[ 2701.535310] ath10k_pci 0000:02:00.0: [08]: 0x00000000 0x00400000 0x00400600 0x00000001
[ 2701.535311] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00931C61 0x00931C7D
[ 2701.535312] ath10k_pci 0000:02:00.0: [16]: 0x0096BDBC 0x009286B6 0x00000000 0x00000000
[ 2701.535314] ath10k_pci 0000:02:00.0: [20]: 0x400A012D 0x0040E2B0 0x00955A00 0x00404590
[ 2701.535315] ath10k_pci 0000:02:00.0: [24]: 0x809287D9 0x0040E310 0x7A5089F8 0xC00A012D
[ 2701.535316] ath10k_pci 0000:02:00.0: [28]: 0x809288D7 0x0040E340 0x00000000 0xFFF08040
[ 2701.535317] ath10k_pci 0000:02:00.0: [32]: 0x809290FE 0x0040E360 0x00400000 0x00400600
[ 2701.535318] ath10k_pci 0000:02:00.0: [36]: 0x80929205 0x0040E380 0x00000000 0x00400600
[ 2701.535320] ath10k_pci 0000:02:00.0: [40]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[ 2701.535321] ath10k_pci 0000:02:00.0: [44]: 0x00000000 0x0040E3D0 0x009BB001 0x00040020
[ 2701.535322] ath10k_pci 0000:02:00.0: [48]: 0x00401BF0 0x00000001 0x00404B9C 0x00400000
[ 2701.535323] ath10k_pci 0000:02:00.0: [52]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[ 2701.535324] ath10k_pci 0000:02:00.0: [56]: 0x13EF6D00 0xC6EE5BA8 0x288FBF5E 0x2FFEC9BF
[ 2702.529245] ath10k_pci 0000:02:00.0: failed to receive control response completion, polling..

```

i do appreciate your patience in helping me with this. but its still not working.

edit: i also rebooted, same results.

---

### Post by Hadaka on 2015-12-05
Hi, it looks like you just need the ath10k firmware
from a working wired connection please do.
please copy and paste.
```
sudo mkdir /lib/firmware/ath10k/QCA6164/
sudo mkdir /lib/firmware/ath10k/QCA6164/hw1.0
```
*If it says these exsist..thats ok..please continue..
```
echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf
git clone https://github.com/kvalo/ath10k-firmware.git
sudo cp -r ath10k-firmware/ /lib/firmware/ath10k/
sudo mv /lib/firmware/ath10k/QCA6164/hw3.0/firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1 /lib/firmwareath10kQCA6164hw3.0/firmware-4.bin
```

boot and test

---

### Post by ben188 on 2015-12-05
hadaka,

im a little confused by your suggestions. they do not make sense to me.
1) where did you come up with the foldername QCA6164 and hw1.0?

this may be the root of my problem ive been looking for QCA6174 hw2.1 because that is the error message ive been seeing in the log. im i looking for the wrong firmware?

2) "QCA6164/hw3.0/firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1" <-- this file does not exist on kvalos repo. in fac the entire QCA6164 folder does not exist.
3) why would i create a folder called hw1.0 if im going to be using the hw3.0 folder?

your instructions dont seem to work for my current problem. unless im missing something.

---

### Post by jeremy31 on 2015-12-05
Wrong firmware and I don't think kvalo has it. The QCA6164 looks for firmware in the QCA6174 directory, explanation on ath10k mailing list was to prevent breaking backwards compatibility with older /lib/firmware/ setups or something.  Hadaka was thinking logically and for some strange reason the kernel developers couldn't do it that way.  

This has worked before

```
git clone https://github.com/atondwal/ath10k-firmware.git
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r /lib/firmware/ath10k/QCA6164/hw2.1 /lib/firmware/ath10k/QCA6174/
```

Reboot

---

### Post by Hadaka on 2015-12-05
hi, i got it from your dmesg
[ 2701.533080] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw SW_RM.1.1.1-00157-QCARMSWPZ-1 fwapi 5 bdapi 1 htt-ver 0.0 wmi-o

the other was from my template, sorry about that.

---

### Post by ben188 on 2015-12-05
jeremy & hadaka, thanks for clearing that up.

a few more questions.
currently i have:
1)cloned kvalo
2) copied every QCA folder into /lib/firmware/ath10k
```

ls /lib/firmware/ath10k/
LICENSE.qca_firmware  Makefile  QCA6174  QCA9377  QCA9887  QCA988X  QCA99X0  README.md

```
and then 
i stripped the .bin_asdf file extentions down to just .bin in the QCA6174 directory with the following (ive tried this to many times to not come up with a shortcut):
```

 sudo rename 's/\.bin.*/\.bin/' *.bin*

```

but now there is conflicting information in the thread.
should board.bin and firmware-5.bin from ath10k-firmware/QCA6174/hw2.1 go in 
a) /lib/firmware/ath10k/QCA6174/hw2.1
b) /lib/firmware/ath10k/QCA6174/
c) /lib/firmware/ath10k/QCA6164/hw2.1
d) /lib/firmware/ath10k/QCA6164/
e) other

.
ive also done some testing
```

cd /lib/firmware/ath10k
sudo rm -r *
modprobe ath10k

```
this should have no chance of working and dmesg give the following error
```

[   75.428550] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   75.662978] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   75.662980] ath10k_pci 0000:02:00.0: Falling back to user helper
[   75.663463] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   75.663466] ath10k_pci 0000:02:00.0: Falling back to user helper
[   75.663828] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-5.bin': -12
[   75.663839] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   75.663841] ath10k_pci 0000:02:00.0: Falling back to user helper
[   75.664426] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-4.bin': -12
[   75.664435] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   75.664437] ath10k_pci 0000:02:00.0: Falling back to user helper
[   75.664849] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-3.bin': -12
[   75.664860] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   75.664861] ath10k_pci 0000:02:00.0: Falling back to user helper
[   75.665249] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-2.bin': -12
[   75.665260] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[   75.665262] ath10k_pci 0000:02:00.0: Falling back to user helper
[   75.665611] ath10k_pci 0000:02:00.0: could not fetch firmware (-12)
[   75.665615] ath10k_pci 0000:02:00.0: could not fetch firmware files (-12)
[   75.665617] ath10k_pci 0000:02:00.0: could not probe fw (-12)

```

it is looking for a firmware file in 'ath10k/QCA6174/hw2.1/firmware-<x>.bin'

so i then copy from my clone of kvalo/ath10k-firmware to that location only the firmware-5.bin file (not the board.bin file)

and modprobe again

now dmesg gives
```

[  521.119827] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[  521.356672] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[  521.356674] ath10k_pci 0000:02:00.0: Falling back to user helper
[  521.420135] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[  521.420137] ath10k_pci 0000:02:00.0: Falling back to user helper
[  522.596710] ath10k_pci 0000:02:00.0: firmware crashed! (uuid da4b0fcc-bb74-4040-95bc-13527e493285)
[  522.596725] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw SW_RM.1.1.1-00157-QCARMSWPZ-1 fwapi 5 bdapi 1 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[  522.596727] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[  522.598732] ath10k_pci 0000:02:00.0: firmware register dump:
[  522.598733] ath10k_pci 0000:02:00.0: [00]: 0x05010000 0x000015B3 0x000A012D 0x00955B31
[  522.598735] ath10k_pci 0000:02:00.0: [04]: 0x000A012D 0x00060330 0x00000016 0x89785006
[  522.598736] ath10k_pci 0000:02:00.0: [08]: 0x00000000 0x00400000 0x00400600 0x00000001
[  522.598737] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00931C61 0x00931C7D
[  522.598738] ath10k_pci 0000:02:00.0: [16]: 0x0096BDBC 0x0097F8C0 0x00000000 0x00000000
[  522.598740] ath10k_pci 0000:02:00.0: [20]: 0x400A012D 0x0040E2B0 0x00955A00 0x00404590
[  522.598741] ath10k_pci 0000:02:00.0: [24]: 0x809287D9 0x0040E310 0x7A5089F8 0xC00A012D
[  522.598742] ath10k_pci 0000:02:00.0: [28]: 0x809288D7 0x0040E340 0x00000000 0xFFF08040
[  522.598743] ath10k_pci 0000:02:00.0: [32]: 0x809290FE 0x0040E360 0x00400000 0x00400600
[  522.598744] ath10k_pci 0000:02:00.0: [36]: 0x80929205 0x0040E380 0x00000000 0x00400600
[  522.598745] ath10k_pci 0000:02:00.0: [40]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[  522.598747] ath10k_pci 0000:02:00.0: [44]: 0x00000000 0x0040E3D0 0x009BB001 0x00040020
[  522.598748] ath10k_pci 0000:02:00.0: [48]: 0x00401BF0 0x00000001 0x00404B9C 0x00400000
[  522.598749] ath10k_pci 0000:02:00.0: [52]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[  522.598750] ath10k_pci 0000:02:00.0: [56]: 0x13EF6D00 0xC6EE5BA8 0x288FBF5E 0x2FFEC9BF
[  523.593056] ath10k_pci 0000:02:00.0: failed to receive control response completion, polling..
[  524.593870] ath10k_pci 0000:02:00.0: ctl_resp never came in (-110)
[  524.593880] ath10k_pci 0000:02:00.0: failed to connect to HTC: -110

```

then i give both files (board and firmware-5)
```

[  657.937082] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[  658.171148] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[  658.171151] ath10k_pci 0000:02:00.0: Falling back to user helper
[  658.234551] ath10k_pci 0000:02:00.0: Direct firmware load failed with error -2
[  658.234554] ath10k_pci 0000:02:00.0: Falling back to user helper
[  659.411209] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 566b2800-6f95-49f0-a5bb-a0e891906671)
[  659.411223] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw SW_RM.1.1.1-00157-QCARMSWPZ-1 fwapi 5 bdapi 1 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[  659.411225] ath10k_pci 0000:02:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[  659.413232] ath10k_pci 0000:02:00.0: firmware register dump:
[  659.413234] ath10k_pci 0000:02:00.0: [00]: 0x05010000 0x000015B3 0x000A012D 0x00955B31
[  659.413235] ath10k_pci 0000:02:00.0: [04]: 0x000A012D 0x00060330 0x00000016 0x89785006
[  659.413236] ath10k_pci 0000:02:00.0: [08]: 0x00000000 0x00400000 0x00400600 0x00000001
[  659.413238] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00931C61 0x00931C7D
[  659.413239] ath10k_pci 0000:02:00.0: [16]: 0x0096BDBC 0x0092C07A 0x00000000 0x00000000
[  659.413240] ath10k_pci 0000:02:00.0: [20]: 0x400A012D 0x0040E2B0 0x00955A00 0x00404590
[  659.413241] ath10k_pci 0000:02:00.0: [24]: 0x809287D9 0x0040E310 0x7A5089F8 0xC00A012D
[  659.413242] ath10k_pci 0000:02:00.0: [28]: 0x809288D7 0x0040E340 0x00000000 0xFFF08040
[  659.413244] ath10k_pci 0000:02:00.0: [32]: 0x809290FE 0x0040E360 0x00400000 0x00400600
[  659.413245] ath10k_pci 0000:02:00.0: [36]: 0x80929205 0x0040E380 0x00000000 0x00400600
[  659.413246] ath10k_pci 0000:02:00.0: [40]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[  659.413247] ath10k_pci 0000:02:00.0: [44]: 0x00000000 0x0040E3D0 0x009BB001 0x00040020
[  659.413248] ath10k_pci 0000:02:00.0: [48]: 0x00401BF0 0x00000001 0x00404B9C 0x00400000
[  659.413249] ath10k_pci 0000:02:00.0: [52]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[  659.413250] ath10k_pci 0000:02:00.0: [56]: 0x13EF6D00 0xC6EE5BA8 0x288FBF5E 0x2FFEC9BF
[  660.407548] ath10k_pci 0000:02:00.0: failed to receive control response completion, polling..
[  661.408326] ath10k_pci 0000:02:00.0: ctl_resp never came in (-110)
[  661.408329] ath10k_pci 0000:02:00.0: failed to connect to HTC: -110
[  661.484820] ath10k_pci 0000:02:00.0: could not init core (-110)
[  661.484838] ath10k_pci 0000:02:00.0: could not probe fw (-110)
[  661.488437] ath10k_pci 0000:02:00.0: cannot restart a device that hasn't been started


``` 

not sure if the additional detail will hep nail down the problem

---

### Post by jeremy31 on 2015-12-05
I updated my post [http://ubuntuforums.org/showthread.php?t=2305404&p=13402315#post13402315](http://ubuntuforums.org/showthread.php?t=2305404&p=13402315#post13402315) as my copy from a bug report did not go well

The firmware from the atondwal github site from folder /QCA6164/hw2.1 needs to be in /lib/firmware/QCA6174/hw2.1 as the firmware from kvallo resulted in the firmware crash you had

---

### Post by ben188 on 2015-12-05
bingo!
thank you so much
to sum up to make it work i had to do the following

```

mkdir wififix
cd wififix
sudo apt-get install build-essential linux-headers-$(uname -r) git 
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz 
tar -zxvf backports-20151120.tar.gz cd backports-20151120 
make defconfig-ath10k 
make 
sudo make install

git clone https://github.com/atondwal/ath10k-firmware.git 
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/ 
sudo cp -r /lib/firmware/ath10k/QCA6164/hw2.1 /lib/firmware/ath10k/QCA6174/


```
then reboot

also my small contribution to others is the following command to strip the extra stuff off the end of bin files.

```

sudo rename 's/\.bin.*/\.bin/' *.bin*

```

---

### Post by jeremy31 on 2015-12-05
> **ben188 said:**
> bingo!
thank you so much
to sum up to make it work i had to do the following

```

mkdir wififix
cd wififix
sudo apt-get install build-essential linux-headers-$(uname -r) git 
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz 
tar -zxvf backports-20151120.tar.gz cd backports-20151120 
make defconfig-ath10k 
make 
sudo make install

git clone https://github.com/atondwal/ath10k-firmware.git 
sudo cp -r ath10k-firmware/ath10k/ /lib/firmware/ 
sudo cp -r /lib/firmware/ath10k/QCA6164/hw2.1 /lib/firmware/ath10k/QCA6174/


```
then reboot

also my small contribution to others is the following command to strip the extra stuff off the end of bin files.

```

sudo rename 's/\.bin.*/\.bin/' *.bin*

```

Glad to hear that it works now

The extra info on the file name may be needed in future kernel versions

And if you need a second wifi card to work I would suggest using ```
make defconfig-wifi
``` instead of ```
make defconfig-ath10k
``` when compiling the backports

Please use the forum or thread tools menu at the top of the page to "Mark as Solved"

---

