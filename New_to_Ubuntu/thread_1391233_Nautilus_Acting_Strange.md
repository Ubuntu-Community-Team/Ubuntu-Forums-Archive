---
title: "Nautilus Acting Strange"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Wataru8675 on 2010-01-26
Tried posting this in General Help, but I'm not getting any hits at all...  Hopefully someone here will know:

Hello,

I just popped in an UberStudent DVD I burned this morning to test drive the new sub-distro, and when I checked the DVD for errors on startup, and there apparently were some because nothing happened for several minutes.  I ejected the CD and was "forced" (at least I couldn't figure out another way to do it) to force shutdown my computer.  When I started it back up and logged in, my desktop wasn't there.  I ran "nautilus" in the terminal and everything popped up, but the terminal also gave me this message:
> ** (nautilus:4030): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
I then found that if I close the terminal (and thus killing the process), my Desktop again disappeared.

Any ideas as to what needs to be done?

---

### Post by warfacegod on 2010-01-26
Sounds like you need to reinstall gnome desktop:

Go to System> Admin.> Synaptic> Search fro gnome-desktop and mark it for reinstallation click apply.

---

