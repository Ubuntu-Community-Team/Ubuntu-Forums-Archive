---
title: "dial up connection"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by fas143 on 2008-12-26
hi all,
       how i can configure settings to connect dialup to my laptop in ubuntu 8.10

---

### Post by balaknair on 2008-12-26
Dial up is always tricky in Linux on Laptops since most laptops have software modems(softmodems or winmodems), so if you have a software modem, you might be better off with either a seperate hardware modem or an alternate internet connection method that uses the ethernet port(such as cable or DSL broadband, or WiFi).

Though things have improved in terms of support for softmodems somewhat with Ubuntu 8.10, it's still not ideal.

For some basic tips on configuring and troubleshooting dialup modems in Ubuntu
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

To see if your modem is supported in Linux, you need to know what make/model your modem is.

[B]a) In Ubuntu
[/B]
Open a terminal(Applications menu> Accessories> Terminal) and type in
 
```
*wvdialconf*
```

This will help you see whether Ubuntu can detect your modem.
 
If Ubuntu can detect your modem here, it is relatively straightforward to configure it and get it working Networkadmin or with GnomePPP(follow instructions in [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) )

If not, you could use a tool like [scanmodem]("http://132.68.73.235/linmodems/index.html#scanModem") to detect and identify your modem.
Download the [scanmodem.gz file]("http://132.68.73.235/linmodems/packages/scanModem.gz") and save it to your desktop.
Then open a terminal, and enter the following commands one by one.
 ```
  cd ~/Desktop
 gunzip scanModem.gz
 sudo chmod +x scanModem
 ./scanModem
 gedit Modem/ModemData.txt
```

Then read through the ModemData.txt file that has now been opened to find what modem scanmodem has found on your laptop.


**b) In Windows**

Control panel> System management> Devices> Modems--> right click on the modem entry and select properties--> Check for manufacturer and model version information.

Once you know what modem you have, check here to see if it is compatible with Linux.
[http://xmodem.org/modems/index.html](http://xmodem.org/modems/index.html)

---

### Post by lkraemer on 2008-12-26
If you try to enable and use the internal modem you will probably
spend more time attempting to make it work than you realize, but
you can always fall back on an External USR Modem.

May I suggest:
The Softmodems and Internal modems can be a bugger, so why not
look on Ebay for an External USRobotics USR5686D, then Flash it to
the latest firmware, and use a USB to Serial Converter to get
online via Dialup using wvdial. Granted it's extra equipment, more cables,
Wall Wart, and Serial Cable but it at least works Great. Ebay has
them for ~$20.00 at times.

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $8.99.

These work wonderful with wvdial, etc.

you will need to do a 
sudo wvdialconf
the config file will be at /etc/wvdial.conf
to configure your ISP's telephone number, login & password etc.

You can later edit your personal information with:
$ sudo gedit /etc/wvdial.conf
and dial out with:
$ wvdial
in a terminal window.....just leave that terminal window open for
the time you are connected.  You can go back to the open window
and do a CNTRL C to terminate the connection.  I think you will
be surprized by the speed if you migrated from XP w/Dialup.

lk

---

### Post by ieee488 on 2008-12-26
If your laptop has a PCMCIA slot, not Express Card slot, I'd buy a used Linux-compatible modem on eBay. They're cheap because no one wants one. I bought two 3Com cards back in the days when I was on dial-up.

---

