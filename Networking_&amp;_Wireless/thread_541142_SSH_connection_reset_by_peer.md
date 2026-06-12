---
title: "SSH: connection reset by peer"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by SanguineIllusion on 2007-09-02
I just started using SSH with this ubuntu at work that we need some things set up on. I am connecting from home via SSH.

After a long and difficult time getting everything working, I was finally able to connect and get some stuff done.

Here's the problem: it seems like the SSH server gives me about 3 minutes to get what I need done before giving me the following error:

Read from remote host *IP ADDRESS*: Connection reset by peer

It's pretty consistently about 2 or 3 minutes. I need to use X forwarding to set up something and I absolutely cannot finish it. That's about all the information I can provide. I've tried putting my computer (not the server)  in DMZ temporarily and it didn't stop the problem. I've also added **KeepAlive yes** to the sshd_config on both my end and the server's end.

And if it offers any clue, if I get disconnected when I use the -X option (and sometimes without it) the server refuses any attempts to reconnect for a few minutes afterwards. Any help would be greatly appreciated :)

---

### Post by kevdog on 2007-09-02
Is sshd part of your /etc/hosts.allow file?

---

### Post by SanguineIllusion on 2007-09-02
> **kevdog said:**
> Is sshd part of your /etc/hosts.allow file?

That file doesn't appear to exist on both ends of this tunnel. Should i create it and what line(s) should I add.

---

### Post by kevdog on 2007-09-02
I think it only has to be on the server.

I think this file must exist by default. Either way try this:

sudo touch /etc/hosts.allow /etc/hosts.deny
echo "SSHD : ALL" | sudo tee -a /etc/hosts.allow

Here are a couple of links you might find interesting:
[http://www.samlesher.com/ubuntu/ubuntu-704-protect-your-ssh-server](http://www.samlesher.com/ubuntu/ubuntu-704-protect-your-ssh-server)
[http://www.ubuntugeek.com/securing-ssh.html](http://www.ubuntugeek.com/securing-ssh.html)

---

### Post by SanguineIllusion on 2007-09-03
Alright just did that on the server's end and it's still disconnecting me. I also did:
sudo /etc/init.d/ssh reload
and
sudo /etc/init.d/ssh restart

but I still keep getting connection reset by peer.

---

### Post by SanguineIllusion on 2007-09-03
bump...

---

### Post by kevdog on 2007-09-04
So you still can connect, but usually after 2-3 minutes you still keep getting disconnected???

Anything appear in your log file? /var/sys/log or dmesg?

---

### Post by SanguineIllusion on 2007-09-04
Ok I assume you meant /var/log/syslog? Nothing too interesting in there. Just some sort of hourly cron thing with php5 it seems. In dmesg I'm getting a lot of lines like this:

[324300.088392] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[324304.078699] e100: eth0: e100_watchdog: link down

Anywhere else I should check?

---

### Post by kevdog on 2007-09-04
When this event occurs, nothing appears in the logs?  Im kind of stuck with this one without any more info to diagnose the cause of the problems

---

### Post by SanguineIllusion on 2007-09-04
Is there some sort of ssh log? 

Syslog definitely has nothing, just hourly cron commands. I have trouble understanding dmesg's timestamping but the only possible entries that take place are those two I pasted, e100 watchdog. This computer isn't really used for anything else so I would have seen something different come up the several times I got disconnected.

Should I be checking anywhere else or on my machine (the client) somewhere?

---

### Post by kevdog on 2007-09-04
I think youve done this already, but the only thing on the client would help would be to initiate ssh with the -vvv option such as

ssh -vvvv ..........

---

### Post by noob12 on 2007-09-04
In a separate window, you might try running **tail -f /var/log/kern.log** and keep it running.  See if those link down messages coincide with your disconnects. [Note that you eventually will have to CTRL-C quit out of the tail -f command or kill that window, or it will keep watching the log forever.]

ADDED:  You might want also to open a third window and run **tail -f /var/log/syslog** as well.

If that ends up being the culprit, we should look at your full **dmesg**.  You might be able to add some boot flags to get around this.

---

### Post by SanguineIllusion on 2007-09-06
> **kevdog said:**
> I think youve done this already, but the only thing on the client would help would be to initiate ssh with the -vvv option such as

ssh -vvvv ..........
Noob12 I'm going to try your idea next, I did -vvv and here's what happened when it dropped me:

debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i0/0 o0/0 fd 4/5 cfd -1)

debug3: channel 0: close_fds r 4 w 5 e 6 c -1
Read from remote host #.#.#.#: Connection reset by peer
Connection to #.#.#.# closed.
debug1: Transferred: stdin 0, stdout 0, stderr 100 bytes in 40.7 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 2.5
debug1: Exit status -1

**ALSO** Noob12, these commands you need to run in separate windows, am I supposed to be doing this on my remote machine or the SSH server itself? I need to know because if it's the latter I'm going to need to get somebody to sit down and I'll walk them through it with your directions.

---

### Post by noob12 on 2007-09-06
They were meant for the client host.  I was just curious if your those link bouncing messages are occurring coincident with your loss of ssh connection.

---

### Post by SanguineIllusion on 2007-09-07
> **noob12 said:**
> They were meant for the client host.  I was just curious if your those link bouncing messages are occurring coincident with your loss of ssh connection.
Sorry it took so long, I just got a chance to try out what you suggested. When my connection closed, nothing changed in kern.log and the only thing that happened around the same time in syslog was the following:

** MY-MACHINE /USR/SBIN/CRON[10642]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)**

