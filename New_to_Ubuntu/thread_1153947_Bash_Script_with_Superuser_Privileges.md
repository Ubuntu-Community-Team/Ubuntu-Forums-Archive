---
title: "Bash Script with Superuser Privileges"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by dtuza on 2009-05-09
I'm sure this must be a question that's been asked many times before, but I've not had much luck finding an answer.  I'm trying to create a basic bash script to change the cpu frequency of both cores of my cpu on command, since I can't seem to find a good way to have it default to the "performance" governor.

Ideally, would like to have two copies of this script, one to set both to conservative and one for performance.  Maybe it seems silly to do this for 2 commands each script but meh, have to start somewhere.

Obviously the cpufreq-selector command needs to be run with superuser privileges - how can I design a script to run this?  Either running it as superuser or prompting me for my password when I run it as a user.  Just having the script with the sudo operator seems not to work when I run it.

---

### Post by ibuclaw on 2009-05-09
If you use a laptop, you can use the power manager directories if you intend to switch between states as you plug-in/unplug from AC.

```
sudo gedit 99-power-govervnor
```

And put in something like:
```

for gov in `ls /sys/devices/system/cpu/cpu?/cpufreq/scaling_governor`; do
   if on_ac_power; then
      echo "performance" > $gov
   else
      echo "conservative" > $gov
done

```

and to install:
```

sudo install 99-power-govervnor /etc/pm/sleep.d
sudo install 99-power-govervnor /etc/pm/power.d

```
Regards
Iain

---

### Post by The Cog on 2009-05-09
I set my cpufreq binary to suid root so that anyone could run it and it always ran with root priv. I know it is theoretically a security risk because if there were a flaw in the program it might be used by malicious users for privilege escalation, but I don't really see that as much of a risk in my case. I don't have remote users other than myself.

---

### Post by dtuza on 2009-05-09
Thanks guys, these suggestions are both much appreciated.

---

