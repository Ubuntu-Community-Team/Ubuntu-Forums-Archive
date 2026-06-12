---
title: "Changing hostname - problem"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by nbakewell on 2008-09-25
Hello everyone,

I used the command *sudo hostname nsb_laptop* to change my newly installed Ubuntu virtual machine's hostname from it's default.  That worked well, but now whenever I use the sudo command, it throws me an error- *sudo: unable to resolve host nsb_laptop*.  After reading through the forums I realized that I need to edit /etc/hosts, since in that file it is still displaying my old hostname.  However, doing sudo nano /etc/hosts throws the same error, so after further searching I found this:

*gksudo gedit /etc/hosts*

That was working for most people.  However, I am getting this error: **Gtk-Warning **: cannot open display:**

I don't know what step to take next - any help?

---

### Post by jetsam on 2008-09-25
You should be able to boot the vm into recovery mode and then edit /etc/hosts from the terminal.  You may need to hit escape when the vm is first booting in order to see the boot menu that allows you into recovery mode.  

You'll then have root access and should be able to do:
```
nano /etc/hosts
```
Then change your host name in the file, save the file, and re-boot into normal mode and see if it works.  

I think this problem generally went away with a bug fix a while ago (see [bug 32609 here]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906")), but you must be using a vm that hasn't been updated with the fix.

---

### Post by theDaveTheRave on 2008-09-29
Hello all,

I have an issue changing my hostname, and this seems to be the correct place for getting help

here is my /etc/hostname file

> 
davem@Dartagnon:~$ more /etc/hosts
127.0.0.1 localhost
127.0.0.1 Dartagnan
134.157.195.42 Anticlimax

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

however as you can see the hostname for my loopback is <Dartagnan> but on my user prompt <davem@Dartagnon>

a call to <hostname> produces the same thing?
> 
davem@Dartagnon:~$ hostname
Dartagnon

if I change my hostname from the command line, I get the following.

> davem@Dartagnon:~$ sudo hostname Dartagnan
sudo: unable to resolve host Dartagnon
[sudo] password for davem: 


then I call hostname again and now it shows the correct detail

> 
davem@Dartagnon:~$ hostname
Dartagnan
davem@Dartagnon:~$ 


but my hostname file hasn't changed and neither has my prompt? here is my /etc/hosts

> 
davem@Dartagnon:~$ more /etc/hosts
127.0.0.1 localhost
127.0.0.1 Dartagnan
134.157.195.42 Anticlimax

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


I'm not sure what else to try to get the change to be permanet, and to be on my command line prompt? 

thanks in advance.

Dave

---

### Post by Iowan on 2008-09-29
Try changing /**etc/hosts** ```
127.0.0.1 localhost
127.0.[COLOR="Red"]1[/COLOR].1 Dartagnan
134.157.195.42 Anticlimax

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```Then change hostname via **hostname.**

---

### Post by theDaveTheRave on 2008-10-01
Thanks for the response, but I had another issue and I ended up re-installing Hardy from CDROM.

This definately had the desired result, but took a little longer than I had really wanted!

Oh well, alls well that ends well!

Dave

---

