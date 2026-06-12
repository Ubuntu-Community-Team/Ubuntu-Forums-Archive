---
title: "saving a downloaded app."
date: 2010-03-12
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-03-12
If you go to Synaptic ,it downloads and installs for you .Easy.  Is there a way to save a download to usb that will install itself in a different computer..?? from synaptic..

---

### Post by 2hot6ft2 on 2010-03-12
Yes, when you go into synaptic and mark it for install or reinstall click on File > Generate Package Download Script.
Save the script to your usb drive.
Close synaptic and go to the usb drive and double click on the script and choose "Run" if you just want it to do it.
Run in Terminal if you want to watch it download in a terminal.
It will download it to the same place/folder where the script is.

Take it to another computer and open synaptic.
Click on File > Add Downloaded Packages
Point it to where the packages and script are.

Apply
That's it.

---

### Post by n0dix on 2010-03-12
Look in /var/cache/apt/archives/. Addictionaly in Synaptic>Preferences>Files make sure "Delete downloaded packages after installation" is NOT checked. And if you click "Delete Cached Package Files" you will loose everything in /var/cache/apt/archives.

---

### Post by sandyd on 2010-03-12
apt-on-cd is a nice graphical way to do what you ask.

However, you will have to have downloaded the package and installed it ahead of time. before running apt-on-cd

---

### Post by asmoore82 on 2010-03-13
I do this a lot...

Say you have 2 machines, named apple and orange, running the same Ubuntu's.
You can run all updates on _*apple*_, then, *_on orange_*
```
**user@orange$** cd /var/cache/apt/archives
**user@orange$** sudo scp user@apple.local:$PWD/*.deb ./
```

Then, when you run updates on orange, it will have very little to download.

---

### Post by n0dix on 2010-03-13
> **asmoore82 said:**
> I do this a lot...

Say you have 2 machines, named apple and orange, running the same Ubuntu's.
You can run all updates on _*apple*_, then, *_on orange_*
```
**user@orange$** cd /var/cache/apt/archives
**user@orange$** sudo scp user@apple.local:$PWD/*.deb ./
```

Then, when you run updates on orange, it will have very little to download.

But the packages not depends on the configuration of the machines?

---

### Post by asmoore82 on 2010-03-14
> **n0dix said:**
> But the packages not depends on the configuration of the machines?

They should have a lot of base packages in common...
I will admit it's the AK47 approach ~ "Kill'em all and let God sort'em out."

It's usually best followed up with a good ```
sudo apt-get clean
```

---

### Post by n0dix on 2010-03-14
> **asmoore82 said:**
> They should have a lot of base packages in common...
I will admit it's the AK47 approach ~ "Kill'em all and let God sort'em out."

It's usually best followed up with a good ```
sudo apt-get clean
```

i see.

---

