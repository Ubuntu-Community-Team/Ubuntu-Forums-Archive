---
title: "Printer Doesn't Appear on Samba Network"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by flowingfire on 2007-05-11
Hi everybody.  I just recently got Samba working-- something I'm quite proud of accomplishing as an Ubuntu n00b.  I have a new problem though.  My printer is not showing up on the network.  

I got files to share successfully over Samba, but I have had less success with the printer.  

In the KDE "Printers" manager, I have "share printers" checked under "global settings."  I also have Webmin installed, and it appears that I have my printer shared in both the Linux file-sharing system and in Samba.  

I have re-booted many times, re-started samba, un-shared and re-shared the printer... Deleted and re-instated settings... But still my printer doesn't appear anywhere on the network.  Now, it's notable that when I enter my Ubuntu computer's share folder from a Windows computer, it displays a "printers and faxes" folder-- only it's empty.  Grr.

Okay, please help.  How do I get my printer to show up on the network?  How can print from another computer if it doesn't show up?  

LOL- if I can just get this working once, I'll never have to think about it again... hopefully-- lol.

Thanks for the help.
-David

Here is the config file:
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
log file = /var/log/samba/log.%m
restrict anonymous = no
ldap ssl = No
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
obey pam restrictions = yes
guest ok = yes
domain master = no
map to guest = Bad User
passdb backend = tdbsam
passwd program = /usr/bin/passwd %u
wins support = true
dns proxy = no
netbios name = PorchComputer
server string = %h server (Samba, Ubuntu)
max protocol = NT
invalid users = root
workgroup = Porch
acl compatibility = winnt
server signing = Auto
syslog = 0
preferred master = no
panic action = /usr/share/samba/panic-action %d
max log size = 1000

[Vista Shares]
path = /media/sda1/Users/Public/

[printers]
printable = yes

[MY DOCUMENTS]
path = /home/david/My Documents/

[PRINTERS]
path = /var/lib/samba/printers/

[SAMBA]
path = /var/spool/samba/

[SDA1]
path = /media/sda1/

[HP PSC 1600 Linux]
	printer = HP_PSC-1600
	printable = yes

---

### Post by flowingfire on 2007-05-12
Oh yes-- and the Printer is an HP PSC 1610v if that makes a difference.  :) Thanks for the help in advance if anyone knows what to do to get a printer working!

---

