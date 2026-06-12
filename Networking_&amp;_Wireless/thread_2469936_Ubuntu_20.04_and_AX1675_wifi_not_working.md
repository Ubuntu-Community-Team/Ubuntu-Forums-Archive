---
title: "Ubuntu 20.04 and AX1675 wifi not working"
date: 2021-12-14
forum: Networking &amp; Wireless
---

### Post by mike430 on 2021-12-14
Hello there fellow earthlings!

After installing Ubuntu 20.04.3 on a machine with Killer wifi 6E AX1675x, there appears to be no support for this card. 

I have been following this thread [https://ubuntuforums.org/showthread.php?t=2465615](https://ubuntuforums.org/showthread.php?t=2465615) , for it appears this user has same card and I believe same machine. Before I devote half of my life to get this card working in some fashion would like to know if any one else has had success in getting this to work on 20.04.3. 

The alternatives per that thread were to install Ubuntu 21.10 for it is supported, however, gpu is not supported. I have no problem installing 21.10 and discarding 20.04 for the wifi card is of more value to me then the gpu on linux. I also do not know much about the short term support versions which I believe in the case of 21.10 is supported < 1 year. Beyond that not sure what limitations are to be had on short support versions would be interested to know however.

ideally of course, would like to have both wifi and gpu working. 

Lastly I find it interesting on Intel's website that appears to be evidence of support for this card. Per this link [https://www.intel.com/content/www/us/en/support/articles/000088040/wireless/intel-wireless-products.html](https://www.intel.com/content/www/us/en/support/articles/000088040/wireless/intel-wireless-products.html) they provide a table that shows a generic intel driver [SIZE=1]([COLOR=#262626][FONT=intel-clear]Intel® Wi-Fi 6 AX210 160MHz) [/FONT][/COLOR][/SIZE]they say supports the ax1675. Another link inside this page has a downloadable tar file corresponding to the generic driver that intel says works. Does anyone know anything about this working or not. Or even safe installing this driver? Also says 5.10+ kernel needed for support.  

Thanks in advance for any help. -mike

---

### Post by jeremy31 on 2021-12-14
Please post results from terminal for ```
lspci -nnk | grep -iA3 net; uname -r; dmesg | grep iwl
```

---

### Post by praseodym on 2021-12-14
The link there "only" contains firmware files *.ucode.

---

### Post by mike430 on 2021-12-14
2e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. Device [10ec:3000] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:12f5]
	Kernel driver in use: r8169
	Kernel modules: r8169
30:00.0 Network controller [0280]: Intel Corporation Device [8086:2725] (rev 1a)
	Subsystem: Bigfoot Networks, Inc. Device [1a56:1674]
5.11.0-41-generic

---

### Post by mike430 on 2021-12-14
So these types of files will not run hardware is what you're saying? What is the function then of intel's file?

---

### Post by praseodym on 2021-12-14
That firmware makes only sense if the driver recognizes the hardware.

Lets see
```

modprobe -c | grep -i "8086.*2725"
sudo modprobe -v iwlwifi
dmesg | grep iwl
```

---

### Post by jeremy31 on 2021-12-14
See if Secure Boot is disabled with ```
mokutil --sb-state
```
Then install the intel wifi backports with
```
sudo apt update and sudo apt install backport-iwlwifi-dkms
```
Reboot

---

### Post by mike430 on 2021-12-14
sudo modprobe -c | grep -i "8086.*2725"
alias pci:v00008086d00002725sv*sd00000020bc*sc*i* iwlwifi
alias pci:v00008086d00002725sv*sd00000024bc*sc*i* iwlwifi
alias pci:v00008086d00002725sv*sd00000090bc*sc*i* iwlwifi
alias pci:v00008086d00002725sv*sd000000B0bc*sc*i* iwlwifi
alias pci:v00008086d00002725sv*sd00000310bc*sc*i* iwlwifi
alias pci:v00008086d00002725sv*sd00000510bc*sc*i* iwlwifi
alias pci:v00008086d00002725sv*sd00000A10bc*sc*i* iwlwifi
alias pci:v00008086d00002725sv*sd00004020bc*sc*i* iwlwifi
alias pci:v00008086d00002725sv*sd00006020bc*sc*i* iwlwifi
alias pci:v00008086d00002725sv*sd00006024bc*sc*i* iwlwifi
alias pci:v00008086d00002725sv*sd0000E020bc*sc*i* iwlwifi
alias pci:v00008086d00002725sv*sd0000E024bc*sc*i* iwlwifi

and

sudo modprobe -v iwlwifi
insmod /lib/modules/5.11.0-41-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/5.11.0-41-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko 

and 

dmesg | grep iwl
(blank)

---

