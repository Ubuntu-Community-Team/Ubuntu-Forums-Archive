---
title: "Ubuntu, SMBFS/CIFS and a QNAP TS-209"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by AlwaysLearning on 2007-12-16
Hi all,

I've been thrashing about on this for a couple of days now reading all the HOWTO posts on SMBFS and CIFS and I'm not making much headway. Have done the whole shebang with sudo apt-get install smbfs, etc, etc and am basically down to two /etc/fstab solutions, neither of which really work satisfactorily.

Local OS: Ubuntu 7.04 - Feisty Fawn
Remote server: QNAP TS-209 (unfortunately not the TS-209 Pro which also supports NFS)

/etc/fstab solution 1: Using SMBFS
```
//192.168.1.23/USERNAME    /media/TS209A-USERNAME    smbfs  cifsexec,credentials=/root/.credentials,iocharset=utf8,uid=USERNAME,gid=USERNAME
//192.168.1.23/Public      /media/TS209A-Public      smbfs  cifsexec,credentials=/root/.credentials,iocharset=utf8,uid=USERNAME,gid=USERNAME
//192.168.1.23/Qdownload   /media/TS209A-Qdownload   smbfs  cifsexec,credentials=/root/.credentials,iocharset=utf8,uid=USERNAME,gid=USERNAME
//192.168.1.23/Qmultimedia /media/TS209A-Qmultimedia smbfs  cifsexec,credentials=/root/.credentials,iocharset=utf8,uid=USERNAME,gid=USERNAME
//192.168.1.23/Qusb        /media/TS209A-Qusb        smbfs  cifsexec,credentials=/root/.credentials,iocharset=utf8,uid=USERNAME,gid=USERNAME
//192.168.1.23/Qweb        /media/TS209A-Qweb        smbfs  cifsexec,credentials=/root/.credentials,iocharset=utf8,uid=USERNAME,gid=USERNAME
```

Pros:
[LIST]
[*]Shares connect successfully.
[*]User specified in /root/.credentials can create, read, update, delete according to permissions set on the TS-209.
[*]Using the /media tree causes the shares appear in the Nautilus Places.
[/LIST]

Cons:
[LIST]
[*]This is system-wide, so any locally logged-on user is using the shares with the same set of remote credentials.
[*]Everyone says SMBFS is deprecated and I should be using CIFS.
[*]SMBFS likes to throw its little request timed out errors periodically as below. Interestingly this seems to be alleviated by using the TS-209's admin user credentials - I managed to upload 100+ gigs of files without a problem while testing with those creds.
[/LIST]

/var/log/syslog extract:
```
Dec 16 23:30:50 LOCALMACHINE kernel: [17185.914683] smb_add_request: request [ffff810042faa540, mid=22357] timed out!
Dec 16 23:31:20 LOCALMACHINE kernel: [17197.898492] smb_add_request: request [ffff810042faa540, mid=22358] timed out!
Dec 16 23:31:20 LOCALMACHINE kernel: [17197.898502] smb_file_aio_read: SOME_FILE validation failed, error=-5
Dec 16 23:31:57 LOCALMACHINE kernel: [17212.674952] smb_add_request: request [ffff810042faa0c0, mid=22359] timed out!
Dec 16 23:32:27 LOCALMACHINE kernel: [17224.679526] smb_add_request: request [ffff810042faa0c0, mid=22360] timed out!
```

/etc/fstab solution 2: Using CIFS
```
//192.168.1.23/USERNAME    /media/TS209A-USERNAME    cifs  credentials=/root/.credentials,rw,iocharset=utf8,uid=USERNAME,gid=USERNAME,file_mode=0777,dir_mode=0777
//192.168.1.23/Public      /media/TS209A-Public      cifs  credentials=/root/.credentials,rw,iocharset=utf8,uid=USERNAME,gid=USERNAME,file_mode=0777,dir_mode=0777
//192.168.1.23/Qdownload   /media/TS209A-Qdownload   cifs  credentials=/root/.credentials,rw,iocharset=utf8,uid=USERNAME,gid=USERNAME,file_mode=0777,dir_mode=0777
//192.168.1.23/Qmultimedia /media/TS209A-Qmultimedia cifs  credentials=/root/.credentials,rw,iocharset=utf8,uid=USERNAME,gid=USERNAME,file_mode=0777,dir_mode=0777
//192.168.1.23/Qusb        /media/TS209A-Qusb        cifs  credentials=/root/.credentials,rw,iocharset=utf8,uid=USERNAME,gid=USERNAME,file_mode=0777,dir_mode=0777
//192.168.1.23/Qweb        /media/TS209A-Qweb        cifs  credentials=/root/.credentials,rw,iocharset=utf8,uid=USERNAME,gid=USERNAME,file_mode=0777,dir_mode=0777
```

