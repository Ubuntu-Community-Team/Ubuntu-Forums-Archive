---
title: "No boot after playing with Startup settings"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by nickm57 on 2010-04-25
I've been using Ubuntu 9.10 kernel 2.6.30-21
After playing round with the startup settings ,time out and splash screen size, I can no longer get any of this install to boot. All other grub setting work.
I've been using this install for some months so I'd like it back.
Any way of editing the config files to get the old settings. If so which files.

Thanks Nick

---

### Post by nickm57 on 2010-04-26
I will add all other installs work. Grub is fine it lists all other installs theses all boot.

Is there a way to reinstall this kernel or get a boot log.

When I try recovery mode I can't see where it is stopping as it scrolls to fast.
Then goes to a blank screen.

I'm not familiar with all the start-up commands etc.

---

### Post by warfacegod on 2010-04-26
When you use Recovery mode, does that blank screen have a prompt on it? If so try: startx

Are there any older kernels for that particular install? If so try one of those and fix the problem from there.

---

### Post by nickm57 on 2010-04-26
Hi
The old kernels of that install do the same. They go to a blank screen  no prompt...

thanks

---

### Post by warfacegod on 2010-04-26
Do you have a separate /home partition?

---

### Post by warfacegod on 2010-04-26
Actually wait. Even better can you access your /home folder from another install?

---

### Post by nickm57 on 2010-04-26
Yes I can access  the install, from another ubuntu install.

---

### Post by warfacegod on 2010-04-26
Then do so. If you used say Startup Manager to play with the settings then the appropriate folder would be hidden (Ctrl+H to show) in your /home folder called .startupmanager or something like that. Whatever it is you did, its likely to be one of those hidden .name folders in your /home.

If you happen to have /home as a separate partition, you can do a fresh install to your OS partition and virtually all of your settings with be in place as long as you remember to mark your Home partition as /home again during the manual install. You'll have to reinstall any programs that you installed yourself before but when you do, they also should have their settings back.

---

