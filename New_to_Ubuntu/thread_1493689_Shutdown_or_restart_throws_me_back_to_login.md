---
title: "Shutdown or restart throws me back to login"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by Lokiii on 2010-05-26
So, this is another issue that just now occurred after booting up this morning. 

If I restart or shutdown from the shutdown menu, the screen goes black and Im back at the login screen. 

If I do a sudo reboot, then the computer reboots instantly. 

If I do a sudo shutdown now, then I get the ubuntu loading screen which eventually freezes..

Any ideas?

Thanks!

---

### Post by Jakiejake on 2010-05-26
Uhhhh
Check the settings
Make sure it's not set to login with password
Some program could have done it...

---

### Post by drpjkurian on 2010-05-26
Hi
I am using Dell vostro laptop with Kubuntu Lucid  with dual display managers (Gnome & KDE).

I always used to Shut down myy machine by pressing(Do not press & hold) the power button.

It Shuts down without any glitch. Try this

---

### Post by garvinrick4 on 2010-05-26
If nothing else works use this code in a terminal if you just want to shutdown or restart until you get it figured out.

restart
```
sudo shutdown -r now

```
shutdown
```
sudo shutdown -h now
```

Just incase that helps you.

---

### Post by Lokiii on 2010-05-26
Problem is that, as I mentioned, if I do a shutdown from the terminal, it just hangs at the ubuntu loading screen.

---

### Post by philinux on 2010-05-26
> **Lokiii said:**
> Problem is that, as I mentioned, if I do a shutdown from the terminal, it just hangs at the ubuntu loading screen.

What are your hardware specs. On launchpad there are a few bugs like this. Some seem plymouth related others graphics cards and some acpi.

---

### Post by Lokiii on 2010-05-26
It doesnt happen when I use the 2.6.32-21-generic kernel. These problems all started after doing the 2.6.32-22 update :(

---

### Post by philinux on 2010-05-26
> **Lokiii said:**
> It doesnt happen when I use the 2.6.32-21-generic kernel. These problems all started after doing the 2.6.32-22 update :(

Right then I would stick with 2.6.32-21 then for now or test out the mainline kernel. This problem for you seems hardware specific.

I would simply remove the offending kernel.

---

### Post by Jakiejake on 2010-05-27
> **Lokiii said:**
> Problem is that, as I mentioned, if I do a shutdown from the terminal, it just hangs at the ubuntu loading screen.

Because Someone always has to be different

---

### Post by zcacogp on 2010-05-27
> **Lokiii said:**
> Problem is that, as I mentioned, if I do a shutdown from the terminal, it just hangs at the ubuntu loading screen.Here as well. Only it doesn't hang at the ubuntu load screen, it hangs with a black (but illuminated) screen and the machine still on. 


Oli.

---

