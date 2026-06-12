---
title: "Creating start up script"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by chaos_efphect on 2010-09-30
Hello all, i have been messing with ubuntu for awhile now but this if my first take on creating a start up script. In short i wanted to know how to create a way to run "sudo modprobe -r psmouse" at start up with out requiring me to type in my password. i tired to create a new entry in the startup apps but had no luck. any help is greatly appreciated :).

---

### Post by duanedesign on 2010-10-01
If you are wanting to prevent pcmouse from loading you can add it to the /etc/modprobe.d/blacklist.conf or /etc/modprobe.d/blacklist if you are on an older version of Ubuntu. Just add this to the bottom of the file, save it, and reboot:

> blacklist pcmouse



To answer your question about running a script at startup, you would use Upstart. Here is an example of a simple job file using your command as an example. There are more job files you can look at in /etc/init/.  

> # modprobe - program to add and remove modules from the Linux Kernel
#

description	"unload psmouse module"

start on runlevel [2345]
stop on runlevel [!2345]

expect fork
respawn

exec modprobe -r psmouse

[URL="https://wiki.ubuntu.com/MeetingLogs/devweek1007/UpstartJobs"]
Here is a Dev Week session[/URL] on Upstart if you would like to learn more.

---

### Post by Paddy Landau on 2010-10-01
> **duanedesign said:**
> ... about running a script at startup, you would use Upstart.
Upstart looks interesting. Is there a place where it is documented clearly?

However, for a newbie, I think there are simpler solutions.

[LIST=1]
[*]You can add start-up programs to your system through the GUI: System > Preferences > Startup Applications. If you've written a script, you can add it here. Note: Avoid sudo commands with this.
[*]You can add start-up commands to your system in the file [FONT=Courier New]~/.bashrc[/FONT]. Again, avoid sudo commands, and this file applies only to when you start a terminal.
[*]You can add start-up commands to your system in the file [FONT=Courier New]~/.profile[/FONT]. Again, avoid sudo commands.
[*]You can add start-up commands to your system in the file [FONT=Courier New]/etc/profile[/FONT]. These commands are run by root (so don't use 'sudo' in front of the command). Be careful -- if you mess this up, you'll find it difficult to boot your system.
[*]You can add start-up commands to your system in the file [FONT=Courier New]/etc/environment[/FONT]. These commands are run by root (so don't use 'sudo' in front of the command). These commands are run before the GUI is initialised. Be careful -- if you mess this up, you'll find it difficult to boot your system.
[/LIST]
In summary, if you want to run normal programs for yourself, use options 1-3. If you need to run programs as root, use options 4-5. But take care with 4-5 as you can mess up your system!

As duanedesign indicated, sometimes there are cleaner ways to go about it.

---

### Post by chaos_efphect on 2010-10-01
Thank you guys so very much :), i am using a notebook and wanted to disable my touch pad since i use a usb mouse. now i ran in to an issue with Paddy Landau's post. i was not able to find a /etc/profile, just a /etc/profile.d is that the same? also i did not find a /etc/environment file. BTW i am running 10.04 lucid lynx 32bit.

---

### Post by Paddy Landau on 2010-10-01
> **chaos_efphect said:**
> i was not able to find a /etc/profile
Strange. I have one.

---

