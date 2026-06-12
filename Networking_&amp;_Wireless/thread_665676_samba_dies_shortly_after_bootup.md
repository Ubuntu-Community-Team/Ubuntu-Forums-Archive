---
title: "samba dies shortly after bootup?"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by ebutton on 2008-01-12
Hi All,
I know that there is apparently an open bug report about a problem with samba at boot time, but it doesn't seem to be what I'm experiencing with Linux ubuntu 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64 GNU/Linux.

I have to restart samba after booting up before I can see my shared drives from any other system on my home network.  When I do restart samba, as shown below, I get an error indicating an expected process is not there.  Sure enough, after the restart there are three samba processes and I can use the shared drives normally from the other systems (XP and Ubuntu).

So,
1.  Is this a known bug?

and,
2.  If not, then what should I look at?  I've already found and changed one etc/samba configuration file entry, changing "available=no" to "available=yes".

Regards,
EdB

Here's the output:
userx@ubuntu:~$ ps -ef | grep smb
root      4753     1  0 13:48 ?        00:00:00 /usr/sbin/smbd -D
root      4864  4753  0 13:48 ?        00:00:00 /usr/sbin/smbd -D
userx   5377  5359  0 14:19 pts/0    00:00:00 grep smb
userx@ubuntu:~$ sudo /etc/init.d/samba restart
[sudo] password for userx:
 * Stopping Samba daemons...                                                    start-stop-daemon: warning: failed to kill 4743: No such process
                                                                         [ OK ]
 * Starting Samba daemons                                                [ OK ] 
userx@ubuntu:~$ ps -ef | grep smb
root      5444     1  0 14:20 ?        00:00:00 /usr/sbin/smbd -D
root      5448  5444  0 14:20 ?        00:00:00 /usr/sbin/smbd -D
root      5450  5444  0 14:20 ?        00:00:00 /usr/sbin/smbd -D
userx   5452  5359  0 14:21 pts/0    00:00:00 grep smb
userx@ubuntu:~$

---

### Post by MacMan on 2008-01-15
I know this doesn't help much, but I have the very same problem myself.

I've upgraded from Feisty tu Gutsy (i386 version) and now samba doesn't work unless I start it manually. The links in /etc/rc*.d/ are there and seem ok, and samba works well after I restart it.

There's no sign of this kind of "sudden death" in the samba logs and I don't know where to look for troubleshooting this issue.

Thanks for any advices.

*Edit*: This post looks promising: [post]2948903[/post]

Ciao.

---

### Post by ebutton on 2008-01-19
Hi,
Thank you for the tip/link.  I did try an edit to /etc/init.d/samba, inserting an explanatory comment and a "sleep 30" immediately following the [log_daemon_msg "Starting Samba daemons"] line.  I first saved a pristine copy to file "samba.original", for safety.

I still have only two smbd processes after a system restart.  I still get the "no such process" on a manual samba restart from the command line, but the restart gives me three smbd processes and makes things work.  (As before.)
Note:  ps -ef | grep smb
to check running processes.

The only difference after my edit is that the manual samba restart pauses 30 seconds, so maybe this file is not used at boot time but only for command line entries.

I will look into the rc scripts that run at boot time, but that's above my skill level so unless I can get a better understanding of those, I probably will wait for someone to post some very specific instructions of what to edit.  My very limited knowledge is that the numbered rc files get executed in sequence by ascending numeric value, but that's about only enough knowledge to break my system beyond repair.  Still, it should be possible to change things so that samba doesn't try to start before the network interface is up.  Assuming that is the actual problem, which is not at all certain.

Regards,
Ed

---

### Post by ebutton on 2008-01-19
Update

I installed sysv-rc-conf with Synaptic, then read the man pages and started it in "priority mode" with the following shell command.

sudo sysv-rc-conf -p

I set samba to "S30" in run levels 2-5 (was S20 in those).  If that doesn't work, I'll set it to "S99", as that worked in the linked post.  I just don't think it needs to be set to the very last priority.

Now I will restart this machine and post the result.

Regards,
Ed

---

### Post by ebutton on 2008-01-19
No joy.  I tried "S30" and "S99" but no help.

I'm back to searches on these forums.

Regards,
Ed

---

### Post by MacMan on 2008-02-07
> **ebutton said:**
> No joy.

No joy for me either.

The only news I have is that I'm not so sure anymore Samba dies at boot-time. A few days ago, I manually restarted it and then left the PC on.
When I tried it again, after 10 or so hours, samba was out-of-service again.

So the problem may unrelated to the rc.x scripts, it could be a bug or a issue with my current configuration.

One hint I have yet to try is SWAT, which should help troubleshoot samba's configuration. I have found [this link on Linux.com](http://www.linux.com/feature/125452) that looks interesting, but I haven't found the time to try it yet.

Ciao.

---

