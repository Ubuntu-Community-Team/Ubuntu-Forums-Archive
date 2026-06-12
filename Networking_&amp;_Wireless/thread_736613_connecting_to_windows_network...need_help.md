---
title: "connecting to windows network...need help"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by jeh311 on 2008-03-26
i have been using Ubuntu 7.10 for a short while now, the only thing that has really pestered me is getting on the network to other pcs' (windows XP based), i have samba installed too. I somewhat got it figured out, if i delete the dns servers off the network settings, it will network great with any machine but then i will have no internet connectivity. It drives you mad after a bit. does anybody know a possible solution to this. Thanks for your time.

---

### Post by DXM31 on 2008-03-26
I'm not sure if this is what you looking for but...
If you start looking on page 2 towards the bottom it will tell you how to hook up to XP network.
[http://ubuntuforums.org/showthread.php?t=721935&highlight=samba+answer&page=2](http://ubuntuforums.org/showthread.php?t=721935&highlight=samba+answer&page=2)

---

### Post by jeh311 on 2008-03-26
i tried that, it sometimes works for me, but there are so many pcs' in this house you get lost real easily.

---

### Post by DXM31 on 2008-03-26
True I was only hooking up to one PC.
But wouldn't all you PC's have a different IP addr?

---

### Post by jeh311 on 2008-03-26
yes all pcs' have a different ip here. i have the dhcp off on the router where it has to be manually configured on each one. My bro-in-law finds one network prob he goes around changing the ips' on some machines, even though it may fix his prob, its just more probs for me to straighten out later. and not to mention all the dns and ip probs win xp can give you sometimes.

---

### Post by chuckH on 2008-03-27
Hey jeh try this.

If you are at the point of seeing and accessing window shares from Linux, but can't access Linux
folders from xp try this. Install SAMBA FIRST!
Found at Synaptic package manager. I checked & installed the samba packages and the smb and swat packages. Also check system-administration-services
be sure samba is running in server settings

1. You cannot be logged in to Ubuntu more than once. So the windows xp needs to log in with a different account than what is running on the ubuntu machine. 

2a. The second account needs to be both a ubuntu user (added in Users and Groups under administration) 

2b. The second account should be a basic user not with admin. permissions) Now create a samba user. From the terminal, type

sudo smbpasswd -a username
first try is your root password
2nd is the new pass for the samba account
to add a samba user. Adding a user to samba will fail
if you didn't add that same user in the O.S. as a user.

It will then ask for a password. Just make sure the password AND the username are the same for Ubuntu and Samba. Hopefully you should be able to log in then from the XP machine.

Double check, you have made the folder sharing
in Linux and check the permissions.
Also System-administration-shared folders-General Properties
there you can change the domain name.

This has worked for me and everything is networked and shared with proper permissions
in less then 10 minutes.

A good hard reboot of the router wouldn't hurt either.

Good luck

---

### Post by Eiríkr on 2008-03-27
Hey there chuckH --

You've got some misunderstandings in here, I'm afraid:

> **chuckH said:**
> 1. You cannot be logged in to Ubuntu more than once. So the windows xp needs to log in with a different account than what is running on the ubuntu machine. 

This isn't correct.  The same username can be logged into one machine multiple times in multiple ways.  I have a Xubuntu server that I can log into directly, then ssh into from a different machine, and access a Samba share from a third machine, all at the same time and all using the same username.  


> **chuckH said:**
> 2a. The second account needs to be both a ubuntu user (added in Users and Groups under administration)

It's true that any username used to access Samba needs to also be an Ubuntu user, unless you're mapping usernames.  It's possible to set up a username mapping file that basically assigns remote usernames (that can be anything at all) to local usernames (that have to be actual Ubuntu users).  This can be controlled using the [FONT="Courier New"][username map]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#USERNAMEMAP")[/FONT] option in the [FONT="Courier New"][global][/FONT] section of the [FONT="Courier New"]/etc/samba/smb.conf[/FONT] file, as shown here:
```
username map = /usr/local/samba/lib/users.map
```
The option's value should be the path to a text file that defines the mappings.  The format is "local_username = remote_username", and the contents can be quite simple, like so:
```
ubuntu_user = winbob
ubuntu_user = macfred
ubuntu_admin = solarisboss
```

However, note that the local usernames ("ubuntu_user" and "ubuntu_admin" here) *must* be real Ubuntu usernames.


> **chuckH said:**
> 2b. The second account should be a basic user not with admin. permissions) Now create a samba user. From the terminal, type

sudo smbpasswd -a username
first try is your root password
2nd is the new pass for the samba account
to add a samba user. Adding a user to samba will fail
if you didn't add that same user in the O.S. as a user.

It will then ask for a password. Just make sure the password AND the username are the same for Ubuntu and Samba. Hopefully you should be able to log in then from the XP machine.

You're correct that any username added to the Samba password file *must* also be an Ubuntu username.  In cases of username mapping, we would add *not* the *remote* username to the Samba password file, but rather the *local* username we were mapping to.  So in our example above, we would add the usernames "ubuntu_user" and "ubuntu_admin", *not* "winbob" or "solarisboss".  

However, your Samba password and your Ubuntu password do *not* need to match.  It's easiest for folks to remember if they do, but there's no technical reason for them to be the same.  Some folks recommend using different passwords for improved security.  


> **chuckH said:**
> Double check, you have made the folder sharing
in Linux and check the permissions.
Also System-administration-shared folders-General Properties
there you can change the domain name.

It's good that you point out filesystem permissions, as these are another point of common confusion that I see on the Forum here.  Whatever Ubuntu username ("ubuntu_user" or "ubuntu_admin" in our example) that is being used for Samba access needs to have permissions on the shared directories.  This is set up *outside* of any Samba configuration, and often involves groups and the use of the [FONT="Courier New"]chmod[/FONT] and [FONT="Courier New"]chown[/FONT] commands.  Have a look at [post=4496702]this post[/post] for some instructions on setting up permissions for either a single-user or multi-user Samba share.  

Note that "domain name" in Samba terms is the same thing as the "workgroup name" in Windows terms.  Make sure your Samba domain name and your Windows workgroup name match, or the two machines will have trouble seeing each other.  


If you make any changes to your Samba configuration, it's always a good idea to restart your Samba server to make sure it uses your new settings:
```
sudo /etc/init.d/samba restart
```

Hope this helps, 

Eiríkr

---

