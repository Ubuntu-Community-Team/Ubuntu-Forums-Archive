---
title: "Seeing Samba shares from the WinXP box is very slow"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by jqp on 2006-12-26
I've searched quite a bit around the internet for an answer to this.  I've found a lot of questions with the same problem, but no answers.

The windows machine is XP Home, so I'm on a workgroup, not a domain or anything fancy like that.

From my Ubuntu machine, I can access shares on the XP machine with no problem.

From the XP machine, accessing shares on the Ubuntu machine is very slow.

In XP,  I can go to "View Workgroup Computers" and see the Ubuntu machine, double-click it and then I see a list of folders, including, for example, my "music" folder.  When I click the "music" folder (or anything else), the window stops responding for about 30-45 seconds before it highlights the icon I clicked on.  When I double-click the "music" folder, after about 30-45 seconds I see the contents of the "music" folder, which for now is just 3 files - a text file, an mp3, and a jpg file.  When I click on any of those files, I get the same long delay before the icon highlights.  When I double-click to open a file, I get the same delay before the file opens in whatever program opens the file, but it does work.  When I drag and drop a new file from the windows machine to that folder, I get the same delay - the window locks up during this time - before - the file does successfully copy into the "music" folder.  I can successfully see those files locally on the ubuntu machine with no problem.

Here's my entire smb.conf file if it helps
```

[global]
server string = Ubuntu
workgroup = MSHOME
hosts allow = 127. 192.168.1.
printcap name = /etc/printcap
printing = cups
cups options = raw
guest account = Debian-exim
log file = /var/log/samba/samba.log
max log size = 1000
username level = 8
password level = 4
username map = /etc/samba/smbusers
add user script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M %u
encrypt passwords = no
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*\n
null passwords = yes
socket options = TCP_NODELAY SO_KEEPALIVE SO_SNDBUF=8192 SO_RCVBUF=8192
interfaces = 127.0.0.1/8 192.168.1.0/24
remote browse sync = 192.168.1.255
remote announce = 192.168.1.255
local master = no
os level = 33
domain master = no
preferred master = no
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
name resolve order = wins lmhosts bcast
wins support = yes

wins proxy = no
dns proxy = no
preserve case = no
winbind use default domain = yes
winbind uid = 16777216-33554431
winbind gid = 16777216-33554431
template shell = /dev/null
security = share
restrict anonymous = no
max protocol = NT
ldap ssl = No
server signing = Auto

[homes]
comment = Home Directories
path = /home
read only = no
share modes = no
# locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /home/profiles
read only = no
locking = no
create mask = 0600
directory mask = 0700
browseable = no

[printers]
comment = All Printers
path = /var/spool/samba
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents


guest ok = yes
read only = no

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

[music]
path = /home/barnett/music/
guest ok = yes
read only = no
case sensitive = no
msdfs proxy = no

```

I have not edited that file manually, yet.  I hope there's some magic trick to making this work properly.

TIA

---

### Post by Alpha01 on 2008-01-10
The problem is Windows

I have the same problem that  you have. When I first installed the samba server on my linux box everything worked like a charm until I change the hostname of the computer that was serving the files and after words its completely slow to access shares from all my Windows computer. 
On the other hand, it is perfectly fast whenever I accessed shares from my Mac Book and from the Desktop thats running Ubuntu Fiesty. 

My solution to this is not to use Windows :-)

---

### Post by countrylane on 2008-04-12
I have the same or similar issue as the original Post, although I am sure that the Ubuntu version is different since the orignal post was in 2006!

The only difference between my issue and the original question is that I have my home folder on Ubuntu visible as a Samba share, which is very fast to connect to and has no slowness problems I also have my second hard drive (physically installed on the Ubuntu PC)  listed as a Samba share......this drive connects quickly on the first click, but whenever I click on any file or any folder on this drive from my WinXP PC, BOTH of my PC's seem to freeze for a very long time (30 seconds to several minutes).

Any suggestions as to how to fix this or what is causing the problem?  Why does the second HD freeze and the home directory stuff doesn't?  BTW, the second drive has been installed and working fine in this PC for years. I ran diagnostics on it and it passed, so I don't think there is a bad sector, or failure issue.

---

### Post by oddin85 on 2008-04-12
when i access my files from windows i mount the samba share as a network drive, this makes accessing the files a bit faster than browsing through the windows network thing

to mount a network drive on XP:
1) start>my computer
2) tools>map network drive
3) for the folder use "\\<ip of ubuntu machine>\<share name>" without the quotes and replacing
 the things in the brackets with the correct information
4) click finish and enter your login info

on vista it's almost the same:
1) start>computer
2) map network drive
3) for the folder use "\\<ip of ubuntu machine>\<share name>" without the quotes and replacing
 the things in the brackets with the correct information
4) click finish and enter your login info

PS: make sure you use backslashes and not forward slashes
/ = *nix
\ = windows

---

### Post by countrylane on 2008-04-12
> 3) for the folder use "\\<ip of ubuntu machine>\<share name>" without the quotes and replacing the things in the brackets with the correct information

I tried using the IP and the name of the Ubuntu machine. Both give the same SSSSSLLLLLLLOOOOOOWWWW results.

---

### Post by gsiliceo on 2008-04-13
You can vote to change this in ubuntu using the brainstorm page, theres already an idea voting to make samba easier. Please vote here.
[Improve file/folder sharing experience (Samba)]("http://brainstorm.ubuntu.com/idea/403/")

---

