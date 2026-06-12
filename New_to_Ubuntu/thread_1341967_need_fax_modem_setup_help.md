---
title: "need fax modem setup help"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by bob12564 on 2009-11-30
I have an external modem connected to the serial port.  It's a Zomm 2949L which I believe uses a Lucent chipset.  My understanding is that external modems "just work" but I don't know how to test it.  In Windows I can go to Control Panel and then Printers and Modems and click modem diagnostics.  I don't see anything in Gnome.

I use DSL for internet so this modem is exclusively for faxes.  I installed HPLIP for my printer and it installed an HP fax utility which says that it can't find a modem.  I read the Gnome help and it recommended efax-gtk and sl-modem-daemon.  I only installed efax-gtk because sl-modem-daemon seems to only apply to modems manufactured by SmartLink.  

I don't know how to configure efax-gtk or get the HP fax utility to work.  I also cannot determine if my modem is even working.  Can anyone help?  Everything I've read so far deals with dialup networking, USB modems, WinModems, and soft modems and that's not my issue.

Many thinks!

---

### Post by bob12564 on 2009-11-30
forgot to mention that I'm using Jaunty/9.04

---

### Post by lkraemer on 2009-11-30
Go to STSYEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER
Search for wvdial, then install.  Once wvdial is installed you will
need to configure the software, then add your loginname and password
to the configuration file along with phone number.

If wvdial wasn't included on the 9.04 LiveCD then you are going to have to download wvdial and the four dependencies and install.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[http://packages.ubuntu.com/jaunty/comm/](http://packages.ubuntu.com/jaunty/comm/)

And that could present a problem unless you have a wired Ethernet connection, or another computer that has internet access to download
the files.


Here are the dependencies for wvdial.
debconf(>=0.5.00) | cdebconf
libc6(>=2.7-1)
libuniconf4.4
libwvstreams4.4-base
livwvstreams4.4-extras
libxplc0.3.13
ppp(>=2.3.0)

Just use Synaptic and search for each of these (minus the (>=2.7-1 etc))
to see which ones you need to download. (The ones that are installed
will have a box beside them that is filled in with a color....
green......if it is like my system.....)

lk

---

### Post by bob12564 on 2009-11-30
Thanks for the reply.  I have an ethernet connection/DSL broadband already running for internet access.

Let me see if I understand this correctly.  I need to add some dialer software that will be used by the fax software.  The fax software doesn't include dial capabilities.  Does that sound correct?

One of the package dependencies you mentioned is PPP and I used PON and POFF with my DSL modem before I converted to a wireless DSL gateway/router.  I presume that means I still have some sort of PPP utility installed and that I can use it.  I've also read about Gnome-ppp as a front end to wvdial.  I want to be very careful not to set up dialup networking for an internet service provider when all I want if fax. I don't want to risk interfering with my broadband setup.

Thanks.

---

### Post by lkraemer on 2009-12-01
Shouldn't be any problems doing just what you want.

Keep us informed on your progress.

lk

---

### Post by bob12564 on 2009-12-01
I had a little bit of progress.  I think I'm understanding that I need wvdial to act as a dialer for the modem.  I checked Symaptic and discovered that I already had it installed.  On another forum I found a command line instruction to run it and it detected my external serial modem.  TO make things simpler I also installed gnome-ppp because it provides a GUI to wvdial.  Gnome-ppp is intended to provide dialup access to and ISP which isn't what I want, so I only filled in a phone number and clicked "connect" to see if something would happen.  The modem actually dialed but then I got a phone company recording telling me that my phone was off the hook.  It was really late and I was getting frustrated so I didn't pursue it.  I think it might have dialed without waiting for a dial tone.  That's another problem for later and I could use some help here.

Having gotten that far I tried Efax-gtk again but it didn't seem to do anything.  I went to the efax website  looking for configuration instructions but didn't find any.  Other posts on this forum suggest adding a dummy printer that has postscript capability and hot wiring Efax to monitor that print queue.  Supposedly that allows you to print-to-fax from applications such as Open Office.  That's a little over my head at this point.  Maybe someone can provide a simple, non-technical overview of how this works.  If I can understand the concept I might be able to understand what I'm doing.

Other beginners have complained about the complexity of configuring dialup modems and I'm sharing their pain.  There are so many thing that work so well in Ubuntu but maybe dialup modems and faxing need more simplification.

---

### Post by bob12564 on 2009-12-01
I've done more reading and getting more confused.

Do I really need wvdial for faxing?