Pros:[LIST]
[*]Shares connect successfully.
[*]Using the /media tree causes the shares appear in the Nautilus Places.
[/LIST]

Cons:
[LIST]
[*]This is system-wide, so any locally logged-on user is using the shares with the same set of remote credentials.
[*]Only top-level items can be created in each share. By this, I mean if you create a folder it gets the little orange padlock icon on it and though you can delete and rename the folder you can't create anything inside it.
[/LIST]

So, I guess my three questions are:
[LIST=1]
[*]What am I doing wrong with CIFS?
[*]Why, when using CIFS, am I restricted to top-level operations, even in the Public share (which is set for Everyone -> FULL CONTROL on the TS-209)?
[*]How can I get the shares to mount with a different set of credentials for each logged-on user? It's not as simple as specifying credentials=~/.credentials since the mount is running under the root user.
[/LIST]

Thanks in advance for any help,
AlwaysLearning.

---

### Post by AlwaysLearning on 2007-12-18
Just so there's a little more information, here's what the ls -la listing for a share looks like after I create a new folder (Untitled) when connected with CIFS:
```
drwxrwxrwx  4 user  users    0 2007-12-18 22:27 .
drwxr-xr-x 12 root  root  4096 2007-12-16 23:16 ..
drwxrwxrwx  6   500 users    0 2007-12-16 23:56 iTunes
drwxr-xr-x  2   500 users    0 2007-12-18 22:27 Untitled
```
The iTunes folder was created when connected with SMBFS.

It also doesn't matter if I chown/chgrp the /media/TS* folders to either root or the local user, or whether I connect to the NAS with the remote admin/user credentials, the same behaviour and directory mask is exhibited. The remote user has "Full Control" of this share, the same as the "Administrators" group.

Thanks,
AlwaysLearning.

---

### Post by AlwaysLearning on 2007-12-18
Success! (At least it seems so for now.)

My interpretation may be wrong, but after spending time trying to absorb the output of **man mount.cifs** I thought I'd try taking permissions and uid/gid control completely out of the hands of Ubuntu and leave it up to the NAS to control. Here's what wound-up being in my /etc/fstab file:
```
//ts209a/USERNAME    /media/TS209A-USERNAME    cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw
//ts209a/Public      /media/TS209A-Public      cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw
//ts209a/Qdownload   /media/TS209A-Qdownload   cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw
//ts209a/Qmultimedia /media/TS209A-Qmultimedia cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw
//ts209a/Qusb        /media/TS209A-Qusb        cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw
//ts209a/Qweb        /media/TS209A-Qweb        cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw
```

It might work with less options, but it's working for me now so I'm not going to mess with it any further. Hopefully this will help other QNAP owners out there.

Note that I'm using the NAS's name now instead of its IP. That's because I've included **wins** on the **hosts** line of **/etc/nsswitch.conf** and also done a **sudo apt-get install winbind**. It didn't help with the permissions problem, but at least I don't need to track the NAS's IP any more.

Good luck,
AlwaysLearning.

---

### Post by trondjac on 2008-03-20
> **AlwaysLearning said:**
> Success! (At least it seems so for now.)

