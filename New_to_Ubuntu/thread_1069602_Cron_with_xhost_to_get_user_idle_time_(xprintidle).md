---
title: "Cron with xhost to get user idle time (xprintidle)"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by vwilsonuk on 2009-02-14
Hi guys,

I've been working on a backup script that copies a specific (critical) directory to an external hard disk when the machine is idle. 

The script runs ok on my own user's crontab, using the following syntax (it's a bash script) to grab the user idle time:

```
export DISPLAY=:0.0
idle=`xprintidle`
```

However, I've discovered that my external hard disk often goes to sleep, which results in the backups failing. To fix this, I'd like to use these commands to wake it up:

```
#Wake mount
sdparm --command=start /dev/sdb1
sleep 15
```

These work fine, although they need to be run from root so I've now moved the script from my own user's crontab to the root crontab (using sudo crontab -e).

Here's where the problems start. I've set up a helper script to return the idle time from xprintidle, which can be run using "sudo -u myuser scriptname.sh". This means the idle time will be for the correct user (not for root)!

But when I try to run this, there's suddenly lots of X errors - the commands used before don't work. I've tried "xhost +" and "xhost +localhost" first, specifying the host in the DISPLAY command - if it's out there somewhere I've tried it.

So now I've set up a very simple test script in my user's crontab. It looks like this:

```
*/1 * * * * env DISPLAY=:0.0 xprintidle > /home/myuser/Documents/System/test.log 2>&1
```

This works fine, and prints the no of idle seconds to the log file.

When I move it to the root crontab, it prints this instead:

```
No protocol specified
couldn't open display
```

I think until I get this simple example working, I don't stand a chance with the backup script. If I could get it working, I could amend the backup script entry in Cron (perhaps add "env DISPLAY=:0.0" into the crontab instead of trying to set it in the script itself, or similar). 

Please would you let me know if you have any ideas of what to try next on this?

I really just want to get the X idle time of a specific user, with the script running as root (so I can wake the drive). "who -u" doesn't work btw, I've tried it - the idle time it reports is wrong.

Many thanks,


V

:guitar:

---

### Post by vwilsonuk on 2009-02-15
Ok, I've fixed this up by:

1. Creating a new, separate script (running on the myuser crontab) to print the idle time to a file every minute
2. Amending the backup script to check this file and obtain the idle information from the file, instead of running the command. This means the backup script can be run from the root crontab, which allows it to wake up the usb drive.

I'm still curious if anyone can tell me why it couldn't all be done in one script, which would've been a much more elegant solution - but for the sake of having working backups this workaround does the job, and I've posted the solution here in case anyone else runs into the same problem!

Good luck with your Ubuntu, folks,


V 

:popcorn:

---

### Post by nZain on 2010-06-18
This is a rather old thread, but I have the same problem. The X server idle time can usually only be retrieved from the user that runs the X session. This holds for some C code found in the web but also for the ubuntu package ```
xprintidle
``` (which does essentially the same: request the idle time from the screensaver module).

So - when run from my user, it returns as expected, when run from a different user (without X session), it gives the error mentioned above.
 ```
No protocol specified
couldn't open display
```I don't like the cron workaround too much. Furthermore, I'm not too familiar with linux, but shouldn't it be possible to run the xprintidle command with another user (namely, the X session owner)? sudo should do the trick. For this to work in a script (without password), I would have to allow this specific command to be run for any user (or at least the one in question). I experimented a little with changing the permissions via visudo, but no success.

The user mythtv needs to retrieve the idle time, but this is only  available to my own user, namely patrick. Can someone help me to set up the permissions correctly?

best
   Patrick

---

### Post by configt on 2011-07-19
I know this thread is a bit stale, but I was looking for the answer to this also and found something that works.  I hope it helps someone someday.

You need to match the user with the X session.  It's not always :0.0.  Run 'who' and see the list of users with the corresponding X sessions (sorry my terminology may be incorrect).  

For example:

```
userx@desktop:~/bin who
user1   tty7         2011-07-17 03:10 (:0)
user2  pts/0        2011-07-18 20:28 (:1.0)
user2  tty8         2011-07-18 20:27 (:1)
user2  pts/1        2011-07-18 20:35 (:1.0)
user2  pts/2        2011-07-18 21:00 (:1.0)
userx@desktop:~/bin sudo -u user2 env DISPLAY=:1.0 xprintidle
82
```That tells me about the idle time for user2 on :1.0.  If I tried user2 :0.0 I would get the protocol error that you have been getting.

Of course, if no users are logged in, obviously no X sessions are active (unless some clever tunneling is going on, but thats another story).

---

