---
title: "intel 3495ABG wireless problems"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by sullam on 2008-05-02
I am having trouble getting past the following step in getting my wireless to work with hardy.
[http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)

Download, build, and install from snapshots

% wget \
  [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-1.2.25.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-1.2.25.tgz)
% tar xvf iwlwifi-1.2.25.tgz
% cd iwlwifi-1.2.25 
% make
Kernel Makefile not found at '/lib/modules/2.6.24-16-386/source'
chmod: cannot access `compatible/*': No such file or directory
chmod: cannot access `compatible/*': No such file or directory
/bin/sh: cannot create compatible/kversion: Directory nonexistent
-e 
Makefile has been modified by generate_compatible, please run `make' again

One thing that is apparent is that there is no source directory under /lib/modules/2.6.4.24-16-386/ I probably can start editing the Makefile, but any help from anyone who has a better idea would be appreciated.

---

### Post by mkoyle on 2008-05-02
You're out of my league, but start by making sure you have your kernel headers file.

```
sudo apt-get install linux-headers-2.6.24-16-386 
```

Then, lets link the ubuntu-default directory for the source to the one it's looking for:

```
sudo ln -s /lib/modules/2.6.24-16-386/build/ /lib/modules/2.6.24-16-386/source
```

Hope that helps.  Just offhand, I'm wondering if there is there a particular reason why you are using the '386' kernel in stead of the 'generic' kernel?  FYI, '386' doesn't support multiple cores...

--Matthew

---

