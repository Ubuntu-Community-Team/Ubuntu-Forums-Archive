---
title: "Asus Eee 1008 Ha wireless lan driver"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by svenkre on 2009-07-29
I bought my new Asus 1008 Ha yesterday, and installed Ubuntu Netbook remix.

I'm not able to connect to wireless lan, and I'm not able to find driver for Asus Eee 1008 Ha anywhere. Can someone help me, or do I have to reinstall XP (I hope not)!

---

### Post by sbeam on 2009-07-30
to get the wired eth0 you need the new atheros driver atl1e, which has to be compiled. Then once you have that you can just install  linux-backports-modules-jaunty from the Unsupported Updates repository. There are a few errors compiling the atheros driver, but these can be ignored safely. 

using some computer that has network and a usb stick:
1. go to [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)
2. download [[459]AR813X-linux-v1.0.0.9.tar.gz]("http://partner.atheros.com/Download.aspx?id=93")
3. put that file on the USB stick and then plug that insto your Eee

then on the Eee
1. copy the driver tarball file to /tmp
2. cd /tmp; tar -xvzf \[459\]AR813X-linux-v1.0.0.9.tar.gz
    [ignore gzip errors]
    $ make
    $ sudo make install
    [ignore error about permissions]
3. $ sudo modprobe atl1e
4. You should now have a eth0 (ifconfig -a) - wired ethernet. Hook up a cable and get an IP addr.

get wlan0 up:
5.  go to Administration > Software Sources > Updates and check off "Unsupported Updates (jaunty-backports)", . 
6. $ sudo apt-get install linux-backports-modules-jaunty  
7. reboot

Once you reboot, you should have wireless showing up in the top status bar. 

Worked for me yesterday, so I hope this helps you. Credit to[ this Amazon reviewer ]("http://www.amazon.com/review/R1FY56FWYYXMFD")who was a super big help to me

---

