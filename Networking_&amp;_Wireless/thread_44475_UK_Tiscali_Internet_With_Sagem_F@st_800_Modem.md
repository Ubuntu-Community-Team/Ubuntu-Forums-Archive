---
title: "UK Tiscali Internet With Sagem F@st 800 Modem"
date: 2005-06-26
forum: Networking &amp; Wireless
---

### Post by podrik0 on 2005-06-26
Just help me get started by getting me connected to the net some how please!!!

Am a complete linux noob, no nothing about installing packages drivers etc!!

So need some simplified steps

Have found:
[http://faq.eagle-usb.org/wakka.php?wiki=InstallSuseEn](http://faq.eagle-usb.org/wakka.php?wiki=InstallSuseEn)

I think its drivers that can get my modem working?

Then hopefully setting the connection will be easy I hope  ](*,) 

Someone please help me out  ](*,)  ](*,) after I'm connected I will directly format my hard drive of the Microsoft rubbish!!!!

Thnaks!

```
To connect a Suse 9.1 (Kernel 2.6) machine via a Sagem Fast800? E2T to a UK-ADSL network with Tiscali as provider.

See the detailed instructions below.

Especially note steps 4 and 8 which were unexpected. They are no longer needed since eagle-usb-2.0.0. Use latest Dev:EagleUsb230 (interwiki)


0. Install development packages (via Yast)

    * kernel-source
    * gcc (C-Compiler)
    * cpp
    * libgcc (C-Bibliotheken)
    * eazy (SUSE Compatibilty Links)
    * lsb (Standard Base Tools)
    * bison (C Parser Generator)
    * libusb (USB-Bibliotheken)
    * usbutils
    * make
    * ncurses
    * ncurses - devel (kernel-menuconfig)



1. Start a root console

2. Preparing the kernel-sources: The sources must belong to the installed kernel.
cd /usr/src/linux
Save an old config if exists:
mv .config .config.old
Type "uname -r" to find out the version of the installed kernel and copy the respective file from "/boot/config*" to "/usr/src/linux/.config".
cp /boot/config-`uname -r` /usr/src/linux/.config
Run
make menuconfig
and exit with saving.

3. Prepare the eagle-usb-driver
Download: eagle-usb-1.9.8.tar.bz2 from SourceForge download area (you may take latest version and adapt)
Unpack it somewhere: e.g. into /opt
cd /opt
tar xvfj eagle-usb-1.9.8.tar.bz2
cd /opt/eagle-usb-1.9.8
If no configure-file exists run
./autogen.sh
Then a configure-file should exist. Run
./configure --prefix=/usr

4. Normally you would proceed with "make" etc. but I had the problem that after completing the installation my modem seemed to be too new:
The modem wouldn't become operational, after waiting and when typing "eaglectrl -p" something like this would appear:
Post-firmware device on USB bus 4 (type=POTS)

The solution for this was to use the original *.bnm-files from the Tiscali-Windows-Installation-CD instead of the *.bnm-files in the eagle-usb-1.9.8-package:
The directory /media/cdrecorder/ASSETS/Sagem/L1/IDMA contains the files:
RTBLDEP0.BNM, RTBLDEP1.BNM, RTBLDEP2.BNM, RTBLDEP3.BNM, RTBLDEP4.BNM

Copy them to /opt/eagle-usb-1.9.8/driver/firmware/sagem/pots and /opt/eagle-usb-1.9.8/driver/firmware/usr/pots and also rename them from uppercase to lowercase letters e.g.:
cp /media/cdrecorder/ASSETS/Sagem/L1/IDMA/RTBLDEP0.BNM /opt/eagle-usb-1.9.8/driver/firmware/sagem/pots/rtbldep0.bnm
etc. (for files 0...4)

Note you may use this alternate method :
dowload latest windows drivers from sagem http://www.sagem.com/web-modems/download/modems/w.2.0.31_fr.zip
cd /opt/eagle-usb-1.9.8/
unzip $(DIR_DL)/eagle-w.2.0.31_fr.zip # where DIR_DL is the directory where you downloaded
cp W.2.0.31_fr/L1/IDMA/rtbldep*.bnm driver/firmware/sagem/pots
cp W.2.0.31_fr/L1/IDMA/rtbldei*.bnm driver/firmware/sagem/isdn

Those .bnm work with E2L modem and work with Fast 800 WA (wanadoo origin) and Fast 908
I don't know the difference from E2T to E2L but I suspect T mind Tiscaly, for L, I don't know.

Do you know if those bnm work with E2T modems?

5. Now it's finally time for make:
make
make install

6. Configuring the ADSL-connection:
eagleconfig
Some questions about country, username, password and when to launch the ADSL-connection will be asked now.

When everything works then text similar to this will appear:
Loading DSP & options... [ OK ]
Waiting for modem to be operational... [ OK ]
Configuration successful.
You can now type "startadsl" to launch the connection.

7. Now run "startadsl" and try to access the internet via konqueror or similar.

8. After restarting the computer neither eagleconfig nor startdsl worked anymore. The problem seemed to be that the DSP-code wasn't reinitialised.
My solution was to change line 59 in /usr/sbin/eagleconfig to
SEND_DSP_NEEDED=1
which forces the DSP-reinitialisation with every launch of eagleconfig.
Then "startadsl" works again.

9. The connection can finally be terminated with "stopadsl".
```

---

### Post by podrik0 on 2005-06-26
HELP!!!

I have burnt it onto CD so far and have no way of knowing where to start!!

---

### Post by podrik0 on 2005-06-26
THANK YOU & everyone else who helped!! 
Finally online posting off linux my first!  :)

---

