---
title: "Chromium browser not working after installing Google Talk plugin"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by ddarryl on 2011-04-05
Hi Everyone!

I'm a noob at Ubuntu. Basically, I installed google talk plugin for Chromium.

And after noticing that it's prevented me from running Chromium entirely, I decided to delete all extensions. Re-run, nothing happened. I reinstalled Chromium. Ran it again. "Starting Chromium Browser" then nothing. :(

When I try to run chromium through terminal, I get "Segmentation fault"

I ran this code through my terminal:
$ which chromium
$ which chromium-browser
$ dpkg -l | grep chrom

It returned: 
ii  chromium-browser                      12.0.726.0~svn20110405r80402-0ubuntu1~ucd1~maverick Chromium browser
ii  chromium-browser-inspector            12.0.726.0~svn20110405r80402-0ubuntu1~ucd1~maverick page inspector for the chromium-browser
ii  chromium-browser-l10n                 12.0.726.0~svn20110405r80402-0ubuntu1~ucd1~maverick chromium-browser language packages
ii  chromium-codecs-ffmpeg                12.0.726.0~svn20110405r80402-0ubuntu1~ucd1~maverick Free ffmpeg codecs for the Chromium Browser
ii  xserver-xorg-video-openchrome         1:0.2.904+svn842-0ubuntu1                           X.Org X server -- VIA display driver

Also: 
I'm running Maverick Meerkat


Any help is appreciated! Thanks! :D

---

### Post by Daniel0108 on 2011-04-05
Try installing Chrome, just as a test, and tell me if it works(with the extension),

Daniel

---

### Post by prshah on 2011-04-05
> **ddarryl said:**
> <..>"Starting Chromium Browser" then nothing. :(

When I try to run chromium through terminal, I get "Segmentation fault"


Try running it from the terminal in safe mode: Eg```
chromium --disable-extensions
``` Replace "chromium" with the actual name and path. (Don't know what the actual name and path is since I don't use it).

---

### Post by ddarryl on 2011-04-06
@Prshah -- I ran **chromium-browser --disable-extensions** on terminal and IT WORKED!!! 

But does that mean I'm not able to run it on normal mode anymore?

Thanks a lot!

---

### Post by gandaran on 2011-04-06
> **ddarryl said:**
> @Prshah -- I ran **chromium-browser --disable-extensions** on terminal and IT WORKED!!! 

But does that mean I'm not able to run it on normal mode anymore?

Thanks a lot!
are you running the stable chromium version? I have the google talk plugin installed with the chromium stable version no problems here.

---

### Post by ddarryl on 2011-04-06
> **gandaran said:**
> are you running the stable chromium version? I have the google talk plugin installed with the chromium stable version no problems here.
I'm running Chromium 12.0.726.0. I have no idea if this is a stable version

---

### Post by gandaran on 2011-04-06
> **ddarryl said:**
> I'm running Chromium 12.0.726.0. I have no idea if this is a stable version
isn't this the daily chromium build? from chromium PPA? stable chromium is available from the Ubuntu systems repository's.

---

### Post by ddarryl on 2011-04-06
> **gandaran said:**
> isn't this the daily chromium build? from chromium PPA? stable chromium is available from the Ubuntu systems repository's.
It appears that I have chromium from the PPA when I check in synaptic and ubuntu software centre. How do I install the stable version?

---

### Post by gandaran on 2011-04-06
> **ddarryl said:**
> It appears that I have chromium from the PPA when I check in synaptic and ubuntu software centre. How do I install the stable version?
first remove the chromium PPA repository then either force install the stable version or remove the installed chromium first and install chromium again after updating the software packages.

---

