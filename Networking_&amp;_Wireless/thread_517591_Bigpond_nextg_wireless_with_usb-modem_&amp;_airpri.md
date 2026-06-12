---
title: "Bigpond nextg wireless with usb-modem &amp; airprime module"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by sharke on 2007-08-04
Bigpond australia nextg wirless internet for desktop supplies a Maxon BP3-EXT USB Modem for connection and this does not get recognised by the system.
To rectify we patch the airprime module adding the the product id to the airprime.c.
I found the easiest way is to patch the module in the kernel-source and rebuild the kernel.

So lets start



# Install necessary needed to configure the kernel
Code:

sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev

# cd /usr/src

# sudo -s


# Now we are going to download the kernel and unpack it
Code:

 apt-get install linux-image-generic (or whatever you use)
 tar.bz2 && tar -xvjf linux-2.6.22.tar.bz2

# We now patch the airprime.c fle in /usr/src/linux-2.6.22/drivers/usb/serial adding the modem device id.

In the terminal
nautilus
browse to  /usr/src/linux-2.6.22/drivers/usb/serial /airprime.c and add the id
 and it should look like this.

static struct usb_device_id id_table [] = {
	{ USB_DEVICE(0x0c88, 0x17da) }, /* Kyocera Wireless KPC650/Passport */
	{ USB_DEVICE(0x413c, 0x8115) }, /* Dell Wireless HSDPA 5500 */
        { USB_DEVICE(0x16d8, 0x6280) }, /* Maxon BP3-USB 3G Bigpond Telstra */
	{ },

We now configure the kernel


# Remove the link to the linux directory, make a new link to the new kernel, and move to the Linux directory:
Code:

rm -rf linux && ln -s /usr/src/linux-2.6.22 linux && cd /usr/src/linux


# Now import your current kernel configuration and get your current kernel options:
Code:

cp /boot/config-`uname -r` .config && make oldconfig

#  build the kernel: Make sure that you are in /usr/src/linux with full root access. This will build a debian file that you can install.

Now in the terminal do this:

Code:

make-kpkg clean

Then this:

Code:

make-kpkg -initrd --revision=64 kernel_image kernel_headers modules_image

Note: Revision can be anything you like

# Install the 2 .deb files in /usr/src. 

cd .. && dpkg -i linux*.deb

Reboot and system should recognise your modem and attach to airprime module.

You now configure your connection with network configuration the phone number is #99* and on my system the modem is /dev/ttyUSB3.

Regards

Sharke

---

