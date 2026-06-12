---
title: "Connecting to Windows Server Shares"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by MikeyDL on 2008-08-04
I've been scanning the message boards for a solution but no luck yet.

It appears that running an ubuntu machine in a Windows Server 2003 domain and accessing password protected shares has some problems.  While I've been able to use nautilus to browse the network it returns 0 (zero) items for password protected shares.

I've tried:

    * smb to the ip .... no luck
    * installing likewise to connect to the domain...still doesn't solve access to the window's authentication share issue.
    * installed Smb4K which sometimes mounts the shares but usually they go out in a minute or so.

Does anybody have any info on different ways to get around this problem?

Thanks

---

### Post by MikeyDL on 2008-08-04
well got some of the bugs worked out in smb4K.  Went into file browser and checked the kerberos authentication.  Was unchecked and that probably caused some authentication issues.  Also put it in SMBFS (which allows the kerberos check to be allowed).  So far (one hour) no problems yet. 

Hope it stays that way.  

Also hope they address this in as a bug fix for nautilus to make it easier to integrate with window's networks.

If anyone has any other tips on how to get better windows domain integration please pass em my way :)

---

### Post by sbrandon on 2008-08-05
Agreed, this has been my stumble as well.  Saw an article last week that showed how to do it using Mac OS X and it was pretty easy. I would love to see a one to three step process that would make this connection - thereby making Ubuntu a viable alternative in the office.  Not sure how Xandos does it but you have to pay for that system.  Could you give a step by step on how you did it?

---

### Post by MikeyDL on 2008-08-05
Sure, 

I really only did two basic things for a "not the best solution but at least it works."

Both applications were installed searching in SPM (package manager).

1.  I installed [COLOR="Red"]Likewise Open[/COLOR] which is supposed to allow you to join to a windows domain.  I did manage to join to my work domain with this but not really sure if it did anything.  

    *   Install:  Just search for "Likewise" in the SPM and install.
    *   Run:  run the app, it should show up here "System - Administration - LikewiseL"

2.  I installed a KDE connect apps called [COLOR="Red"]smb4K[/COLOR].  This app opens a different type network scan browser that lets you browse through network shares, enter login/passwd info for protected shares.

    *  **Install**:  Search for smb4K with SPM and install.
    *  **Run**:  Either in terminal or run app window (Alt + F2) type smb4K to run the basic app.
    *  **Initial Setup**:  The application will have you password a wallet to store all your share password information initially.  
    *  **Browse to Share**:  Hopefully you will be able to see network resources in the browse window.  First you want to rclick on the computer share to check Kerberos ACD authentication.  It may have you provide authentication first first.   You would enter your login/passwrd info for the win domain.  
    *  **Choose Your Share**:  After that every shared folder you click on gets mounted as a share.  You can rclick in the mounted folders in the right pane and then unmount the resource if you mount something you don't want.
    *  **Close the smb4K App**:  After you X (close) the app its really TSR and running as an applet in your gnome panel.  You can open it again later from that point.  

This method at least works.  After you mount the folder with smb4K you can see it in Nautilus and browse the resource from there too.

