---
title: "Perfect install yesterday,today??."
date: 2009-07-31
forum: New to Ubuntu
---

### Post by gasmansteve on 2009-07-31
HI folks
New to the forum so please be gentle, its a couple of years since dipping my toes in the Linux pond:).
Installed 9.04 yesterday next to my XP partition everything worked perfectly even my Buffalo usb wireless stick got online everything great which suggests all my components ok with Ubuntu 9.04. Fired it up today and no wireless available not in Network manager not even an `enable wireless` label like I had yesterday, my desktop wallpaper has even vanished?. I`m thinking everything I did yesterday was as root and today I`m logged in as `Steve`hence the different desktop. I can`t access any root folders and If I type `su` in terminal it asks for a password which I dont remember setting up when installed so what default root password is it wanting please?. I was so pleased yesterday when it all worked perfectly but today :(.
Any suggestions please how to get it all back and how to log in as root?.
Many thanks
Steve

---

### Post by nothingspecial on 2009-07-31
Did you do your updates. I got a new kernel today and it broke my wireless.

Easiest fix, reboot and hold down escape. When the boot menu comes up choose the kernel with the lowest number at the end ie

```
Ubuntu 9.04, kernel 2.6.28-13-generic
```

instead of

```
Ubuntu 9.04, kernel 2.6.28-14-generic
```

If that works and you`re interested I can tell you how to boot that kernel by default.

However as you did everything as root yesterday (which you shouldn`t have done - but that is a different conversation) it is possible that you have changed ownership of some of your essential config files. In that case you need to do the same as before (reboot and hold down escape) and choose recovery mode.

Issue these commands

```
chown -R [COLOR="Red"]username:username[/COLOR] /home/[COLOR="Red"]username[/COLOR]
```

```
chmod -R 755 /home/[COLOR="Red"]username[/COLOR]/
```

```
chmod 644 /home/[COLOR="Red"]username[/COLOR]/.dmrc
```
```
chmod 644 /home/[COLOR="Red"]username[/COLOR]/.ICEauthority
```

Where the red username is your actual username.

Then reboot.

Try the first thing first and as you were working as root yesterday I honestly have no idea what you may have done so the chances are that these things wont work but they are worth a go.

---

### Post by Liolikas on 2009-07-31
> 
so what default root password is it wanting please?

There is no default it would be insane security hole and end up with viruses and even worse.

Ubuntu has root disabled at all by default. You can enable it by inserting livecd and editing /etc/shadow file, but that file is partially encrypted so not much fun to edit it better just reinstall and remember password.

---

### Post by swoll1980 on 2009-07-31
instead of su type sudo. If you want to set up a UNIX su password type. ```
sudo passwd
```

---

### Post by TUOggy on 2009-07-31
Hi Steve,

Whatever you did yesterday was done as whatever user you set up when installing.  I am assuming that you set up Steve when you were installing it.

I would try sticking in the cd again, and trying to run the live cd.  See if your wireless works on the live cd.  It might be a simple case of having a corrupt installation (which can happen with any OS) in which case you may want to consider a fast reinstallation of Ubuntu.

Do you have a wired connection available at all?  If you do, you may want to run updates to see if that can correct it

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by ajgreeny on 2009-07-31
Sorry but you can't login as root in ubuntu,  it uses the sudo system instead.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
I don't think you can have actually been logged in as root yesterday, but equally, I don't know quite what has happened.  During install you will have made a username entry and chosen a password, which is not root's password but yours, and can then be used with sudo (or gksudo for GUI apps) to get you temporary admin privileges.  If you know your username and pasword you chose you should be able to login, or is that what you are already doing, but getting nowhere?

Can you see your chosen username in /home from the desktop you do have, even if it's not what you expected, and if so can you see any files you may have made yesterday?  If so try to back them up to a usb drive in case a reinstall is needed.

I would like to know more, however, about what exactly you did yesterday, how you partitioned and actually whether you really did install or just run the live CD.  Tell us more please.

---

### Post by nothingspecial on 2009-07-31
> **ajgreeny said:**
> Sorry but you can't login as root in ubuntu,  it uses the sudo system instead.


Yes you can, and you can do untold damage to your install if you do.

---

### Post by Liolikas on 2009-07-31
> **nothingspecial said:**
> Yes you can, and you can do untold damage to your install if you do.
Really!? I think too that root login is not allowed in Ubuntu.

---

### Post by ajgreeny on 2009-07-31
> **nothingspecial said:**
> Yes you can, and you can do untold damage to your install if you do.
Yes agreed, but only if you know how, and I would suggest that this new user would never know how to do that.  Installing from the live CD, which I suspect is what the OP did will not give you the option of enabling the root account.  I think you are probably confusing the OP with your comment, even more than he probably is already.

---

### Post by LowSky on 2009-07-31
> **nothingspecial said:**
> Yes you can, and you can do untold damage to your install if you do.

using root to log in is as safe as using windows XP as user with administrator privileges. yes you can break stuff but the real harm is done when you don't know what your doing.

Ubuntu disables root so that a user with sudo can do the same functions. is it any safer, kinda I guess, but its still nearly the same thing.

---

### Post by gasmansteve on 2009-07-31
Hi all
Thanks for the speedy replies really helped. I just tried the lsusb command and found my wireless stick wasn`t detected so unplugged it and messed about with the switch a few times plugged it back in and Presto stick detected and net up and running again so must have a dodgy Buffalo stick.
Cheers again
Steve

---

