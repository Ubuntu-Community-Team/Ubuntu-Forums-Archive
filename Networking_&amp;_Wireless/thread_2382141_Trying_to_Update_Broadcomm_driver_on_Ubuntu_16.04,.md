---
title: "Trying to Update Broadcomm driver on Ubuntu 16.04, not responding"
date: 2018-01-09
forum: Networking &amp; Wireless
---

### Post by radhika1226 on 2018-01-09
First post from a Newbie. 

I converted an old DELL PC to install Ubuntu, just to practice using Linux. It loaded and installed updates except for Bluetooth connectivity. I know this is a big problem, all over Linux. "Adapter not found"  I searched various ways and think I found he model/chipset and downloaded the Install Kit for #43b using another machine. Back at the Dell, Linux was able to view the Install Kit (both DVD and USB versions) but never responded when I pressed the INSTALL BUTTON. I don't know enough about Linux yet on how to manually accomplish this. 

Any hints or code will be appreciated.

---

### Post by dagorret2 on 2018-01-09
Run [FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][COLOR=#111111]: [/COLOR][/FONT][B]sudo lshw -C network
[/B]
this command show you network hardware and you firmware.

If you do not have the installed drivers (firmware) try running the following command with cable connection: **sudo apt install firmware-b43-installer**

---

### Post by jeremy31 on 2018-01-09
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2018-01-09
> **dagorret2 said:**
> Run [FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][COLOR=#111111]: [/COLOR][/FONT][B]sudo lshw -C network
[/B]
this command show you network hardware and you firmware.

If you do not have the installed drivers (firmware) try running the following command with cable connection: **sudo apt install firmware-b43-installer**Does he have a Broadcom? Will this fix his bluetooth?

---

### Post by dagorret2 on 2018-01-09
Sorry i read bad. 

Check this for bluetooth: [https://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working](https://askubuntu.com/questions/632336/bluetooth-broadcom-43142-isnt-working)

---

### Post by chili555 on 2018-01-09
Let’s find out some specifics; please post the result of these terminal commands:```
lsusb
dmesg | grep -i blue
```

---

### Post by radhika1226 on 2018-01-11
Thanks everyone for fast response. I will get on this later today (prior commitments) and try to provide specifics as to results. Since the Ubuntu machine can't reach Internet or even the wireless printer, it means manually copying or entering command results into another machine. btw: Many of these were tried, but I'll walk through one more time.

---

### Post by radhika1226 on 2018-01-11
I do have this info. Too much to key in...

It's Broadcomm BCM4312. I believe I located the correct install kit, but it won't launch from DVD. Broadcomm is proprietary, so it needs to be installed.

---

### Post by radhika1226 on 2018-01-11
No results to dmseg

ls /lib/firmware shows a lot of wifi codes, however it clearly omits the one I need. Hence the install kit needed. 
    15.Ucode

i appreciate the responses, but will exit for a bit. 

I think I tried all the suggestions on other forum threads.

---

### Post by chili555 on 2018-01-11
Are you asking about bluetooth? Is Broadcom 4312 your bluetooth device? How about:```
lsusb
```We will have trouble guessing what to suggest for a fix with no details to go on.> ls /lib/firmware shows a lot of wifi codes, however it clearly omits the one I need. Hence the install kit needed. 
15.Ucode
Are you attempting to fix the wireless or the bluetooth? You said:> I converted an old DELL PC to install Ubuntu, just to practice using Linux. It loaded and installed updates [COLOR="#FF0000"]except for Bluetooth connectivity.[/COLOR] Old Chili is confused...

---

