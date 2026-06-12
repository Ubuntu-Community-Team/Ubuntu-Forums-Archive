---
title: "Wifi adapter not found for Ubuntu 18.04"
date: 2018-09-09
forum: Networking &amp; Wireless
---

### Post by cchowdhury on 2018-09-09
[FONT=Arial]Hi

I installed Ubuntu 18.04.1 LTS into my HP laptop. The laptop was pre-loaded with Windows 10 and wireless was working. 
After I installed Ubuntu - it says "Wifi Adapter not found" and I am unable to connect to the internet/work. 

I tried to install rtlwifi modules as suggested here (used a wired connection to the router) : 

[/FONT]http://ubuntuhandbook.org/index.php/2018/08/no-wifi-adapter-found-hp-laptops-ubuntu-18-04/ [FONT=Arial]


$: sudo make install  .....throws the following error and I couldn't progress any further.

****************************************ERROR ***************************
chan@chan:~/rtlwifi_new$ sudo make install[/FONT]
[FONT=Arial]make -C /lib/modules/4.15.0-29-[/FONT][FONT=Arial]generic/build M=/home/chan/rtlwifi_new modules[/FONT]
[FONT=Arial]make[1]: Entering directory '/usr/src/linux-headers-4.15.[/FONT][FONT=Arial]0-29-generic'[/FONT]
[FONT=Arial]arch/x86/Makefile:156: CONFIG_X86_X32 enabled but no binutils support[/FONT]
[FONT=Arial]Makefile:976: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"[/FONT]
[FONT=Arial]  CC [M]  /home/chan/rtlwifi_new/base.[/FONT][FONT=Arial]o[/FONT]
[FONT=Arial]/bin/sh: 1: gcc: not found[/FONT]
[FONT=Arial]scripts/Makefile.build:332: recipe for target '/home/chan/rtlwifi_new/[/FONT][FONT=Arial]base.o' failed[/FONT]
[FONT=Arial]make[2]: *** [/home/chan/rtlwifi_new/[/FONT][FONT=Arial]base.o] Error 127[/FONT]
[FONT=Arial]Makefile:1552: recipe for target '_module_/home/chan/rtlwifi_[/FONT][FONT=Arial]new' failed[/FONT]
[FONT=Arial]make[1]: *** [_module_/home/chan/rtlwifi_[/FONT][FONT=Arial]new] Error 2[/FONT]
[FONT=Arial]make[1]: Leaving directory '/usr/src/linux-headers-4.15.[/FONT][FONT=Arial]0-29-generic'[/FONT]
[FONT=Arial]Makefile:87: recipe for target 'all' failed[/FONT]
[FONT=Arial]make: *** [all] Error 2

****************************************************

Any idea how to fix it?? or an alternative to getting wifi drivers installed for Ubuntu 18.04

Thanks,
Chandan




[/FONT]

---

