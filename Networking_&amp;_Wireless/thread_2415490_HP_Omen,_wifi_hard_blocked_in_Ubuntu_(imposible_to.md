---
title: "HP Omen, wifi hard blocked in Ubuntu (imposible to switch on) with dual boot"
date: 2019-03-26
forum: Networking &amp; Wireless
---

### Post by lateow on 2019-03-26
Hi everyone, 

 First of all, I want to apologize for my bad english and for that I'm a beginner in the world of linux. 

I have Windows 10 installed in my HP Omen, and I've installed dual boot  with Ubuntu. All works fine, except for the wireless... (ethernet is ok)  

I can't switch it on, and show that no wifi adapter found. (Appears but hard blocked with rfkill list)

Here is the script : [http://paste.ubuntu.com/p/8PdmYwJp3p/]("http://paste.ubuntu.com/p/8PdmYwJp3p/?fbclid=IwAR2kuiNdji-jJdaAfzjzfweZUcE8llW-cIxo1vfCgt1EpGZmv0na_p1TClM")[URL="http://paste.ubuntu.com/p/8PdmYwJp3p/?fbclid=IwAR2kuiNdji-jJdaAfzjzfweZUcE8llW-cIxo1vfCgt1EpGZmv0na_p1TClM"]
[/URL]
Seems that I have the same problem than : [https://ubuntuforums.org/showthread.php?t=2414598](https://ubuntuforums.org/showthread.php?t=2414598) (unsolved) 

I've tried almost all the typical things (even too much!) :  
         - its sure that this is not the button off the keypad!
         - secure boot is disabled in the BIOS 
         - as you can see I blacklisted all of the things I saw linked with this problem on the web.   
         - this lines too : 
[COLOR=#808080][SIZE=1][I]
sudo apt-get install dkms git build-essential
git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
Thing I've not done : reset the setup default in the BIOS (this will not change my dual boot?) 
[/I][/SIZE][/COLOR]

All kind of help more than welcomed, I'm trying to fix to for months :'( 

Thanks. 


[URL="http://paste.ubuntu.com/p/8PdmYwJp3p/?fbclid=IwAR2kuiNdji-jJdaAfzjzfweZUcE8llW-cIxo1vfCgt1EpGZmv0na_p1TClM"]
[/URL]

---

### Post by chili555 on 2019-03-26
The issue of HP wireless being inoperable because of a hard block and therefore the usual wireless key not toggling wireless on and off is long-standing. There are only a few things you can try.

First, try removing the helper module hp_wmi and then try to switch the wireless on with the key combination. 

You could also try:

```
sudo modprobe -r hp_wmi
sudo rfkill unblock all
rfkill list all
```

Second, check the user guide for your HP laptop and be certain that the wireless key combination you are using is correct. Be certain that you are not using Fn+F12, for example, if the user guide says it is simply F12. On the other hand, if you are certain you are using the correct sequence, try the wrong sequence as an experiment; i.e., use Fn+F12 (or whatever your sequence is) if the user guide says it’s F12 and vice versa.

Next, you can remove the card, tape off pin 20 and re-insert it: [https://ubuntuforums.org/showthread.php?t=2150597](https://ubuntuforums.org/showthread.php?t=2150597)

You can, if all these steps fail, file a bug report against the module hp_wmi: [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Finally, in many, but not every case, a USB wireless will also be hard blocked for the same reasons. If you want to try one, be certain to try it within a return period.

I regret that there isn’t a better answer for HP laptops.

---

### Post by lateow on 2019-03-28
Thank you very much for you answer! Its confirms me that this is almost incurable ... :'(

The modprobe command with the hp_wmi module doesn't change anything.. 

I will try to remove the card as the thread you send to me say and report if it still doesn't work. 

By replacing Ubuntu with ArchLinux or LinuxMint I will still have the same problem, no? 
All others OS except Windows will never have wireless working ?

---

### Post by jeremy31 on 2019-03-28
You could try going into BIOS and reset to defaults

---

### Post by chili555 on 2019-03-28
> 
By replacing Ubuntu with ArchLinux or LinuxMint I will still have the same problem, no? 
I suspect so. You might search the Mint and Arch forums for hp_wmi and see what you find.

@jeremy31 is a frequent flyer on the Mint forum. Perhaps he can offer an opinion.

We will be interested in your report.

Is the behavior the same with both a cold boot and a reboot from Windows?

---

### Post by jeremy31 on 2019-03-28
Mint uses Ubuntu kernels so the result will be the same in Mint.

Why was acpi=off added to grub?

---

