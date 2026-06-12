---
title: "Hardy32 &amp; Option GlobeSurfer iCON USB Modem (GPRS/UMTS networks)"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by rautamiekka on 2008-05-01
Got this modem, [http://www.option.com/products/globesurfer_icon.shtml](http://www.option.com/products/globesurfer_icon.shtml), and Hardy32. Can't find any (clear) instructions to install that box. If you have 'em reply here without any needless writings, please.

---

### Post by Shai Hulud on 2008-07-09
I double this request :)

---

### Post by kestas.j on 2008-11-13
Hello there,

Hope attached file will help you. I had opened a thread long time ago and figured out how to fix it my self. After several Ubuntu updates I have automated this process. The only thing needed is to run this script and configure the connection parameters afterwords.

It seams intrepid recognizes the Icon but the thing is that it does not switch it from mass storage to modem mode. That's where little handy icon_switch by Frederick Reid comes in power.

Intrepid have also implemented the GSM modem handling via network manager applet so it became even easier to configure connection after installing the script.

Chears,
Kestas J.

---

### Post by rautamiekka on 2008-11-27
Configure connection parameters ? Simple instructions, please ;)

---

### Post by Bolle1961 on 2008-11-29
> **kestas.j said:**
> Hello there,

Hope attached file will help you. I had opened a thread long time ago and figured out how to fix it my self. After several Ubuntu updates I have automated this process. The only thing needed is to run this script and configure the connection parameters afterwords.

It seams intrepid recognizes the Icon but the thing is that it does not switch it from mass storage to modem mode. That's where little handy icon_switch by Frederick Reid comes in power.

Intrepid have also implemented the GSM modem handling via network manager applet so it became even easier to configure connection after installing the script.

Chears,
Kestas J.

I have a question about the script

do I need to fill in the vendor and product ID which I get with lsusb in the last line of the script? or leave the script that way?

I'm trying to help someone by e-mail to getr his Globesurfer working but now I'm a bit stuck

thanks in advance Arie

---

### Post by kestas.j on 2008-12-04
> **rautamiekka said:**
> Configure connection parameters ? Simple instructions, please ;)

Hi there,

First of all [this]("http://www.option.com/products/globesurfer_icon_72.shtml") is the Icon I am using. If the modem you are trying to connect looks different you might need to change item ID in the script.

After installation the Icon should be automaticly switched to modem mode when connected. That you can prove by listing connected USB devices:
>  lsusb | grep Option
You should get something like:
> Bus 001 Device 005: ID 0af0:6901 Option
If so, you just need to configure the connection. 

8.10. When Icon is connected to PC Intrepid network managers applet informes about detection of new mobile broadband adapter and suggests to configure it. That is done by choosing the service supplier and writing the name for connection. After you have finished with that the only thing left is to left click on network managers icon and choosing the connection you've just created.

8.04 and earlier. That was little bit more complicated. That is done via network managers modem connection section. Actual dial-up configuration is depending on service supplier (I found it at suppliers webpage) but I will state mine:
> Dial-up number: *99#
Prefix:
User name: omni
Password: omni

It is necessary to specify the modem in the second table. It is not found in drop-down list so you should manually write it:
> Modem: /dev/ttyUSB0

In the third table all 3 check-boxes can be checked. After exiting the network manager PC must be restarted. The connection is established by left-clicking the network managers icon, going to dial-up and choosing connect from menu.

Regards,
Kestas J.

---

