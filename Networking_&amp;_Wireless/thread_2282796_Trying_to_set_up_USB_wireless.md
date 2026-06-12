---
title: "Trying to set up USB wireless"
date: 2015-06-17
forum: Networking &amp; Wireless
---

### Post by Bill_Sutton on 2015-06-17
Replaced the dlink with an Asus USB AC56 wireless adapter as it has linux on the support disk. It has a script which I run  
*1. Using install.sh Script for PC-Linux*
*For driver compilation and installation in PC-Linux, we provide an install.sh*
*script to do the duties automatically. If you want to use our Wi-Fi solutions to access*
*network on PC-Linux, you can just run install.sh script and then control Wi-Fi with*
*utilities such as Network Manager. For further information about Wi-Fi station mode,*
*please refer to:*
[I]document/Quick_Start_Guide_for_Station_Mode.pdf.

below is documentation from station mode.pdf

[/I]*1. Connecting with Network Manager*
*For Linux distributions such as: Fedora, Ubuntu, etc., using Network Manager*
[I]GUI utility to connect wireless networks is easy and intuitive.

[/I]Running Ubuntu last supported Ubuntu ( there is another version released )

So have now switched back to windows to type this and the USB adapter works good.

**So how do I get this going......and yes, I am not the brightest spark in the shop**


Now tried this and am not sure I even had the right utility but I did try entering SSID and password but I am missing something.

---

### Post by Bill_Sutton on 2015-06-17
here is the output of the setup script

```
#!/bin/bash
# Auto install for 8192cu
# September, 1 2010 v1.0.0, willisTang
#
# Add make_drv to select chip type
# Novembor, 21 2011 v1.1.0, Jeff Hung
################################################################################
 
echo"##################################################"
echo "Realtek Wi-Fi driver Auto installationscript"
echo "Novembor, 21 2011 v1.1.0"
echo "##################################################"
 
################################################################################
#                                  Decompressthe driver source tal ball
################################################################################
cd driver
Drvfoulder=`ls |grep .tar.gz`
echo "Decompress the driver source tar ball:"
echo "  "$Drvfoulder
tar zxvf $Drvfoulder
 
Drvfoulder=`ls |grep -iv '.tar.gz'`
echo "$Drvfoulder"
cd  $Drvfoulder
 
################################################################################
#                                  Ifmakd_drv exixt, execute it to select chip type
################################################################################
if [ -e ./make_drv ]; then
            ./make_drv
fi
 
################################################################################
#                      make clean
################################################################################
echo "Authentication requested [root] for makeclean:"
if [ "`uname -r |grep fc`" == " " ]; then
        sudo su -c"make clean"; Error=$?
else
        su -c"make clean"; Error=$?
fi
 
################################################################################
#                                  Compilethe driver
################################################################################
echo "Authentication requested [root] for makedriver:"
if [ "`uname -r |grep fc`" == " " ]; then
            sudo su -cmake; Error=$?
else      
            su -c make;Error=$?
fi
################################################################################
#                                  Checkwhether or not the driver compilation is done
################################################################################
module=`ls |grep -i 'ko'`
echo"##################################################"
if [ "$Error" != 0 ];then
            echo"Compile make driver error: $Error"
            echo"Please check error Mesg"
            echo"##################################################"
            exit
else
            echo"Compile make driver ok!!"       
            echo"##################################################"
fi
 
if [ "`uname -r |grep fc`" == " " ]; then
            echo"Authentication requested [root] for remove driver:"
            sudo su -c"rmmod $module"
            echo"Authentication requested [root] for insert driver:"
            sudo su -c"insmod $module"
            echo"Authentication requested [root] for install driver:"
            sudo su -c"make install"
else
            echo "Authenticationrequested [root] for remove driver:"
            su -c"rmmod $module"
            echo"Authentication requested [root] for insert driver:"
            su -c"insmod $module"
            echo"Authentication requested [root] for install driver:"
            su -c"make install"
fi
echo "##################################################"
echo "The Setup Script is completed !"
echo"##################################################"

and here is the output of iwconfig that shows no wireless so above didnt work and also the output of lpci | grep network



[COLOR=#0000ff]william@Z77XUD5H:~$ iwconfig[/COLOR]
[COLOR=#0000ff]eth0      no wirelessextensions.[/COLOR]
[COLOR=#0000ff] [/COLOR]
[COLOR=#0000ff]eth1      no wirelessextensions.[/COLOR]
[COLOR=#0000ff] [/COLOR]
[COLOR=#0000ff]lo        no wirelessextensions.[/COLOR]
[COLOR=#0000ff] [/COLOR]
[COLOR=#0000ff]william@Z77XUD5H:~$[/COLOR]
[COLOR=#0000ff]william@Z77XUD5H:~$ lspci | grep network[/COLOR]
[COLOR=#0000ff]william@Z77XUD5H:~$
```


Doing this on a different machine with windows and copied the above on to a usb stick and put it in here[/COLOR]
[COLOR=#0000ff][/COLOR]
[COLOR=#0000ff] [/COLOR]

---

### Post by Pilot6 on 2015-06-17
Download this file to your home folder

[https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+files/rtl8192cu-dkms_0.2_all.deb](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+files/rtl8192cu-dkms_0.2_all.deb)

Then run in terminal

sudo dpkg -i  rtl8192cu-dkms_0.2_all.deb

Then reboot and insert the dongle.

---

### Post by Bill_Sutton on 2015-06-18
thanks for your efforts but it didnt work

it installed ok but when I run iwconfig it shows no wireless

---

### Post by wildmanne39 on 2015-06-18
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Bill_Sutton on 2015-06-18
> **Wild Man said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.



?????????


basically only one reply and it didnt work

edit: ok, see you are referring to my 2nd post and not my last one...had me confused

---

### Post by Bill_Sutton on 2015-06-20
well have the solution......get rid of ubuntu, just cant get wireless working, even brought another wireless adapter

---

