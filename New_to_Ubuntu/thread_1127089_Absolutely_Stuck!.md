---
title: "Absolutely Stuck!"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by brandoncolorado on 2009-04-16
Hi everyone,

I installed the netbook remix on my netbook.  I had it working great.  I switched to regular desktop mode, logged out, and logged back in.  Now I can only see the desktop and no panels.  I can't figure out how to switch back to netbook desktop.  I have tried these things:

1) alt+f2 doesn't work to start terminal
2) alt+prtscr doesn't work to take a screenshot
3) I got browser open by starting some random file.
4) restarting


What is my next step?

---

### Post by balaknair on 2009-04-16
I'm not familiar with the netbook remix interface, but can you select the type of login session at the GDM login menu(assuming you see a login menu).

---

### Post by njpatel on 2009-04-16
> **brandoncolorado said:**
> Hi everyone,

I installed the netbook remix on my netbook.  I had it working great.  I switched to regular desktop mode, logged out, and logged back in.  Now I can only see the desktop and no panels.  I can't figure out how to switch back to netbook desktop.  I have tried these things:

1) alt+f2 doesn't work to start terminal
2) alt+prtscr doesn't work to take a screenshot
3) I got browser open by starting some random file.
4) restarting


What is my next step?


1. Right-click on the desktop and select "Create Launcher"
2. As the "Command", type "gnome-terminal" (without quotes)
3. Double-click and you should get a terminal open
4. Run `gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]` (without quotes)
5. Reboot, things should be fine.

You can find some more information on my post [http://ubuntuforums.org/showpost.php?p=7081942&postcount=8](http://ubuntuforums.org/showpost.php?p=7081942&postcount=8).

Thanks,

Neil

---

### Post by brandoncolorado on 2009-04-17
Thanks,

For people that find this thread with the same problem, this is a known bug.  I can't find it right now.  The bug thread states that you can delete some config files to get back to the working layout until the bug is fixed.

---

