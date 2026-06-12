---
title: "I can't get the video drivers to install, help?"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by whywouldyoudothat on 2010-05-23
Ok so I've read over 9000 guides on how to install nvidia drivers. By some miracle(I guess the planets were aligned at the time) in version 8 of ubuntu I managed to install them. Now I can't seem to get them going again.

From what I know, it seems all I need to do is download the drivers, disable the gui, run the installer, restart the gui and it should work.

I read the nvidia readme and all it said was to disable the x server and run the installer, which it didn't describe how to do, so it was of little help.

1.I open the terminal

2.I've tried various ways of doing this,

sudo service gdm stop
/etc/init.d/gdm stop (something like that)
other ways I can't remember atm

3. I just see the task bar disappear and all I see is the wallpaper, no console/terminal/whatever
I can't do anything but restart.

4. AFAIK I have the right packages installed.

5. HELP?

---

### Post by sylvester_0 on 2010-05-23
Why don't you try using the pre-packaged drivers from the repository?

System -> Administration -> Hardware Drivers

---

### Post by skarme on 2010-05-23
Well to disable x server; press CTRL+ALT+F1
It will ask you for your password,etc.
Once thats done...
you should type...
sudo service gdm stop
to start the x server again type...
sudo service gdm start

---

### Post by whywouldyoudothat on 2010-05-23
Are they the latest drivers?

But I would still like to know how to do this for myself in the future.

---

### Post by sandyd on 2010-05-23
> **whywouldyoudothat said:**
> Ok so I've read over 9000 guides on how to install nvidia drivers. By some miracle(I guess the planets were aligned at the time) in version 8 of ubuntu I managed to install them. Now I can't seem to get them going again.

From what I know, it seems all I need to do is download the drivers, disable the gui, run the installer, restart the gui and it should work.

I read the nvidia readme and all it said was to disable the x server and run the installer, which it didn't describe how to do, so it was of little help.

1.I open the terminal

2.I've tried various ways of doing this,

sudo service gdm stop
/etc/init.d/gdm stop (something like that)
other ways I can't remember atm

3. I just see the task bar disappear and all I see is the wallpaper, no console/terminal/whatever
I can't do anything but restart.

4. AFAIK I have the right packages installed.

5. HELP?
Press Ctrl + F1, login, and try the commands :)

---

### Post by whywouldyoudothat on 2010-05-23
> **skarme said:**
> Well to disable x server; press CTRL+ALT+F1
It will ask you for your password,etc.
Once thats done...
you should type...
sudo service gdm stop
to start the x server again type...
sudo service gdm start

That's what I typed but it just gives me the wallpaper screen after I do the stop and I can't type anything.

---

### Post by sandyd on 2010-05-23
> **whywouldyoudothat said:**
> That's what I typed but it just gives me the wallpaper screen after I do the stop and I can't type anything.
boot in recovery mode.

select "root"

login, then type in 
```

cd /home/*your_username_here*

```
to get to your home directory.

---

### Post by skarme on 2010-05-23
You mentioned typing that in the terminal didn't you?

---

### Post by whywouldyoudothat on 2010-05-23
> **carlee said:**
> Press Ctrl + F1, login, and try the commands :)

Ok trying it with this way gets me to the right screen now but when it asks for a password and I type it in it says incorrect login.

---

### Post by sandyd on 2010-05-23
> **whywouldyoudothat said:**
> Ok trying it with this way gets me to the right screen now but when it asks for a password and I type it in it says incorrect login.
which was due to someone who thought that making a password entry there for the root user was a good idea :|

go back to a normal boot, 

