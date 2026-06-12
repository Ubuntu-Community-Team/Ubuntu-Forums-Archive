---
title: "Problem w/ Flash &amp; Chrome"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by psychx on 2010-07-13
I am running Ubuntu 10.04 LTS and am using Google Chrome as my internet browser. Flash is lagging on websites, and I have seen a few threads about this already. So, I will try to be as helpful as I can.

I will post plugins that are currently running in Google Chrome:
```

1. Shockwave Flash (10.1 r53)
   /opt/google/chrome/libgcflashplayer.so
2. Shockwave Flash (10.1 r53)
   /opt/google/chrome/plugins/libflashplayer.so
3. iTunes Application Detector
   /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so
4. Shockwave Flash 10.1 r53
   /usr/lib/adobe-flashplugin/libflashplayer.so
5. VLC Multimedia Plugin (compatible Totem 2.30.2)
   /usr/lib/mozilla/plugins/libtotem-cone-plugin.so
6. Windows Media Player Plug-in 10 (compatible; Totem)
   /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
7. DivX Web Player version 1.4.0.233
   /usr/lib/mozilla/plugins/libtotem-mully-plugin.so
8. QuickTime Plug-in 7.6.6
   /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so

```

I believe that I may have messed something up when trying to fix the problem myself. Before I thought to check if a Flash plugin was already running in Chrome, I copied a plugin that I found by searching in Terminal to the Chrome plugins directory. Or so I thought.

Any help is appreciated, and I will reply if anything changes. Thank you very much!

- Mike "psychx"

---

### Post by psychx on 2010-07-13
I just realized that my graphics driver wasn't activated. I activated that, restarted - but still have the same problem with flash.

---

### Post by Twitch6000 on 2010-07-13
> **psychx said:**
> I just realized that my graphics driver wasn't activated. I activated that, restarted - but still have the same problem with flash.

Silly question,but is this happening in firefox aswell?

---

### Post by psychx on 2010-07-13
> **Twitch6000 said:**
> Silly question,but is this happening in firefox aswell?

It appears to be lagging as well, but possibly not as bad. Still annoying, even in Firefox.

---

### Post by rolleander on 2010-07-13
Are you using the flash-plugin from the repositories or from adobe's website?

Just cuz I found the one from Adobe to work better for some reason

Try uninstalling the plugin and go to 

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by TBABill on 2010-07-13
Remove gnash via synaptic. You already have adobe flash and they may be conflicting.

---

### Post by psychx on 2010-07-13
> **TBABill said:**
> Remove gnash via synaptic. You already have adobe flash and they may be conflicting.

When I search "gnash" in Synaptic, it shows a few entries. None of them are showing as installed.

---

### Post by psychx on 2010-07-13
> **rolleander said:**
> Are you using the flash-plugin from the repositories or from adobe's website?

Just cuz I found the one from Adobe to work better for some reason

Try uninstalling the plugin and go to 

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

This may be a stupid question, but how should I go about uninstalling the plugins? Through Synaptic? Or is there a different way?

---

### Post by Cityscape on 2010-07-13
If you installed Flash from the repositories I would uninstall it and use the one that you can download from Adobe's website.

---

### Post by rolleander on 2010-07-13
Well, uninstalling flash from synaptic should uninstall it completely - but you can also disable the plugins from the browsers preferences - not sure if you need to do both...

---

### Post by psychx on 2010-07-13
> **rolleander said:**
> Well, uninstalling flash from synaptic should uninstall it completely - but you can also disable the plugins from the browsers preferences - not sure if you need to do both...

Ok, I just disabled plugins 2, 3, and 4 [according to my list at the top]. I uninstalled adobe's flash plugin from Synaptic. I went to adobe's website, and downloaded the APT file from them and installed flash. It appears to still be lagging.

---

### Post by Twitch6000 on 2010-07-13
Do you have compiz enabled? if so disable it. I have found when I have compiz enabled almost anything lags for me.

---

### Post by psychx on 2010-07-13
> **Twitch6000 said:**
> Do you have compiz enabled? if so enable it. I have found when I have compiz enable almost anything lags for me.

This seems to have fixed it for the most part. Videos are running must smoother.

---

### Post by Twitch6000 on 2010-07-13
> **psychx said:**
> This seems to have fixed it for the most part. Videos are running must smoother.

