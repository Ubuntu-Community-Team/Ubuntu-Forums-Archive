---
title: "Share Folders on a NTFS Partitioned harddrive"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by longtom on 2009-02-10
Hi,

I'm running a dualboot system with WinXP on one HD and Ubuntu on a second one.  In order for my fileserver as well as other machines to be able to see some of my folders, I'd like to share those.

Ubuntu doesn't take kindly to that idea and gives me the following:

"'net usershare' returned error 255: net usershare add: cannot share path /media/disk/My Documents old/1 exper as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this."

No - I'm still kind of jittery to fiddle arround in files I don't know what they are and do.

A quick runthrough, if at all possible, will be appreciated.

regards

longtom

---

### Post by yeats on 2009-02-10
There are a couple of things you can do here.  One is to change the ownership of the file you're trying to share to yourself, using Alt-F2 or opening a terminal:

```
sudo chown -R *username:username filename*
```

To explain, "chown" means "change owner," the "username:username" is actually "user:group" (as UNIX permissions follow the model of user, group, other) and both will be your own username, and "filename" would be the name of the file/directory you're trying to share.  The "-R" flag makes it recursive (applies to all files and subdirectories in the directory).  You should then be able to share it, since you'll then be the owner.

Oh - and smb.conf is the file that controls Samba, the program that allows Windows machines to interact with Linux machines.  Once you get your bearings, it is a fairly straightforward file to use (though I understand your hesitation :-) ).  Mine looks like this:

```
[global]
        workgroup = WORKGROUP
        server string = SWAN Fileshare
        security = share
        browsable = yes
        hosts allow = 192.168.1.

[Fileshare]
        path = /fileshare
        comment = SWAN Fileshare
        read only = No
        guest ok = Yes
```

Mine allows for a VERY open sharing situation, since I'm behind a strong firewall, so don't just copy it unless you are in a secure situation.  It would be worthwhile to learn about Samba.  A Google search for the book "Using Samba" will bring you to an online copy of the 2003 edition in Google books.

---

### Post by longtom on 2009-02-10
Thank you, chris.

I'll have a go at your suggestions.

lt

---

### Post by yeats on 2009-02-10
> **longtom said:**
> Thank you, chris.

I'll have a go at your suggestions.

lt

Great!  Happy to help.  Oh - and for reference, in my smb.conf file, my network is called SWAN and I named my shared folder "fileshare" and used the Windows Vista default name of WORKGROUP.  Just in case you DO actually use my file as a template, you'll have an idea of what's what.

---

### Post by longtom on 2009-02-10
One more question...(yeah right...)

Search gave me quite a few smb.config files.  Which one is the one I need to change?

I kind of remember the one in the etc driectory.  Could somebody confirm or rectify that?

thanks

lt

---

### Post by yeats on 2009-02-10
The primary config file is /etc/samba/smb.conf.  Almost all of these major config files are in /etc somewhere.  Oh - PLEASE make a backup copy before you edit anything! :-)

---

### Post by longtom on 2009-02-10
Good idea, that one with the backup.  

Haven't destroyed anything yet so.  Got it going as well.

Thanks again!

longtom

---

### Post by jonandrews on 2009-02-10
Have a look a my overview & step-by-step guides to file sharing between Windows & Ubuntu pc's:

[www.europe.eclipse.co.uk/Ubuntu](www.europe.eclipse.co.uk/Ubuntu)

---

### Post by longtom on 2009-02-10
> **jonandrews said:**
> Have a look a my overview & step-by-step guides to file sharing between Windows & Ubuntu pc's:

[www.europe.eclipse.co.uk/Ubuntu](www.europe.eclipse.co.uk/Ubuntu)

Very useful - thank you!

lt

---

