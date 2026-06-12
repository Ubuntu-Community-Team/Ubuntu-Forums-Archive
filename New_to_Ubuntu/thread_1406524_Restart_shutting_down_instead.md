---
title: "Restart shutting down instead"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Matspoiss on 2010-02-14
Good morning dear forum-goers, I come to you in search of aid once again. The source of the problem at hand may take a while to chase down so I hope you bear with me!

I'm using a 64 bit Karmic Koala and in order to speed up the booting process, I decided to remove some unwanted services from the list. Not wanting to do that manually I installed the boot up manager (bum) and disabled some laptop-related services, the bluetooth manager and the printing server. 

Now the idiocy kicks in - bum is quite ambiguous when deciding what processes are already activated. Most of the services have question marks under the "running" tab and some of which I thought should be active (network-manager for instance) weren't ticked at all. So in my confusion I ticked and enabled the services I thought were essential, thus probably breaking the boot-up process severely. 

Everything is still working properly though, but one thing got damaged - shutting down and restarting. The restart button is simply shutting down the system and to me it seems that the process is too quick, like it's not shutting down all the programs properly but just doing a hasty halt.

I also tried "init 6" from the terminal and even from the recovery console - the result is the same. The "boot" log under logs is empty for some reason so no help there.

So I broke my settings somehow. Is there any hope of salvation?

---

### Post by Satoru-san on 2010-02-14
uninstall bum readd services...

Dont just delete stuff, its not windows, most things are pretty vital to the system boot, I cant speak for ubuntu, but on my system not one single thing it does at boot can be skipped or the system wont work..

Welcome to the forums:KS:KS

While on the forums beware of commands that you do not know what they do, if someone tells you something that you dont understand, dont just do it, ask instead!

---

### Post by Matspoiss on 2010-02-23
Thank you for the quick reply. 

I did as was told, re-enabled the services I disabled before (the cups server and laptop power-manager). The problem, though, persists.

When shutting down (or restarting, it doesn't seem to matter), there is no stopping processes as would be normal. Instead, I see "computer will now halt" almost immediately. This can't be good for the health of my pc!

Is there any way to check if and where my upstart or runlevel configurations are broken?

Thanks!

---

### Post by JiuJitsu500 on 2010-02-23
I had that SAME exact issue a while back, but I was using a 32-bit Karmic and thought about upgrading to 64 anyway.... I solved it by re-installing with 64 :)

