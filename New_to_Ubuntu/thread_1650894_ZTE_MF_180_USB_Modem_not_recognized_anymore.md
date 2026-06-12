---
title: "ZTE MF 180 USB Modem not recognized anymore"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by eiscafe on 2010-12-22
Hi!

I've been using all kinds of distros so far before settling with Ubuntu ~2 years ago. So while I'm not a complete beginner I never really advanced into Linux...

Recently I got myself a ZTE MF 180 USB modem and following the instructions here [http://blog.lynxworks.eu/2010/08/huawei-e1550-in-ubuntu-10-04-1/](http://blog.lynxworks.eu/2010/08/huawei-e1550-in-ubuntu-10-04-1/) I actually got it to work on my Thinkpad X61 running 10.04. 

Two days later after not having changed anything it suddenly doesn't work anymore. Using lsusb @ dmesg I identified three problems: 

1.) dmesq is stuck with 'usb-storage: waiting for device to settle before scanning' almost every time I plug in the modem.

2.) The Product ID of the modem keeps changing between 0177 and 2000 whenever I unplub and replug it.

3.) modem-modeswitch doesn't seem to do anything (when invoked manually)

any help is appreciated! 

greetings from the wintery Austria,
Martin


dmesg output:

```

[ 4028.336112] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 4028.472126] usb 1-3: configuration #1 chosen from 1 choice
[ 4028.474707] scsi11 : SCSI emulation for USB Mass Storage devices
[ 4028.475055] usb-storage: device found at 5
[ 4028.475060] usb-storage: waiting for device to settle before scanning

```

lsusb -v output for the modem:

```

Bus 001 Device 005: ID 19d2:2000 ONDA Communication S.p.A. ZTE MF627/MF628/MF628+ HSDPA
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x19d2 ONDA Communication S.p.A.
  idProduct          0x2000 ZTE MF627/MF628/MF628+ HSDPA
  bcdDevice            0.00
  iManufacturer           3 ZTE,Incorporated
  iProduct                2 ZTE WCDMA Technologies MSM
  iSerial                 4 MF1800ZTED010000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          1 ZTE Configuration
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
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

/etc/udec/rules.d/16-zte-mf-180.rules - file:

```

SUBSYSTEM=="usb" SYSFS{idProduct}=="2000" SYSFS{idVendor}=="19d2" RUN+="/lib/udev/modem-modeswitch --vendor 0x19d2 --product 0x2000 --type option-zerocd"

