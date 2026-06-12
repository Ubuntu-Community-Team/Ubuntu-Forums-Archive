---
title: "Chromium and Chrome can't load certain websites"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by BlueCanary9999 on 2011-08-15
Running Ubuntu 11.04, 64 bit, and Chromium 12.0.

When I try to load certain websites (including NYT, all of the Lifehacker/Gawker/Gizmodo network, and some random websites), Chromium and Chrome just crash, giving me the "Aw, snap!" page. When I run chromium-browser through the terminal, going to the NYT page gives
```
ERROR: unable to open font '6101'
```
Going to Lifehacker or Gizmodo or one of those sites gives
```
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
```
Loading Gawker gives both the NYT error and the Lifehacker error.

These websites work fine in Firefox, however.

I'm not sure if this is caused by Flash, although that usually gives me problems. Uninstalling Flash doesn't help, and nor does disabling it. Disabling any of the plugins or extensions, for that matter, doesn't help. Google suggested creating a new profile by deleting/renaming the ~/.config/chromium/Default/ directory.

Interestingly, sometimes I can get into the Gawker network through Gawker or Gizmodo, through which I can load the other websites in the network, such as Lifehacker. Reading an article causes the website to crash, however, as does switching to the Blog View, sometimes.

So... I'm not really sure what to do except move to Firefox, but I love Chrome's omnibar :/ Any help is appreciated.

---

### Post by LowSky on 2011-08-15
delete the config file it should fix things.

if it does not delete chromium, then delete the home folder data then reinstall.

Note I have no issue visiting those sites.

---

### Post by BlueCanary9999 on 2011-08-15
> **LowSky said:**
> delete the config file it should fix things.

if it does not delete chromium, then delete the home folder data then reinstall.

Note I have no issue visiting those sites.

I used Synaptic to completely remove Chromium and related packages. Then I deleted the .config/chromium/ directory, and then reinstalled Chromium.
It didn't work. Thanks for the suggestion tho.

Interestingly, loading Gmail sends three of the ```
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
``` errors. But Gmail loads and works fine.

---

### Post by b0b138 on 2011-08-16
I'm guessing flash. The nsplugin is what runs the 32bit flash plugin on 64bit systems.

Try removing ALL instances of flash and the nspluginwrapper (don't remove the nsplugin if its there for anything else though, like wifi drivers) and try the native 64bit flash plugin [http://labs.adobe.com/downloads/flashplayer11.html](http://labs.adobe.com/downloads/flashplayer11.html)

---

