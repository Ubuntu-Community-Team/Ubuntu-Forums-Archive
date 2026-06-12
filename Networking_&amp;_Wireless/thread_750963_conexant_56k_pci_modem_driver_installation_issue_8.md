---
title: "conexant 56k pci modem driver installation issue 8.04"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by ikt on 2008-04-10
Hi guys,

I have a conexant pci 56k modem and ubuntu 8.04 and it's giving me a pretty tough time :( 

When I try to install the driver from the dell website I get the error:

Newer version already installed.

But in Gnome PPP, when I try to auto detect the modem, it says no modem was found.

I'm fairly confused at this point :(

---

### Post by KMuchane on 2008-04-10
ikt, 
Hello...    
Run the command sudo wvdialconf and paste the results...

---

### Post by ikt on 2008-04-14
> **KMuchane said:**
> ikt, 
Hello...    
Run the command sudo wvdialconf and paste the results...

$ sudo wvdialconf 

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttySHSF0 first, /dev/modem is a link to it.
Modem Port Scan<*1>: SHSF0 
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   SHSF1 SHSF2 SHSF3 SHSF4 SHSF5 
Modem Port Scan<*1>: SHSF6 SHSF7 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
:~$

---

I understand it says no modem found, but that doesn't make any sense, I have the cover off the pc, and am looking at the physical modem itself right now. :s

---

### Post by KMuchane on 2008-04-14
itk,  
Hi... of course you need the drivers for Ubuntu to "see" it. But first things first, take a look at:  [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)     HTH.

---

### Post by ikt on 2008-04-14
> **KMuchane said:**
> you need the drivers for Ubuntu to "see" it. But first things first, take a look at:  [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)     HTH.

> **ikt said:**
> When I try to install the driver from the dell website I get the error:

Newer version already installed.

^

---

### Post by ikt on 2008-04-15
bump

---

### Post by KMuchane on 2008-04-16
Hi ,

Hmmm... bump what ? If it worked let us know how, someone might be having a similar problem.

---

### Post by ikt on 2008-04-18
> **KMuchane said:**
> Hi ,

Hmmm... bump what ? If it worked let us know how, someone might be having a similar problem.

You mentioned going to the Dial Up modem help page, I quoted your post suggesting this, and my original post in which I had already been to the dial up modem help page:

[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

> Conexant drivers provided by Dell

    *      Dell provides drivers for the Conexant modems of their Linux-based laptops that should work for all Conexant HSF modems. The latest drivers are available here: [WWW] [http://linux.dell.com/files/ubuntu/modem-drivers/hsf/](http://linux.dell.com/files/ubuntu/modem-drivers/hsf/). Download the .deb file, double click it and it will be installed automatically. 

My problem is specifically that the modem drivers are installed and yet it still can't see the modem.

---

### Post by ikt on 2008-04-21
went back to 7.10, installed the dell driver and now get the following error:

$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Err>: Cannot open /dev/modem: Input/output error
WvDial<Err>: Cannot open /dev/modem: Input/output error
WvDial<Err>: Cannot open /dev/modem: Input/output error

---

### Post by KMuchane on 2008-04-21
Hi!

It should be sudo wvdialconf. What you are doing now is dialing out. 
What happens when you run the scanModem tool?  Does lspci | grep Modem, output a result indicating the presence of a modem ?

---

### Post by ikt on 2008-04-21
> **KMuchane said:**
> Hi!

It should be sudo wvdialconf. What you are doing now is dialing out. 
What happens when you run the scanModem tool?  Does lspci | grep Modem, output a result indicating the presence of a modem ?

$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttySHSF0 first, /dev/modem is a link to it.
Modem Port Scan<*1>: SHSF0 
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   SHSF1 SHSF2 SHSF3 SHSF4 SHSF5 
Modem Port Scan<*1>: SHSF6 SHSF7 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

$ lspci | grep Modem
00:0f.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 08)

+

[http://adam.com.au/totalss/modem.png](http://adam.com.au/totalss/modem.png)

Will run the scanmodem tool :/

-----------------------------

Decided to try another modem, an Intel 536EP 56k modem, installed the .deb package listed here:

[https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)

then:

$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<Err>: Configuration does not specify a valid phone number.
WvDial<Err>: Configuration does not specify a valid login name.
WvDial<Err>: Configuration does not specify a valid password.

then downloaded and installed gnome ppp, put in username/password and phone number and it connected all good.

Thanks for your help :)

---

### Post by KMuchane on 2008-04-22
Hi,

Glad to hear it worked for you. Cheers!

---

### Post by Dobroslav on 2008-04-24
Hello everybody!
(off)I want to upgrade my ubuntu to 8.04.I have HSF driver 7.68.00.07 full.Can driver work on 8.04?(/off)

---

### Post by ikt on 2008-05-08
> **Dobroslav said:**
> Hello everybody!
(off)I want to upgrade my ubuntu to 8.04.I have HSF driver 7.68.00.07 full.Can driver work on 8.04?(/off)

good question, If it's crucial I would wait a bit until it's confirmed to work as I'm having some issues with different hardware, If I knew what I know now I wouldn't be that excited about hardy.

---

### Post by W.Sorting on 2008-05-18
Hello, 

I am having exactly the same problem as IKT. The conexant modem i'm using (U.S. Robotics USR5600A) isn't recognized by ubuntu 8.04, even after I install the right modem driver.  It says that no modem is found, and an extra line saying that "hda modems might require reboot".  However after reboot the same problem was still there.  I don't have the extra money to buy another modem, which solved IKT's problem-- does anyone have any ideas how to get the modem working?

Thanks, 
W.Sorting

---

### Post by Raval on 2008-05-25
[http://ubuntuforums.org/showpost.php?p=5042873&postcount=28](http://ubuntuforums.org/showpost.php?p=5042873&postcount=28)

---

