---
title: "QCA9377 not working post update"
date: 2017-08-08
forum: Networking &amp; Wireless
---

### Post by recoder2 on 2017-08-08
Hey! I am currently on Ubuntu 14.04 LTS (+Windows 10 Dual Boot). I usually defer from any updates but today I installed updates (Settings -> Details --> Check for Updates). I am still on 14.04.
I have QCA9377 Wifi Adapter and it did not work earlier. So I had to backport 20151120 and also install ath10k-firmware. And then it worked.
Post the updates, the wifi stopped working again only this time backporting / installing the firmware does nothing. Wifi still does not work.

lib/firmware/ath10k/QCA9377/hw1.0 and its files still present but there is no wifi detected. ( lspci shows 3:0:0 Qualcomm 0042 (rev 30)

---

### Post by jeremy31 on 2017-08-08
See the wireless script link in my signature and post your results
Welcome to the forums

---

### Post by recoder2 on 2017-08-08
[https://pastebin.com/iAhCd2qg](https://pastebin.com/iAhCd2qg)

---

### Post by jeremy31 on 2017-08-08
What happens if you ```
sudo modprobe -v ath10k_pci
```
I think you may have to try building the backports again

---

### Post by recoder2 on 2017-08-08
insmod /lib/modules/4.2.0-42-generic/updates/compat/compat.ko 
modprobe: ERROR: could not insert 'ath10k_pci': Required key not available

I tried make backport a few times already, then sudo make install
Also, while make backports, i had "can't read private key"

---

### Post by jeremy31 on 2017-08-08
Is Secure Boot enabled in UEFI(BIOS)?  I would have you update to the 4.4 kernel series but I think it might break the graphics support with Ubuntu 14.04

---

### Post by recoder2 on 2017-08-08
Yes. secure boot is enabled

---

### Post by jeremy31 on 2017-08-08
If you want to use Secure Boot you will need the 4.4 kernel, instruction [here](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop-1) otherwise you can turn it off and the backports will work
If you have graphics issues with 4.4 press shift during reboot until the grub menu appears, select previous linux versions or advanced options then select the old kernel to boot to.  The 4.2 kernel series has been unsupported for a year now and the 4.4 kernel is supported for longer than Ubuntu 14.04 will be

---

### Post by recoder2 on 2017-08-09
Thanks. Backport is working after disabling secure boot with kernel 4.2.0.42. btw, wifi works with secure boot and 4.2.0.27. Guess its time to upgrade to 16 series maybe.

---

### Post by kimnov on 2017-08-13
I tried the suggested steps, but unfortunately my wifi is still not working. Here is the link for the info [http://paste.ubuntu.com/25305843/](http://paste.ubuntu.com/25305843/).
Can someone help me with the problem??
TY

---

### Post by praseodym on 2017-08-13
Hi kimnov,

in your case the firmware is not loading correctly, see the "dmesg" section of the script output. Upgrade the firmware via cable
```

sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```
Reboot

---

### Post by kimnov on 2017-08-14
Thank you so much, you with the name of a cool chemical element ;p (btw why praseodymium? just curious because i studied chemistry)
Thank you very very  much. I'm so happy to see the wifi above the beautiful purple :D 
Greetings and I wish you a really nice day!!
Kim

---

### Post by praseodym on 2017-08-14
Looked for a nickname for a email portal back then during NMR practises using praseodymium as paramagnetic shifter ;)

Glad it works. Please use thread tools to mark it "SOLVED"

---

### Post by kimnov on 2017-08-15
I don't see the "marked as solved option" otherwise I would do it:| Maybe because I didn't start the thread??

---

### Post by praseodym on 2017-08-15
Well...yes :)

---

