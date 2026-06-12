---
title: "Samba is a myth. Never been able to actually connect to a share and create something."
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by greg52 on 2014-05-15
Ive been working with computers since the late 80's and consider myself a bit of an expert but apparently networking a windows pc to a linux server is just a myth. This is the third time in 10 years I've tried but the walk throughs that always say oh just load this then configure that and its just a piece of cake is just a deflection to keep linux and windows networking from interacting in any way. I understand, I hate Microsoft too., and would love to have only linux PC's in my world. Thats not the reality unfortunately...  So can someone actually give me a link to info that can actually make this work?

Clean Ubuntu 14.04 install with samba installed and running.

Samba config file:

[global]

   workgroup = SWC
   security = user


[share]
   comment = Ubuntu File Server Share
   path = /srv/samba/share
   browsable = yes
   guest ok = yes
   read only = no
   create mask = 0777  ; I tried 0755 too


I saved the config file. Restarted the Samba server. Created the shared folder and set the permissions.

sudo mkdir -p /srv/samba/share
sudo chown nobody.nogroup /srv/samba/share/

sudo restart nmbd
sudo restart smbd


I can see the server on the net and I'm asked for the user name and password to connect to it. I use the root ID and PW.  I then see the share. Cannot create anything in the folder...   (Destination folder access denied.......You need permission to perform this action.....)

Sorry for venting, it shouldn't be this hard for a simple share....

Help!!

---

### Post by QIII on 2014-05-15
Not a myth...

[ATTACH=CONFIG]253199[/ATTACH]

DUKE is my server (Ubuntu), and that is definitely my Windows 7 machine.  I grabbed a print screen on the Windows machine, saved it to Thor_Public from there and then attached it to this post from one of my Linux machines.

Could you tell us if you have used a particular wiki or tutorial to get started?  We'll try to steer you to better ones.

---

### Post by HiImTye on 2014-05-16
a few questions. you said 'I used the root ID and password' - do you mean to say you enabled the root account and gave it a password? if not, what account are you using?
what are the permissions on the files and folders your are accessing? file system?
what version of Windows are you trying to connect with?
can you perform these functions using Samba from your Ubuntu computer?

---

### Post by Morbius1 on 2014-05-16
> Clean Ubuntu 14.04 install with samba installed and running.

Samba config file:

[global]

   workgroup = SWC
   security = user
Your first mistake was deciding to monkey around with the default settings in smb.conf. That's not what the default [global] section should look like.

