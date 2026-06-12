---
title: "nVidia settings won't save in X config"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by gshockxc on 2009-06-25
I am running Kubuntu 9.04, Jaunty.  I just installed a GeForce 8800 GTS card.  So far, it works great, and it automatically picked up the latest 180.44 driver.  I set it up to have a dual heads up display with two monitors, got all the settings the way I want, but it won't save to the Xconfig.backup file.

NVidia X Server Settings --> X Server Display configuration --> Save to X configuration file (/etc/X11/xorg.conf), gives the following message: 
```

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

```

Thanks for any help you can offer.

---

### Post by Bachstelze on 2009-06-25
You must run the nvidia control panel with root privileges (using [font="monospace"]gksudo[/font]) if you want it to be able to write to xorg.conf.

---

### Post by gshockxc on 2009-06-25
I'm not sure what command to run.  I have the terminal window open, gksudo gives me the 'Run Program' dialog.  I don't know what the commands would be to give me root privileges when I'm in the Nvidia settings window.

Thanks.

---

### Post by Bachstelze on 2009-06-25
Last time I had to use it, the command was [font="monospace"]nvidia-settings[/font], so you would need to do:

```
gksudo nvidia-settings
```

It might have changed, though, so use the Tab key to your advantage. ;)

---

### Post by gshockxc on 2009-06-25
> **HymnToLife said:**
> Last time I had to use it, the command was [font="monospace"]nvidia-settings[/font], so you would need to do:

```
gksudo nvidia-settings
```

It might have changed, though, so use the Tab key to your advantage. ;)

That did the trick.  Even old help is good help.  Thanks again.

---

