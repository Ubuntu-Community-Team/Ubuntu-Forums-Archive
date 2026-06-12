---
title: "Make SUDO ask for password every time?"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by RichieB07 on 2011-01-21
I'm dual-booting 10.10 with Windows 7, and I was really just trying to find a way to make sudo ask for a password every time.  I have my UAC in Windows turned on to "Always Ask", so I'm used to it.

I know there's a way to do it, but I couldn't even find it on Google (maybe I'm searching the wrong thing).

Any help would be awesome.

---

### Post by lotus@terminal on 2011-01-21
Do you want it to ask you for the root password or your 'current' user password?

---

### Post by RichieB07 on 2011-01-21
I want it to ask for my password every time I start Synaptic, or Update Manager, or run a command that starts with "sudo".  So I'm guessing that's my user password.

---

### Post by mastablasta on 2011-01-21
it asks always when it will do changes to system files. sudo ocmmand saways require password. so does update manager, synaptic and such as soon as you want to install something.

---

### Post by RichieB07 on 2011-01-21
But I want it to ask every time, not every 5 minutes or so.

---

### Post by entangled on 2011-01-21
You could read 'man sudoers'. You need to set the sudo timeout to 0.

---

### Post by yetiman64 on 2011-01-21
Setting sudo timeout to 0, will do that. [[COLOR=Blue]--Link to instructions--[/COLOR]]("https://help.ubuntu.com/community/RootSudoTimeout")

> where X is the timeout expiration **in minutes**. If you specify 0 you will always be asked the password.

---

### Post by lotus@terminal on 2011-01-21
Setting the sudo timeout will fix your problem then. :)

---

### Post by RichieB07 on 2011-01-21
I just did this and it worked perfectly!

---

