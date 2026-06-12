---
title: "icewm blank black window on startup"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by a.sarkar on 2010-10-16
Dear All,

Recently I was trying to shift my focus to icewm. However after installing
icewm and using the startup script a small blank, black window has started to appear
on the top left corner with "X" as the icon. (Check screenshot). I can't close it.

I know it probably has to do with starting X, but it's bugging me.
How do I remove/hide the small blank, black window from my desktop, panel, window-list on each startup?

My ~/.icewm/startup script is the following:
```

## D-bus
if which dbus-launch >/dev/null && test -z "$DBUS_SESSION_BUS_ADDRESS"; then
    eval `dbus-launch --sh-syntax --exit-with-session`
fi

xrdb -load ~/.Xdefaults
xscreensaver -no-splash &
update-notifier &
nm-applet --sm-disable &
ibus-daemon -rd &

```

---

### Post by jtarin on 2010-10-16
In a terminal issue the command ```
xwininfo 
```and click in the subject window and post the output from the terminal.

---

### Post by a.sarkar on 2010-10-16
Thanks for the quick reply jtarin. The output of "xwininfo" is 

```

xwininfo: Window id: 0x1200243 (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 36
  Height: 53
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: yes
  Corners:  +0+0  -1244+0  -1244-747  +0-747
  -geometry 36x53+0+0

```
In the mean time I think I have found out what the problem is. Couple of apps in my startup script were probably starting before Icewm. Like if I add "idesk" to my startup script then it's better to add the line
```
(sleep 2 && idesk) &
```instead of
```
idesk &
```If I add the sleep command, the blank, black window on the upper left corner is no more. Let me know if I have diagnosed the problem correctly or not.

---

### Post by jtarin on 2010-10-16
I believe you have.....I remember running Idesk in the distant past and had something similar to take care of.

---

### Post by a.sarkar on 2010-10-16
Thanks.
Now the black window appears randomly. Sometimes it appears, sometimes it doesn't while logging in. I guess I have to play with the time of sleep commands for the various apps that I am using. Otherwise I think I will go back to openbox.

---

