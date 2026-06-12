---
title: "Brother MFC-665CW Printer"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by froggontherocks on 2006-11-16
I have a Brother MFC-665CW Connected Wireless to my router. I am looking for a driver to allow it to print I've gotten it to say it's receiving data but nothing every prints. Anybody have any advice?

---

### Post by froggontherocks on 2006-11-17
After getting a hold of Brother Their Japan division replied rather promptly and informed me that web drivers for this printer simply haven't been put up yet. They did send me the 2 files that I have attached and said to try these Sample drivers. I'm assuming there a beta or alpha version. But after installing and a little configuring with Cups I have successfully printed and wirelessly at that. If you search Google.com for Brother Linux it will take you right to the page with the config instructions. Hopefully this helps somebody out. :KS Thanks a Million Brother! :KS

---

### Post by family on 2007-07-06
Definitely helped me, thanks man.

---

### Post by marwml on 2007-08-28
Very helpful.  Latest Linux drivers are at Brother.com:  [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html).  Have to install the LPR driver before the CUPS drivers.  I used GNOME software installer for each driver during download.  Then 665CW printer appeared in sys>admin>printer box.  But sending Firefox page for printing in it failed as did printing out test.  Just sat in printer spool.

I then deleted the 665CW printer icon, selected "Detect LAN Printers" under "Global Settings", selected "Add Printer" under "Printer".  665CW icon appeared as a choice under "Local or Detected Printer" (even though its setup as a network printer using my routers DHCP server) but did not appear as a "Network printer" choice, selected "Forward" and it installed.  I then marked it as "Default".   I then was able to print to it just fine.

---

### Post by kenski on 2007-11-06
> **froggontherocks said:**
> After getting a hold of Brother Their Japan division replied rather promptly and informed me that web drivers for this printer simply haven't been put up yet. They did send me the 2 files that I have attached and said to try these Sample drivers. I'm assuming there a beta or alpha version. But after installing and a little configuring with Cups I have successfully printed and wirelessly at that. If you search Google.com for Brother Linux it will take you right to the page with the config instructions. Hopefully this helps somebody out. :KS Thanks a Million Brother! :KS

Helped me too, thanks from a novice!

---

### Post by digifan on 2007-11-06
Same goes for this here multi functional the DCP-770CW, what a treat, the linux drivers from Brother themselves and the short instruction on their website have it made possible for me to print AND scan WIRELESSLY.
WOW. 
So they really exist, "**linux aware**" hardware companies.

Kudo's **Brother** ):P
[ATTACH]49342[/ATTACH][ATTACH]49346[/ATTACH]

---

### Post by master5o1 on 2007-11-16
So how do I set up wireless printing? (if the wlan AP is the laptop itself)

AND: My cups is asking for a password to 'localhost'. I input my sudo password and it claims that its incorrect. So what is the password?

---

### Post by vitorio on 2007-11-22
Hi folks,

Sorry if my question is slightly out of topic.  But since you are all using Brother MFC-665cw All-in-One you would be the best source to ask.

You see, I am looking to buy one of them and badly need to know whether its cartridges are refillable?  I mean, is it possible to refill them on my own?  And if it is possible, could you tell me if it is very messy. 

I currently own Canon i550 and to refill its cartridges is a piece of cake.  Takes 5-10 minutes.  But since I've decided to switch completely to Ubuntu I want to replace it as the support for it is a kind of flaky.

Appreciate any info.

Thanks.

---

### Post by master5o1 on 2007-12-25
How do I compile the source to the Cupswrapper for the MFC-665CW?

file = source from brother's site.

---

### Post by hduong01 on 2008-04-02
HI, I followed the steps and installed the newest drivers and cups:
mfc665cwlpr-1.0.1-1.i386.deb
mfc665cwcupswrapper-1.0.1-1.i386.deb

When I send something to print, I see the printer processing the job, on the display of my MFC-655CW but it won't start printing.  I was wondering if I miss a step or what I can do? Any help would be greatly appreciated.

---

### Post by delvsional on 2008-04-17
Thanks so much.  works with the mfc-685cw too.

---

### Post by muzzamo on 2008-04-29
Hi all, 

Just thought I would add a note for hardy users who come looking to setup the MFC-685CW or other brother printers.

Brother have a note on their linux FAQ ([http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html)) 

"I'm using Ubuntu 8.04. I have installed the drivers, but I am still unable to print.


Ubuntu 8.04 does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message about it.

1. Uninstall the cupswrapper driver.
Command : sudo dpkg -P (driver name)

2. Create /usr/share/cups/model directory
Command : sudo mkdir /usr/share/cups/model

3. Install the cupswrapper driver
Command : sudo dpkg -i --force-all --force-architecture (driver file name)"

---

### Post by frup on 2008-04-29
I'm working on installing this printer right now.

Does it only work on LPR/LPD? (i.e ethernet right?) or can I get it working through USB. This is my grandparents printer and they don't have a switch or multiport router so to use LPR/LPD they would have to unplug their internet connection without buying extra hardware.

---

### Post by labinnsw on 2008-05-10
For example

username@username-desktop:~$ **sudo dpkg -P mfc665cwcupswrapper**

(Reading database ... 113419 files and directories currently installed.)

Removing mfc665cwcupswrapper ...

 * Restarting Common Unix Printing System: cupsd                                                                      [ OK ] 

username@username-desktop:~$ **sudo mkdir /usr/share/cups/model**

username@username-desktop:~$ **sudo dpkg -i --force-all --force-architecture ~/Desktop/mfc665cw/mfc665cwcupswrapper-1.0.1-1.i386.deb**

Selecting previously deselected package mfc665cwcupswrapper.

