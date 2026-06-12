---
title: "SD Card Reader doesnt work"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by bs_one on 2009-02-27
Ok first of all, I'm a total newbie to linux / ubuntu. My problem is that I just cant use my built in SD Card reader. I'm using a HP EliteBook 8530w and using Ubuntu 8.10 Kernel 2.6.27-11-generic. I also already googled for a long time but couldnt find any solution.

Sry for my bad english but its not my first language.

thanks in advance
bs_one

---

### Post by 73ckn797 on 2009-02-27
Are you using a regular SD card or the newer type SDHC? I cannot get a SDHC card to read  but regular SD will. I have not looked for any solution.

---

### Post by bs_one on 2009-02-27
> **73ckn797 said:**
> Are you using a regular SD card or the newer type SDHC? I cannot get a SDHC card to read  but regular SD will. I have not looked for any solution.

No I'm using a normal SD card and nothing happens when I plug it in.

regards
bs_one

---

### Post by 73ckn797 on 2009-02-27
I am not using my laptop right now but if you with go to Applications/Accessories/Terminal and enter:

```
sudo lshw
```you can find the info on the card reader. That may allow you to search more precisely for info on the card reader issue(s).

It is not a Sony memory card with a provided adapter is it? I could not read the camera card using that unless I also used a USB adapter with it.

You might also try using a USB adapter for the SD card if you cannot find any solution.

---

### Post by steveneddy on 2009-02-27
A few versions back I had to purchase an SD card reader that plugged into a USB port.

Worked great that way.

Have you tried other versions of Ubuntu?

---

### Post by bs_one on 2009-02-28
> **73ckn797 said:**
> I am not using my laptop right now but if you with go to Applications/Accessories/Terminal and enter:

```
sudo lshw
```you can find the info on the card reader. That may allow you to search more precisely for info on the card reader issue(s).

It is not a Sony memory card with a provided adapter is it? I could not read the camera card using that unless I also used a USB adapter with it.

You might also try using a USB adapter for the SD card if you cannot find any solution.

output of sudo lshw is:

 *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@0000:86:09.1
                version: 25
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=0 module=sdhci_pci

nope theres no adapter included
buying a usb adapter is no solution its just running away from the problem ;)
thanks anyways

@steveneddy
no I didnt try any other versions of ubuntu yet and I probably cant trie it, because my internet is kinda slow so I'd have to wait to long to load it.

regards
bs_one

---

### Post by adult swim on 2009-02-28
what does ```
lsmod | grep sd
``` return?

---

### Post by bs_one on 2009-02-28
> **adult swim said:**
> what does ```
lsmod | grep sd
``` return?

it returns:
```

tifm_sd                18184  0 
tifm_core              16028  1 tifm_sd
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
mmc_core               58268  2 tifm_sd,sdhci
sd_mod                 42392  4 
crc_t10dif              9984  1 sd_mod
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata

```

regards
bs_one

---

### Post by 73ckn797 on 2009-03-01
> **bs_one said:**
> 
buying a usb adapter is no solution its just running away from the problem ;)
thanks anyways

Buying an adapter **IS** a solution until the problem can be fixed. If you need it to complete a necessary task then whatever works is my avenue to take.

---

### Post by steveneddy on 2009-03-01
This may be the answer to your issue:

[http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu/](http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu/)

---

### Post by bs_one on 2009-03-04
> **steveneddy said:**
> This may be the answer to your issue:

[http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu/](http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu/)

Hey thanks but I already tried that before and it didn't work. I tried it again, but it still doesn't work :(

@73ckn797
Hey sorry it just should be a joke. I don't need it for something that's REALLY important, I just don't want to have to switch to Windows to load the photos I took on my Laptop.

regards
bs_one

P.s.: Sorry that I took so long to response, but I had a lot of things to do in school.

---

### Post by bs_one on 2009-03-13
So nobody actually can help me? :(
Guess I have to find a different site to solve my problem

regards bs_one

---

### Post by 73ckn797 on 2009-03-13
> **bs_one said:**
> Hey thanks but I already tried that before and it didn't work. I tried it again, but it still doesn't work :(

@73ckn797
Hey sorry it just should be a joke. I don't need it for something that's REALLY important, I just don't want to have to switch to Windows to load the photos I took on my Laptop.

regards
bs_one

P.s.: Sorry that I took so long to response, but I had a lot of things to do in school.

Then get an adapter and you won't have to load Windows.....:D

---

### Post by bs_one on 2009-03-14
> **73ckn797 said:**
> Then get an adapter and you won't have to load Windows.....:D

^^ my problem is that I'm currently in New Zealand and I have NO idea where I can get an adapter here XD
And even if I would know where I can buy one I couldn't get, because nobody can drive me and the public transport is really bad here :/
So I thought there might be a different possibility to get it working when I got my card reader already included :)

regards
bs_one

---

### Post by ymo on 2009-03-15
I just tried Jaunty Alpha-6 on my Dell Inspiron 6000 laptop. It has the same Ricoh SDIO controller as your laptop:

```
           *-system
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 17
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
```
I had no problems accessing an SD card. I have not yet tried 8.10 on my laptop but it looks like next month's Ubuntu release might be worth trying on yours.

---

### Post by bs_one on 2009-03-15
> **ymo said:**
> I just tried Jaunty Alpha-6 on my Dell Inspiron 6000 laptop. It has the same Ricoh SDIO controller as your laptop:

```
           *-system
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 17
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
```
I had no problems accessing an SD card. I have not yet tried 8.10 on my laptop but it looks like next month's Ubuntu release might be worth trying on yours.

I'll definitely try it out and let you know if it works.

regards
bs_one

---

### Post by kansasnoob on 2009-03-15
Try simply installing pmount from synaptic! Or go to terminal and:

```
sudo apt-get install pmount
```

You'll then have to restart.

---

### Post by bs_one on 2009-03-15
> **kansasnoob said:**
> Try simply installing pmount from synaptic! Or go to terminal and:

```
sudo apt-get install pmount
```

You'll then have to restart.

It seems that I for some reason already have got it installed?

```
 sudo apt-get install pmount
[sudo] password for jakob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pmount is already the newest version.
pmount set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I didn't install it I'm quite sure...

regards
bs_one

---

### Post by zabien1970 on 2009-03-15
I'm running a dell laptop with 8.10 and it reads my card fine. sometimes though I have to eject it then put it back in for it to mount. it shows up as an icon on my desktop

---

