---
title: "HOWTO: Build a public terminal lab using Ubuntu 12.04 and LTSP"
date: 2013-10-01
forum: Networking &amp; Wireless
---

### Post by Emblem Parade on 2013-10-01
***Note: This guide also applies to Ubuntu 14.04***

Do you manage a public computer lab? Maintaining a single terminal server is so much easier and cheaper than maintaining individual workstations.

Unfortunately, [LTSP]("http://www.ltsp.org/") (the Linux Terminal Server Project) does not support this scenario out of the box. While it supports guest logins, it leaves the work of maintaining these guest accounts up to you. This guide will help you fill in that gap. In particular, it will show you how to make sure that when public users login they get a fresh, clean desktop according to your specifications.

In this guide we're going to assume that you're using the Xfce desktop (via Xubuntu), but the guide should work for any other desktop supported by LTSP.

You may want to start with the [guide I wrote for installing LTSP]("http://ubuntuforums.org/showthread.php?t=2173749"). Make sure your clients can boot and login with regular (non-guest) users before proceeding!

**USERS**

Let's set up our guest user accounts. First, it's important to understand that these are *not* the "login as guest" feature implemented by Ubuntu/LightDM. The mechanism used there cannot work with LTSP, because LTSP uses its own greeter. However, in this guide we will simulate that feature.

We need one user named "template", which we will use to configure our guests, and then unique users for each single terminal. It's a good idea to use a numbering scheme for your terminals. For this guide, we've decided on "lab-" as the prefix:
```
sudo adduser template
sudo adduser lab01
sudo adduser lab02
sudo adduser lab03
...

```
Create as many users as you have terminals, and perhaps add a few more if you're anticipating growth. It's up to you if you want to use the same password for all "lab-" users or not.

Now, let's create a "lab" group and add all the users to it:
```
sudo addgroup lab
sudo usermod -a -G lab lab01
sudo usermod -a -G lab lab02
sudo usermod -a -G lab lab03
...
```

**GUEST SESSION SCRIPT**

Create a script in a file called "ltsp-session.sh", which you should put in a common location. In our example, "/opt/ltsp/ltsp-session.sh":
```
#!/bin/bash

if groups | grep &>/dev/null '\blab\b'; then
	# For users in the 'lab' group, copy from 'template' user
	shopt -s dotglob
	find /home/$USER/* ! -path /home/$USER/.Xauthority -exec rm -rf {} \;
	rsync --archive --exclude .Xauthority /home/template/* /home/$USER/
	shopt -u dotglob
	chmod -R go-wrx /home/$USER
fi

/usr/bin/xfce4-session

if [ $USER == template ]; then
	# Make 'template' user copyable
	shopt -s dotglob
	chmod -R a+r /home/template/*
	find /home/template/* -type d -exec chmod a+x {} \;
	shopt -u dotglob
fi

```
This script runs the usual Xfce session, but adds two things:

[LIST=1]
[*]For lab users, *before* the session starts, it makes sure to delete the home directory and copy it over from the "template" user. Note that we are taking care not to override the .Xauthority file, which is created by X11 per session.
[*]For the "template" user, we are making sure that *after* logging out it home directory is readable. This allows the directory to be copied, as we do above.
[/LIST]
Note that this script is run as the user logging in, *not* as root.

**GUEST LOGINS**

We'll now configure the LTSP greeter to support a "Login as Guest" feature for each terminal. Edit /var/lib/tftpboot/ltsp/i386/lts.conf (it's OK to create this file if it doesn't exist):
```
[Default]
LDM_XSESSION = /opt/ltsp/ltsp-session.sh

[00:5d:09:22:10:1e]
LDM_GUESTLOGIN = True
LDM_USERNAME = lab01
LDM_PASSWORD = mypassword

[00:5d:09:25:d0:a6]
LDM_GUESTLOGIN = True
LDM_USERNAME = lab02
LDM_PASSWORD = mypassword

[00:5d:09:2c:3e:e9]
LDM_GUESTLOGIN = True
LDM_USERNAME = lab03
LDM_PASSWORD = mypassword

...

```
Things you will have to change:

[LIST=1]
[*]Change LDM_XSESSION to point to a place where you put your "ltsp-session.sh" file.
[*]You must use the Ethernet MAC addresses for all your terminals. This associates each terminal with a specific "lab-" guest user. You can see the client's MAC address during its network boot. **Note that you can use IP addresses instead of MAC addresses if you prefer.** However, this would require you to configure your DHCP server to provide static IP addresses for each terminal, which would in turn still require you to know the MAC addresses. Might as well work directly with MAC!
[*]Set the appropriate passwords for each "lab-" user.
[/LIST]

