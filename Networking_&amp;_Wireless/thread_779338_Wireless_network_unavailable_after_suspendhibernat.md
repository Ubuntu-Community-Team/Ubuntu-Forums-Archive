---
title: "Wireless network unavailable after suspend/hibernate/resume ACER3624W MADWIFI HARDY"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Impact_666 on 2008-05-02
Hello!

I'm currently running Ubuntu v8.04 on an Acer Aspire 3624W laptop w/ Atheros WIFI w/ Madwifi.

When I resume from suspend or hibernate, the wireless network becomes inaccessible.

I'm able to restore access if I perform the following commands:

ifdown ath0
ifup ath0

I've been looking over the /etc/acpi/ directory (and subs), but I'm not sure how I should go about affecting change.

Has anyone else experienced this, and is there a fix?

---

### Post by Phinnay on 2008-05-06
I am having the same problem on my Inspiron 2650 with a D-link DWL-G650 PCMCIA card. 

Every time I put the laptop into hibernate and bring it back up, I must reboot before the wireless will work again. Using the ifdown and ifup thing as you posted will work some of the time. It is pretty annoying that this doesn't seem to function properly. 

Is there a script that runs when the laptop comes out of hibernate that I can add those commands to?

---

### Post by Impact_666 on 2008-05-06
> **Phinnay said:**
> Is there a script that runs when the laptop comes out of hibernate that I can add those commands to?

Take a look in /etc/acpi.  There are scripts and directories with more scripts :)

When I look over the scripts, they look good to me (not that I would know any better ;)  I tried messing around with a few things, with no results.

Since I'm new to Linux, I have lots of questions.  The main one is, what actually happens during suspend/hibernate and resume events that is causing the network connection to stop working?  If I could learn the answer to this, perhaps I could find a solution.

I'll have to do some more learning methinks :)

---

### Post by sirclaudio on 2008-05-07
I recommend to you to add the wireless drivers to the blacklist in /etc/default/acpi-support. This way, whenever you suspend/hibernate, it will remove the driver and it modprobe it when you resume. Don't know if it will work, but it's harmless if you try.

---

### Post by Impact_666 on 2008-05-09
> **sirclaudio said:**
> I recommend to you to add the wireless drivers to the blacklist in /etc/default/acpi-support. This way, whenever you suspend/hibernate, it will remove the driver and it modprobe it when you resume. Don't know if it will work, but it's harmless if you try.

Thanks for the suggestion.  I tried that last night, and it was unsuccessful :(

I added some code of my own to /etc/acpi/resume.d/62-ifup.sh that creates a file on my desktop when executed.  Guess what - it's not being executed on resume.

If I manually execute this script, my tell-tale file is created, and the network is restored.

I found lots of references to editing the 62-ifup.sh file.  I had a really hard time doing this.  Nothing happened when I did a sudo gedit /etc/acpi/resume.d/62-ifup.sh, but I could edit the file if I copied it to my desktop, then edit it, save it, then copy it over the old one.  Is that odd, or am I missing something?

---

### Post by gib2800 on 2008-12-30
It's probably a little late, but I found this solution for the same problem. First get a list of system hardware with this command in terminal:
```
lswh
```
Find network/ethernet/wireless, under "configuration" line will be a driver (mine was “driver=ath_pci")
Now edit your "00sleep_module" file in terminal:
```
sudo gedit /etc/pm/config.d/00sleep_module
```
At the end of the file, add the following, substituting the name of your driver for "ath_pci."
```
SUSPEND_MODULES="ath_pci"
```

---

### Post by danmarycap on 2009-03-11
what does adding "Suspend_Modules" do?  will it automatically renew the ip from DHCP upon resume?

Update: I've posted a similar solution here ([http://ubuntuforums.org/showthread.php?p=6883391](http://ubuntuforums.org/showthread.php?p=6883391)) with a shout-out to gib2800 for the code above.

-Dan

---

