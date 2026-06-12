---
title: "Starup Progs"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-31
I have already disabled bluetooth on start-up, for I know for a fact that I don't need it. However, there are some things that I'm not completely sure about, so I was wondering if it's safe to delete these.

- AT SPI Registry Wrapper
- GNOME Keywring Daemon Wrapper
- GNOME Setting Daemon
- GNOME Setting Daemon Helper
- GNOME Splash Screen
- Print Queue Applet
- PulseAudio Session Management
- Remote Desktop
- User folders update
- Window Manager

---

### Post by marcusesses on 2008-12-31
> **adobrakic said:**
> I have already disabled bluetooth on start-up, for I know for a fact that I don't need it. However, there are some things that I'm not completely sure about, so I was wondering if it's safe to delete these.

- AT SPI Registry Wrapper
- GNOME Keywring Daemon Wrapper
- GNOME Setting Daemon
- GNOME Setting Daemon Helper
- GNOME Splash Screen
- Print Queue Applet
- PulseAudio Session Management
- Remote Desktop
- User folders update
- Window Manager

I'd be wary of deleting anything until you know how it will affect your system.

For example, the GNOME daemons runs GNOME desktop processes in the background, so you may be disabling your desktop by uninstalling those. I think Window Manager also manages features on your desktop.

I'd search individually for what each program does, and then decide if you can live without what it provides (e.g desktop, sound, GUI, etc.).

---

### Post by linux_tech on 2008-12-31
I unchecked most of those in sessions and it hasn't made much difference in anything.
Window manager is a good idea to leave on.

---

