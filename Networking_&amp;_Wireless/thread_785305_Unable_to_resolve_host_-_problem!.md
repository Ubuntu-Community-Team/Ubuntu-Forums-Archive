---
title: "Unable to resolve host - problem!"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by Tim Silver on 2008-05-07
Hi,

I'm completely new to Ubuntu (only installed it this morning), so please forgive!

8.04 installed on external hard drive on Dell Inspiron 9400.

I was following the 'sticky' by kevdog but stumbled at first hurdle!

I typed 'lshw -C network' and got the details of both my wireless and ethernet interfaces - fine.

Then, 'sudo ifconfig wmaster0 down' gave the response - 'sudo: unable to resolve host tim-laptop'

Could someone point me to appropriate reading please. The only thing I can add is that I'm pretty sure it's not a hardware issue.

---

### Post by chili555 on 2008-05-07
I'm pretty sure it's not hardware, either. Could you please post the result, in a terminal, of:```
cat /etc/hosts
```Let's see if we need to tweak it a bit.

---

### Post by BightningLug on 2008-05-07
I get the same "unable to resolve host" message.

Here's the results of cat /etc/hosts
```
127.0.0.1 localhost
127.0.1.1 hog-dev.hog.dev

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by chili555 on 2008-05-07
When you open a terminal, does it report the name of your computer as *tim-laptop* like mine does LAPTOP60?```
chili@LAPTOP60:~$
```My hosts file relates LAPTOP60 to 127.0.1.1.```
127.0.0.1 localhost
127.0.1.1 LAPTOP60

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```I suggest making a backup of your hosts file, just in case we err:```
sudo cp /etc/hosts /etc/hosts.bak
```Then I suggest *sudo gedit /etc/hosts* to amend it to:```
127.0.0.1 localhost
127.0.1.1 tim-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```Save and close gedit. Then restart networking:```
sudo /etc/init.d/networking restart
```Then let's see if your problems have been solved.

Any idea where: hog-dev.hog.dev came from?

---

### Post by Tim Silver on 2008-05-08
Hi Chilli,

Thanks for reply (sorry for delay but have to do this at work!)

```
tim@tim-laptop:-$ cat /etc/hosts
127.0.0.1 locahost
127.0.1.1 tim-laptop.PMS

#The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff03::3 ip6-allhosts
192.168.1.193 Tim Host
tim@tim-laptop:-$
```

The PMS will be the company network (I guess). I'm not trying to connect to the network - just to the router for internet access.

---

### Post by mattress on 2008-05-08
Howdy...

I think it may be a problem with the last entry in your hosts file:
```

192.168.1.193 Tim Host

```


Try changing that to something else or commenting it out with a #
Generally host entries are like so:
```


IP hostname alias
192.168.0.1  mymachine.mydomain.com mymachine

```

I could be wrong though...

---

### Post by Tim Silver on 2008-05-08
Hi mattress,

I'll try that but won't be able to do so for 3 hours (lunch-time in the UK). However, I think my problem may be more serious. When in a terminal, the cursor stops blinking, turns white (just borders showing) and freezes - I have to 'click' in the window to continue. I installed 8.04 from a live CD and have read (subsequently) that I should have performed a 'clean' install.

---

### Post by Tim Silver on 2008-05-08
mattress,

Before changing the 'hosts' file, I first went to make a backup of it (as suggested by Chili555). Here's the result -
```
tim@tim-laptop:-$ sudo cp /etc/hosts /etc/hosts.bak
sudo: unable to resolve host tim-laptop
tim@tim-laptop:-$
```

!!!!!!!!!!!!!!!!!!!

So what do I do now? I'm fully prepared to start from scratch but, of course, XP no longer sees my external drive so I can't format it. Any suggestions most welcome.

---

### Post by jetsam on 2008-05-08
This is a new kink in Hardy-- sudo fails if your hostname can't resolve.

You need to edit the file to function as per post 4, but since you can't sudo, you're stuck in a catch 22.

Two possible solutions:
try 
```
gksudo gedit /etc/hosts
```
might work, and is easier.  Several people have reported that gksudo works for them even when sudo fails. If you can get gedit running, you may be able to make a copy from gedit before you change the actual file.

The other possibility is to reboot into recovery mode.  This will give you root access and allow you to copy the file and edit it with 
```
nano /etc/hosts
```
or the terminal based text editor of your choice.

---

### Post by Tim Silver on 2008-05-08
Hi Jetsam,

```
gksudo gedit /etc/hosts
``` - cursor just went to new line and did nothing.

I then booted into recovery mode (scary! well, it was my first time and I'm only 55::lolflag:), commented out the last line and saved.

Continued with normal boot, opened terminal and typed
```
sudo ifconfig wmaster0 down
```
still got the same
```
sudo: unable to resolve host tim-laptop
```

'Mattress' also suggested trying to change the 'hosts' file along the lines of
```
IP hostname alias
192.168.0.1  mymachine.mydomain.com mymachine
```
If I replaced <mymachine> with <tim-laptop>, where might I find the <mydomain.com> info?

---

### Post by jetsam on 2008-05-08
You can add secondary host definitions after the first one.  

```
**127.0.1.1 tim-laptop** tim-laptop.PMS
```
...would resolve both tim-laptop and tim-laptop.pms to the local machine.  

The important part, though, for sudo, is just the first part in bold above.  You need to be able to resolve your hostname without the domain extension.

Are you sure you set this line correctly?  I'm concerned that this isn't working.

---

### Post by jetsam on 2008-05-08
If you're still stuck, a status update might help with diagnosis.  Can you post the output of:
```
cat /etc/hosts
```
```
cat /etc/nsswitch.conf
```
and
```
ping -c3 localhost
```
They really ought to change sudo back so this doesn't happen.  A bunch of new users are getting caught up with this.

---

### Post by diegomedaglia on 2008-05-08
Hi! I just had this problem. You have to become a superuser to edit your /etc/hosts, but you've got to have your root password set.

[LIST=1]
[*]go to System->Administration->Users and Groups
[*]click on 'Unlock' and enter your administrator password (for some reason this authentication still works)
[*]select user 'root' and click 'Properties'
[*]in the fields below 'Set Password by hand' enter a new password (must be 6 characters long)
[/LIST]
You should now be able to become superuser. Open a terminal and code:
```

