---
title: "Enable Compositing"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by hammad1337 on 2010-02-02
I recently upgraded from Jaunty to Karmic. By upgrade, I mean by using apt dist-upgrade method. Not the fresh CD install method.

After the upgrade, desktop effects cannot be enabled.
Running compiz --replace in terminal gives
```

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

```

Desktop compositing ran fine before the upgrade.
Desktop compositing also works fine on Karmic Live CD.

I had a similar problem in the days of Gutsy, at that time running:
```

dpkg-reconfigure xserver-xorg

```
solved the problem.
Now, it just returns no output.

Ideas?

Fyi, I use Radeon 7000, which does not need any restricted drivers.

---

### Post by nerdy_kid on 2010-02-02
i get that error with a radon 200m, the card uses the free mesa drivers which can only handle one user at a time using the gfx card i guess.  So one use can have compositing, but the other gets that error.  hope this helps...

---

### Post by hammad1337 on 2010-02-02
I am the only user of my desktop, however.

---

### Post by sundol on 2010-07-11
If you updated it to the Ubuntu 10.04, you can set it easily.

On the menubar: System -> Preference -> Desktop setting -> Windows -> check 'Use Gnome Compositing'

---

### Post by techunit on 2010-07-11
I thought he would have had to enable metacity compositing...

```
sudo gconf-editor
```click apps in the "tree" scoll down to metacity open that and then open general. On the main part of the window click check compositing_manager

hope this helps. Please correct me if I am wrong but this should at least give him some desktop effects.

---

### Post by gandaran on 2010-07-11
> **techunit said:**
> I thought he would have had to enable metacity compositing...

```
sudo gconf-editor
```click apps in the "tree" scoll down to metacity open that and then open general. On the main part of the window click check compositing_manager

hope this helps. Please correct me if I am wrong but this should at least give him some desktop effects.
I use metacity compositing (my video card doesn't support 3D effects) and it doesn't give any desktop effects like compiz, what it does is allow me to run the AWN dock, but the AWN trunk version not the usual AWN from synaptic that runs on compiz, but if fact you wont notice any deference between the two AWN versions.

---

### Post by techunit on 2010-07-11
> **gandaran said:**
> I use metacity compositing (my video card doesn't support 3D effects) and it doesn't give any desktop effects like compiz, what it does is allow me to run the AWN dock, but the AWN trunk version not the usual AWN from synaptic that runs on compiz, but if fact you wont notice any deference between the two AWN versions.
Ok well sorry about that but metacity compositing can be helpful and I have seen it work in cases such as AWN so I suggested it.

---

