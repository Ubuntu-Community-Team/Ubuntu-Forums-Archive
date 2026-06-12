---
title: "Can I disable workspace switcher?  Also, trouble with mic and screen brightness."
date: 2011-07-20
forum: New to Ubuntu
---

### Post by Rajahal on 2011-07-20
I'm absolutely loving Ubuntu 11.04, you can read about my initial reactions to it in [this thread](http://lime-technology.com/forum/index.php?topic=13534.0) on the unRAID forums.  I'm running Ubuntu on an Acer Aspire Timeline 4810TZ laptop which boots from an SSD.  I've checked out the [Acer support page](http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=1183) for my laptop, but of course there are no Linux drivers available, only Windows drivers.

I have three small problems.  First of all, I would like to completely disable workspace switcher, or at least change its behavior.  I simply don't need it - I'm so used to working on a single workspace that I find workspace switcher to be more of an annoyance than anything else.  However, I don't want to lose all of the other aspects of Unity that I've grown to love.

If it is not possible for workspace switcher to be disabled, then is there any way to force all applications to automatically open in the first workspace?  Specifically, LibreOffice Writer always opens in workspace 2 (top right).  I never told it to do this, it just started doing it on its own one day.  How do I fix this?

I've noticed two driver-related problems with my system.  First, my built-in microphone does not work (tested using Skype, gchat video, and Sound Recorder).  As there's no Linux driver supplied by Acer, is there any way to get it working?

Second, I am unable to adjust my screen brightness.  My keyboard shortcuts (Fn + Arrow keys) do make the brightness gauge appear, but adjusting them does nothing to actually adjust the screen brightness, despite the gauge responding appropriately.  Again, with no manufacturer-provided Linux drivers, do I have any recourse?

---

### Post by CatKiller on 2011-07-21
> **Rajahal said:**
> I have three small problems.  First of all, I would like to completely disable workspace switcher, or at least change its behavior.  I simply don't need it - I'm so used to working on a single workspace that I find workspace switcher to be more of an annoyance than anything else.  However, I don't want to lose all of the other aspects of Unity that I've grown to love.

Add the workspace switcher applet to your panel. Set the number of workspaces to 1.

---

### Post by Rajahal on 2011-07-21
> **CatKiller said:**
> Add the workspace switcher applet to your panel. Set the number of workspaces to 1.

Thank you for your reply.  Unfortunately, I'm new enough to this that I don't know how to follow your instructions.  The workspace switcher icon is already in my dock/taskbar (is that what you mean by the panel?).  I've tried right clicking it and finding other means of change its settings, but haven't been successful.  How do I change the number of workspaces?

---

### Post by CatKiller on 2011-07-21
> **Rajahal said:**
>  How do I change the number of workspaces?

The Panel is the bar along the top. I can't remember exactly how it looks because I only used the default Unity setup for about five minutes. Right-click on the Workspace Switcher applet and select Preferences. Change both Columns and Rows to 1.

---

### Post by Rajahal on 2011-07-21
Thank you again.  Workspace Switcher has no icon in the panel, only the launch icon in the dock (on the left side of the screen).  I've looked through the system settings and can't figure out a way to alter any of Workspace Switcher's settings.

---

### Post by CatKiller on 2011-07-21
> **Rajahal said:**
> Thank you again.  Workspace Switcher has no icon in the panel, 

Then add it :)

Right-click on a blank part of the panel, select Add to Panel... and select Workspace Switcher. You can always remove it once you've changed the number of workspaces.

---

### Post by Rajahal on 2011-07-21
Right-clicking the panel does nothing :confused:

I've seen screenshots of the workspace switcher applet in the panel on older versions of Ubuntu, so I know what it is supposed to look like.  I'm using the same version you are (11.04), but with all unity settings at default.  Maybe I need to temporarily disable unity?

---

### Post by TerribleLIar on 2011-07-21
Try opening a terminal and enter this:

```
gconftool-2 --type=int --set /apps/metacity/general/num_workspaces 1


```

I found it here: [http://www.linuxnov.com/how-to-change-number-of-workspaces-on-ubuntu-10-10-netbook/](http://www.linuxnov.com/how-to-change-number-of-workspaces-on-ubuntu-10-10-netbook/) It's for 10.10 Netbook edition, but that used Unity as well, so it should still apply.

---

### Post by Rajahal on 2011-07-21
> **TerribleLIar said:**
> Try opening a terminal and enter this:

```
gconftool-2 --type=int --set /apps/metacity/general/num_workspaces 1


```

I found it here: [http://www.linuxnov.com/how-to-change-number-of-workspaces-on-ubuntu-10-10-netbook/](http://www.linuxnov.com/how-to-change-number-of-workspaces-on-ubuntu-10-10-netbook/) It's for 10.10 Netbook edition, but that used Unity as well, so it should still apply.

Thank you!  I think it worked?  LibreOffice writer is opening in the first workspace now, so that's definitely an improvement.  I can still access the other three workspaces from the icon, but I assume I can just delete the icon and be done with it.  Thanks again!

---

### Post by winstontj on 2012-03-15
> **Rajahal said:**
> I've noticed two driver-related problems with my system.  First, my built-in microphone does not work (tested using Skype, gchat video, and Sound Recorder).  As there's no Linux driver supplied by Acer, is there any way to get it working?

Has anyone found a solution to this?

Also the touchpad on/off button isn't working properly - the button seems to work (toggle, LED works and it turns off) but then when I try to turn the touchpad back on the mouse is frozen on the screen. 

Need microphone functionality or else this needs to go back to a simple W7x86 install. 

Thx.

---

### Post by rg4w on 2012-03-15
> **CatKiller said:**
> Then add it :)

Right-click on a blank part of the panel, select Add to Panel... and select Workspace Switcher. You can always remove it once you've changed the number of workspaces.
If there's a way to do that in 11.10 please let me know.  

The two-step process to switch workspaces in the Launcher isn't nearly as effective for me as the older workspace switcher in the panel, but I've not been able to figure out how to add one in 11.10.

---

