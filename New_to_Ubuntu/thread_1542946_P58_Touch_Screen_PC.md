---
title: "P58 Touch Screen PC"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by Nigel H Crosby on 2010-07-31
Dear All

New to Ubuntu but not Pc / Unix / Novell / Windows ; That said not used Unix for long long time so let say newby to all. Ok this project is one I started it a bit of fun but may lead somewhere. I just purchased a P58 from Chine ? what a P58 well it an IPAD Clone based on intel chip set see spec below

Intel Atom 450 Chip
1.66Ghz CPU
2Gbyte Memory
160Gbyte SATA Hard Disk (Can use 32 / 64 Solid State or upto 320Gbyte SATA)
3 x USB Ports
1 x SDI Card Reader
1 x 3G Slot (Not installed)
1 x Firewire Port
1 x 802.11g/b 3DSP-BlueW 2310 Wireless & Bluetooth Adaptor (Installed)
10" x 7" Touch Screen using Intel 3200 Grphics Adaptor

Work well with Windows 7 Home / Ultimate all drivers load and runs fast well fast as canbe. I like to get it working with linux, I have tried Android 1.6 and 2.1 both work well but no wireless / sound or touch screen, tried Moblin (Not very nice to work with) installed Ubuntu 10.04 load very nice dual boot with Windows ; screen looks good, graphics are fine, speed is very good, sound work however no wireless / bluetooth or touch screen ; I have down loaded the Wireless Drivers as recommeded and run the install script but still not working ; say no device ; also un able to get the touch screen working. So they are two problems I like to get help with ; but the help need to be set out in simple man terms whilst I find my feet with ubuntu.

SO

1, How do I load / check the Wireless / Bluetooth Adaptor
2, Any help in getting Touch Screen up and running

Thanks in advanced for any support / pointers / HELP..

Nigel

---

### Post by anewguy on 2010-07-31
What did you use for the wireless/bluetooth driver?  I did find [this]("http://http://www.wireless-driver.com/download/other/3dsp-bluew2310u-usb-windows-linux-driver-sofware.htm") page with an Ubuntu driver for 9.10 - don't know if it works in 10.04 or not.  It also has a link for more Linux driver help if needed.

Also, some basic things but I have to ask:

- did you install the driver as a native driver, or did you use ndiswrapper?

- did you right-click on the network manager icon to be sure "Enable Wireless" is clicked?


As far as the touch screen is concerned, I know that it used to have to be defined in xorg.conf, but since they seem to have done away with xorg.conf, I'm not sure how to do that.  I'll do some searching on the net and let you know if I find anything.

Dave ;)

---

### Post by Nigel H Crosby on 2010-07-31
Thank Dave

I went to the 3DSP Wireless Web Site and found below a link where it had drivers for version 10.04 which I loaded from the installation script using the command line installation which was supplied with the drivers.  command string used "sudo bash Install_3DSPUSB.sh" this seem to install the application and all drivers ; however it then say go to applications and select 3DSP uWD to start the application but when I do this I get the error message "/usr/bin/uwb" file or folder not found ; it is their I wonder if it permissions but not sure.

I read a bit on the touch screen but not making to much sense to me ; I did try to locate the file xorg.conf but could not find it so at a wall on that one. I'll keep reading. Thanks

---

### Post by anewguy on 2010-08-04
I haven't had any more luck trying to find things to help with your touch screen.  I know there are a lot of how-to's and posts on the web but everything seemed to point to needing xorg.conf.

Perhaps some searching on ubuntu 10.04 xorg.conf might turn up something.

EDIT:  I did find [ this ]("https://wiki.ubuntu.com/X/Config") which may be of some help.  It appears you could create an input section in the same format as that used by xorg.conf in prior releases, and just add it as a seperate conf file as noted.  Now to find out how to define your touchscreen in that file....

EDIT: I did find [ this ]("http://blog.technologeek.org/2009/12/24/248")for a description of a sample xorg configuration section for a touchscreen.  I have no idea if it will work with yours or not, or what modifications might be required.

Dave

---