type in ```

sudo passwd root

```
type in the same password you use for your account (so you don't lose it)

now do the steps again, and try entering the password....

after installing the drivers, run
```

sudo usermod -p '!' root
[B]
```
[/B]

---

### Post by skarme on 2010-05-23
Its the username first and then the password...You might be making that mistake.

---

### Post by whywouldyoudothat on 2010-05-23
> **carlee said:**
> which was due to someone who thought that making a password entry there for the root user was a good idea :|

go back to a normal boot, 

type in ```

sudo passwd root

```type in the same password you use for your account (so you don't lose it)

now do the steps again, and try entering the password....

after installing the drivers, run
```

sudo usermod -p '!' root

```

I seemed to be able to change the password with a terminal but not when I do ctrl alt f1. With ctrl alt f1 it says incorrect login even after I changed it.

---

### Post by sylvester_0 on 2010-05-23
The drivers in the repository (195.36.15-0ubuntu2) are slightly behind the latest (195.36.24) drivers. Now, I like to always have the most up to date drivers, firmware, BIOS rev etc, but I can't think of what you would gain by manually installing the slightly newer nvidia drivers.

If you do manage to manually install the drivers, prepare to reinstall them every time there is a kernel upgrade. It sounds like you want to learn how your system works/tweak it. Maybe a distro such as Gentoo or Arch would be more of a fit for you?

---

### Post by sylvester_0 on 2010-05-23
> **whywouldyoudothat said:**
> I seemed to be able to change the password with a terminal but not when I do ctrl alt f1. With ctrl alt f1 it says incorrect login even after I changed it.

Please be aware that running
```
sudo usermod -p '!' root
```
disables the root login (default Ubuntu config.) There's really no reason to go into recovery mode (that I know of) to install the nvidia drivers.

Here are the rough steps:

1. Download nvidia drivers.
2. Press ctrl-alt-f1 and login with your normal credentials
3. sudo service gdm stop
4. sudo /path/to/nvidia/installer (such as /home/user/Downloads/nvidia-blahblah.bin)
5. sudo nvidia-xconfig
6. sudo service gdm start

I haven't done it manually in Ubuntu for a long time (heck, even in Gentoo I just use the drivers that are in portage) but that should work.

---

### Post by whywouldyoudothat on 2010-05-23
> **skarme said:**
> Its the username first and then the password...You might be making that mistake.

That's what I was doing wrong. I am properly logged in now but when I try to install it says "Cannot Open file"

It says username-desktop so I assume it is like being in the desktop directory.

I tried:

sudo sh nvdrv.run

sudo sh /home/username/desktop/nvdrv.run

Neither worked.

---

### Post by sandyd on 2010-05-23
> **whywouldyoudothat said:**
> That's what I was doing wrong. I am properly logged in now but when I try to install it says "Cannot Open file"

It says username-desktop so I assume it is like being in the desktop directory.

I tried:

sudo sh nvdrv.run

sudo sh /home/username/desktop/nvdrv.run

Neither worked.
try```

sudo sh ~/Desktop/nvdrv.run
```

and yea... ignore my other post... i thought you booted into recovery mode..

---

### Post by sylvester_0 on 2010-05-23
Did you chmod +x the file? Exactly what's happening when you try running it?

---

### Post by whywouldyoudothat on 2010-05-23
> **carlee said:**
> try```

sudo sh ~/Desktop/nvdrv.run
```and yea... ignore my other post... i thought you booted into recovery mode..

Ok that works, the installer starts now. Unfortunately it tells me there is an error.

This is what it says:

[I]"ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.[/I]"

---

### Post by skarme on 2010-05-23
Did you view this.....
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
for installation guide. If not; try it.

---

### Post by sylvester_0 on 2010-05-23
Do you have the build-essential package installed?

---

### Post by whywouldyoudothat on 2010-05-23
> **sylvester_0 said:**
> Do you have the build-essential package installed?

Yes. It says build-essential 11.4build1 is installed.

Also, I am trying to install the beta drivers not the official ones.

ver 256.25 if that makes a difference?

---

### Post by sylvester_0 on 2010-05-23
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by whywouldyoudothat on 2010-05-23
Looks like the newest beta drivers are installed and everything works now. Thanks everyone.

---

