---
title: "Automating certain things on startup..."
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Dreakon on 2010-01-14
I'm just curious if there's some way to automate certain things on startup.

1. My bluetooth mouse.  It seems upon rebooting it disconnects it, then refuses to reconnect it (even when I select for it to do so)... so I end up having to remove it and set it up all over again.  Any way to keep it always discovered and functional whenever I turn it or the computer on?

2. My other partition.  It seems I have to remount it every time I restart the computer.  For example, my wallpaper wont appear until I do so since all of my image files are on that partition.  Any way to make it so I don't have to do that and my wallpaper will appear normally on startup? :)

Thanks guys!

---

### Post by drs305 on 2010-01-14
> **Dreakon said:**
> 2. My othe[r]("http://ubuntuforums.org/showthread.php?&t=283131") partition.  It seems I have to remount it every time I restart the computer.  For example, my wallpaper wont appear until I do so since all of my image files are on that partition.  Any way to make it so I don't have to do that and my wallpaper will appear normally on startup? :)

Thanks guys!

Is it mounted initially or is it not mounted at all. You can use the "mount" command as soon as you get to the desktop to see what is mounted. 

If it isn't mounted, you can put the partition into /etc/fstab so that it mounts automatically on boot. bodhi_zazen wrote a tutorial on fstab that provides instructions:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

If it is already mounted but you have to remount it, you could add a script in /etc/init.d/rc.local which remounts it after a given number of seconds (sleep=) so you don't have to do it manually.

---

