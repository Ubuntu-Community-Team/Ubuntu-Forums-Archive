---
title: "ATI driver problems"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Michael Dooley on 2009-05-03
I updated my 64 bit machine from 8.10 t0 9.04 this weekend using a 56kb modem. After getting the new fglrx driver for jaunty, my system would boot to a black screen - no mouse, no ability to get to a terminal. Rebooting into recovery mode did not allow me to fix what appeared to be a graphics problem. Eventually, I used the root terminal in recovery mode and issued the following command:
```
apt-get remove fglrx*
```
which enabled me to boot to a gui. However, the GUI was problematic - none of the gnome windows (or any other window for that matter) had title bars. 

I can fix that on a per-session basis by clicking on System, Preferences, Appearence, Visual Effects and attempting to get either Normal or Extra Effects up and running. Neither takes hold (I get a "searching for available drivers" dialog box and then a "Desktop effects could not be enabled" dialog box) but after clicking OK, my windows now have title bars and complete borders. And my screenlets (previously invisible) can then be manually restarted. 

(1) How may I get my windows to have title bars upon booting? and (2) What should I do about an ATI graphics driver since fglrx doesn't work for me? I have downloaded the current (as of Monday, April 20) driver from ATI labeled:

ati-driver-installer-9-3-x86.x86_64.run

Should I attempt to somehow get this running on my 64 bit machine with an ATI 3450 graphics card (from ASUS)? I'm holding off on screwing up my Hardy day-to-day installation until I can be sure that Jaunty will work a little bit better.

Thanks for reading this.

---

### Post by Mark Phelps on 2009-05-04
Just so you know --- Catalyst 9.3 won't work with 9.04; you need Catalyst 9.4.  However, I don't think your card has been removed from support, so you should be able to download and install the 9.4 driver without problems.

---

### Post by Michael Dooley on 2009-05-04
Thanks for the heads up Mark. I'll get the correct driver and see if it mitigates my graphics problem. I expect to report back in a day or so with the results.

Thanks again.

---

### Post by markbuntu on 2009-05-04
You really need to remove fglrx using the script in usr/share/ati before upgrading. Using apt-get remove will not purge all the files.

---

### Post by Michael Dooley on 2009-05-24
> 
(1) How may I get my windows to have title bars upon booting?

I inserted the "metacity --replace" command into the System> Preferences> Startup Applications> Startup Programs. Thereafter, upon booting, my windows had title bars. 

> (2) What should I do about an ATI graphics driver since fglrx doesn't work for me?

I removed the proprietary driver using the method provided by [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7230361&postcount=199") post. The method he described for reconfiguring the xorg.conf file was a bit off but I was able to get to a GUI evenso. 

I downloaded the appropriate driver from ATI labeled:ati-driver-installer-9-4-x86.x86_64.run and followed the instructions provided on the Unofficial ATI Linux Driver Wiki page [[COLOR="Red"]here[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide"). After installing the driver, and logging off and back on, my graphics were substantially improved. 

I plan on installing the newest [9.5 ATI driver]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-5-x86.x86_64.run") this afternoon and anticipate better performance.

Thanks for reading this. Sorry to be so late in following up my original concerns.

---

### Post by ssri on 2009-05-24
> **markbuntu said:**
> You really need to remove fglrx using the script in usr/share/ati before upgrading. Using apt-get remove will not purge all the files.

Seconded...  Only use apt-get if you installed fglrx from Ubuntu repos or used dpkg to install the drivers from created .deb packages.

If you used "sudo sh ./file.run" to install the drivers, use the uninstall script, as recommended by Mark.

---

### Post by alphacrucis2 on 2009-05-24
Just a note that ATI have released a new version of fglrx in catalyst 9.5. You can download from their website and install following their instructions. This fixed a few things for me such as Googleearth no longer flickers madly if I have desktop effects enabled.

---

### Post by Michael Dooley on 2009-05-25
I removed catalyst 9.4 and ran my gui with the open source drivers for an hour or two. After installing catalyst 9.5, my glxgears frame rate went from 383-400 FPS (9.4) to 233-235 FPS (open source ati) to 1023 FPS (9.5). The 9.5 Catalyst drivers seem to work well for my ATI 3450 pcie graphics card.

---