You will need to rebuild the client OS image:
```
sudo ltsp-update-image --arch=i386
```

If you followed my [installation guide]("http://ubuntuforums.org/showthread.php?t=2173749"), you know that you also need to fix the proxy DHCP issue:
```
(cat <<EOF
ipappend 3
EOF
) | sudo tee -a /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default
```

**CONFIGURE THE TEMPLATE**

Login as user "template" and configure your desktop and applications as you wish. Logout when done.

In the future you can login as "template" again and change the configuration.

**THAT'S IT!**

When you next boot your clients they will display a "Login as Guest" button that will provide them with a fresh desktop based on "template".

**AUTOLOGIN?**

It's also possible to skip the greeter and have clients login straight to their guest user. **However, if you do this note that when users log out they will return right back to a new fresh desktop.** This may confuse users into thinking they have not really logged out, and so may not be the best idea. Still, if you want this it's easy to configure by using LDM_AUTOLOGIN instead of LDM_GUESTLOGIN in your ltsp.conf:
```
[00:5d:09:22:10:1e]
LDM_AUTOLOGIN = True
LDM_USERNAME = lab01
LDM_PASSWORD = mypassword

...

```

---

### Post by Brian_Carson on 2014-05-30
Emblem,

I read this post this morning and couldn't believe how easy it actually was to set everything up! I am a 75 station call center and trying to keep each one clean of viruses, malware, inappropriate desktop images, and other "unwanted" stuff is too much for my one man shop. We started up a LTSP machine a few weeks ago, and everyone used the same user, but that had issues when running firefox because the profile was locked by the first person. Your setup is the perfect solution, but I am stuck and need help, if you don't mind.

I have 2 sticking points...
> 
1) I made the template user, "booths", and configured the profile how I want all the others to look. I can log in and out as "booths" fine. When I try to log in as the specific account for that PC, it says "no response from server, rebooting". I have tried specifying the username & password, just clicking "Login as Guest", putting in the username and clicking "log in as guest". None of them seem to work. I followed your steps line for line. I have tried it both with ldm_autologin and ldm_guestlogin, but again, neither works. ldm_Autologin just gets stuck in a constant reboot loop... - Fixed... The users were all created with "No Logon Allowed" according to webmin... after changing it to a normal password, the test terminal logged right in!

2) Secondly, when I do login as the "booths" template account, I cannot browse network folders. I tried both of the preinstalled file browsers, Thudar just doesn't have an option for Network and Nuatalis says the Network Manager is not running. But I can get on the internet and ssh to other machines just fine... I need network access as we run projects where they need centralized resources.

Thanks for helping!

~Brian

---

### Post by Emblem Parade on 2014-05-30
Brian, do a quick test for issue #2: login with those users on the terminal server machine itself (*not* remotely) and see if you have the same problem accessing network drives.

My guess is that this problem has nothing to do with terminal access and probably something to do with Samba settings on the server.

---

### Post by felix10 on 2014-07-03
Hi,

does this configure work for Ubuntu 14.04 LTS as well?  I've tried on 14.04 i386 but it didn't work for me.  Without the lts.conf then I'll get to the prompt where I can enter username and password, but with the lts.conf with mac address, username and password, I would end up in PXE-E32: tftp open timeout or error socket failed connection refused existing.  


What did I done wrong here! Any thoughts?

---

### Post by Emblem Parade on 2014-07-03
Yes, it works on 14.04. Make sure you follow my [previous guide]("http://ubuntuforums.org/showthread.php?t=2173749") and that everything works before advancing to this one.

---

### Post by felix10 on 2014-07-03
hmm.. I wonder what I did wrong??

---

### Post by felix10 on 2014-07-03
Hi, one more thing that I'm stuck on.  I wonder if you can point me out.  I think the option logon automatically is working since I edit the lts.conf to:
[mac]
LDM_GUESTLOGIN = True
LDM_USERNAME = lab01
LDM_PASSWORD = password

I'll get to the prompt for username for the above setting, but when I change LDM_GUESTLOGIN to LDM_AUTOLOGIN I get a black screen with blinking cursor on the screen.  I'm sorry, but what's there I need to fix.  Thanks in advance!

---

