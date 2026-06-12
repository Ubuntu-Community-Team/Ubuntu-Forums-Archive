---
title: "brother mfc-465cn drivers"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by tbird6820 on 2010-08-18
I just install 10.04 on my hp pavilion 526x and connected my brother mfc-465cn searched for driver with no luck but did get to this page, [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) 

there are instructions on cups and LPR, not sure which ones I need and before I do anything, is there a easy solution for me to get this mfc-465cn to work with 10.04?

here is the troubleshoot.tex

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dests_available': [], 'cups_queue_listed': False}
Page 3 (Local or remote?):
{'printer_is_remote': False}
Page 4 (Choose device):
{'cups_device_attributes': {'device-class': u'direct',
                            'device-id': u'MFG:Brother;CMD:HBP,BRPJL;MDL:MFC-465CN;CLS:PRINTER;',
                            'device-info': u'Brother MFC-465CN',
                            'device-location': u'',
                            'device-make-and-model': u'Brother MFC-465CN'},
 'cups_device_listed': True,
 'cups_device_uri': 'usb://Brother/MFC-465CN'}
Page 5 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

---

### Post by plucky on 2010-08-18
> there are instructions on cups and LPR, not sure which ones I need and before I do anything, is there a easy solution for me to get this mfc-465cn to work with 10.04?

The drivers for your printer are packaged in the **Synaptic Package Manager**.

Open SPM and search for **mfc-465cn** and you should get ```
brother-lpr-drivers-extra
brother-cups-wrapper-extra
```
Select both and install.Although selecting the cups-wrapper driver will also install the lpr driver.

After the installation you can then connect the printer and power on and the drivers will be available for you to install the printer.

Good Luck

---

### Post by ajgreeny on 2010-08-18
You will still need the scanner driver from [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html) however, so get that and away you go.

Just download the 32 or 64 bit brscan2 file as a deb and it's as simple as that.

---

### Post by tbird6820 on 2010-08-18
Thats great! thanks.

Now would the fax for the mfc-465cn be brmfcfax cupswrapper driver 	deb 	1.0.0-1 	29 KB 	2005.Dec.07?

---

### Post by ajgreeny on 2010-08-19
I would suggest you get both the lpr and cupswrapper drivers in .deb form from [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_pcf.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_pcf.html)
as I don't really know which is needed.  If you install both I imagine all will be ok; one or other should work.

---

### Post by tbird6820 on 2010-08-30
I've been really busy lately and I'm going to download both and get back:D

---

