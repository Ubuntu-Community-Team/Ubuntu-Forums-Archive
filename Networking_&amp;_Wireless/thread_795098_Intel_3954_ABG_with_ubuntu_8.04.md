---
title: "Intel 3954 A/B/G with ubuntu 8.04"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by sagivegh on 2008-05-15
Hi all,

I have a problem...
I have Lenovo N200 B5G with Intel PRO/Wireless 3954 A/B/G, and installed Ubuntu 8.04, and I can't connected to the wifi network...
and the LED of the wifi don't work!!!
I tried to install ndiswrapper driver, but didn't work for me...
and I tried to install the backport too, but didn't work too...

Please help me, Anybody...

Thanks,
Sagi

---

### Post by chili555 on 2008-05-15
I wonder what driver it thinks it's using now, after all that. Please let us see:```
lsmod | grep ndis
lsmod | grep iwl
sudo cat /var/log/messages | grep switch
```Thanks.

---

### Post by notwen on 2008-05-15
I'm betting you're still using the ipw module for your Intel 3945 wireless.  The ipw module is being replaced by the iwl module, which is a lot more stable.  Type the following into a term:

```
$ lsmod | egrep 'Module|iwl|ipw'
```

You're wanting output w/ **iwl**, not **ipw**.  If you're sitll using ipw, let's blacklist it and add iwl. To do this let's do the following:

```
sudo gedit /etc/modprobe.d/blacklist-ipw3945
```

Add the following to your new file and save/close:

```
blacklist ipw3945
```

Now add the iwl module:

```
sudo gedit /etc/modules
```

Add the following to /etc/modules and save/close:

```
iwl3945
```

Now run the first command again, hopefully you'll see **iwl** and not **ipw**.

```
$ lsmod | egrep 'Module|iwl|ipw'
```



Post back if you run into any issues, I also use this wireless chipset and can verify that ndiswrapper is not needed.  This new module should also correct your wifi LED, although it won't blink w/ activity, it will only light up when connected.  Future drivers should correct this though.  =]

---

### Post by sagivegh on 2008-05-18
Hi again,

OK...I checked and I running the system only with the iwl module,
so...this is my output for chili555:

lsmod | grep iwl:

sagi@sagi-laptop:~$ lsmod | grep iwl
iwl3945               104820  0 
led_class               7176  1 iwl3945
iwlwifi_mac80211      251876  1 iwl3945
cfg80211               17680  1 iwlwifi_mac80211

lsmod | grep ndis:

sagi@sagi-laptop:~$ lsmod | grep ndis
ndiswrapper           243872  0 
usbcore               169904  7 uvcvideo,hci_usb,ndiswrapper,usbhid,uhci_hcd,ehci_hcd

sudo cat /var/log/messages | grep switch:

sagi@sagi-laptop:~$ sudo cat /var/log/messages | grep switch
[sudo] password for sagi: 
May 15 02:52:24 sagi-laptop kernel: [   20.558090] SMP alternatives: switching to UP code
May 15 02:52:24 sagi-laptop kernel: [   21.200889] SMP alternatives: switching to SMP code
May 15 02:52:24 sagi-laptop kernel: [   21.308289] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 15 12:42:21 sagi-laptop kernel: [   28.540781] SMP alternatives: switching to UP code
May 15 12:42:21 sagi-laptop kernel: [   29.174072] SMP alternatives: switching to SMP code
May 15 12:42:21 sagi-laptop kernel: [   29.279842] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 15 13:28:11 sagi-laptop kernel: [   28.976809] SMP alternatives: switching to UP code
May 15 13:28:11 sagi-laptop kernel: [   29.608534] SMP alternatives: switching to SMP code
May 15 13:28:11 sagi-laptop kernel: [   29.713400] ACPI: EC: non-query interrupt received, switching to interrupt mode
May 18 14:18:32 sagi-laptop kernel: [   16.498764] SMP alternatives: switching to UP code
May 18 14:18:32 sagi-laptop kernel: [   17.131699] SMP alternatives: switching to SMP code
May 18 14:18:32 sagi-laptop kernel: [   17.236518] ACPI: EC: non-query interrupt received, switching to interrupt mode

Thanks again,
Sagi

---

### Post by chili555 on 2008-05-18
Both iwl3945 and ndiswrapper are getting loaded. You want one or the other, not both. Since the *backports* driver works so well for most people, let's try:```
sudo rmmod -f ndiswrapper
```Does your 3945ABG work now? If so, we'll expel ndiswrapper from school for not playing well with others.

> usbcore 169904 7 uvcvideo,hci_usb,ndiswrapper,usbhid,uhci_hcd,ehci_ hcdDo you have a separate USB wireless device you are using ndiswrapper with?

May we see:```
iwconfig
```Thanks.

---

### Post by sagivegh on 2008-05-18
Hi again,

I did what you told me, to do, and still nothing...
so, I downgrade the version back to Ubuntu 7.10,
and the did upgrade to 8.04, and with the old kernel 2.6.22-14
the wireless is working...

---

### Post by Charlie708 on 2008-05-19
Try this fix, it worked for my T61 with 3945 wireless:
[http://ubuntuforums.org/showpost.php?p=4852027&postcount=10](http://ubuntuforums.org/showpost.php?p=4852027&postcount=10)

---

### Post by sagivegh on 2008-05-21
This didn't work for me...
the wifi light went on and then off...

---

### Post by sagivegh on 2008-06-05
Hi,

I found a solution to the problem:
First, you will need to enter this command line:
```
sudo echo "options iwl3954 disable_hw_scan=1" > /etc/modprobe.d/iwl3945
```

And reboot, or reload the iwl3954 module:
```
sudo modprobe -r iwl3945 && sudo modprobe iwl3945
```

And last thing is the LED that don't work, so the linux-backports-modules-hardy-generic. fix this.

---

### Post by montas on 2009-03-16
i tried all of these aswell. i fixed it by going into BIOS and selecting Restore Defaults.

Light came on and WIreless Worked

---