(Reading database ... 113417 files and directories currently installed.)

Unpacking mfc665cwcupswrapper (from .../mfc665cwcupswrapper-1.0.1-1.i386.deb) ...

Setting up mfc665cwcupswrapper (1.0.1-1) ...

 * Restarting Common Unix Printing System: cupsd                                                                                                    [ OK ] 



username@username-desktop:~$ 

In System>>Administration>>Printing delete any MFC665CW printers you see and make your own.

Description: Brother MFC-665CW
Location: username-desktop
Device URI: usb://Brother/MFC-665CW
Make and Model: Brother MFC-665CW CUPS v1.1

or similar.

---

### Post by labinnsw on 2008-05-10
hduong01

You need to go back to post number 7 in this thread. Good Luck

---

### Post by rjfoo on 2008-05-22
Selecting previously deselected package mfc665cwcupswrapper.
(Reading database ... 106064 files and directories currently installed.)
Preparing to replace mfc665cwcupswrapper 1.0.1-1 (using .../mfc665cwcupswrapper-1.0.1-1.i386.deb) ...
/var/lib/dpkg/info/mfc665cwcupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: Permission denied
dpkg: warning - old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: Permission denied
dpkg: error processing /home/rj/mfc665cwcupswrapper-1.0.1-1.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 126
/var/lib/dpkg/info/mfc665cwcupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: Permission denied
Errors were encountered while processing:
 /home/rj/mfc665cwcupswrapper-1.0.1-1.i386.deb


umm what do i do?

---

### Post by labinnsw on 2008-05-22
Ensure that you have no other package manager (e.g. Synaptic or the Add/Remove Applications package manager) open and try again. If that is not the case then I hope someone else can help.

---

### Post by labinnsw on 2008-05-26
rjfoo I suggest you start over if you have not yet been successful in installing your printer.

I just backed up my files, favourites, evolution and gtodo and reinstalled my system over the weekend. This is how I reinstalled the printer.

Credits to [Bob Songs]("http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c"), [Matchless]("http://ubuntuforums.org/showthread.php?t=302960"), [Guitara]("http://ubuntuforums.org/showpost.php?p=2277190&postcount=283") and [Brother]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9").

**Installing Brother MFC-665**

Part 1
Use synaptic to install **csh** and **sane**

In a terminal (Applications>>Accessories>>Terminal) do the following

username@username-desktop:~$ **sudo mkdir /var/spool/lpd** 
username@username-desktop:~$ **sudo ln -s /etc/init.d/cupsys /etc/init.d/cups** 
username@username-desktop:~$ **sudo mkdir /usr/share/cups/model** 
username@username-desktop:~$ **sudo ln -s /usr/share/cups/model/mfc665cwcups.ppd /usr/share/ppd** 
username@username-desktop:~$ **sudo ln -s /usr/share/cups/model/brmfcfaxcups.ppd /usr/share/ppd** 
username@username-desktop:~$  

Part 2
Go to the "mfc665cw" folder on your desktop and double click the "mfc665cwlpr-1.0.1-1.i386.deb" package to install it.

Then go back to the terminal and do the following.
username@username-desktop:~$ **sudo dpkg -i --force-all --force-architecture ~/Desktop/mfc665cw/mfc665cwcupswrapper-1.0.1-1.i386.deb** 
Selecting previously deselected package mfc665cwcupswrapper. 
(Reading database ... 115681 files and directories currently installed.) 
Unpacking mfc665cwcupswrapper (from .../mfc665cwcupswrapper-1.0.1-1.i386.deb) ... 
Setting up mfc665cwcupswrapper (1.0.1-1) ... 
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

username@username-desktop:~$

In System>>Administration>>Printing delete any MFC665CW printers you see and make your own.

Description: Brother MFC-665CW
Location: username-desktop
Device URI: usb://Brother/MFC-665CW
Make and Model: Brother MFC-665CW CUPS v1.1

**Install Scanner**

1.Install package &#8220;brscan2-0.2.4-0.i386.deb&#8221;
2.Open "/etc/udev/rules.d/40-basic-permissions.rules" file.
3.Edit "0664" to "0666" in "USB devices" section.

Before the edit --------------------------
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

After the edit --------------------------
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"
4.Restart the system.

**Install Fax**

1.Make sure the printer is switched off.
2.Install packages &#8220;brmfcfaxlpd-1.0.0-1.i386.deb&#8221; and &#8220;brmfcfaxcups-1.0.0-1.i386.deb&#8221;_ in that order_
3.Switch the printer back on.
4.In System>>Administration>>Printing, change URI to &#8220;usb://Brother/MFC-665CW&#8221;

**To Send A Fax**
1.Use &#8220;Print to file&#8221; from your application (i.e. OOo) to generate a postscript file called i.e &#8220;testfax.ps&#8221;
2.Right click the testfax.ps file and select &#8220;Open with&#8221; and now click &#8220;Send As Fax&#8221;, the dialup screen gui should come up
3.Enter fax number and click Send.

N.B. For the fax to work you will need to have [Java installed]("https://help.ubuntu.com/community/Java")

---

### Post by nmerch on 2008-06-06
all i hard to do was go into synaptics package manager and search for MFC-665CW, two packages are listed, install them and go back into System, Admin, Printers and Hit NEW... everything else shoulda autodetect, i had no problems at all... hope this helps.. (using Hardy Heron)
-N

---

### Post by rjfoo on 2008-07-01
what about for a 64bit setup? recently switched and when i try installing the deb it gives a wrong architecture message

---

### Post by labinnsw on 2008-07-02
Not sure, but I think that all you will need to do differently, is get the 64 bit packages from the brother site.

Now I know for sure. See also [this link]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142") from Brother.

---

