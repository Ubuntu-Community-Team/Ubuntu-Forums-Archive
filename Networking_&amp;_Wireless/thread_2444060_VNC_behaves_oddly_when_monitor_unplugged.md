---
title: "VNC behaves oddly when monitor unplugged"
date: 2020-05-24
forum: Networking &amp; Wireless
---

### Post by richardi99 on 2020-05-24
I have an Intel NUC with the latest version of Ubuntu installed. I have VNC server running on it to allow remote access, because I want to rackmount the NUC without direct-attached KVM and use it as a headless server.  Want to VNC in when I need to.

I can connect fine remotely, and control the NUC, until I unplug its HDMI monitor cable. As soon as I do that I can only view, and cannot remotely control.
Can anyone help me with this please?

---

### Post by richardi99 on 2020-05-25
Ok - so moved forwards one step.  Discovered I need to buy an HDMI monitor emulator. to plug into the HDMI port.  Done that.  Now cannot seem to get VNC to start up at boot so I can VNC into this as a headless NUC.  Have tried two things with no luck: [https://tecadmin.net/setup-x11vnc-server-on-ubuntu-linuxmint/](https://tecadmin.net/setup-x11vnc-server-on-ubuntu-linuxmint/) and [https://tecadmin.net/setup-x11vnc-server-on-ubuntu-linuxmint/](https://tecadmin.net/setup-x11vnc-server-on-ubuntu-linuxmint/).  Any help appreciated

---

### Post by Tadaen_Sylvermane on 2020-05-25
You don't need that. Can be done without it.

[https://askubuntu.com/questions/453109/add-fake-display-when-no-monitor-is-plugged-in](https://askubuntu.com/questions/453109/add-fake-display-when-no-monitor-is-plugged-in)

I used this to run Kodi inside an LXD container on my headless server. Works great. X11VNC and away you go.

Systemd service to restart x11vnc after you exit it. I use for above purpose, rather I did until I changed to another service + script to stream audio out of the container to a remote pulse server. Change user & group as needed.

```
[COLOR=#074454][FONT=Monaco][Unit][/FONT][/COLOR]
[COLOR=#074454][FONT=Monaco]Description = Start and keep X11VNC server running[/FONT][/COLOR]

[COLOR=#074454][FONT=Monaco][Service][/FONT][/COLOR]
[COLOR=#074454][FONT=Monaco]User = kodi[/FONT][/COLOR]
[COLOR=#074454][FONT=Monaco]Group = kodi[/FONT][/COLOR]
[COLOR=#074454][FONT=Monaco]Type = simple[/FONT][/COLOR]
[COLOR=#074454][FONT=Monaco]ExecStart = /usr/bin/x11vnc -display :0[/FONT][/COLOR]
[COLOR=#074454][FONT=Monaco]Restart = always[/FONT][/COLOR]

[COLOR=#074454][FONT=Monaco][Install][/FONT][/COLOR]
[COLOR=#074454][FONT=Monaco]WantedBy = multi-user.target[/FONT][/COLOR]
```

In regards to VNC starting on boot you need something for it to connect to. In my container I have LightDM set to autologin to my kodi user on openbox, which autostarts Kodi. Using lightdm have it autologin to your user and that is it. The above service will keep the vnc server running.

---

### Post by richardi99 on 2020-05-26
Thank you for your help.  I have closed this thread and started another more pertinent to where my issue is now.  I will reply on that one

---

