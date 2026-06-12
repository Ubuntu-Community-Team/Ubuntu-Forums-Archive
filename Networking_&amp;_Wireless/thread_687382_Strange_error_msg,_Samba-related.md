---
title: "Strange error msg, Samba-related?"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by dphirschler on 2008-02-04
I just got a strange error message on boot and I am not sure what to do with it.  I suspect it's Samba-related since I just set up a file server.  Here is the error message.

> !
 
User's $HOME/.dmre file is being ignored.  This prevents the default sesson and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other userers.
 
OK


And here is my smb.conf.

```
[global]
    ; General server settings
    netbios name = UBUNTU
    server string =
    workgroup = HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    guest account = nobody
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

;[MyFiles]
;    path = /home/darryl/
;    browseable = yes
;    read only = no
;    guest ok = no
;    create mask = 0644
;    directory mask = 0755
;    force user = darryl
;    force group = darryl

[share]
    path = /home/darryl/
    comment = File server
    browseable = yes
    writeable = yes
    read only = no
    hide dot files = yes
    create mask = 0700
    directory mask = 0755
    veto files = /*.{*}/.*/mail/bin/

    public = yes
    guest ok = yes
    guest account = nobody

```

So my questions are, what does the error message mean, and is it Samba-related?  Furthermore, how can I fix it?

Lastly, I think I should point out that I am still sort of new to Linux and Ubuntu.


Darryl

---

### Post by ruy_lopez on 2008-02-04
Probably just means that ~/.dmre is owned by root or something. Check the ownership and permissions for the directory in question. 

That said, if Samba is working fine, you can probably ignore it.

---

### Post by dphirschler on 2008-02-04
Well, I am not comfortable ignoring the error message even if it is harmless.  I'd like to fix it.  I can change the permissions on the file with a chmod, but I don't know how to change the ownership.  The permission on that file probably got changed when I set it for the whole directory... while setting up my Samba share.  I should probably set the permissions for all the .* files to 644, right?


Darryl

---

### Post by dphirschler on 2008-02-05
I tried to change permissions on that file ($HOME/.dmre).  First I went to it in the GUI and did a "Show hidden files".  The file was not there.  So then I went in in the Terminal and did an ls -l.  Still didn't show up.  So then I did a chmod 0644 .drme.  It seemed to work, but when I rebooted the same error message appeared.

It seems that I am missing some fundamentals with dealing with Linux with users and permissions.  I am the only user on this machine (except for root) yet I see directories that were created by another user.  These are probably directories I created on this machine working through Samba (using one of the XP machines on the network).  

I'd like to understand this error message because I believe I caused it while setting up the Samba share.  In setting it up, I wanted the following:

- users do not have to log in.
- users have power to read, write, delete, and create files and directories.
- users can do these actions from any Windows PC just like they can on their local hdd.
- mp3 files in the home/music folder
- pics in the home/pictures folder
- documents in the home/documents folder

In setting this up, and dealing with each issue as I discovered it, I set the permissions on the home directory (and all files/directories within it) to 755.  I also put in the smb.conf file the lines necessary to give permission to users of the share to do all the above.  

Since this is all new to me, I am certain that I may not have the smb.conf file or my permissions entirely correct.  Somebody please steer me in the right direction, because I seem to be getting lost.


Darryl

---

### Post by ruy_lopez on 2008-02-05
Try this:

```


sudo chown yourusername:yourgroupname ~/.drme


```

chmod changes permissions
chown changes ownership
chgrp changes group

using chown like I show above changes ownership and group in one fell swoop. So you rarely need to use chgrp.

You will see directories created by others because you own the directory which is being shared. It is the permissions for the parent directory, in this case darryl, which determines whether you can see files and directories. Plus the directory mask in the smb.conf allows you to see **inside** of other people's directories.

If you only want people to see files and directories they create, you should create a folder for sharing, then create subdirectories which only can be entered by the owner.

---

### Post by dphirschler on 2008-02-06
OK I did the following:

```
sudo chown darryl:HOME ~/.drme
```

