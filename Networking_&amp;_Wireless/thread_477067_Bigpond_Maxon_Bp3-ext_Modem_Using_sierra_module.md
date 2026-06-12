---
title: "Bigpond Maxon Bp3-ext Modem Using sierra module"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by sharke on 2007-06-18
Go here and download the driver and the pppscripts file [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601)
Now extract the files.
In a terminal

# cd <directory of source>
# tar &#8211;zxf sierra.v.X.Y.Z.tar.gz
# cd sierra.v.X.Y.Z

Before installing the driver we need to patch the source with the modem uids. Quozl has done this many thanks Quozl for your excellent work you can be proud of your work.[http://quozl.netrek.org/bp3-usb/](http://quozl.netrek.org/bp3-usb/)

Patch
 
CONFIG_USB_SERIAL_SIERRAWIRELESS=m

--- linux-2.6.19.2/drivers/usb/serial/sierra.c  2006-11-30 08:57:37.000000000 +1100
+++ linux-2.6.19.2-maxon/drivers/usb/serial/sierra.c    2007-01-24 10:36:24.000000000 +1100
@@ -44,6 +44,7 @@
 
        { USB_DEVICE(0x1199, 0x0112) }, /* Sierra Wireless AirCard 580 */
        { USB_DEVICE(0x0F3D, 0x0112) }, /* AirPrime/Sierra PC 5220 */
+       { USB_DEVICE(0x16d8, 0x6280) }, /* Maxon BP3-USB 3G Bigpond Telstra */
        { }
 };
 MODULE_DEVICE_TABLE(usb, id_table);
@@ -65,6 +66,7 @@
        { USB_DEVICE(0x1199, 0x6804) }, /* Sierra Wireless MC8755 for Europe */
        { USB_DEVICE(0x1199, 0x6812) }, /* Sierra Wireless MC8775 */
        { USB_DEVICE(0x1199, 0x6820) }, /* Sierra Wireless AirCard 875 */
+       { USB_DEVICE(0x16d8, 0x6280) }, /* Maxon BP3-USB 3G Bigpond Telstra */
        { }
 };
We now add quozls patch to the sierra.c file

