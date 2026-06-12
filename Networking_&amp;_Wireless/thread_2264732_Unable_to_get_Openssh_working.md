---
title: "Unable to get Openssh working"
date: 2015-02-09
forum: Networking &amp; Wireless
---

### Post by zachary16 on 2015-02-09
I recently purchased a basic vps service to start hosting a teamspeak and a basic website for my gaming organization but I'm running into some problems with what is probably the most basic step in getting started: the SSH server.


When I first purchased the service it came with ubuntu 11.04 installed which is VERY old and no longer supported, but it worked and I could connect and manage it with Putty and I had the teamspeak and everything working but was running into some problems with apt-get and a buddy of mine told me to reinstall it with ubuntu 14 instead as it's an LTS release.


I did that, but now I'm having issue getting SSH to work at all. I can only access the VPS via the serial console at the moment and any attempts to start the ssh service fail and don't give me anything to go on as to why. The only feedback the server gives me is "start: Job failed to start" when I attempt to start the service which is unhelpful at best.


Where do I even start troubleshooting this? I removed and reinstalled both Openssh client and server to no avail. 


When I reinstalled the openssh server it did return an error but through some googling I haven't found any solutions. Here's the install log:


```



root@:/# sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  openssh-sftp-server python-chardet python-requests python-six python-urllib3
  ssh-import-id
Suggested packages:
  ssh-askpass rssh molly-guard ufw monkeysphere
The following NEW packages will be installed:
  openssh-server openssh-sftp-server python-chardet python-requests python-six
  python-urllib3 ssh-import-id
0 upgraded, 7 newly installed, 0 to remove and 62 not upgraded.
Need to get 560 kB of archives.
After this operation, 2218 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main openssh-sftp-server amd64 1:6.6p1-2ubuntu2 [34.1 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main openssh-server amd64 1:6.6p1-2ubuntu2 [319 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty/main python-chardet all 2.0.1-2build2 [106 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ trusty/main python-six all 1.5.2-1 [8060 B]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python-urllib3 all 1.7.1-1ubuntu0.1 [39.3 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python-requests all 2.2.1-1ubuntu0.1 [42.9 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty/main ssh-import-id all 3.21-0ubuntu1 [9624 B]
Fetched 560 kB in 0s (638 kB/s)
Preconfiguring packages ...
Selecting previously unselected package openssh-sftp-server.
(Reading database ... 26034 files and directories currently installed.)
Preparing to unpack .../openssh-sftp-server_1%3a6.6p1-2ubuntu2_amd64.deb ...
Unpacking openssh-sftp-server (1:6.6p1-2ubuntu2) ...
Selecting previously unselected package openssh-server.
Preparing to unpack .../openssh-server_1%3a6.6p1-2ubuntu2_amd64.deb ...
Unpacking openssh-server (1:6.6p1-2ubuntu2) ...
Selecting previously unselected package python-chardet.
Preparing to unpack .../python-chardet_2.0.1-2build2_all.deb ...
Unpacking python-chardet (2.0.1-2build2) ...
Selecting previously unselected package python-six.
Preparing to unpack .../python-six_1.5.2-1_all.deb ...
Unpacking python-six (1.5.2-1) ...
Selecting previously unselected package python-urllib3.
Preparing to unpack .../python-urllib3_1.7.1-1ubuntu0.1_all.deb ...
Unpacking python-urllib3 (1.7.1-1ubuntu0.1) ...
Selecting previously unselected package python-requests.
Preparing to unpack .../python-requests_2.2.1-1ubuntu0.1_all.deb ...
Unpacking python-requests (2.2.1-1ubuntu0.1) ...
Selecting previously unselected package ssh-import-id.
Preparing to unpack .../ssh-import-id_3.21-0ubuntu1_all.deb ...
Unpacking ssh-import-id (3.21-0ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up openssh-sftp-server (1:6.6p1-2ubuntu2) ...
Setting up openssh-server (1:6.6p1-2ubuntu2) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
Creating SSH2 ECDSA key; this may take some time ...
Creating SSH2 ED25519 key; this may take some time ...
runlevel:/var/run/utmp: No such file or directory
start: Job failed to start
invoke-rc.d: initscript ssh, action "start" failed.
dpkg: error processing package openssh-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-chardet (2.0.1-2build2) ...
Setting up python-six (1.5.2-1) ...
Setting up python-urllib3 (1.7.1-1ubuntu0.1) ...
Setting up python-requests (2.2.1-1ubuntu0.1) ...
Setting up ssh-import-id (3.21-0ubuntu1) ...
Errors were encountered while processing:
 openssh-server
E: Sub-process /usr/bin/dpkg returned an error code (1)



```


I'm pretty new to linux so forgive me if this post seems daft but I've been trying to figure this out for two days now and I'm just stuck. There's probably something super simple that I'm missing.


Thanks

---

### Post by TheFu on 2015-02-09
Exactly which version of the OS are you currently running?

BTW, you can turn up the logging - just add -vvvv to the command startup.  Might be helpful to not daemonize it too when troubleshooting.

Never run a release that isn't supported. Package repos will disappear over time. That ended 3 years ago for 11.04.

Right now, there are only 3 releases for consideration - 12.04, 14.04, 14.10. Everything else is not supported - that isn't exactly true - but 10.04 server support ends in 2 months, so nobody should deploy that now.

---

### Post by CrAzY12 on 2015-02-13
[FONT=times new roman]I am actually having the same problem with Ubuntu Server  14.04.1.  l used:

#*apt-get install ssh *  
#*ssh -v localhost* ; to make sure if I can connect(connection refused)
#ps ; to see if ssh is running no go
*#ufw disable *; to disable firewall for now
#*restart ssh*; unknown job
#/etc/init.d/ssh restart; no errors were found
#ssh -v localhost: connection refused
[/FONT][FONT=times new roman]Do I have to change the config file? Also I disabled my firewall I think? So it wont cause me problems while I troubleshoot but any help will be great!  [/FONT]

---

### Post by TheFu on 2015-02-13
CrAzY12 - The "server" package is named openssh-server, I think. It includes the client and since I always want the server on every machine I have, I don't know the name of the client ssh package. I dont think your issue is the same.

BTW, unless you have EXACTLY the same issue, thread high-jacking is bad. Creating a new thread is recommended.

---

### Post by Lars Noodén on 2015-02-13
zachary16, something is wrong with the VPS set up.  When the VPS was created and boot up, it should have created the directory /var/run/utmp but it didn't.  Does the directory /var/run also not exist?

```

runlevel:/var/run/utmp: No such file or directory
start: Job failed to start
invoke-rc.d: initscript ssh, action "start" failed.
dpkg: error processing package openssh-server (--configure):
 subprocess installed post-installation script returned error exit status 1

```

I think this is a matter for your hosting provider to solve since they created the VPS and the image from which it was spun up.

---

