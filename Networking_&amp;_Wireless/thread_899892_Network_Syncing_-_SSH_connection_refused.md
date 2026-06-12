---
title: "Network Syncing - SSH connection refused"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by tshearman on 2008-08-24
Hey everyone,

My goal is to sync 3 devices (1 USB key, 1 desktop, and 1 laptop); I'm using unison. I've written an autorun script for when the USB key is mounted.

This file is executed in a gnome-terminal by the autorun file (this is one part of an if statement, the rest follows but is basically the same):
```
	if [ $HOSTNAME = "mathchehome" ]; then
		echo "The 'Working Documents' directory will now be synced between the USB drive and $HOSTNAME"
		unison "usb_home";
		ping 192.168.1.101 -c 1
			success=$?
			if [ $success = 0 ]; then
#				ssh-agent startx;
				unison "home_mobile";
				unison "usb_mobile";
			else
				echo "No syncing will occur with mobile, mobile is not connected to the network."
			fi
```

The unison profile to connect to the mobile PC looks like this:

```
root = /home/toby/Desktop/Working Documents
root = ssh://toby@192.168.1.101//home/toby/Desktop/Working Documents
```

However, when I run the script I get the following error:
```
Contacting server...
ssh: connect to host 192.168.1.101 port 22: Connection refused
Fatal error: Lost connection with the server
```

And, it never asked me to login to the SSH.  Could this be the problem?  I know this may not be the best way to sync three devices, or if this will even work, but it's an experiment.

If anyone has tips on how to actually get this script to do what I want I would appreciate them... Perhaps we can bypass the SSH login or SSH all together somehow, or ensure that I log in at the beginning of the script...

Help!

Thanks so much everyone!

---

### Post by drjimmy42 on 2009-03-03
I know its been a long time but I thought I'd reply.  Connection Refused is a specific error meaning, there is a computer at that address, and it went out of its way to tell you that no one is listening on the port you requested, in this case port 22 which is the default port for ssh.  Things to check.

1) Was the server running?
2) did you have it configured to listen on a different port?

---

