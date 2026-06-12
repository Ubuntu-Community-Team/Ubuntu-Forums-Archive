---
title: "enabling restricted STA driver"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Akisuokas on 2010-10-26
I have a new HP Probook 4515s which used to have only Ubuntu 10.4. And everything worked.
For the reason to run one windows program (it did not work under Wine) I installed first Windows 7 and then Ubuntu 10.4.

With W7 wireless network works.
With Uduntu liveCD it works (after enabling restricted drivers).
But on installed Uduntu it does not work. And there is nothing under Restricted Driver settings.  

Where/how can I enable that driver (which obviously was on liveCD)??

---

### Post by fatality_uk on 2010-10-26
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Seem you have the Broadcom BCM43xx chipset in there.The link above should give you the information you need to install the correct drivers for WIFI.

---

### Post by UbuNoob001 on 2010-10-26
> **Akisuokas said:**
> I have a new HP Probook 4515s which used to have only Ubuntu 10.4. And everything worked.
For the reason to run one windows program (it did not work under Wine) I installed first Windows 7 and then Ubuntu 10.4.

With W7 wireless network works.
With Uduntu liveCD it works (after enabling restricted drivers).
But on installed Uduntu it does not work. And there is nothing under Restricted Driver settings.  

Where/how can I enable that driver (which obviously was on liveCD)??

Akisoukas, are you connected to a wired connection when you open the Restricted Drivers menu option? If you are not connect wired,since you aren't wirelessly, then you will be unable to detect the  STA/b43 etc for download.

---

### Post by Akisuokas on 2010-10-26
Problem solved, thanks.

That first try was made without wired/wireless internet connection.
So when plugged to wire, system instantly on opening started to look for drivers and when found/downloaded, one click and it was working.

The question for future is, why was the liveCD equipped to install (some) driver, when the installation package was not?

Aki

---

### Post by lavinog on 2010-10-26
> **Akisuokas said:**
> Problem solved, thanks.

That first try was made without wired/wireless internet connection.
So when plugged to wire, system instantly on opening started to look for drivers and when found/downloaded, one click and it was working.

The question for future is, why was the liveCD equipped to install (some) driver, when the installation package was not?

Aki

Broadcom has prevented the distribution of the firmware from the livecd.

I think there is a clause that allows the use on the livecd, but it cannot be installed from the livecd.

Fortunately, it looks like Broadcom will finally support FOSS, so maybe this issue will be a non-issue in the future.

---

### Post by UbuNoob001 on 2010-10-26
> **Akisuokas said:**
> Problem solved, thanks.

That first try was made without wired/wireless internet connection.
So when plugged to wire, system instantly on opening started to look for drivers and when found/downloaded, one click and it was working.

The question for future is, why was the liveCD equipped to install (some) driver, when the installation package was not?

Aki

Glad I could help. The installation medium, not just the LiveDVD OS implementation, does contain the driver. Simply, under your new HD installation, even without Internet, put ur install DVD into the drive. Explore the disk. and move to Pool

you need the following from the DVD  ```
../pool/main/d/dkms , ../pool/main/p/patch , ../pool/main/f/fakeroot  and ../pool/restricted/b/bcmwl 
``` these are .deb files which can be installed via deb installer.

---

