---
title: "can't close port 22"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-07-18
I was playing around with openSSH, successfully as it turns out as I was able to establish a connection. But now that the fun's over I wanted to close off port 22, only I can't seem to do so. I tried

```
sudo ufw deny 22
```

as well as

```
sudo ufw default deny
```

but when I ran an nmap scan it showed that port 22 is still open. Is there a way to close it back up? I hate feeling vulnerable.

---

### Post by AlphaLexman on 2010-07-18
port 22 ([http://localhost:22](http://localhost:22)) is reserved for the 'ssh' secure logins. See [http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers) for more info.

---

### Post by whitethorn on 2010-07-18
Have you tried turning off the ssh daemon?  

```
sudo /etc/init.d/sshd stop
```

---

### Post by Chris1274 on 2010-07-18
That doesn't seem to work. Here's the result I got:

```
sudo: /etc/init.d/sshd: command not found
```

I then tried:

```
sudo stop /etc/init.d/sshd
```

and was told:

```
stop: Unknown job: /etc/init.d/sshd
```

---

### Post by ajgreeny on 2010-07-18
```
sudo service ssh stop
``` will do it.

---

### Post by Chris1274 on 2010-07-18
That did it, thanks!

---

### Post by alphacrucis2 on 2010-07-18
> **ajgreeny said:**
> ```
sudo service ssh stop
``` will do it.


Yeah but it will probably come back again next time he reboots. Not sure of the recommended way in Ubuntu/Debian but in Redhat you use chkconfig to set whether or not a service is to be started.

Found this:

[http://www.liberiangeek.net/2010/05/how-to-start-stop-services-in-ubuntu-lucid-automatically/]("http://www.liberiangeek.net/2010/05/how-to-start-stop-services-in-ubuntu-lucid-automatically/")

---

### Post by stmiller on 2010-07-18
```
sudo apt-get install sysv-rc-conf
```

Then run 

```
sudo sysv-rc-conf
```

This lets you enable/disable services at different run levels.

---

### Post by Chris1274 on 2010-07-18
It's odd, sysv-rc-conf doesn't show the ssh service as being active (no X's in any of the run levels), yet as was said, when I reboot and do a port scan it shows port 22 open.

---

### Post by alphacrucis2 on 2010-07-19
> **Chris1274 said:**
> It's odd, sysv-rc-conf doesn't show the ssh service as being active (no X's in any of the run levels), yet as was said, when I reboot and do a port scan it shows port 22 open.

I'm getting the same result. Doing ```
ps -e | grep sshd
``` shows that the ssh daemon is running yet it isn't marked in the list displayed by sysv-rc-conf. Hmmmmm.  Perhaps a bug in sysv-rc-conf ??

---

### Post by Chris1274 on 2010-07-19
.

---

### Post by 3rdalbum on 2010-07-19
sysv-rc-conf will not be able to activate or deactivate the SSH service, because Ubuntu doesn't use SysV Init anymore. (hasn't done so since Ubuntu 9.04, please keep up-to-date with your advice, people!).

If you're not going to use SSH again then you can just remove it.

Also I believe nmap will still show the SSH port open even when firewalled, if you are running it on the same computer as the SSH service. Firewalls work on traffic from other computers, not traffic on the same computer.

---

### Post by Chris1274 on 2010-07-19
Removing ssh-server does work, it just seems like throwing in the towel :-({|=

---

### Post by ajgreeny on 2010-07-19
You may be able to do this with an edit of /etc/rc.local by adding ```
service ssh stop
``` just above the "exit 0" line at the end.
Note no sudo is needed as this is run by root at boot-up.

I'm just about to try it out.

EDIT:

Yes it works with no problem; after a reboot sshd is not running.

You can now start sshd manually when you need it with ```
sudo service ssh start
```

---

### Post by Chris1274 on 2010-07-19
Works perfectly.

How did you know that /etc/rc.local was the file to edit? (just some newbie curiostiy)

---

### Post by ajgreeny on 2010-07-19
> **Chris1274 said:**
> Works perfectly.

How did you know that /etc/rc.local was the file to edit? (just some newbie curiostiy)
From enormous use and reading of this forum I have learned a great deal about Ubuntu and Linux in general.  The /etc/rc.local file is where all user scripts that would normally require sudo privileges to run can be put.

Make a note of that and file it away somewhere, and you may find it useful in the future.

I have a folder in home called quicknotes, and use the quicknotes add-on in Firefox, so when I see something useful like that I quickly copy it to a txt file note and save it.  The folder is getting pretty full of short notes now, but I use it a lot as a quick reminder of command and tips.

---

