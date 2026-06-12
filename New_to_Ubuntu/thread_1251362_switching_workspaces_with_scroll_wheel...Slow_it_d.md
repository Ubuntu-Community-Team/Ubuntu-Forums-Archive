---
title: "switching workspaces with scroll wheel...Slow it down.."
date: 2009-08-27
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-08-27
any way to slow this feature down so it doesn;t go crazy when i use my scroll pad on my lap top?

if not how do i disable it conpleatly?

thanks

---

### Post by Hospadar on 2009-08-27
If you're in gnome (not kde or xubuntu) you can do this I believe in the compizconfig-settings-manager

first install it, either from synaptic or:
sudo apt-get install compizconfig-settings-manager

then go System->Preferences->Compiz settings (I think is the name? in KDE right now)
And you can poke around in there.  I know for sure at least you can set the number of scroll wheel tics it takes to switch workspaces to something obscenely high so it never happens unless you hook a motor up to your scroll wheel.

---

### Post by mc4man on 2009-08-27
If not already installed then install
```
sudo apt-get install compizconfig-settings-manager
```

Found in System => Preferences -> Advanced Desktop Effects Settings

The desktop wall is a pita to use on a laptop, you can control a bit better by increasing the 'duration' and by not keeping your finger on the scroll area - just tap with a slight up or down bias to go 1 workspace left or right
(duration setting for wall is under "Desktop Wall -> Viewport Switching -> Sliding Wall Duration"

I prefer to enable "Desktop Cube and Rotate Cube" plugins instead. More controllable with default setting, also can be slowed down ( in the Rotate Cube settings -> acceleration

---

