---
title: "ndisgtk maze"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by Gardiner Westbound on 2008-04-08
**Ubuntu 7.10** provides the following instruction for installing and enabling a Windows wireless adapter driver.

1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
2. Install ndisgtk (System ? Administration ? Synaptic Package Manager).
3. Open ndisgtk (System ? Administration ? Windows Wireless Drivers).
4. Select Install new driver.
5. Choose the location of your Windows .inf file and click Install.
6. Click OK.

Ubuntu's _Synaptic Package Manager_ cannot find *ndisgtk*. Nor can it find* ndiswrapper-utils*, which apparently is also required. For some unfathomable reason they are not included on the installation CD. They are in the universe repositories, unreachable without the Internet connection one needs ndisgtk to set up. This is a Catch-22.

Clearly ndisgtk and whatever else is required must be obtained beforehand and presumably burned to a CD along with the required Windows wireless adapter driver. Then they must be activated or somehow accessed from Ubuntu.

I will be grateful to anyone who will post step-by-step instructions.

GW

---

### Post by dmizer on 2008-04-08
in synaptic, click:
settings > repositories

make sure there is a checkmark next to "Software restricted by copyright or legal issues (multiverse)" as well as "Community-maintained Open Source Software (universe)"

click "close"

click on the "reload" button in synaptic.

search for ndiswrapper-utils and ndisgtk again.

---

### Post by Gardiner Westbound on 2008-04-08
Thank you for your reply. It did not work.

The conundrum is I need ndisgtk to enable the Ubuntu wireless connection to the Internet, but I cannot get ndisgtk from within Ubuntu without a wireless connection to the Internet. Inexplicably ndisgtk and whatever else is required is not supplied on the Ubuntu 7.10 installation CD.

I think ndisgtk must be obtained and burned to a CD beforehand and then somehow accessed by Synaptic Package Manager.

To reply to this thread I had to take Ubuntu down and use Windows.

GW

---

### Post by dmizer on 2008-04-08
not as easy as if you had internet acess on ubuntu, but still possible.

here's how: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29#head-715b64e4eb010761a0c694dde40d3a569f414b5e](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29#head-715b64e4eb010761a0c694dde40d3a569f414b5e)

---

### Post by dstew on 2008-04-08
You can also use the [nonetdebs service]("http://nonetdebs.homeip.net/") to install packages (with all the dependencies) or even update off-line.

---

### Post by Gardiner Westbound on 2008-04-08
Thanks for the help all.

I followed the instruction and believe I successfully installed the three required files. Unfortunately the driver would not install, so I'm dead in the water.

---

### Post by dstew on 2008-04-09
> Unfortunately the driver would not installYou were trying to install ndiswrapper-utils and ndisgtk before. Did you install these packages successfully? Then, did you try to install the Windows driver into ndiswrapper? Is that the problem you are having?

---

### Post by Gardiner Westbound on 2008-04-09
As suggested above, I carefully followed the instructions at
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29#head-715b64e4eb010761a0c694dde40d3a569f414b5e](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29#head-715b64e4eb010761a0c694dde40d3a569f414b5e)

I downloaded_ ndiswrapper-common_, _ndiswrapper-utils_ and _ndisgtk_ for 7.10 Gutsy Gibbon on a alternate computer, saved them to a diskette, and copied them to the Ubuntu "Home" directory along with_ rt2500usb.inf_, the required Windows USB wireless network adapter driver.

My attempts to install ndiswrapper-common, ndiswrapper-utils and ndisgtk with Terminal command lines were unsuccessful notwithstanding carefully copying and pasting the commands. I was having severe DOS flashbacks and chest pains when I discovered Unbuntu 7.10 has a graphical package installer. It successfully installed them.

I clicked on the newly created Wireless Windows Network menu item, selected and inserted rt2500usb.inf into the resulting dialog box, and clicked OK. Nothing happened; zero, zip bupkis. I checked the instructions and retraced my steps several times, but all efforts failed.

---

### Post by dstew on 2008-04-09
The file rt2500usb.inf is not the driver, it is only the "information" file. It is actually a text script that directs Windows (or ndiswrapper) how to install the driver, which is the .sys file that should accompany the .inf file. The .inf file by itself cannot do anything. You can open it with a text editor, and examine it if you like, to see the name of the different .sys files that it wants to find.

Post the output of the command```
ndiswrapper -l
```That will show if a driver is inside ndiswrapper or not.

---

### Post by Gardiner Westbound on 2008-04-09
The Wireless Network Driver dialog box specifically requests an *.inf file. I entered the rt2500usb.inf file I copied to the desktop again. It returned an "invalid driver" error message. I then pointed it at the Linksys installation CD. This time it seemed to accept the driver. I suspect the .inf file refers it to the .sys file. Unfortunately that was my sole success for the afternoon. Attempts to configure the network failed.

I ran ndiswrapper -1 and copied the message a floppy. Unfortunately my Windows computer cannot read it and I cannot duplicate it. From what I can make out there is no driver is inside ndiswrapper. 

I am sincerely grateful for your assistance, but after days of effort I’m hanging it up before I say something I will regret. Ubuntu looks like a wonderful operating system. I cannot fathom the logic behind Canonical’s omission of the required files from the CD. The huge number of similar queries on this forum alone suggests wireless networking is a major Ubuntu issue.

---

### Post by dmizer on 2008-04-09
sorry it didn't work out for you.  more than happy to help you if you're ever interested in trying again.

---

### Post by dcraven on 2008-04-09
The reason why such tools aren't on the install CD is because there is no room for such things on the disk. Things are pretty tight on there.

~djc

---

### Post by dmizer on 2008-04-09
> **dcraven said:**
> The reason why such tools aren't on the install CD is because there is no room for such things on the disk. Things are pretty tight on there.

~djc

no ... the reason is because ndiswrapper is not part of the canonical supported main repositories.  this is because ndiswrapper does not meet ubuntu licensing requirements: [http://www.ubuntu.com/community/ubuntustory/licensing](http://www.ubuntu.com/community/ubuntustory/licensing)

ndiswrapper injects restricted (not open source) windows code into the kernel.

---

### Post by dstew on 2008-04-10
> The Wireless Network Driver dialog box specifically requests an *.inf file. I entered the rt2500usb.inf file I copied to the desktop again. It returned an "invalid driver" error message.Yes, ndiswrapper requests the .inf file, but *the .inf file requests the .sys file*. If you did not have the proper .sys file in the directory, it will fail. Make sure you have both the .inf and .sys files before you try to set up ndiswrapper.

---

