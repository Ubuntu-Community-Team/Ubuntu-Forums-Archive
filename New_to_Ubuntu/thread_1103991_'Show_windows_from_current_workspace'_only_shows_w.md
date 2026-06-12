---
title: "'Show windows from current workspace' only shows windows on one screen?"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by steve.klebanoff on 2009-03-23
At work, I connect a 24" monitor to my laptop, and use both the laptop and the monitor for a dual screen effect.  

The setup is great, but there is a small snag.  I like to use more than one workspace.  When I right click my taskbar, go to Preferences and select 'Show windows from current workspace', the only windows that show up in the task bar are windows that are on the laptop screen. 

For example, if I have Firefox and Komodo open on workspace 1, with Firefox on my laptop screen and Komodo on my monitor, if I set 'Show window from current workspace' the only window in the taskbar is Firefox.

Is this intended functionality?  Is there anyway to have both windows from my laptop screen and my monitor show up in the taskbar?

As of right now I have to 'Show windows from all workspaces' which half defeats the point of having two workspaces, as I like to keep my taskbar clean...

Here's my xorg.conf if it'll help:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 3200 1200
                Modes "1280x800" "1920x1200"
        EndSubSection
EndSection

```

Thanks all.

---