I got "invalid groupname".  So either my capitalization screwed it up, or I have the wrong groupname.  I was thinking the workgroup name, but that must be wrong.  So the question now is... what groupname?


Darryl

---

### Post by jetsam on 2008-02-06
Just your own group should work:

```
sudo chown darryl:darryl ~/.drme
```

---

### Post by dphirschler on 2008-02-07
OK, first of all, I discovered a typo.  I meant .dmrc, not .drme.  Anyways, I did the command

sudo chown darryl:darryl ~/.dmrc

And then I did an ls -l to see the permissions.  And then for good measure, I did 

sudo chmod 0644 .dmrc

And then I did ls -l again.  Nothing changed, so the permissions were already correct.  And then I rebooted and I see the error message still.  Next time I boot, I will compare it to the one I wrote down to be sure.

So the next thing I want to try is commenting out the lines under [share] in my smb.conf file.  If that makes the error message go away then I will at least know what caused it.  Then I can figure out how to deal with it.  But I am getting the feeling that Linux does not like me sharing my home folder with everybody.


Darryl

---

### Post by ruy_lopez on 2008-02-07
Take a look at this:

[http://rudikismo.wordpress.com/2008/01/09/homedmrc-error-message-on-ubuntu-704/]("http://rudikismo.wordpress.com/2008/01/09/homedmrc-error-message-on-ubuntu-704/")

Amazing what "google .dmrc ubuntu" turns up.

It looks like it's not .dmrc that's the problem. It's your home folder.

running this should fix it:

```
sudo chmod 755 /home/darryl
```

If that doesn't fix it, follow the steps on the linked webpage.

---

### Post by dphirschler on 2008-02-08
Thanks.  I went to that website and did the recommended steps.  By the way, the steps were as follows:

```
sudo chown –R [username] /home/[username]

sudo chmod –R 755 /home/[username]

sudo chown [username] $HOME/.dmrc

sudo chmod 644 $home/.dmrc
```

The last line would not work.  Assuming it was because I was already in my home directory, I removed the '$home/' and it worked.  Then I rebooted and the error message was gone.  But then I went to my Windows XP machine and tried to create a directory within that share and it would not allow it.

So then I did this:

```
sudo chmod –R 775 /home/darryl

sudo chmod 644 $home/.dmrc
```

And then I was able to create a directory from the Windows PC.  I copied a file to it, executed the file,and deleted the file and directory.  Then I rebooted the Linux PC and still no error message.  yay!  

But then I noticed could not create a directory from the Windows PC.  :-(  I should probably have paid better attention, because I might have been one directory deeper when I did the first test.  I went into a directory and was able to create one, so I am guessing that was the deal.  So now I need to give myself permission to create directories from the Windows PCs.  I suppose it could be a Samba setting, but I am thinking I need to tweak the permissions on that home folder again.

FWIW, here are the permissions:

```
darryl@darryl-desktop:/home$ ls -l
total 4
drwxrwxr-x 48 darryl darryl 4096 2008-02-08 00:11 darryl
darryl@darryl-desktop:/home$ cd home
bash: cd: home: No such file or directory
darryl@darryl-desktop:/home$ cd darryl
darryl@darryl-desktop:~$ ls -l
total 1596
drwxrwxr-x  2 darryl darryl     4096 2007-09-27 17:24 Desktop
drwxrwxr-x 12 darryl darryl     4096 2008-02-01 08:25 Documents
-rwxrwxr-x  1 darryl darryl      118 2008-02-06 08:48 dph_links.txt
lrwxrwxrwx  1 darryl darryl       26 2007-05-26 17:35 Examples -> /usr/share/example-content
-rwxrwxr-x  1 darryl darryl   277072 2005-04-10 20:53 gxmame_0.35beta2-1_i386.deb
drwxrwxr-x 40 darryl darryl     4096 2008-02-02 00:16 Music
drwxrwxr-x 29 darryl darryl    12288 2008-02-02 17:30 Pictures
drwxrwxr-x  2 darryl darryl     4096 2008-01-29 21:05 Public
-rwxrwxr-x  1 darryl root     199704 2007-06-02 10:37 sdl_1.2.11-2_i386.deb
-rwxrwxr-x  1 darryl darryl     2343 2008-01-31 22:51 smb.conf
drwxrwxr-x  2 darryl nogroup    4096 2008-01-31 22:35 _source code
drwxrwxr-x  2 darryl darryl     4096 2008-01-29 21:05 Templates
drwxrwxr-x  5 darryl darryl     4096 2008-02-05 16:50 _Utilities
drwxrwxr-x  3 darryl darryl     4096 2007-09-20 23:02 utorrent
drwxrwxr-x  2 darryl darryl     4096 2008-01-29 21:05 Videos
drwxrwxr-x  6 darryl darryl     4096 2007-05-30 14:05 Wallpaper
drwxrwxr-x  9 darryl darryl     4096 2007-07-23 04:48 xmame
drwxrwxr-x  5 darryl darryl     4096 2007-06-02 14:27 zsnes_1_51
-rwxrwxr-x  1 darryl darryl  1071712 2007-05-30 19:13 zsnes151src.tar.bz2
darryl@darryl-desktop:~$ 
```

Does anything look out of place?  BTW, the smb.conf file sitting in the home/darryl folderis a backup copy that I put there so that I could see it from my remote PC.


Darryl

---

### Post by ruy_lopez on 2008-02-08
The last line of those commands should be:

```
sudo chmod 644 $HOME/.dmrc
```

$HOME should be capitalised.

As for creating folders from XP, try changing the path to:

smb.conf```
path = /home/darryl
```

All you are doing is removing the trailing slash "/". 

It looks like you are sharing everything *within* your "home/darryl/" folder, but not actually sharing "darryl" itself. Removing the trailing slash "/" will hopefully fix it, so you can create directories at the top level of the share.

---

### Post by dphirschler on 2008-02-11
I fooled with it a lot this weekend and I finally got it figured out.  First of all, much to my dismay the trailing '/' made no difference.  But I checked a few folders and discovered I had writing privileges.  So then I looked at the permissions on those folders.  The difference was the group owner was 'nogroup' instead of darryl.  So then I performed another test.  I went to my Windows PC and created a folder where I could and checked its permissions in Linux.  It had 'nogroup' as its owner.  So I manually set the owner on any folder I wanted writing privileges to 'nogroup'.  And that solved it.  

Now that I think about it, I am not out of the woods yet.  I may have to set the permissions of 'home/darryl' to 'nogroup' so that I can create new folders whenever I want to from Windows.

Anyways, thanks to ruy_lopez and jetsam for helping me out.  Hopefully, this is the end of this thread.


Darryl

---

### Post by ruy_lopez on 2008-02-11
How are you logging in from Windows? Are you using the guest account? You can try adding this to smb.conf

Add it to the settings under [share]

```
force group = darryl
force user = darryl
```

It sounds like the problem stems from how you log in. Did you create a password and user using smbpasswd? 

Since you are using your home for the share, the above settings should iron-out any wrinkles.

Consider setting up an account using smbpasswd for Windows to login from, and then disabling guest logins, for security reasons.

```
sudo smbpasswd -a <windowsusername>
```

Use your Windows account name. The command asks for a password. If you don't use a password for windows, leave that blank. 

Once you've set up smbpasswd, add the Windows username to smb.conf:

```
valid users = darryl <windowsusername>
```

This way you control who can access the share. And when you create a file or folder, it will create it using darryl:darryl as the owner and group, which is what your home folder expects.

Try the first command, to ensure everything works, then think about the others.

Best of luck.

---

### Post by dphirschler on 2008-02-11
I originally had it setup with a username/pw login just to get it working.  Then I modified it to remove that restriction.  So now there is no login at all.  It acts just like any other local folder on a Windows PC.  

Now I wouldn't mind setting up some security on certain folders so that if anyone tried to delete something it would then require a login.  Not sure if this is possible though.  But from what I have read, Samba is mighty powerful, so maybe it is a possibility.  I also wouldn't mind setting up some sort of automatic redundancy/backup as well.  

Needless to say, I have a lot of learning to do.


Darryl

---

