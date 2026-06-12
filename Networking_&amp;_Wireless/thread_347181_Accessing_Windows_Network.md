---
title: "Accessing Windows Network"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by droogie2799 on 2007-01-26
I have an Ubuntu box as well as a Windows box on the same network.  Both are hardwired in to a linksys router.  If I browse network places on the windows box, I can see both machine under the workgroup workgroup.  When I double click the ubuntu box I get a user name and password prompt.  I enter my credentials, which are correct, and the screen just bounces back.  No error or anything, basically getting an access denied.

From the ubuntu box, I go places, network server.  I see an icon for each of the machines (windows and ubuntu) and I see an icon for windows network.  If I click on the windows machine icon, I get a user name and password prompt which has the workgroup and username filled out.  They are actually correct because I use the same user name and password under both OS's.  So I type my windows user name and password and nothing.  One thing to note, on the top of the log in window it says you must login to access guest@desktop (desktop being the name of the windows box)  I tried enabling the guest account and logging in as guest.  Nothing.

I then click on the Windows Network icon.  I then see the workgroup icon (name of workgroup), click that, I see both machines.  They are acutally file icons at this type.  I click the windwos icon, get an error that it isn't a file, then I see the correct icon of a computer.  I click the windows box and I get the same login screen as before.  Enter credentials, nothing.  I click on the ubuuntu box, I see the shares. 

Can anyone help me share files between the two  In order for Ubuntu to be viable on my network I need to share files.

---

### Post by Buck2348 on 2007-01-26
This will fix your minor problem--the wrong icon and error message:
```
gksudo gedit /etc/gnome-vfs-2.0/modules
```
change
Code:  [COLOR="RoyalBlue"]smb: [daemon] libsmb[/COLOR]     to
Code:  [COLOR="RoyalBlue"]smb: libsmb[/COLOR]
For the major problem, you might find that this allows you to browse Ubuntu shares from Windows (with no password):
```
gksudo gedit /etc/samba/smb.conf
```
Find these lines:
```
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
;   security = user

```
Change the last line to:
   ```
security = share
```
For more info see [http://easylinux.info/wiki/Ubuntu_Edgy#Samba_Server](http://easylinux.info/wiki/Ubuntu_Edgy#Samba_Server)

I don't believe you mentioned having set a samba password.  If you haven't you might need to run the command "smbpasswd."  Again there is more info in the link above.

I hope that helps some--I'm not a Linux guru.

Buck

---

### Post by droogie2799 on 2007-01-27
Thanks for the link that was very helpful.  I never did setup any password with samba.  When I run the password utility, I get an error that the password change was rejected.  I am guessing since I never set up a password, when it asks me to type my old password I don't know it.  How do you set up an initial password with samba?  I thought it would assume the password of the su account I was logged in as.

---

### Post by Buck2348 on 2007-01-27
After reading part of man smbpasswd, I believe if there is no samba password already set, you should just press <enter> for the old password and then type in what you want for the new password.

Buck

---

