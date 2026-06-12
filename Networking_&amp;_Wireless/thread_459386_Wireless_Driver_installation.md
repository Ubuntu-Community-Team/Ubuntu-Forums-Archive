---
title: "Wireless Driver installation"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by phanteh on 2007-05-30
Hi, I've recently installed Ubuntu on my home PC for a laugh - I have to say I'd love to use Ubuntu for pretty much everything other than games; if only I could connect to the internet!

I've been following the Documentation for supported wireless cards and have gotten as far as installing the drivers from the source code on the [ralink website]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") (RT61 chipset) but I get as far as this part of the readme:

7> $load                
    #[kernel 2.4]
    #    $/sbin/insmod rt61.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt61.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

 This is the final step and should then allow me to start setting up the wireless card properly... But I can't figure out what I'm missing - the terminal just says there's an error with the load command. I've tried it with the $ before and then it comes up with a filename error.

I've tried both with the sudo command, to no avail.

If anyone could help me out it'd be much appreciated!

---

### Post by blazercist on 2007-05-30
ok theres your first problem, dont use the ralink drivers... instead use RT61 CVS ones found here [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

also you may want to tell us things like what type of encryption you are using on your router.

once you have compiled and installed the drivers that I've mentioned in that link post again.  if you have trouble you can PM me or ask me on AIM.. im good like that.  I have an rt61 also.

In order to get this working you need to do the following

extract the folder from the archive you downloaded to your /home directory.

open a command prompt and cd to the directory containing the source ... itll be something like 

cd rt61*/Modu*

now we do the following to compile the driver:

make

sudo make install

Then we need to unload the current driver module:

sudo ifconfig ra0 down

sudo rmmod rt61.ko

Now we need to insert the newly compiled module:

sudo insmod ./rt61.ko

at this point the new driver is installed and good to go, you can verify this by typing:

sudo ifconfig

you should get an output about all the networking devices on ur comp and it should now include an entry called "wlan0"  if you see anything about "ra0" then you've messed up somewhere.

if you have wlan0 everything should be ready, you may still have problems getting your wifi associated with the access point but that should be the easy part.

---

### Post by phanteh on 2007-05-30
Cheers, I'll try this as soon as I get back from work.

I've currently set the wifi network to unsecured, just to try and get it connected up first. The card seemed to half work with the out-of-the-box drivers - it'd pick up my SSID etc. without any prompt for info but wouldn't connect to it. Eventually I got it to connect but it wasn't issuing me with an IP address or any other details. I tried to manually configure the connection (through the GUI & terminal) but to no avail: it just refused to let me connect with static IP info.

Is a good way to kill an afternoon!

Cheers for your help, will post once I've had a bash with those drivers

---

