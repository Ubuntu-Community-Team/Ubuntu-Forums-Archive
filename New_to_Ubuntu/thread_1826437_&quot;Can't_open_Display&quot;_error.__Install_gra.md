---
title: "&quot;Can't open Display&quot; error.  Install graphics drivers?"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by honeycombs_big_yahyahyah on 2011-08-16
Hi Folks,

Just installed Server 11.04 on an old Toshiba A10-sp129 laptop.  This guy has an Intel 852GM chipset.  I also installed Unity, and when I run it, I get a "Can't Open Display" error.  I'm wondering if it's because I haven't installed proper graphics drivers?  I'm not sure how to check (via terminal) if I have the right drivers installed, and if not, how to go about installing them.  Any help greatly appreciated!

Thanks!

Ubuntu Server 11.04 i386
Toshiba A10-SP129
Intel 852GM

---

### Post by linuxman94 on 2011-08-16
Did you install Xorg? 

```
sudo apt-get install xorg
```

Also, why did you choose the server version if you want a graphical interface?

---

### Post by honeycombs_big_yahyahyah on 2011-08-16
Thanks for the reply, linuxman94.  I just wanted access to a GUI, but didn't want to run it all the time.  I'll be using it 99% of the time as a server (smb and dlna type stuff mostly).  Also, I want to run XBMC on it - not sure if I need to be running a desktop environment underneath XMBC?  (and not sure if that disqualifies it as a "server" - probably does.)

I installed ubuntu-desktop, and the GUI comes up now (is it lighter on the system to just install Xorg instead?  Or perhaps ubuntu-desktop actually installed Xorg).  Regardless, I'd rather the desktop didn't come up automatically upon boot.  Any idea how I can just run the GUI from the terminal when I want to, but leave it dormant otherwise?

---

### Post by scruffyeagle on 2011-08-16
> **honeycombs_big_yahyahyah said:**
> <snipped>
Any idea how I can just run the GUI from the terminal when I want to, but leave it dormant otherwise?

I think you can start graphic apps from a command line by prefixing the command with "gsudo".

---

### Post by decoherence on 2011-08-17
> **honeycombs_big_yahyahyah said:**
> I installed ubuntu-desktop, and the GUI comes up now (is it lighter on the system to just install Xorg instead?  Or perhaps ubuntu-desktop actually installed Xorg).  Regardless, I'd rather the desktop didn't come up automatically upon boot.  Any idea how I can just run the GUI from the terminal when I want to, but leave it dormant otherwise?

It is lighter on the system to just install xorg. Installing ubuntu-desktop basically turned it in to an ubuntu desktop system, complete with GDM (which starts the graphics automatically)

If don't want to get the graphical login, get rid of gdm.

Once you are logged in to the command line, the command to start xorg is 'startx' but you may want to write yourself a .xinitrc file first and put it in your home directory. This file simply contains the commands you want to run when you type startx (starting X on its own isn't terribly useful.) You can probably just put 'gnome-session' in there, or another window manager/desktop environment. When you log out of the session, you will be back at the command line.

---

### Post by honeycombs_big_yahyahyah on 2011-08-17
thanks decoherence.  If I've already installed ubuntu-desktop, is it enough to just remove GDM, or are there other things I should get rid of too?  Perhaps "apt-get remove ubuntu-desktop", and then install xorg thereafter?

update: i've uninstalled gdm, and now the machine boots in "low graphics mode".  when i turn that off to go to the command line, i never get a login prompt - it's just putting up a bunch of log lines about starting/stopping cron.  ugh.  any idea how to get back to where i was before, but with xorg installed?  thanks!

---

### Post by decoherence on 2011-08-17
> **honeycombs_big_yahyahyah said:**
> update: i've uninstalled gdm, and now the machine boots in "low graphics mode".  when i turn that off to go to the command line, i never get a login prompt - it's just putting up a bunch of log lines about starting/stopping cron.  ugh.  any idea how to get back to where i was before, but with xorg installed?  thanks!

Gee, I had hoped it would fail over a little more gracefully than that.

Likely all you need to do is hit Alt F1 to get your login prompt. It's probably just leaving you on the wrong virtual console.

You say it's booting in low graphics mode? I'm not sure I know what that means. It's booting at a lower resolution than it did before you installed ubuntu-desktop? There is a fairly recent technology being used called kernel mode setting. I'm no expert on that subject but perhaps it is not installed by default on ubuntu server but got installed when you put on ubuntu-desktop? That's just a guess.

As far as getting things back to how they were before, basically when you install ubuntu server, your default runlevel is 3. When you installed ubuntu-desktop this got changed to runlevel 5. You want to get back in runlevel 3. At least, that's how it used to work. 

Once upon a time this was configured in the /etc/inittab file but these days I don't know what Ubuntu uses (I have been phasing Ubuntu out on my system because they like to break things that worked perfectly in favour of new things that don't work perfectly, sort of like Apple.)

In any case, you're going to want to talk to someone who has a very solid understanding of the package layout and configuration methods of recent Ubuntu releases, and I'm not that guy.

If you haven't already done a lot of configuration work, it might be easiest to reinstall. Then just install xorg and whichever window manager you please, create a .xinitrc file with the command to run the window manager and run startx when you want graphics.

Good luck and sorry I can't be of more assistance!

---

