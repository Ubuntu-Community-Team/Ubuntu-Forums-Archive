---
title: "Permissions of files saved into a shared folder."
date: 2010-01-07
forum: New to Ubuntu
---

### Post by scweston on 2010-01-07
Hi all,

I use my desktop pc, running Karmic, like a file server. I have a shared folder, which seems to be accessible by my other computers (all windows machines).

I do occasionally make a document directly on the desktop and save it in to the shared folder to access it on my windows laptop. Unfortunately, at the moment, everytime I do this all the files I save this way appear in the shared folder from the other windows computers, but I'm unable to open the documents or modify them.

The only way I can fully access them is to manually change the permission of the documents I saved so that others can 'read and write'. Is is possible to have files saved in to the shared folder automatically have permissions that enable anybody accessing them from another windows computer to be able to 'read and write' to them.

I hope I explained myself clearly enough, but if that isn't please do ask for more information if you think you can help.

Stephen

---

### Post by Morbius1 on 2010-01-07
Nope, I'm lost. But that's my normal state ;)

Can you post your share definition please. I don't which method you're using to share so post both:

Open **Terminal**
Type **net usershare info**
Type [B]testparm -s
[/B]
This may be a simple fix

---

### Post by Morbius1 on 2010-01-07
I've got to pack it in for the day so let me leave you with this. I looked at your post again and I think I understand the problem. 

One way out of this is to do this. I'm assuming you used nautilus-share to create the share ( Nautilus > Right Click > Sharing Options ):

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

In the [COLOR=Blue][global] [/COLOR]section of smb.conf add the following line:

**forece user = your_server_login_user_name**

Save the file, exit gedit, and back in the Terminal type:

**sudo service samba restart**

When the remote user accesses your folder it will appear to that share to be you. Just so there's no misunderstanding about the force user parameter:

Samba deals with access rights and access permissions.
force user deals with the identity of the remote user after he gets access.

If you set the share to read only and add **force user =**, the remote user will appear to be you but still wont be able to write. If you set the share to read / write and add force user, the remote user will be able to read / write as you.

There is a downside to this. All remote files added will now be owned by you. So if you want to maintain the ownership of the remote user on his saved files, this technique will override it. On the other hand, if you set up your share to allow guest access, you've got a lot of remotely saved files with **ownership = nobody**. All future files remotely added will now be owned by you.

If you've used "Classic Samba" and your share definition is contained in smb.conf itself then add the force user to that share definition. For example:
> 
[sharename]
comment = 
path = /media/drive
public = yes
writable = yes
[COLOR=Blue]force user = morbius1 [/COLOR]I hope this addresses your problem. If not I've rambled far too long :)

---

### Post by scweston on 2010-01-07
Hi Morbious1

Very sorry not to get back to you quicker. I'm impressed by the quick response to my post. I wasn't expecting that, so went off to do other things instead of waiting by my computer.

Anyways, with regard to you first post, here is the output you requested: -

```

stephen@stephen-desktop:~$ net usershare info
[sharedwork]
path=/mymedia/SharedWork
comment=
usershare_acl=Everyone:F,
guest_ok=y

stephen@stephen-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```

I'm just about to attempt the things you suggested in your second post. I think I understand the principles of what you saying. Basically instead of changing the file permissions of the documents I make on the desktop and save to the shared folder, I make it appear as though the windows computer accessing the shared folder is me (aka my user account).

I appreciate your help and will get back to you when I've tried your suggestions.

Stephen

---

### Post by scweston on 2010-01-07
Morbius1,

Thank you! Your **force user = stephen** suggestion seems to have done the trick.

I really appreciate your help it done exactly what I needed. I'm slowly trying to get my head around sharing folders and printers. I'm getting there, albeit, slowly. Next on my list is to sort out sharing my printer. Although, this appears to be an issue in Karmic from many of the posts I've read in this forum.

One thing I didn't get from you posts though, is the way you seemed to imply that there is more than one way to share a folder? What are the two ways? Should I be concerned about which way I use?

Thanks again for your help.

Stephen

---

