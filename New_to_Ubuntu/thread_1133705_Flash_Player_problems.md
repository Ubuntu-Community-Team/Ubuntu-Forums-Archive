---
title: "Flash Player problems"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by russcb on 2009-04-23
I'm a new convert to Ubuntu and I'm hooked! however, I need some guidance as I have problems accessing Flash videos on say Youtube.
I run Ubuntu 8.10 (intrepid) and Firefox 3.0.8 (Mozilla Firefox for Ubuntu)
On trying to access a Youtube vid I receive a message *"You either have Javascript turned off or an old version of Adobe's Flash Player. Get the latest Flash Player"*
Synaptic shows that I have Adobe-Flash Plugin 10.0.22.87-1 installed but does not show in the FF Ad-ond/Plugins.
Javascript is enabled in FF Preferences.
Can anyone help???

---

### Post by RichardLinx on 2009-04-23
Try the following:
Clear the cache in firefox. (Tools > Clear Private Data > Cache)

It's possible that you have some conflicting packages, run:

```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```

These commands will remove any old or 'useless' packages. 

If problems persist then remove flash (ie. delete it) and then reinstall the latest version of flash from the Adobe site. 
Or just type: 
```
sudo apt-get install flashplugin-nonfree
```

Post your results. :)

---

### Post by russcb on 2009-04-24
Thanx RichardLinx for your reply.
I followed your suggestions with no result. The autoremove, autoclean and install returned *"flashplugin-nonfree is already the newest version, 0 upgrade, 0 newley installed, 0 to remove and 0 not upgraded."*
However, I no longer receive the message *"You either have javascript turned off....etc"*
Should the Adobe Flash Player appear in the FF Add-ons list? Shockwave Flash 10.0 r22 now appears there. Are they the same?

---

### Post by RichardLinx on 2009-04-24
> Should the Adobe Flash Player appear in the FF Add-ons list? Shockwave Flash 10.0 r22 now appears there. Are they the same?
Yes, "Shockwave Flash 10.0 r22" should appear in the Firefox Add-ons list under the plugins tab.

Since you removed and reinstalled Flash then I doubt that's the issue. It could be the Java plugin. Make sure you have "sun-java6-plugin" installed. (You can get it from Synaptic)

If that doesn't fix it then I'm not really sure what the issue is. You're probably missing a plugin/codec of some kind, if all else fails you can always just reinstall Firefox from scratch.

One more thing, do you have the "ubuntu-restricted-extras" installed by any chance?

---

### Post by gandaran on 2009-04-24
> **russcb said:**
> I'm a new convert to Ubuntu and I'm hooked! however, I need some guidance as I have problems accessing Flash videos on say Youtube.
I run Ubuntu 8.10 (intrepid) and Firefox 3.0.8 (Mozilla Firefox for Ubuntu)
On trying to access a Youtube vid I receive a message *"You either have Javascript turned off or an old version of Adobe's Flash Player. Get the latest Flash Player"*
Synaptic shows that I have Adobe-Flash Plugin 10.0.22.87-1 installed but does not show in the FF Ad-ond/Plugins.
Javascript is enabled in FF Preferences.
Can anyone help???
maybe you have installed a broken package, run **sudo apt-get update** first, install all updates if any and reinstall the flashplugin-nonfree
also make sure you don't have any open source flash installed like gnash or swfdec.

---

### Post by russcb on 2009-04-25
Thanks Richardlinx and gandaran!
I followed your instructs and now have access to the flash videos:)
I think it was the uninstall/reinstall of FF and the disable of swfdec that fixed it. So far so good, no other issues - yet.:biggrin:

---

### Post by pixies7 on 2009-06-18
what i did to get it working again (messed up after installing NetBeans 6.7 rc3):

in synaptic: looked for adobe packages and selected to remove the adobe-flash, flashplugin-nonfree

installed the latest package with: 
 sudo apt-get install flashplugin-nonfree

restart FF and cleared its cache

Done.

---

### Post by russcb on 2009-06-20
Thanks pixies7! All is now well!!!!:biggrin::biggrin::biggrin:

---

### Post by hyperdude111 on 2009-06-20
If you want more codecs eg. mp3, mp4, avi, flv and more use this command.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by niceguy123 on 2009-06-23
> **RichardLinx said:**
> Try the following:
Clear the cache in firefox. (Tools > Clear Private Data > Cache)

It's possible that you have some conflicting packages, run:

```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```

These commands will remove any old or 'useless' packages. 

If problems persist then remove flash (ie. delete it) and then reinstall the latest version of flash from the Adobe site. 
Or just type: 
```
sudo apt-get install flashplugin-nonfree
```

Post your results. :)

Thanks.

---

