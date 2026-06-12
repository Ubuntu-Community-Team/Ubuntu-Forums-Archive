---
title: "I can only load Gnome in FailSafe mode, Please help me fix it."
date: 2009-03-24
forum: New to Ubuntu
---

### Post by legolas_w on 2009-03-24
Hi
Thank you for reading my post. Please guide me to troubleshoot this problem. I couldnt go further than loading the system into fail safe Gnome session.

I was playing with Nvidia driver installation and ubuntu restricted module for Nvidia to install one and uninstall the other. after some time I restart the computer and it does not properly booted into Gnome :-O with an error which was saying: I should check .xsession-errors. I checked that file and I found nothing.

I uninstalled the nvidia driver using the nvidia-uninstall and restart the computer, the same error shown again. I delete the xorg.conf and reboot the machine, Ubuntu create the file but it showed the same error again.

Finally, in the login page of Gnome I tried Gnome Fail Safe and it worked, but the fail safe session is hardly useable as the grahic resolution and refresh rate are not usable.

So, I update the computer to the last kernel version with hope that it will fix the problem, but the same error message shown and I forced to retreat into fail safe gnome session.

I even tried to boot in recovery mode and used the X server configuration fixer, but again it resulted in nothing :-(

Here is latest lines of of .xsession-errors which indicate some errors:

```

/home/legolas/.profile: line 25: alias: -l: not found
/etc/gdm/Xsession: line 73: ’ls: command not found
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator
Usage: x-terminal-emulator [options]

x-terminal-emulator: error: no such option: -g

```


And here is the area around line 73 of Xsession, the the first line is line 73.

```

run_parts () {
  # until run-parts --noexec is implemented
  if [ -z "$1" ]; then
    internal_errormsg "run_parts() called without an argument."
  fi
  if [ ! -d "$1" ]; then
    internal_errormsg "run_parts() called, but \"$1\" does not exist or is" \
                      "not a directory."
  fi
  for F in $(ls $1); do
    if expr "$F" : '[[:alnum:]_-]\+$' > /dev/null 2>&1; then
      if [ -f "$1/$F" ]; then
        echo "$1/$F"
      fi
    fi
  done
}

```

And finally here is line 25 of .profile, I think I know that this alias is wrong so I will remove it in the next step.

```

alias ll=’ls -l --color=tty’

```

---

### Post by Bachstelze on 2009-03-24
Your quotes are weird. They should be standard ASCII single-quotes [size=7](')[/size], not typographic apostrophes [size=7](&#8217;)[/size].

Your alias should be

```
alias ll='ls -l --color=tty'
```

---

### Post by blazemore on 2009-03-24
Try
```
sudo aptitude purge nvidia-common
```
```
sudo aptitude install nvidia-common
```

---

### Post by mhgsys on 2009-03-24
try to get it working again with 

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

and if that doesn't work 
```

sudo dpkg-reconfigure xserver-xorg

```

I believe the last will get you default driver back to vesa.
and from there you could reinstall the correct drivers.

The first code will try to update the /etc/X11/xorg.conf

---

### Post by Bachstelze on 2009-03-24
Those are "command not found" errors, for crying out loud! How on Earth could those be caused by a driver error?

---

### Post by blazemore on 2009-03-24
Bit of a hack... also a guess.
You could try making a symbolic link to ls, and call it 'ls. Maybe?

---

### Post by legolas_w on 2009-03-24
> **blazemore said:**
> Try
```
sudo aptitude purge nvidia-common
```
```
sudo aptitude install nvidia-common
```



Hi
I use the above commands, fixed those aliases and I also reversed some customization which I borrowed from [http://www.pythian.com/news/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex](http://www.pythian.com/news/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex) to install ORACLE and not the Ubuntu is as new as it was in day 0.


Thank you all.

---

### Post by turbozmike on 2009-12-12
I think this is a video issue that pops up when you install the 3d drivers, an nvidia 8800 gts in my case with the first revision of the 64-190.18.05 drivers.  there is a new  one 64-190.40 that Im currently using with sucess in normal Gnome mode.

Pretty easy to fix for me. I downloaded the new nvidia drivers.  I followed the instructions above a purged nvidia drivers.
I checked synapic and removed all nvidia stuff, the again used above instructions and installed nvidia-common.

CTRL ALT F1 to a terminal and login.
sudo stop gdm to exit the active xserver
sudo sh ./NVIDA.run (I rename the driver download to make it simple.)
follow the Nvidia install instructions.  when finished
sudo start gdm

Everythings working fine now.
Might not be the correct or best way to go about it but Im a newbie and the end results are it works with no adverse side affects like disabling compbiz and other things I saw suggested for this issue.

---