### Post by Morbius1 on 2010-01-08
> One thing I didn't get from you posts though, is the way you seemed to imply that there is more than one way to share a folder? What are the two ways? Should I be concerned about which way I use?The two ways you can share folders are Nautilus-Share ( or Simple Sharing ) and "Classic Samba". You're using Nautilus-Share BTW.

In Nautilus-Share the share definition ( Read / Write, allow guest access , etc..) are located at /var/lib/samba/usershares. When you do a **net usershare info** you display to the terminal that definition. You access the sharing utility through nautilus and the whole user experience is very "windows-like".

In Classic Samba the share definition is embedded into smb.conf itself. One needs to configure a share either though a separate utility or by editing smb.conf directly.

I don't have a religious affiliation with either method but I think that for the average desktop user, Nautilus-share will take care of most needs. There are however two big advantages in using the classic method. It's universal. It works the same way regardless of what linux you're using or what desktop environment. Nautilus-share requires you use a gnome-based environment so you're limited to gnome itself or XFCE (thunar-share). There may be others - I don't know.

The other advantage of the classic method is that it can do things on a share level. Nautilus-share does things globally. Let's say that I'm the server administrator and I have two users - John and Mary. I want John to have access to one share and Mary to have access to another. Nautilus-share cannot do that. If you create two shares that requires a username/password then John and Mary will have access to both.

As a long time KDE user, when I switched to gnome and found nautilus-share I considered it a gift. Create a share on the fly with a couple of clicks and without restarting the samba service - it's a gift. :D

Sorry you asked ?

---

### Post by bkaplan on 2010-01-10
Just a note of thanks for this thread.  I had the same issue, which was driving me nuts.  This post solved it.  Thanks!!!

As an aside, my Win XP Pro and 9.10 installs handled file permissions correctly from the outset.  When an 8.10 or 9.04 user touched the file, however, the file was locked thereafter until I cleared the lock with chmod.  In any event, this solution fixed the problem for all version users.

Regards,
BK

---

### Post by dmaxel on 2010-01-10
Hahaha wow, this could have helped me a year ago or so. ;)

Since we're on this topic, might I ask a quick question as well? Since forceuser seems to work pretty well, I would like to know if it would also work if you put directory mask=xxxx and create mask=xxxx? Probably 0777 for easiest access if those work as well....

---

### Post by Morbius1 on 2010-01-11
dmaxel,

It probably will work. I tend to seek out simple solutions because , well .. I'm simple minded. Plus I'm kind of "old school" when it comes to permissions so I tend to avoid 777 permission settings. You could I suppose also insert a **force group = plugdev** ( all local users are members of plugdev ) and set permissions to 775. But like I said, this is getting more and more complex so I find it easier to use force user.

Using something other than force user does have one advantage though.
Every time a remote user saves a file into your share with force user, the ownership becomes yours. If you set up your share to require authentication and want to maintain the identity of the remote user so you know who added what file, force user is not the way to go.

---

### Post by dmaxel on 2010-01-11
> **Morbius1 said:**
> dmaxel,

It probably will work. I tend to seek out simple solutions because , well .. I'm simple minded. Plus I'm kind of "old school" when it comes to permissions so I tend to avoid 777 permission settings. You could I suppose also insert a **force group = plugdev** ( all local users are members of plugdev ) and set permissions to 775. But like I said, this is getting more and more complex so I find it easier to use force user.

Using something other than force user does have one advantage though.
Every time a remote user saves a file into your share with force user, the ownership becomes yours. If you set up your share to require authentication and want to maintain the identity of the remote user so you know who added what file, force user is not the way to go.
Ahhh, so for a server that serves multiple users that each have their own area, shared areas, and public areas, **force user** isn't the way to go then. That's probably what I would have needed. Thanks a lot. :)

---

### Post by Morbius1 on 2010-01-12
dmaxel, only if you as the server administrator wants to know the identity of the owner of the saved file. It makes no difference in the "own area" and "public areas" shares. It might come into play in the "shared" areas.

Of course if you have that level of authentication you're not using nautilus-share because there is no such thing as a remote user specific "own area". In Classic samba you can use force user on a per share basis instead of a global basis in smb.conf.

---