Yep that is the problem. I am glad this has solved the issue for you. Why anyone has compiz by default always confuses me. It is buggy :/.

To uninstall compiz just use synaptic.

---

### Post by psychx on 2010-07-13
Thank you very much!

---

### Post by Twitch6000 on 2010-07-13
> **psychx said:**
> Thank you very much!

No Problem =].

---

### Post by Demolition Man on 2010-07-13
I am having a similar problem. I followed all the advice in this thread and I can play most videos in Firefox without a problem (except hulu videos, no luck there), but flash videos in Chrome are still laggy. For example, full Daily Show episodes play fine in Firefox but play extremely choppy in Chrome. Is this a Chrome issue? TIA.

---

### Post by psychx on 2010-07-13
> **Demolition Man said:**
> I am having a similar problem. I followed all the advice in this thread and I can play most videos in Firefox without a problem (except hulu videos, no luck there), but flash videos in Chrome are still laggy. For example, full Daily Show episodes play fine in Firefox but play extremely choppy in Chrome. Is this a Chrome issue? TIA.

Hey, I'm just wondering - did you make sure to activate your video driver? System > Administration > Hardware Drivers

---

### Post by Demolition Man on 2010-07-13
It says no proprietary drivers installed.

---

### Post by psychx on 2010-07-13
> **Demolition Man said:**
> It says no proprietary drivers installed.

Do you know what graphics card is in your computer?

By the way, I attached an image of what mine looks like.

---

### Post by Demolition Man on 2010-07-14
> **psychx said:**
> Do you know what graphics card is in your computer?

By the way, I attached an image of what mine looks like.

It's a netbook, ASUS EeePC 1005HAB. I've tried looking for drivers on the ASUS website, but there are none listed for Linux.

---

### Post by psychx on 2010-07-14
> **Demolition Man said:**
> It's a netbook, ASUS EeePC 1005HAB. I've tried looking for drivers on the ASUS website, but there are none listed for Linux.

Looks like you're using an Intel GMA 950 video card in that netbook. [http://en.wikipedia.org/wiki/Intel_GMA#GMA_950](http://en.wikipedia.org/wiki/Intel_GMA#GMA_950)

You might not need to enable any driver, it looks like it is using open-source drivers that come with Linux. Though, someone else might know more. I did find an old post on this forum, which can be found here: [http://ubuntuforums.org/showthread.php?t=215578](http://ubuntuforums.org/showthread.php?t=215578)

I hope you can use some of this information.

---

### Post by Demolition Man on 2010-07-14
> **psychx said:**
> Looks like you're using an Intel GMA 950 video card in that netbook. [http://en.wikipedia.org/wiki/Intel_GMA#GMA_950](http://en.wikipedia.org/wiki/Intel_GMA#GMA_950)

You might not need to enable any driver, it looks like it is using open-source drivers that come with Linux. Though, someone else might know more. I did find an old post on this forum, which can be found here: [http://ubuntuforums.org/showthread.php?t=215578](http://ubuntuforums.org/showthread.php?t=215578)

I hope you can use some of this information.

Using Sysinfo I found out I have an Intel 945GME graphics controller. The driver I currently have installed is "X.org X Server -- Intel i8xx, i9xx display driver." Not sure if that's the best one.:/

---

### Post by renkinjutsu on 2010-07-14
> **psychx said:**
> 
```

1. Shockwave Flash (10.1 r53)
   /opt/google/chrome/libgcflashplayer.so
[B]2. Shockwave Flash (10.1 r53)
   /opt/google/chrome/plugins/libflashplayer.so
[/B]3. iTunes Application Detector
   /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so
4. Shockwave Flash 10.1 r53
   /usr/lib/adobe-flashplugin/libflashplayer.so
5. VLC Multimedia Plugin (compatible Totem 2.30.2)
   /usr/lib/mozilla/plugins/libtotem-cone-plugin.so
6. Windows Media Player Plug-in 10 (compatible; Totem)
   /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
7. DivX Web Player version 1.4.0.233
   /usr/lib/mozilla/plugins/libtotem-mully-plugin.so
8. QuickTime Plug-in 7.6.6
   /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so

```

- Mike "psychx"

I noticed that you have two Flash player plugins in your plugins page. Disable the second one..

libgcflashplayer.so is the one that comes WITH the chrome package.. try disabling the other one from the about:plugins page

---

