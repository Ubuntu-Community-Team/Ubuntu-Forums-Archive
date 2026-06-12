---
title: "How to exit if desktop &quot;freezes&quot;"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by limatwo on 2010-02-09
New linux user. My system seems to be stable at the moment, so this is more for my own enlightenment rather than an immediate "fix", if that's alright.
After some issues experimenting dual booting winXP/Ubuntu 8.4 on a different machine, yesterday I installed Ubuntu 9.10 as sole OS on an old dell (specs below). All fine, surfed, watched movies, etc for hours with no problems. This morning ubuntu prompted me to download & install 42 updates. About 80% into the installation, my desktop froze. Not being able to research a solution (frozen desktop!) I eventually turned the machine off/on. I was presented with the grub boot menu (didn't see this previously - presumably because I'm single booting) with options for 2.6.31.19, and 2.6.31.14. 
To cut a long story short, I was not able to load the default option (...19) but was able to load the other (....14).
I then followed prompts to solve a problem with "config defaults for GNOME Power Manager not installed correctly" by typing:
" sudo dpkg --configure -a "
in terminal. I rebooted & all seemed fine until just now when everything froze again while I was using firefox. I had to off/on again, but this time, we booted right back into ubuntu. 
So, my questions:
1/ What to do if all freezes? I understand off/on is a bad option - and after the first time I thought I'd found a (win equivalent ctrl+alt+del) way out, with ctrl+alt+backspace, but that didn't work.
2/ Any ideas why the freezing? I appreciate the machine is old & low spec, but I would have thought sufficient.
3/ "sudo dpkg --configure -a" - I was blindly following instructions by typing this. After doing a bit of research, am I right in thinking this just kickstarts the upgrades that were in process when the system hung, and not anything to to with the cause of the hang itself???

Thanks

System Specs:
Dell Optiplex, onboard vid/sound
Intel P4 1.8 GHz
614 Mb ram
160 Gb HD
Ubuntu 9.10 sole OS

---

### Post by unmole on 2010-02-09
See [this]("http://techspalace.blogspot.com/2008/07/magicsysrq-keys.html") and [this]("http://mytechxp.blogspot.com/2007/10/what-to-do-when-your-linux-system-hangs.html"). Hmmm... I think I'll go write a blog entry of my own on this.

---

### Post by mushwars on 2010-02-09
control + alt + f2

login.

```
sudo /etc/init.d/gdm restart
```


I dont use gdm but I think that will do it.

---

### Post by raymondh on 2010-02-09
Hi ....

1.  You can still enable the combo key (ctr + alt + backspace).

system > preferences > keyboard > layout tab > layout options > 'choose sequence to kill X' > enable ctr + atl + backspace

2.  Seems to me X is having problems.  See if any of [this]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze") can help.

3.  Yes, the command you used is meant to 'jumpstart' any botched update and should not be the cause of the hang/freeze.

Raymond

---

### Post by unmole on 2010-02-09
I really don't think Ctrl+Alt+F2 will work in a situation where Alt+Ctrl+Backspace is not working. Then again, In my 2+ years experience with Linux, I have faced this situation only once so I'am not exactly experienced with regard to this.:lolflag:

---

### Post by foldingstock on 2010-02-09
> **unmole said:**
> I really don't think Ctrl+Alt+F2 will work in a situation where Alt+Ctrl+Backspace is not working. Then again, In my 2+ years experience with Linux, I have faced this situation only once so I'am not exactly experienced with regard to this.:lolflag:

Yes, it will work. "Ctrl+Alt+Backspace" is disabled via the X configurations. "Ctrl+Alt+Fx" (x=1-12) is a system shortcut that drops to a console. This shortcut is not configured by X.

---

### Post by unmole on 2010-02-09
> **foldingstock said:**
> Yes, it will work. "Ctrl+Alt+Backspace" is disabled via the X configurations. "Ctrl+Alt+Fx" (x=1-12) is a system shortcut that drops to a console. This shortcut is not configured by X.

My bad. I mixed up Alt+F2 with Alt+Ctrl+F2

---

### Post by limatwo on 2010-02-09
Thanks all for the tips. Especially the links to troubleshooting x freezes.

---

### Post by philinux on 2010-02-09
Another key combo to kill x.

Alt+SysRq+k

Takes you to the login screen.

---

### Post by Maheriano on 2010-02-09
Whenever this happens to me I just SSH into it from another machine and reboot it from the command line.

---

### Post by jrandolph on 2010-02-09
sometimes i have my system lock up and ctrl+alt+backsapce does nothing
ctrl+alt+F2 does nothing 
so my only option is either the trusty power button or alt+sysrq+b

---

