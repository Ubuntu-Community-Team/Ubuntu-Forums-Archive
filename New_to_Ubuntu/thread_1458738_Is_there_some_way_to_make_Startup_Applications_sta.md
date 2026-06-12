---
title: "Is there some way to make Startup Applications startup Minimized?"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by brucewagner on 2010-04-20
Is there some way to make Startup Applications start Minimized?  (or toggled off, only appearing in the task tray -- like Transmission or Skype or...)

I know you can in Windows...  But I've never been able to figure out how to so that in Ubuntu....

---

### Post by utnubuuser on 2010-04-20
You might want to try Alltray or Kdocker.

Alltray/kdocker minimizes all apps to tray, and one way to go about it is to install alltray or kdocker, then prefix the application's launch command with 'alltray'.

I'm running 8.04, so all the "Seesion/startup apps" and their launch commands are accessible through System>>Preferences>>Sessions. "Sessions" also remembers running apps at shutdown.

Another approach might be to go through gconf-editor (Alt+F2>>gconf-editor), and prefix your applications' launch commands with "alltray or kdocker".

Kdocker is probably more configurable, and applications prefixed with kdocker will open, then immediately be parked in the tray.

---

### Post by Seq on 2010-04-20
"Startup applications" just fires off a bunch of applications on log-in, so they don't know to start minimized or not.

Some applications support an option you can add to their command line. For example, `empathy -h` causes empathy to start, but in it's hidden mode.

Others do not support this. For those, you may want to look at something like devilspie to configure their behaviour.

---

### Post by utnubuuser on 2010-04-22
I've just switched to kdocker, and one of the options in the configuration menu is to have the apps opened at startup.

---

