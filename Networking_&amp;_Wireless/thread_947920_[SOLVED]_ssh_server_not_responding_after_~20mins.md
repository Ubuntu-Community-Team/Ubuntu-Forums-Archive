---
title: "[SOLVED] ssh server not responding after ~20mins"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by scottie277 on 2008-10-14
Hello,
I am running ubuntu 8.04.1 (x64 ) on a new Mac Pro. The install went smoothly, except that the ssh server is not working properly.
I used synaptic to install the open-ssh server. I rebooted and was able to ssh into my Mac Pro from another computer.
The problem is that if I leave the Mac Pro sitting with no one logged in via ssh, the ssh server will not accept incoming users after about 20mins. I just get a timeout error. Does anyone have any thoughts as to why the ssh server would stop accepting incoming connections after some idle time?

Some other potentially useful info:
When the Mac Pro is booted into OSX, the OSX ssh server does not have this problem. 
When the Mac Pro is booted into Windows, the Cygwin ssh server does not have this problem. 
This makes me think that this timeout is not a hardware issue.
Any help would be appreciated.

---

### Post by cariboo on 2008-10-14
I found this in another forum:

> This sounds suspiciously like the connection timing out, possibly due to a NAT/firewall dropping the connection or something like that.

You can workaround the issue by putting:

KeepAlive yes

into your ~/.ssh/config

Jim

---

### Post by scottie277 on 2008-10-15
> **cariboo907 said:**
> I found this in another forum:



Jim
cariboo907, thanks for this suggestion...
I don't have a config file in my ~/.ssh dir. I doubt this would solve the problem though...let me better explain.

My ssh connection is not timing out once I am connected, rather after my Ubuntu machine sits (with no one logged in locally or remotely) for about 20 mins, no one can log in via ssh.
For example if I physically sit at the machine and log in locally, everything is fine. Now if I log out and go get a coke and come back 20 mins later and try to remotely log in, I get no response from the ssh server.
So, again, once I am connected remotely via ssh I can stay connected indefinitely. The problem is occurs when no one is logged in for >20mins.
Any thoughts.

---

### Post by cariboo on 2008-10-15
Can you ping the server or access shares? Does networking restart when you access the server directly, or do have to restart networking before you can access it again?

Jim

---

### Post by scottie277 on 2008-10-16
> **cariboo907 said:**
> Can you ping the server or access shares? Does networking restart when you access the server directly, or do have to restart networking before you can access it again?

Jim

I just tried to ping the ubuntu machine and it returned a Dest Unreachable error. I then walked over to the Ubuntu Machine, logged locally, opened firefox to "wake up" the eth connection. As I did this, my remote ping started returning packets and working properly.
Now I can ssh into my box, but after another 20mins in idle, the same not responding stuff happens.
This is really strange! I've used Fedora for years and never had any issues with ssh/networking.

---

### Post by DataMatrix on 2008-10-16
I think that you should be able to workaround this problem by setting up a cronjob to ping something, let's say google.com, every 15-20 minutes. this should keep the connection "awake" if mozilla was able to wake it locally.

Also, check for any powersaving features, I'm not very familar (or likeing MACs verymuch for that mater) with MAC-s

How to setup a cron task via terminal (or atleast this is the only way i know):
user@computer:~$ crontab -e
(nano starts here, add the folloing line, it'l start a ping every hour in 9,19,29,39,49,59 minutes thrugh the hour)
```
9/* * * * * ping -c 10 google.com
```
If you're in nano press ctrl+x , press "y" to accept saving and press enter to save (confusing, i know).
crontab says: _crontab: installing new crontab064/0.092/0.010 ms_

---

### Post by jerome1232 on 2008-10-16
offtopic

I wonder how much bandwidth google wastes on ping responses :)
We should start pinging Microsoft websites for testing.

---

### Post by DataMatrix on 2008-10-16
> **jerome1232 said:**
> offtopic