su
gedit /etc/hosts

```
My problem was the line like "127.0.1.1 tim-laptop.PMS". I just removed the ".PMS" and it started working again. In my case I had
127.0.1.1 diego-ubuntu.WORKGROUP
Changing it to "127.0.1.1 diego-ubuntu" did the trick.

Hope this helps!

---

### Post by Tim Silver on 2008-05-09
Morning!

Right, jetsam, results:
```
cat /etc/hosts
```
returned
```
127.0.0.1 localhost
127.0.1.1 tim-laptop.PMS

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localhost
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff002::3 ip6-allhosts
#192.168.1.193 Tim Host
```
(Remember that you suggested I try commenting out the last line)

```
cat /etc/nsswitch.conf
```
returned (there was some commented out stuff that I haven't bothered typing as I'm guessing you already know what it says:lolflag:)
```
passwd:      compat
group:       compat
shadow:      compat

hosts:       files mdns4_minimal (NOTFOUND=return) dns mdns4
network:     files

protocols:   db files
services:    db files
ethers:      db files
rpc:         db files

netgroup:    nis
```

and
```
ping -c3 localhost
```
returned
```
PING localhost (127.0.0.1 56(84) bytes of data
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl64 time=0.041 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl64 time=0.040 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl64 time=0.039 ms
--- localhost ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.39/0.40/0.41/0/000 ms
```
(I think I copied all of that correctly)

I'm now going to remove the hash from the last line of hosts and try what diegomedaglia suggested. I'll keep you informed!

---

### Post by jetsam on 2008-05-09
OK.  That's all good.

Make your file look like this:
```
127.0.0.1 localhost
127.0.1.1 [COLOR="Red"]tim-laptop[/COLOR] tim-laptop.PMS

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localhost
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff002::3 ip6-allhosts
#192.168.1.193 Tim Host
```

Changes in red.  You can leave the last line commented.  I don't think it will do any harm either way, but I don't think it's necessary, either.

---

### Post by Tim Silver on 2008-05-09
Well, I've tried without the .PMS as per diegomedaglia and with the extra <tim-laptop> as per jetsam. (I must admit that it was a nicer experience editing through 'super user' method rather than in recovery mode - although it changed my keyboard settings to US!)

Sorry guys, but still no internet!

It's probably me. I'm working on the assumption that the heron will automatically see the available wireless connection just like XP does. Is this assumption correct, or might there be some more basic step that I should have performed?

---

### Post by jetsam on 2008-05-09
Ok.  We haven't really gotten to work on the internet connection problem yet because the sudo problem came up.  Wireless can be tough, or it can be easy, and I'll have to beg off on any more specifics than that because I'm personally utterly unfamiliar with it.  Hopefully someone else can help get you going.  

Can you sudo now?  If you need a test case, try 
```
sudo ls
```
It should ask you for your user password, and then give you a directory listing.  It's important that sudo work; you'll need it for any further configuration that you do.

---

### Post by Tim Silver on 2008-05-09
Jetsam - brilliant - I can sudo! (I'd forgotten that we sorting sudo - like I said, it's an age thing)

Thank you

Now what do I do?

Oh yes, I remember. Continue with the 'sticky'!

---

### Post by killdragon on 2008-05-09
Hi,

  I can only point you to something that worked for me

 search for Scotsgait post from about a week ago.

He called it Hardy Headaches

---

### Post by jetsam on 2008-05-09
**Killdragon**:  Thanks for that, but that thread is a less convoluted version of what just got fixed.  

**Tim**:  I'm glad there's been some progress and you're all set in the sudo department.  I didn't realize you had to re-type everything, or I wouldn't have asked for so much output!  You should be fine with Linux, though, with that kind of tenacity.    

I was tired last night.  The official Ubuntu documentation has the simple version of wireless that if you're lucky will do it for you:
[https://help.ubuntu.com/8.04/internet/C/wireless.html]("https://help.ubuntu.com/8.04/internet/C/wireless.html")
Have a look at it and try the stuff under "connecting using network manager" before you start digging into forum how-tos.  

If wireless turns out to be giving you much grief, you might consider plugging in if it's possible.  Wired connections can be a lot easier to get going.  That's just me though; I have a tendency to recommend the things I understand over the things I don't.  ;)

---

### Post by kevdog on 2008-05-09
wmaster0 is the wrong interface.  Can you post your entire ifconfig?

---

