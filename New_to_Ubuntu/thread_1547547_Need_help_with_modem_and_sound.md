---
title: "Need help with modem and sound"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by gone2ocean on 2010-08-06
Hello,
I am a new user of Ubuntu Karmic on a pentium 4 gateway model # 7330gz with 512 memory. Tired of the problems with Windows, I tried many, many attempts to install ubuntu 10.04 and would have a black screen. I finally gave up and installed Karmic.  However, I can not get my modem (to send faxes) or sound to work. I installed efax-gtk and get the following response. One of many different responses.
[COLOR=Navy]GPL Ghostscript GPL Ghostscript 8.708.70: : Unrecoverable error, exit code 1
Unrecoverable error, exit code 1
Not valid postscript file
Print job received on socket
efax-0.9a: 17:27:18 opened /dev/ttyS1
efax-0.9a: 17:27:18 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 17:27:18 failed page /home/wilfredo/efax-gtk-server/efax-gtk-server-DGGfiD.001
efax-0.9a: 17:27:18 failed page /home/wilfredo/efax-gtk-server/efax-gtk-server-DGGfiD.002
efax-0.9a: 17:27:18 failed page /home/wilfredo/efax-gtk-server/efax-gtk-server-DGGfiD.003
efax-0.9a: 17:27:18 failed page /home/wilfredo/efax-gtk-server/efax-gtk-server-DGGfiD.004
efax-0.9a: 17:27:18 failed page /home/wilfredo/efax-gtk-server/efax-gtk-server-DGGfiD.005
efax-0.9a: 17:27:18 failed page /home/wilfredo/efax-gtk-server/efax-gtk-server-DGGfiD.006
efax-0.9a: 17:27:19 Error: fax device write: Input/output error
efax-0.9a: 17:27:21 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 17:27:23 Error: fax device write: Input/output error
efax-0.9a: 17:27:25 sync: dropping DTR
efax-0.9a: 17:27:25 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 17:27:25 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 17:27:25 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 17:27:27 Error: fax device write: Input/output error
efax-0.9a: 17:27:29 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 17:27:29 Error: fax device write: Input/output error
efax-0.9a: 17:27:29 Error: fax device write: Input/output error
efax-0.9a: 17:27:29 sync: sending escapes
efax-0.9a: 17:27:29 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 17:27:29 Error: fax device write: Input/output error
efax-0.9a: 17:27:29 Error: fax device write: Input/output error
efax-0.9a: 17:27:31 Error: fax device write: Input/output error
efax-0.9a: 17:27:33 Error: fax device write: Input/output error
efax-0.9a: 17:27:35 Error: sync: modem not responding
efax-0.9a: 17:27:35 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 17:27:35 finished - unrecoverable error[/COLOR]

[COLOR=Black]i have tried and tried to no avail to get it to work. I used scanModem, still no help. the modem information is 
[COLOR=DarkGreen] *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:e800(size=256) ioport:ec00(size=128)
[/COLOR]any assistance would be greatly appreciated. [/COLOR]the scanModem information is:
[COLOR=Purple] There are weekly updates of scanModem.  Your copy is more than
    10  weeks old!!
 If decisive guidance is not provided by this scanModem of 2010_05_29, 
 download an update from  [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il)

 Continuing in 10 seconds.

DISTRIB_ID=Ubuntu
num=30

Identifying PCI bus slots with candidate modems.
Running PCIbus cases
Analysing card in PCI bus 00:1f.6, writing to scanout.00:1f.6
Using scanout.00:1f.6 data, and writing guidance to ModemData.txt
Writing DOCs/Intel.txt
Writing DOCs/Conexant.txt

 Writing residual guidance customized to your System.
   A subfolder Modem/  has been written,  containing these files with more detailed Information: 
 ------------------------------------------------------------------------------------------
 1stRead.txt  Bootup.txt  dmesg.txt  DOCs  ModemData.txt  scanout.00:1f.6  tmp
    and in the DOCs subfolder:
 Conexant.txt   DriverCompiling.txt  InfoGeneral.txt  Intel.txt     Rational.txt
SoftModem.txt  Testing.txt        UNSUBSCRIBE.txt  wvdial.txt  YourSystem.txt
--------------------------------------------------------------------------------[/COLOR]
[COLOR=Black]Sound had worked on previous versions of ubuntu live CD,but not any more.  I amabout ready to go back to Windows with this headache.  Please help[/COLOR]

---

### Post by cariboo on 2010-08-07
Have you had a look [here]("https://help.ubuntu.com/community/DialupModemHowto"), I used this about a year ago, and it was pretty simple.

---