### Post by tbird6820 on 2010-09-02
ok I installed both the lpr and cupswrapper drivers in .deb, no problems.
I wanted to send a fax and I was reading on this page [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_pcf.html#f00094](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_pcf.html#f00094) 

do I need to do this?

# I want to send a fax from Ubuntu 10.04.


NOTE:
This FAQ is verified using Ubuntu 10.04 Beta2.
Operation may differ in the formal release of Ubuntu 10.04.


   1. Install openjdk-6-jre from Synaptic Package Manager.

   2. Create /usr/share/cups/model, if it does not exist.

      Command: sudo mkdir /usr/share/cups/model


   3. Install the drivers.

      Command: sudo dpkg -i -force-all brmfcfaxlpd-1.0.0-1.i386.deb
      Command: sudo dpkg -i -force-all brmfcfaxcups-1.0.2-2.i386.deb


   4. Change the access permission of /usr/lib/cups/filter/brfaxfilter

      Command: sudo chmod 755 /usr/lib/cups/filter/brfaxfilter

---

### Post by tbird6820 on 2010-09-27
I installed the scanner driver:
 brscan2 32bit rpm 0.2.5-1 74 KB 2009.Dec.16 it supports the mfc-465cn

when I go to:
Install Instruction : scanner driver

I select:
Scanner Driver Install with USB Connection

and go to:
Step 4. Install the driver 
4-1. Turn on your MFC/DCP and connect the USB cable. 
4-2. Open the terminal and go to the directory where the driver is. 
4-3. Install the scanner driver 

Command (for rpm)**:**rpm**-ihv**--nodeps**(scanner-drivername)

I copy:
rpm**-ihv**--nodeps**(scanner-drivername)
and replace  scanner-drivername with (brother-mfc-465cn)

I get this:
$ rpm**-ihv**--nodeps**(brother-mfc-465cn)

bash: syntax error near unexpected token `brother-mfc-465cn'


So I try without brackets and I get this:
rpm  -ihv  --nodeps  brother-mfc-465cn

The program 'rpm' is currently not installed.  You can install it by typing:

sudo apt-get install rpm

I copy sudo apt-get install rpm and get this:
sudo apt-get install rpm

[sudo] password for dave: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following packages were automatically installed and are no longer required:

  menu libgle3

Use 'apt-get autoremove' to remove them.

The following extra packages will be installed:

  liblua5.1-0 librpm0 librpmbuild0 librpmio0 rpm-common rpm2cpio

Suggested packages:

  alien elfutils rpm-i18n

The following NEW packages will be installed:

  liblua5.1-0 librpm0 librpmbuild0 librpmio0 rpm rpm-common rpm2cpio

0 upgraded, 7 newly installed, 0 to remove and 1 not upgraded.

Need to get 4,469kB of archives.

After this operation, 5,833kB of additional disk space will be used.

Do you want to continue [Y/n]? y

Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main liblua5.1-0 5.1.4-5 [82.2kB]

Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main librpmio0 4.7.2-1lbuild1 [724kB]

Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main rpm-common 4.7.2-1lbuild1 [665kB]

Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main librpm0 4.7.2-1lbuild1 [839kB]

Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main librpmbuild0 4.7.2-1lbuild1 [714kB]

Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main rpm2cpio 4.7.2-1lbuild1 [650kB]

Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main rpm 4.7.2-1lbuild1 [794kB]

Fetched 4,469kB in 6s (712kB/s)                                                

Preconfiguring packages ...

Selecting previously deselected package liblua5.1-0.

(Reading database ... 127405 files and directories currently installed.)

Unpacking liblua5.1-0 (from .../liblua5.1-0_5.1.4-5_i386.deb) ...

Selecting previously deselected package librpmio0.

Unpacking librpmio0 (from .../librpmio0_4.7.2-1lbuild1_i386.deb) ...

Selecting previously deselected package rpm-common.

Unpacking rpm-common (from .../rpm-common_4.7.2-1lbuild1_all.deb) ...

Selecting previously deselected package librpm0.

Unpacking librpm0 (from .../librpm0_4.7.2-1lbuild1_i386.deb) ...

Selecting previously deselected package librpmbuild0.

Unpacking librpmbuild0 (from .../librpmbuild0_4.7.2-1lbuild1_i386.deb) ...

Selecting previously deselected package rpm2cpio.

Unpacking rpm2cpio (from .../rpm2cpio_4.7.2-1lbuild1_i386.deb) ...

Selecting previously deselected package rpm.

Unpacking rpm (from .../rpm_4.7.2-1lbuild1_i386.deb) ...

Processing triggers for man-db ...

Setting up liblua5.1-0 (5.1.4-5) ...



Setting up librpmio0 (4.7.2-1lbuild1) ...



Setting up rpm-common (4.7.2-1lbuild1) ...

Setting up librpm0 (4.7.2-1lbuild1) ...



Setting up librpmbuild0 (4.7.2-1lbuild1) ...



Setting up rpm2cpio (4.7.2-1lbuild1) ...

Setting up rpm (4.7.2-1lbuild1) ...

Trying rpm init...



Processing triggers for libc-bin ...

ldconfig deferred processing now taking place


I go to 4-4. Check if the driver is installed 
rpm**-qa**|**grep**-e**brother-mfc-465cn

I get this:
rpm  -qa  |  grep  -e  brother-mfc-465cn

error: cannot open Name index using db3 - No such file or directory (2)

---

### Post by drillerccg on 2011-01-27
I did this pretty easily: (USN connection only, not Network)

Printer: as mentioned in this thrtead, Synaptic has the files. Search for Brother 465CN, find both and install. The printer will work.

Scanner: A bit tricky. You need 2 files brscan2 to scan from computer and scan-key-tool to scan from the scanner. You can find them here, make sure you get deb version and the right one for your computer, 32 or 64 bit: [URL="http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html"]http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html
[/URL]
The instructions are here: (even the Network one)

 [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1.html)

check in synaptic and see if **sane-utils** is installed. It was for me.

Then go here to install:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html)

and here to set it up:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html)

I chose the closest one to 10.10

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

The problem was the file they wanted to edit was read only, so I used this to edit it: open terminal

```
sudo -i
```enter password and back up your original just in case:
```
cp  /lib/udev/rules.d/50-udev-default.rules  /lib/udev/rules.d/50-udev-default.rules.BAK
```then open it with nano

```
nano  /lib/udev/rules.d/50-udev-default.rules
```use your arrows to navigate to the end but above the line "# The following rule will disable ..."
and add what you need (as said in above instruction). then  <CTRL><o>  to save and then "Exit" which is <CTRL><x>.

restart your computer and it should work.

I have not gotten the fax to work yet. Will update if I get it to work.

---

