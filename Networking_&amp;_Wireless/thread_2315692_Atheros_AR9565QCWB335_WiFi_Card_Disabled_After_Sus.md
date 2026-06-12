---
title: "Atheros AR9565/QCWB335 WiFi Card Disabled After Suspend"
date: 2016-03-01
forum: Networking &amp; Wireless
---

### Post by Buecai9ahd on 2016-03-01
I bought an HP Envy K201NA laptop recently and installed Ubuntu 15.10 on it.
The problem I have is that when I put it to sleep, the wireless disables itself with a hard block on wake and won't re-enable.

It originally had a Broadcom BCM4350 in it which I ditched because it wasn't supported and nothing worked to fix the problem. 
I swapped it with an Atheros AR9565 because it's the same one I was using in my old laptop which worked without problems (although the old laptop was running 15.04 rather than 15.10).

Low and behold when I swapped the wireless card into my new laptop, I got the same problem as the original card, disabled on resume.
And the same problem of WiFi being disabled on resume happens on the 15.04 and 15.10 live USBs I tested.

I've tried the usual:
Trying the hardware switch which just seems to toggle the soft block and doesn't do anything (unless I haven't suspended in which case it turns the WiFi on and off as it should)
sudo rfkill unblock all, sudo rfkill unblock wifi
Checking the BIOS for anything that could potentially block it
Reset the BIOS settings

Restarting the laptop is the only way to get the WiFi working again.
When I try ```
sudo ifconfig wlo1 up
``` it says operation not possible due to RF-Kill. 
I've attached the output of the wireless-info script when it's unblocked and again when it's blocked!
Something is happening to block the WiFi on resume, can anyone help? It's driving me crazy.

---

### Post by chili555 on 2016-03-01
I am not sure this is the entire reason, but it is related to suspend and it's wrong, so let's try fixing it and see if it helps.> ##### pm-utils ##########################

[/etc/pm/config.d/config] (644 root)
SUSPEND_MODULES="wl"
Your driver isn't *wl*; it is *ath9k*. Moreover, we see ath9k is still loaded after suspend. Let's remove the improper file:```
sudo rm /etc/pm/config.d/config
```Also, we see this:> [/etc/pm/sleep.d/10_resume_wifi~] (644 root)
caseGenerally, a file appended with ~ is a systems back-up file. I don't know if the simple word 'case' does anything here, but, just in case, let's try removing it, too:```
sudo rm /etc/pm/sleep.d/10_resume_wifi~
```Reboot and let us hear your report. 

If the issue remains, let us have wireless scripts again.

---------------

Reference for chili: [http://askubuntu.com/questions/638124/no-wifi-after-suspend-on-15-04/642559](http://askubuntu.com/questions/638124/no-wifi-after-suspend-on-15-04/642559)

---

### Post by Buecai9ahd on 2016-03-02
Hi Chili and thanks for your reply!
I removed the config file and also the 10_resume_wifi~ file and rebooted but no luck I'm afraid.
I've attached a new wireless-info if you could spare the time to have a look!
Thanks a lot.

---

### Post by chili555 on 2016-03-02
Let's try one of the techniques in the link I referenced. Please open a terminal and do:```
sudo gedit  /etc/systemd/system/wifi-resume.service
```Use nano or kate or leafpad if you don't have the text editor gedit. A new empty file will open. Add the following:```
[Unit]
Description=Local system resume actions
After=suspend.target

[Service]
Type=oneshot
ExecStart=/bin/systemctl restart network-manager.service

[Install]
WantedBy=suspend.target
```Proofread carefully twice, save and close the text editor.

Now do:```
sudo chmod +x  /etc/systemd/system/wifi-resume.service
```And next:```
sudo systemctl enable wifi-resume.service
```Just to be on the OCD, safe, belt-and-suspender mode, I suggest you reboot. Test and let us hear your report.

---

### Post by Buecai9ahd on 2016-03-02
Hi Chili,

I've tried your steps and alas no luck, the same issue is occurring. 
I have noticed after resuming from suspend in the System Settings > Network window aeroplane mode is on. If I disable airplane mode and try flick the wireless network switch to 'on' it won't switch and keeps reverting to 'off'.
Sigh.

---

### Post by chili555 on 2016-03-02
Let's remove what we tried and that didn't work:```
sudo systemctl disable wifi-resume.service
```The file we created is needless; let's remove it:```
sudo rm /etc/systemd/system/wifi-resume.service
```Now reboot. Get to the GRUB menu by pressing the right shift key as quickly as you can after the BIOS or set-up page disappears. Select Advanced Options and then highlight and boot in upstart. Test.

[ATTACH=CONFIG]267608[/ATTACH]

---

### Post by Buecai9ahd on 2016-03-03
Okay, I've tried that and it is the same. What's the difference between 'upstart' and a normal boot?

---

### Post by Buecai9ahd on 2016-03-03
I booted into Trisquel (debian based) and Manjaro (arch based) live distros and the same thing happened on them. Do you think this is something to do with the network cards themselves that causes the same issue on different distros?

---

### Post by Buecai9ahd on 2016-03-19
If it helps anyone else, it was the laptop itself or something in the BIOS that couldn't be changed that was doing something odd with the network cards in Linux. Who knows.
But third network card lucky! I tried it with an Intel 6300 card and the problem was sorted.

---

