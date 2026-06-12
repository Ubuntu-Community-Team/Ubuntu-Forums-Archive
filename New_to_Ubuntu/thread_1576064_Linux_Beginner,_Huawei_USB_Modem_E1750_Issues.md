---
title: "Linux Beginner, Huawei USB Modem E1750 Issues"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by tvaetbjorn on 2010-09-16
I have tried off an on for a month to make my Huawei E1750 work, looking at various threads here, and trying out different versions of Ubuntu (10.04, 9.04, 8.04). I currently have Ubuntu 9.04. 

I will probably ask a lot of obvious questions, but I really am a beginner and I have no previous experience with Linux. 

I think the problem begins with the Tele2 software install itself. For some reason every site I go to about E1750 says it "works right out of the box". Well, for me, using Wine, the installation windows are glitchy and sometimes are missing buttons so I can't go forward, accept the license agreement, and even get to the install. I don't know if installing it that way is the only way. There always seems to be a few ways to install something on Ubuntu, so I am hoping there is another way. 

I have tried all the advice I have seen, I've set up the Network using the correct information, gotten the USB Modeswitch before, but I am probably doing something really obvious wrong if so many people aren't have as hard a time as I am. 

lsusb without the modem plugged in:

 Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ac8:3343 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lsusb with the modem plugged in:

Bus 002 Device 004: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ac8:3343 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Please help me! I have run out of help pages to read and none seem to address my particular problem (as far as I know).

---

### Post by gandaran on 2010-09-16
> I think the problem begins with the Tele2 software install itself. For some reason every site I go to about E1750 says it "works right out of the box". Well, for me, using Wine, the installation windows are glitchy and sometimes are missing buttons so I can't go forward, accept the license agreement, and even get to the install. I don't know if installing it that way is the only way. There always seems to be a few ways to install something on Ubuntu, so I am hoping there is another way. 
forget using wine, even if the software installed correctly it would never work, windows drivers don't work in wine.
> I have tried all the advice I have seen, I've set up the Network using the correct information, gotten the USB Modeswitch before, but I am probably doing something really obvious wrong if so many people aren't have as hard a time as I am.
network manager/mobile broadband tab is the way to go, run the setup wizard, check that the wizard detects the modem, choose your country and internet provider and you need to fill in the correct information for the setup, the APN and authentication method details are very important, one wrong detail and it wont work.
you may need to reboot the computer for the setup to start working.

---

### Post by tvaetbjorn on 2010-09-25
I've done all this before except it never notices the modem when I run the setup wizard. 


Then again, I have heard others having that problem. Ok, so, forget installing anything? Got it. I'll just trust you that it can somehow work anyways. And... back to all the other pages I once tried to look for help on.

If you're feeling extra kind, maybe give me some tips on making my modem recognized? It could save me a few more weeks of banging my head against a wall.

---

### Post by Kr4zyl3gz on 2010-09-25
never had any issues On my USB Modem =\

---

### Post by spiky001 on 2010-09-25
Hi tvaetbjorn when you installed the modeswitch did you install usb modeswitch data? only checking

---

### Post by cogier on 2010-09-25
Not sure if this will work for you but I have been very, very impressed with Sakis3G

What you need to do is run the following in Terminal and with any luck it will all fall into place: -

```
wget "http://www.sakis3g.org/versions/latest/i386/sakis3g.gz"
echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c
gunzip sakis3g.gz
chmod +x sakis3g
./sakis3g --interactive
```

It has worked for me on more than one computer with out a hitch.

More details here: - [http://www.sakis3g.org/]("http://www.sakis3g.org/")

Have fun!!

---

