---
title: "Samba on 14.04 ... passwords refused?"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by Tom Collier on 2014-09-07
Upgraded 2 laptops from 12.04 to 14.04. Both are clean, unmodified default installations. No Windows machines on the network at all. Just 2 Ubuntu 14.04 installations.

Never used Samba before, so did plain unadorned vanilla "sudo apt-get..." installation, including config GUI. Set up config according to [this online guide]("http://www.maketecheasier.com/install-and-configure-samba-in-ubuntu-for-file-sharing/"). Shares are recognized, show on the screen, and appear to be available. However, password to sign into share is not recognized. The password dialog box just comes up over and over again.

I have no idea of next steps to troubleshoot this. Any help is appreciated very much.

---

### Post by weatherman2 on 2014-09-07
On the server (the one that is sharing files), enter a terminal and run smbpasswd to add a Samba user.  If your Ubuntu login name on that machine (the one sharing the files) is "tom" then open a terminal on that machine and type

```
sudo smbpasswd -a tom
```

(replace "tom" with the real login name)

Type your sudo password first if needed, then enter the Samba password - probably the same as your login password.

---

### Post by Tom Collier on 2014-09-07
Thanks for responding.

On installation, I originally set username and password with the GUI, "system-config-samba".  Did what you suggested in terminal. It asked for "new password" / "Confirm new password".  Still just presents the password dialog box over and over again.

Here's results from "testparm"

> tom@tom-Satellite-P105:/etc/samba$ sudo testparm
[sudo] password for tom: 
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
WARNING: [printers] service MUST be printable!
WARNING: No path in service printers - making it unavailable!
NOTE: Service printers is flagged unavailable.
Processing section "[home]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
	workgroup = HOA
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb


[printers]
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No
	available = No


[home]
	comment = HOA Computer
	path = /home
	valid users = tom
	read only = No
	browseable = No
tom@tom-Satellite-P105:/etc/samba$ 


---

### Post by weatherman2 on 2014-09-07
I'm not sure what you are trying to accomplish here.  What are you trying to share, with whom?  Just a simple share on your local network, with one user?

I used to configure Samba manually, but now I simply go into the Nautilus browser, right-click on a folder and choose "Local Network Share" and choose the options there (as described - albeit for 12.04 - in the "online guide" link you gave under the paragraph that starts with "On your Nautilus File Manager, you can also right-click on any folder").  I did that earlier today before responding to your post on a 14.04 sever and all I needed to do was the smbpasswd command and it worked fine, to share a folder with password.  I didn't need to install Samba or do anything else, except the smbpasswd command.  Very easy and simple for simple folder sharing.

The main reason you would setup Samba manually would be to add more options, for more users, etc.  If you simply google "Samba file sharing" you're more likely to run into lots of these more complicated how-to guides than the average person really needs.

---

### Post by Tom Collier on 2014-09-08
Computer #1 is my general use computer. Computer #2 contains files and data specific to a customer who requires me to maintain separately from all other data, on a separate, dedicated machine.

Occasionally, information, documents as email attachments, scanned documents, etc., come in while I am seated at Computer #1. I would like to transfer those files to Computer #2 using my network.  Right now, I carry out that transfer by loading files from #1 onto a thumb drive, walking across the room to #2, inserting the thumb drive into #2's USB port and moving the files to the appropriate location on Computer #2. 

Oh well, I need the exercise so I guess I'll continue manually transferring files. Thank you for your attempts to assist.

---

### Post by weatherman2 on 2014-09-08
Did you not try to do it the way I suggested?  Just right-click on the folder and try to share it, instead of using all of that Samba setup?

If you're on a secure network, you can do away with password requirement altogether by allowing guest access (then username = guest, no password).

---

### Post by Tom Collier on 2014-09-08
I did as you suggested; created myself as a user + password; then right-clicked on the folder icon, ticked the "Share this Folder", box and got a dialog box that requires the installation of Samba.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=256247&stc=1&thumb=1&d=1410157190[/IMG]

---

### Post by weatherman2 on 2014-09-08
OK - so click on the "Install Service" button and go from there, then try again.

---

### Post by Tom Collier on 2014-09-08
It loads Samba, but right-clicking a file presents a dialog box which says file sharing isn't available because necessary packages are not installed. Trying to connect with computer #2, from computer number #1 presents the password dialog box over and over again.

I'll just stay with my tried and true method of using a USB thumb drive to physically transfer files. Got along without Samba before upgrading from 12.04 to 14.04. Will get along without it now.

Clearly, Samba is broken in 14.04.  Maybe they can fix it before 2019.

Again, thanks for your assistance and interest in helping.

---

### Post by weatherman2 on 2014-09-08
So after you clicked the "install Service" button in your graphic, exactly what happens after that?  Did the packages install correctly?  If not, was there any other message?

If you are having trouble installing packages, drop into a terminal and type:

```
sudo apt-get update
```

Did you try rebooting and then going back to the folder and right-clicking "Local Network Share" again?

As I noted above, i set it up sharing quickly on my 14.04 box, right before my first response in this thread.  So clearly it works.

I suspect that all of the other stuff you did for Samba using that 12.04 guide (which I didn't do) did something to mess up sharing for you in 14.04.   It's probably not going to fix itself just with an update.

---

