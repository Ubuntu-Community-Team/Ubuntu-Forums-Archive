---
title: "Failed to check for installed &amp; available applications"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by futhiap on 2009-08-31
Hi,
Im totally new to ubuntu, and i just installed ubuntu 8.10 (dual boot with windows vista) on my laptop.
Im having problem in opening songs or videos and downloading some missing plug-ins from java.
I'll get this ERROR and I don't know what should I do..:confused:

Failed to check for installed and available applications
"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file 'etc/apt/sources.list' and reload the software information with 'sudo apt-get update' and 'sudo apt-get install-f'."

Thanks....

---

### Post by kansasnoob on 2009-08-31
> **futhiap said:**
> Hi,
Im totally new to ubuntu, and i just installed ubuntu 8.10 (dual boot with windows vista) on my laptop.
Im having problem in opening songs or videos and downloading some missing plug-ins from java.
I'll get this ERROR and I don't know what should I do..:confused:

Failed to check for installed and available applications
"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file 'etc/apt/sources.list' and reload the software information with 'sudo apt-get update' and 'sudo apt-get install-f'."

Thanks....

Go to System > Administration > Synaptic Package Manager and click Edit > Fix Broken Packages. See what happens, if the apply button becomes "active" you can click on it and see what's going to be installed.

But while you're in Synaptic let's check "sources.list" graphically. Click on Settings > Repositories. I like pictures:

[ATTACH]126904[/ATTACH]

[ATTACH]126905[/ATTACH]

[ATTACH]126906[/ATTACH]

Next, after closing Synaptic, you'll want to go to Accessories > Terminal and run the following commands:

```
sudo apt-get update
```

You may find there are updates available or you may get some errors that we'll need to know about.

```
sudo apt-get -f install
```

This may show you have packages that need to be removed and/or installed to resolve unmet dependencies.

Since we're in Terminal, unless you have a bunch of errors pop up, I'd install a few things for multi-media, first let's get the Medibuntu repos:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

Now we'll install some helpful packages:

```
sudo apt-get install totem-plugins-extra totem-xine ubuntu-restricted-extras mozilla-plugin-vlc  vlc-plugin-pulse libdvdcss2 w32codecs
```

Be sure and restart Firefox afterwards so the plug-in changes will take effect.

Let us know how that goes.

---

### Post by futhiap on 2009-08-31
> **kansasnoob said:**
> Go to System > Administration > Synaptic Package Manager and click Edit > Fix Broken Packages. See what happens, if the apply button becomes "active" you can click on it and see what's going to be installed.

But while you're in Synaptic let's check "sources.list" graphically. Click on Settings > Repositories. I like pictures:

[ATTACH]126904[/ATTACH]

[ATTACH]126905[/ATTACH]

[ATTACH]126906[/ATTACH]

Next, after closing Synaptic, you'll want to go to Accessories > Terminal and run the following commands:

```
sudo apt-get update
```You may find there are updates available or you may get some errors that we'll need to know about.

```
sudo apt-get -f install
```This may show you have packages that need to be removed and/or installed to resolve unmet dependencies.

Since we're in Terminal, unless you have a bunch of errors pop up, I'd install a few things for multi-media, first let's get the Medibuntu repos:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```Now we'll install some helpful packages:

```
sudo apt-get install totem-plugins-extra totem-xine ubuntu-restricted-extras mozilla-plugin-vlc  vlc-plugin-pulse libdvdcss2 w32codecs
```Be sure and restart Firefox afterwards so the plug-in changes will take effect.

Let us know how that goes.




Wow... Thanks for the help... The error nw gone and it can verify my java version.

---

