---
title: "ehci_hcd module conflict with ndiswrapper"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by ikg74 on 2007-03-12
Hello everyone,

I'm encountering an annoying problem with the wireless network on the laptop I'm using.

The wireless usb adapter is setup correctly using ndiswrapper and the relevant Windows drivers but when I restart the laptop with the adapter plugged into the usb 2.0 port, the startup process hangs.

The only way I can boot ubuntu 5.10 is by keeping the usb port empty and then in order to use the wireless usb adapter I first have to remove the ehci_hcd module with the rmmod command before I insert the wireless usb adapter.

I have tried several methods to prevent the ehci_hcd module from being activated during the boot process but none have been successfull.

I'd like to know what is the correct way to do this so that I don't have the conflict when I boot the laptop with the wireless usb adapter in place.

Thanks in advance for any help you provide.

Regards,

ikg74

---

### Post by dmizer on 2007-03-13
add the line:
ehci_hcd

to the end of /etc/hotplug/blacklist

if the file does not exist (i seem to vaguely recall needing to create this file for some reason), you can create it by doing the following:
```
sudo touch /etc/hotplug/blacklist
```
and then add the above single line to the file.

more information: [http://doc.gwos.org/index.php/Get_rid_of_useless_modules_loaded_at_boot](http://doc.gwos.org/index.php/Get_rid_of_useless_modules_loaded_at_boot)

---

### Post by ikg74 on 2007-03-13
Thanks dmizer,

The blacklist file is already there and I added the ehci_hcd entry.

I had tried editing the same file in my previous attempts but wasn't doing it properly. This time it works well and I disabled a couple of other hotplug modules I don't require to start on boot as well O:)

Thanks for the help O:)

---

