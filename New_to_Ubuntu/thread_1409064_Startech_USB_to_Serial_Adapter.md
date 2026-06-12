---
title: "Startech USB to Serial Adapter"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by ak07 on 2010-02-17
Hello,

I'm hoping someone could explain this strange issue i'm having with Startech USB to Serial adapters.

I have been using a 1 port USB serial adapter ([http://www.startech.com/item/ICUSB2321X-Professional-USB-to-RS-232-Serial-Adapter.aspx](http://www.startech.com/item/ICUSB2321X-Professional-USB-to-RS-232-Serial-Adapter.aspx)) no problem i plug in and the adapter is immediately picked up and i can confirm this by issuing the command

dmesg | grep tty

I get the message - converter now attached to ttyUSB0

but

when i use the 4 port adapter ([http://www.startech.com/item/ICUSB2324X-Professional-4-Port-USB-to-RS-232-Serial-Adapter.aspx](http://www.startech.com/item/ICUSB2324X-Professional-4-Port-USB-to-RS-232-Serial-Adapter.aspx)) and run the same command dmesg | grep tty the ports are not picked up automatically

I have found an article [http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html](http://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html) that enables the ports to work.

What I don't understand is why does one adapter work as soon as it's plugged it and the other doesn't

To  load this module automatically i need to add a line /etc/modules file.

Any help in understanding this issue would be appreciated.

I'm running 9.10 64bit

---

### Post by GeorgeVita on 2010-02-17
Hi **ak07**, welcome to this forum!

Not all USB peripherals are 'compatible by default' to linux OS due to lack of technical info from manufacturers. In your case the simple USB to serial adapter is already defined but not the 4 port.

Check **lsusb** before and after attaching the 4-port peripheral to determine actual vendorID : productID and then try to create the ports manually (possibly already done): ```
sudo modprobe usbserial vendor=0x1234 product=0x5678
```
Check creation of ports from **dmesg** and ```
ls /dev/ttyU*
```

When succeeded add a udev rule to become automatic: ```
gksudo gedit /etc/udev/rules.d/90-4port.rules
```Copy into that file the following line **after replacing** 1234 with vendorID and 5678 with productID (from lsusb):
```
SYSFS{idVendor}=="1234", SYSFS{idProduct}=="5678", RUN+="/sbin/modprobe usbserial vendor=0x1234 product=0x5678", OPTIONS+="last_rule"
```

Regards,
George

---

### Post by ak07 on 2010-02-17
Hi George,

Many thanks for your explanation now I understand what is happening.

In regards to creating a udev rule I have added the relevant line inside the “/etc/modules” file.

Would your method be a better way of automating this process or is adding the relevant line into the modules file?

---

### Post by GeorgeVita on 2010-02-17
> **ak07 said:**
> ...Would your method be a better way of automating this process or is adding the relevant line into the modules file?
I really doNOT know as I am always a computing newbie!

Just remember to check the 'changes' in case a major update cancel them.

Regards,
George

---

### Post by ak07 on 2010-02-17
Once again many thanks George

AK

---

### Post by ak07 on 2010-02-22
with George's helpful post the usb serial adapter is now loading on startup - thanks George

but the usb adapter does not seems to be communicating with anything.

I think it is to do with the driver I have been trying a few things but at a dead end now.

As I mentioned in my first post the 1 port adapter works fine and loads on boot, I have noticed this uses a prolific driver.

The four port adapter is listed as using a generic driver in ubuntu when i run the command** ****dmesg**

I'm sure these devices use the same chip could i force the 4 port adapter to use the prolific driver in George's script, George maybe you could help me out with this one too.

Cheers
AK

---

### Post by GeorgeVita on 2010-02-23
Hi **ak07**, an idea is to try the following:

- boot with none USB 2 serial interface attached
- from terminal: **sudo dmesg -c**
(this will show and clear system activity till then)
- from terminal: **lsusb**
- attach the non working interface (4 port ?)
- **wait 20sec.**
- from terminal check **lsusb** and a simple **dmesg** (not '-c') to see vendorID and productID plus NEW system activity

As this is a different circuit, it must NOT have the same productID as the single converter. Check it.

If so, try 'sudo modprobe ...' using the new IDs.

Regards,
George

---

### Post by ak07 on 2010-02-23
Hey George thanks again - your advice is always helpful.

It turns out after a few days of trying to get the 4 port adapter to work that it is not supported in Linux, this straight from the manufacturer just my luck.

So even though the ports seemed to be assigned they weren't working, with my limited knowledge using ubuntu I presume the driver being assigned (which was referred to as generic) was not sufficient.

Thanks again
Regards

---