### Post by chili555 on 2018-09-09
Before we install a driver from rtlwifi_new, let's identify your exact device. Please run and post:```
lspci -nnk | grep 0280 -A3
rfkill list all
```Thanks.

---

### Post by Yellow Pasque on 2018-09-09
The tutorial makes the (poor) assumption that you have the prerequisite packages. It should have included:

```
sudo apt-get install git build-essential libelf-dev
```

But you should double check your wifi adapter as suggested to make sure you're attempting to use the correct driver.

---

### Post by cchowdhury on 2018-09-10
Thanks for replying. Results as requested are: 

$: lspci -nnk ¦ grep 0280 -A3 
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
subsystem: Hewlett-Packard Company Device [103c:8319]

$: rfkill list all
0: hci0: Bluetooth
Soft blocked: no 
Hard Blocked: no

---

### Post by cchowdhury on 2018-09-10
Thanks for your reply. Yes, you are right they missed all that and I had to install all three above and more. It still did not work.

---

### Post by cchowdhury on 2018-09-10
> **chili555 said:**
> Before we install a driver from rtlwifi_new, let's identify your exact device. Please run and post:```
lspci -nnk | grep 0280 -A3
rfkill list all
```Thanks.

[COLOR=#000000]Thanks for replying. Results as requested are: [/COLOR]

[COLOR=#000000]$: lspci -nnk ¦ grep 0280 -A3 [/COLOR]
[COLOR=#000000]03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723][/COLOR]
[COLOR=#000000]subsystem: Hewlett-Packard Company Device [103c:8319][/COLOR]

[COLOR=#000000]$: rfkill list all[/COLOR]
[COLOR=#000000]0: hci0: Bluetooth[/COLOR]
[COLOR=#000000]Soft blocked: no [/COLOR]
[COLOR=#000000]Hard Blocked: no[/COLOR]

---

### Post by Yellow Pasque on 2018-09-10
> **cchowdhury said:**
> It still did not work.

Be more specific. What did not work: building the module, loading it, running it? Give output if relevant.

---

### Post by cchowdhury on 2018-09-10
> **Temüjin said:**
> Be more specific. What did not work: building the module, loading it, running it? Give output if relevant.

So even after a successful install of modules (git, [COLOR=#000000][FONT=Arial]libelf-dev, libelf-devel, elfutils-libelf-devel, build-essentials )[/FONT][/COLOR] 
 
[COLOR=#333333][FONT=Monaco]$: sudo make install 
continued to generate the errors that I originally posted. 

Do you want me to run the "sudo apt-get installs" again and post the outputs here? [/FONT][/COLOR]

---

### Post by Yellow Pasque on 2018-09-10
> Do you want me to run the "sudo apt-get installs" again and post the outputs here? 
I don't think that would be helpful. Try running make clean and then run make again.
```
cd ~/rtlwifi_new
sudo make clean
make
```

---

### Post by chili555 on 2018-09-10
> **Temüjin said:**
> I don't think that would be helpful. Try running make clean and then run make again.
```
cd ~/rtlwifi_new
sudo make clean
make
```And then post any errors, please.

---

### Post by cchowdhury on 2018-09-10
> **chili555 said:**
> And then post any errors, please.
cd ~/rtlwifi_new
sudo make clean
make


Thank you. It moved a few steps further... 
I ran the three commands that you suggested and "*make*" ran successfully. I then typed *"sudo make install"* and that ran successfully. 
Then I ran *"*[FONT=Arial]*sudo modprobe -r rtl8723de"* and finally *"sudo modprobe rtl8723de" *and I get the error [COLOR=#ff0000]below in RED>. [/COLOR][/FONT]


***************************************************************
[FONT=Arial]CC      /home/ruchie/rtlwifi_new/rtl8723com/rtl8723-common.mod.o
  LD [M]  /home/ruchie/rtlwifi_new/rtl8723com/rtl8723-common.ko
  CC      /home/ruchie/rtlwifi_new/rtl8723de/rtl8723de.mod.o
  LD [M]  /home/ruchie/rtlwifi_new/rtl8723de/rtl8723de.ko
  CC      /home/ruchie/rtlwifi_new/rtl8821ae/rtl8821ae.mod.o
  LD [M]  /home/ruchie/rtlwifi_new/rtl8821ae/rtl8821ae.ko
  CC      /home/ruchie/rtlwifi_new/rtl8822be/rtl8822be.mod.o
  LD [M]  /home/ruchie/rtlwifi_new/rtl8822be/rtl8822be.ko
  CC      /home/ruchie/rtlwifi_new/rtl_pci.mod.o
  LD [M]  /home/ruchie/rtlwifi_new/rtl_pci.ko
  CC      /home/ruchie/rtlwifi_new/rtl_usb.mod.o
  LD [M]  /home/ruchie/rtlwifi_new/rtl_usb.ko
  CC      /home/ruchie/rtlwifi_new/rtlwifi.mod.o
  LD [M]  /home/ruchie/rtlwifi_new/rtlwifi.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-29-generic'
home:$sudo make install
make -C /lib/modules/4.15.0-29-generic/build M=/home/ruchie/rtlwifi_new modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-29-generic'
  Building modules, stage 2.
  MODPOST 19 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-29-generic'
Making backups
Install rtlwifi SUCCESS
home:$sudo modprobe -r rtl8723de
[B][COLOR=#ff0000]home:$sudo modprobe rtl8723de
modprobe: ERROR: could not insert 'rtl8723de': Required key not available[/COLOR][/B]

***************************************************


home:$lspci -nnk | grep 0280 -A3
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    Subsystem: Hewlett-Packard Company Device [103c:8319]
    [COLOR=#0000ff]Kernel modules: rtl8723de[/COLOR]
home:$




Ref: Step 5 in  [http://ubuntuhandbook.org/index.php/2018/08/no-wifi-adapter-found-hp-laptops-ubuntu-18-04/](http://ubuntuhandbook.org/index.php/2018/08/no-wifi-adapter-found-hp-laptops-ubuntu-18-04/)


[/FONT]

---

### Post by chili555 on 2018-09-10
> modprobe: ERROR: could not insert 'rtl8723de': Required key not available
Please see: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

I suggest that you disable Secure Boot.

---

### Post by cchowdhury on 2018-09-10
> **chili555 said:**
> Please see: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

I suggest that you disable Secure Boot.


BIG THANKS!! Wifi Adapter working and I could connect to home wifi :)
I DISABLED Secure Boot from BIOS Settings.. 
ESC while booting; then navigated to Boot Settings and found the option to Disable Secure Boot.. 

However, the signal strength is very low.. Router is only detected within a range of 2 meters.. 

Any ideas?? Thank you so much!!

---

### Post by jeremy31 on 2018-09-10
For the signal strength do ```
sudo modprobe -r rtl8723de
sudo modprobe rtl8723de ant_sel=2
```
If that improves it then do
```
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de-ant.conf
```

---

### Post by chili555 on 2018-09-10
Also see my post #2 here: [https://ubuntuforums.org/showthread.php?t=2400796&highlight=rtl8723de](https://ubuntuforums.org/showthread.php?t=2400796&highlight=rtl8723de)

---

### Post by cchowdhury on 2018-09-10
> **jeremy31 said:**
> For the signal strength do ```
sudo modprobe -r rtl8723de
sudo modprobe rtl8723de ant_sel=2
```
If that improves it then do
```
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de-ant.conf
```


:D Excellent !! Thank you ... Signal Strength improved significantly... 

Great Support @Chili555 and @Jeremy31 !! Thank you.

---

### Post by vvmspace on 2018-10-30
I've fixed driver for Ubuntu 18.10 & 18.04, try it:

[https://github.com/vvmspace/rtl8723de](https://github.com/vvmspace/rtl8723de)

> sudo apt-get install git dkms libelf-dev
git clone [https://github.com/vvmspace/rtl8723de.git](https://github.com/vvmspace/rtl8723de.git)
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
sudo reboot

---

