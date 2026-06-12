---
title: "Why can't I install Adobe Flash onto Chromium browser?"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-07-22
Everytime I try to watch a Flash video in Chromium (or is it called Chrome?), I get a message that says 

The Flash plug-in was blocked because it is out of date. 

I have two options, "Run this time" which allows me to view the video but I have to keep clicking it for all other videos each time, and "Update plug-in".

When I click Update plug-in, I get taken to the adobe site which says this

[COLOR=#000000][FONT=Times New Roman][COLOR=#ff0000][FONT=Arial][COLOR=#000000]If you are using the Google Chrome browser, Adobe® Flash® Player is built-in but has been disabled. To enable Flash Player, follow the steps in [this TechNote]("http://www.adobe.com/go/flashplayerchrome")[/COLOR]

[COLOR=#888888][COLOR=#000000][FONT=Times New Roman][FONT=Arial]If you are using the open source Chromium browser, please download and install the Flash Player plug-in below.[/FONT][/FONT][/COLOR][/COLOR]
[COLOR=#888888]
[/COLOR]
[COLOR=#888888][COLOR=#000000][FONT=Times New Roman][FONT=Arial]How do I know which one I'm using, the Google Chrome browser, or the open source CHROMIUM browser?[/FONT][/FONT][/COLOR][/COLOR][COLOR=#888888][/COLOR]
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by akand074 on 2011-07-22
Install the flashaid extension, it'll wipe your system of old/unneeded flash and install the latest flash for you with a click of a button. If I'm not mistaken, there is one for chrome too...

I can't seem to find it:S I thought I saw it before. If it doesn't exist, do you have the ubuntu-restricted-extras installed? it should come as part of the package. Also I believe Chrome itself already has flash built into the browser (while chromium doesn't).

---

### Post by silex89 on 2011-07-22
FYI Chromium is NOT the same browser than Google Chrome, the first one is open-source, the last one isn't.

I have Chromium in my Kubuntu and to install flashplayer I just enabled the partner repository from synaptic (or KPackageKit in my case), then a couple of clicks here and there to mark the installation and everything went fine with youtube :D


Best Luck :)

---

### Post by brawnypandora0 on 2011-07-22
> **silex89 said:**
> FYI Chromium is NOT the same browser than Google Chrome, the first one is open-source, the last one isn't.

I have Chromium in my Kubuntu and to install flashplayer I just enabled the partner repository from synaptic (or KPackageKit in my case), then a couple of clicks here and there to mark the installation and everything went fine with youtube :D


Best Luck :)

That sounds hard. Is there an easier way through the Adobe website?

---

### Post by Rex Bouwense on 2011-07-22
You more than likely have Chromium installed unless you downloaded and installed Chrome which is unlikely.  Did the browser come installed with the OS or did you download it from the Ubuntu Software Center.  If either is the case , it is Chromium.

---

### Post by lovinglinux on 2011-07-22
Type *about[noparse]:[/noparse]plugins* in the browser address bar, then *click Details*, then copy everything in the Flash section and post here, like this:

> Flash (2 files) - Version: 11.0.1
Shockwave Flash 11.0 d1
Name:	Shockwave Flash
Version:	10.3 r181
Location:	/opt/google/chrome/libgcflashplayer.so
 	(Disabled) Enable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Name:	Shockwave Flash
Version:	11.0 d1
Location:	/usr/lib/mozilla/plugins/libflashplayer.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Disable

---

### Post by I2k4 on 2011-07-23
Frankly I just don't get "Chromium" or why some people seem to be loyal to it - it didn't run right on sites I use, and requires extra Flash installation that is dodgy and unreliable.  I suggest installing the real deal Google Chrome stable version from the Google site.  Once you have that installed, get rid of Chromium.  Official Google Chrome comes with Flash preinstalled no muss no fuss, and it works on every site in my experience.

---

### Post by SoFl W on 2011-07-23
> **I2k4 said:**
> Frankly I just don't get "Chromium" 

Some people don't like Google.
Chromium came first.

---

### Post by Rex Bouwense on 2011-07-23
For future reference Chromium is the real deal.  Google Chrome is merely a browser that is based on Chromium with some additional things added, i.e. the tracking feature.

---