```

---

### Post by gandaran on 2010-12-22
hi,
have you tried deleting the existing network manager mobile broadband setup and run the setup wizard again?
if it did work before the it should work again or maybe theres some problem with the usb modem
I had a problem with my e1550 after installing a new kernel, it stopped working and took me two hours to fix, only when I tried the e1550 on windows and it did work (the original windows modem drivers must have done some kind of reseting) and started working again on ubuntu.
hope you get it sorted out.

---

### Post by eiscafe on 2010-12-22
thanks! gonna try this!

---

### Post by eiscafe on 2010-12-22
hm...keep being stuck with udev trying to "scan" the stick...

just started an update to 10.10. even though I can't see how that's going to help it's worth a try.

---

### Post by gandaran on 2010-12-22
> **eiscafe said:**
> hm...keep being stuck with udev trying to "scan" the stick...

just started an update to 10.10. even though I can't see how that's going to help it's worth a try.
maybe it can help, 10.10's 'usb-modeswitch' has better support for usb modem's.
if after setting up the network manager connection the modem doesn't connect strait away reboot the computer or better still shut down the computer and restart, some usb modems like mine huawei e1550 require to shut down the computer completely only then it starts working, I also have another huawei 169g this one works strait away after setting up the connection so you see some modems are better supported than others.

---

### Post by eiscafe on 2010-12-22
yeah, but is the "scanning problem" connected to modeswitch? I thought modeswitch only kicks in after the usb has been connected?

---

### Post by gandaran on 2010-12-22
> **eiscafe said:**
> yeah, but is the "scanning problem" connected to modeswitch? I thought modeswitch only kicks in after the usb has been connected?
well, I cant answer that, I just don't know!
but try doing it my way shutting down the computer (and remove the udev rule), I did not enter any udev rule for my e1550 and there isn't any ubuntu generated udev rule for my modem yet the modem is working very well, I know I could have followed the tutorial and added the udev rule then the modem would connect strait away but I like to do things my way as long as they work!

---

### Post by eiscafe on 2010-12-22
ok. so I updated to 10.10 and for now it seems to work. still a bit sceptical whether it's gonna stay (as it did work before too) but it seems to be a 10.04 specific problem. 

thanks gandaran!

---

### Post by Akhnatoun on 2010-12-22
> **eiscafe said:**
> 

Recently I got myself a ZTE MF 180 USB modem and following the instructions here [http://blog.lynxworks.eu/2010/08/huawei-e1550-in-ubuntu-10-04-1/](http://blog.lynxworks.eu/2010/08/huawei-e1550-in-ubuntu-10-04-1/) I actually got it to work on my Thinkpad X61 running 10.04. 



I hope you solved the problem. But are you sure that you needed to use “modem-modeswitch” from the beginning to use you ZTE modem, cause i bought the same MF 180 USB modem and using it for one month with both Ubuntu 10.04 & 10.10 on my HP dv4, and i never needed to add a udev rule or to use the modem-modeswitch program.

On both Ubuntu versions, I just needed to create a new mobile broadband connection using the default NetworkManager, inserting some parameters in the wizard, and it's working fine with me till now.

In Ubuntu 10.10, the New Mobile Broadband Connection Wizard window popped up automatically the first time I connected the modem. So I don't think that anyone needs an additional configuration with this kind of usb modems.;)

---

### Post by Akhnatoun on 2010-12-22
> **eiscafe said:**
> 

Recently I got myself a ZTE MF 180 USB modem and following the instructions here [http://blog.lynxworks.eu/2010/08/huawei-e1550-in-ubuntu-10-04-1/](http://blog.lynxworks.eu/2010/08/huawei-e1550-in-ubuntu-10-04-1/) I actually got it to work on my Thinkpad X61 running 10.04. 



I hope you solved the problem. But are you sure that you needed to use “modem-modeswitch” from the beginning to use you ZTE modem, cause i bought the same MF 180 USB modem and using it for one month with both Ubuntu 10.04 & 10.10 on my HP dv4, and i never needed to add a udev rule or to use the modem-modeswitch program.

On both Ubuntu versions, I just needed to create a new mobile broadband connection using the default NetworkManager, inserting some parameters in the wizard, and it's working fine with me till now.

In Ubuntu 10.10, the New Mobile Broadband Connection Wizard window popped up automatically the first time I connected the modem. So I don't think that anyone needs an additional configuration with this kind of usb modems.;)

---

### Post by eiscafe on 2010-12-23
> **Akhnatoun said:**
>  But are you sure that you needed to use “modem-modeswitch” from the beginning to use you ZTE modem, cause i bought the same MF 180 USB modem and using it for one month with both Ubuntu 10.04 & 10.10 on my HP dv4, and i never needed to add a udev rule or to use the modem-modeswitch program.


Since the modem was not recognized as a modem when I plugged it in it does *seem* like I needed it. after upgrading though the modem was recognized without any hazzle. 

funny thing though...it stopped working once I got home. and again I can't get it to work. it is recognized. the LED lights up red, then - after typing in my PIN - blue but I cannot connect. and it can't be that there simply is no signal here since I am sitting in the middle of the city.

---

### Post by metallus on 2010-12-28
just open a terminal and type:
sudo rmmod usb-storage
(enter your password if asked for one)
then the modem is in modem mode (do not plug in any usb storage device after that). It is an old trick that works with almost any modem with the same problem you have. The rmmod is not permanent. The usb-storage module is reloaded on reboot or by the command: sudo modprobe usb-storage .
Good luck.

---

### Post by lamad on 2012-12-20
This may not be a very intelligent solution...but it sure solved the issue for me...
I also got into this problem recently...and had to search through thousands of online guides, forums and tutos to find a solution.. I'm using Ubuntu 12.04 LTS. 

After following a guide that told me to add a .rules file to the** /etc/udev/rules.d** which would probably solve the prolem my system hangs itself at the ubuntu logo.. SO I GOT TWO PROBLEMS NOW!!...
After another round in the web.. i finally found a solution that actually solve both problems. 
My intention was to remove the rules file which i added cuz i knw it was the root for the system to hang... So how can i remove it without logging in????... 
The LIVE CD came into help.. i boot into the Ubuntu live OS.. but then.. it won't let me change files on the other system...SO????
What i did is outlined in the following..
1. Made a directory in  /media   ex:** /media/temp**
2. Mounted the ubuntu partition in that directory

NOW i have CONTROL over the files :) :)
3. Remove the newly added rules file from **/etc/udev/rules.**d directory

For some reason, it occurred to me that the problem is with the rules file that connects to   my ZTE modem. the file was 9-cdrom.rules.. i just took a back up of that file and removed it too... and typed in *sudo reboot*... 

VOILA!!!!!...the system boots up without a prob...and now when i connect my modem Ubuntu detected it and i was able to establish a connection without a hassle...

HOPE THIS WILL BE A HELP TO SOMEONE....:)

---

### Post by overdrank on 2012-12-20
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