### Post by mike430 on 2021-12-14
[COLOR=#000000][FONT=Verdana]Secure boot is disabled.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]When I go to install backports I get some dependency issues not sure how to easily resolve.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]sudo dpkg -i Desktop/wifi1675/backport-iwlwifi-dkms_9340-0ubuntu4_all.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana](Reading database ... 189243 files and directories currently installed.)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Preparing to unpack .../backport-iwlwifi-dkms_9340-0ubuntu4_all.deb ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Unpacking backport-iwlwifi-dkms (9340-0ubuntu4) over (9340-0ubuntu4) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]dpkg: dependency problems prevent configuration of backport-iwlwifi-dkms:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]backport-iwlwifi-dkms depends on dkms (>= 2.1.0.0); however:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Package dkms is not installed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]backport-iwlwifi-dkms depends on libc6-dev | libc-dev; however:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Package libc6-dev is not installed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Package libc-dev is not installed.

[/FONT][/COLOR][FONT=Verdana]sudo apt-get install dkms [/FONT]
[FONT=Verdana]Reading package lists... Done[/FONT]
[FONT=Verdana]Building dependency tree       [/FONT]
[FONT=Verdana]Reading state information... Done[/FONT]
[FONT=Verdana]You might want to run 'apt --fix-broken install' to correct these.[/FONT]
[FONT=Verdana]The following packages have unmet dependencies:[/FONT]
[FONT=Verdana] backport-iwlwifi-dkms : Depends: libc6-dev but it is not going to be installed or[/FONT]
[FONT=Verdana]                                  libc-dev[/FONT]
[FONT=Verdana] dkms : Depends: gcc but it is not going to be installed or[/FONT]
[FONT=Verdana]                 c-compiler[/FONT]
[FONT=Verdana]        Depends: dpkg-dev but it is not going to be installed[/FONT]
[FONT=Verdana]        Depends: make or[/FONT]
[FONT=Verdana]                 build-essential but it is not going to be installed[/FONT]
[FONT=Verdana]        Depends: dctrl-tools[/FONT]
[FONT=Verdana]        Recommends: fakeroot[/FONT]
[FONT=Verdana]E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).[/FONT]

---

### Post by praseodym on 2021-12-15
Have you tried
```

sudo apt-get -f install
```

---

### Post by mike430 on 2021-12-15
right...

---

### Post by mike430 on 2021-12-15
It's working. Thanks for your help. It really boiled down to doing this.

go to-  [https://launchpad.net/ubuntu/impish/amd64/backport-iwlwifi-dkms/9340-0ubuntu4](https://launchpad.net/ubuntu/impish/amd64/backport-iwlwifi-dkms/9340-0ubuntu4)

download and run [FONT=var(--ff-mono)]sudo dpkg -i backport-iwlwifi-dkms_9340-0ubuntu4_all.deb

then go to [/FONT]https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git

download and run [FONT=var(--ff-mono)]sudo tar -zxf linux-firmware-20210818.tar.gz -C /lib/firmware

rebooted and was good...surprisingly. Love linux but nothing I mean nothing works the first time. 

This thread is where i got this, towards the end of the page [/FONT]https://askubuntu.com/questions/1356118/ax210-wifi-not-working-on-ubuntu21-04

---

### Post by mike430 on 2021-12-15
[SIZE=7]SOLVED! 
[SIZE=2]couldn't find the solved button so I made it myself. [/SIZE]
[/SIZE]

---

### Post by praseodym on 2021-12-16
Use "Thread tools" in the first post for marking it solved

---

### Post by mike430 on 2021-12-16
Thanks. Will do..

---

### Post by T6&amp;sfpER35% on 2021-12-16
> but nothing I mean nothing works the first time
not true
i did a few installs on different pc's/laptops and **everything** worked out of the box.
besides a printer , never could get the damn to work ,so eventually sold it . problem solved lol

ps. all my pc's and laptops were really old machines,maybe that's why no problems. Iv'e kinda noticed it's the newer hardware that tends to give hassles.

---

### Post by kurt18947 on 2021-12-16
> **3nd said:**
> not true
i did a few installs on different pc's/laptops and **everything** worked out of the box.
besides a printer , never could get the damn to work ,so eventually sold it . problem solved lol

ps. all my pc's and laptops were really old machines,maybe that's why no problems. Iv'e kinda noticed it's the newer hardware that tends to give hassles.

Exactly. Fairly mainstream hardware that's been around for a year or more generally "just works".  Hardware that was just released last month could well to be problematic. It's also really helpful if the hardware manufacturer makes an effort to support *nix systems. I've purchased a couple off-lease Thinkpads and they've been flawless. 2 things working in my favor

1)  Thinkpads are pretty well supported in Ubuntu and they use mostly mainstream components.
2)  They've been 3+ years old.

---

### Post by mike430 on 2021-12-17
Yah, I don't think I was clear on my comment. Have had quite a few machines over the years where Ubuntu runs all hardware no problem. I think the point I was trying to drive home here was that when something does not work on linux, at least personally in my experience and it's not too often that things don't work, I find myself spending a ton of time on a resolution. But this is something I enjoy doing and will allocate the time. It gets more difficult to afford the time as I get older however, due to other life obligations. That's all.

---

### Post by jamesyuan on 2022-01-05
Fantastic !!!!!!!!!!!!!!!> **mike430 said:**
> It's working. Thanks for your help. It really boiled down to doing this.

go to-  [https://launchpad.net/ubuntu/impish/amd64/backport-iwlwifi-dkms/9340-0ubuntu4](https://launchpad.net/ubuntu/impish/amd64/backport-iwlwifi-dkms/9340-0ubuntu4)

download and run [FONT=var(--ff-mono)]sudo dpkg -i backport-iwlwifi-dkms_9340-0ubuntu4_all.deb

then go to [/FONT]https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git

download and run [FONT=var(--ff-mono)]sudo tar -zxf linux-firmware-20210818.tar.gz -C /lib/firmware

rebooted and was good...surprisingly. Love linux but nothing I mean nothing works the first time. 

This thread is where i got this, towards the end of the page [/FONT]https://askubuntu.com/questions/1356118/ax210-wifi-not-working-on-ubuntu21-04

---