*[COLOR=#0000cd]**For example**[/COLOR]* - [COLOR=#0000cd]and this is just one omission[/COLOR] - when a Windows machine accesses a Samba server it passes the current users login name and password to that server. This in turn forces the samba server to deal with those credentials. By default samba has a setting "map to guest = Never" which means that the Windows guest user will never gain access. What Ubuntu does in it's smb.conf file is override that default with a new one: map to guest = Bad User. A "Bad User" is one that is not in the samba password database - i.e. a guest user. Also by default the "guest user" is defined as "nobody" which also happens to be the owner of the folder you are sharing.

I suggest you reset yourself to the default smb.conf.

[COLOR=#0000cd]***Side note***[/COLOR]: This share will break the instant you create samba users ( by adding them to smbpasswd ) because at that point they are no longer "nobody":
> [share]
   comment = Ubuntu File Server Share
   path = /srv/samba/share
   browsable = yes
   guest ok = yes
   read only = no
   create mask = 0777
At a _minimum_ I would add a line to fix that issue:
> [share]
   comment = Ubuntu File Server Share
   path = /srv/samba/share
   browsable = yes
   guest ok = yes
   read only = no
**[COLOR=#0000cd]force user = nobody[/COLOR]**
   create mask = 0777

---

### Post by david144 on 2014-05-16
Besides what Morbius1 said above about:
```

map to guest = bad user

```
[quote="http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html"][COLOR=black][FONT=helvetica][SIZE=1]This parameter can take four different values, which tell [smbd(8)]("http://www.samba.org/samba/docs/man/manpages-3/smbd.8.html") what to do with user login requests that don't match a valid UNIX user in some way.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=helvetica][SIZE=1]The four settings are :[/SIZE][/FONT][/COLOR]
[COLOR=#3333CC][FONT=helvetica]
[LIST]
[*][COLOR=black][SIZE=1]Never - Means user login requests with an invalid password are rejected. This is the default.[/SIZE][/COLOR]
[/LIST]
[/FONT][/COLOR][FONT=helvetica]
[LIST]
[*]**[SIZE=1][COLOR=#0000ff]Bad User - Means user logins with an invalid password are rejected, unless the username does not exist, in which case it is treated as a guest login and mapped into the [/COLOR][[COLOR=#0000ff]guest account[/COLOR]]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT")[COLOR=#0000ff].[/COLOR][/SIZE]**
[/LIST]
[/FONT][COLOR=#3333CC][FONT=helvetica]
[LIST]
[*][COLOR=black][SIZE=1]Bad Password - Means user logins with an invalid password are treated as a guest login and mapped into the [guest account]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#GUESTACCOUNT"). Note that this can cause problems as it means that any user incorrectly typing their password will be silently logged on as "guest" - and will not know the reason they cannot access files they think they should - there will have been no message given to them that they got their password wrong. Helpdesk services will *hate* you if you set the *map to guest* parameter this way :-).[/SIZE][/COLOR]
[*][COLOR=black][SIZE=1]Bad Uid - Is only applicable when Samba is configured in some type of domain mode security (security = {domain|ads}) and means that user logins which are successfully authenticated but which have no valid Unix user account (and smbd is unable to create one) should be mapped to the defined guest account. This was the default behavior of Samba 2.x releases. Note that if a member server is running winbindd, this option should never be required because the nss_winbind library will export the Windows domain users and groups to the underlying OS via the Name Service Switch interface.[/SIZE][/COLOR]
[/LIST]
[/FONT][/COLOR]
[COLOR=black][FONT=helvetica][SIZE=1]Note that this parameter is needed to set up "Guest" share services. This is because in these modes the name of the resource being requested is *not* sent to the server until after the server has successfully authenticated the client so the server cannot make authentication decisions at the correct time (connection to the share) for "Guest" shares.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=helvetica][SIZE=1]Default: *[I]map to guest* = Never[/I][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=helvetica][SIZE=1]Example: *[I]map to guest* = Bad User[/I][/SIZE][/FONT][/COLOR]
[/quote]

I don't know if this is it but have you tried adding:
```

 [share]
 comment = Ubuntu File Server Share
 path = /srv/samba/share
 browsable = yes
 guest ok = yes
 read only = no
 create mask = 0777
[COLOR=#0000ff]** writeable = yes**[/COLOR]

```

I know it's just an inverted synonym but I did it on my smb.conf and fixed my problem not being able to write. The next problem I had was my mask isn't inheriting my desired group permissions so I'm still trying to figure that one out.

I'm not using guest on mine, I have specific usernames and groups which passively match my windows domain usernames and passwords, gets me right past the prompting. Although I only have 2 users at home for [my SAN]("http://ubuntuforums.org/showthread.php?t=2220677").

If your environment has too many users for that and you have a windows domain you might try attaching to it
[quote=http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html][SIZE=1]
**security (G)**[/SIZE][SIZE=1]
[/SIZE][SIZE=1]This option affects how clients respond to Samba and is one of the most important settings in the smb.conf file.[/SIZE]
[SIZE=1]
The default is security = user, as this is the most common setting, used for a standalone file server or a DC.[/SIZE]
[SIZE=1]
The alternatives are security = ads or security = domain , which support joining Samba to a Windows domain[/SIZE]
[SIZE=1].
.
*SECURITY = DOMAIN*[/SIZE][SIZE=1]
[/SIZE][SIZE=1]
This mode will only work correctly if net(8) has been used to add this machine into a Windows NT Domain. It expects the encrypted passwords parameter to be set to yes.[COLOR=#0000ff]_ In this mode Samba will try to validate the username/password by passing it to a Windows NT Primary or Backup Domain Controller, in exactly the same way that a Windows NT Server would do._[/COLOR][/SIZE]

[SIZE=1][COLOR=#ff0000]**Note that a valid UNIX user must still exist as well as the account on the Domain Controller to allow Samba to have a valid UNIX account to map file access to.**[/COLOR][/SIZE]

[SIZE=1]Note that from the client's point of view security = domain is the same as security = user. It only affects how the server deals with the authentication, it does not in any way affect what the client sees.[/SIZE]

[SIZE=1]Note that the name of the resource being requested is not sent to the server until after the server has successfully authenticated the client. This is why guest shares don't work in user level security without allowing the server to automatically map unknown users into the guest account. See the map to guest parameter for details on doing this.[/SIZE]
[SIZE=1]
[/SIZE][SIZE=1]See also the password server parameter and the encrypted passwords parameter.[/SIZE]
[SIZE=1]
[/SIZE][SIZE=1]Note that the name of the resource being requested is not sent to the server until after the server has successfully authenticated the client. This is why guest shares don't work in user level security without allowing the server to automatically map unknown users into the guest account. See the map to guest parameter for details on doing this.[/SIZE]
[SIZE=1]
[/SIZE][SIZE=1]See also the password server parameter and the encrypted passwords parameter.[/SIZE]

[SIZE=1]*SECURITY = ADS*[/SIZE]
[SIZE=1]
[/SIZE][SIZE=1]In this mode, Samba will act as a domain member in an ADS realm. To operate in this mode, the machine running Samba will need to have Kerberos installed and configured and Samba will need to be joined to the ADS realm using the net utility.[/SIZE]
[SIZE=1]
[/SIZE][SIZE=1]Note that this mode does NOT make Samba operate as a Active Directory Domain Controller.[/SIZE]
[SIZE=1]
[/SIZE]**[COLOR=#0000ff][SIZE=1]Read the chapter about Domain Membership in the HOWTO for details.[/SIZE][/COLOR]**
[/quote]

---

