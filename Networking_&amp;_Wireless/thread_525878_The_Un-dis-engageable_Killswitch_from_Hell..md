---
title: "The Un-dis-engageable Killswitch from Hell."
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by pKp on 2007-08-14
Hello,
I'm trying to get wifi to work on my Asus A7J. The chipset is the infamous intel Pro Wireless 3945, using the ipw3945 module from the restricted-modules package.
I think I have the problem narrowed down, but I'm stuck.
dmesg messages gives me that :```

ipw3945 : Radio Frequency Kill Switch is On:
Kill Switch must be turned off for wireless networking to work.
```
The problem is, that switch IS turned off :confused:
There is two ways to des/activate this switch : a hard switch placed on the machine's side, and the Fn+F2 combination. I have tried both, before and after boot, to no effect.
The card is perfectly recognised on my Dapper livecd.
Can someone help me out on this ?
Thanks a lot
pKp

---

### Post by noob12 on 2007-08-14
First make sure the wireless is enabled in the BIOS, and if there is such a setting in yours, also under "application" control.

Also make sure the wireless switch is in the ON position.  Bad nomenclature.  Wireless ON = RF kill switch OFF.

Is the module **asus_acpi** loaded?  Let's see
```

lsmod | grep asus_acpi

```

If you see nothing then run this 
```

sudo modprobe asus_acpi

```

Check if it loaded
```

lsmod | grep asus_acpi
dmesg | tail -50

```

Then see if 
```

ls /proc/acpi/asus/wled

```
exists.

If it does then try this
```

echo 1 | sudo tee /proc/acpi/asus/wled

```

---

### Post by pKp on 2007-08-14
Already checked the BIOS, no such setting.
I've loaded the asus_acpi module, done as you suggested (las command suggested sends "1" as a result). Still nothing, dmesg is the same, still no wireless device detected via iwconfig.

---

### Post by noob12 on 2007-08-14
Oh.  No wireless device at all is probably a different problem from just the kill-switch.  Can you post the output of these:
```

lspci -nn

sudo lshw -C network

dmesg

```

Send the whole dmesg if your device does not show up in both of the first two listings.

---

### Post by pKp on 2007-08-14
It's here !
lspci :
```
04:00.0 Network Controller (0280) : Intel Corporation PRO/Wireless 3945ABG Network Connection (8086:4222) (rev02)
```
lshw :
```
*-network
description : network controller
product : PRO/Wireless 3945ABG Network Connection
vendor : Intel Corporation
Physical id : 0
bus info : pci@04:00.0
version : 02
width : 32bits
clock : 33mhz
capabilities : bus_master cap_list
configuration : driver=ipw3945 latency = 0
resources : iomemory:fdeff000-fdefffff irq:17
```
(I"m on a different computer, so all this is hand-typed. I checked, but there may be mistakes).

---

### Post by noob12 on 2007-08-14
But not entirely.  Try this
```

sudo /etc/init.d/networking stop
sudo modprobe -r ipw3945
sudo modprobe ipw3945 led=1
sudo /etc/init.d/networking start

```

Probably won't work.  (Let me know if it does.) But then show me 
```

ifconfig -a

dmesg

```
No excerpts.

---

### Post by noob12 on 2007-08-14
Also, can you post the output of
```

cat /sys/bus/pci/drivers/ipw3945/*/rf_kill

```

---

### Post by noob12 on 2007-08-14
Eek.  Just noticed you said you are hand-typing.  Do you also have no wired network?  What about a jump-drive?

---

### Post by pKp on 2007-08-15
Any ideas ? :confused:

---

### Post by pKp on 2007-08-15
OK, when I woke up, the kill switch was disabled, the wifi led was on, but still no trace of eth1 in iwconfig.
The modprobe thing (I had already tried it) made the "killswitch on" message appear in dmesg. No changes in ifconfig.
cat /sys/bus/pci/drivers/ipw3945/*/rf_kill give "2".
EDIT : I've done it again : it's the "echo 1 | sudo tee /proc/acpi/asus/wled" bit that turns the led on. dmesg still shows the killswitch thing, however, even after a /etc/init.d/networking restart.

---

### Post by pKp on 2007-08-15
OK, this IS ****** up. It all works now :grin: so I'm not complaining, but still.
The "echo 1 | sudo tee /proc/acpi/asus/wled" was probably what made the thing work. It just...appeared. Hope it won't disappear.
Thanks muchly for your time && precious help, noob12.

---

### Post by noob12 on 2007-08-15
[COLOR="Red"]EDIT: This was posted before seeing posting #11[/COLOR]

Well, we want to understand why the driver isn't completing intialization.  Generally, having the kill switch on (radio disabled) won't cause this.  The interface will be there, but the radio will be disabled.  In your case the driver can't finish claiming the device and no interface shows up.

I'm not sure I can help you make more progress without more output, and I understand it's not really practical to hand-transcribe the output I'm asking for.  What's going to be critical is either plugging in wired so you can post from the affected computer or finding a flash drive you can use to transfer text files to whatever computer you are using to post the messages.  This will allow you to post the diagnostic output that's going to help resolve this.

I'm expecting the kill switch message will go away (on the tail of dmesg or /var/log/kern.log) if you do the following sequence.  But I'm really looking for other complaints from the driver ipw3945 or problems during the initial PCI bus assignment.  These should show up in dmesg, but I'd need to see the whole thing.

```

sudo /etc/init.d/networking stop
sudo modprobe -r ipw3945
sudo modprobe asus_acpi
echo "1" | sudo tee /proc/acpi/asus/wled
sudo modprobe ipw3945 led=1
sudo /etc/init.d/networking start

```

By the way, it would be useful to know whether you had to load asus_acpi or if it was already loaded (see my first message)

After doing the sequence above I would like to see the output of
```

cat /sys/bus/pci/drivers/ipw3945/*/rf_kill

cat /etc/iftab

sudo lshw -C network

ifconfig -a

dmesg

```

I'm expecting the first to show 0 indicating that the driver has recognized the kill switch is off.  I'm expecting the device to show up in **lshw -C network** with a logical name like **eth1** and the driver **ipw3945** associated to it.  I'm not sure if the additional interface will begin to show up or not in the **ifconfig -a**; if it does I'd like to know if the MAC is also in /etc/iftab.  For these you could possibly be the eyes.

From the **dmesg** I am looking for any errors earlier or as a result of this last sequence; these may be errors reported by ipw3945 or issues in the PCI assignments by ACPI.  Unless the earlier stuff just starts working, I'm don't see how to avoid looking at the full dmesg.

---

### Post by noob12 on 2007-08-15
OK.  I posted the last message before seeing your success.  I'm not sure what you did then.
If you have more trouble, drop me a PM because I'll stop watching this thread.

If you need to put the command to turn on the wireless led in your startup, it's possible to do that.

---

### Post by pKp on 2007-08-15
Yeah, I know, I'll do that. Thanks again for your time.

---

### Post by Guillaume2x on 2007-08-18
In my case (A6J + Debian sid), doing :
```
rm -rf /etc/acpi/start.d/
```
solved everything.

If you want to do this a more subtle way, then try to disable  the 60-asus-wireless-led.sh script, inside the  /etc/acpi/start.d directory. You can do this by deleting it, or adding "exit 0" at the top. 

You might also try :
```
chmod -x /etc/acpi/start.d/60-asus-wireless-led.sh
```, but it did not work for me.

---

