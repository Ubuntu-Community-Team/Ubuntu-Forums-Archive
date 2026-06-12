---
title: "Completely puzzled - SMB and internet sharing"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by chris_tikva on 2008-09-08
Having wrestled with internet sharing for some time and having worked through the material I could find on the net, some of it contradictory, I thought I'd finally managed to get a reliable shared internet connection and shared disk drives between my two machines.

The way I did it was this:

Install firestarter
Install dnsmasq
Make sure that dhcp3-server is NOT installed since I found that firestarter crapped out with an "unknown error" when it tried to start it.

Then: uncomment the line in /etc/sysctl.conf to allow forwarding

Add the line: ifconfig eth0 192.168.0.1 to /etc/init.d/rc.local 

Then activate firestarter with the internet sharing option ticked and dhcp asked for. 

That worked like a dream until I decided to be a bit more ambitios and connect a network drive to the same ethernet hub. Not only did it throw up when it saw the drive but, having removed the drive, switched everything off and rebooted, I can't get internet sharing to work. Nothing else has changed - well I've not changed anything else.

Another odd thing. If I leave the eth0 very much alone then the SMB sharing works fine. If I do the "ifconfig..." line above then SMB goes away. 

I haven't really much of a clue of what is happening here, although I'm learning by trial and error and experiment, and it's very disconcerting when something which was working unexpectedly stops!

Still more bizarre, when I booted into another ubuntu system which had previously worked, this one didn't work now either. Windows still works as before with internet and disk sharing. 

I'm puzzled.

Any light would be very much appreciated!

thanks,

Chris

---

### Post by redmk2 on 2008-09-08
Do you have a file listed below?```
/etc/samba/smb.conf
```

Not sure what all this means:> Install firestarter
Install dnsmasq
Make sure that dhcp3-server is NOT installed since I found that firestarter crapped out with an "unknown error" when it tried to start it.

Then: uncomment the line in /etc/sysctl.conf to allow forwarding

Add the line: ifconfig eth0 192.168.0.1 to /etc/init.d/rc.local

Then activate firestarter with the internet sharing option ticked and dhcp asked for.


To share files with a Windows host you need to have Samba and the Samba client "smbfs" installed.

Read [**[COLOR="Green"]Samba 3 by Example[/COLOR]**]("http://us1.samba.org/samba/docs/man/Samba-Guide/").  It's a great guide that will take you from the basics to very complex uses.

---

### Post by gregphil on 2008-09-08
Samba is the answer, but the most recent version of ubuntu 8.04.1switched gnome libraries and broke authenticated file sharing:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/224351](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/224351)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

---

### Post by redmk2 on 2008-09-08
@gregphil

It must be a setup problem.  I don't have the problems listed in the bugs.  The second bug is only related to AD domains, so it sure doesn't apply to simple workgroup setups.  The first listing seems to be abandoned due to lack of documentation of the problem.  I wonder way this only happens to a few users and not others.  What backend (database) are the smbusers stored in, etc.

---

### Post by gregphil on 2008-09-08
The sharing bug is real.  The reason it has not been fixed for so long seems to be denial that it could exit.  *many* bugs have been opened on this topic, most were closed as "duplicates" or unverified.

Re-read the bug reports I listed (all the way through) and note that the developers now believe the bug effects all authenticated share browsing of Windows boxes when the application is using the new gvfs library.

The reason sharing can still work for some, is many inexperienced users setup un-authenticated shares from Windows boxes (the default).  The new library works ok in this case. But un-authenticated shares are a security risk.

You could use command line sharing tools to get around the bug in the gvfs library.  See:

smbtree
smbclinet -L COMPUTERNAME
smbclient //COMPUTERNAME/SHARE


see the final comments of 
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

---

### Post by chris_tikva on 2008-09-09
Thanks for the replies... 

I tried again this morning and after the software equivalent of giving the machine a good kicking, the network came back to life. Try again this evening and zilch. So a few more good kicks in the form of disenabling and reenabling firestarter, restarting the network with /etc/init.d/networking, bring the ethernet card down and up again with ifconfig and then reassigning the ip address.....  Eventually, and I don't know which kick worked, I found the samba shares were available and even the network drive was on line as well. 

I have no idea what the problem is but now I know two things, first the hardware I have is capable of doing what it is supposed to and second there is the software equivalent of a loose wire somewhere. Unfortunately, being a novice, I have no idea where...

One question. I've put the ifconfig eth0 line in the file /etc/init.d/rc.local. Is that the best place for it if I want the network to start when I boot up?

---

