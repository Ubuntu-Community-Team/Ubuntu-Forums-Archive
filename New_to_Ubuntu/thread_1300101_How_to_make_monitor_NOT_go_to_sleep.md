---
title: "How to make monitor NOT go to sleep?"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by Julita on 2009-10-24
I get annoyed seeing how my monitor blackens out every 10 or so minutes. Any help would be appreciated! I wonder if there is a command-line way to do this...

---

### Post by corncob on 2009-10-24
> **Julita said:**
> I get annoyed seeing how my monitor blackens out every 10 or so minutes. Any help would be appreciated! I wonder if there is a command-line way to do this...

My default is 40 minutes.  Anyway, go to System > Preferences > Power Management > On AC Power.  Move the "put display to sleep slider" all the way to the right ("never").

---

### Post by barbz127 on 2009-10-24
Also check you screen saver as i believe the default is a blank screen after 10 minutes.
Paul

---

### Post by Julita on 2009-10-24
Thank you for your answers. In fact, I did just that: put the time to "never" and my screensaver is disabled! I do not know what to do. I am really confused...

---

### Post by sisco311 on 2009-10-24
> **Julita said:**
> I get annoyed seeing how my monitor blackens out every 10 or so minutes. Any help would be appreciated! I wonder if there is a command-line way to do this...

what's the output of:
```
grep -i dpms /var/log/Xorg.0.log
```

---

### Post by Julita on 2009-10-24
I have removed gnome-power-manager from autostarted applications; now I have enabled it. It might be the right solution.

---

### Post by Julita on 2009-10-24
```
 grep -i dpms /var/log/Xorg.0.log
(II) Loading extension DPMS
(II) RADEON(0): DPMS enabled 
```

---

### Post by sisco311 on 2009-10-24
You can set the Stanby time in the xorg.conf file:
[http://linuxreviews.org/howtos/power/xorg_dpms/index.html.en]("http://linuxreviews.org/howtos/power/xorg_dpms/index.html.en")

Also you may want to try [caffeine]("http://www.blastfromthepast.se/blabbermouth/2009/10/caffeine-for-linux-1-released/#more-757").

---

### Post by Julita on 2009-10-24
sisco, thank you very much! I did as prescribed! Caffeine is a great option, though! When I read your message, my first thought was how the media player could help, but, oh, THAT is Kaffeine, so I got confused. Thank you very much for this useful info!

---

### Post by Stosskraft on 2009-11-24
```
grep -i dpms /var/log/Xorg.0.log
(II) Loading extension DPMS
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): DPMS enabled
```


This is the output I am getting from the command, it seem different that Juilita has.

Any ideas?

---

### Post by doas777 on 2009-11-24
> **Stosskraft said:**
> ```
grep -i dpms /var/log/Xorg.0.log
(II) Loading extension DPMS
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): DPMS enabled
```
This is the output I am getting from the command, it seem different that Juilita has.

Any ideas?
it's just because you use a differant driver. no signifigant differance.
dpms indicates the monitor power-save feature, so enabling it is the opposite of what the op requested.

---

### Post by DarinB on 2010-02-15
i have the same problem and here is my read out 
I set my power manager to never and added my authentication code when it asked for it. the enabled one below is that the problem or is everything ok now????
darin@darin-desktop:~$ grep -i dpms /var/log/Xorg.0.log
(II) Loading extension DPMS
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): DPMS enabled
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): DPMS capabilities: StandBy Suspend Off
darin@darin-desktop:~$

---

### Post by Julita on 2010-02-16
Hi! You have DPMS turned on. You need it to be turned off. Type in terminal
```
xset -dpms
``` it will be disabled for the current session. If you are using Karmic, in order to make it permanent, you have to create your own file /etc/X11/xorg.conf (in Jaunty the file exists) and uncomment the option DPMS, but first see if disabling it for the session works.

---