Wvdial seems to include PPP and it wants logon information for an ISP.  I can't see any fax software working with wvdial because it'll hang on the login step generated by wvdial.  I've read that minicom is a dialer that does not include PPP.  Is that more appropriate than wvdial for faxing?

---

### Post by _duncan_ on 2009-12-04
Someone from [[COLOR="Blue"]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1269397") thread was successful. I haven't actually tried setting up fax on my PC, so I can't vouch if it will work for you.

I'm merely speculating, but I think you have to install the appropriate driver for your modem first, before you can use the process referenced in the thread.

Based on your original post, it seems you have a softmodem with a Lucent/Agere chipset. The appropriate driver for it I think is the open-source 'martian' driver. Unforunately, that's all I know about this chipset. Maybe linmodems.org will have more info. Also, I've seen folks here in this forum reporting success installing the 'martian' driver, so a little search using keywords like lucent/agere, martian driver, etc. might help.

---

### Post by bob12564 on 2009-12-05
I was able to get everything working and I can send and receive faxes.  My next problem is the quality - or lack of- of the faxes.  My outgoing faxes are illegible. I'll move that to a new thread.  Thanks to everyone who replied.

---

### Post by johnaaronrose on 2010-02-17
I've got a Zoom modem. I downloaded from Linuxant the driver and installed it OK, as the device's CD did not have a karmic driver available and its driver source failed to compile. I've installed gnome-ppp and specified the Device as each of /dev/ttyS1,/dev/ttyS2 & /dev/modem with Type of USB Modem but all failed to Detect. Any ideas?

---

### Post by GeorgeVita on 2010-02-17
Hi **johnaaronrose**,
please let us know the exact model of your modem. If you do not know it, supply more info:

- is this modem internal or external?
- why you got Linuxant drivers? Did you find/know its chipset?
- as you state 'USB modem', how is it listed on **lsusb** command (or **lshw** if internal)?

Regards,
George

---

### Post by johnaaronrose on 2010-02-17
George,

Zoom model 3095 56K v.92 external USB modem.

I bought it from Amazon where there was a customer review:
"I bought this USB mini modem for my laptop running a 64-bit version of Linux with the 2.6.32 kernel, and it works a treat.
"The supplied Quick Start Guide and CD have information and instructions for Linux users, including driver packages for some specific distributions (not for the distribution I use, unfortunately) and also a non-distro specific tarball. Unfortunately the driver from the CD failed to install. However, I surfed over to the Linuxant driver download page on the Web and grabbed a copy of the latest driver tarball, and that installed without problem. 
Although not mentioned in the supplied guide, I had to add myself to the uucp group and change the group of the symlink /dev/modem from root to uucp. After doing these things, the modem worked.".

The compile/install displays:
Conexant DGC USB modem driver, version 1.11

lsusb shows: Bus 001 Device 010: ID 0803:3095 Zoom Telephonics, Inc. 

hwinfo shows:
idVendor = 0x0803
    idProduct = 0x3095
    manufacturer = "Conexant"
    product = "USB Modem"
    serial = "24680246"

---

### Post by GeorgeVita on 2010-02-18
Hi ****,
read some info at [Dial-up Redux]("http://ubuntuforums.org/showthread.php?t=1377619")

And check system activity:

- Boot without modem, **wait** for the system to load
- do NOT RUN any communication program
- open a terminal window and try: **sudo dmesg -c**
(this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show only 'new' activity)
- attach modem
- **wait** 30-40 seconds
- from terminal: **dmesg**
- from terminal: **uname -a**

Post output from THE LAST **dmesg** (not from the previous 'sudo dmesg -c') and kernel version from 'uname -a'.

We need to know if any communication port is created.

Regards,
George

---

### Post by johnaaronrose on 2010-02-18
George,

Requested results:

administrator@JohnLaptop:~$ dmesg
[  963.612534] usb 1-5.4: new full speed USB device using ehci_hcd and address 10
[  963.684419] usb 1-5.4: device descriptor read/64, error -32
[  963.860431] usb 1-5.4: device descriptor read/64, error -32
[  964.036427] usb 1-5.4: new full speed USB device using ehci_hcd and address 11
[  966.575314] usb 1-5.4: configuration #1 chosen from 2 choices
[  966.580641] cdc_acm 1-5.4:1.0: ttyACM1: USB ACM device
[  966.582844] dgcusbdcp: dgcusbdcp_probe: adding union descriptor for cdc_acm
[  966.603449] cdc_acm 1-5.4:2.0: ttyACM1: USB ACM device
administrator@JohnLaptop:~$ uname -a
Linux JohnLaptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux

PS After that, I tried GNOME PPP again with device of ttyACM1 and it it failed to detect modem.

---

### Post by GeorgeVita on 2010-02-18
> **johnaaronrose said:**
> ...PS After that, I tried GNOME PPP again with device of **ttyACM1** and it it failed to detect modem.

Type manually the **/dev/ttyACM1** at 'Device' (gnome-ppp > setup > modem). Replace /dev/ttyUSB0 in the example below:
 [IMG]http://acomelectronics.com/GeorgeVita/pppco.jpg[/IMG]

---

### Post by johnaaronrose on 2010-02-18
George,

I already tried both /dev/ttyACM1 & /dev/ttyACM0 in GNOME PPP. ls /dev shows ttyACM0 but not ttyACM1.

---

### Post by harrisheatair on 2010-02-21
I have Ubuntu 9.10.  I like learning new things and trying to figure them out.  I have read past forums to get an idea of what to do for faxing but I can't find my internal modem.  It is a Rosewill RC-403 PCI 56Kbps V.92 Data/fax Voice Modem card.  If you can help it is appreciated.

---

### Post by johnaaronrose on 2010-02-21
harrisheathair,
I removed the modem-manager package and the modem was detected by Gnome PPP (in package gnome-ppp). I haven't yet tried faxing using efax-gtk due to family visit this weekend.

---

### Post by harrisheatair on 2010-02-21
I just tried the gnome ppp.  I use broadband and vonage phone.  Could this be my problem, or have I got to that point yet.  It still can't detect my modem.

[COLOR=Red]modem: no file or directory[/COLOR]

---

### Post by lyall on 2010-02-21
why are you still using a fax?

set up a CUPS-PDF-Printer in your printer configuration
then you can print the document to CUPS-PDF-Printer 
and e-mail the pdf file
it is faster than sending a fax and it does not cost you (it is FREE).
Faxing a document out of your call zone is going to cost you
in long distance calling.

good luck and have fun learning

---

### Post by harrisheatair on 2010-02-22
There is two reasons for the efax.  One is for work.  The place were I work likes things faxed from time to time.  If I can do this at home, it allows more time with my family.  The other is out of personal knowledge and curiosity.  I have unlimited long distance.  I realize emailing would be easier and quicker, but I enjoy learning new things that can be done on my computer. ( New to me that is)  I really enjoyed learning about using virtual box and fire starter.  I just wanted to add this to my resources for work and personally.

---

### Post by GeorgeVita on 2010-02-23
> **johnaaronrose said:**
> I removed the modem-manager package and the modem was detected by Gnome PPP (in package gnome-ppp). I haven't yet tried faxing using efax-gtk due to family visit this weekend.

Hi **johnaaronrose**, most times an external modem ca be controlled with AT commands as you have the 'communication port'. For your case this port was /dev/ttyACM0 or /dev/ttyACM1 which must be stable after a reboot, after modem attachment with NONE communication program running. There is a possibility modem-manager faced some problems (this program is used for mobile broadband modems as dial-up seem to be left behind ...).
If Gnome PPP detects the modem and connects you are OK.

--------

Hi **harrisheatair**, your case is probably more complicated as most internal modems are win-modems and they need specific driver. Search for more info starting from [http://linmodems.technion.ac.il/first.html](http://linmodems.technion.ac.il/first.html)

Regards,
George

---

### Post by RifRaf1961 on 2010-04-01
> **lyall said:**
> why are you still using a fax?

set up a CUPS-PDF-Printer in your printer configuration
then you can print the document to CUPS-PDF-Printer 
and e-mail the pdf file
it is faster than sending a fax and it does not cost you (it is FREE).
Faxing a document out of your call zone is going to cost you
in long distance calling.

good luck and have fun learning

Hello,
MANY companies and virtually all Government Depts will not allow you to email things to them anymore and require a Fax instead.  I asked a guy at a Gov Dept today if I could email a PDF of my daughter's birth certificate and he said NO!  You can either bring it in or send it via Fax.  They have had too many issues with virus.  That is why I've spent the last two hours on this site reading a bunch of gripe posts about how ubuntu is not supporting dial-up users very well.  Personally, with all the constant updates, I don't think ubuntu would be a good choice for dial-up users anyway.  It works great with my DSL though.  However, I still haven't figured out how to install my external modem in ubuntu so I can send faxes.  Still searching... :(

Rif

---

