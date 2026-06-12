---
title: "Lucid in Low-Graphics mode"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by Tahakki on 2010-05-13
Starting up Lucid, I get this error message:

```
(EE)NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the system's kernel log for additional error messages.

***Aborting***

Screen(s) found, but none have a usable configuration.
```

Can anyone work out what's wrong? I don't seem to have a  file at /etc/X11/xorg.conf.

I have a GeForce 220GT, and was using the driver from Hardware Drivers - it's called 'version current'.

Thanks.

---

### Post by Tahakki on 2010-05-13
Just to add - I was able to fix the issue temporarily by resetting the X config to default, and then reinstalling the driver. I did this before, though, so this issue is not solved.

Cheers!

---

### Post by skookiesprite on 2010-05-14
Same here... Lucid seems to be ok on my netbook (which installed easily, just like Koala), but I got a new laptop (a sony vaio pcg series - which is multi-processor) and I have tried every possible thiy ng to get it to recognize the display and then to use the proprietary drivers and - apart from being unsucessful (due to my limited linux skills when working with and understanding X and super-graphic stuff) have been frustrated with the lack of any apparent reliable fix for this... I have had to go to the absurd length of uninstalling and re-installing over a dozen times over the last 30 hours (which seems to take a lot longer than koala ever did, but that could be a problem on my end due to the multi-processors)... and have tried everything I could find code-wise... I'm at my wits end... if anyone else has a newer vaio and has experienced similar problems, please chime in... Also: I only really care because (during the alleatory periods when it does let me boot into full res X) the "margins" of the desktop are trimmed so that I can't use my new wonderful machine to have dozens of drag and droppable desktops open. IN the meantime, I;'m booting into CLI, and working on my stuff there... Totally not a huge deal (I've been using a netbook as my primary for months now), but... Sigh... I had such high hopes for this new notebook and its super humongous screen... :-(

Any help is truly appreciated...

---

### Post by dtfinch on 2010-05-14
I've been getting this about 2/3's of boots (GT 240, current drivers [195.36.15]), ever since I added a second monitor.

Still looking for a solution, apart from disconnecting the monitor or RMAing the card, the latter of which is growing more appealing. I have a 9600 GSO card that works just fine with the same driver and both monitors, but it's slightly slower and a lot louder, and I still use the other computer I have it in.

What I've tried so far is exporting EDID information on both monitors and adding them to the device section my xorg.conf like so (only one monitor uses DVI):
Option "ConnectedMonitor" "DFP-0,CRT-1"
Option "CustomEDID" "DFP-0:/etc/X11/edid2.bin;CRT-1:/etc/X11/edid.bin"

But then with the above options it crashes 100% of the time. If I specify only one monitor or the other, it does not crash at all, but then I only get that monitor. With the options commented out, it randomly either completely works for both monitors or it crashes.

Update: Crashes went away when I made DFP-0 instead of CRT-1 my primary display. Not sure if the driver or card was to blame.

Update 2: Nevermind. Just crashes much less frequently now.

---

### Post by Tahakki on 2010-05-15
Just happened to me again. Solution was to reconfigure graphics to default, and then reboot, then reinstall the driver, then reboot again. This, however, is only a temporary fix.

---

### Post by Tahakki on 2010-05-17
It has now happened twice since my last post. Can anyone help?

---

### Post by gradinaruvasile on 2010-05-17
You MUST have an xorg.conf file if using other than OSS drivers.

Install the driver and type:

sudo nvidia-xconfig

To set up your xorg.conf. If you see at the end of the output that it writes another file such as XF86something, rename that file to xorg.conf.

@Dtfinch:

When you want to set up yout monitors, first rename xorg.conf, run "sudo nvidia-xconfig" from a terminal, reboot, connect both monitors start the computer, log in, launch "gksudo nvidia-settings" in a terminal. Set up the monitors as you like, then click "save to X configuration file". You MUST launch the nvidia-settings with gksudo in front to be able to write to that file, simply launching the nvidia-settings will retain the settings only until you reboot/logout.

---

### Post by Tahakki on 2010-05-18
I was wrong - I do have an xorg.conf. I'm still getting these errors though.

---

### Post by dtfinch on 2010-05-18
> **gradinaruvasile said:**
> @Dtfinch:

When you want to set up yout monitors, first rename xorg.conf, run "sudo nvidia-xconfig" from a terminal, reboot, connect both monitors start the computer, log in, launch "gksudo nvidia-settings" in a terminal. Set up the monitors as you like, then click "save to X configuration file". You MUST launch the nvidia-settings with gksudo in front to be able to write to that file, simply launching the nvidia-settings will retain the settings only until you reboot/logout.

That's the first thing I did after connecting the 2nd monitor, having done it before. It works perfectly except for the random times that it fails during bootup.

Another thing I've found is that when I get to the error, if I exit to the console and rerun gdm manually, it works, though I haven't tried enough times to be positive whether that's all the time or I've just been lucky.

Relevant parts of /etc/X11/xorg.conf:
```

...
Section "Monitor"
    #this section was added when I ran nvidia-xconfig, but it skipped my DVI-connected monitor, like it didn't need a section.
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA2226w"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    #commented this out because it didn't help. Exported edid files from nvidia-xconfig
    #Option "ConnectedMonitor" "DFP-0,CRT-1"
    #Option "CustomEDID" "DFP-0:/etc/X11/edid2.bin;CRT-1:/etc/X11/edid.bin"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 240"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    #Initially just one metamode when problems started. Added others to fix fullscreen games.
    Option         "metamodes" "CRT: 1680x1050_60 +1680+0, DFP: 1680x1050_60 +0+0; CRT: NULL, DFP: 1680x1050_60 +0+0; CRT: NULL, DFP: 1440x900_60 +0+0; CRT: NULL, DFP: 1024x768_60 +0+0; CRT: NULL, DFP: 640x480_60 +0+0"
    SubSection     "Display"
        Depth       24
	Modes "3360x1050" "1680x1050" "1440x900" "1024x768" "640x480"
    EndSubSection
EndSection
```

The error says to check the kernel log, but I've found no related errors in /var/log/kern.log, syslog, messages, dmesg, and nothing in Xorg.*.log apart from the original error.

```
(**) May 13 18:29:57 NVIDIA(0): Enabling RENDER acceleration
(II) May 13 18:29:57 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 13 18:29:57 NVIDIA(0):     enabled.
(EE) May 13 18:29:57 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) May 13 18:29:57 NVIDIA(0):     system's kernel log for additional error messages and
(EE) May 13 18:29:57 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.
```

---

### Post by undoIT on 2010-05-20
what i have done as a temporary fix is to uninstall the current proprietary driver and install the old 173 driver. no low graphics mode with the old driver. hopefully this is fixed soon.

---

### Post by Chenzo on 2010-06-21
dtfinch, 
I have the same graphics card (GTX 240) and the same problem, where the error happens randomly on boot... Have you found a solution yet?

reinstalling grub-pc did not work for me (as was recommended in some other threads).

---

### Post by dtfinch on 2010-06-21
Not yet, apart from exiting to the console and re-running gdm, which has always worked.

I feel that it'd go away entirely if I could insert a brief delay between attempts to restart X. Currently it tries to restart it instantly, giving up after 5 or so retries in only a small fraction of a second. I think I'd have to recompile GDM from the source to change it. I've tried adding brief (usually 1/2 second) delays in other places, like before the start of gdm, though I'm not sure how effective they've been. I probably still get the error once or twice a week.

---

