---
title: "Sharing Wired Internet connection with wireless Vista"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by rhyguy on 2008-03-24
I have a desktop thats running ubuntu 7.10, and using a usb modem (ethernet function broke).
I also have an ethernet card, a wireless router (with ethernet ports) and a laptop running vista which i want to share an internet connection with.

how would i go about this?

Right now, i can acess the internet connection and ping my laptopand router at the same time
my laptop can ping router and desktop, but does not see thedesktop in the full network map (i think i need top layer link discovery or w/e to be seen)

where do i go from here?

---

### Post by chuckH on 2008-03-25
Here's my notes for my own use.
See if this helps.

If you are at the point of seeing and accessing window shares from Linux, but can't access 

Linux
folders from xp try this. Install SAMBA FIRST!
Found at Synaptic package manager. I checked & installed the samba packages and the 

smb and swat packages. Also check system-administration-services
be sure samba is running in server settings

1. You cannot be logged in to Ubuntu more than once. So the windows xp needs to log 

in with a different account than what is running on the ubuntu machine. 

2a. The second account needs to be both a ubuntu user (added in Users and Groups 

under administration) 

2b. The second account shouold be a basic user not with admin. permissions) Now create 

a samba user. From the terminal, type

sudo smbpasswd -a username
first try is your root password
2nd is the new pass for the samba account
to add a samba user. Adding a user to samba will fail
if you didn't add that same user in the O.S. as a user.

It will then ask for a password. Just make sure the password AND the username are the 

same for Ubuntu and Samba. Hopefully you should be able to log in then from the XP 

machine.

Double check, you have made the folder sharing
in Linux and check the permissions.
Also System-administration-shared folders-General Properties
there you can change the domain name.

This has worked for me and everything is networked and shared with proper permissions
in less then 10 minutes.

Good luck

---

