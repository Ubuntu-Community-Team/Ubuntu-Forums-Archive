---
title: "Googled and Googled and Googled"
date: 2005-04-14
forum: Networking &amp; Wireless
---

### Post by domesticatewhat on 2005-04-14
I wasn't sure which forum this should go in considering I have the ubuntu64 but here goes.

I have read through the forums with no luck and googled until my hands hurt. I have samba setup and configured.

I can access the windows share and edit files but cannot do the same on windows. I cant even access the samba share locally. I am prompted for a username and password (which I have also setup) and am denied because I dont have the correct permissions.

here is my smb.conf:
______________________
[global]
workgroup = Network
netbios name = Samba
security = share
wins support = yes
server string = SambaShare

[SambaShare]
path = /media/usbdisk
comment = External Hard Drive
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes
only guest = yes
_______________________

Any suggestions would be awesome.

---

### Post by heimo on 2005-04-14
My quick guess is that you haven't set up samba password. (smbpasswd) By default there's no syncronization of unix->samba passwords and you can't use just your regular password to authenticate to your samba network shares. At least this is how it was couple years ago.

You may want to set also syncronization, so that you don't have to maintain two different lists of passwords (of course this is probably not problem if there's small number of users).

---

### Post by domesticatewhat on 2005-04-14
I tried to set the password and got this:

____________
Failed to find entry for user root.
Failed to modify password entry for user root
____________

---

### Post by heimo on 2005-04-15
How about [i]smbpasswd -a [username]
[/i](adds new samba user)

---

### Post by domesticatewhat on 2005-04-15
tried that also. It says that the user was added and once I try to login with that username/password it doesn't let me. I even tried to creat groups and guest logins with no success.

---

### Post by heimo on 2005-04-15
Hmm.. Only now I had a good look on your config. So you're forcing to guest only account? I think you need to define which unix account is used as a guest account. I'm not sure but line in your global section like this may help:

guest account = ftp
substitute ftp with appropriate account

Also try running *testparm *to check for possible syntax errors.


EDIT: *man smb.conf *is really, really helpful

---

### Post by domesticatewhat on 2005-04-15
Still a no go. I have read countless help files and manuals with no such luck. Is it as simple as

apt-get remove samba etc...etc..

to remove samba and the conf file? I am thinking maybe if I start over with what information I know now it might help.

---

### Post by heimo on 2005-04-15
You do remember to restart samba after configuration changes? (*/etc/init.d/samba restart*) To complete reinstall, you need to *apt-get remove [samba packages] *and rename your smb.conf.

Maybe you also could (or maybe you already have) try to first configure it to allow also regular user accounts (only guest = no). It's easier if you can get it working at all first and then get it to do what you really want.

If you're familiar with tools like tcpdump and ethereal, those could be of use in this situation. You could also try *nmap localhost* and if possible do port scan from Windows to your samba server to make sure that ports (I guess 135 and 139) are open and accepting connections. (EDIT: probably 139 and 445)

---

### Post by domesticatewhat on 2005-04-15
I will try to do a port scan and see if that helps. Yeah, I already tried to regular access but was (needless to say) unsuccessful there also.

I just can't understand why I can't even set a root password for samba. I'm thinking a reinstall is invitable.

---

### Post by domesticatewhat on 2005-04-15
Finally got it. For me I do not have an option to set the windows domain/host name in the network config gui so I set it manually and voila it worked. I also setup webmin to make things a little easier.

Thanks for your help!

---