I do this in nautilus running sudo nautilus
browse to sierra directory open sierra.c and ad to this section
 static struct usb_device_id id_table [] = { 
	{ USB_DEVICE(0x1199, 0x0017) },	/* Sierra Wireless EM5625 */ 
	{ USB_DEVICE(0x1199, 0x0018) },	/* Sierra Wireless MC5720 */ 
	{ USB_DEVICE(0x1199, 0x0218) },	/* Sierra Wireless MC5720 */ 
	{ USB_DEVICE(0x1199, 0x0020) },	/* Sierra Wireless MC5725 */ 
	{ USB_DEVICE(0x1199, 0x0019) },	/* Sierra Wireless AirCard 595 */ 
	{ USB_DEVICE(0x1199, 0x0021) },	/* Sierra Wireless AirCard 597E */ 
	{ USB_DEVICE(0x1199, 0x0120) },	/* Sierra Wireless USB Dongle 595U*/ 
	 
	{ USB_DEVICE(0x1199, 0x6802) },	/* Sierra Wireless MC8755 */ 
	{ USB_DEVICE(0x1199, 0x6804) },	/* Sierra Wireless MC8755 */ 
	{ USB_DEVICE(0x1199, 0x6803) },	/* Sierra Wireless MC8765 */ 
	{ USB_DEVICE(0x1199, 0x6812) },	/* Sierra Wireless MC8775 */ 
	{ USB_DEVICE(0x1199, 0x6820) },	/* Sierra Wireless AirCard 875 */ 

	{ USB_DEVICE(0x1199, 0x0112) }, /* Sierra Wireless AirCard 580 */ 
	{ USB_DEVICE(0x0F3D, 0x0112) }, /* AirPrime/Sierra PC 5220 */

the lines from patch

{ USB_DEVICE(0x1199, 0x0112) }, /* Sierra Wireless AirCard 580 */ 
 	{ USB_DEVICE(0x0F3D, 0x0112) }, /* AirPrime/Sierra PC 5220 */ 
        { USB_DEVICE(0x16d8, 0x6280) }, /* Maxon BP3-USB 3G Bigpond Telstra */

Andto this section
 MODULE_DEVICE_TABLE(usb, id_table); 

static struct usb_device_id id_table_1port [] = { 
	{ USB_DEVICE(0x1199, 0x0112) }, /* Sierra Wireless AirCard 580 */ 
	{ USB_DEVICE(0x0F3D, 0x0112) }, /* AirPrime/Sierra PC 5220 */ 
        { USB_DEVICE(0x1199, 0x6804) },	/* Sierra Wireless MC8755 for Europe */ 
 	{ USB_DEVICE(0x1199, 0x6812) },	/* Sierra Wireless MC8775 */ 
 	{ USB_DEVICE(0x1199, 0x6820) },	/* Sierra Wireless AirCard 875 */

This line from patch

 { USB_DEVICE(0x16d8, 0x6280) }, /* Maxon BP3-USB 3G Bigpond Telstra */

            Save and exit Patch now complete 
We can now install the driver
# sudo cd /sierra directory

# make
# make install

Reboot and the driver should connect to the modem which in my system is /dev/ttyUSB1
We now extract the pppfile to /etc/ppp/peers
this is a copy of the files i use to connect with pon gsm
/etc/ppp/peers/gsm

-detach

lcp-echo-failure 0

/dev/ttyUSB1

115200

debug

defaultroute

#usepeerdns



#ipcp-no-address

#ipcp-no-addresses

ipcp-max-failure 4

ipcp-accept-local

ipcp-accept-remote



# AUTHENTICATION

# If noauth works, use that, otherwise you have to pass

# the user name and password. This is an example of a

# standard Cingular user/pw combo



#noauth

user [email]sharkenew@bigpond.com[/email]

password  ENTER YOUR BIGPOND PASSWORD HERE


crtscts

lock

connect '/usr/sbin/chat -v -t6 -f /etc/ppp/peers/gsm_chat'


/etc/ppp/peers/gsm_chat

# Connection script for Sierra Wireless GSM/UMTS modems

# Note: This demo script is setup to work on the Cingular EDGE network

#

SAY 'Starting Sierra Wireless GSM connect script...\n'

SAY '\n'



#######################################

SAY 'Setting the abort string\n'

SAY '\n'

# Abort String ------------------------------

ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT 'NO CARRIER' ABORT DELAYED



#######################################

SAY 'Initializing modem\n'

# Modem Initialization 

'' AT

OK ATZ



#######################################

SAY '\n'

SAY     'Setting APN\n'

# Access Point Name (APN) 

# Incorrect APN or CGDCONT can often cause errors in connection.

# Below are a bunch of different popular APNs



#REG:\s1 AT+cgdcont=1,"IP","proxy"

#OK     'AT+CGDCONT=0,"IP","proxy"'

#OK     'AT+CGDCONT=1,"IP","proxy"'

#OK     'AT+CGDCONT=2,"IP","proxy"'

#OK     'AT+CGDCONT=0,"IP","ISP.CINGULAR"'

OK     'AT+CGDCONT=1,"IP","TELSTRA.BIGPOND"'

#OK     'AT+CGDCONT=2,"IP","ISP.CINGULAR"'



#######################################

SAY '\n'

SAY     'Dialing...\n'

# Dial the ISP, this is the common Cingular dial string



OK ATD*99#

CONNECT ''
Thats it mission accomplished and hopefully your system wont self distruct in 60
 seconds

---

### Post by rosco99 on 2007-06-30
Hey Sharke,Should this /etc/peers/gsm_chat be /etc/ppp/peers/gsm_chat?
Rosco99

---

### Post by sharke on 2007-06-30
Rosco99
Yes thats should be /etc/ppp/peers/gsm-chat

And here is my files without the cingular junk
/etc/ppp/peers/gsm

-detach

lcp-echo-failure 0

/dev/ttyUSB1

115200

debug

defaultroute

usepeerdns



#ipcp-no-address

#ipcp-no-addresses

ipcp-max-failure 4

ipcp-accept-local

ipcp-accept-remote



# AUTHENTICATION

# If noauth works, use that, otherwise you have to pass

# the user name and password. This is an example of a

# standard bigpond user/pw combo



noauth

user [email]sharkenew@bigpond.com[/email]

password ********* Enter Your Password



crtscts

lock

connect '/usr/sbin/chat -v -t6 -f /etc/ppp/peers/gsm_chat'

And
/etc/ppp/peers/gsm-chat


# Connection script for Sierra Wireless GSM/UMTS modems
# Note: This demo script is setup to work on the bigpond network
#
SAY 'Starting Sierra Wireless GSM connect script...\n'
SAY '\n'

#######################################
SAY 'Setting the abort string\n'
SAY '\n'
# Abort String ------------------------------
ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT 'NO CARRIER' ABORT DELAYED

#######################################
SAY 'Initializing modem\n'
# Modem Initialization 
'' AT
OK ATZ

#######################################
SAY '\n'
SAY     'Setting APN\n'
# Access Point Name (APN) 
# Incorrect APN or CGDCONT can often cause errors in connection.
# Below are a bunch of different popular APNs


OK     'AT+CGDCONT=2,"IP","TELSTRA.BIGPOND"'

#######################################
SAY '\n'
SAY     'Dialing...\n'
# Dial the ISP, this is the common Cingular dial string

OK ATD*99#
CONNECT ''

Regards
Sharke

---

### Post by rosco99 on 2007-07-01
Hey Sharke,
In the line
# cd <directory of source>
# tar &#8211;zxf sierra.v.X.Y.Z.tar.gz
# cd sierra.v.X.Y.Z
What was the directory you put it in.
Also are v.X.Y.Z the actual figures you put in or do you use sierra.v.1.0.3 as downloaded?
Also when you
Save and exit Patch now complete
We can now install the driver
# sudo cd /sierra directory

# make
# make install
what was the sierra directory?
Do you have to put a file name after make  & make install?---This is not working for me.
Rosco

---

### Post by sharke on 2007-07-01
cd <directory of source> = cd to where you downloaded siera to . In my case cd Desktop/sierra.v.1.0.6.tar.gz
Then
tar -zxf sierra.v.1.0.6.tar,gz

This will create a folder called sierra.v.1.0.6 which has all the files you need.
open the sierra .c in a text editor and add the patch
This is my patched source file showing the bit where i have patched'
sierra.c
/*
  USB Driver for Sierra Wireless

  Copyright (C) 2006  Kevin Lloyd <linux@sierrawireless.com>

  IMPORTANT DISCLAIMER: This driver is not commercially supported by
  Sierra Wireless. Use at your own risk.

  This driver is free software; you can redistribute it and/or modify
  it under the terms of Version 2 of the GNU General Public License as
  published by the Free Software Foundation.

  Portions based on the option driver by Matthias Urlichs <smurf@smurf.noris.de>
  Whom based his on the Keyspan driver by Hugh Blemings <hugh@blemings.org>

  History:
v.1.0.6:
 klloyd
 Added more devices and added Vendor Specific USB message to make sure
 that devices are in D0 state when they start. This is very important for
 MC5720 and EM5625 modules that go between Windows and Non-Windows 
 machines.
v.1.0.5:
 Greg KH
 This saves over 30 lines and fixes a warning from sparse and allows
 debugging to work dynamically like all other usb-serial drivers.
 klloyd
 Changed versioning to v.x.y.z
v.1.04:
 klloyd
 Adds significant throughput increase to the Sierra driver (uses multiple
 urgs for download link). This patch also updates the current sierra.c 
 driver so that it supports both 3-port Sierra devices and 1-port legacy
 devices and removes Sierra's references in other related files (Kconfig
 and airprime.c).
v.1.03
 klloyd
 Adds DTR line control support and impliments urb control.
*/

#define DRIVER_VERSION "v.1.0.6"
#define DRIVER_AUTHOR "Kevin Lloyd <linux@sierrawireless.com>"
#define DRIVER_DESC "USB Driver for Sierra Wireless USB modems"

#include <linux/kernel.h>
#include <linux/jiffies.h>
#include <linux/errno.h>
#include <linux/tty.h>
#include <linux/tty_flip.h>
#include <linux/module.h>
#include <linux/usb.h>
#include <linux/usb/serial.h>


static struct usb_device_id id_table [] = {
	{ USB_DEVICE(0x1199, 0x0017) },	/* Sierra Wireless EM5625 */
	{ USB_DEVICE(0x1199, 0x0018) },	/* Sierra Wireless MC5720 */
	{ USB_DEVICE(0x1199, 0x0218) },	/* Sierra Wireless MC5720 */
	{ USB_DEVICE(0x1199, 0x0020) },	/* Sierra Wireless MC5725 */
	{ USB_DEVICE(0x1199, 0x0019) },	/* Sierra Wireless AirCard 595 */
	{ USB_DEVICE(0x1199, 0x0021) },	/* Sierra Wireless AirCard 597E */
	{ USB_DEVICE(0x1199, 0x0120) },	/* Sierra Wireless USB Dongle 595U*/
	
	{ USB_DEVICE(0x1199, 0x6802) },	/* Sierra Wireless MC8755 */
	{ USB_DEVICE(0x1199, 0x6804) },	/* Sierra Wireless MC8755 */
	{ USB_DEVICE(0x1199, 0x6803) },	/* Sierra Wireless MC8765 */
	{ USB_DEVICE(0x1199, 0x6812) },	/* Sierra Wireless MC8775 */
	{ USB_DEVICE(0x1199, 0x6820) },	/* Sierra Wireless AirCard 875 */

	{ USB_DEVICE(0x1199, 0x0112) }, /* Sierra Wireless AirCard 580 */
	{ USB_DEVICE(0x0F3D, 0x0112) }, /* AirPrime/Sierra PC 5220 */
        { USB_DEVICE(0x1199, 0x0112) }, /* Sierra Wireless AirCard 580 */
 	{ USB_DEVICE(0x0F3D, 0x0112) }, /* AirPrime/Sierra PC 5220 */
	{ USB_DEVICE(0x16d8, 0x6280) }, /* Maxon BP3-USB 3G Bigpond Telstra */  

 	
	{ }
};
MODULE_DEVICE_TABLE(usb, id_table);

static struct usb_device_id id_table_1port [] = {
	{ USB_DEVICE(0x1199, 0x0112) }, /* Sierra Wireless AirCard 580 */
	{ USB_DEVICE(0x0F3D, 0x0112) }, /* AirPrime/Sierra PC 5220 */
        { USB_DEVICE(0x1199, 0x6804) },	/* Sierra Wireless MC8755 for Europe */
 	{ USB_DEVICE(0x1199, 0x6812) },	/* Sierra Wireless MC8775 */
 	{ USB_DEVICE(0x1199, 0x6820) },	/* Sierra Wireless AirCard 875 */
	{ USB_DEVICE(0x16d8, 0x6280) }, /* Maxon BP3-USB 3G Bigpond Telstra */
	{ }
};

You add the lines that are not in your existing sierra.c

Regards
Sharke

---

### Post by rosco99 on 2007-07-01
Hi Sharke,
I could not get the tar command to work, so I right clicked on the file and extracted it which produced the file sierra.v.106. I then edited sierra.c. I also reproduced the gsm and gsm-chat files.
Which directory is sierra.v.1.0.6 meant to finish up in?
When I did pon gsm I got an error related to the screts file (I can't remember the exact wording and the printer wouldn't print the terminal screen).
I wonder if doing tar puts the file in the drivers folder whereas extracting just puts it on the desk top.
If it needs to be in the drivers file how will i get the priveleges to allow me to do it?
Thank you,
Ross

---

### Post by sharke on 2007-07-02
rosco99
After patching the sierra,c file   cd to sierra.v.106 yours may be slightly different
In terminal 
make
after this completes with no errors
sudo make install
Then if you take a look at dmesg you should see the modem connected to the sierra module
Make sure you copy the ppp files into /etc/ppp/peers
Regards
Sharke

---

### Post by rosco99 on 2007-07-02
Hey Sharke,
Which directory does sierra.c occupy?
Ross

---

### Post by sharke on 2007-07-02
sierra.c should be in the sierra.v.1.0.6 folder and is only used by the make command to build the module dont move it.
Regards
Sharke

---

### Post by rosco99 on 2007-07-02
OK, so it doesn't matter where the sierra v.1.0.6 is located--the make command puts it in the corrct place?

---

### Post by sharke on 2007-07-02
not quite rhe make command builds the module & the make install installs it in correct place.
Regards
Sharke
PS
Did you get connected with usb-serial

---

### Post by rosco99 on 2007-07-02
I got a series of errors and warnings when doing  make. They are errors 103,136,138,143,145,153,154,162,and 167. Presume I mucked up the editing when adding the two extra lines.
Would it be possible for me to add your file?
Thank you,
Ross

---

### Post by sharke on 2007-07-02
Hereis the complete siera .c with patch added.
/*
  USB Driver for Sierra Wireless

  Copyright (C) 2006  Kevin Lloyd <linux@sierrawireless.com>

  IMPORTANT DISCLAIMER: This driver is not commercially supported by
  Sierra Wireless. Use at your own risk.

  This driver is free software; you can redistribute it and/or modify
  it under the terms of Version 2 of the GNU General Public License as
  published by the Free Software Foundation.

  Portions based on the option driver by Matthias Urlichs <smurf@smurf.noris.de>
  Whom based his on the Keyspan driver by Hugh Blemings <hugh@blemings.org>

  History:
v.1.0.6:
 klloyd
 Added more devices and added Vendor Specific USB message to make sure
 that devices are in D0 state when they start. This is very important for
 MC5720 and EM5625 modules that go between Windows and Non-Windows 
 machines.
v.1.0.5:
 Greg KH
 This saves over 30 lines and fixes a warning from sparse and allows
 debugging to work dynamically like all other usb-serial drivers.
 klloyd
 Changed versioning to v.x.y.z
v.1.04:
 klloyd
 Adds significant throughput increase to the Sierra driver (uses multiple
 urgs for download link). This patch also updates the current sierra.c 
 driver so that it supports both 3-port Sierra devices and 1-port legacy
 devices and removes Sierra's references in other related files (Kconfig
 and airprime.c).
v.1.03
 klloyd
 Adds DTR line control support and impliments urb control.
*/

#define DRIVER_VERSION "v.1.0.6"
#define DRIVER_AUTHOR "Kevin Lloyd <linux@sierrawireless.com>"
#define DRIVER_DESC "USB Driver for Sierra Wireless USB modems"

#include <linux/kernel.h>
#include <linux/jiffies.h>
#include <linux/errno.h>
#include <linux/tty.h>
#include <linux/tty_flip.h>
#include <linux/module.h>
#include <linux/usb.h>
#include <linux/usb/serial.h>


static struct usb_device_id id_table [] = {
	{ USB_DEVICE(0x1199, 0x0017) },	/* Sierra Wireless EM5625 */
	{ USB_DEVICE(0x1199, 0x0018) },	/* Sierra Wireless MC5720 */
	{ USB_DEVICE(0x1199, 0x0218) },	/* Sierra Wireless MC5720 */
	{ USB_DEVICE(0x1199, 0x0020) },	/* Sierra Wireless MC5725 */
	{ USB_DEVICE(0x1199, 0x0019) },	/* Sierra Wireless AirCard 595 */
	{ USB_DEVICE(0x1199, 0x0021) },	/* Sierra Wireless AirCard 597E */
	{ USB_DEVICE(0x1199, 0x0120) },	/* Sierra Wireless USB Dongle 595U*/
	
	{ USB_DEVICE(0x1199, 0x6802) },	/* Sierra Wireless MC8755 */
	{ USB_DEVICE(0x1199, 0x6804) },	/* Sierra Wireless MC8755 */
	{ USB_DEVICE(0x1199, 0x6803) },	/* Sierra Wireless MC8765 */
	{ USB_DEVICE(0x1199, 0x6812) },	/* Sierra Wireless MC8775 */
	{ USB_DEVICE(0x1199, 0x6820) },	/* Sierra Wireless AirCard 875 */

	{ USB_DEVICE(0x1199, 0x0112) }, /* Sierra Wireless AirCard 580 */
	{ USB_DEVICE(0x0F3D, 0x0112) }, /* AirPrime/Sierra PC 5220 */
        { USB_DEVICE(0x1199, 0x0112) }, /* Sierra Wireless AirCard 580 */
 	{ USB_DEVICE(0x0F3D, 0x0112) }, /* AirPrime/Sierra PC 5220 */
	{ USB_DEVICE(0x16d8, 0x6280) }, /* Maxon BP3-USB 3G Bigpond Telstra */
 	
	{ }
};
MODULE_DEVICE_TABLE(usb, id_table);

static struct usb_device_id id_table_1port [] = {
	{ USB_DEVICE(0x1199, 0x0112) }, /* Sierra Wireless AirCard 580 */
	{ USB_DEVICE(0x0F3D, 0x0112) }, /* AirPrime/Sierra PC 5220 */
        { USB_DEVICE(0x1199, 0x6804) },	/* Sierra Wireless MC8755 for Europe */
 	{ USB_DEVICE(0x1199, 0x6812) },	/* Sierra Wireless MC8775 */
 	{ USB_DEVICE(0x1199, 0x6820) },	/* Sierra Wireless AirCard 875 */
	{ USB_DEVICE(0x16d8, 0x6280) }, /* Maxon BP3-USB 3G Bigpond Telstra */
	{ }
};

static struct usb_device_id id_table_3port [] = {
	{ USB_DEVICE(0x1199, 0x0017) },	/* Sierra Wireless EM5625 */
	{ USB_DEVICE(0x1199, 0x0018) },	/* Sierra Wireless MC5720 */
	{ USB_DEVICE(0x1199, 0x0218) },	/* Sierra Wireless MC5720 */
	{ USB_DEVICE(0x1199, 0x0020) },	/* Sierra Wireless MC5725 */
	{ USB_DEVICE(0x1199, 0x0019) },	/* Sierra Wireless AirCard 595 */
	{ USB_DEVICE(0x1199, 0x0021) },	/* Sierra Wireless AirCard 597E */
	{ USB_DEVICE(0x1199, 0x0120) },	/* Sierra Wireless USB Dongle 595U*/
	
	{ USB_DEVICE(0x1199, 0x6802) },	/* Sierra Wireless MC8755 */
	{ USB_DEVICE(0x1199, 0x6804) },	/* Sierra Wireless MC8755 */
	{ USB_DEVICE(0x1199, 0x6803) },	/* Sierra Wireless MC8765 */
	{ USB_DEVICE(0x1199, 0x6812) },	/* Sierra Wireless MC8775 */
	{ USB_DEVICE(0x1199, 0x6820) },	/* Sierra Wireless AirCard 875 */
	{ }
};

static struct usb_driver sierra_driver = {
	.name       = "sierra",
	.probe      = usb_serial_probe,
	.disconnect = usb_serial_disconnect,
	.id_table   = id_table,
	.no_dynamic_id = 	1,
};


static int debug;

/* per port private data */
#define N_IN_URB	4
#define N_OUT_URB	1
#define IN_BUFLEN	4096
#define OUT_BUFLEN	128

struct sierra_port_private {
	/* Input endpoints and buffer for this port */
	struct urb *in_urbs[N_IN_URB];
	char in_buffer[N_IN_URB][IN_BUFLEN];
	/* Output endpoints and buffer for this port */
	struct urb *out_urbs[N_OUT_URB];
	char out_buffer[N_OUT_URB][OUT_BUFLEN];

	/* Settings for the port */
	int rts_state;	/* Handshaking pins (outputs) */
	int dtr_state;
	int cts_state;	/* Handshaking pins (inputs) */
	int dsr_state;
	int dcd_state;
	int ri_state;

	unsigned long tx_start_time[N_OUT_URB];
};

static int sierra_send_setup(struct usb_serial_port *port)
{
	struct usb_serial *serial = port->serial;
	struct sierra_port_private *portdata;

	dbg("%s", __FUNCTION__);

	portdata = usb_get_serial_port_data(port);

	if (port->tty) {
		int val = 0;

		if (portdata->dtr_state)
			val |= 0x01;
		if (portdata->rts_state)
			val |= 0x02;

		return usb_control_msg(serial->dev,
				usb_rcvctrlpipe(serial->dev, 0),
				0x22,0x21,val,0,NULL,0,USB_CTRL_SET_TIMEOUT);

	}

	return 0;
}

static void sierra_rx_throttle(struct usb_serial_port *port)
{
	dbg("%s", __FUNCTION__);
}

static void sierra_rx_unthrottle(struct usb_serial_port *port)
{
	dbg("%s", __FUNCTION__);
}

static void sierra_break_ctl(struct usb_serial_port *port, int break_state)
{
	/* Unfortunately, I don't know how to send a break */
	dbg("%s", __FUNCTION__);
}

static void sierra_set_termios(struct usb_serial_port *port,
			struct ktermios *old_termios)
{
	dbg("%s", __FUNCTION__);

	sierra_send_setup(port);
}

static int sierra_tiocmget(struct usb_serial_port *port, struct file *file)
{
	unsigned int value;
	struct sierra_port_private *portdata;

	portdata = usb_get_serial_port_data(port);

	value = ((portdata->rts_state) ? TIOCM_RTS : 0) |
		((portdata->dtr_state) ? TIOCM_DTR : 0) |
		((portdata->cts_state) ? TIOCM_CTS : 0) |
		((portdata->dsr_state) ? TIOCM_DSR : 0) |
		((portdata->dcd_state) ? TIOCM_CAR : 0) |
		((portdata->ri_state) ? TIOCM_RNG : 0);

	return value;
}

static int sierra_tiocmset(struct usb_serial_port *port, struct file *file,
			unsigned int set, unsigned int clear)
{
	struct sierra_port_private *portdata;

	portdata = usb_get_serial_port_data(port);

	if (set & TIOCM_RTS)
		portdata->rts_state = 1;
	if (set & TIOCM_DTR)
		portdata->dtr_state = 1;

	if (clear & TIOCM_RTS)
		portdata->rts_state = 0;
	if (clear & TIOCM_DTR)
		portdata->dtr_state = 0;
	return sierra_send_setup(port);
}

static int sierra_ioctl(struct usb_serial_port *port, struct file *file,
			unsigned int cmd, unsigned long arg)
{
	return -ENOIOCTLCMD;
}

/* Write */
static int sierra_write(struct usb_serial_port *port,
			const unsigned char *buf, int count)
{
	struct sierra_port_private *portdata;
	int i;
	int left, todo;
	struct urb *this_urb = NULL; /* spurious */
	int err;

	portdata = usb_get_serial_port_data(port);

	dbg("%s: write (%d chars)", __FUNCTION__, count);

	i = 0;
	left = count;
	for (i=0; left > 0 && i < N_OUT_URB; i++) {
		todo = left;
		if (todo > OUT_BUFLEN)
			todo = OUT_BUFLEN;

		this_urb = portdata->out_urbs[i];
		if (this_urb->status == -EINPROGRESS) {
			if (time_before(jiffies,
					portdata->tx_start_time[i] + 10 * HZ))
				continue;
			usb_unlink_urb(this_urb);
			continue;
		}
		if (this_urb->status != 0)
			dbg("usb_write %p failed (err=%d)",
				this_urb, this_urb->status);

		dbg("%s: endpoint %d buf %d", __FUNCTION__,
			usb_pipeendpoint(this_urb->pipe), i);

		/* send the data */
		memcpy (this_urb->transfer_buffer, buf, todo);
		this_urb->transfer_buffer_length = todo;

		this_urb->dev = port->serial->dev;
		err = usb_submit_urb(this_urb, GFP_ATOMIC);
		if (err) {
			dbg("usb_submit_urb %p (write bulk) failed "
				"(%d, has %d)", this_urb,
				err, this_urb->status);
			continue;
		}
		portdata->tx_start_time[i] = jiffies;
		buf += todo;
		left -= todo;
	}

	count -= left;
	dbg("%s: wrote (did %d)", __FUNCTION__, count);
	return count;
}

static void sierra_indat_callback(struct urb *urb)
{
	int err;
	int endpoint;
	struct usb_serial_port *port;
	struct tty_struct *tty;
	unsigned char *data = urb->transfer_buffer;

	dbg("%s: %p", __FUNCTION__, urb);

	endpoint = usb_pipeendpoint(urb->pipe);
	port = (struct usb_serial_port *) urb->context;

	if (urb->status) {
		dbg("%s: nonzero status: %d on endpoint %02x.",
		    __FUNCTION__, urb->status, endpoint);
	} else {
		tty = port->tty;
		if (urb->actual_length) {
			tty_buffer_request_room(tty, urb->actual_length);
			tty_insert_flip_string(tty, data, urb->actual_length);
			tty_flip_buffer_push(tty);
		} else {
			dbg("%s: empty read urb received", __FUNCTION__);
		}

		/* Resubmit urb so we continue receiving */
		if (port->open_count && urb->status != -ESHUTDOWN) {
			err = usb_submit_urb(urb, GFP_ATOMIC);
			if (err)
				printk(KERN_ERR "%s: resubmit read urb failed. "
					"(%d)", __FUNCTION__, err);
		}
	}
	return;
}

static void sierra_outdat_callback(struct urb *urb)
{
	struct usb_serial_port *port;

	dbg("%s", __FUNCTION__);

	port = (struct usb_serial_port *) urb->context;

	usb_serial_port_softint(port);
}

static void sierra_instat_callback(struct urb *urb)
{
	int err;
	struct usb_serial_port *port = (struct usb_serial_port *) urb->context;
	struct sierra_port_private *portdata = usb_get_serial_port_data(port);
	struct usb_serial *serial = port->serial;

	dbg("%s", __FUNCTION__);
	dbg("%s: urb %p port %p has data %p", __FUNCTION__,urb,port,portdata);

	if (urb->status == 0) {
		struct usb_ctrlrequest *req_pkt =
				(struct usb_ctrlrequest *)urb->transfer_buffer;

		if (!req_pkt) {
			dbg("%s: NULL req_pkt\n", __FUNCTION__);
			return;
		}
		if ((req_pkt->bRequestType == 0xA1) &&
				(req_pkt->bRequest == 0x20)) {
			int old_dcd_state;
			unsigned char signals = *((unsigned char *)
					urb->transfer_buffer +
					sizeof(struct usb_ctrlrequest));

			dbg("%s: signal x%x", __FUNCTION__, signals);

			old_dcd_state = portdata->dcd_state;
			portdata->cts_state = 1;
			portdata->dcd_state = ((signals & 0x01) ? 1 : 0);
			portdata->dsr_state = ((signals & 0x02) ? 1 : 0);
			portdata->ri_state = ((signals & 0x08) ? 1 : 0);

			if (port->tty && !C_CLOCAL(port->tty) &&
					old_dcd_state && !portdata->dcd_state)
				tty_hangup(port->tty);
		} else {
			dbg("%s: type %x req %x", __FUNCTION__,
				req_pkt->bRequestType,req_pkt->bRequest);
		}
	} else
		dbg("%s: error %d", __FUNCTION__, urb->status);

	/* Resubmit urb so we continue receiving IRQ data */
	if (urb->status != -ESHUTDOWN) {
		urb->dev = serial->dev;
		err = usb_submit_urb(urb, GFP_ATOMIC);
		if (err)
			dbg("%s: resubmit intr urb failed. (%d)",
				__FUNCTION__, err);
	}
}

static int sierra_write_room(struct usb_serial_port *port)
{
	struct sierra_port_private *portdata;
	int i;
	int data_len = 0;
	struct urb *this_urb;

	portdata = usb_get_serial_port_data(port);

	for (i=0; i < N_OUT_URB; i++) {
		this_urb = portdata->out_urbs[i];
		if (this_urb && this_urb->status != -EINPROGRESS)
			data_len += OUT_BUFLEN;
	}

	dbg("%s: %d", __FUNCTION__, data_len);
	return data_len;
}

static int sierra_chars_in_buffer(struct usb_serial_port *port)
{
	struct sierra_port_private *portdata;
	int i;
	int data_len = 0;
	struct urb *this_urb;

	portdata = usb_get_serial_port_data(port);

	for (i=0; i < N_OUT_URB; i++) {
		this_urb = portdata->out_urbs[i];
		if (this_urb && this_urb->status == -EINPROGRESS)
			data_len += this_urb->transfer_buffer_length;
	}
	dbg("%s: %d", __FUNCTION__, data_len);
	return data_len;
}

static int sierra_open(struct usb_serial_port *port, struct file *filp)
{
	struct sierra_port_private *portdata;
	struct usb_serial *serial = port->serial;
	int i, err;
	struct urb *urb;
	int result;
	unsigned long setmode = 0x0000; //Set mode to D0

	portdata = usb_get_serial_port_data(port);

	dbg("%s", __FUNCTION__);

	/* Set some sane defaults */
	portdata->rts_state = 1;
	portdata->dtr_state = 1;

	/* Reset low level data toggle and start reading from endpoints */
	for (i = 0; i < N_IN_URB; i++) {
		urb = portdata->in_urbs[i];
		if (! urb)
			continue;
		if (urb->dev != serial->dev) {
			dbg("%s: dev %p != %p", __FUNCTION__,
				urb->dev, serial->dev);
			continue;
		}

		/*
		 * make sure endpoint data toggle is synchronized with the
		 * device
		 */
		usb_clear_halt(urb->dev, urb->pipe);

		err = usb_submit_urb(urb, GFP_KERNEL);
		if (err) {
			dbg("%s: submit urb %d failed (%d) %d",
				__FUNCTION__, i, err,
				urb->transfer_buffer_length);
		}
	}

	/* Reset low level data toggle on out endpoints */
	for (i = 0; i < N_OUT_URB; i++) {
		urb = portdata->out_urbs[i];
		if (! urb)
			continue;
		urb->dev = serial->dev;
		/* usb_settoggle(urb->dev, usb_pipeendpoint(urb->pipe),
				usb_pipeout(urb->pipe), 0); */
	}

	port->tty->low_latency = 1;

	//set mode to D0
	result = usb_control_msg(serial->dev,
			usb_rcvctrlpipe(serial->dev, 0),
			0x00,0x40,setmode,0,NULL,0,USB_CTRL_SET_TIMEOUT);

	sierra_send_setup(port);

	return (0);
}

static inline void stop_urb(struct urb *urb)
{
	if (urb && urb->status == -EINPROGRESS)
		usb_kill_urb(urb);
}

static void sierra_close(struct usb_serial_port *port, struct file *filp)
{
	int i;
	struct usb_serial *serial = port->serial;
	struct sierra_port_private *portdata;

	dbg("%s", __FUNCTION__);
	portdata = usb_get_serial_port_data(port);

	portdata->rts_state = 0;
	portdata->dtr_state = 0;

	if (serial->dev) {
		sierra_send_setup(port);

		/* Stop reading/writing urbs */
		for (i = 0; i < N_IN_URB; i++)
			stop_urb(portdata->in_urbs[i]);
		for (i = 0; i < N_OUT_URB; i++)
			stop_urb(portdata->out_urbs[i]);
	}
	port->tty = NULL;
}

/* Helper functions used by sierra_setup_urbs */
static struct urb *sierra_setup_urb(struct usb_serial *serial, int endpoint,
				    int dir, void *ctx, char *buf, int len,
				    usb_complete_t callback)
{
	struct urb *urb;

	if (endpoint == -1)
		return NULL;		/* endpoint not needed */

	urb = usb_alloc_urb(0, GFP_KERNEL);		/* No ISO */
	if (urb == NULL) {
		dbg("%s: alloc for endpoint %d failed.", __FUNCTION__, endpoint);
		return NULL;
	}

		/* Fill URB using supplied data. */
	usb_fill_bulk_urb(urb, serial->dev,
		      usb_sndbulkpipe(serial->dev, endpoint) | dir,
		      buf, len, callback, ctx);

	return urb;
}

/* Setup urbs */
static void sierra_setup_urbs(struct usb_serial *serial)
{
	int i,j;
	struct usb_serial_port *port;
	struct sierra_port_private *portdata;

	dbg("%s", __FUNCTION__);

	for (i = 0; i < serial->num_ports; i++) {
		port = serial->port[i];
		portdata = usb_get_serial_port_data(port);

	/* Do indat endpoints first */
		for (j = 0; j < N_IN_URB; ++j) {
			portdata->in_urbs[j] = sierra_setup_urb (serial,
                  	port->bulk_in_endpointAddress, USB_DIR_IN, port,
                  	portdata->in_buffer[j], IN_BUFLEN, sierra_indat_callback);
		}

		/* outdat endpoints */
		for (j = 0; j < N_OUT_URB; ++j) {
			portdata->out_urbs[j] = sierra_setup_urb (serial,
                  	port->bulk_out_endpointAddress, USB_DIR_OUT, port,
                  	portdata->out_buffer[j], OUT_BUFLEN, sierra_outdat_callback);
		}
	}
}

static int sierra_startup(struct usb_serial *serial)
{
	int i, err;
	struct usb_serial_port *port;
	struct sierra_port_private *portdata;

	dbg("%s", __FUNCTION__);

	/* Now setup per port private data */
	for (i = 0; i < serial->num_ports; i++) {
		port = serial->port[i];
		portdata = kzalloc(sizeof(*portdata), GFP_KERNEL);
		if (!portdata) {
			dbg("%s: kmalloc for sierra_port_private (%d) failed!.",
					__FUNCTION__, i);
			return (1);
		}

		usb_set_serial_port_data(port, portdata);

		if (! port->interrupt_in_urb)
			continue;
		err = usb_submit_urb(port->interrupt_in_urb, GFP_KERNEL);
		if (err)
			dbg("%s: submit irq_in urb failed %d",
				__FUNCTION__, err);
	}

	sierra_setup_urbs(serial);

	return (0);
}

static void sierra_shutdown(struct usb_serial *serial)
{
	int i, j;
	struct usb_serial_port *port;
	struct sierra_port_private *portdata;

	dbg("%s", __FUNCTION__);

	/* Stop reading/writing urbs */
	for (i = 0; i < serial->num_ports; ++i) {
		port = serial->port[i];
		portdata = usb_get_serial_port_data(port);
		for (j = 0; j < N_IN_URB; j++)
			stop_urb(portdata->in_urbs[j]);
		for (j = 0; j < N_OUT_URB; j++)
			stop_urb(portdata->out_urbs[j]);
	}

	/* Now free them */
	for (i = 0; i < serial->num_ports; ++i) {
		port = serial->port[i];
		portdata = usb_get_serial_port_data(port);

		for (j = 0; j < N_IN_URB; j++) {
			if (portdata->in_urbs[j]) {
				usb_free_urb(portdata->in_urbs[j]);
				portdata->in_urbs[j] = NULL;
			}
		}
		for (j = 0; j < N_OUT_URB; j++) {
			if (portdata->out_urbs[j]) {
				usb_free_urb(portdata->out_urbs[j]);
				portdata->out_urbs[j] = NULL;
			}
		}
	}

	/* Now free per port private data */
	for (i = 0; i < serial->num_ports; i++) {
		port = serial->port[i];
		kfree(usb_get_serial_port_data(port));
	}
}

static struct usb_serial_driver sierra_1port_device = {
	.driver = {
		.owner =	THIS_MODULE,
		.name =		"sierra1",
	},
	.description       = "Sierra USB modem (1 port)",
	.id_table          = id_table_1port,
	.num_interrupt_in  = NUM_DONT_CARE,
	.num_bulk_in       = 1,
	.num_bulk_out      = 1,
	.num_ports         = 1,
	.open              = sierra_open,
	.close             = sierra_close,
	.write             = sierra_write,
	.write_room        = sierra_write_room,
	.chars_in_buffer   = sierra_chars_in_buffer,
	.throttle          = sierra_rx_throttle,
	.unthrottle        = sierra_rx_unthrottle,
	.ioctl             = sierra_ioctl,
	.set_termios       = sierra_set_termios,
	.break_ctl         = sierra_break_ctl,
	.tiocmget          = sierra_tiocmget,
	.tiocmset          = sierra_tiocmset,
	.attach            = sierra_startup,
	.shutdown          = sierra_shutdown,
	.read_int_callback = sierra_instat_callback,
};

static struct usb_serial_driver sierra_3port_device = {
	.driver = {
		.owner =	THIS_MODULE,
		.name =		"sierra3",
	},
	.description       = "Sierra USB modem (3 port)",
	.id_table          = id_table_3port,
	.num_interrupt_in  = NUM_DONT_CARE,
	.num_bulk_in       = 3,
	.num_bulk_out      = 3,
	.num_ports         = 3,
	.open              = sierra_open,
	.close             = sierra_close,
	.write             = sierra_write,
	.write_room        = sierra_write_room,
	.chars_in_buffer   = sierra_chars_in_buffer,
	.throttle          = sierra_rx_throttle,
	.unthrottle        = sierra_rx_unthrottle,
	.ioctl             = sierra_ioctl,
	.set_termios       = sierra_set_termios,
	.break_ctl         = sierra_break_ctl,
	.tiocmget          = sierra_tiocmget,
	.tiocmset          = sierra_tiocmset,
	.attach            = sierra_startup,
	.shutdown          = sierra_shutdown,
	.read_int_callback = sierra_instat_callback,
};

/* Functions used by new usb-serial code. */
static int __init sierra_init(void)
{
	int retval;
	retval = usb_serial_register(&sierra_1port_device);
	if (retval)
		goto failed_1port_device_register;
	retval = usb_serial_register(&sierra_3port_device);
	if (retval)
		goto failed_3port_device_register;


	retval = usb_register(&sierra_driver);
	if (retval)
		goto failed_driver_register;

	info(DRIVER_DESC ": " DRIVER_VERSION);

	return 0;

failed_driver_register:
	usb_serial_deregister(&sierra_3port_device);
failed_3port_device_register:
	usb_serial_deregister(&sierra_1port_device);
failed_1port_device_register:
	return retval;
}

static void __exit sierra_exit(void)
{
	usb_deregister (&sierra_driver);
	usb_serial_deregister(&sierra_1port_device);
	usb_serial_deregister(&sierra_3port_device);
}

module_init(sierra_init);
module_exit(sierra_exit);

MODULE_AUTHOR(DRIVER_AUTHOR);
MODULE_DESCRIPTION(DRIVER_DESC);
MODULE_VERSION(DRIVER_VERSION);
MODULE_LICENSE("GPL");

#ifdef CONFIG_USB_DEBUG
module_param(debug, bool, S_IRUGO | S_IWUSR);
MODULE_PARM_DESC(debug, "Debug messages");
#endif

---

### Post by rosco99 on 2007-07-02
I still get too many errors. I  will have to solve the initial problem of doing the tar. Extracting must not put the correct files in place.
I placed a question in absolute beginners about that a couple of days ago but are still awaiting a reply.

---

### Post by sharke on 2007-07-02
rosco99
I dont think the problem is extracting i think maybe you dont have necessary compiling tools installed try sudo apt-get install build-essential and try make than make install again.
Regards
Sharke
PS did you get your modem working with the usb-serial

---

### Post by rosco99 on 2007-07-02
OK, I will try that tonight.
No, usb-serial still gives timeout error. Where I am located the signal is marginal and in windows it only gives one bar, but still works. I hope that Sierra wireless will work at home.
I used to be pretty competent in Windows dos and Basic but I am finding Linux a steep learning curve, particularly when I can't connect to the net with it. Previously I had isdn and I solved that problem in Linux. I upgraded to Wireless next G so I could use one service in 2 locations and in Windows it does work well. My aim is to run my HTPC under linux but I need the internet to obtain the programs.
Thanks for your continuing help.
Ross

---

### Post by sharke on 2007-07-03
Ross 
Try with the attached files . Downlooad to desktop right click on file sierra.v.1.0.6.tar.gz extract here.
In a terminal 
cd /home/jeff/Desktop/sierra.v.1.0.6  {ghange jeff to your username}

then

make

then

 sudo make install

 That is the module done now right click on ppp.tar.gz extract here ,
then i sudo nautilus and copy the files in ppp to /etc/ppp/peers

after doing this and editing the files with username you should be able to connect with pon gsm

Regards
Sharke

---

### Post by sharke on 2007-07-03
> **sharke said:**
> Ross 
Try with the attached files . Downlooad to desktop right click on file sierra.v.1.0.6.tar.gz extract here.
In a terminal 
cd /home/jeff/Desktop/sierra.v.1.0.6  {ghange jeff to your username}

then

make

then

 sudo make install

 That is the module done now right click on ppp.tar.gz extract here ,
then i sudo nautilus and copy the files in ppp to /etc/ppp/peers

after doing this and editing the files with username you should be able to connect with pon gsm

Regards
Sharke

Sorry ileft out edit your chap-secrets file with username & Password if not alreadt done.

Regards
Sharke

---

### Post by rosco99 on 2007-07-03
You are correct, I don't have the correct tools to make.
The build essentials is not avilable either.
I got a reply to the question I posted in Absolute beginners and it seems i need to upgrade my make command.
see-http://ubuntuforums.org/showthread.php?t=132477.
I get the same make errors in my dvd version of kubuntu 6.10 and suse 10.2.
I will try to overcome these hurdles then get back to Sierra.

---

### Post by sharke on 2007-07-04
rosco99
The make command in this instance is very simple. It only calls for 2 existing directorys.
/lib/modules/uname-r/build.
You may  edit the existing makefile in sierra to something like /lib/modules/2.6.20-16-generic/build
And
/lib/modules/2.6.20-16-generic/kernel/drivers/usb-serial

Regards 
sharke
Ps 
you can find kernel version by typing uname -r in terminal

---

### Post by rosco99 on 2007-07-04
Sharke,
I modified the makefile but still get the error 2 as before. The other person who had this problem (thread 13247) was advised to change the sources. Makefile assumes the kernel module is in /lib/modules/'uname-r'/   and the kernel source is located at /usr/src/linux.
How do I check that ?-- I don't know what to look for!!
There was also advice for the same problem installing madwifi and they were told
"Go to the  /boot directory and find a file config-uname-r. As root copy that to your kernel source directory as .config(usually '/usr/src/linux', its the same as  'lib/modules/uname-r'/build/'
Then also as root go to the source directory and prepare the source for the new module. Use the command 'make modules-prepare' "

Iam afraid I can't understand that (does it mean to copy "config-uname-r" to '/usr/src/linux'? --I tried that but I am not allowed.
A simple explanation would be greatly appreciated.
Regards,
Ross

---

### Post by sharke on 2007-07-04
Okay
i can see how this can be confusing so lets explain.
uname  -r is a console command so if you enter uname -r in a terminal and click enter your kernel version is shown. So you will not have a file called uname -r it is a way for the make to find your kernel version.
If you take a look in /lib/modules yuo should have a folder something like 2.6.20-16-generic this is the fojder that unam -r finds in the command.
In the make file  /lib/modules tells it what directory to use $(shell uname -r) tells make to isue command in shell to find kernel version in my system 2.6.20-16-generic build tells make where to find build files . therefor if you browse to /lib and open the modules folder then open the kernel version folder you must see a build folder for this to work
Hope this helps a little
basicly you do need to install build essentials to install the sierra module.

Regards
Sharke
Ps
You will also need  the linux headers which should br im /usr/src make sure you have the same version as your kernel you do not need kernel source.

---

### Post by sharke on 2007-07-04
Ross
do you recall pillbe from the nextg wireless post he now has the sierra module working and is getting 1.4mb downloads iamjealous i max at 250kbs
Regards
Sharke

---

### Post by rosco99 on 2007-07-04
Hey Sharke,
Yes I did see what pillbe had done. Fantastic.
He gave up on kubuntu and set up ubuntu.
I understand all these files now but can't find build-essentials.
I have managed to make (sierra) in Suse 10.2 but it doesn't have the pon and poff command and I can't see an equivalent of it.
I would have thought installing build-essentials would be similar in kubuntu and ubunto so perhaps someone could tell me how to do it.
Regards,
Ross
If all else fails I might get an Ubuntu dvd and install that.

---

### Post by sharke on 2007-07-05
My Mistake should be build-essential not essentials.
Regards
Sharke

---

### Post by Jussi01 on 2007-08-02
> **sharke said:**
> Ross 
Try with the attached files . Downlooad to desktop right click on file sierra.v.1.0.6.tar.gz extract here.
In a terminal 
cd /home/jeff/Desktop/sierra.v.1.0.6  {ghange jeff to your username}

then

make

then

 sudo make install

 That is the module done now right click on ppp.tar.gz extract here ,
then i sudo nautilus and copy the files in ppp to /etc/ppp/peers

after doing this and editing the files with username you should be able to connect with pon gsm

Regards
Sharke

Hi Sharke, 

I assume these files are the already patched ones? there is nothing more to do than what you have mentioned here? also is this the same with kubuntu? Do i need any additional packages? (other than build essential) ie. a dialer package?

---

### Post by sharke on 2007-08-02
Ross
Yes they are the patched files.
You should not have any problems with kubuntu if you do you can also get the sources for your kernel than patch the module in the sources and rebuild the kernel.
Regards
Sharke

---

### Post by rosco99 on 2007-08-18
Hey Sharke,
Just thought I would let you know ADSL has come to my rural property and Telstra gave me a good deal to give up the wireless and connect. Couldn't be easier just connected, configured and its away. I can effectively use Linux at last. (this is my first posting from linux instead of having to post from windows)
Thanks for your patience and help.

---

### Post by sharke on 2007-08-19
Ross
Great to see you can finally browse internet with linux. yes adsl i definatly easier to setup.
Regards
Sharke

---

### Post by Jussi01 on 2007-09-20
Hei sharke,

Im still having a problem with this - it gives me connection script failed when I try to connect. 


any Ideas?

Jussi

---

### Post by sharke on 2007-09-20
> **Jussi01 said:**
> Hei sharke,

Im still having a problem with this - it gives me connection script failed when I try to connect. 


any Ideas?

Jussi

What kernel version are you using you need you need 2.6.20 or later .
the patched files were really only an attempt to help ross who seemed to have a problem with patching and building the module.
The most common form of connection problem i have came across is incorrect username being used . Please make certain your usename is like this
********@bigpond.com   *******(replace with your username).
regards
Sharke

---

### Post by Frans81 on 2007-09-21
Hi, i have the Blue BP3USB with the bigpond sticker.
To establish the connection i am running ```
pon gsm
```
the chap authentication appears to function, but it seems like it cant get an IP address.

```

Starting Sierra Wireless GSM connect script...



Setting the abort string



Initializing modem



Setting APN



Dialing...

Serial connection established.
using channel 5
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x62dd465d> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0xc <asyncmap 0x0> <auth chap MD5> <magic 0xe3eb8ee0> <pcomp> <accomp>]
sent [LCP ConfAck id=0xc <asyncmap 0x0> <auth chap MD5> <magic 0xe3eb8ee0> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x62dd465d> <pcomp> <accomp>]
rcvd [LCP DiscReq id=0xd magic=0xe3eb8ee0]
rcvd [CHAP Challenge id=0x1 <ceeb6674165d03111258d4f3cc82e2f9>, name = "UMTS_CHAP_SRVR"]
sent [CHAP Response id=0x1 <43a625845f8f0b4951ada198a1b7b58d>, name = "[COLOR="Red"]XXXXX[/COLOR]@bigpond.com"]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [LCP ProtRej id=0xe 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
IPCP: timeout sending Config-Requests
sent [LCP TermReq id=0x2 "No network protocols running"]
sent [LCP TermReq id=0x3 "No network protocols running"]
Connection terminated.
Modem hangup

```

here is the gsm file below
```

-detach

lcp-echo-failure 0

/dev/ttyUSB1

115200

debug

defaultroute

usepeerdns



#ipcp-no-address

#ipcp-no-addresses

ipcp-max-failure 4

ipcp-accept-local

ipcp-accept-remote



# AUTHENTICATION

# If noauth works, use that, otherwise you have to pass

# the user name and password. This is an example of a

# standard bigpond user/pw combo



# noauth

user [COLOR="Red"]XXXXX[/COLOR]@bigpond.com

password [COLOR="Red"]XXXXX[/COLOR]


crtscts

lock

connect '/usr/sbin/chat -v -t6 -f /etc/ppp/peers/gsm_chat'


```

and here is the gsm_chat file below (Not Modified)
```

# Connection script for Sierra Wireless GSM/UMTS modems
# Note: This demo script is setup to work on the bigpond network
#
SAY 'Starting Sierra Wireless GSM connect script...\n'
SAY '\n'

#######################################
SAY 'Setting the abort string\n'
SAY '\n'
# Abort String ------------------------------
ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT 'NO CARRIER' ABORT DELAYED

#######################################
SAY 'Initializing modem\n'
# Modem Initialization 
'' AT
OK ATZ

#######################################
SAY '\n'
SAY     'Setting APN\n'
# Access Point Name (APN) 
# Incorrect APN or CGDCONT can often cause errors in connection.
# Below are a bunch of different popular APNs
OK     'AT+CGDCONT=2,"IP","TELSTRA.BIGPOND"'

#######################################
SAY '\n'
SAY     'Dialing...\n'
# Dial the ISP, this is the common Cingular dial string

OK ATD*99#
CONNECT ''

```

Has anybody got any ideas WTF is happening, ie why it won't connect ?

---

### Post by Frans81 on 2007-09-22
[COLOR="Red"][SIZE="6"]Everything works fine ![/SIZE][/COLOR]
I just had the wrong password.

The built in dialer in the ubuntu networking window will not disconnect if you choose to use that.
i recommend using kppp or alternatively a script to connect and disconnect using pon to connect, and poff to disconnect.

---

### Post by sharke on 2007-09-22
> **Frans81 said:**
> [COLOR="Red"][SIZE="6"]Everything works fine ![/SIZE][/COLOR]
I just had the wrong password.

The built in dialer in the ubuntu networking window will not disconnect if you choose to use that.
i recommend using kppp or alternatively a script to connect and disconnect using pon to connect, and poff to disconnect.
Glad to here you got it fired up. it can be difficult to debug the connection script i think the modem actually connects to bigpond through the sim card and all we are doing is connecting to the modem and the authentication is then connected by the sim.
Re network manager
I now use kubuntu and with knetworkmanager i add to the /etc/network/interface file
iface ppp0 inet ppp
provider nextg  (nextg being whatever you called your provider)
Then reboot right click networkmanager icon select connect to nextg via modem and i have a nice modem icon replace networkmanager when connected you can also disconnect in the same manner. this only works with a setup via pppconfig.

Regards
Sharke

---

### Post by Frans81 on 2007-09-22
Unfortunately i don't have the BP3USB at my disposal any more, i was setting it up for someone who lives out bush where ADSL is not available. i would have liked to try this to make it easyer for the user of the machine to connect and disconnect.

Maybe and installation script my be in order, in a single package with a config script for the username and password. then again i have made a fairly simple "howto" [URL="http://ubuntuforums.org/showthread.php?t=405006"]here
[/URL]
check it out for accuracy, i may have missed some prerequisite packages that needed to be installed.

---

### Post by fox.django@gmail.com on 2007-10-20
hi i think I've read everything here and I'm still having problems. heres the read out from KPPP

Oct 20 12:35:35 john pppd[5610]: pppd 2.4.4 started by john, uid 1000
Oct 20 12:35:35 john pppd[5610]: using channel 4
Oct 20 12:35:35 john pppd[5610]: Using interface ppp0
Oct 20 12:35:35 john pppd[5610]: Connect: ppp0 <--> /dev/ttyUSB1
Oct 20 12:35:35 john pppd[5610]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x12ef4f58> <pcomp> <accomp>]
Oct 20 12:35:35 john pppd[5610]: rcvd [LCP ConfReq id=0x9 <asyncmap 0x0> <auth chap MD5> <magic 0x480641ef> <pcomp> <accomp>]
Oct 20 12:35:35 john pppd[5610]: sent [LCP ConfAck id=0x9 <asyncmap 0x0> <auth chap MD5> <magic 0x480641ef> <pcomp> <accomp>]
Oct 20 12:35:35 john pppd[5610]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x12ef4f58> <pcomp> <accomp>]
Oct 20 12:35:35 john pppd[5610]: sent [LCP EchoReq id=0x0 magic=0x12ef4f58]
Oct 20 12:35:35 john pppd[5610]: rcvd [LCP DiscReq id=0xa magic=0x480641ef]
Oct 20 12:35:35 john pppd[5610]: rcvd [CHAP Challenge id=0x1 <9e3a56ee50d5225ffaa7e2e7048582d1>, name = "UMTS_CHAP_SRVR"]
Oct 20 12:35:35 john pppd[5610]: sent [CHAP Response id=0x1 <f1b4d5dcd3ff252a2d6dd2d46034a0f5>, name = "john.poletti5@bigpond.com"]
Oct 20 12:35:35 john pppd[5610]: rcvd [LCP EchoRep id=0x0 magic=0x480641ef 12 ef 4f 58]
Oct 20 12:35:35 john pppd[5610]: rcvd [CHAP Success id=0x1 ""]
Oct 20 12:35:35 john pppd[5610]: CHAP authentication succeeded
Oct 20 12:35:35 john pppd[5610]: CHAP authentication succeeded
Oct 20 12:35:35 john pppd[5610]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Oct 20 12:35:35 john pppd[5610]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Oct 20 12:35:35 john pppd[5610]: rcvd [LCP ProtRej id=0xb 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Oct 20 12:35:35 john pppd[5610]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Oct 20 12:35:36 john pppd[5610]: rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Oct 20 12:35:36 john pppd[5610]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
Oct 20 12:36:04 john pppd[5610]: Terminating on signal 15
Oct 20 12:36:04 john pppd[5610]: sent [LCP TermReq id=0x2 "User request"]
Oct 20 12:36:07 john pppd[5610]: sent [LCP TermReq id=0x3 "User request"]
Oct 20 12:36:10 john pppd[5610]: Connection terminated.
Oct 20 12:36:10 john pppd[5610]: Modem hangup
Oct 20 12:36:10 john pppd[5610]: Exit.

any help would be fantastic

cheers

---

