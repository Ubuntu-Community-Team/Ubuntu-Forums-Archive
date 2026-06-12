---
title: "Another Samba Problem"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by Yacaph on 2008-04-02
I'm trying to set up Samba on a Ubuntu Server 7.10 machine to act as a file server for my home network with an XP and a W2K machine on WORKGROUP. 

I can see and access the Windows machines from the Linux box and vis-a-versa, but do not have write access to the Linux Samba shares from Windows unless I create a Windows user that matches my Samba primary Samba user which is both a user and a group. 

I have tried creating a Samba user with the same name and password that is used for the Windows login but it didn't work.

I've been working on this for a couple of days and am getting very frustrated. 

Any help would be greatly appreciated. My smb.conf file follows:

[global]
	workgroup = WORKGROUP
	netbios name = linux
	null passwords = yes
	security = SHARE
	path = /home
	wins support = yes

[Server]
comment = File storage on Server
path = /data
force user = voices
force group = voices
read only = No
guest ok = Yes
available = yes
browsable = yes
public = yes
writable = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = %S
    create mode = 0644
    create mask = 0944
    directory mode = 0755
    directory mask = 0755
    browseable = yes
    read only = no
    veto files = /*.{*}/.*/mail/bin/



[Data]
path = /home/voices/Data
available = yes
browsable = yes
public = yes
writable = yes

[home]
path = /home
available = yes
browsable = yes
public = yes
writable = yes

[voices]
path = /home/voices
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by superprash2003 on 2008-04-02
is your samba username and windows username the same, but the password different?

---

### Post by Yacaph on 2008-04-03
I have added users and passwords to Linux and Samba which match the Windows user names and passwords. When I did this folders were created for the users under the home folder, and I've shared these folders, but not included them in smb.conf. The Windows users have been added to the "voices" group.

Do I need to add a "force user" statement for these? I really don't understand what the "force user" and "force group" do.

On my W2K machine I added a user "voices" with the appropriate password and when logged on as voices I was able to write to the Linux shares specified in the smb.conf file, but with my normal login I am read-only.

I have run "chown" for voices "chown -R voices voices". Do I need to do this for the others users?

I'm fairly new to Linux and totally new to Samba and very confused.

---

### Post by superprash2003 on 2008-04-03
try accessing with a samba username and password which is not a windows username..

---

### Post by Yacaph on 2008-04-03
How do I do that? I don't get any type of login window when accessing Linux from Windows?

---

### Post by Eiríkr on 2008-04-03
Sounds like there are multiple factors leading to your frustration.  On one side, Windows is being stupid (not giving you a login prompt); on another side, Linux and its permissions work very differently than in Windows and require an understanding of how usernames and groups can be used to manage access; and on a third side, there are the complexities of configuring Samba.  Here we go:

----------
Windows is very poorly designed in a number of respects, one of which is that it constantly tries to second-guess the user.  Regarding Samba shares, Windows does this by caching the login credentials (username and password) the very first time you access a share, and then automatically just uses those same credentials forever more.  Doesn't matter if you want to access a different share or use different credentials or even if the credentials on the server side change, Windows will forever use the same credentials for that server.  You have to dig around to clear out the muck to force Windows to behave more sanely and allow you to specify different credentials.  Thankfully, user KennedyM put in the grunt work to figure out what you need to do to enable this, and described it in [thread=720889]this thread[/thread].  Follow his directions and you'll get that login window back.

