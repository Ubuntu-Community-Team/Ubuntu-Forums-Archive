---
title: "tata photon net connect"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by ankit_kohli on 2009-09-24
i am unable to connect ubuntu 8.04 with tata photon whiz please help me

---

### Post by ~sHyLoCk~ on 2009-09-24
I don't think you can unless the distributor supports a Linux specific version. Well does it?

---

### Post by ankit_kohli on 2009-09-24
yes

---

### Post by ~sHyLoCk~ on 2009-09-24
> **ankit_kohli said:**
> yes

More info please.:lolflag:

---

### Post by ankit_kohli on 2009-09-24
[http://www.tataindicom.com/print-t-personal-internet-photon-whiz.aspx](http://www.tataindicom.com/print-t-personal-internet-photon-whiz.aspx)

---

### Post by anewguy on 2009-09-25
Have you downloaded and read the pdf users guide for Linux at the bottom of the page you pointed to?

You need to be sure you are using supported equipment as shown in that guide and then follow it's instructions.  If you don't have wvdial installed, you'll have to download it somewhere and install it on the PC (it's easiest to go to Synaptic Package Manager, find wvdial and mark it for installation -> this will show all of the dependencies your system needs that will also need to be downloaded).

Dave :)

---

### Post by ankit_kohli on 2009-10-03
i have wvdial installed

---

### Post by anewguy on 2009-10-03
What happens at each of the steps in the Linux user guide - where does it fail, what is the message text, etc..?

Thanks
Dave :)

---

### Post by ujjwalkanth on 2009-10-11
Tata Photon has a feature of mounting itself first as a CDROM drive. 
In Windows it first opens itself as CDROM then ..  as Mobile 3G dialer.. 
i am having the same problem as ankit.
whenever i dial up the connection it says

modem cant be found. 

[http://ubuntuforums.org/showthread.php?t=1268906&highlight=Photon+Whiz](http://ubuntuforums.org/showthread.php?t=1268906&highlight=Photon+Whiz)
here is the problem .. as stated by ankit.

it mounts itself as /dev/scd2 
rather than recognising as /dev/ttyACM0 so when i run wvdialconf, no modem is found.

I hope i have stated myself properly... though i was able to use it on my laptop on Linux Mint .. but then again on my Desktop i was getting the same prob.

---

### Post by ankit_kohli on 2009-10-11
> **anewguy said:**
> What happens at each of the steps in the Linux user guide - where does it fail, what is the message text, etc..?

Thanks
Dave :)





i tried the procedure but it says

ankit@SaNg-FrOiD:~$ sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

---

### Post by anewguy on 2009-10-12
Okay, forgive another dumb question from me - you are running one of the supported pieces of hardware as listed in that Linux guide, right?

What is it - a cell phone?  I'm not familiar with what you are doing, and just going by what I see in that Linux guide. One thing I did notice is that it expects you to log in as root first before doing the things in the guide, saying the device can only be accessed by root (this is probably a permissions problem in the udev files for USB devices).  Since Ubuntu by default does not have the root account activated for log in, be sure to do every step in the Linux guide (the wvdial, the editing of the config file, everything) with a prefix of "sudo " in order to run as the super user.

Also, with the device plugged in your USB port, please do:

sudo lsusb <press enter> 

in a terminal window and post the output back here.  I may be able to come up with some udev rules to allow you to run this as your normal user with sudo.

Dave :)

---

### Post by makafsal on 2010-10-20
Please visit this page and download 
[click here]("http://makafsal.weebly.com/photon-in-ubuntu-1004.html")

---

