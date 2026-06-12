---
title: "I'm so close yet, so far from perfecting my samba share"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by vamp4life666 on 2008-01-24
I have been trying to set up a a simple samba share.

I found the following how to and followed it to exactly:
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+solutions](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+solutions)


I am able to reach the machine from both OSX 10.5 and Win XP.
I can login into the Ubuntu 7.10 sever that has samba running on it with both.

When I login I have access to a shared folder file called "share" however I honestly don't know where that is on my ubuntu box.

Also he file I am attempting to share is "users".


Bellow is the smb.conf file if someone could give it a glance....

[global]
netbios name = storageserver
server string = 
workgroup = rendergroup
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192

pssdb  tdbsam
security = user
null passwords = true
username map = /etc/smaba/smbusers
name resolve order = hosts wins bcast

wins support = yes

syslog = 1
ayslog only = yes

[share]
path = /storage/users
browasable = yes
read only = no
guest ok = yes
create mask = 0775
force user michael
force group = michael

Any help would be great, thanks... michael

---

### Post by vamp4life666 on 2008-01-24
i feel slightly retarted....

one of my cowrokers just pointed out that the reson it comes up as such is because that what titled it [share].

To prove the point he shanged it in the smb.conf file to [johnsbox]     and now thats what it mountss as....

i think its time to go back to bed.....

---

