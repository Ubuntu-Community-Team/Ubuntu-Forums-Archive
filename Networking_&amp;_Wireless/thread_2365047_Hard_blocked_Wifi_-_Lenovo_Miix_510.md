---
title: "Hard blocked Wifi - Lenovo Miix 510"
date: 2017-07-01
forum: Networking &amp; Wireless
---

### Post by max-bernd on 2017-07-01
Hello,

since I reinstalled Windows 10 after the purchase of my Lenovo Miix 510, to get rid of the preinstalled software, the network-adapter has stopped working. I reinstalled the drivers several times but I could not get it to work. 

A few days ago I switched to Linux and installed Ubuntu 17.04. Unfortunately it's still not working. With "rfkill list" I could see that the Wifi + the Bluetooth are hard blocked. There isn't any physical switch to turn the wifi off/on and I tried to activate it via the F7-Key (also in combination with the fn-Key), and I checked and reseted the BIOS. No changes at all.

I've run the wireless-info-script and here is the output: [https://pastebin.com/fc9q4S4y](https://pastebin.com/fc9q4S4y) (before running the script I updated my system via "sudo apt update" and "sudo apt dist-upgrade")

I hope you can help me and thanks in advance.


//Edit: of course I tried to use google for the problem but either I didn't understand what excactly to do or it hasn't solved the problem

---

### Post by jeremy31 on 2017-07-01
This should get your wireless going ```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
```
Reboot

If it works I suggest filing a bug report, see [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) against package linux so your model might be added to the quirks list in the source code

---

### Post by max-bernd on 2017-07-01
Thanks for your answer. It still doesn't work, but now it doesn't show up after I enter the command "rfkill list". 

Here is the new PasteBin: [https://pastebin.com/p94yyhCR](https://pastebin.com/p94yyhCR)

I hope you have another suggestion :)

---

### Post by praseodym on 2017-07-01
Check this here:

[https://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](https://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

---

### Post by max-bernd on 2017-07-01
> **praseodym said:**
> Check this here:

[https://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](https://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

Thanks but it didn't work... I couldn't try the second point because I can't remove the battery

---

### Post by praseodym on 2017-07-01
Any button, switch key or key combo?

---

### Post by max-bernd on 2017-07-01
> **praseodym said:**
> Any button, switch key or key combo?

The only possible button could be the "airplane-mode"-button on the F7-Key but it doesn't change anything. Doesn't matter if I try it with or without the fn-Key...

---

### Post by max-bernd on 2017-07-03
Any further ideas? I am despairing :(

---

### Post by johndough2 on 2017-07-03
Hi

I do not understand the question.

So to help me

Does / did ethernet work in windows
Did /does WiFi work in windows

Does / did ethernet work in Ubuntu
Did /does WiFi work in Ubuntu

##########################

I would look very carefully at all the BIOS settings to see if WiFi is enabled on the motherboard, of course if it works in windows that will be a yes.

#################################
since I reinstalled Windows 10 after the purchase of my Lenovo Miix 510, to get rid of the preinstalled software, the network-adapter has stopped working. I reinstalled the drivers several times but I could not get it to work. 
#################

So please give us some details of what has been done, in chronological order if possible.

---

### Post by jeremy31 on 2017-07-03
It might help to revert my change with
```
sudo rm /etc/modprobe.d/ideapad-laptop.conf
```

Reboot

---

### Post by linxify on 2017-08-13
Description:	Ubuntu 16.04.3 LTS
MIIX-510-12ISK 4.11.0-13-generic #19~16.04.1-Ubuntu SMP Wed Aug 2 20:06:21 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

This worked for me.
first, like many have mentioned earlier, in a terminal window, execute  
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
then reboot.
Access the Bios with F2. Disable the 'Intel Secure Platform ... ', its the option under the 'Secure Boot'
Wifi is now not hardblocked and is usable.

and yes, had installed the linux-image-generic-hwe-16.04 using a usb type-c to ethernet dongle earlier.

---

### Post by johndough2 on 2017-08-13
Hi

Sometimes a battery reset via the pinhole on the underside?

---

### Post by chili555 on 2017-08-13
After a fresh reboot, may we see:```
dmesg | grep -e wlp -e iwl
```

---

