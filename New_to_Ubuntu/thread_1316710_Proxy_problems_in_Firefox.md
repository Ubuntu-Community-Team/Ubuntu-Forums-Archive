---
title: "Proxy problems in Firefox"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by tstana on 2009-11-06
Hey,

I am a new Ubuntu user, have been for a few weeks and I've just upgraded to Karmic.

Previously, on a new setup of Jaunty, I first accessed the Internet on a proxy network using Firefox 3.0 and inserted the proxy in Mozilla's *Preferences* menu. Browsing worked fine, except that I couldn't install any plugins, nor did the general "sudo apt-get update" work. 

Anyway, changed location, got the updates running, upgraded to Karmic, now everything runs smoothly, updating, Synaptic Package Manager, browsing the internet. Except (could it be any other way? :) ) that Mozilla's kept some settings in some file that are still looking for the old proxy. This is the error I get when I try to install new updates:
> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.32.18ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.32.18ubuntu1_i386.deb)Could not connect to [10.11.1.1:3128]("http://10.11.1.1:3128/") (10.11.1.1), connection timed out where 10.11.1.1:3128 is my previous proxy server. 

I tried to uninstall Firefox 3.0, the installed 3.5 and still got the same problem. In the end, I installed the Flash Plugin using Synaptic, it works fine, so no problem there.

My question is, does anyone know where Mozilla keeps such proxy settings, has anyone had such problems and if yes, how did you solve them?


Thanks in advance,
Ted

---

### Post by Trebaruna on 2009-11-06
In general, user-specific settings are all in hidden folders in your home folder. Firefox, specifically, stores its stuff in ~/.mozilla/firefox where ~ means your home folder.

EDIT: To look at hidden files in the file browser, use ctrl+h. Use that combo again to hide them afterwards.

---

### Post by ukripper on 2009-11-06
> **tstana said:**
> 

My question is, does anyone know where Mozilla keeps such proxy settings, has anyone had such problems and if yes, how did you solve them?


Thanks in advance,
Ted

firefox proxy stetings are stored in **~/mozilla/firefox/*whatevertheprofilenameis*.default/prefs.js**

Hope it helps

---

### Post by tstana on 2009-11-06
Thanks a lot, I've taken out two lines of the code that kept the proxy active and all the others seem to have been deleted too. All that's left (proxy-related) is some lines of code which I presume keep the proxy as a backup:
```
user_pref("network.proxy.backup.ftp", "10.11.1.1");
user_pref("network.proxy.backup.ftp_port", 3128 );
```etc. Am I right?

And btw, do you happen to know does the following line
```
 user_pref("network.proxy.share_proxy_settings", true);
```refer to using the proxy from System > Preferences > Network Proxy?

I've installed some Add-ons for Firefox and it seems to work ok, I don't know of any sites that would need downloading of new plugins, youtube works, sites that need flash work... If you know anything that needs new plugins so I can test the settings, please tell me.


Thanks again,
Ted

---

### Post by ukripper on 2009-11-06
> **tstana said:**
> Thanks a lot, I've taken out two lines of the code that kept the proxy active and all the others seem to have been deleted too. All that's left (proxy-related) is some lines of code which I presume keep the proxy as a backup:
```
user_pref("network.proxy.backup.ftp", "10.11.1.1");
user_pref("network.proxy.backup.ftp_port", 3128 );
```etc. Am I right?

Yes keep proxy as backup incase later you want to switch back

> **tstana said:**
> 
And btw, do you happen to know does the following line
```
 user_pref("network.proxy.share_proxy_settings", true);
```refer to using the proxy from System > Preferences > Network Proxy?

Yes you are right.

> **tstana said:**
> 
I've installed some Add-ons for Firefox and it seems to work ok, I don't know of any sites that would need downloading of new plugins, youtube works, sites that need flash work... If you know anything that needs new plugins so I can test the settings, please tell me.


Thanks again,
Ted

I think it should be ok for you now. Flash is the only cumbersome plugin, others don't give any pain. If your flash is working it seems everything else should be ok as well. if you find any problems just post in here.

---

