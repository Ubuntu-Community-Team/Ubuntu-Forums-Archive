---
title: "Windows Domain Controller replacement."
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by thecha on 2008-01-16
Hello I am a computer teacher at a small elementary school in italy.  We don't have a full time network admin so I have been taking care of the network/computer problems for the past year. 

We currently have a Win2003 SBS which seems to be limited to 20 CALs...  Which seems to mean that only 20 people can be properly authenticated on our network at one time.  I looked into purchasing more CALs and they are more than the schools budget can afford.  So my proposed solution to the school is to try to migrate to using a Linux server. 

I would like to put together a linux box that can completely replace the Win2003 SBS.  My requirements are fairly minimal.  We currently have ~300 users.  

1. When they log in it maps their windows ***my document ***folder to a folder on the server.

2.  It also maps a shared network drive that students and teachers use for colaberative work. This drive is different depending on if the user is a teacher or a student.

Thats it...  The PC's in the lab all run Windows and we also have 4 intel imacs running 10.5.  I would love it if I could authenticate with the macs too however as it's currently not happening I would be fine without it.

I tried looking for a Virtual Application that was pre-setup to do this for me using vmware player, but I havn't found one.  So I guess I'm going to have to set it up myself.

I don't know much about linux or ubuntu.  I have installed the desktop version on several of our older PC's with only small problems (No sound).  But that is my only experience.  I don't really have any experience running a Win2003 SBS either so I'm just as happy to move to something where the school doesn't have to pay the Microsoft Tax and we can spend our money on something more fun like lego mindstorm..

Thanks for any help/advice you can offer.
-Matt

---

### Post by jeffus_il on 2008-01-16
Use Samba as a domain controller, Here is a guide, there are many more on the net.
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)

---

### Post by thecha on 2008-01-16
I was hoping there might be a more newbie friendly guide... 

I need hand holding as I know nothing about this... I don't no much about windows server either however the GUI's make it easy to figure out... I'm not a network administrator just a computer an elementary school teacher...

-Matt

---

### Post by jeffus_il on 2008-01-16
Try this one:
[http://daniel.fiser.cz/?samba](http://daniel.fiser.cz/?samba)
If you have problems, post.

---

### Post by thecha on 2008-01-16
@jeffus_il  I installed ubuntu 7.10 desktop on a virtual machine to test things out before I try the real thing...  I'm following the second guide you posted... 

It seems that samba is already installed I looked in the Synaptic Package Manager and it seems as thought samba-common is installed... There are several other samba choices listed including samba(not common) should I install this instead?  Should I first uninstall samba-common?

---

### Post by veloce on 2008-01-16
It might be heresy on the Ubuntu list, but I would look around for a specialised distribution for this application.  For example, I use IPCop for my firewall and would recommend this approach to anyone.

You might check out the LormaLinux site

[http://linux.lorma.edu/main/](http://linux.lorma.edu/main/)

Their Samba Server is still developmental but may be just the thing for you.

---

### Post by jeffus_il on 2008-01-17
You have a few choices,[LIST]
[*]Find a good tutorial on the internet, and post your problems, I'm sure you will solve them.
[*]Use a graphical user interface to set up Samba, try  gsambad[/LIST]Samba is a good program and you can achieve what you want to with it.
The samba setup could be easier.
The virtual machine may be introducing problems, it can complicate networking.
You could maybe experiment on a LiveCd without an install or do a temporary install on a small partition.

Here is a friendly ubuntu explanation:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

and try this:
[https://wiki.ubuntu.com/JoinWindowsDomain](https://wiki.ubuntu.com/JoinWindowsDomain)

---

### Post by thecha on 2008-01-17
Thanks for the info **veloce's** and **jeffus_il's** I will try both avenues.  Do you know does Lorma take care of authentication of the users as well? Or does it just create a public share?  Ideally I need something that can **replace **the windows domain controller...

---

### Post by jeffus_il on 2008-01-17
Samba can replace Windows domain controller.
I assumed that the first step would be to get Samba up and running, maybe do a little test share and then add the domain controller setting to the setup, so that if something went wrong it would be easier to identify the problem.
It would also be good to become acquainted with samba, the daemons, startup and shutdown, the logging system and setup files, if you want to depend on it in your environment. Not a big deal, but worth while knowing.

Here is an example of the domain controller setup. You may try it also through the gui "GSambad"

>  That was all about joining an NT domain. Setting up Samba as your Primary Domain Controller is not very difficult. 
 **Samba as Primary Domain Controller** 
 Add the following to the global section of your smb.conf file. 
 
# The domain you want to be a PDC for
workgroup = SIMPLE

# Tell Samba to use domain logons
domain logons = yes

# User-level security. Users must 
# authenticate themselves with
# valid username and password
security = user

# Set to yes so that nmbd participates 
# in local master browser
# elections
local master = yes 

# Set Os level value to make sure nmbd 
# wins local browse master 
# elections. 65 should beat everyone 
# according to the man page
os level = 65

# Give nmbd an advantage in local 
# master browser elections
preferred master = yes

# Set so that nmbd claims a unique 
# NetBIOS name identifying it as 
# a domain master
domain master = yes

# The following share is required to support
# domain logons. The directory may be 
# created anywhere on your system. Make 
# sure the share is non-writeable and also
# not a public share.
[netlogon]
comment = The domain logon service
path = /usr/local/samba/netlogon
public = no
writeable = no
 The next thing to do is create the users on the Samba server that is to act as the domain controller. You can do this using the useradd command. 
 useradd &#8211;-g smbuser &#8211;-d /dev/null &#8211;-s /dev/null ntuser 


---

### Post by thecha on 2008-01-17
I installed **gsambad** and I copied your example conf file into the configuration window.

> [global]
# The domain you want to be a PDC for
workgroup = BES

# Tell Samba to use domain logons
domain logons = yes

# User-level security. Users must
# authenticate themselves with
# valid username and password
security = user

# Set to yes so that nmbd participates
# in local master browser
# elections
local master = yes

# Set Os level value to make sure nmbd
# wins local browse master
# elections. 65 should beat everyone
# according to the man page
os level = 65

# Give nmbd an advantage in local
# master browser elections
preferred master = yes

# Set so that nmbd claims a unique
# NetBIOS name identifying it as
# a domain master
domain master = yes

# The following share is required to support
# domain logons. The directory may be
# created anywhere on your system. Make
# sure the share is non-writeable and also
# not a public share.
[netlogon]
comment = The domain logon service
path = /usr/local/samba/netlogon
public = no
writeable = no
The next thing to do is create the users on the Samba server that is to act as the domain controller. You can do this using the useradd command.
useradd &#8211;-g smbuser &#8211;-d /dev/null &#8211;-s /dev/null ntuser

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no



[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gsambadpdf %s %u
lpq command =
lprm command =


I think there is some extra stuff in there from gsambad...   Anyway I added an administrator account and activated it.  And I tried to add a windows machine to the domain.  When it asks for a username and password to authenticate to the domain I've tried the administrator acount I created and root... But it doesn't seem to work.. It says it can't find the username?  Any thoughts?

 I changed the root password too, as I have no recolection of being asked to set a root password when I setup ubuntu.

---

### Post by anim-eh on 2008-06-16
sudo passwd

i think would work...maybe

su
passwd

---

