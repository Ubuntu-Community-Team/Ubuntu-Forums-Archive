---
title: "Editing file is somehow not permanent"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Arkian on 2010-05-06
Hi all. Been searching the forum an answer to my problem. No luck finding any, so hopefully I will be able to get some help this way.

I did an upgrade from my 9.10 to 10.04 just the other day on my Lenovo Thinkpad x61s. Everything went smoothly as usual and almost no tweaking was needed.

However I had to adjust settings for my trackpoint to enable it to be used for scrolling. Plenty of guides out there for that, so no problem.

But after adjusting these settings my trackpoint button (the red one, if you are wondering) was now also enabled as an actual button when pressed. Looking into why, I found out which file controlled this setting:

/sys/devices/platform/i8042/serio1/press_to_select

When trying to change this *press_to_select* file's value from 1 to 0 via the gui as root I wasn't able to save the file.

Via the terminal and the following command as root

```
echo -n 0 > /sys/devices/platform/i8042/serio1/press_to_select
```

I was able to change the value and feel the result, but after reboot the system changed the value back to 1 and the trackpoint was again enabled as a button.

So what I dont understand is why my change to the file isn't permanent?

Any help appreciated. Thx.

---

### Post by Hospadar on 2010-05-06
Probably that file is not a real file.

In unix-like systems (linux is unix-like) everything is represented as a file that can be accessed through the filesystem somewhere.  All your hardware devices, disks, etc are a file somewhere in the filesystem, but that doesn't mean they are all saved on your hard disk.  For example, if you were to open a device file (if you were a program, and not a person), you could read data out of it to figure out what that device is doing, and you could write data to it, which might send commands to that device.  whatever data you write into that device file is interpreted by the device driver, and sent down some wires somewhere to something.

Soooooo - probably, the file you wrote into, is not actually a file at all, but rather a node created by the device driver to recieve input as to whether or not it should enable press_to_select.  The file in question probably links directly to some spot in memory where the driver stores the "press_to_select" option.  So what you'd need to do is to set the command (the one you mentioned above) to run every boot.  Probably the quickest way is to add it to /etc/init.d/rc.local, although there are a lot of ways to make a command run on boot.  You can put it in a script (just paste that command into a text file) and have it get run every time your GUI opens up, or you could install your own startup script.  Google around for something that works for you.

Another possibility, more mundane, is that some other script just re-writes that file on boot.  I can't really imagine why that would happen, but even if that's the case, the remedy would be the same, have your command run every time you boot up to set that option.

---

### Post by psusi on 2010-05-06
/sys is a psuedo filesystem that provides a window into variables in the running kernel, not real on disk files.  Anything you tweak there you will need to repeat at every boot, so you probably want to put a script in /etc/rc.local to do that.

---

### Post by Arkian on 2010-05-06
Thank you for your replies that makes excellent sense. Would anyone be able to help me put the command in to the mentioned rc.local. 

Where to put it excactly - and what the command should consist of. 

Thank you.

---

### Post by dracayr on 2010-05-06
Well just open the file (with vim, nano, emacs, gedit, or your favorite text editor) and put that command you posted somewhere before the 'exit 0'.

If you want more info about rc.d scripts: [http://www.linux.com/news/enterprise/systems-management/8116-an-introduction-to-services-runlevels-and-rcd-scripts](http://www.linux.com/news/enterprise/systems-management/8116-an-introduction-to-services-runlevels-and-rcd-scripts)

dracayr

---

### Post by Arkian on 2010-05-07
This sure sounds like the solution to my problem. I tried editing the rc.local file, but with no effect.

The content of my original rc.local file was 

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs $syslog $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
	        [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		ES=$?
		[ "$VERBOSE" != no ] && log_end_msg $ES
		return $ES
	fi
}

case "$1" in
    start)
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

And the command I want to run automatically is 

```
echo -n 0 > /sys/devices/platform/i8042/serio1/press_to_select
```

Can anyone point me to how/where to put the command so it runs on each boot.

Thank you guys for the help so far.

---

### Post by bredman on 2010-05-07
You should add your command to the file /etc/rc.local. This file contains all the extra commands that the user wishes to add to the boot sequence.

Add your command just before the 'exit 0' at the end.

Read the comments at the top of /etc/init.d/rc.local and /etc/rc.local to figure out their relationship.

Note that /etc/rc.local is owned by root. Use the command
sudo gedit /etc/rc.local
to edit it.

---

### Post by Arkian on 2010-05-07
Excellent. I was editing the wrong file. 

Put the command in the right file, and it is now executed correctly on each boot.

Thanks alot to all who helped.

---

