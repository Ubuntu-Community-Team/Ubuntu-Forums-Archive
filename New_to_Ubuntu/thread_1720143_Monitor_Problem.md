---
title: "Monitor Problem"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by Crash 0verride on 2011-04-02
Alright I am running Ubuntu Desktop Edition on my laptop. It has been great so far. I have a nice screen on my monitor but I wanted to watch movies using my Desktop monitor and this monitor I don't want to make them one big monitor I want to make them two Identical Monitors as in they both show the same thing at the same time.

I am currently running Ubuntu 10.10 and Have a NVIDIA Go 7000 Series card so I am running restricted graphics card drivers I chose the one that said [Recommended] on installation. It came packaged with this NVIDIA X Server Config program.

I am a 3 year off and on user of ubuntu but I know my way around the Ubuntu Distro and if you give me a terminal input I can do it.

Any help would be appreciated.

---

### Post by fabricator4 on 2011-04-02
> **Crash 0verride said:**
> watch movies using my Desktop monitor and this monitor I don't want to make them one big monitor I want to make them two Identical Monitors as in they both show the same thing at the same time.

I think this is actually the default operation.  Have you tried just plugging the monitor in?  Go to "Configure display settings" and select "detect monitors" if you have to, then click the box that says "same image in all monitors".

If the monitors are different resolutions and/or different ratios it can cause some odd side effects, but generally you can get it working quite nicely.

Chris.

---

### Post by seawolf167 on 2011-04-02
System -> Preferences -> Monitors -> Choose to "Mirror Monitors"

You can also do this through any video driver suites you may have installed

---

### Post by Crash 0verride on 2011-04-05
It will not allow me to open the monitor menu as I have a application that came packaged with my driver called NVIDIA X Server Settings. There is also the issue of there being no option like that in NVIDIA X Server Settings.

I might try it on a clean install or Live CD to see if by default it is mirroring the monitors. Because by default with NVIDIA X Server it has the 2nd Monitor Disabled and I have the monitor Setup for VGA and DVI the DVI setting is for my Desktop why the VGA Setup is for my laptop if the Monitor does not detect a VGA or DVI setup it will switch to the alternative channel and if there is not one it will just go into standby mode waiting for a visual input.

Right now it has 3 Options

Disabled (Requires X Server Restart)
Twinview (Enabled)
and another option I cant view it

---

### Post by Crash 0verride on 2011-04-05
Update: I found the solution

You have to enable Twinview (Mine is already enabled) and then they have a second one that says Left of, Above, Under, Right of. I really didn't mess with this setting turns out when I looked there was another option **CLONE** fixed the problem instantly. Thanks for your help.

/solved.

---

