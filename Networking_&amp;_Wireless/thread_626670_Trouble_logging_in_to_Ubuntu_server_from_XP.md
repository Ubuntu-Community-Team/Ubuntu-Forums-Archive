---
title: "Trouble logging in to Ubuntu server from XP"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by sszook on 2007-11-29
I just set up a Ubuntu (file) server for our school.  I have configured Samba.  I have a variety of Windows machines (some Home, some Pro, some 2000) that will be logging in to it.  My XP machines can see the server and the user groups, but when I try to connect, it returns my user name with the computer name in front (Businesslab1/szook) and refuses to log in.  No error messages.  
Please let me know what info I can post from my set up that would help.  
Thanks,
Sarah

---

### Post by paulau on 2007-11-29
Hi,

I'm actualy having the exact same problem. Also my user name and password dont when when connecting from a Vista machine and Leopard.

I have also tried putting the computer name before the username ie"computername\user" which didnt work.

Regards,
Paul

---

### Post by digitalbenji on 2007-11-29
Is the Ubuntu server being used as a domain controller (login authentication to start a user session), or, is it only being used as a file server?  Have either of you made the necessary modifications to the smb.conf file (or installed samba?) to set this up?

Post your smb.conf files if you have them.  If not, say so, and me or someone else will explain how to set this up.

---

### Post by paulau on 2007-11-29
Hi,

I am logging into the Ubuntu machine with a username and password, although i dont have  a domain setup on my network. I've tried the same user name and password when accessing the machine with smb.

The share was setup with samba using the "Shared Folders" application.

I don't actually have my smb.conf on this machine at the moment. 

Thanks,
Paul

---

### Post by digitalbenji on 2007-11-29
If I understand correctly, the issue you are having is that from a Windows Vista machine you can't access a folder shared from an Ubuntu machine?  Correct?

Are you able to navigate to the share, and the password just isn't working?  Or are you having problems locating the share to begin with?

On the Ubuntu box, you will need to add a samba user I think.  
```
 smbpasswd -a username 
```

That should create a user who can access the share.
Because you don't have a domain, DNS resolution may not be working.  In my experience this has a lot to do with your router at home, as this is essentially an ad hoc domain you would be talking about (no domain controller).  If you can't browse to the share, I would try doing start->run and then entering \\the.ip.of.server\

---

### Post by paulau on 2007-11-29
Hi,

Ok i had a quick play with it before work this morning and   added an account with smbpasswd, however it seems to be a read only account?

I don't have the read only box checked in "Shared Folders". 

Also when i connected with Leopard i was asked to authenticate, however with Vista i wasn't asked.

Regards,
Paul

---

### Post by digitalbenji on 2007-11-30
You need to edit the /etc/samba/smb.conf .  Do this as root
```
sudo nano /etc/samba/smb.conf 
```

Locate the section regarding your share, and add the following line to it
```
read only = no
```

Regards

---

### Post by lintoon on 2007-11-30
I had the same problem ages ago.  My problem was a mismatch between the username and passwords on both boxes.

Ensure your details are the same for both machines.  Eg set the ubuntu username and password to be the same as the XP login details.

---

### Post by sszook on 2007-11-30
Here is my smb.conf file.  I just need the server to be a file server.  I try to get into the Central workgroup throughWindows Explorer and I get "not accessible--The account is not authorized from this station.

# Global Parameters
[global]
workgroup = CENTRAL
netbios name = gfcchsmain
security = user
encrypt passwords = false
passwd chat = *New*Password* %n\n*Re-enter*new*password* %n\n *Password*changed*
username map = /etc/samba/smbusers
syslog = 0
name resolve order = wins bcast hosts
printcap name = CUPS
show add printer wizard = No
add user script = /usr/sbin/useradd -m -G users '%u'
delete user script = /usr/sbin/userdel -r '%u'
add group script = /usr/sbin/groupadd '%g'
delete group script = /usr/sbin/groupdel '%g'
add user to group script = /usr/sbin/usermod -A '%g' '%u'
add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody '%u'
logon script = scripts\login.bat
logon path =
logon drive = Z:
domain logons = Yes
preferred master = Yes
wins support = no
printing = CUPS

[staff]

path = /home/samba/staff
read only = no
valid users = %G

available = yes
browsable = yes
public = yes
writable = yes
[students]

path = /home/samba/students
read only = no
valid users = %G

available = yes
browsable = yes
public = yes
writable = yes
[deskpub]
comment = Desktop Publishing
path = /home/samba/deskpub
read only = no
valid users = %G

available = yes
browsable = yes
public = yes
writable = yes
[office]

path = /home/samba/office
read only = no
valid users = %G


available = yes
browsable = yes
public = yes
writable = yes

[samba]
path = /home/samba
available = yes
browsable = yes
public = yes
writable = yes

[software]
path = /home/samba/software
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by sszook on 2007-11-30
Check.  they are the same.

---

### Post by sszook on 2007-11-30
I think my shares are all set to "read only = no".  It seems to be fighting with a domain name at the XP box?

---

### Post by sszook on 2007-11-30
I set my "encript passwords" to true and now I can see the shared folders, but it still keeps putting the computer name in front of the username when I try to connect to it.

---

### Post by Björn Felten on 2007-11-30
I used to have the exact same problem from time to time. But after I discovered [URL="http://ubuntuforums.org/showpost.php?p=3842392&postcount=13"]
_**this great guide**_[/URL] I never again have had any problems setting up shared folders on my Ubuntu machines.

---

### Post by sszook on 2007-12-03
I had already added my users.  I did the enable command.  I still get the computer name in front of user response when I try to connect to my shared folder.  Is there a problem with a shared folder within a shared folder?  
For example:  I have a Samba folder that contains my groups' shared folders and then within the group folders are individual folders.  Each user has a path mapped to their individual folder...  i.e. students accessing their own folder only, staff each accessing their own.

---

### Post by jonandrews on 2007-12-04
Hi. I put the guide together the guide mentioned in the previous post.

To investigate your last question, I've just set up a basic shared folder within a shared folder with no problem at all. I didn't have to set any permissions for the sub-folder, just selected 'Share folder' and, from the next dialog,  'Share through Windows network'.  It was immediately accessible from Windows machines.

---

### Post by sszook on 2007-12-12
I think it has to do with the users only having access.  I have a folder that anyone can access that works, but the ones where only certain users can access (their own folders)--the Windows machines put the computer name in front of the username and it won't log in.  I don't think it is even getting out of the Windows machine...or it is getting rejected extremely quickly.

I welcome any suggestions!!

---

