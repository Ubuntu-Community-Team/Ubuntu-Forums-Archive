---
title: "No bluetooth on R61"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by Johann Spies on 2008-08-18
I am running 64-bit 8.04 on my Lenovo R61.  I have no success at all in getting bluetooth to work.  The led's for the wireless and bluetooth does not work at all.

From what I have read bluetooth should be easy to use on Ubuntu Hardy.  I also own a Macbook and there it is easy.  However, I have made no progress at all after spending a few hours of googling and experimenting.
More information:

% sudo hcid -n
hcid[32428]: Bluetooth HCI daemon
hcid[32428]: Could not become the primary owner of org.bluez
hcid[32428]: Unable to get on D-Bus

%  % dmesg | grep lue 
[   77.949290] Bluetooth: Core ver 2.11
[   77.952353] Bluetooth: HCI device and connection manager initialized
[   77.952362] Bluetooth: HCI socket layer initialized
[   77.975134] Bluetooth: L2CAP ver 2.9
[   77.975143] Bluetooth: L2CAP socket layer initialized
[   78.130133] Bluetooth: RFCOMM socket layer initialized
[   78.130158] Bluetooth: RFCOMM TTY layer initialized
[   78.130162] Bluetooth: RFCOMM ver 1.8

 % lsmod | grep lue
bluetooth              67748  4 rfcomm,l2cap

% bluetooth-applet   
Bluetooth OBEX server failed: Bluez DBus interface not available

% wajig list bluez
ii  bluez-audio         3.26-0ubuntu6          Bluetooth audio support
ii  bluez-cups          3.26-0ubuntu6          Bluetooth printer driver for CUPS
ii  bluez-gnome         0.25-0ubuntu1          Bluetooth utilities for GNOME
ii  bluez-utils         3.26-0ubuntu6          Bluetooth tools and daemons

 % uname -a
Linux demensie 2.6.24-21-generic #1 SMP Tue Aug 12 13:03:01 UTC 2008 x86_64 GNU/Linux

% grep blue /var/log/syslog
Aug 18 14:39:26 demensie hcid[32415]: Could not become the primary owner of org.bluez
Aug 18 14:39:44 demensie hcid[32428]: Could not become the primary owner of org.bluez
Aug 18 14:41:52 demensie hcid[25746]: Default passkey agent (:1.4222, /org/bluez/passkey) registered
Aug 18 14:41:52 demensie hcid[25746]: Default authorization agent (:1.4222, /org/bluez/auth) registered
Aug 18 14:47:36 demensie hcid[25746]: Unregister path: /org/bluez
Aug 18 14:47:36 demensie audio[25753]: Removing service record 0x10000 failed: The name org.bluez was not provided by any .service files
Aug 18 14:47:37 demensie input[392]: Registered input manager path:/org/bluez/input
Aug 18 14:47:37 demensie audio[395]: Registered manager path:/org/bluez/audio

Regards
Johann

---

### Post by jasper.noid on 2008-08-24
Same problem here.

I'm running 32-bit Kubuntu 8.04 on an R61 and I've been looking for a solution for about a month now. I got in touch with the poster of 

  [http://www.nabble.com/missing--proc-acpi-ibm-bluetooth-td17998095.html](http://www.nabble.com/missing--proc-acpi-ibm-bluetooth-td17998095.html)

He told me only a few days ago that he eventually got it fixed because he discovered how to turn bluetooth on in the BIOS, warning me that indeed the option is not called "BIOS".

Well I looked and I looked but really there isn't all that much to configure in the R61's BIOS, and I couldn't find anything that hinted at bluetooth, except perhaps the "Wireless radio frequency" which of course is set to "Enabled".

I've kinda given up. Was thinking of installing XP on a separate partition, but I suspect XP won't detect it either, as reported here:

  [http://www.bleepingcomputer.com/forums/topic157589.html](http://www.bleepingcomputer.com/forums/topic157589.html)

The hardware seems to be completely disabled, as nothing suggesting any bluetooth capability even shows up in lshw's output. Someone suggested that perhaps my exact model (7732-A47) just doesn't have a bluetooth adapter. Although that seemed silly at the time, because it is marketed everywhere as having bluetooth, I am wondering if perhaps it's true. You see, I read somewhere that in the R61's that *do* support bluetooth, the bluetooth adapter is integrated with the wireless adapter. And my wireless adapter is the Intel PRO/Wireless 3945BG, which is not reported by lshw to have anything like a bluetooth capability...

By the way, my wireless (802.11b/g that is) has worked fine from the start, although the LED never comes on.

If you manage to fix this, please post.

Thanks,
Jasper.

---

### Post by meistercobbman on 2009-01-02
someone please help here... I also have a Lenovo R61 and can't get bluetooth to work. I have very similar outputs to the first post. 

Though bluetooth works just fine on my XP partition. I'd rather not have to reboot into XP just to use bluetooth. 

fyi, i'm using Linux Mint v5 (Ubuntu 8.04 equiv) 64 bit.

thanks!

---

### Post by meistercobbman on 2009-01-02
I GOT IT TO WORK! 

Here's what I had to do:

I had to reboot into Windows XP, and using the Lenovo Thinkpad Utilities (free download from their drivers web site) I turned on the Blue tooth connection... which had to be "enabled" in the Hardware Profiled dialog (apparently it was turned off somehow, though I remember it being on before). 

When I rebooted the Blue tooth indicator light stayed on, and it WORKED in Linux!

I know this is just a simple fix, but you should try it. Make sure you go to your hardware profiles in Windows and make sure the devices are "enabled" and not "disabled".

How to get to "Hardware Profiles"... right click on "My computer" go to properties, then check the Hardware tab, then click on "Device Manager" and look for your bluetooth device. If there are yellow quesion marks, try to reinstall the drivers for those items.

Or, for a more automated approach, download the Thinkpad utilities from lenovo's web site, and it will scan your hardware for you and tell you how to fix it.

---

