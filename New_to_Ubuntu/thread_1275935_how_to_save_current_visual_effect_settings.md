---
title: "how to save current visual effect settings"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by infotechwizkid on 2009-09-26
Hello guys i'm Dave from the Philippines. And i just want to ask how to save the visual settings for EXTRA ? And the different effects seetings that i do in my desktop.
As you can see there are 3 visual effect settings in appearance preferences such as:
1.None
2.Normal
3.Extra
Here's the scenario , when i already finished setting up my CCSM and shutdown my computer. And turn it on again,the settings that i made did not save. And as i noticed that in the visual effect as i mention above there is no check in any of the 3 options. As i check the extra option. The wobbly windows automaticaly enable and as i disable the wobbly window. It give me same result and the settings that i made did not save and it goes back when i started. Pls if anyone knows how to fix this problem pls give me a detailed steps on how will i fix this problem and save my settings so that when linux starts the settings that i made is still there. I hope that somebody will reply to this thread as soon as possible, thanks =)

Here's my specs i think it will help u out to fix my problem:
CPU:Interl Dual Core 2.5
RAM: 1GB - but i shared 64mb of it's memory to the on board video which gives me a 256Mb of video on board.
Mobo: XFX 
Hard Disk: 80GB IDE

Well that's all i hope that somebody will help me =)

---

### Post by drs305 on 2009-09-26
I am going from memory as I don't use Compiz any longer - there used to be an issue of not seeing any of the selections but if you don't see "None" - even if the other two aren't showing enabled - it meant you were using Compiz. To see them, I believe you had to install simple-ccsm. There is now a better Compiz Settings manager called CompizConfig-Settings-Manager. 
Install it via Synaptic (compizconfig-settings-manager) or via terminal:
```

sudo apt-get install compizconfig-settings-manager

```
Once you install it, you *may* see the selected mode in System, Preferences: Appearance.

Now, once installed, you can also *save* your settings. Again, I'm doing this from memory, but I believe you start CCSM (System Preferences, CompizConfig Settings Manager. Go to Preferences then there is an Export button with which you can save your current settings. Once saved, you can Import them again.

---

