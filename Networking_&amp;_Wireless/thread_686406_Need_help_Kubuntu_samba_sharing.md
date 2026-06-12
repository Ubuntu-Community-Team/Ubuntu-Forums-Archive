---
title: "Need help: Kubuntu samba sharing"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by wahr on 2008-02-03
I followed all the steps through KDE to share a folder through samba on my network.
I chose allow all users, allow read and write.

It shows up on the network, but attempts to connect to it with my mac show "failure: this samba share does not allow guests" :confused:

I'm also unable to detect files shared on my mac through samba.

Any help would be appreciated.

---

### Post by wahr on 2008-02-03
This same error is confirmed with the gnome based ubuntu as well.

I can't see my mac's smb shares, and I get the "guest account not permitted" error trying to connect from my mac to ubuntu's smb shares.

---

### Post by Mantis86 on 2008-02-03
First try to connect like this... [http://www.ualberta.ca/CNS/SAMBA/mac.html](http://www.ualberta.ca/CNS/SAMBA/mac.html) 

if that still fails then lets take a look at your /etc/samba/smb.conf file

---

### Post by wahr on 2008-02-03
I'm afraid that guide is a little dated, though the procedure is pretty much the same. I've been using said dialogue to attempt connection by straight smb://<ip address here>, because the finder isn't registering it.

it also assumes user identification when I'm trying to configure it for anonymous access.

I'm getting the feeling the gui dialogues are not properly updating the config. I set the workgroup name to "Workgroup" to match the one used by my mac's samba sharing, but it still ends up in "MS home" when I browse my network.

Attempts to log in to the share from my mac as my linux admin account also fail.. apparently root has no right to access his own network shares? :lolflag:

---

### Post by swerdna on 2008-02-03
If you post the contents of smb.conf, there's a good chance it can be sorted  using what has been constructed there for the share. And if you want a guest-accessed share we take it from what's already there and modify that. perhaps.

Swerdna

---

### Post by wahr on 2008-02-04
Alright, here's the smb.conf file.  I appreciate your time on this.


```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = Workgroup

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC

```

---

### Post by swerdna on 2008-02-04
Hi. That shows a problem. The file is corrupted. It's heavily truncated.

Please you confirm that you copied all of it? If you've made a mistake in the copying, please re-post with the actual file. If you haven't made a mistake I'll post the original default file and you can copy that over your truncated copy.

Also describe what sort of share you want and I'll code one into the new file for you.

Also, just to be thorough,  check that you have the Samba program installed and running. You can do that with this shell command: **sudo /etc/init.d/samba restart**. If Samba is or isn't installed and running OK will be obvious from the reaction you get to that command.

Swerdna

---

### Post by wahr on 2008-02-04
that was definitely the whole file.. im glad it was something simple.

I wanted to share my ~/public folder so I could dump stuff between my machines.  

Will fixing this problem also make my mac's samba shares visible to this system?

I'd appreciate you keeping track of this a little longer after posting a replacement cfg file for me.

p.s.
I'd love to learn something more from this than the size and general layout of a non-corrupted config though. If you could run down in non-cryptic-ese what the important option flags are I may gain something more with which to help myself and others .

---

### Post by swerdna on 2008-02-04
> **wahr said:**
> that was definitely the whole file.. im glad it was something simple.
I'd appreciate you keeping track of this a little longer after posting a replacement cfg file for me
I've attached smb.conf.orig.txt a copy of Ubuntu default which you should store for reference in /etc/samba/

OK I've ediited that changing and adding lines as follows to make it suitable for a SOHO LAN:

workgroup = WORKGROUP
make the workgroup name the same on all computers in the LAN

server string = %h server (Samba, Ubuntu)
change to
server string = ""
This makes the string in Network Browsers manageably short. You can put there anything you like if you need more info displayed. Try it as is first.

;   name resolve order = lmhosts host wins bcast
change to
name resolve order = bcast host lmhosts wins
The Debian-suggested default is wrong for a home lan unless you create a list of computers on the lmhosts file, which newbies would never do.

FYI:   "dns proxy = no" is ineffective unless you're using a wins server, so it's also an irrelevant confusion. But it won't hiurt ATM. I comment it out so it doesn't come back to bite later.

   obey pam restrictions = yes
change to
#   obey pam restrictions = yes
Not necessary for home LAN

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
comment these out
#   passwd program = /usr/bin/passwd %u
 #  passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
The default over-complicates the home LAN

   socket options = TCP_NODELAY
chnage to 
socket options = IPTOS_LOWDELAY TCP_NODELAY
it's better see smb.conf on the internet

> Will fixing this problem also make my mac's samba shares visible to this system?I have never used a Mac, but it should, after all it's SMB/CIFS. If the Mac is broadcasting correctly you should see the shares.
> I wanted to share my ~/public folder so I could dump stuff between my machines.
Here's a share that makes /home/yourname/Public available to just you from other computers:
```
[UbuntuPublic]
path = /home/yourname/Public
writeable = yes
force user = yourname
```

You see "UbuntuPublic" in Network Browsers. You can change the text for it.
You often also see the line "browseable = yes". It's there by default so you don't have to write it.

Adfd "yourname" to the Samba use database with this shell command: **sudo smbpasswd -a yourname** Then you can authenticate from other computers.

If you want the share to be accessible and writeable to eveyone on the LAN then add this line: **guest ok = yes**
 and change the permissions on folder Public to drwxrwxrwx

Try that. It's in the attached file smb.conf.txt which you can copy to /etc/samba/ and rename to smb.conf. Remember change 'yourname' to your username.

Restart Samba with this: **sudo /etc/init.d/samba restart**.

It takes 5/10 mins for changes to seep around network. Don't know MACs - maybe reboot the computers sequentially starting with Ubuntu and finally ending with Ubuntu again. Makes them talk to each other. Have tea/coffee/beer while waiting.

Swerdna

EDIT: I mucked up the attachment smb.conf.txt which came up as a duplicate I think of the default - silly me - I'll post the correct on on a separate post because I can't work out how to upload it during this edit

---

### Post by swerdna on 2008-02-04
Here's the correct version of the edited file, called smb.conf.correct.txt

---

### Post by wahr on 2008-02-05
That new config helped a lot. Ubuntu can now see ans share files (and the gui for that works now).

EDIT: figured that last part out, guest ok = yes goes in the general settings under browsing.

Everything is up and running now! thanks a lot!

---

### Post by swerdna on 2008-02-05
> **wahr said:**
> That new config helped a lot. Ubuntu can now see ans share files (and the gui for that works now).

I'm still unable to log into my new share from my mac though.. It's still giving me the "guest not allowed" and "incorrect user/pass" errors respectively.
On the Ubuntu machine, what is the respomnse in a terminal to this command: **sudo pdbedit -Lw**. The response will look strange but don't worry, it's a diagnostec. Just copy/paste it into your reply

---

### Post by wahr on 2008-02-05
well, I figured out you had to enter security = share in authentication and guest access = yes in browsing on that config.. 

but now samba isnt properly restarting when the laptop wakes from suspend.

---

### Post by swerdna on 2008-02-05
> **wahr said:**
> well, I figured out you had to enter security = share in authentication and guest access = yes in browsing on that config.. 
Good for you. That would be the case for a failed Samba user database. Or if MACs simply can't network using authentication.
> but now samba isnt properly restarting when the laptop wakes from suspend
Sorry, can't help there

Swerdna

---

### Post by wahr on 2008-02-05
it appears the samba user database has failed then, since macs default to authentication first.

How do i fix that?

---

### Post by swerdna on 2008-02-05
> **wahr said:**
> it appears the samba user database has failed then, since macs default to authentication first.

How do i fix that?
I saw your pre-edit output of **sudo pdbedit -Lw** which was very puzzling, indicating a problem. But then it vanished, probably edited out. So let's have a look at this one: **sudo pdbedit -L**. For example this is what I get:
> sudo pdbedit -L
[sudo] password for suzette:
suzette:1000:suzette,,,
Which shows that I have successfully added one user to the samba user database. What do you get?

Swerdna

---

### Post by wahr on 2008-02-07
Sorry for the wait, here's the result

```
$ sudo pdbedit -L
games:5:games
nobody:65534:nobody
proxy:13:proxy
syslog:101:
www-data:33:www-data
root:0:root
news:9:news
bin:2:bin
mail:8:mail
hplip:104:HPLIP system user,,,
messagebus:103:
dhcp:100:
daemon:1:daemon
avahi-autoipd:105:Avahi autoip daemon,,,
man:6:man
lp:7:lp
gnats:41:Gnats Bug-Reporting System (admin)
backup:34:backup
haldaemon:107:Hardware abstraction layer,,,
sys:3:sys
klog:102:
avahi:106:Avahi mDNS daemon,,,
plasmacutter:1000:plasmacutter,,,
list:38:Mailing List Manager
irc:39:ircd
gdm:108:Gnome Display Manager
statd:109:
sync:4:sync
uucp:10:uucp

```

---

### Post by swerdna on 2008-02-07
That's got me beat. I don't know why it looks so corrupted, with everything added but the user you want. The line in smb.conf **passdb backend = tdbsam** is directing to use tdbsam. So let's change that to an alternate password manager and see what happens.

Open the smb.conf for editing with this command **sudo gedit /etc/samba/smb.conf**
Then change this line:
**passdb backend = tdbsam**
to this:
**passdb backend = smbpasswd**
While you're at it disable two lines by putting a hash mark at the front. They are  **[COLOR="Red"]#[/COLOR] security = share** and **[COLOR="Red"]#[/COLOR] guest access = yes**, just to see if the smbpasswd thing works - you can reverse that if it doesn't help.

Then restart smaba with **sudo /etc/init.d/samba restart**. 
Now when you execute this: **sudo pdbedit -L** you will hopefully get a blank response.
Then you can add your user with **sudo smbpasswd -a yourname**, once again substituting the correct name for "yourname".

Then maybe **sudo pdbedit -L** will be correct and if you reboot the network maybe it will work correctly.

Incidentally, I don't know why but lurking in my mind is to check that the line **netbios name = some_name_of_yr_choice** is in [global]. - Just a thought.

Swerdna

---

