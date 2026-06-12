---
title: "Problems with Huawei E173 dongle (O2)"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by nadrach on 2014-05-11
Trying various versions of 14.04 on old equipment (eeePC 900, ASUS Aspire One, Sony Viao dual-core) and settled on Lubuntu for the speed. It has quirks, but nothing I could not find the way around, except for a 3G dongle. This identifies on the internal plastic as E173u-2, but on the external cover as just E173. Having trawled through the forums, I now have an entry added in the usb-modeswitch rules for the manufacturer and product (1436), and also in /etc/modules. I have also set the user permissions for modems. internet access and a bunch of other missing stuff. The dongle now configures in the network setup and saves the dongle network password (it didn't do that without the user permissions, for some reason; saved everything else except the password), but although it appears in the "lsusb" list correctly as being in modem mode, it resolutely fails to be connected. The only thing I did find is that Lubuntu always sets up both an SD device and a CD/DVD device in the disk list, with the SD unmounted but the CD/DVD mounted as a 102MB disk. Attempting to eject this (per forum suggestions) randomly returns an LXDE "Internal Error" that Lubuntu wants to report back (but it can't with the dongle not working). The thing I notice is that although with "Manage Networks" enabled in systray, I get icons for ethernet (all the time) and Wi-Fi (when enabled), no network icon ever appears for mobile broadband ... so something is missing/not enabled/not set up.

This dongle did work on Kubuntu 12.04 (still does on the eeePC 900 which has been reverted for the moment).

Any suggestions?

---

### Post by pdc on 2014-05-12
I similarly noticed an issue with a ZTE modem of ours: was fine on an older kernel (3.2 from memory) but on a 3.11 that we installed for a trial; the ZTE would not configure; I know no more