My interpretation may be wrong, but after spending time trying to absorb the output of **man mount.cifs** I thought I'd try taking permissions and uid/gid control completely out of the hands of Ubuntu and leave it up to the NAS to control. Here's what wound-up being in my /etc/fstab file:
```
//ts209a/USERNAME    /media/TS209A-USERNAME    cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw
//ts209a/Public      /media/TS209A-Public      cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw
//ts209a/Qdownload   /media/TS209A-Qdownload   cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw
//ts209a/Qmultimedia /media/TS209A-Qmultimedia cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw
//ts209a/Qusb        /media/TS209A-Qusb        cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw
//ts209a/Qweb        /media/TS209A-Qweb        cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw
```

It might work with less options, but it's working for me now so I'm not going to mess with it any further. Hopefully this will help other QNAP owners out there.

Note that I'm using the NAS's name now instead of its IP. That's because I've included **wins** on the **hosts** line of **/etc/nsswitch.conf** and also done a **sudo apt-get install winbind**. It didn't help with the permissions problem, but at least I don't need to track the NAS's IP any more.

Good luck,
AlwaysLearning.

THANK YOU!
I Have a QNAP 201, and mounted the dirs with cifs, but I have got the lock icons on varius of files. Now you solved the problem for me :-)
I'm new to linux you see, so I couldn't fi it out on my own... hehe

---

### Post by Eiríkr on 2008-03-20
Hey there AlwaysLearning --

I'm confused by a few things in your post.  

> **AlwaysLearning said:**
> Remote server: QNAP TS-209 (unfortunately not the TS-209 Pro which also supports NFS)

