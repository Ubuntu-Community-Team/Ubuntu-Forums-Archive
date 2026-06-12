---
title: "Intrepid strange issue!!!!"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by bobigeorge on 2008-12-23
Hello everyone...

I have recently upgraded into Ubuntu 8.10 and is impressed with its performance. 

But now after one day, when I started it up the theme was automatically changed.

When I tried to open System->Preferences->Appearance  an error appears

```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

```

Please help me out of this problem...
Thanks in advance.

---

### Post by gettinoriginal on 2008-12-23
Log out, and when the log in window appears, bottom left corner says "options", click on that and choose "gnome".  Log in and it should reset.  :P

---

### Post by bobigeorge on 2008-12-28
Thank you for the reply gettinoriginal.

I have checked your solution... But no luck.. The problem still persists. Pls help me

---

### Post by Rolcol on 2008-12-28
I had this problem when I wanted to change my theme.  I'm not sure how "legal" it is (I don't know how your system will handle) but mine worked fine after killing the Bonobo process.  I didn't have noticeable problems.

---

### Post by bobigeorge on 2008-12-28
Thank you Rolcol. Please tell me how to kill the processes and its consequences..

---

### Post by Rolcol on 2008-12-28
I don't know of any consequences.  The simple way would be to go into System > Administration > System Monitor and look for the bonobo process.  You probably won't be able to kill it from inside System Monitor because I don't think it belongs to you, the user.  You'll probably have to open up a terminal and manually kill it.```
sudo kill _PID_
```Replace _PID_ with the Process ID next to the bonobo name in the System Monitor.  If it doesn't end, add the -9 switch to the command.```
sudo kill -9 _PID_
```

_**Edit**:  I just realized something...  try just running the System Monitor using sudo.  Press alt+f2 and type in: ```
gksu gnome-system-monitor
```It will prompt you for your password.  You'll probably be able to kill the bonobo process without having to do it manually through the terminal._

---

