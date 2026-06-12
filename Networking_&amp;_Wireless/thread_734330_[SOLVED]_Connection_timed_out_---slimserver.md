---
title: "[SOLVED] Connection timed out ---slimserver"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by Fjatle on 2008-03-24
Hi!
I have posted this one on the slimdevices forums, but maybe there is some clever geeks here to help me out :)

(Not sure if networking is the best place to post, but anyway here it is)

I'm running Ubuntu Gutsy.. My Squeezebox have been running fine, but after a complete fresh re-install of Gutsy, things have not been working that good.

I first tried Squeezecenter 7.0... Now, the entire system was extremly slow.
When using the remote controll to browse the Squeezebox, there was almost no
response. And when I tried to remote it from my web-browser, I got an error
(which is displayed on the squeezebox) "connection to server timed out"..

Changing settings seemed to be working OK. Changing font and stuff, seemed to
have a quick response. It's whenslimserver cannot connect to server ubuntu I press Play, the bug happens.

So, I tried to upgrade to Squeezecenter 7.01 (from the unstable repos)...
Still the same problem..

Then I went into synaptic PM, and ticked squeezecenter for complete removal.

Next, I installed the slimserver which is originally in the repos (v6.3.0-5).

Now the player was not that slow anymore. I could easily browse with the remote controll, with good response.

But when I hit Play, the same problem occur. Both when I click play from the remote controll, and when I access it from the web-browser.

I have seen a tips about restarting the router by unplug/plug the power with no result.

I have a feeling that mysql is the sinner. But I have absolutely no clue how to debug it...

Can anyone help me out here?
If there is any log files, or anything you would like to see then tell me where the path to the file is :)


edit:
After a reboot an the computer, the remote controll browsing, is just as slow as hell aswell even on slimserver 6....

---

### Post by teeleef on 2008-03-26
I too am having trouble with Squeezecenter.    It has installed but cannot find it in my browser no matter whether I type [http://localhost:9000](http://localhost:9000) or [http://127.0.0.1:9000](http://127.0.0.1:9000).

Completely stumped.   Slimserver worked fine under Gusty but not with my Hardy Beta install.



Teeleef

---

### Post by icroak on 2008-03-26
Squeezecenter also stopped working for me after upgrading to hardy beta. In my system logs I get a mysql error.

...operation="inode_permission" request_mask="r::" denied_mask="r::" name="/var/lib/squeezecenter/cache/my.cnf" pid=9919 profile="/usr/sbin/mysqld" namespace="default"

Every few seconds I get the same message, only with a different pid. Anyone have a clue?

---

### Post by wieman01 on 2008-03-26
> **icroak said:**
> Squeezecenter also stopped working for me after upgrading to hardy beta. In my system logs I get a mysql error.

...operation="inode_permission" request_mask="r::" denied_mask="r::" name="/var/lib/squeezecenter/cache/my.cnf" pid=9919 profile="/usr/sbin/mysqld" namespace="default"

Every few seconds I get the same message, only with a different pid. Anyone have a clue?
For this I would file a bug report on Launchpad right away. Let developers know that there is a bug.

Slimserver works fine for me no Gutsy... Any system log files you could attach?

---

### Post by Fjatle on 2008-03-26
Solved!!

Ok, so a guy at work figured out my problem.
I had to  gedit /etc/defaul/slimserver

Here it says:
# This limits http access to the local host.
# Comment it out for network-wide access, or change 
# to enable a single interface.
HTTP_ADDR=127.0.0.1

I had to comment out Http... so it said:
# This limits http access to the local host.
# Comment it out for network-wide access, or change 
# to enable a single interface.
#HTTP_ADDR=127.0.0.1

Now, my squeezebox once again play my music :D


Ps.
I wont set the topic to 'Solved*, since there now are more questions here from others

---

### Post by Fjatle on 2008-03-26
Well, the fix was done with slimserver 6.3 installed (the one in the repos).

So I thougt 'Will squeezecenter 7.0 work now?' 
...And Yes it did!

I don't know why, but it does

---

### Post by teeleef on 2008-03-26
Well done Fjatle!!!!   It did work for me, one thing was a permissions problem too.

I removed squeezecenter and installed slimserver.  One question if I install squeezecenter where do I find that file not the "/etc/default/slimserver" but the one for the squeezcenter settings, with the similar settings that need 127.0.0.1 enabling?


Thanks again


Teeleef

---

### Post by Fjatle on 2008-03-26
I don't know... I tried looking it up, but didn't find... You have the /etc/default/squeezecenter, but that one is just about empty..


But I didn't have to make any changes after upgrading to 7.0, it just worked!

---

### Post by sudoreboot on 2008-04-02
I just found this thread. 
Squeezecenter from unstable sources list was working fine yesterday - connecting a remote XP softsqueeze using its built-in ssh port forwarding. Today it didn't work: I've got a blank screen on softsqueeze display after the ssh connection and web timeout in [http://127.0.0.1:9000/](http://127.0.0.1:9000/) of the same remote machine. I also tried ssh -L 9000:127.0.0.1:9000 without softsqueeze, same result for timeout.
Afterwards, I also tried downgrading my squeezecenter to "stable" but that caused softsqueeze version mismatch, so I now I try  "testing". Squeezecenter still doesn't work so I replace it with slimserver, and again sofsqueeze version doesn't match with server.
During my various experiments I also modified /etc/default/slimserver as described above. Now the web timeout problem is solved, but I can't activate a remote xp player yet.

---

### Post by Fjatle on 2008-04-02
I don't quite get you there..
Are you trying to access the server (from another computer)  by using 127.0.0.1:9000 ?? 
If that is the case, then of course you don't get any response.
You have to use the ip adress given by your router (or whatever), like 192.168.0.2:9000

You can find your ipadress by typiing ifconfig in the terminal.

Have you tried to restart the server (sudo /etc/init.d/squeezecenter restart) ?

---

### Post by sudoreboot on 2008-04-02
Actually I was trying to stream music from home over the internet.
I ssh to my router internet IP address using no-ip.com DNS, and port-forward port 9000 to the XP machine, either by softsqueeze or cygwin ssh. This works for sure, I don't even need to configure NAT for port 9000 on the router as long as port 22 is forwarded to the squeezecenter/slimserver PC.
On the remote PC, accessing 127.0.0.1:9000 will access the home PC port as long the ssh connection is alive (I think this is called tunneling). I'm now at home and 192.168.2.104:9000 (my slimserver PC) is dead for some reason, so I'll continue debugging remote access tomorrow, afer reinstalling squeezecenter instead of slimserver again (I'm confused as for what is a better choice with Gutsy).

---

### Post by sudoreboot on 2008-04-03
Remote streaming from gutsy+squeezecenter "testing" sources.list over the internet to xp machine using softsqueeze 2 is working fine now.
Turns out that the squeezecenter was not responsive because I had 0 space left on root folder, caused by 4.4Gb of mythtv (now uninsalld) /var/log files.

---

