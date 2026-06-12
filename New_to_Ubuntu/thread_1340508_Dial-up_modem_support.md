---
title: "Dial-up modem support"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Wendy3754875 on 2009-11-28
Will the next release include dial-up modem support?
If the installation of drivers etc were more user friendly then I would be happy to purchase the full driver version at Linuxant.

---

### Post by clhsharky on 2009-11-28
HI

There is support for some dial-up modems, but there probably wont ever be support for "soft or  win" dial-up modems.

Hardware based dial-up modems do work well and most of them are all ready supported. Here are 3 that are supported.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16825164005](http://www.newegg.com/Product/Product.aspx?Item=N82E16825164005)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16825104006](http://www.newegg.com/Product/Product.aspx?Item=N82E16825104006)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16825104007](http://www.newegg.com/Product/Product.aspx?Item=N82E16825104007)

Sharky

---

### Post by lkraemer on 2009-11-30
If you select the middle (USB Modem) and follow this guide, you should
be able to be up and running in less than 30 minutes.  This assumes that
wvdial is available on your LiveCD with the dependencies.
(If you need those dependencies post here and I'll look them up.)

[http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56)
Posting #4  Start at the sentence following:
"These work wonderful with wvdial, etc."

If wvdial isn't included you will need to download wvdial and the 4 required
dependencies so you can install wvdial.

Once you have wvdial installed, configured, and functional with dialup,
install Gnome-PPP and use dialup from the Graphics User Interface (GUI).

lk

---

### Post by Wendy3754875 on 2009-12-04
Thanks. I am up and running but only on the limited Linuxant driver version. In this regard, Ubuntu is not for newbies!

Everything else works very well.

---

### Post by Robster2 on 2009-12-05
Here are full instructions on how to get your internal dialup modem to work

I release it is not easy.

Ironically you need find someone that has broadband support.   You have to download some files to make this work.   For Part 3 you are going to need the Synaptic Package manager.  (If some one can work out a way to install the Gnome network manager via another method then this can be done by dialup)


Part 1 this what I found so far if you go system>Help and support search "Dialup Modem"

---------------------------------------------------------------------------

PART 1  Identifying your modem

---------------------------------------------------------------------------
Most dialup modems are not supported by Ubuntu, but drivers can be found that will enable the use of some such modems. First you need to identify what chipset your dialup modem is:

   1.      Download scanmodem ([http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)) using a computer with an Internet connection.


   2.  Copy the downloaded file to the Home folder of the computer with the dialup modem you wish to use.

3.      Open a Terminal (Applications &#8594; Accessories &#8594; Terminal) and type the following commands, pressing Return after each line:

      gunzip -c scanModem.gz > scanModem
      chmod +x scanModem
      sudo ./scanModem
      gedit Modem/ModemData.txt
             

   4.  A file containing information on the chipsets used by any detected modems should open. Print or save the information.

----------------------------------------------------------------------------

PART 2  Seting up the driver for your Modem (Now that you know what it is)

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
----------------------------------------------------------------------------
---------------------------------------------------------------------------

PART 3

---------------------------------------------------------------------------

You will need to install the Network Manager Gnome package with the Synaptic Package Manager

System>Administration>Synaptic Package Manager

You will need to know the following information:

ISP Phone Number; Username; Password; Domain Name Server (DNS) addresses.

   1.   Press System &#8594; Administration &#8594; Network
   2.   Press Unlock and type your password to unlock the settings
   3.   Select the Connections tab.   
   4.   Select Modem connection or Point to point connection and press       Properties.
   5.Ensure that Enable this connection is unchecked and enter appropriate information on each of the three tabs.
   6. Click OK to save the information you just entered
   7. Select the DNS tab.
   8. Click Add and enter the DNS address given to you by your ISP.
   9. Click Close.

---

### Post by Wendy3754875 on 2009-12-05
I have more or less completed the three part steps and the limited driver version does work, at 14.4 kbps. I have the option to purchase the full version. If Ubuntu does not offer modem support, changes to the kernel may make the drivers inoperable. This leaves me with two choices: paying for drivers repeatedly or never upgrading Ubuntu.

I'm going to try installing the Conexant Dell drivers, which are said to be free, but this won't resolve the uncertainty modem users face. Only a commitment to dial-up support would do that, for both end users and manufacturers.

I'm anxious to see Ubuntu move beyond being a hobbyist project. In nearly every aspect it has become a full-fledged OS, able to meet the needs of the average person. If it weren't for the lack of dial-up support, I could uninstall Windows and make the transition to Ubuntu complete. This is the last hurdle!

Wen

---

### Post by Bartender on 2009-12-05
Dial-up support is likely to get worse instead of better.

But even if you get dial-up working, it's a horrible experience.  Ubuntu updates are often 30 to 40 MB.  Excruciating.

Some of us were talking about the situation  [here]("http://ubuntuforums.org/showthread.php?t=1238954")

And here's my old dial-up [diary]("http://ubuntuforums.org/showthread.php?t=480717")

Those two should give you a pretty good idea of the state of dial-up.

I feel pretty confident that the best dial-up speeds are likely to be acquired with a good old US Robotics external serial modem.  The Sportsters are the most common.  Mine says "5686" on the bottom.  Lots of these USR's are laying around in closets unused.  I collected three or four of them from ebay and craigslist.

---

### Post by Robster2 on 2009-12-05
What version of Ubuntu are you using?

14.4kbps is pathetic

This the Dell full speed driver for Jaunty.

[https://help.ubuntu.com/community/DialupModemHowto/Conexant?action=AttachFile&do=view&target=hsfmodem-7.80.02.03full_Jaunty.tar.bz2](https://help.ubuntu.com/community/DialupModemHowto/Conexant?action=AttachFile&do=view&target=hsfmodem-7.80.02.03full_Jaunty.tar.bz2)

Let us know how you get on.

---

### Post by Wendy3754875 on 2009-12-05
> **Bartender said:**
> Dial-up support is likely to get worse instead of better.

But even if you get dial-up working, it's a horrible experience.  Ubuntu updates are often 30 to 40 MB.  Excruciating.
Compared with Windows Vista updates, it's not that bad. Downloads can be completed overnight, in stages.
> 
Some of us were talking about the situation  [here]("http://ubuntuforums.org/showthread.php?t=1238954")

And here's my old dial-up [diary]("http://ubuntuforums.org/showthread.php?t=480717")

Those two should give you a pretty good idea of the state of dial-up.
Yes, way beyond the average users expertise or patience :(
> 
I feel pretty confident that the best dial-up speeds are likely to be acquired with a good old US Robotics external serial modem.  The Sportsters are the most common.  Mine says "5686" on the bottom.  Lots of these USR's are laying around in closets unused.  I collected three or four of them from ebay and craigslist.
I have a few PCI modems. Have not tried going online with Linux on my desktop computer. The one in the laptop is supported by Linuxant, but is limited to 14.4 kbps for the free version.
[quote=Robster2]What version of Ubuntu are you using?[/quote]
9.04
> 14.4kbps is pathetic

This the Dell full speed driver for Jaunty.

[https://help.ubuntu.com/community/Di...Jaunty.tar.bz2](https://help.ubuntu.com/community/Di...Jaunty.tar.bz2)

Let us know how you get on. 
The driver has failed to detect the device.
This was a long shot because my laptop is a Gateway.
[color=green]
From ModemData.txt:
===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.18
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1
00-01: Conexant Digital : Conexant Digital : playback 1
00-03: INTEL HDMI : INTEL HDMI : playback 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0700000 irq 22

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: Conexant ID 2c06
Address: 1
Vendor Id: 0x14f12c06
Subsystem Id: 0x1025021c
Revision Id: 0x100000
Modem Function Group: 0x2

 The audio card hosts a softmodem chip:  0x14f12c06

 14f1 is the Conexant Vendor ID, and 0x14f12c06 a softmodem chipset.
 Get a hsfmodem package through [http://www.linuxant.com](http://www.linuxant.com)

If not a Conexant modem, the driver hsfmodem-drivers with its dependent drivers:

----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:1b.0:
	Modem chipset  detected on
NAME="Audio device: Intel Corporation 82801I "
CLASS=0403
PCIDEV=8086:293e
SUBSYS=1025:021c
IRQ=22
HDA=8086:293e
SOFT=8086:293e.HDA
HDAchipVendorID=14f1
CHIP=0x14f12c06
IDENT=hsfmodem
Driver=hsfmodem-drivers

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801I 
      Primary device ID:  8086:293e
    Subsystem PCI_id  1025:021c 
    Softmodem codec or chipset from diagnostics: 0x14f12c06
                               from    Archives: 
                        The HDA card softmodem chip is 0x14f12c06
      

Support type needed or chipset:	hsfmodem


Writing DOCs/Intel.txt

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt[/color]

---

### Post by Wendy3754875 on 2009-12-05
Meanwhile, I'm going to see about updating the ALSA drivers.

---

### Post by lkraemer on 2009-12-05
Wendy3754875,
The best thing to do is to forget about trying to make any Win-modem
work with such drivers and do as clhsharky suggested.  Purchase a 
USB US Robotics Hardware modem, plug it in the USB port and to the
phone line.  Those work wonderful with wvdial and Gnome-PPP.
I've been on dialup at home for years, and other than the long upgrade
times, it isn't so bad.  It is usable, but slow on the downloads.

Instead of purchasing the Drivers, spend an additonoal $24.00 and buy 
the USB Hardware Modem.  It's your best bet.

Good luck.

lk

---

### Post by Shazaam on 2009-12-05
Run the scanmodem tool to get info on the modem's chipset. It could be either an hsf or hcf chipset. That way you know exactly which driver you need.
When you purchase the full version from Linuxant you are buying a licence, not the driver. After that you can download a newer/different version of the driver that works with your kernel versions/distros at any time.
Or, you can download the version that needs to be compiled. Not a problem as this saves you the time it takes waiting for Linuxant to post a newer version when your kernel gets updated. Just make sure you have build-essential installed.
For the money Linuxant charges for the licence you could pick up a used external serial modem from places like ebay. Stay away from usb based ones as these are usually winmodems (software based like your internal).

---

