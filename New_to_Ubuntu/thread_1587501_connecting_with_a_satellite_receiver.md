---
title: "connecting with a satellite receiver"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by sallam on 2010-10-03
Greetings

My satellite receiver has an SMB file setup option, and I would like to connect my ubuntu laptop with the receiver so that I can record from TV channels on my laptop's hard disk, or play recorded videos.

How can I connect them using SMB file sharing?
When I go to the SMB page in the receiver, it requires info input in 3 fields: share address, username and password. Could someone help with those fields please? I don't know which info I should type there?
I have samba and pyneighborhood installed, but since I'm a newbie, I don't know how to use them..

Many thanks.

---

### Post by sallam on 2010-10-04
Anyone please?

---

### Post by luvshines on 2010-10-04
You will need to setup a Samba server on ur Ubuntu machine and create a Samba share(SMB share).
Here is a tutorial:
[https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba](https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba)

Then the share address and username, password needs to be entered into the Satellite receiver.

---

### Post by luvshines on 2010-10-04
And before you run into any complications, getting confused and coming up with more difficult to debug issues (seeing the number of people posting Samba issues), I should give you the steps which I followed.

4 simple steps, no rocket science:

1. Install sudo apt-get install samba

2. Change the default /etc/samba/smb.conf file to include the following:

netbios name = <your-host-name>
security = user

[Share-name-of-your-choice]
comment = Movies for Sharing
path = <complete-path-to-share>
browseable = yes
writeable = yes
guest ok = no

Save and exit the editor

3. sudo service smbd restart

4. sudo smbpasswd -a <user-name>

It will prompt for password twice

**DONE !!**

To see if it is working

A. From nautilus:
1. ctrl+l <tFor the address bar>

2. smb://<netbios-name OR server ip>

And the share should be accessible

B. From terminal:

sudo apt-get install smbclient

To list the share
smbclient -L <netbios-name OR server ip> -U<username>%<passwd>

To access the share:
smbcliet //<netbios-name OR server ip> -U<username>%<passwd>

Some things to take care off:
1. Avoid share name with spaces to keep away from issues
2. Make sure firewalls rules are good if access is not working. Better switch them off :)

sudo service iptables off
sudo ufw disable

3. The complete path upto the share location should have the permission 755(every directory) atleast since you are sharing it for world, so the world should be able to read it :D
4. Avoid guest and other stuff in the beginning. Once you get this working then you can modify, that is what I would suggest

If you still run into trouble --> Post what you did and your smb.conf file

Good LUCK !!

---