Just looking over [the online info on the company website](http://www.qnap.com/pro_detail_software.asp?p_id=83), it looks like the non-Pro version uses a Linux embedded OS and does allow SSH logins, in which case you could ostensibly install NFS yourself, no?  

**Pros:**
**SMBFS / CIFS:** [COLOR="purple"]Both connect successfully[/COLOR] -- 
Great, but bear in mind that SMBFS no longer seems to work in Gutsy 7.10.

**SMBFS:** [COLOR="purple"]User specified in /root/.credentials can create, read, update, delete according to permissions set on the TS-209.[/COLOR] --
This shouldn't be any different for your CIFS mounts, since those also specify the same [font=courier]credentials[/font] file...?

**SMBFS / CIFS:** [COLOR="purple"]Using the /media tree causes the shares appear in the Nautilus Places.[/COLOR] --
I don't think this has anything to do with Samba, as pretty much anything mounted / linked to within the /media tree should show up there in Nautilus.  But for that matter, it's possible to add arbitrary directories to the Places sidebar, so there's no real need to confine Samba mounts to /media.  You could rework the shares to mount within the user's /home tree instead if you wanted.

**Cons:**
**SMBFS / CIFS:** [COLOR="purple"]This is system-wide, so any locally logged-on user is using the shares with the same set of remote credentials.[/COLOR] --
If this is an issue, why not set up the fstab entries to allow users to mount the shares, and require each to provide their own credentials at mount time?  And I'm curious -- this fstab setup doesn't look like it's automounting on boot, so you must be mounting the shares later on.  Why not have each user do so then?  

**SMBFS:** [COLOR="purple"]Everyone says SMBFS is deprecated and I should be using CIFS.[/COLOR] --
See point above -- SMBFS no longer works in Ubuntu 7.10 / Samba 3.026.  

**SMBFS:** [COLOR="purple"]SMBFS likes to throw its little request timed out errors periodically as below. Interestingly this seems to be alleviated by using the TS-209's admin user credentials - I managed to upload 100+ gigs of files without a problem while testing with those creds.[/COLOR] --
Might this be related to filesystem permissions on the TS-209 side?

**CIFS:** [COLOR="purple"]Only top-level items can be created in each share. By this, I mean if you create a folder it gets the little orange padlock icon on it and though you can delete and rename the folder you can't create anything inside it.[/COLOR] --
This is a complex issue.  Let's look at the mount options you specify, and [what the man page has to say about them](http://us1.samba.org/samba/docs/man/manpages-3/mount.cifs.8.html#id2481203).

**credentials** -- 
> credentials=filename

    specifies a file that contains a username and/or password. The format of the file is:

    		[font=courier]username=value
    		password=value[/font]

    This is preferred over having passwords in plaintext in a shared file, such as /etc/fstab. Be sure to protect any credentials file properly.

So the share is mounted with the username and password specified.  And since the share server in this case is a proper Linux Samba server, we can be pretty sure that permissions will work in a Unixy way.  

**rw, iocharset=utf8** --
Pretty straightforward.

**uid=USERNAME, gid=USERNAME** --
> uid=arg

    sets the uid that will own all files on the mounted filesystem. It may be specified as either a username or a numeric uid. **For mounts to servers which do support the CIFS Unix extensions, such as a properly configured Samba server, the server provides the uid, gid and mode so this parameter should not be specified unless the server and client uid and gid numbering differ. If the server and client are in the same domain (e.g. running winbind or nss_ldap) and the server supports the Unix Extensions then the uid and gid can be retrieved from the server (and uid and gid would not have to be specifed on the mount.** For servers which do not support the CIFS Unix extensions, the default uid (and gid) returned on lookup of existing files will be the uid (gid) of the person who executed the mount (root, except when mount.cifs is configured setuid for user mounts) unless the "uid=" (gid) mount option is specified. For the uid (gid) of newly created files and directories, ie files created since the last mount of the server share, the expected uid (gid) is cached as long as the inode remains in memory on the client. Also note that permission checks (authorization checks) on accesses to a file occur at the server, but there are cases in which an administrator may want to restrict at the client as well. For those servers which do not report a uid/gid owner (such as Windows), permissions can also be checked at the client, and a crude form of client side permission checking can be enabled by specifying file_mode and dir_mode on the client. Note that the mount.cifs helper must be at version 1.10 or higher to support specifying the uid (or gid) in non-numeric form. 
    
gid=arg

    sets the gid that will own all files on the mounted filesystem. It may be specified as either a groupname or a numeric gid. For other considerations see the description of uid above. 

Note the two bolded sentence above.  Since your Samba server, the QNAP TS-209, should ostensibly meet this description of "a properly configured Samba server", there should be no need to use these mount options provided you've properly set up users and groups on the server to match the ones you're using on the client.

**file_mode=0777, dir_mode=0777** --
> file_mode=arg

    **If the server does not support the CIFS Unix extensions** this overrides the default file mode.
    
dir_mode=arg

    **If the server does not support the CIFS Unix extensions** this overrides the default mode for directories. 

These bolded sections, combined with what we saw above for the [font=courier]uid[/font] and [font=courier]gid[/font] options, should make it clear that these mount options are unnecessary if you've properly set up users and groups on the server to match those on the client.

-----

Now to answer your specific questions:

[LIST=1]
[*][COLOR="purple"]What am I doing wrong with CIFS?[/COLOR] -- 
I think we've covered this in the analysis of the mount options.
[*][COLOR="purple"]Why, when using CIFS, am I restricted to top-level operations, even in the Public share (which is set for Everyone -> FULL CONTROL on the TS-209)?[/COLOR] --
Again, the mount options analysis should explain this.  I'm very curious, though -- the TS-209 is ostensibly running Linux, so why do you describe the Public share permissions here in Windows terms?  There is no "Everyone" or "FULL CONTROL" on Linux systems.  
[*][COLOR="purple"]How can I get the shares to mount with a different set of credentials for each logged-on user? It's not as simple as specifying credentials=~/.credentials since the mount is running under the root user.[/COLOR] --
Why are you running the mount under the root user?  If there's no compelling need to have it this way, change it.  The *only* way I'm aware of to use different credentials for each user is to have each user handle their own mounts, and for there to be no credentials specified in fstab (the server will prompt for these at mount time).
[/LIST]

I'd suggest reworking fstab to allow users to mount.  Ditch the credentials mount option, and have each user supply their own at mount time.  Ditch the uid, gid, file_mode, and dir_mode options and let the Samba server manage those properly based on the permissions of the user / group that's accessing the server.  This might require you to SSH into your server and make sure that the proper users and groups exist, with the same user IDs and group IDs.  Let us know if you need any help with how to do this.

If none of that works, SSH into your server and post us a copy of your server's /etc/samba/smb.conf file.  

HTH,

Eirikr

---