I wonder how much bandwidth google wastes on ping responses :)
We should start pinging Microsoft websites for testing.
You're right. Unfortunately, microsoft has disabled ICMP on their machines, or atleast i'm not getting any reply when their sites are opening properly. :(

---

### Post by scottie277 on 2008-10-18
> **DataMatrix said:**
> I think that you should be able to workaround this problem by setting up a cronjob to ping something, let's say google.com, every 15-20 minutes. this should keep the connection "awake" if mozilla was able to wake it locally.

Also, check for any powersaving features, I'm not very familar (or likeing MACs verymuch for that mater) with MAC-s

How to setup a cron task via terminal (or atleast this is the only way i know):
user@computer:~$ crontab -e
(nano starts here, add the folloing line, it'l start a ping every hour in 9,19,29,39,49,59 minutes thrugh the hour)
```
9/* * * * * ping -c 10 google.com
```
If you're in nano press ctrl+x , press "y" to accept saving and press enter to save (confusing, i know).
crontab says: _crontab: installing new crontab064/0.092/0.010 ms_

Thanks for the suggestion DataMatrix, but I don't want to have to constantly ping some host just to keep my ssh server running. I am confident that this is not a power setting on the mac, because when the same machine is booted in OSx, the ssh server runs fine.

I have tried adding 
"KeepAlive yes"
"TCPKeepAlive yes"
"ServerAliveInterval 10"
to both the /etc/ssh_config and /etc/sshd_config
None of these worked.

I also tried turning off my roaming enabled setting in the network manager. This didn't solve the problem either. I also tried setting my ip address statically and the same issue happened.
I even tried uninstalling the network manager and installing autossh.

At the end of the day (actually about a week now), I even reinstalled Ubuntu, updated it, and found the same problem.
I'm about ready to give up and go with Fedora. Does anyone have any ideas? It would be a shame to switch because Ubuntu has so many nice features, but a 24/7 ssh server is completely essential to my work.

---

### Post by DataMatrix on 2008-10-19
> **scottie277 said:**
> Thanks for the suggestion DataMatrix, but I don't want to have to constantly ping some host just to keep my ssh server running. I am confident that this is not a power setting on the mac, because when the same machine is booted in OSx, the ssh server runs fine.

I have tried adding 
"KeepAlive yes"
"TCPKeepAlive yes"
"ServerAliveInterval 10"
to both the /etc/ssh_config and /etc/sshd_config
None of these worked.

I also tried turning off my roaming enabled setting in the network manager. This didn't solve the problem either. I also tried setting my ip address statically and the same issue happened.
I even tried uninstalling the network manager and installing autossh.

At the end of the day (actually about a week now), I even reinstalled Ubuntu, updated it, and found the same problem.
I'm about ready to give up and go with Fedora. Does anyone have any ideas? It would be a shame to switch because Ubuntu has so many nice features, but a 24/7 ssh server is completely essential to my work.

If you're concerned about generated traffic, you can set the ping to work with your local interface (i.e. eth0's IP address). Ping isn't memory or cpu consuming (much).

You can also take a look in /etc/sysctl.conf and if you make any changes, run ```
sysctl -p
``` to reload (or just restart). I didn't find anything in mine that would indicate a solution to your problem.

I didn't find anything useful in /etc/networking either.

:confused:

---

### Post by P5791 on 2008-10-20
if you can't ping the interface it will not respond to any packet so tweaking your ssh settings won't help.

Check your power savings settings to make sure your network interface isn't turned off.

The ubuntu power settings may differ from OS X

---

### Post by scottie277 on 2008-10-20
> **DataMatrix said:**
> If you're concerned about generated traffic, you can set the ping to work with your local interface (i.e. eth0's IP address). Ping isn't memory or cpu consuming (much).

You can also take a look in /etc/sysctl.conf and if you make any changes, run ```
sysctl -p
``` to reload (or just restart). I didn't find anything in mine that would indicate a solution to your problem.

I didn't find anything useful in /etc/networking either.

:confused:

Thanks DataMatrix, I did the ping suggestion and it is working.
I am familiar with nano so, I had no problems. Most Linux distros that I have used use vi for crontab -e. Anyway, I tried pinging the computer itself three times every five minutes e.g.
*/5 * * * * ping -c3 127.0.1.1
but this didn't work. I imagine this is because it is not pinging anything external.
I also tried pinging the machine's ip address and this didn't work either. I guess because the ip is a LAN ip and not a WAN ip.

Anyway, I bit the bullet and added a crontab job as root.
*/5 * * * * ping -c3 google.com

Now the machine does not turn off its network connection after idle time and is functioning properly. Now that I know that the problem is with the eth0 connection and not the ssh server, I will post a new thread on this topic. But, thanks for the help. Although bandaged, I consider this problem effectively fixed.
Cheers! :)

---

### Post by jerome1232 on 2008-10-20
Honestly it's not a bandwidth hog or anything :) But if your truly concerned are you connected a router? You could ping that.

---

### Post by scottie277 on 2008-10-20
> **jerome1232 said:**
> Honestly it's not a bandwidth hog or anything :) But if your truly concerned are you connected a router? You could ping that.

I'm on a university campus, so I'm sure there is a server here that is doing the routing, but our tech folks aren't the best, so I don't want to bother asking them questions that they probably can't answer anyway.

The pinging of google seems to work fine for now, I agree that this is a very minor use of resources, so I'm satisfied for now.
Thanks again for the suggestions.
:)

---

### Post by QaysHP on 2009-06-09
I was running into a similar problem, but think I found the culprit. If not logged in locally (either log out, or fresh reboot) my box will not be on the network. On my machine running Desktop Edition 9.04 this resolves the issue (and recreates it when undone).

Note: Only applies if you use custom network settings, and not "Auto eth0."

Open System -> Preferences -> Network Connections. Select the network configuration that you are using and click edit (double-clicking works as well). You may need to authenticate, this is fine. On the window that comes up there is a check box at the bottom that says "Available to all users," you will want to select this and apply the settings.

Basically, the network interface doesn't have access to this configuration when you are not logged in, and thus will not appear on the network. "Auto eth0" (the default) has this already enabled.

---

### Post by lensman3 on 2009-06-09
I use the following script that is run from a cronjob.  This script is called keepalive.sh and lives in /usr/local/bin

```
#!/bin/sh

if [ -f /var/run/dhclient-eth1.pid ] ; then
 ping -c4 -l3 67.165.192.1  2>&1 | grep "0 received" > /dev/null && \
  { /sbin/ifdown eth1 > /dev/null; sleep 2; /sbin/ifup eth1; }
else
  /sbin/ifdown eth1;
  sleep 2;
  /sbin/ifup eth1;
fi
```


My outgoing router is a linux firewall and the Internet side Ethercard is eth1.   67.165.192.1 is my default gateway for that interface.  This cronjob runs once a minute.

---

