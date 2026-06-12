---
title: "Gammu SMS strange problem"
date: 2015-06-30
forum: Networking &amp; Wireless
---

### Post by raimonds2 on 2015-06-30
Good day, 

I am having a really strange problem with my Huawei E353 modem. Mostly the SMS that I send work, and they work without problems. Why did I wrote mostly? 
Because every second one just drops the message:

 No response in specified timeout. Probably phone not connected.

Tue 2015/06/30 07:16:47: [Gammu            - 1.33.0 built 09:23:21 Jul 25 2013 using GCC 4.8]
Tue 2015/06/30 07:16:47: [Connection       - "at19200"]
Tue 2015/06/30 07:16:47: [Connection index - 0]
Tue 2015/06/30 07:16:47: [Model type       - ""]
Tue 2015/06/30 07:16:47: [Device           - "/dev/ttyUSB0"]
Tue 2015/06/30 07:16:47: [Running on       - Linux, kernel 3.16.0-4-amd64 (#1 SMP Debian 3.16.7-ckt11-1 (2015-05-24))]
Tue 2015/06/30 07:16:47: Serial device: DTR is up, RTS is up, CAR is down, CTS is up
Tue 2015/06/30 07:16:47: Setting speed to 19200
Tue 2015/06/30 07:16:47: [Module           - "auto"]
Tue 2015/06/30 07:16:47: Escaping SMS mode
Tue 2015/06/30 07:16:48: Sending simple AT command to wake up some devices
Tue 2015/06/30 07:16:50: Enabling echo
Tue 2015/06/30 07:16:53: Phone does not support enabled echo, it can not work with Gammu!
Tue 2015/06/30 07:16:53: Init:GSM_TryGetModel failed with error TIMEOUT[14]: No response in specified timeout. Probably phone not connected.
Tue 2015/06/30 07:16:53: [Terminating]
Tue 2015/06/30 07:16:53: [Closing]



But only for every second SMS.
After a while it's after every third and than it just drops the connection altogeather.

Why is this so?
I really dont have a clue, because it works, and than after while doesn't work.

---

### Post by raimonds2 on 2015-06-30
Found another problem, after like 3 - 4 hours the virtualbox machine simply hangs up.

---

### Post by matt_symes on 2015-06-30
Hi

This is an absolute stab in the dark but is power saving set on the USB modem ?

Have you tried turning it off if it is ?

Kind regards

---

### Post by raimonds2 on 2015-07-01
I am sorry for the question but how do I actually do that?

---

### Post by Bucky Ball on 2015-07-01
Confused. What is the support request about? Do you want help with the virtual box crashing or SMS stuff? Are you actually using Ubuntu? You give no details whatever, only details about SMS messages and a modem, neither of which, from what I can see, has a lot to do with Ubuntu from the information you've given here. Apart from that, your vitual machine hangs after 3-4 hours. Not enough to go on.

Please elaborate on what exactly you want help with. If there are two separate issues, please post separate threads for each, not both on the same support thread. Thanks.

---

### Post by raimonds2 on 2015-07-01
Obviously I am using ubuntu why would I be posting here otherwise???!?

I will just copy the problem, because I expressed myself clearly:

[COLOR=#daa520]Mostly the SMS that I send work, and they work without problems. Why did I wrote mostly? 

Because every second one just drops.[/COLOR][COLOR=#000000]

[/COLOR]So is the problem really not clear enough for you? Every second SMS just hangs up and shows the error message I posted in my first post. After 3 - 4 hours when I try resetting usb-modeswitch the virtualmachine just hangs up.

That is why I wrote "strange" I have no idea why this is happening and I need help with it. It's partially working. And obviously it is the same issue which is causing these problems.

---

### Post by matt_symes on 2015-07-01
Hi

> **Bucky Ball said:**
> Confused. What is the support request about? Do you want help with the virtual box crashing or SMS stuff? Are you actually using Ubuntu? You give no details whatever, only details about SMS messages and a modem, neither of which, from what I can see, has a lot to do with Ubuntu from the information you've given here. Apart from that, your vitual machine hangs after 3-4 hours. Not enough to go on.

Please elaborate on what exactly you want help with. If there are two separate issues, please post separate threads for each, not both on the same support thread. Thanks.

Agreed. 

If you are having a problem with Virtual Box as well then please raise another thread. 

The reason is that we can move that thread, if required, into a more applicable forum than 'networking and wireless' where others will be able to look at it and, hopefully, give you better help. 

It's also not good practice to create a thread with more than one help request.

Anyway, assuming you still are having problems with your modem device....

To disable power saving you have to tell the OS not to suspend the HUB the device is connected to and, also, maybe the device itself.

Something along the lines of this will disable auto-suspend on the hub, where X is the number of the HUB your device is connected to.

```
echo on | sudo tee /sys/bus/usb/devices/usbX/power/level
```

However, you are using the USB device inside Virtual Box so you may have to disable auto suspend on  the host and in the guest device. I really not sure though as i have not tried disabling any USB hub power management in a VM before.

Anyway, plug the USB modem into the port you intend to use, open terminals on both the host and the guest and post the results of this command from both.

```
lsusb -t
```

Remember that this is still a guess at the moment but worth a try i think.

Kind regards

---

### Post by raimonds2 on 2015-07-01
It says On for power.

The output from lsusb -t

/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/8p, 12M
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/8p, 480M
    |__ Port 1: Dev 3, If 0, Class=Vendor Specific Class, Driver=option, 480M
    |__ Port 1: Dev 3, If 1, Class=Vendor Specific Class, Driver=huawei_cdc_ncm, 480M
    |__ Port 1: Dev 3, If 2, Class=Vendor Specific Class, Driver=option, 480M
    |__ Port 1: Dev 3, If 3, Class=Vendor Specific Class, Driver=option, 480M
    |__ Port 1: Dev 3, If 4, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 1: Dev 3, If 5, Class=Mass Storage, Driver=usb-storage, 480M

I meantioned the Virtualbox crashing because it is most certainly connected with this issue. But I will keep the tip in my mind for my next posts, thanks for pointing that out.

I will give anything a try I have spent a lot of time trying to solve this.

---

### Post by matt_symes on 2015-07-01
Hi

> **raimonds2 said:**
> It says On for power.

The output from lsusb -t

/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/8p, 12M
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/8p, 480M
    |__ Port 1: Dev 3, If 0, Class=Vendor Specific Class, Driver=option, 480M
    |__ Port 1: Dev 3, If 1, Class=Vendor Specific Class, Driver=huawei_cdc_ncm, 480M
    |__ Port 1: Dev 3, If 2, Class=Vendor Specific Class, Driver=option, 480M
    |__ Port 1: Dev 3, If 3, Class=Vendor Specific Class, Driver=option, 480M
    |__ Port 1: Dev 3, If 4, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 1: Dev 3, If 5, Class=Mass Storage, Driver=usb-storage, 480M

I meantioned the Virtualbox crashing because it is most certainly connected with this issue. But I will keep the tip in my mind for my next posts, thanks for pointing that out.

I will give anything a try I have spent a lot of time trying to solve this.

I assume the above output nis from the host OS and not the guest in Virtual Box ?

Can you post the output of these commands from the host OS.

```
cat /sys/bus/usb/devices/usb1/{product,power/{level,autosuspend}}
```

and 

```
cat /sys/bus/usb/devices/usb1/1-*/{product,power/level,autosuspend}
```

Kind regards

---

### Post by raimonds2 on 2015-07-01
I am doing everything from Guest OS. The Host OS sadly is Windows :/.
All it has is the Virtualbox USB driver. After that the device shows up in Virtualbox guest OS.

From the first command:

EHCI Host Controller
on
0

From second

HUAWEI Mobile
on


I don't know if you will be much help with this since it's Windows but this is the output for energy options.

Current energy condition:
D0


Energy options:
00000019
PDCAP_D0_SUPPORTED
PDCAP_D3_SUPPORTED
PDCAP_WAKE_FROM_D0_SUPPORTED


Energy condition:
S0 -> D0
S1 -> D2
S2 -> D2
S3 -> D2
S4 -> D2
S5 -> D3

---

### Post by matt_symes on 2015-07-01
Hi

> **raimonds2 said:**
> I am doing everything from Guest OS. The Host OS sadly is Windows :/.
All it has is the Virtualbox USB driver. After that the device shows up in Virtualbox guest OS.

From the first command:

EHCI Host Controller
on
0

From second

HUAWEI Mobile
on


I don't know if you will be much help with this since it's Windows but this is the output for energy options.

Current energy condition:
D0


Energy options:
00000019
PDCAP_D0_SUPPORTED
PDCAP_D3_SUPPORTED
PDCAP_WAKE_FROM_D0_SUPPORTED


Energy condition:
S0 -> D0
S1 -> D2
S2 -> D2
S3 -> D2
S4 -> D2
S5 -> D3

That's fine for the guest.

I would try disabling USB power saving on the host Windows machine.

Here are some links to get you started. I would disable USB device suspend on every USB device and hub while trouble shooting.

[http://answers.microsoft.com/en-us/windows/forum/windows_vista-hardware/what-does-usb-selective-suspend-mean/71fa747b-914f-4d17-b476-cf4bb1bb783c?auth=1](http://answers.microsoft.com/en-us/windows/forum/windows_vista-hardware/what-does-usb-selective-suspend-mean/71fa747b-914f-4d17-b476-cf4bb1bb783c?auth=1)

[http://www.sevenforums.com/tutorials/147369-usb-selective-suspend-turn-off.html](http://www.sevenforums.com/tutorials/147369-usb-selective-suspend-turn-off.html)

[http://answers.microsoft.com/en-us/windows/forum/windows_vista-hardware/how-do-i-permanently-disable-usb-selective-suspend/a7f2c720-e191-4918-939d-5a101b559a29](http://answers.microsoft.com/en-us/windows/forum/windows_vista-hardware/how-do-i-permanently-disable-usb-selective-suspend/a7f2c720-e191-4918-939d-5a101b559a29)

If we are barking up the wrong tree here, i'll scratch my head and see what else i can think of.

BTW: What version of Windows ?

Kind regards

---

### Post by matt_symes on 2015-07-16
Hi

Did you find a solution to this problem ?

Kind regards

---

