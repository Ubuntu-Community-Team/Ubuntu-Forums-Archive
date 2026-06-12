---
title: "Good old huawei e173 modeswitch fail 14.04"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by mart-suga on 2014-05-15
My laptop: Acer aspire v3-772g with Ubuntu 14.04

I noticed there are a lot of threads about Huawei e173 but none of these solutions work for me.

Here is my case:

The only possible way to get it into modem mode is adding this line to /etc/modules:

```
usbserial vendor=0x12d1 product=0x1446
```

When i restart my laptop after this, it works correctly and lsusb output is this:

```
Bus 003 Device 006: ID 12d1:1436 Huawei Technologies Co., Ltd. E173 3G Modem (modem-mode)
```

but when i plug it after restart the lsusb will stay like that no matter what i try (wrong mode):

```
Bus 003 Device 006: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800/E173 (HSPA modem)
```

I have tried:

```
sudo usb_modeswitch -v 0x12d1 -p 0x1446 -M "55534243123456780000000000000011062000000100000000000000000000"
```

...and this...

```
sudo usb_modeswitch -v 12d1 -p 1446 -V 12d1 -P 1436
```

... and this ...

```
sudo modprobe usbserial vendor=0x12d1 product=0x1446
```

... also tried adding to /lib/udev/rules.d/40-usb_modeswitch.rules this line:

```
ATTR{idVendor}=="12d1", ATTR{idProduct}=="1446", RUN+="usb_modeswitch '%b/%k'"
```

... even created a new file called /etc/usb_modeswitch.d/12d1 and inserted into it:

```
######################################################## # Huawei E270+ (HSPA+ modem)


DefaultVendor= 0x12d1
DefaultProduct=0x1446
TargetVendor= 0x12d1
TargetProductList="1001,1406,140c,14ac,1436"
CheckSuccess=20 


MessageContent="55534243123456780000000000000011060000000000000000000000000000"
```

Just in case added a line into /etc/modprobe.d/usb-storage.conf:

```
options usb-storage delay_use=3
```

But absolutely none of this works. There is no difference of using usb2 or usb3 ports.
Any more ideas?

---

### Post by pdc on 2014-05-15
I can only say we have a ZTE modem that gets an occasional airing; I noticed that with the 3.11 kernel I had installed; it was not recognised; when I used an older one (3.3 I think); it was recognised well so I wonder if there is mischief there; I have seen various threads recently about modems not working; you could try a small partition for 12.04 that is an LTS ubuntu; supported till 2017; or perhaps just a live usb stick of it; see if it works better there

---

### Post by nadrach on 2014-05-16
Take a look at this thread from August 2013 (penultimate message):
 [http://ubuntuforums.org/showthread.php?t=2128479&page=2&highlight=E173](http://ubuntuforums.org/showthread.php?t=2128479&page=2&highlight=E173)

To paraphrase ... usb_modeswitch is making the wrong product ID change ...
> The problem is that usb_modeswitch switches the device from its default operation (product id 1446 which is a storage device) to the incorrect product id of 1436. In fact, it should change it to product id 140c, which is the correct product id for the modem.

The post then describes a file edit to change the configuration message sent by usb_modeswitch ... unfortunately none of the configuration files that the post specifies for 12.04 are present in 14.04.

---

### Post by abrutschy on 2014-08-14
I had the same problem. Got this to work with:

Created file /etc/usb_modeswitch.d/12d1 with content:
```
DefaultVendor= 0x12d1
DefaultProduct=0x1446


TargetVendor=  0x12d1
TargetProductList="1001,1406,140b,140c,1412,141b,1433,14ac,1446"


CheckSuccess=20


MessageContent="55534243123456780000000000000011062000000100000000000000000000"
```

For the record, I also changed some (probably inessential) things in /etc/usb_modeswitch.conf:
```

DisableSwitching=0
EnableLogging=1
SetStorageDelay=4
```

Lastly, note that my E173 worked only on a USB3 port - not sure if this is by accident.

---

### Post by ianni67 on 2015-03-03
Man thank you very much! you saved my day. It worked perfectly for me, Ubuntu 14.04 on a Dell XPS13 developer edition.

---

### Post by rag4 on 2015-08-09
Hi:

It didn't work for me. I followed the steps from [**[COLOR=#000000]abrutschy[/COLOR]**]("http://ubuntuforums.org/member.php?u=1939805") but not working.

Regards.

---

