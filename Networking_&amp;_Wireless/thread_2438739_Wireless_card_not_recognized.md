---
title: "Wireless card not recognized"
date: 2020-03-17
forum: Networking &amp; Wireless
---

### Post by totobonemaine on 2020-03-17
Hi everyone,

I tried installing different versions of Ubuntu (18.04 LTS and 19.10, the latter being the one I have currently) with dual boot. While my WiFi works fine with Windows, I can't get my card recognized with Ubuntu. Internet works fine when I use ethernet.
My computer is the Lenovo Ideapad 130s ( [https://www.bestbuy.com/site/lenovo-ideapad-130s-11-6-laptop-intel-celeron-4gb-memory-64gb-emmc-flash-memory-mineral-gray/6331986.p?skuId=6331986&intl=nosplash](https://www.bestbuy.com/site/lenovo-ideapad-130s-11-6-laptop-intel-celeron-4gb-memory-64gb-emmc-flash-memory-mineral-gray/6331986.p?skuId=6331986&intl=nosplash) )
What can I do to fix it?

Thank you so much
Toto

---

### Post by chili555 on 2020-03-17
Please open a terminal and run and post:

```
lspci -nnk | grep 0280 -A3
rfkill list all
```Thanks.

---

### Post by totobonemaine on 2020-03-19
Hi,

The first command outputs:
```
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
    Subsystem: Lenovo RTL8821CE 802.11ac PCIe Wireless Network Adapter [17aa:c024]
```

The second one:
```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Thank you for your help

---

### Post by chili555 on 2020-03-19
With a working internet connection, open a terminal and do:

```
sudo apt update
sudo apt install rtl8821ce-dkms
```Turn off Secure Boot in the EFI/BIOS, reboot and you should be all set.

---

### Post by totobonemaine on 2020-03-19
Hi!

Thank you so much, it worked!

---

### Post by dengineer on 2020-03-19
It would help those of us dealing with similar and not identical issues if the above fix was explained in more general terms. e.g. what does ... install trl8821ce-dkms  actually do and how might that apply with a different wireless device?

---

### Post by chili555 on 2020-03-19
> **dengineer said:**
> It would help those of us dealing with similar and not identical issues if the above fix was explained in more general terms. e.g. what does ... install trl8821ce-dkms  actually do and how might that apply with a different wireless device?The package rtl8821ce-dkms is the driver that covers his exact device and a few similar devices:> 
 Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [[COLOR="#FF0000"]**10ec:c821**[/COLOR]]
    Subsystem: Lenovo RTL8821CE 802.11ac PCIe Wireless Network Adapter [17aa:c024]
That is the reason that, before we even started, I wanted to know the exact identity of his device. Once I knew it from his reply, I knew, from lots of experience, what the appropriate driver was and I proposed the solution. As you see, it worked.

If I didn't know this by experience, I could have Googled the pci.id, in this case 10ec:c821 and found that the driver is rtl8188ce and that there is a package in the Ubuntu repos to cover it. Here, as an example: [https://askubuntu.com/questions/1071299/how-to-install-wi-fi-driver-for-realtek-rtl8821ce-on-ubuntu-18-04](https://askubuntu.com/questions/1071299/how-to-install-wi-fi-driver-for-realtek-rtl8821ce-on-ubuntu-18-04) 

Your question gives me the opportunity to rant!

I have seen hundreds of posts over the years that say, essentially, "My wireless doesn't work and I installed rtl8821ce and it still doesn't work. Help!!!" When we ask for details of the wireless card as I did above, it turns out that the wireless card isn't even a Realtek (!!!), it is, rather, an Intel. Obviously, a Realtek driver won't help an Intel at all.

Until you know the exact identity of your wireless card, it is *useless* to blindly install a driver or two or three. Before you proceed, open a terminal and run, if it is an internal card:```
lspci -nnk | grep 0280
```And if it is a USB:```
lsusb
```Then search this forum for the pci.id or usb.id. The chances are nearly 100% that someone has the same card and the solution is in their thread. If you are still stuck, post a new thread and our team of volunteers will be happy to help.

---

