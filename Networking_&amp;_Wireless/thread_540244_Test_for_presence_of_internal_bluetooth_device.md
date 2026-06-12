---
title: "Test for presence of internal bluetooth device?"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2007-09-01
I've got a Dell D620, and I'm not sure if it's got a built-in Bluetooth device. How do I check?

Is this sufficient? (If so, I don't have one, I guess.)
sudo lshw | grep blue

---

### Post by Jamie Jackson on 2007-09-02
bump

---

### Post by noob12 on 2007-09-02
It should show up in listings if it is being detected at all, regardless of whether there is a driver claiming it.

```

lspci -nn

sudo lshw

```

---

### Post by Jamie Jackson on 2007-09-02
I see no mention of Bluetooth in either of those commands' output. I guess I've got no Bluetooth device.

---

### Post by noob12 on 2007-09-02
It might be a USB device off an onboard USB.  Check **lsusb** as well.

I think you'll probably have the Dell 350.   I think its ids are 413C:8103 if you have it.

---

### Post by Jamie Jackson on 2007-09-02
Nope, it's not showing up there either. Thanks for helping me check.

---

### Post by Jamie Jackson on 2007-09-02
I'm looking at buying the internal Dell 350--the one you mentioned. How well does it play with Feisty Fawn? Anything I should know?

---

### Post by noob12 on 2007-09-02
Sorry.  I don't have any direct experience with that.  I do actually use a D620 (among other laptops), but mine has no bluetooth.  Perhaps other readers can pitch in?  Also you might search around.

---

### Post by marvinrichards on 2007-10-04
I would go to the terminal and type   lshw.  I think this would list everything on the motherboard.

---

### Post by Jamie Jackson on 2007-10-04
> **marvinrichards said:**
> I would go to the terminal and type   lshw.  I think this would list everything on the motherboard.

I could tell from my hardware profile at the Dell site, that I didn't have the bluetooth device. I did buy a refurbished one for around $12. It's in now, and lshw does report it:

                 *-usb:1
                      description: Bluetooth wireless interface
                      physical id: 4
                      bus info: usb@1:2.4
                      version: 24.22
                      capabilities: bluetooth usb-2.00
                      configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s

Thanks,
Jamie

---

