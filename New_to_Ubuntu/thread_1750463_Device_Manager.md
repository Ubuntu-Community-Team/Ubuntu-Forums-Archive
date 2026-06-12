---
title: "Device Manager?"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by joe7dust on 2011-05-05
I just need to get a PCI wireless card working in this desktop that I've put 11.04 on.

I downloaded an app called Device Manager, but it really should be called Device LIST because that's all it does as far as I can tell.

There is a similar app that appears it would have more functionality called something along the lines of GNOME Advanced Device Manager (libgnome-something-something), but the version in the 'app store' is only 152kb and appeared to only install some text files on the hard drive... Further digging yielded a 0.2 version of that program on the internet of a bigger size (452kb) but the INSTALL file made my eyes bleed a little bit.

Is there an easy install or simpler solution to this? The first app shows the D-LINK card just fine with lots of correct info, but there is no option to update the driver and make it useful in any way AFAIK.

I tried manually adding my SSID and wireless key from the icon at top right, but it doesn't look like the card is functioning at all and shows zero bars.

---

### Post by TeoBigusGeekus on 2011-05-05
Have you checked whether there are restricted drivers for your card?

---

### Post by dniMretsaM on 2011-05-05
You may have to hook your laptop directly up to an Ethernet cable and install the driver while connected. You may need to download a special driver for your card if there isn't one that works with it in the repositories. To find out what the card is (if you don't know already), run
```
lspci
```

---

### Post by joe7dust on 2011-05-05
> **dniMretsaM said:**
> You may have to hook your laptop directly up to an Ethernet cable and install the driver while connected. You may need to download a special driver for your card if there isn't one that works with it in the repositories. To find out what the card is (if you don't know already), run
```
lspci
```

It's a desktop. I downloaded an app called Additional Drivers and it appeared to do nothing at all. I did hook it up via ethernet, of course I had to in order to download the programs mentioned in my first post. Not sure how to make the leap from Ethernet access to a working wireless card...

---

### Post by lboorse2 on 2011-05-05
In the dashboard search, type in "drivers" and click the Additional Drivers icon.  This should tell you whether or not there is a restricted driver available for your device.  

Like the above reply says, connect to wired ethernet to download the restricted drivers.  

If no restricted drivers are displayed, you may need to search in Synaptic Package Manager to see if there are driver and files available for your device.  

First step -- let us know if you see and can download restricted drivers.

---

### Post by joe7dust on 2011-05-05
> **lboorse2 said:**
> In the dashboard search, type in "drivers" and click the Additional Drivers icon.  This should tell you whether or not there is a restricted driver available for your device.  

Like the above reply says, connect to wired ethernet to download the restricted drivers.  

If no restricted drivers are displayed, you may need to search in Synaptic Package Manager to see if there are driver and files available for your device.  

First step -- let us know if you see and can download restricted drivers.

Just shows an empty list and the message "No restricted drivers found in use on your system"

The card shows up just fine in the app, Device Manager... but that program doesn't seem to offer a lick of management options. It's just a list and shows D-LINK and several other info. fields on the PCI wireless card.

---

### Post by dniMretsaM on 2011-05-05
What type of card is it? You may have to download one from somewhere other than the Software Center.

---

### Post by joe7dust on 2011-05-05
> **dniMretsaM said:**
> What type of card is it? You may have to download one from somewhere other than the Software Center.

Says the model # is ACX 100, but later on in parenthesis it says DWL-520+
Vendor is Texas Intruments / D-LINK and its a PCI wireless card for desktops.

If this is going to end up anywhere near the PITA that this guy had then just forget it I won't use wireless. A script to run every 3 minutes or you get disconnected?? [http://ubuntuforums.org/showthread.php?t=43311&page=2](http://ubuntuforums.org/showthread.php?t=43311&page=2)

Is it possible that drivers available on 5.10 are no longer included with 11.04?? See this: [http://www.linuxquestions.org/questions/linux-wireless-networking-41/dwl-520-dwl-g520-ubuntu-373241/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/dwl-520-dwl-g520-ubuntu-373241/)

Found some open source drivers, but I have no idea how to install them. I have to pull some command line voodoo right? [http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless](http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless) [ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/)

---

### Post by dniMretsaM on 2011-05-05
> **joe7dust said:**
> Found some open source drivers, but I have no idea how to install them. I have to pull some command line voodoo right? [http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless](http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless) [ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/)

Yes, you'll have to decompress them an compile the source code. I don't know the specifics for these though, just check the read me, it's probably not hard.

---

### Post by joe7dust on 2011-05-05
> **dniMretsaM said:**
> Yes, you'll have to decompress them an compile the source code. I don't know the specifics for these though, just check the read me, it's probably not hard.

Thanks for the help but I probably won't bother. I have tried a few times in the past to compile things and it NEVER worked. Not in the mood for a headache. Linux has come a long way though, good to see things are moving in the right direction as far as ease-of-use goes.

edit: I've actually seen a couple advantages to Ubuntu already, tabbed file explorer & detailed end-user info on unconfigured devices. If this had been a windows setup, I'd have to either yank the card out or google the DevIDxxxx&VenIDxxxx junk from the details tab in device manager just the find out the model number and maker of the card!

---

