---
title: "Getting the right display settings (refresh rate)"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by m_ad on 2009-07-26
I have a Samsung SyncMaster 931BW. In the Screen Resolution options, the native resolution appears (1440x900), but the refresh rate is stuck at 50Hz. I think this may be the cause of some poor video playback I've been experiencing. My question is, how can I change this to fit the monitors native refresh rate(s)?

From the manual:

```
Synchronization
Horizontal          31 ~ 81 kHz
Vertical            56 ~ 75 Hz
Display Color
16.7M Colors (8bit)
Resolution
Optimum resolution  1440 X 900@60 Hz
Maximum resolution  1440 X 900@75 Hz

```

And from my Xorg.conf

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection
```

---

### Post by Liolikas on 2009-07-26
Here not bad article, but try to find old examples in forums better:
[http://www.linux.com/news/software/applications/8201-editing-basics-for-the-xorgconf-file](http://www.linux.com/news/software/applications/8201-editing-basics-for-the-xorgconf-file)

---

### Post by m_ad on 2009-07-26
> **Liolikas said:**
> Here not bad article, but try to find old examples in forums better:
[http://www.linux.com/news/software/applications/8201-editing-basics-for-the-xorgconf-file](http://www.linux.com/news/software/applications/8201-editing-basics-for-the-xorgconf-file)

Thanks for the response. This article didn't help much, I know I need to change the settings in Xorg.conf but I don't know how :)

---

### Post by Liolikas on 2009-07-26
```

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync    30-107
        VertRefresh  48-120
EndSection

```

---

### Post by m_ad on 2009-07-26
> **Liolikas said:**
> ```

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync    30-107
        VertRefresh  48-120
EndSection

```

this will give me a refresh rate of 60hz?

---

### Post by Liolikas on 2009-07-26
> **m_ad said:**
> this will give me a refresh rate of 60hz?
nono do not forget to edit numbers!

---

### Post by m_ad on 2009-07-26
Thanks, this is my new xorg.conf

```
Section "Monitor"
	Identifier	"Configured Monitor"
	VendorName	"Samsung"
	ModelName	"SyncMaster 931BW"
	HorizSync	31-81
	VertRefresh	56-75
EndSection
```

Does this automatically change refresh rate? What should I do now?

---

### Post by cmapesjr on 2009-07-26
Edit what numbers where? :confused:

---

### Post by m_ad on 2009-07-26
> **cmapesjr said:**
> Edit what numbers where? :confused:

Edit the numbers under HorizSync and VertRefresh, along with the appropriate names in this section:

> **Liolikas said:**
> ```

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync    30-107
        VertRefresh  48-120
EndSection

```

I've done that, and now I don't know if that changes the refresh rate automatically after restarting X, or if I have to make more changes somewhere.

I restarted X and 'Screen Resolution' is still stuck at 50Hz.

---

### Post by cmapesjr on 2009-07-26
That is why I also asked. The answer you received was not enough information. Not bashing, just asking. :)

---

### Post by CatKiller on 2009-07-26
> **m_ad said:**
> the refresh rate is stuck at 50Hz.

No it isn't.

The proprietary NVidia driver deliberately mis-reports the refresh rate for the standard tools. If you run the nvidia-settings tool you'll see that the refresh rate is really something sensible.

If you wish to change that behaviour, you could put ```
        Option          "DynamicTwinView"               "False"
```in the Device section of your xorg.conf. This will also disable Dynamic TwinView, obviously.

---

### Post by skwhirl on 2009-08-31
I installed the proprietary drivers NVidia (180.44) on my recently installed Hardy, restarted and then the monitor reports "Frequency out of range" The Jaunty distro got it right Hardy set it too high.

The last time I used Linux (RH flavor) it was fairly straightforward to fix a problem like this by running Xconfigurator. Unfortunately someone at the xorg project doesn't like to maintain a standard, and that command is now defunct. 

I've also tried the nvidia-settings suggestion "Command not found" Something is apparently awry. This is turning into an evening long project to simply get the video working.

If anyone has any answers to the missing nvidia-settings, or Xorg configurator, I'd love to hear it. Else I'm going to have to go in vi and manually try entering the 'depth' settings from a printout and pray :)

---

### Post by CatKiller on 2009-08-31
If Jaunty works, why are you using Hardy?

Never heard of xconfigurator. xorg.conf is mostly legacy at the moment. I just use nano.

nvidia-settings is a separate package. If you've installed the nVidia driver through the package manager, it will be pulled in as a recommended package. If you didn't use the package manager, then you probably should have done. That's what it's there for.

---

### Post by mapes12 on 2009-09-01
> **m_ad said:**
> I have a Samsung SyncMaster 931BW. In the Screen Resolution options, the native resolution appears (1440x900), but the refresh rate is stuck at 50Hz. I think this may be the cause of some poor video playback I've been experiencing. My question is, how can I change this to fit the monitors native refresh rate(s)?

I too am running Hardy and had the very same problem yesterday. This is how I fixed it:

First of all, you need to download some packages. Go to the following 2 links. At the bottom of each page is a link to allow the package to be downloaded. Make sure that, for guidance-backends you select the correct architecture for your computer. For displayconfig-gtk there is only one possible download for all architectures. You will have to select a mirror near to you before each download will begin.

[http://packages.ubuntu.com/hardy/admin/displayconfig-gtk](http://packages.ubuntu.com/hardy/admin/displayconfig-gtk)

[http://packages.ubuntu.com/hardy/guidance-backends](http://packages.ubuntu.com/hardy/guidance-backends)

Once downloaded, click on the guidance-backends first, and you should be presented with the option 'Open with GDebi' or something similar. This program installs the package on your system. It will ask for your password.

Do the same for the displayconfig-gtk package.

Once they are both successfully installed (< 30 seconds ) open a terminal and type:

```
gksu displayconfig-gtk
```

A GUI will come up. It will let you install your screen from manufacturers' data, or you can simply select a Generic display that has the correct resolution for your screen. For LCD monitors a screen refresh rate of 60Mhz is a safe bet.

Jaunty will not let you carry out the above. It only works for Hardy.

---