----------
Permissions on a Unixy system are based primarily on username and group membership.  Read [this good write-up over on Wikipedia](http://en.wikipedia.org/wiki/File_system_permissions#Traditional_Unix_permissions) for a better idea of how this works.  

As an example, suppose you have a shared directory [font=courier]/data[/font], owned now by user "voices" and group "voices" (as you described in your post above).  So if you run [font=courier]ls[/font] ("**_l_**i**_s_**t") with the "long" option (-l) on this directory (-d), it'd look something like this:
```
yacaph@smbserver:~$ ls -ld /data
drwxr-xr-x 8 voices voices 4096 2008-04-01 13:59 /data
yacaph@smbserver:~$
```

We can see the "voices voices" bit, denoting the owning user and group.  The bit at the start of the line shows us permissions.  The first character tells us the type, "d" for directory in this case (run [font=courier]man ls[/font] in a terminal for more details on long-format notation).  Then come the three permissions triples.  The first is for the owner, the second for group members, and the last for everyone else.  So user "voices" has **_r_**ead, **_w_**rite, and e**_x_**ecute permissions on this directory (execute for a directory means you can open it).  Members of the group "voices" only have read and execute.  Everyone else also has read and execute.  

If you want to share that directory with multiple other users, you're best off creating a new group just for Samba sharing, adding your Samba users to that group, setting that group as the primary group on the shared directory, and then setting the group permissions on the directory.  These commands would look something like this:
```
sudo addgroup smbusers
sudo usermod -aG USERNAME   # <-- repeat for all relevant users
sudo chgrp smbusers /data
sudo chmod g+rwx /data
```

However, the owner and group of new files and directories on Unixy systems defaults to the user's username and group.  So if user "fred" creates a new sub-directory in /data, it will only be accessible by user "fred" and members of that user's primary group (usually the same name as the username, with that username as the only member).  That's where the "force user" / "force group" options come in handy, as you can force that new files directories would have a different owner / group.  In most cases, it's enough to just use the "force group" option, so you can still tell which user added which files or directories.

Aside from the owner and group for new files and directories, there are also the permissions on them (the "rwx" triples).  On Unixy systems, these are defined by something called a umask.  You can check your own umask by just typing in [font=courier]umask[/font] on a terminal.  The umask is like the chmod octal values in reverse, so a umask value of "2" would be the same as a "5" in chmod for directories or a "4" for regular files.  If memory serves, most Unixy systems have a default umask of 0022, which means no additional permissions (setuid, setgid, or sticky, see [url=http://en.wikipedia.org/wiki/File_system_permissions#Additional_Permissions]here[/ur]), a "7" on directories or a "6" on regular files for the owner (all three rwx on directories, and only r and w on files), a "5" on directories or a "4" on files for group members (only r and x on directories, and only r on files), and again a "5" or a "4" for all others.  So if user "fred" creates a new sub-directory in /data, even with the "force user" / "force group" options set (say, to "voices"), the new directory would have permissions of rwxr-xr-x, meaning group members still could not write any files to this directory.  This isn't very helpful for communal shares.  But then this is where the mode / mask options come in handy, as you can specify a different set of default permissions on new files and directories.  In most cases, you'll probably want to allow owners and groups full access, but only read access for all others, which would be "775" for directories and "664" for files.

----------
Regarding your smb.conf file:

**[global]**

This mostly looks good.  Note, however, that [font=courier]null passwords = yes[/font] is almost ***never*** a good idea, as null passwords are a gaping security hole.  


For all your share definitions, the lines:
[font=courier]browsable = yes
available = yes[/font]
are already the default values, and are therefore redundant.  I'd suggest deleting these lines to simplify your conf file.  Over the years, I've found the KISS principle (short for "Keep it simple, stupid!" ;)) to be a very good idea.  


**[Server]**

You've got some redundancy here.  These lines:
[font=courier]guest ok = Yes
public = yes[/font]
are synonyms, both saying the same thing.  You only need one or the other.  And these lines:
[font=courier]read only = No
writable = yes[/font]
are antonyms, both saying the same thing.  Again, you only need one or the other.  

These lines:
[font=courier]force user = voices
force group = voices[/font]
indicate that any connection to this share will access it as user "voices" with the primary group of "voices".  This has to do with filesystem permissions, which work differently in the Unixy lands than they do in Windows World.  Have a look [here]("http://en.wikipedia.org/wiki/File_system_permissions") for a brief overview.  Suffice it to say that any file or directory access will be allowed or denied based on this username and group and the relevant permissions, and any allowed new file or directory creation will have this user and group as the owner.  

This line:
[font=courier]guest ok = yes[/font]
tells me you're trying to set up guest access, which is actually quite complicated.  For small home systems, this is almost *never* required, and it's actually much easier to just have regular username-based access.  If you decide you still want guest access (maybe because you share sometimes with other folks and you don't know their usernames ahead of time), it's important to note that, even with guest access, Samba ***always*** uses a valid Linux username behind the scenes.  This is because you need a username before filesystem permissions can happen, as described above.  You can specify which username Samba should use in the [font=courier]guest account[/font] option in the [global] section, but if you don't specify anything, Samba defaults to the "nobody" username.  "nobody" is usually *very* restricted, and usually belongs to no groups, so will only have permission to any shares as defined by the final triple for "other" users (i.e. not the owner and not a group member).  This generally isn't very useful, so if you really want guest access, be sure to specify a guest account that has the needed permissions to your share.  


[B][homes]
[home][/B]

If you've got the **[homes]** share definition, you don't also need the **[home]** share.  I'd recommend you delete the **[home]** share and just go with the more elegant **[homes]**.  More about how the **[homes]** share definition works [here on the online man page]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#HOMESECT").  

These lines:
[font=courier]create mode =...
create mask = ...[/font]
and these lines:
[font=courier]directory mode = ...
directory mask = ...[/font]
are synonym pairs.  You only need one or the other.  As noted above in the permissions description, you probably want "664" for files and "775" for directories.  

However, I note in your **[homes]** share that you have the following line:
[font=courier]create mask = 0944[/font]
The numeric values in all the mode or mask options can only be those numeric values found in the octal codes for filesystem permissions (more [here]("http://en.wikipedia.org/wiki/File_system_permissions#Octal_notation") on Wikipedia), which only go as high as 7.  There should be no 9 anywhere here.


[b][Data]
[voices][/b]

You have the line:
[font=courier]public = yes[/font]
defined for both of these shares.  (Remember, this is the same as [font=courier]guest ok = yes[/font].)  Note that accessing these shares with a username that you haven't added to the Samba password file (using [font=courier]sudo smbpasswd -a USERNAME[/font]) will use the guest account, which in your case is the default "nobody" account because you have no [font=courier]guest account = USERNAME[/font] line in your [global] section.

----------
Definitely read over [the Wikipedia article on file system permissions](http://en.wikipedia.org/wiki/File_system_permissions).  You'll probably also want to bookmark [the online man page for smb.conf](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html), as this is an indispensable resource for figuring out and setting up your Samba server.

Good luck,

Eiríkr

---

### Post by Yacaph on 2008-04-03
Thanks Eiríkr,

It will take me a while to digest all of the info that you have provided.

---

### Post by Eiríkr on 2008-04-03
Cheers, Yacaph.  :D  Hope it helps.

Eiríkr

---

