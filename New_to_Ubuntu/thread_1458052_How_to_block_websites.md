---
title: "How to block websites"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by Dark006 on 2010-04-19
Just had a question on how to block Facebook from 10PM to 8AM everyday. Any programs that are easy to configure and password protected? I'll take any suggestions, thanks!

---

### Post by e4uforums on 2010-04-19
Here is a thread re: parental controls.  It may be a good place to start.
[URL="http://ubuntuforums.org/showthread.php?t=843510"]
http://ubuntuforums.org/showthread.php?t=843510[/URL]

---

### Post by Iowan on 2010-04-19
I haven't used [Squid]("https://help.ubuntu.com/9.10/serverguide/C/squid.html") yet, but [here]("https://help.ubuntu.com/community/SquidGuard") is a(nother) help page to check.

---

### Post by Nisal on 2010-04-19
use a filter u can find enough from google

---

### Post by 2hot6ft2 on 2010-04-19
Gnome Nanny
> **kostkon said:**
> A good solution that a simple user (e.g. a parent) could use is *Gnome Nanny* (it's similar to what windows offers for parent control).

An article about it [here]("http://www.webupd8.org/2010/03/gnome-nanny-parental-control-takes-care.html") and the PPA is [here]("https://launchpad.net/~nanny/+archive/ppa").

Hope that helps.
I think you can do it with [http://www.opendns.com/](http://www.opendns.com/) but I think they charge.
Some routers can be configured to do it as well, I know mine can.

---

### Post by k3lt01 on 2010-04-19
> **Dark006 said:**
> Just had a question on how to block Facebook from 10PM to 8AM everyday. Any programs that are easy to configure and password protected? I'll take any suggestions, thanks!I suppose you could use a HOSTS file to do it but how you would make it work in that time frame I don't know. Maybe a cron job or something?

Just out of interest why between 10pm and 8am?

---

### Post by Iowan on 2010-04-20
> **k3lt01 said:**
> Just out of interest why between 10pm and 8am?Kinda sounds like bedtime... :)

---

### Post by k3lt01 on 2010-04-20
> **Iowan said:**
> Kinda sounds like bedtime... :)Yeah so why would you need to block anything if your asleep? :P

---

### Post by Zintha on 2010-04-20
> **k3lt01 said:**
> Yeah so why would you need to block anything if your asleep? :P
I'm thinking its more a lack of self control :P

---

### Post by uRock on 2010-04-20
If you have a Cisco Linksys Router, then you can easily filter websites during certain times. Let me know if you do an I can walk you through it if necessary.

---

### Post by e4uforums on 2010-04-21
> **k3lt01 said:**
> 

Just out of interest why between 10pm and 8am?

I'm thinking that's when the kiddos should be sleeping   :)

---

### Post by donkyhotay on 2010-04-21
Be aware that kids are often more tech savvy then people realize. Putting filters on a system may be a good reminder that it's time for them to go to bed but if they're breaking bedtime rules anways, one google search for "how do I remove a website filter" will allow them to figure out how to bypass just about anything you can set up. Personally I think using technological filters for kids is a waste of time, the best thing (IMO) is to keep the computer in an open area and monitor usage that way.

---

### Post by uRock on 2010-04-21
[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/) is a great tutorial on setting up a filtering.

---

### Post by HarrisonNapper on 2010-04-21
> **donkyhotay said:**
> Be aware that kids are often more tech savvy then people realize. Putting filters on a system may be a good reminder that it's time for them to go to bed but if they're breaking bedtime rules anways, one google search for "how do I remove a website filter" will allow them to figure out how to bypass just about anything you can set up. Personally I think using technological filters for kids is a waste of time, the best thing (IMO) is to keep the computer in an open area and monitor usage that way.

Agreed. However, in this case, the user may want some controls over none. Network controls at my High School unintentionally made computer experts out of a good number of kids, but at least it did some good. If it really gets that intense, you can do as suggested and use cron to change out the host file or modify iptables during those hours and then use chattr to make the host file immutable. That way the kiddos would need the root password to put it back.

The most control in any linux distro will always be through the tools that come with linux in general and most (read: all) of those are managed through the command line.

---

### Post by dwarfolo on 2010-04-21
Well maybe it's not a "catch all" solution, but the following could be enough to keep your kids away from the worst social disorder ... erm ... network ever :P
The trik is to redirect any DNS query for facebook.com originated by your Linux box directly to the loopback address (i.e. the Linux box itslef). 

Make a copy of your /etc/hosts file

```
sudo cp /etc/hosts /etc/hosts.filter
```

Edit /etc/hosts.filter and add the following line
```
127.0.0.1  facebook.com
```

Make a script in your /root directory named filter.sh
```

#!/bin/sh
case "$1" in
'start')
  mv /etc/hosts /etc/hosts.bkp
  mv /etc/hosts.filter /etc/hosts
  ;;
'stop')
  mv /etc/hosts /etc/hosts.filter
  mv /etc/hosts.bkp /etc/hosts
  ;;
*)
  ;;
esac

```
Make the script executable
```
sudo chmod +x /root/filter.sh
```
Now edit root crontab to add two jobs: one to turn the filter on and one to turn it off
```
sudo crontab -e
```
add the following line to the crontab file
```

00 22 * * * /root/filter.sh start 1> /dev/null
00 08 * * * /root/filter.sh stop 1> /dev/null

```

Beware, as someone stated before in this thread, kids are growing smarter then us!
:lolflag:

---

### Post by HarrisonNapper on 2010-04-21
@dwarfolo: wouldn't that result in a recursive request to the loopback address? True, *nix will break it manually eventually, but there's probably a better solution like redirecting to google or something.

---

### Post by dwarfolo on 2010-04-21
No, /etc/hosts works just like a sort of "cache", a static archive that actually bypasses a real DNS lookup.
In other words that line inside /etc/hosts creates an alias for "localhost" and hence pointing the browser to [http://www.facebook.com](http://www.facebook.com) is translated in [http://localhost](http://localhost).

EDIT:
The same trick should work in windows too.
I don't know at present, but in the past Windows used to have a hosts file somewhere in the system directories. This file worked almost the same way as the *nix file. So, using the tasks scheduler and this file, someone could reproduce the trick. :P

---

### Post by HarrisonNapper on 2010-04-21
Ah, learn something new every day. :)

---

### Post by dwarfolo on 2010-04-21
> **HarrisonNapper said:**
> Ah, learn something new every day. :)

And so do the kids .... but way much faster than us :P

---

### Post by karthick87 on 2010-06-22
You can use squid proxy server,it will do what you want..

---

### Post by julio_cortez on 2010-06-22
> **Zintha said:**
> I'm thinking its more a lack of self control :P
Or maybe parental control over kids, why not?

If it's parental control over kids, maybe a cron job and two different hosts files are enough..
If it's lack of self control, I'm sorry but everything you do would be useless, as you immediately will know how to circumvent a barrier that you made yourself ;)

---