I installed crunchbang on an old EEE for us and it works well; is derived from debian [http://crunchbang.org/](http://crunchbang.org/)            (and the kernel is ..........3.4 or so I think......)

---

### Post by nadrach on 2014-05-16
OK, now I have weird.

I reverted to Lubuntu 13.10 on a test machine and compared. Couple of things to note:
(1) The desktop keyboard setting appears next to the "systray" icon and is set to the configured system setting (in my case "en_GB").
(2) The Task Bar "systray" icon provides access to all network connections, including a choice list for WiFi connections.

Whereas on Lubuntu 14.04:
(1) The desktop keyboard setting stays on the default of "en_US", until I go into "Preferences/Keyboard Input Methods/Advanced/Keyboard Layout" and tick "Use system keyboard layout". Then I have to reboot in order to get use of the "en_GB" layout. This is not necessary in 13.10. (BTW, the top screen indicator bar at login shows "en_GB", but after login everything goes back to "en_US" until I tick the box in the keyboard input methods.)
(2) There is no "systray" icon for network settings, even though it is specified in "Task Bar\Add/Remove Panel Items\Panel Applets" in exactly the same way as in 13.10. HOWEVER ... after I have fixed the keyboard problem in (1), I get a keyboard icon in the "systray" location on the Task Bar, that specifies "English - English (US)" as an alternate keyboard layout and this extra icon can be controlled/moved by modifying the "systray"entry in the "Panel Applets" list.
(3) The only way to get network control is to add the "Manage Networks" applet to the Task Bar.

This looks like something is out of whack with the system and/or Task Bar management of both keyboard layout and network management in 14.04. It repeats on 4 different test machines, so is not hardware dependent. It may therefore relate to the inablity to get my dongle to connect.

---

### Post by nadrach on 2014-05-16
Less weird, less wrong end of stick ...

The extra keyboards icon in the Task Bar is from "IBus" and is a consequence of ticking the "Use system keyboard layout box". But why is this extra box tick necessary to get my local language system setting to work for keyboard use in the desktop on Lubuntu 14.04? Not necessary in 13.10.

What is missing from the Task Bar is the "Indicator Applets" icon, even though this is configured in the Task Bar "Panel Applets" menu (by default at install). Removing and re-adding the "Indicator Applets" option in the "Panel Applets" has no effect. The icon is gone, and with it the Task Bar ability to configure network connections in a simplified manner. Not an improvement on 13.10 and earlier, definately a backward step. I suspect the cause is also connected to the inability to get a configured dongle to connect with the software and provide a network path.

Trying the dongle on 13.10 tomorrow.

---

### Post by nadrach on 2014-05-16
Found something in this thread from August 2013 (penultimate message):
 [http://ubuntuforums.org/showthread.php?t=2128479&page=2&highlight=E173](http://ubuntuforums.org/showthread.php?t=2128479&page=2&highlight=E173)

To paraphrase ... usb_modeswitch is making the wrong product ID change ...
> The problem is that usb_modeswitch switches the device from its default operation (product id 1446 which is a storage device) to the incorrect product id of 1436. In fact, it should change it to product id 140c, which is the correct product id for the modem.

The post then describes a file edit to change the configuration message sent by usb_modeswitch ... unfortunately none of the configuration files that the post specifies for 12.04 are present in 14.04.

Any suggestions?

---

### Post by nadrach on 2014-05-18
The 26Jan14 post in this thread: [http://ubuntuforums.org/showthread.php?t=2128479&page=2&highlight=E173](http://ubuntuforums.org/showthread.php?t=2128479&page=2&highlight=E173) points to Huawei's own driver. This works.
PDF instructions are here: [http://www.huaweidevice.co.in/Downloads/Linux-Installation-User-Guide.pdf](http://www.huaweidevice.co.in/Downloads/Linux-Installation-User-Guide.pdf)
Driver download is here: [http://huaweifirmwares.com/download/huawei-linxu-driver-download/](http://huaweifirmwares.com/download/huawei-linxu-driver-download/)
[Yes, I know there is a typo of "linxu" ... the website has that.]
Driver download also includes a text file with a link to an on-line version of the PDF contents (on a website full of interesting stuff about Huawei things) that is a bit easier to read.

Notes:
(1) The driver dates from about 2011/2012 and has special fixes for a number of then current Linux flavours (including Ubuntu 9.04 and derivatives) but has not been updated for later versions, although this does not seem to matter. Although the install may report a number of errors, the driver does get installed.
(2) You need to extract the contents of the driver download, which includes a "driver" directory, and then run an "install" file with a directory parameter (see the instructions). Depending on which program you use to extract the files, you may need to set the "execute" permissions on the "install" file before running it.
(3) Plug your dongle in and allow it time to go through USB setup and recognition before running the "install".
(3) The first part of the install generates some recognition messages and just after reporting that it has installed (or failed to install) an NDIS facility, the program halts after a statement that in my terminal was in blue text. This statement is actually a question, the reply to which is to hit the "enter" key. The install program then runs to completion.
(4) Remove the dongle, reboot, plug the dongle back in and then go through the network setup procedure for your distro for configuring mobile broadband.
(5) Do NOT remove the "driver" directory after install. The dongle stopped working on my system after a clean-up did this and I had to put the driver directory back, run the "Uninstall" and go through the "install" again. Note the capitalisation on "Uninstall" but not on "install".
(6) I am using Lubuntu 13.10 for the moment because the lack of a Task Bar access to network setup in 14.04 interferes. This is because the method of operation with Lubuntu is to bootup and login, wait for the network manager initialisation to complete (puts extra status info on display in the "Indicator applets" panel) then plug in the dongle and wait for the "Mobile Broadband" option to appear. Then I tick this, and within a few seconds I get a "GSM Connected" message followed by a confirmation message that I have ISP access. I cannot do this in Lubuntu 14.04 because the "Indicator applets" icon is missing from the Task Bar, despite being configured in the "Panel Applets" menu.

---

### Post by nadrach on 2014-09-27
Late addendum:
The problem with the keyboard layout stems from Ibus doing something different and seems to be a case of, "It's not a bug, it's an undocumented feature."
See bug report [https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1284635](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1284635)
I would think that setting "Preferences>Keyboard Input Methods>Advanced>Keyboard Layout>Use system keyboard layout" as ticked by default in Lubuntu's use of LXDE, would be a good idea.

---

