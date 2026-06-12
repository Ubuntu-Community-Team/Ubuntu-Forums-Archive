---
title: "Connecting to internet from Huawei USB modem ( tata photon plus ) in ubuntu 13.10."
date: 2013-10-21
forum: Networking &amp; Wireless
---

### Post by Sandeep_Tripathy on 2013-10-21
I have started using ubuntu just now and have been taking  help from various forums for setup related queries. Now, I am stuck on  how to install a Huawei USB modem in Ubuntu 13.10. There are a lot of  documentations but I am stuck because of my lack of knowledge on how the  OS actually works.


  I downloaded usb-modeswitch package as well as data. accidentally, I  started with installation of data ( please let me know if that may cause  any problem ), however, installation of package didn't succeed, it  threw an error that libsub-dev was not found. I downloaded  libsubx-1.0.16 from the website, but I have no clue on how to install  it and how to make it work.

  I think something wrong may have happened, so to avoid all this, I wish to start the process from the scratch and would appreciate if  someone can help me with the steps ( this is a fresh installation, so  some prerequisite package may not be present in it, kindly keep it in  mind ).

  
Regards, 
Sandeep

---

### Post by dany3 on 2013-10-21
Fortunately, this is easy to do. Right clicking the Network Manager icon in the system tray you'll see 'Edit Connections'. There, under the Mobile Broadband tab, you can add your connection info. Usually, you would add a new connection under this tab using the 'Add' button, which will start a wizard. If you don't find your carrier info listed in the wizard, you can add a custom entry. 

In the setup entry you just created you'll find another tab, also called Mobile Broadband. In the Number field, usually the dial out number is *99#. Enter the APN, which is typically 'internet' or 'browse', but may vary according to ISP. They will verify the APN info for you if necessary. 

If you want to add your own DNS servers you can do so under the IP v4 tab using comma separated values for multiple entries. 

Use the default authentication, as that will usually work. And, that is it! No software to install or nothing. Everything you need to connect already comes installed with the OS. 

Hope this helps.

---

### Post by Sandeep_Tripathy on 2013-10-21
Thanks for your response, but it appears that due to some reason, usb device is not appearing neither under devices ( flash memory ) nor under Network manager from the panel. However, it is listed when i use lsusb command. I tried troubleshooting a lot, but its just taking me from one error to another.

I installed usb-modeswitch package and data again but while running the command 'usb_modeswitch -v 0x12d1 -p 0x140b -H -W',
I got the following error: 
libusbx: error [_get_usbfs_fd] libusbx couldn't open USB device /dev/bus/usb/002/004: Permission denied
libusbx: error [_get_usbfs_fd] libusbx requires write access to USB device nodes.
Error opening the device. Abort

How do we resolve this problem ?

---

### Post by dany3 on 2013-10-22
If the device is listed using the lsusb command then it is being detected as a usb device and is mounted. Ordinarily, there should be no need to use modeswitch as usb modems normally function as a dual usb/modem device on your system. Also, using Nautilus, Ubuntu's file explorer, you will see all the devices that are mounted listed in the left panel. If the modem interface is available, you can verify it by running ifconfig from the command line. There, you will see all available network interfaces, and your modem will appear as a ppp device followed by a number, e.g. ppp0. To force mount a usb device you can also run sudo mount -t usbfs usbdevfs /proc/bus/usb. 

Network Manager is not accessed from the Systems Settings panel, and you would not see the device listed there. It is accessed from the Network Manager icon in the system tray area, which is usually located at the top right of the screen along with Date, User and other background processes. Right clicking on this will open a menu, and the last entry on that menu is 'Edit Connections'. It is here that you'll find the rest as described above, and you can simply use the wizard or create a manual entry yourself from there.

To connect, you should have to do nothing other than described above in my previous post unless somehow you've modified the device. To use the modem as a cd device, should you want to access the Windows program on it or use it for storage, you could then use modeswitch from a command line. To use this, you must use it as root  by placing the sudo command at the beginning of the command line.

As I mentioned, there is usually no issue running these devices as both a cd-usb and modem device at the same time. But, there is yet another utility you can use to force your device to be used as a modem called Ozerocdoff, should this actually be necessary. If after doing the above and it still does not work. You can find this here: [http://www.pharscape.org/ozerocdoff.html](http://www.pharscape.org/ozerocdoff.html) along with instructions on how to use it.

Cheers

---

### Post by Sandeep_Tripathy on 2013-10-22
When i ran the force mount command, i got the error " mount point /proc/bus/usb does not exist". N/w manager ( on the top bar on the screen which contains wifi, time etc ) is not listing the device. I am wondering what is to be done. Encountered several undefined reference to 'usb_release_interface' while running ozerocdoff, how to resolve it ?

---

### Post by Sandeep_Tripathy on 2013-10-23
While I try to install Ozerocdoff, I am getting several undefined reference errors such as usb_get_driver_close_np, usb_close and many more. I think I am missing some setting/prerequisite here.

> **dany3 said:**
> 
As I mentioned, there is usually no issue running these devices as both a cd-usb and modem device at the same time. But, there is yet another utility you can use to force your device to be used as a modem called Ozerocdoff, should this actually be necessary. If after doing the above and it still does not work. You can find this here: [http://www.pharscape.org/ozerocdoff.html](http://www.pharscape.org/ozerocdoff.html) along with instructions on how to use it.

Cheers

---

### Post by dany3 on 2013-10-25
If you've run the ifconfig command and the modem is listed and you've run lsusb and the usb device is listed there is no apparent reason the device would not also appear in the Network-manager configuration wizard. There would be no need to mount the usb device, and it is not necessary to do so in order to use the modem. Have you tried using the Network-manager wizard? 

You can also see all the usb devices registered on your system by using hwinfo --usb. If this is not installed on your system you can do so by using: 

*sudo apt-get install hwinfo*  at the command line.

---

### Post by Akilesh on 2013-12-01
Just in case you have not sorted out the problem. tata photon plus has recently made some changes to its network. I had photon working prior to this network upgrade. I can't figure out what changes to make to make it working now. But there is an alternative. 

first make sure lsusb displays the below device
 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card

The device id should be 140b. If its anything else you have to make use of usb_modeswitch to change it to 140b. 

Then install wvdial. then run 'wvdialconf' . This should detect your modem and install the correct config file at /etc/wvdial.conf. 

After this run 'wvdial' and wait untill you see your ip address on terminal. You are then connected.

---

### Post by bonemarrowconsulti on 2013-12-05
Tata photon USB modem :

first find out which modem you are using by using the command lsusb on terminal.

Then go to tata store and update the software in the dongle since they have recently upgraded it before 1 week.

then follow modeswitch --- sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1\:1505  command and start networking from setting and u will connect.

---

