---
title: "rt25xx: Linux fails where Windows succeeds"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by mogliii on 2008-04-21
Hi,

I have a desktop computer. Connected to it, I have a USB-Wireless-Dongle.
Buffalo WLI-U2-KG54-AI, it uses the rt2570.

On that computer I have windows installed.
In windows, even though the signal is not perfect, I can connect every time quickly. 

Now I tried the Ubuntu 8.4 Beta live-cd. The stick gets recognized and shows me three networks in my neighbourhood. 

For many tries, I could not connect to the network (it has WPA-TKIP security). I already gave up and thought that there is a driver problem. But for once, maybe 10 seconds, there was a connection, and I could load one webpage partially. Now I was trying for another 15 times without success.

This means, that the problem is not the driver, but the signal strength. But can anyone explain me, why the same stick, in the same location, can connect many times without problems on the windows.

So my question: Is there a option in some config file where I can redirect some more power to the stick? Or what is the matter?

Would appreaciate any hint very much.

---

### Post by mrsteveman1 on 2008-04-21
That is in fact a driver problem, the driver is the only thing different in that case.

I can never remember which chips are made by realtek and which are ralink, but they both suck at writing drivers apparently.

---

### Post by mogliii on 2008-04-21
So what should I do now?

I have a centrino notebook and wireless works well since 3 years.

Is there any stick I can buy that will work as the centrino in my notebook? I spent so much f*** time on trying to get this to work that I should just consider what is more valuable. More wasted hours or 30 Euro.

But even after looking for a long time, I could not find a 100% recommendation for a Linux-out-of-the-box, dont-worry-never-ever-again usb-dongle.

Any hints?

---

### Post by prshah on 2008-04-21
> **mogliii said:**
> So my question: Is there a option in some config file where I can redirect some more power to the stick? Or what is the matter?


```
sudo iwconfig wifi0 txpower fixed
``` will set and keep your wifi at full power. If you like, you can even specify a particular power if you know what it is:```

iwconfig wifi0 txpower 15
iwconfig wifi0 txpower 30mW

```

Since I dont know what max power your adapter has, the above values are examples (from the man pages).

Replace "wifi0" with the actual wireless adapter name, as reported by "iwconfig"

---

### Post by Saint Angeles on 2008-04-21
> **mogliii said:**
> Hi,

I have a desktop computer. Connected to it, I have a USB-Wireless-Dongle.
Buffalo WLI-U2-KG54-AI, it uses the rt2570.

On that computer I have windows installed.
In windows, even though the signal is not perfect, I can connect every time quickly. 

Now I tried the Ubuntu 8.4 Beta live-cd. The stick gets recognized and shows me three networks in my neighbourhood. 

For many tries, I could not connect to the network (it has WPA-TKIP security). I already gave up and thought that there is a driver problem. But for once, maybe 10 seconds, there was a connection, and I could load one webpage partially. Now I was trying for another 15 times without success.

This means, that the problem is not the driver, but the signal strength. But can anyone explain me, why the same stick, in the same location, can connect many times without problems on the windows.

So my question: Is there a option in some config file where I can redirect some more power to the stick? Or what is the matter?

Would appreaciate any hint very much.

wait... you are comparing a windows installation to a LIVE CD of linux?

windows doesn't even have anything close to a live CD so your title is flawed.

---

### Post by mrsteveman1 on 2008-04-21
The livecd part is irrelevant , the same kernel and userspace are running on the livecd that would be running on a true install.

Changing the TX power of the radio only helps get your frames to the access point, if your chip is dropping connections or frames increasing the power won't help unless the access point disassociated your client because the power was too low. If the chip is dropping frames in Linux but not Windows, its a driver issue.

Do try the power fix though, it MAY help or it may just tell you that power isn't an issue.

You might also consider just using ndiswrapper, since then you would be using the same driver as on windows.

---

### Post by mogliii on 2008-04-21
Tweaking the dongle with the iwconfig command did not help.

And I dont want to go to ndiswrapper, as I heard about many difficulties with it. My centrino works fine out of the box, so I expect my usb-dongle to do the same thing.

So I am still happy to get more suggestions on how to solve this, or tell me about a 

works-out-of-the-box-no-worry-ever-again usb-dongle and I will buy it and have peace of mind.

Thank you to everyone so far!

---

### Post by mrsteveman1 on 2008-04-21
I have a belkin stick with a zydas chipset that works perfectly out of the box.

Its an F5D7050 version 3, the other versions have different chips.

Zydas is pretty well supported, it started as a vendor gpl driver and was improved and rewritten by the kernel developers. The firmware is also included on the ubuntu cd and is free to distribute, though its just a set of hex registers i think, its not actually complex code.

One thing to stay away from are atheros usb sticks, they aren't supported natively by any driver, even madwifi.

Its difficult to tell what chip will be in a stick before buying, my advice would be to buy a few from a few manufacturers, check the chip, and return the ones that don't work with your operating system, which in my view is perfectly reasonable.

---

### Post by mogliii on 2008-04-21
Hi,

does your Belkin look like this?

[http://www.conrad.de/goto.php?artikel=973485]("http://www.conrad.de/goto.php?artikel=973485")


Then I will try it.

In germany we can return for 2 weeks when mail ordered.

Regards

---

### Post by mrsteveman1 on 2008-04-21
They have updated the stick since then, its a realtek chip now i believe.

There are other zydas chipset USB sticks available im sure, I don't however know which models are which.

You should just buy a few sticks, check whats in them, and return the ones you can't use.

---

### Post by mogliii on 2008-04-22
I ordered one now that is told to have a zydas chip (1211b) and I read about somebody who could use it out of the box with ubuntu 7.10. (MSI US54SE)

Guess I will get it in three days and report about it.

Thank you so far.

---

### Post by mogliii on 2008-04-26
Hi,

two things:
I borrowed yesterday a router from a friend and placed it directly next to my computer. Still I could not connect with my Buffalo stick. This means it has to be the stick. But as it works well in windows it has to be the linux driver.

Secondly: I have my new stick. Its an MSI US54SE II (picture below).
I had read somewhere else that it uses a Zydas chip.

I started with the live-cd of ubuntu 8.04 final and I could connect to the network. So the stick works.

However, when I run lsusb, it shows me that it is a ralink (see below). How can I exactly find out which chip is inside without opening it? 
Still it works out of box. So I am very happy!

[[IMG]http://img137.imageshack.us/img137/6017/msius54seiinq7.th.jpg[/IMG]](http://img137.imageshack.us/my.php?image=msius54seiinq7.jpg)

[[IMG]http://img182.imageshack.us/img182/2264/sidepe9.th.jpg[/IMG]](http://img182.imageshack.us/my.php?image=sidepe9.jpg)

```
Bus 006 Device 004: ID 148f:2573 Ralink Technology, Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x2573 
  bcdDevice            0.01
  iManufacturer           1 Ralink
  iProduct                2 54M.USB.......
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

---

### Post by mrsteveman1 on 2008-04-26
Its a ralink RT73, otherwise known as 2573 i suppose :D

If it works, good, keep it. Test it out a bit though first.

---

