---
title: "Modifying cron / anacron based on network SSID"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by djmac on 2010-11-24
I regularly move between 3 different local networks, and I am interested to know if it is possible to modify cron and anacron jobs based on the network I am in.

I am trying to rsync between various computers in the different networks. Depending on the network I am in, the network locations change between local and remote, and the different local networks have different computers ip's etc within them.

Essentially, what I want to do is have different rules (i.e. differing sshfs and cifs mount commands and differing rsync commands) depending on location. 

If someone could point me in the right direction to achieve this it would be greatly appreciated!

Cheers

---

### Post by Cheesehead on 2010-11-24
Yes, it's possible. Yes, it's possible using only shell scripts.

You need to capture a network-up/down event, using that event to launch a script that determines which network you are on and then edits the crontab accordingly.

Step 1 - Capture a network up/down event. There are several ways to do this, but the two easiest are to listen for an Upstart event or to put your script (or link) in /etc/network/if-up.d and /if-down.d. Upstart is useful if you want additional criteria or if you just like working Upstart events. If you really want to know about Upstart, it's not difficult and I have an example at [http://kiwinc.itgo.com/ian/TechBlog.html]("http://kiwinc.itgo.com/ian/TechBlog.html"). Since network connection is the only real criteria, let's ignore upstart and go with the simple /etc/network/if-up.d and if-down.d folders.

Step 2 - Determine your network using the 'route' command. Try it. Note that this captures the router name, which may be different from the wireless ESSID. How you want to capture it is up to you. I use 'route | grep default | cut -d' ' -f10', though you can use awk or sed or regexes if they make you happier.

Step 3 - Editing your crontab is in some ways the easiest and hardest part of the script. In your network-up script, append the specific lines you want to the crontab. In your network-down script, use 'grep -E' to remove all the auto-appended lines. If you are using user-level crontabs, use 'crontab -u <username> -l > /tmp/tempfile', then edit the tempfile, then 'crontab -u <username> /tmp/tempfile to install the edited crontab, then 'rm /tmp/tempfile' to clean up, of course.

So place a file something like this in /etc/if-up.d (assumes user-level crontabs, which are more complicated to edit)
```
LOCATION = route | grep default | cut -d' ' -f10         # Get network name
if ["$LOCATION"] = "Network1"
   crontab -u myusername -l > /tmp/crontabtemp
   CRONTABLINE="*/20 * * * * /home/myusername/dosomething.sh"
   echo "$CRONTABLINE" >> /tmp/crontabtemp               # Append crontab line
   crontab -u myusername /tmp/crontabtemp                # Install crontab   
   rm /tmp/crontabtemp
fi
```

And place a file something like this in /etc/if-down.d (let's do this one as the root crontab)
```
CRONTABLINE="*/20 * * * * root /scripts/dosomething.sh"
cp /etc/crontab > /tmp/crontabtemp1
grep -Ev $CRONTABLINE /tmp/crontabtemp1 > /etc/crontab     # Remove crontab line
rm /tmp/crontabtemp1
```


Warning - these scripts will run as root!
DANGER - These are simplified examples only! DON'T use them!

---

### Post by djmac on 2010-11-24
Thanks for your idea. I like it, and think it would work quite well. I will have a play around with it. 

Along a similar vain, instead of modifying the crontab, I might try and make a shell script for the crontab (i.e. /home/myusername/dosomething.sh), which can be modified based on the location. That way you would not have to mess around with the crontab / crontab temp files. 

Also, maybe I could incorporate the "if" statements into that shell script itself. (Also, will probably grep the ESSID from "iwlist scanning")


What are your thoughts? 

Cheers, and thanks for the ideas.

---

### Post by Cheesehead on 2010-11-25
Modifying crontabs isn't difficult, and it's much easier than trying to duplicate cron's wonderful functionality. The tempfiles-and-such are simply my way of keeping my process and code simple and maintainable. You're just adding and deleting a line of text like any other; how you want to do it is up to you.

I tested mine quite thoroughly to ensure the crontab appends and removes were clean. They are, and my crontab-edits-upon-network-changes are wonderful and problem-free.

The shell script examples for network-up should obviously have more than one if/fi branch. Mine has three. I limited it to Network1 for brevity. The network-down script can happily try to clean up everything (useful in case of a hard reset).

Mine also changes the default printer while on each network.

Will you be mounting network drives upon network-up? Or saving that until the cron jobs run?

---

### Post by DaithiF on 2010-11-25
> **djmac said:**
> Essentially, what I want to do is have different rules (i.e. differing sshfs and cifs mount commands and differing rsync commands) depending on location. 


The approach of doing this by altering your crontab is not a good one.  

If your crontab command is anything more than a simple 1-liner then it should not be in crontab itself, instead it should be in a script that is called from crontab.

It sounds like you are at a minimum:
(1) mounting a filesystem
(2) executing a rsync command
you should probably also be testing for success of the mount and capturing output to a log.  This makes it too complex to stuff into a single crontab line.  Instead you need a single (unchanging) crontab line which calls a script which does the work, and (based on the helpful info provided by Cheesehead), determines what network you are on and chooses the various parameters for mount targets and rysnc destinations etc.

---

### Post by Cheesehead on 2010-11-25
Excellent point. On my own scripts, that's what I do, too.

---