Where MY-MACHINE is the name of my computer. I am running firefox and trying to install a php app called SugarCRM if this explains anything. I was in a different terminal window so I don't know if this message came up immediately prior to me getting disconnected or if it just ran when i started firefox and loaded the installation php file.

Any ideas?

---

### Post by noob12 on 2007-09-07
Sorry.  No.  I was hoping for a relationship between those two events.  Have no guesses otherwise.

---

### Post by eentonig on 2007-09-07
Can you open a few seperate  consoles.

On each of them, ssh to the remote server.
In the first, do

> ping - v <ip address for ssh server>

> tail -f /var/log/messages

> tail -f /var/log/kern.log

> tail -f /var/log/syslog

and then a console window without ssh
> ping -v [www.google.com](www.google.com)


And now check what happens if you loose your connection.

In the mean time. Is your server behind a FW? What brand? Do you have the same issue when you ssh to it at work?

---

### Post by SanguineIllusion on 2007-09-09
HI. Just tried.

Yes I believe the server is behind a firewall, I can probably find out from the manager this evening but I don't have it off hand. Also I actually live in another state from the main office so I've never tried SSH locally and neither has anyone else there (windows users).

I think maybe I did something wrong? My consoles got disconnected at different times. The first was the one I know to happen, running the SugarOS installation in firefox:

> firefox localhost/SugarOS

I got connection reset by peer on that one while everything was running. The next to fall was **syslog** and it died as far as I can tell, immediately after this line:

> Sep  9 19:39:01 Ubuntu /USR/SBIN/CRON[3868]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Read from remote host *IP*: Connection reset by peer


**Kern.log** is silent, **messages** just has --MARK-- every 20 minutes it seems, but is **STILL RUNNING** and the ping just kept going until I got the same:

> Read from remote host 75.18.112.203: Connection reset by peer

I'm pretty sure this happened independently of the other disconnections.

Does this offer any clues? I'm kind of suspicious of that cron php5 line, but other than that, I've got no idea...

---

### Post by robert_pectol on 2007-09-10
I bet it just needs a keep-alive.  Try adding the following to your /etc/ssh/sshd_conf on the server:
```
KeepAlive yes
ClientAliveInterval 60
```
Let us know how it goes.  Good luck.

---

### Post by SanguineIllusion on 2007-09-10
> **robert_pectol said:**
> I bet it just needs a keep-alive.  Try adding the following to your /etc/ssh/sshd_conf on the server:
```
KeepAlive yes
ClientAliveInterval 60
```
Let us know how it goes.  Good luck.
I already had KeepAlive yes in there but I added ClientAliveInterval 60, restarted the ssh service but it still continues to crash a few minutes in when im running that installation in firefox with **connection reset by peer**.

---

### Post by SanguineIllusion on 2007-09-12
Any ideas?

---

### Post by psusi on 2007-09-12
The interface should not keep going down and coming up again all the time.  It looks like you have a hardware problem with your ethernet network.  

And you need to run the log and ping commands on the server obviously, since you won't be able to see them remotely when you disconnect.

---

### Post by SanguineIllusion on 2007-09-13
If this helps at all I was trying to get some help in IRC and they had me run a TCP dump to determine if the connection was being closed on my side or the server side. I ran a loop to print the date and every time I get disconnected at approximdately 2:45 or 3 minutes. Also in the tcp dump, it appears that the disconnect is coming from the server side because I have an RST packet originating from it's ip that seems to initiate all the problems.

---

### Post by psusi on 2007-09-14
This is likely caused by the interface bouncing up and down.  The server disconnects the socket because the interface is down, then when the interface comes back up, as soon as the client tries to send anything, the server responds with an RST since the socket is no longer valid.

---

### Post by SanguineIllusion on 2007-09-14
Ok, but i mean why would the connection keep going down at that set interval of approximately 3 minutes? What should I be telling the guys that have access to the machine itself to do?

---

### Post by psusi on 2007-09-14
Tell them to test the ethernet connection with a good ethernet cable/signal tester.  If a problem with the line/switch is ruled out, then try changing the ethernet card to get the constant ups/downs to go away.  You might also look at the ethernet error statistics, and see if you can maintain a solid connection to some other service, such as a bulk http download.

---