Here is the link for the original forum note that lead me to this solution:  [http://ubuntuforums.org/showthread.php?t=775199&highlight=windows+2003+server+nautilus+shares&page=2]("http://ubuntuforums.org/showthread.php?t=775199&highlight=windows+2003+server+nautilus+shares&page=2")

I"m still learning the basics here so hope this helps out a bit.

---

### Post by MikeyDL on 2008-08-05
Minor note....

After doing a reboot I needed to restart smb4K and redo the shares.  I"m using this at work and don't normally log or turn off the puter but this could be a minor pain with regards to usability.

---

### Post by dmizer on 2008-08-05
If you don't mind working in the CLI, you can try the second link in my sig.  You may get better performance, and you'll get connected at boot.

---

### Post by cprofitt on 2008-08-05
When you say password protected shares -- could you be more specific...

If you are truly in a 'domain' then you should setup shared to be 'everyone' 'full permission' and then use NTFS rights to narrow down what users can do. There should be no reason to password protect the share on an W2K3 server if it is part of a domain.

I do this in my environment with no issue...

you do need to put your user name in correctly:

domain\username

if you leave off the domain you would be trying to login with a local account which the server likely does not have.

---

### Post by nittybitty on 2008-08-05
it is a ridiculous problem to have, but all ubuntu users have it, at least under gnome.  hard to believe version 8.something of a distribution still doesn't address this problem.  Too bad bc this is one thing that turns people off from linux (at least gnome) and who knows if anyone will ever care enough to address it.  It's a shame.

search for pyneighborhood in your package manager.

[http://pyneighborhood.sourceforge.net/](http://pyneighborhood.sourceforge.net/)

worked great for me, but it pisses me off it took me 4 hours to solve such a simple problem.

---

### Post by Moridin333 on 2008-08-06
Maybe I don't understand but I have no problem connecting all my computers to a password protected ntfs share.  I have to say that this is on a linux server but I believe this should still work.  this line is in fstab

//192.168.1.11/Data /media/Data cifs rw,username= ,password= 0 0

please note that I've removed the username and password

---

### Post by ktrnka on 2008-08-06
I have successfully mounted password protected shares on a windows 2003 domain.

```
sudo mount //servername/sharedfolder -W DOMAINNAME -o username=username /path/to/mountpoint
```

I have found that it wont mount if you have password=password after the username. It will prompt for the password instead. Something related to cifs I think. You can also add -o allow_user so that way it wont only be accessible only to root. If you go that route, you will also need to edit /etc/fuse.conf and remove the comment marker "#" from in front of user_allow_other.

This has worked for me. Hope it helps.

---

### Post by dmizer on 2008-08-06
> **ktrnka said:**
> I have successfully mounted password protected shares on a windows 2003 domain.

```
sudo mount //servername/sharedfolder -W DOMAINNAME -o username=username /path/to/mountpoint
```

I have found that it wont mount if you have password=password after the username. It will prompt for the password instead. Something related to cifs I think. You can also add -o allow_user so that way it wont only be accessible only to root. If you go that route, you will also need to edit /etc/fuse.conf and remove the comment marker "#" from in front of user_allow_other.

This has worked for me. Hope it helps.

Does Hardy make use of Fuse by default instead of the Gnomevfs? Last I remember, it does not.

If not, you'd have to install and configure fuse to work with samba mount.  I also vaguely recall that there can be issues with fuse and samba, but don't quote me on that.

---

### Post by ktrnka on 2008-08-06
> **dmizer said:**
> Does Hardy make use of Fuse by default instead of the Gnomevfs? Last I remember, it does not.

If not, you'd have to install and configure fuse to work with samba mount.  I also vaguely recall that there can be issues with fuse and samba, but don't quote me on that.

Hardy is using GVFS with FUSE. [http://ubuntuforums.org/showthread.php?t=754624]("http://ubuntuforums.org/showthread.php?t=754624") GnomeVFS has been deemed depreciated as of last April. Check the wiki.

I have not had any problems other than simple syntax changes. Example is in my previous post. I had to change my mount command cause it wouldn't take the password if I provided it in the mount command like it had been doing previously.

---

### Post by pwebster25 on 2008-11-30
> **ktrnka said:**
> I have successfully mounted password protected shares on a windows 2003 domain.

```
sudo mount //servername/sharedfolder -W DOMAINNAME -o username=username /path/to/mountpoint
```

I have found that it wont mount if you have password=password after the username. It will prompt for the password instead. Something related to cifs I think. You can also add -o allow_user so that way it wont only be accessible only to root. If you go that route, you will also need to edit /etc/fuse.conf and remove the comment marker "#" from in front of user_allow_other.

This has worked for me. Hope it helps.

Will this work if I need a dynamic mount for a network folder, based on the username.  Can I use a wildcard for the username?  We use likewise-open to authenticate credentials on the network.  We have a bunch of network users on any given machine (we are a school).  Our "server-x" has a folder for each student user on active directory.
So, could I use the following to map each userfolder to mount upon login?  Our domain is MSD.DOMAIN (do I use MSD or MSD.DOMAIN?).

```
sudo mount //server-x/student-files/%U -W MSD -o username=username /home/MSD/%U/Network_Folder
```

---

### Post by pwebster25 on 2008-11-30
> **nittybitty said:**
> search for pyneighborhood in your package manager.

[http://pyneighborhood.sourceforge.net/](http://pyneighborhood.sourceforge.net/)


Can pyneighborhood do dynamic mapping of network shares, based on AD usernames?  We use likewise-open to authenticate in a windows domain.  It looks handy for individual mounts of network resources.

---

