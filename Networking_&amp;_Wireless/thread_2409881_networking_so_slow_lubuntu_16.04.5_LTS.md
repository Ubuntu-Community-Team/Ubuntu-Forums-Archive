---
title: "networking so slow lubuntu 16.04.5 LTS"
date: 2019-01-08
forum: Networking &amp; Wireless
---

### Post by carlsonv on 2019-01-08
i have recently done fresh install of lubuntu as per title and the wireless internet is so slow but the wired connection is good.  i have run the script as per instruction here is the paste [http://paste.ubuntu.com/p/DjbfjCtxqW/](http://paste.ubuntu.com/p/DjbfjCtxqW/).  the system works fine except that i cannot use the wireless connection as it is so unstable and slow
any help is much appreciated

kind regards
Mark

---

### Post by chili555 on 2019-01-08
May I assume that you have already instituted the usual fixes?

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

I also notice this file:> [/etc/modprobe.d/rt2800.conf]
options rt2800pci nohwcrypt=1According to:```
modinfo rt2800pci
```...the paramater is boolean; that is Y or N. I suggest that you amend the file to read:```
options rt2800pci nohwcrypt=Y
```It may or may not make any difference, but why not do it right?

---

### Post by carlsonv on 2019-01-08
Thank you for your help, I will implement the changes and report back.  I apologize for the jump on a different thread....very much a noob move.  Thank you for kindly pointing that out

cheers

---

### Post by carlsonv on 2019-01-08
i have implemented the suggested changes and rebooted everything as instructed and the wireless connection is poor.  here is new pastebin with changes as suggested [http://paste.ubuntu.com/p/JbYfGvgZrZ/](http://paste.ubuntu.com/p/JbYfGvgZrZ/)

anything else? would upgrading the kernel to a newer version (say 4.19) fix this? i am just throwing an idea perhaps this is the incorrect approach

appreciate your insights

thank you

---

### Post by carlsonv on 2019-01-08
apologize for last post (post #4) i gave bad information here is the updated (corrected) pastebin. i did implement suggestions and still no improvement.
thank you in advance

[http://paste.ubuntu.com/p/vXgGzBzbv6/](http://paste.ubuntu.com/p/vXgGzBzbv6/)

---

### Post by carlsonv on 2019-01-08
do you think the driver is correct for wireless? i have a ralink RT5390R 802.11bgn PCIe card and when i connect the information for wireless say "rt2800pci" as my wireless driver.

---

### Post by chili555 on 2019-01-09
> **carlsonv said:**
> do you think the driver is correct for wireless? i have a ralink RT5390R 802.11bgn PCIe card and when i connect the information for wireless say "rt2800pci" as my wireless driver.As far as I know it is the correct and, in fact, the only driver available in modern Ubuntu versions. There are a number of purported rt5390sta drivers out there but they are all based on Mediatek's circa-2011 driver. Those will not compile on any 4.xx kernel.

As to whether a newer kernel version might help, I really don't know. It sould be easy enogh to test, however. I suggest that you download the beta version of Ubuntu 19.04: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) Make a USB or DVD with the image and try a live session. Does the wireless work better?

Frankly, and this is only my opinion and in no way is supported by the forum or Ubuntu themselves, the rt2800xx series chipsets and drivers have always been a bit twtchy. In your paste, we see nothing whatever wrong. It ought to work perfectly except it just doesn't. I am not at all sure I can think of another suggestion that doesn't involve a screwdriver.

---

### Post by carlsonv on 2019-01-09
ok, thank you for helping.  the Laptop i am putting this on is old and does not really have the power to run ubuntu well...i put lubuntu 16.04 on it to help with that (LXDE is very nice).  Is there a beta version of lubuntu i could try to see if it fixes the network issue?

the laptop is a HP 2000 with 2x intel Celeron CPU B820 1.7Ghz (2GB RAM)

kind regards

---

### Post by carlsonv on 2019-01-09
disregard last post, i had a brain lapse on that question.....i found the lubuntu beta 19.04

---

### Post by chili555 on 2019-01-09
> **carlsonv said:**
> disregard last post, i had a brain lapse on that question.....i found the lubuntu beta 19.04Please keep us posted. Does the wireless work better? What is the kernel version in 19.04?```
uname -r
```

---

### Post by carlsonv on 2019-01-10
i have tried 19.04 and have no luck.....the wireless is still poor.  kernel version was 4.18

regards

---

### Post by chili555 on 2019-01-10
> 
Frankly, and this is only my opinion and in no way is supported by the forum or Ubuntu themselves, the rt2800xx series chipsets and drivers have always been a bit twtchy.
All I have left to suggest is a different device. Sorry.

---

### Post by carlsonv on 2019-01-10
what about changing the wireless card? or using a USB wifi?  seems like this laptop with RT5390R is the problem otherwise the laptop is fine

what do you think?

regards

---

### Post by chili555 on 2019-01-10
> **carlsonv said:**
> what about changing the wireless card? or using a USB wifi?  seems like this laptop with RT5390R is the problem otherwise the laptop is fine

what do you think?

regardsIsn't that exactly what I suggested?> All I have left to suggest is a different device. Sorry.If you don't have any whitelist issues, I'd replace the internal device with an Intel.

---

### Post by carlsonv on 2019-01-11
ok, got er.  i have plugged in a USB wifi it works!!!!!  i was going to try replace the internal device but the cost was absolutely ridiculous and it would only accept specific wireless chips (it is whitelisted to only specific hardware).  i bought this USB wifi for $29 instead of the $160 internal chip.  i plugged it in and was able to connect with it and it works flawlessly.  

do you know how i could disable the Ralink internal chip so my computer just uses the usb wifi?  i can easily flip laptop over, remove batter and one screw and the chip pops right out if that is the best way but i wanted to know if there is a different method.

kind regards

---

### Post by chili555 on 2019-01-11
Removing the internal card is, of course, foolproof. You can also blacklist its driver.```
sudo -i
echo "blacklist rt2800pci"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r rt2800pci
exit
```I am surprised at the costs you quote. I replaced my whitelisted card for $20 from Ebay.

Do you have any details as to the allowed; i.e. whitelisted cards?

This suggests that the service manual, usually available online, will show the cards on the whitelist: [https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/Replacement-of-Mediatek-MT7630E-802-11-bgn-wireless-card/td-p/5270474](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/Replacement-of-Mediatek-MT7630E-802-11-bgn-wireless-card/td-p/5270474)

Does your current card have one antenna wire or two? If only one, then you needn't look for an AC-capable card since it will require two.

[http://www.insidemylaptop.com/images/HP-Pavilion-dm4-base/disassemble-laptop-06.jpg](http://www.insidemylaptop.com/images/HP-Pavilion-dm4-base/disassemble-laptop-06.jpg)

---

### Post by praseodym on 2019-01-11
Lets try
```

sudo iwconfig wlo1 power off
```

---

### Post by carlsonv on 2019-01-12
yes i was surprised also by that cost! Considering i got a usb wifi for $30 and it works fine (better than the old chip for sure!!) i can't believe anyone would want to replace the internal one for that price ($160 is atrocious).  yes i found a list of acceptable ones on an HP forum (there was 5-6 i think).  i could see $160 for the chip with bluetooth and wifi radios on it but my chip had only one radio and one of the chips on the list was wifi radio only and still wanted $160!  what i ended up doing is flipping the laptop over popped one screw out and the chip is right there, i removed it.  booted up and the wifi usb is working perfectly

thank you kindly for all help, very much appreciated!  

kind regards

---