I don't know why BUM does that, but even if you put everything back to normal after changing anything, it'll do it sometimes, and it's not the reboot or shut down scripts. I think it has to to with one of the acpi daemons... they're the ones I changed. I wish I could find an answer, and I posted about that before... but alas, no one was able to solve it (I wasn't very persistent in finding an answer though).

---

### Post by rnerwein on 2010-02-23
hi
have a look at: /etc/init.d/halt and /etc/default/halt
an the other way in a terminal try: [COLOR=Green]sudo /sbin/reboot[/COLOR]  instead of shutdown
for hat and reboot have a look at the man pages.

hope this help you
ciao

---

### Post by Matspoiss on 2010-02-23
Thanks for taking the time to answer!

Whereas reinstalling might be an option should the problem really prove unsolvable, I'd like to put it off as long as possible. One of the reasons I love linux is the chance to dissect everything and get to the bottom of any problems that might occur, thus learning about the opsys in general. Therefore I don't want to give up just yet.

As to your suggestions, merwein, I checked the files, read the man pages and tried the manual shutdown from the terminal. As I'm quite new to all this, I couldn't find anything particularly wrong with either of the files. Thus I thought I'd copy the contents of both files here and humbly ask you, if anything nasty pops out.

```
cat /etc/init.d/halt

#! /bin/sh
### BEGIN INIT INFO
# Provides:          halt
# Required-Start:
# Required-Stop:
# Default-Start:
# Default-Stop:      0
# Short-Description: Execute the halt command.
# Description:
### END INIT INFO

NETDOWN=yes

PATH=/sbin:/usr/sbin:/bin:/usr/bin
[ -f /etc/default/halt ] && . /etc/default/halt

. /lib/lsb/init-functions

do_stop () {
	if [ "$INIT_HALT" = "" ]
	then
		case "$HALT" in
		  [Pp]*)
			INIT_HALT=POWEROFF
			;;
		  [Hh]*)
			INIT_HALT=HALT
			;;
		  *)
			INIT_HALT=POWEROFF
			;;
		esac
	fi

	# See if we need to cut the power.
	if [ "$INIT_HALT" = "POWEROFF" ] && [ -x /etc/init.d/ups-monitor ]
	then
		/etc/init.d/ups-monitor poweroff
	fi

	# Don't shut down drives if we're using RAID.
	hddown="-h"
	if grep -qs '^md.*active' /proc/mdstat
	then
		hddown=""
	fi

	# If INIT_HALT=HALT don't poweroff.
	poweroff="-p"
	if [ "$INIT_HALT" = "HALT" ]
	then
		poweroff=""
	fi

	# Make it possible to not shut down network interfaces,
	# needed to use wake-on-lan
	netdown="-i"
	if [ "$NETDOWN" = "no" ]; then
		netdown=""
	fi

	log_action_msg "Will now halt"
	halt -d -f $netdown $poweroff $hddown
}

case "$1" in
  start)
	# No-op
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	do_stop
	;;
  *)
	echo "Usage: $0 start|stop" >&2
	exit 3
	;;
esac

:
```

```
cat /etc/default/halt 

# Default behaviour of shutdown -h / halt. Set to "halt" or "poweroff".
HALT=poweroff
```

Regarding the manual shutdown (sudo /sbin/reboot --verbose) - sadly it had the same effect as any other shutdown method.

---

### Post by Rayve on 2010-02-23
Matsposis,

Not sure if this is of any help, but I checked my /etc/init.d/halt and /etc/default/halt files and mine were the same as yours.

Recently, my problem was that when I would reboot by doing "sudo reboot" from the terminal, I'd get fsck for each partition when I booted back up, and it usually hung on the /home partition.

A friendly forum user recommended I try ```
 sudo shutdown -r -t 0 now 
``` and the fscks don't happen nearly as often and it doesn't seem to hang on /home.

I haven't looked at the man page for it, but my guess would be that if you were to change the "0 now" to something else, it would pause the reboot for a period of time to perhaps allow programs to safely shutdown?

EDIT: Okay, just checked the manpage, looks like I may not need the "-t" in there.  But the format appears to be: shutdown [option] ... [TIME] [message]  so you could do something like 

```
 # sudo shutdown -r [to reboot] +1 [for one minute from now] 1 minute [to display the message "1 minute"]
sudo shutdown -r +1 1 minute 
```On my screen, this left my terminal running (because I didn't & it into the background) so I opened another terminal and did "sudo shutdown -c" and it cancelled the shutdown and opened up my previously busy terminal appropriately.

Not sure if this is what you're looking for, but hopefully it helps.

---

### Post by Peter09 on 2010-02-23
For immediate restart use
```
sudo shutdown -r now
```

---

### Post by Matspoiss on 2010-02-23
Thanks for the replies!

I tried the delay option on shutdown and reboot, but it seems that it delays the whole process. It doesn't stop any services until the 1 minute is up and then it halts without proper preparation like before.

I've really no idea where to look further. The problem is likely in the wrong order of runlevel items, but I'm too green in that field to make any further assumptions.

Please don't give up fellows! :)

---

### Post by jdorenbush on 2010-11-08
I just started experiencing the same problem today. When trying to Reboot my system just shuts down instead.

I'm using Ubuntu 10.10 64-bit.

Any help is appreciated.

---

### Post by Cabalbl4 on 2010-11-15
Have same problem in Karmic. No way to fix, can only reboot by reset button.

---

### Post by jdorenbush on 2010-11-15
Not sure if there was a recent update that fixed this, but my problem seems to have resolved itself.

---

