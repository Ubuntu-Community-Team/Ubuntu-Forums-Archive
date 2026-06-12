---
title: "Darkstat problems"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by SpyderCS on 2006-08-10
Hello folks,
I am having some issues using darkstat. I have used the intructions from [debianhelp]("http://www.debianhelp.co.uk/darkstat.htm")however when I start the process (/etc/init.d/darkstat start) then type darkstat I get?

darkstat v2.6 using libpcap v2.4 (i386-pc-linux-gnu)
Error: pcap_lookupdev(): no suitable device found

I am unsure of how to proceed. I take it that pcap is a different process that darkstat is trying to gather some information from?

any help will be appreciated.

---

### Post by SpyderCS on 2006-08-11
I installed libpcap-dev with the apt-get install and then rebooted, this seems to have worked somewhat. Now I am getting

Fatal error: WWW: Problem binding socket to port <1024. Are you not root?

Dying now...

I am root though, I used "sudo su" to get root so this shouldn't be an issue.

---

### Post by SpyderCS on 2006-08-11
The service seems to be working even with the error message, however I am unsure of whether it is indeed tracking all of the traffic. I would expect more ip's over the course of the night.

---

### Post by SpyderCS on 2006-08-14
Interesingly enough, after another reboot I started getting the first error again. Unfortunately no one seems to know enough to help with this app. Can anyone suggest a good app for watching and logging network traffic? I am interested in intrusion attempts as well, perhaps something that would be able to work with my router.

---

### Post by MrGrey1 on 2007-04-16
Same issue with darkstat;

Error: pcap_lookupdev(): no suitable device found

I have also noted that when I try to stop darkstat;

Stopping darkstat network daemon: darkstatstart-stop-daemon: warning: failed to kill 4297: Operation not permitted is not running.

even though;

sudo /etc/init.d/darkstat start
Starting darkstat network daemon: darkstat is already running.

Has anyone found any other good network monitoring tools, specifically one for monitoring intrusion attempts?

---

### Post by MrGrey1 on 2007-04-16
Got it working. It needs to be started and stopped as sudo as well as run as sudo. 
sudo darkstat
darkstat v2.6 using libpcap v2.4 (i486-pc-linux-gnu)
Firing up threads...
Sniffing on device eth0, local IP is 192.168.1.3
GRAPH: Starting at 14 secs, 40 mins, 15 hrs, 16 days.
Loaded darkstat.db.
DNS: Thread is awake.
WWW: Thread is awake and awaiting connections.
WWW: You are using the English language version.
ACCT: Capturing traffic...
Point your browser at [http://localhost:666/](http://localhost:666/) to see the stats.

My only issue now is that I have set the port as 8888 yet it's still visible on 666... hmmm.

I would still like to know if anyone has found any other good monitoring tools...?

---

### Post by rafalr on 2007-08-14
Hi,

I used darkstat with Dapper with no problem, managed to have it launched automatically at each new X session by inserting a command "sudo darkstat -i eth0 -l 192.168.2.100/255.255.255.0 -d /home/rafal/.darkstat" in the list of demons to be started with each session.

I however can not achieve this in Feisty: the same command is apparently not being accepted/executed on session startup, as I always need to manually open terminal and start darkstat by the above command, then it can be visible in web browser at 666 ...

How to have darkstat initiated automatically at each boot/session ?

Rafal

---

### Post by Hewus on 2008-03-31
/etc/darkstat/init.cfg is what you're looking for. Just set START_DARKSTAT=yes and it will take care of the rest :-)

---

