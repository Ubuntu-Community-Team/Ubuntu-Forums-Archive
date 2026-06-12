---
title: "Linksys WRT310N &amp; Linksys WUSB 300N"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by jbocean on 2008-06-25
Can't get wireless working.

_Computer_
Campq Presario 6000
AMD Athlon 1.40 GHz
224 MB Ram
38 Gig HD
4 USB-1 slots

_OS_
Ubuntu 8.04 Studio Theme
installed over Windows XP home.

_Router_
Linksys WRT310N

_Card_
Linksys WUSB 300N

Trying to connect to a Dell Inspiron 531s
w/ Windows Vista as the 'host' computer, would like to file share as well with this computer as well, but **just getting internet going is #1 priority**.  
*Does the fact that the WUSB 300N is a USB-2 device, going into a USB-1 slot on the compaq make a big difference?* 

Thanks from social worker trying to go open source.

---

### Post by nobull on 2008-08-18
Have you got the wireless card to work with the ubuntu machine?  If not then you will have to set it up so it will run on the windows drivers.  This can be done by using a little application called ndiswrapper.  The most recent attempt for me(and most successful) was using the ndisgtk graphical tool.  This can be installed by through the package manager(I just searched for ndis and I did have to plug in the hardwire connection momentarily).  Also, if you install this it will install all of the requirements needed.

Once installed the 4 windows driver files need to be copied to the local machine.  These drivers can be found on the Linksys cd(win2k) or downloaded from the manufactures website.  I don't know if it important or not but I copied them to a hidden folder in my home directory to ensure full access to the files(read/write).

Then from the System>Administration there should be a Windows wireless driver button to choose.  Then just pick the *.inf file from the proper location.  If the hardware is plugged in then it will show present.

The only security settings that I have got to work are WPA or on my Linksys router it would be listed as PSK personal with AES encryption.  On the Ubuntu machine just remove the Enable roaming check box and pick your SSID with WPA personal and type in your passkey.  Hopefully this works for ya.

---

