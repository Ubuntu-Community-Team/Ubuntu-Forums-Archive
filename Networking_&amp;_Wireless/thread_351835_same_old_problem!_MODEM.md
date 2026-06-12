---
title: "same old problem! MODEM"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by thorosius on 2007-02-02
One thing I am happy to know is that I am not totaly alone in this big, never ending dilema.

                I used Red Hat Linux for 5-6 months a year back but couldn't get my modem to work so formated my drive, broke its 4 CDs and threw them in the bin. I then learnt about Ubuntu installed it and after a month bad memories are coming back. I have tried some things with no success.

                I have an Mercury IntelChipset modem I cant determine whether its a 537, 537EP or anyother (if any exist). scanmodem tool's ModemData.txt says its "INTEL537". What should I do?

                Please Please Please can any one help?


                
This is modem's HomePage:
[http://www.mercury-pc.com/product-detail.php?link=p-modem&subtitle=Fax%20Modem&productid=180](http://www.mercury-pc.com/product-detail.php?link=p-modem&subtitle=Fax%20Modem&productid=180)




ModemData.txt:
 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
 Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2006_December_25


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 02:02.0	e159:0001	8086:0003	Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface

 Modem interrupt assignment and sharing: 
193:        637          0   IO-APIC-level  ehci_hcd:usb5

 --- Bootup diagnositcs for card in PCI slot 02:02.0 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  02:02.0
   Class 0780: e159:0001 Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
      Primary PCI_id  e159:0001
 Support type needed or chipset:	INTEL537
 


 Vendor e159 is Tiger Jet , [http://www.tjnet.com/](http://www.tjnet.com/)
  Controller e159:0001  translates PCI commands to the serial link used by
     the silabs DAA from the si3034, si3044 and si3056 family.
  The e159:0001  with SubSystem 8086:0003 is TJ320 v2.0 
  is the first and still most common of the Intel537 modem family.
  However primary controller chip can have broader uses:  [http://www.tjnet.com/chips/tiger320.htm](http://www.tjnet.com/chips/tiger320.htm)
  Though having its own driver package under 2.4.n. kernels,
  support (if any) from Intel is now included within the Intel-537EP package.

 ====== end Tigerjet section =======
 In 2006, Intel appears to have ceased updates for Linux.
 For the INTEL537 and INTEL536 chipset modems, the most current support is provided at:
       [http://phep2.technion.ac.il/linmodems/packages/intel/Philippe.Vouters/](http://phep2.technion.ac.il/linmodems/packages/intel/Philippe.Vouters/)
 But regular support is not available, see:  [http://archives.linmodems.org/24939](http://archives.linmodems.org/24939)
:
 The outdated official Intel support packages can be accessed through:
       [http://developer.intel.com/design/modems/support/drivers.htm](http://developer.intel.com/design/modems/support/drivers.htm)
 Read Intel.txt and Modem/YourSystem.txt for follow through guidance.


Writing Intel.txt

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   kernel_headers base folder /lib/modules/2.6.17-10-generic/build


Checking pppd properties:
	-rwsr-xr-- 1 root dip 260920 2006-07-11 00:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by thorosius on 2007-02-03
I have successfully installed the drivers but wvdial says I have no dial tone. Please have a look at this:

************************************************** ************************
fahd@fahd-desktop:~/home/philippe/intel-537EP_secure-2.60.80.1$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1 S2 S3 


Sorry, no modem was detected! Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

************************************************** ************************
WVDIAL.CONF CONTENTS
************************************************** ************************
[Dialer Defaults]
Modem = /dev/modem
Baud = 57600
SetVolume = 3
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+GCI=84
Init3 = ATM1L3
Carrier Check = no
Phone = 13198765
Username = cstb
Password = cstb

************************************************** ************************
WVDIAL OUTPUT
************************************************** ************************
fahd@fahd-desktop:~/home/philippe/intel-537EP_secure-2.60.80.1$ sudo wvdial
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=84
AT+GCI=84
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Modem initialized.
--> Sending: ATDT13198765
--> Waiting for carrier.
ATDT13198765
NO DIALTONE
--> No dial tone.
--> Disconnecting at Sat Feb 3 15:14:26 2007

I must add that when wvdial starts I hear a click sound from my modem (its buzzer I think) but when wvdial says its dialing I picked the phone but there was no dialing going on just the dial tone.

---

