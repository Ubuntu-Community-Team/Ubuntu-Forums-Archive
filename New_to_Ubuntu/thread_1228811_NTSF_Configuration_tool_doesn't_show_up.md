---
title: "NTSF Configuration tool doesn't show up"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by pbateman on 2009-08-01
Hi guys,
I was trying to install the NTFS configuration tool to mount my NTFS drives permanently as mentioned in the Psychocats webpage. Everything seems to go ok, I go into Add/remove, installed it with no problems but when I go into Applications>System Tools> it does not show up.
I went to System>preferences>main menu but it is not even listed there so  I could add it.
If i go into Add/remove and look under installed apps, it does show up there. I've tried uninstalling and reinstalling it again but same results....
Any ideas?
Thanks!!

ps. If i go into the run application dialog box and try to pick from the list, it does not show it there.

---

### Post by Bucky Ball on 2009-08-01
ntfs-3g are you talking about? It is in there repositories and advisable to install from there unless there is some specific reason not to. That way it will be updated.

If it is that, you could try pasting this in a terminal:

```
sudo ntfs-3g
```

---

### Post by pbateman on 2009-08-01
I'm not sure if there's a ntfs and an ntfs 3g. When I go into add/remove programs it only shows it as NTFS
But towards the end of the description it lists a separate page for each..
I ran the sudo command you mentioned and got:
ntfs-3g: No device is specified.
I don't know if that command was to actually mount the drive and should have been followed by something else?

[IMG]http://i113.photobucket.com/albums/n230/typ8lbb/Screenshot-Add-RemoveApplications.png[/IMG]


Thanks!

---

### Post by Bucky Ball on 2009-08-01
Nope, it is actually called ntfs-3g. Search for that and install. When you run it (it will be in the drop down list; system I think), it will identify your NTFS disks and ask which ones you want added to your fstab so they will mount at boot. That easy.

---

### Post by pbateman on 2009-08-01
Thanks! Got it! I was looking under Applications>system tools..(like it shows on the website)
I looked under System, as you said, and its showing there!

---

### Post by Bucky Ball on 2009-08-01
Yea, you need to be root (sign in) to do stuff like that. :)

---

