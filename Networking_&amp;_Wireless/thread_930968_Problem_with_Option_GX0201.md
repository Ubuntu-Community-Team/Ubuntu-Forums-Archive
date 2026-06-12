---
title: "Problem with Option GX0201"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by fmiers on 2008-09-26
I have a T-Mobile Web'n'Walk Compact II wireless broadband card, manufactured by Option N.V. The Option designation for this card is GX0201. The card is PCMCIA. I am trying to get this card to work on a laptop (hp Compaq 8510w) running Hardy Heron.

When the card is pushed in the slot, it flashes pink (normal behaviour), then rapidly flashes red/blue (it should normally give slow blue flashes). When flashing red/blue, the card will not accept any commands.

I have tried a large number of solutions, including the following:
- Trying various HOWTO's in the excellent PHARscape forums
- Trying a solution by a guy called Bernd, who found the flashing could be stopped by blacklisting the usb_serial driver. I attempted to blacklist this drive by placing the line

blacklist "usb_storage"

in the file "/etc/mobprobe.d/blacklist"

but the blacklisting had no effect. It may be that the reason is that Bernd was using SUSE (although his card exhibited exactly the same symptoms), and the solution in SUSE is different from that in Ubuntu. I have found that the card seems to work normally if I boot using live versions of SUSE 11.0 and Mandriva One 2008 Spring.

I have found out that Option 3G cards such as the GX0201, when inserted, initially show the characteristics of a USB drive. The purpose of this is so that, in Windows, they can copy their driver onto the hard disc. Having done this task, they switch to being a USB modem. In Linux, the swithc of mode from a USB drive to a USB modem is not always done automatically. This problem can be solved by using a utility like usb_modeswitch.

Unfortunately, with the red/blue flashing, I have not got as far as being able to use usb_modeswitch.

I would be grateful for any hints on how to solve this problem.

---

### Post by thoughtbox on 2008-10-25
Interesting. I've got a similar card from Telenor in Norway, but when I insert it, it ends up flashing pink.

I am unable to communicate with the card, even though it appears to be detected using the option driver:

[32293.785414] hub 9-0:1.0: USB hub found
[32293.785424] hub 9-0:1.0: 1 port detected
[32297.808248] usb 9-1: new full speed USB device using ohci_hcd and address 2
[32298.039654] usb 9-1: configuration #1 chosen from 1 choice
[32298.042797] option 9-1:1.0: GSM modem (1-port) converter detected
[32298.042899] usb 9-1: GSM modem (1-port) converter now attached to ttyUSB3
[32298.045904] option 9-1:1.1: GSM modem (1-port) converter detected
[32298.045989] usb 9-1: GSM modem (1-port) converter now attached to ttyUSB4

When I say "unable to communicate", I wasn't aware that this card is a dual-personality card, so perhaps it still thinks it is a storage device?

/TB

---

### Post by fmiers on 2008-10-30
I have found a solution to the problem. The blacklisting did not work because the correct name of the driver to blacklist is "libusual", not "usb_storage". After that, the modem does not flash rapidly red/blue, but settles into its normal slow blue flash. "usb_modeswitch" works and the modem can be controlled and a connection established with standard connection software (I used KPPP).

To summarize the exact steps required:

**Prerequisites (do once):**
1. Insert in the blacklist file "/etc/modprobe.d/blacklist" the line "blacklist libusual".
2. Install the usb_modeswitch utility, available from [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
3. Set up KPPP using the following instructions taken from [http://www.net42.co.uk/os/linux/d620_3g_datacard.html](http://www.net42.co.uk/os/linux/d620_3g_datacard.html):

[INDENT]Start KPPP and press 'Configure...'.
Under 'Accounts', press 'New' and create a name for the 3G/GPRS connection.
Enter the telephone number to dial as *99***1# (dial first profile on data card).
Press 'Customize PPPD Arguments' and enter the argument novj (THIS IS IMPORTANT or the radio will connect but the link will not start!).
Under 'Modems', add a new modem. In the modem Device tab, set the port to be /dev/ttyUSB0 from the drop-down menu. If /dev/ttyUSB0 isn't listed, then make a symlink from /dev/modem to /dev/ttyUSB0 and use /dev/modem instead.
Under the modem's 'Modem' properties tab, press 'Modem Commands', and in 'Init String 2' you need to enter: AT+CGDCONT=1,"IP","general.t-mobile.uk" - note that it is .uk not .co.uk. If you're using a provider other than T-Mobile UK then you'll need to change this to reflect the correct APN for your provider (see 'GPRS in the UK' link below).
Username and password don't seem to matter, but I set them to web/web.
[/INDENT]


**Instructions (do with each conmnection)**
1. Insert the GX0201 card. It should settle into a slow blue flash
2. Type "sudo usb_modeswitch"
3. Type "sudo ln -s /dev/ttyUSB0 /dev/modem". This creates a link between the device name of the GX0201, /dev/ttyUSB0, and the standard modem device name. It looks like it should be possible to enter /dev/ttyUSB0 directly into the KPPP settings and thus avoid this step, but I cannot get it to work.
4. Start KPPP and click Connect
5. Start a browser and begin surfing. I have found that with Firefox it is necessary to uncheck the "work offline" box in the file menu, which starts out as checked by default when connecting in this way.

**Weaknesses**
1. the blacklisting of libusual disables the USB port for the purposes of pen-drives. I occasionally have to use a pen-drve in which case, I have to remove the blacklist before I can do so. If anyone knows of a more elegant way of preventing the modem from rapid-flashing, please let me know.

---

### Post by fmiers on 2008-10-30
> **thoughtbox said:**
> Interesting. I've got a similar card from Telenor in Norway, but when I insert it, it ends up flashing pink.

I am unable to communicate with the card, even though it appears to be detected using the option driver:

[32293.785414] hub 9-0:1.0: USB hub found
[32293.785424] hub 9-0:1.0: 1 port detected
[32297.808248] usb 9-1: new full speed USB device using ohci_hcd and address 2
[32298.039654] usb 9-1: configuration #1 chosen from 1 choice
[32298.042797] option 9-1:1.0: GSM modem (1-port) converter detected
[32298.042899] usb 9-1: GSM modem (1-port) converter now attached to ttyUSB3
[32298.045904] option 9-1:1.1: GSM modem (1-port) converter detected
[32298.045989] usb 9-1: GSM modem (1-port) converter now attached to ttyUSB4

When I say "unable to communicate", I wasn't aware that this card is a dual-personality card, so perhaps it still thinks it is a storage device?

/TB

If you type "lsusb" you should see your card listed among the USB devices attached to your machine. If the card is in its initial storage mode it will appear as

Bus 009 Device 002: ID 05c6:1000 Qualcomm, Inc.

If it is working as a modem, it will appear as:

Bus 009 Device 003: ID 0af0:6701 Option

The usb_modeswitch software switches it from the first mode to the second.

---

