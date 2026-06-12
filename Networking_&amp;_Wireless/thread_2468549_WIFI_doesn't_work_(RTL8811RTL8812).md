---
title: "WIFI doesn't work (RTL8811/RTL8812)"
date: 2021-11-02
forum: Networking &amp; Wireless
---

### Post by miklagard2 on 2021-11-02
I have one built-in and one USB dongle WIFI adaptors and they don't work.

```

lsusb

Bus 001 Device 003: ID 0bda:c820 Realtek Semiconductor Corp. 802.11ac NIC 
Bus 001 Device 005: ID 0bda:c811 Realtek Semiconductor Corp. 802.11ac NIC 

```

I have installed several drivers but none of them has worked yet:

```

sudo dkms status 

8812au, 4.2.3, 5.13.0-19-generic, x86_64: installed 
8821cu, 5.4.1, 5.13.0-19-generic, x86_64: installed 
88x2bu, 5.8.7.4, 5.13.0-19-generic, x86_64: installed 
backport-iwlwifi, 9340, 5.13.0-19-generic, x86_64: installed 

```


```

git clone https://github.com/morrownr/88x2bu.git 
sudo mv 88x2bu /usr/src/88x2bu-5.8.7.4
sudo dkms add -m 88x2bu -v 5.8.7.4 
sudo dkms build -m 88x2bu -v 5.8.7.4 
sudo dkms install -m 88x2bu -v 5.8.7.4 

```

I did the same process for the following drivers;

```

git clone [https://github.com/brektrou/rtl8821CU.git](https://github.com/brektrou/rtl8821CU.git) 
git clone [https://github.com/gnab/rtl8812au](https://github.com/gnab/rtl8812au)

``` 

So far, none of them has worked any of my WIFI devices.

Does anyone have any idea what is wrong? I have almost lost my hope :)

Notes:
Kernel: 5.13.0-19-generic
OS: Ubuntu 21.10

PS: A very similar tread here didn't solve my problem
[URL="https://askubuntu.com/questions/1162974/wireless-usb-adapter-0bdac811-realtek-semiconductor-corp"]https://askubuntu.com/questions/1162974/wireless-usb-adapter-0bdac811-realtek-semiconductor-corp


[/URL]

---

### Post by T6&amp;sfpER35% on 2021-11-02
i have a funny story that came to mind as i read this...
sold this laptop awhile back to some woman,everything on it worked 100s. 
few days later she phones me and complains she can't get the wifi to work ,her and her son has tried everything and nothing works and she want to give the laptop back to me ...
well long story short , i asked her did she flick the physical switch for wifi on the front of lappy  ,to ON??

it worked miraculously after that :P

probably not of any help for this thread , but one never knows lol

---

### Post by miklagard2 on 2021-11-02
:) Sadly, there is no any physical switch for this on this computer. Nothing on keyboard as well.

And sure, USB dongle doesn't have any switch either. Thank you anyway.

---

### Post by T6&amp;sfpER35% on 2021-11-02
is it a dual boot with windows system ? i'm just reaching here cause there's not any info
saw this thread, that's why i'm asking
[https://ubuntuforums.org/showthread.php?t=2468066]("https://ubuntuforums.org/showthread.php?t=2468066")

---

### Post by miklagard2 on 2021-11-02
No, just Ubuntu.

---

### Post by jeremy31 on 2021-11-02
What is the result from terminal for ```
mokutil --sb-state
```

Moved to Networking and Wireless

---

### Post by miklagard2 on 2021-11-02
This:

SecureBoot disabled 

Now I upgrade kernel 5.13.0-19 into 5.13.0-20

And probably it will not solve anything

---

### Post by jeremy31 on 2021-11-02
I think the backports-iwlwifi is causing issues so do
```
sudo dkms uninstall backport-iwlwifi/9340
sudo dkms remove backport-iwlwifi/9340 --all
```

Reboot and see is the USB wifi works

---

### Post by miklagard2 on 2021-11-03
That worked, now, two wifi devices are functioning. Thank you so much :)

The working driver is:

8821cu, 5.4.1, 5.13.0-19-generic, x86_64: installed

---

