---
title: "Copying Plug-Ins"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by Somecuitears on 2010-07-19
hi.
is there any way i can copy all the downloaded plugins + installed pluins so tht i dont have to download it next time i install ubuntu????

---

### Post by an0dos on 2010-07-19
> **Somecuitears said:**
> hi.
is there any way i can copy all the downloaded plugins + installed pluins so tht i dont have to download it next time i install ubuntu????

I believe firefox plugins are stored in the ".mozilla" folder under your home directory. See here: [http://support.mozilla.com/en-US/kb/profiles](http://support.mozilla.com/en-US/kb/profiles).

---

### Post by lovinglinux on 2010-07-20
Are you talking about plugins like flash and quicktime or extensions like [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722/), that you get from Mozilla Add-ons site?

Plugins are installed mostly from the repositories. Some extensions can be installed from the repositories, but most of them you will get from Mozilla site (where I download all my extensions).

To backup your extensions, you can simply copy the extensions folder (~/.mozilla/firefox/<userprofile>/extensions), although I would recommend copying the entire profile folder, since several extensions save data in that location and not in their folders, so they can be kept if you uninstall them.

To easily backup your extensions and all personal Firefox data (bookmarks,  passwords, etc), you can use [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109/) extension. It also has a feature, called Quick Backup, that allows you to create a single installation file with all your extensions, so they can be installed all at once.

You can also create a [Add-ons Collection](https://addons.mozilla.org/en-US/firefox/collections/editors_picks) on Mozilla site, with all your extensions. The auto-publisher feature of the [Add-on Collector](https://addons.mozilla.org/en-US/firefox/pages/collector) extension allows you to easily add your extensions to a collection automatically and retrieve them on another machine.

If you want to re-install all your software installed from the repositories, all-at-once, then get my extension called [Umarks](https://addons.mozilla.org/en-US/firefox/addon/13153/).

I also would recommend [creating a separate partition for your /home directory](creating a separate partition for you /home), so you can install a new version of Ubuntu without losing settings and personal files.

---

### Post by Somecuitears on 2010-07-20
i m talking about the plugins like fstreamer, libvcode52, MPEG3-layer3 plugins and others.....

---

### Post by lovinglinux on 2010-07-20
> **Somecuitears said:**
> i m talking about the plugins like fstreamer, libvcode52, MPEG3-layer3 plugins and others.....

[Umarks](https://addons.mozilla.org/en-US/firefox/addon/13153/).

---

### Post by Somecuitears on 2010-07-26
I m using APTonCD software to backup my plugins.. but it doesnot show all the installed plugin..so i want to kno where are they installed so i can backup them so tht i dont hav to download it all again....

---

### Post by Paqman on 2010-07-26
> **Somecuitears said:**
> I m using APTonCD software to backup my plugins.. but it doesnot show all the installed plugin..so i want to kno where are they installed so i can backup them so tht i dont hav to download it all again....

Everything you install will be sitting in the package manager's cache (unless you've emptied it at some point).

Go to /var/cache/apt/archives, all the .deb files in there are the installers, you can copy anything you want over to the same folder in your new system. The package manager will still try to download a newer version if there's one available online, but if the one in the cache is the newest it will just use that. You can of course also install things by double-clicking on the .deb file itself.

---

### Post by Somecuitears on 2010-07-27
> **Paqman said:**
> Everything you install will be sitting in the package manager's cache (unless you've emptied it at some point).

Go to /var/cache/apt/archives, all the .deb files in there are the installers, you can copy anything you want over to the same folder in your new system. The package manager will still try to download a newer version if there's one available online, but if the one in the cache is the newest it will just use that. You can of course also install things by double-clicking on the .deb file itself.

i cannot see any .deb files in tht folder.. there is just one folder named partial and another file named locked..

---

### Post by sandyd on 2010-07-27
> **Somecuitears said:**
> i cannot see any .deb files in tht folder.. there is just one folder named partial and another file named locked..
means you ran apt-get clean
run
```

sudo apt-get [packagename] -d
```and look again.

you can also use
```

dpkg -l
```
to list everythign installed.

---

