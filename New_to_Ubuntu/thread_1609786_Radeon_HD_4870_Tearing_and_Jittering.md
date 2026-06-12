---
title: "Radeon HD 4870 Tearing and Jittering"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by FearTheNoFear on 2010-10-30
I have a ATI Radeon HD 4870 with some horrible tearing. I notice it in every video as well as some basic flash games. It doesn't matter if it's 360p or 720p that it screen tears. There is two horizontal lines on the videos that it tears. One near the top and one near the bottom. Now for the jittering, it seems to be any stream like youtube, channelsurfing.net, or any other service that when it's put to full screen it jitters. The sound keeps going like it's still playing video perfectly. Now if it stays at the scaled version it works fine besides the tearing. I have taken a search online and didn't really find anything that helps. Right now I have the FGLRX proprietary drivers enabled (System > Administration > Additional Drivers). I am using Maverick Meerkat Ubuntu. Thanks in advance for your help.

---

### Post by cpmman on 2010-10-31
If you are using Firefox have you tried the FLASH-AID add-on from lovinglinux?

---

### Post by P4man on 2010-10-31
I have the same card, and while Im not exactly happy with the ATI drivers, I cant say I have the same issue, unless I run a windows app through wine. That causes massive flickering in the areas you describe, but it goes away after the app loaded. Probably not much help but thought Id share anyway.

---

### Post by FearTheNoFear on 2010-10-31
Well, it's in both browsers. Firefox and Chrome. It seems like it happens the same amount in both browsers. Screen tearing happens outside of the browsers. I can try the FLASH-AID and see if it'll work better. I wonder why P4man isn't having the same issues that I am having unless if it's just because of different vendors and what not.

---

### Post by sandyd on 2010-10-31
> **FearTheNoFear said:**
> I have a ATI Radeon HD 4870 with some horrible tearing. I notice it in every video as well as some basic flash games. It doesn't matter if it's 360p or 720p that it screen tears. There is two horizontal lines on the videos that it tears. One near the top and one near the bottom. Now for the jittering, it seems to be any stream like youtube, channelsurfing.net, or any other service that when it's put to full screen it jitters. The sound keeps going like it's still playing video perfectly. Now if it stays at the scaled version it works fine besides the tearing. I have taken a search online and didn't really find anything that helps. Right now I have the FGLRX proprietary drivers enabled (System > Administration > Additional Drivers). I am using Maverick Meerkat Ubuntu. Thanks in advance for your help.
enable vsync.

catalyst 10.10 should have fixed a whole bunch of those tearing issues. (or rather, that is what most people report)

---

### Post by FearTheNoFear on 2010-10-31
How do you enable Vsync? I don't see it in the CCC. Also, how do you tell what your version of CCC is? I have vertical refresh always on which I thought would fix it but maybe updating CCC to 10.10 will help. Is there any way to add that to the sources so it automatically updates?

---

### Post by sandyd on 2010-10-31
> **FearTheNoFear said:**
> How do you enable Vsync? I don't see it in the CCC. Also, how do you tell what your version of CCC is? I have vertical refresh always on which I thought would fix it but maybe updating CCC to 10.10 will help. Is there any way to add that to the sources so it automatically updates?

[s]im not sure how to vsyncvsync in ubuntu because I use KDE SVN.[/s]
You are, however using the latest driver already.

EDIT:
wait. you using compiz?
If you do, enable vsync there.

---

### Post by FearTheNoFear on 2010-10-31
> **sandyd said:**
> 
You are, however using the latest driver already.

EDIT:
wait. you using compiz?
If you do, enable vsync there.

I don't seem to be using compiz. It was on normal effects but there isn't any button to customize settings. I'm looking in the right menu by right clicking on the desktop then going to change desktop background then go to effects right?

---

### Post by sandyd on 2010-10-31
> **FearTheNoFear said:**
> I don't seem to be using compiz. It was on normal effects but there isn't any button to customize settings. I'm looking in the right menu by right clicking on the desktop then going to change desktop background then go to effects right?

```

sudo apt-get install compizconfig-settings-manager
compizconfig-settings-manager

```

---

### Post by sandyd on 2010-10-31
> **FearTheNoFear said:**
> I don't seem to be using compiz. It was on normal effects but there isn't any button to customize settings. I'm looking in the right menu by right clicking on the desktop then going to change desktop background then go to effects right?

also, vsync is called "wait for vertical refresh" in catalyst control center

---

### Post by FearTheNoFear on 2010-10-31
> also, vsync is called "wait for vertical refresh" in catalyst control center
I thought that's what it was considered as. Alright, I'll install that and see if it does any better.

---

### Post by FearTheNoFear on 2010-10-31
I wasn't able to find the vsync in the compiz manager settings. I did find sync to vblank: only performs update during vertical screen blanking period.

---

### Post by P4man on 2010-11-01
IN catalyst control center, go to 3D > More settings > wait for vertical refresh. Try setting it to quality / always on.

---

### Post by FearTheNoFear on 2010-11-01
> **P4man said:**
> IN catalyst control center, go to 3D > More settings > wait for vertical refresh. Try setting it to quality / always on.

It's already on always on, that's why I'm so confused on why it's having horrible video issues. It doesn't have any problems in Windows besides some tearing in video games but not real noticeable.

---

### Post by FearTheNoFear on 2010-11-05
Alright, so I decided to uninstall the proprietary drivers and then I was going to reinstall them. Well, this is running better without proprietary drivers being installed but my fan on the vid card is running higher. These 4870's for some reason have a loud fan. The video at full screen doesn't have nearly as much jittering as it used to. There isn't any screen tearing either so I'm not sure what the real problem is now because I thought the quality would be worse but it's actually better after getting rid of the proprietary drivers.

---

### Post by P4man on 2010-11-05
With the opensource driver, you can lower the clocks on your card which reduces the fan. Try this in a terminal:
```

sudo bash -c 'echo low > /sys/class/drm/card0/device/power_profile'

```

You can view the setting with

```
cat /sys/kernel/debug/dri/0/radeon_pm_info
```

Change low to high if you want performance (and noise).

BTW, I got the same card. Proprietary drivers seem to work okayish for me in gnome, but they are a disaster in KDE.

---

### Post by FearTheNoFear on 2010-11-05
Thanks, that helped bring the fan down. I always wondered why ATI doesn't give good support for linux.

---

