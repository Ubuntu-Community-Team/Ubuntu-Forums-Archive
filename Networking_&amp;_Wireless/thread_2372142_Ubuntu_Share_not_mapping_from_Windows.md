---
title: "Ubuntu Share not mapping from Windows"
date: 2017-09-21
forum: Networking &amp; Wireless
---

### Post by ozmotherboard on 2017-09-21
I'm a newbie, so pardon my ignorance. I have an old Dell Latitude D610 laptop that has Ubuntu installed on it.  I have Linux shares that work. e.g. /home/user/Documents. I can connect from my Windows PC and I can copy files from it.  This has been working for years.  I have relaxed security because I'm a newbie and I just want things to work.

I have just mounted an extra hard drive in the CD/battery/drive bay and it appears as /media/user/UbuntuD but I can't connect to this from my Windows PC. I have checked the permissions and I'm not sure what I'm doing wrong. From the Windows PC, it seems to map the path, but then reports "Access is denied" when I try to connect.

When I check on the Ubuntu terminal (sudo smbstatus -S -p), it appears that the the User "nobody" is making the connection. Which is OK because I set the usershare_acl to Everyone. "nobody" works for the /home/user/Documents and /home/user/Downloads but not for the /media/user/UbuntuD. It seems to me that the /media/user/... is the problem.

I have forced the connection from a new user that I've created and verified that the 'working' shares are connecting using that new username, but the /media/user/UbuntuD still cannot be connected.

Can someone help me with what I need to do to make this work? Thanks in advance.

---

### Post by Morbius1 on 2017-09-22
> **ozmotherboard said:**
> [SIZE=3]It seems to me that the /media/user/... is the problem.[/SIZE]
You are correct.

/media/user is set up by the system with an acl that permits only "user" the ability to get to what is under it. You can run this command to verify this for yourself:
```
getfacl /media/$USER
```
> getfacl: Removing leading '/' from absolute path names
# file: media/morbius
# owner: root
# group: root
user::rwx
[COLOR=#0000cd]**user:morbius:r-x**[/COLOR]
group::---
mask::r-x
other::---
In the case above only I (morbius) can open the /media/morbius folder to access what's under it.

Rather than mess about with permissions on /media/user and since your share allows guest access and since you created the share from your file manager I recommend the following:

** Edit /etc/samba/smb.conf and add the following line - right under the "workgroup = WORKGROUP" line:
```
force user = your-user-name
```
[COLOR=#0000cd][I]Change your-user-name to your ubuntu login user name

[/I][/COLOR][COLOR=#000000]*** *Then restart smbd[I]:
```
sudo service smbd restart
```[/I]

"nobody" will be converted to your user name for these samba shares making it possible to gain access to the drive.[/COLOR]

---

### Post by ozmotherboard on 2017-09-23
> **Morbius1 said:**
> 
```
force user = your-user-name
```

Thank you very much.  That worked.

Kind regards.

---

