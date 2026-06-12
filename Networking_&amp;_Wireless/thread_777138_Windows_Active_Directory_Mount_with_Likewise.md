---
title: "Windows Active Directory Mount with Likewise"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by meadmarc on 2008-05-01
I was amazed yesterday when I was finally able to use Likewise to authenticate an Ubuntu workstation to our school's Windows server.  For the first time since I began using Linux, I now have a compelling reason to present to my supervisors in favor of switching to Ubuntu for at least some of our clients.

Two problem remain:

Does anyone know how I can mount a drive based on the current user's name and password?  The drive location is \\kas\wc0029\username, where username is the name of the current user.  I've mounted windows shares before, but I have always had to make a file with username and password in it, and that's not going to work here with over a thousand users.  I need something that will take the current user's name and password, and mount accordingly.

Is there any way to keep the user from browsing the network?  Samba is so nice, showing everyone everything.  Sure, the shares are locked, but with XP, the kids can't even SEE them! The temptation to map the network and start hacking is strong;  I'd like to open up the share above, and lock the rest of the network down for non-Admin users.

Thanks in advance!

Marcus

---

### Post by ic3000 on 2008-06-27
Hi,

I have the a similar situation here for an non lucrative association... Until a few days ago my colegues and i use windows but im using linux at home for about 2 years now and i promoting some possible changes on the desktop side of our network.

I can use likewise open for conect some testing ubuntu desktop clients for our windows 2003 server AD(we need this server because some administrative application dont support linux) but i have to show my colegues how to connect to the user document folder that is stored on the same server. Because we are alot of users and alot of desktops on the network im trying to find a way to make this connection automaticly started at each user login.

Do you think that this is possible?

Thanks in advance!

---

### Post by MikeEvans on 2009-05-13
I realize this is an old thread but the solution to your issue is described here:
[URL="https://help.ubuntu.com/9.04/serverguide/C/samba-ad-integration.html"]
https://help.ubuntu.com/9.04/serverguide/C/samba-ad-integration.html[/URL]

Once your setup you should be able to mount any windows AD share with your current logon credentials.  After you get it working you would add some mounting instructions to your /etc/fstab file so it auto mounts every time.

---

### Post by horned0wl on 2009-05-29
> **meadmarc said:**
> I was amazed yesterday when I was finally able to use Likewise to authenticate an Ubuntu workstation to our school's Windows server.  For the first time since I began using Linux, I now have a compelling reason to present to my supervisors in favor of switching to Ubuntu for at least some of our clients.

Two problem remain:

Does anyone know how I can mount a drive based on the current user's name and password?  The drive location is \\kas\wc0029\username, where username is the name of the current user.  I've mounted windows shares before, but I have always had to make a file with username and password in it, and that's not going to work here with over a thousand users.  I need something that will take the current user's name and password, and mount accordingly.

Is there any way to keep the user from browsing the network?  Samba is so nice, showing everyone everything.  Sure, the shares are locked, but with XP, the kids can't even SEE them! The temptation to map the network and start hacking is strong;  I'd like to open up the share above, and lock the rest of the network down for non-Admin users.

Thanks in advance!

Marcus

I have roughly the same problem from a different angle, in that I'm trying to mount a common or "all users" folder so that folk logging into AD through the Ubuntu box can start with the same desktop and basic common apps.  Any thoughts?

Cheers;
Ed

---

### Post by Stuart42 on 2009-05-29
For setting up a sort of 'default profile', this thread has the answer: [http://ubuntuforums.org/showthread.php?t=859002](http://ubuntuforums.org/showthread.php?t=859002)

A simple bash script can handle the mounting.
It's just a matter of creating a mount point, and mounting it based on the username. Set this script to run when users login, and you'll be set.

I've been working on login scripts for our OS X and Linux clients recently, and as long as you don't need to check group membership before mounting it's simple.

To paraphrase some of our code...

#!/bin/bash

mkdir 'Desktop/Home Folder'
mount -t smbfs //windowsserver/sharename/$USER 'Desktop/Home Folder'

This of course assumes that the $USER environmental variable will be in the form of username, without DOMAIN\username, however it can be stripped out if you find DOMAIN\ preceeding it. No passwords needed because it will use the kerberos ticket given during login, just like Windows.

I'll try and post more tips as I discover them :-)

EDIT: mount.cifs (what smbfs now points to) doesn't seem to actually handle kerberos tickets in  Jaunty. Looking for a fix...
EDIT: It's so easy, just use mount -t cifs //server/share /mountpoint -o "user=username"

---

### Post by mbeierl on 2009-06-11
My computer is part of the domain, and I can log in using SSH as DOMAIN\myaccount, but whenever I try to mount a share from the PDC itself, I am still always prompted for a password.  I am completely stumped - why?

```

DOMAIN\myaccount@pc1:~$ mount.cifs //domain-pdc/Public test/
Password: 
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

---

### Post by mweichert on 2009-06-12
I think you're having the same issue as I've been having. 

[http://ubuntuforums.org/showthread.php?t=1178484&highlight=cifs+jaunty](http://ubuntuforums.org/showthread.php?t=1178484&highlight=cifs+jaunty)

I think it's an upstream bug in debian sid. Please let me know if find a solution, however.

---

### Post by mbeierl on 2009-06-12
But I wish I knew what Stuart42 did that made it "so easy" that the simple mount command worked for him after all...

---

### Post by jmeckert on 2009-06-23
I'm new to this forum, but have been trying to make the exact same thing work, and this seems to resolve the problem:

mount.cifs //servername.fqdn/sharename /mount/point -o sec=krb5

Ubuntu Jaunty amd64, all of the latest updates from the repositories.

I was running Hardy but had some odd authentication and timeout issues when testing SSH with Active Directory Likewise accounts.  Upgraded to Jaunty, but couldn't get this to work without storing the passwords in a file, plaintext, obviously not acceptable from a security perspective and more admin headache.

Was reading tonight, came across this:
[http://us3.samba.org/samba/history/samba-3.0.34.html](http://us3.samba.org/samba/history/samba-3.0.34.html)
mentions "Don't prompt for password on krb5 mounts in mount.cifs"

Took a VMware snapshot of the box, compiled and installed 3.0.x source version, tested, same thing, asked for password.  Looked at the parameters again, had previously tried osec=krb5 where it should have been -o sec=krb5, after reading that in another forum.  This worked and mounted the share without prompting for a password.
I reverted to an old snapshot, tested the command line syntax as above, and it worked.

Very cool -- was trying to get an SSH front-end to our Windows file servers for some time now to allow seamless remote access.

---

### Post by keenears on 2009-09-16
Well, probably I can set some shares to be mounted by these instructions, but what if I need it to be simplier? like I`m browsing shares in my AD with Dolphin or Konqueror (using KDE 4.3.1) and just clicking whenever I need ? probably I can set these file managers to use scripts with smbmount to use these shares or maybe there`s a better solution? right now it keeps asking the password.

EDIT: I`ve found that entering the user name and password in System Parameters/Shared folders makes it work. Howver, it`s not exactly what I`ve needed. I need share mounted to work with documents in OpenOffice. If I open a document from the share in Dolphin, it gets copied to temp dir and the copy will never be copied back.

---

### Post by danboid on 2009-09-22
I'm another school IT tech who would dearly love to get a a few Ubuntu/Linux boxes on our network. I was delighted at how easy it was to get the authentication with our w2k3 working with Likewise but now I need to get auto-mounting of users AD network home folders working before I can go any further.

I'm going to be sticking with GDM and GNOME and I would like it so that when the user clicks on Places/Home they will be took to their AD network home folder share. I've read a few threads now on how to achieve this but amazingly they all seem to neglect to mention exactly where I'm supposed to place the mount command which should be run immediately after the user has logged in. From having a quick read of the GDM docs my guess is that it should be placed in

```
/etc/gdm/PostLogin/Default
```

and that file should be 'chmod +x''d. I've tried the example mount command above but I can't see any of them working without prompting for a password so after reading the mount.cifs man page I decided that my script will prob need to look something like this:

```
mkdir /home/$USER
mount.cifs //192.168.0.3/student/$USER /home/$USER -o sec=krb5 -o user=$USER -o password=$PASSWD

```

I placed that under /etc/gdm/PostLogin/Default but I know its not being run as the /home/$USER dir isn't being created after logging in.

All tips much appreciated!

---

### Post by mweichert on 2009-09-22
Rather than create your own post-login mount mechanism, look at pam_mount:

[http://pam-mount.sourceforge.net/](http://pam-mount.sourceforge.net/)

---

### Post by mbeierl on 2009-09-22
I have successfully done the pam-mount thing by putting the following into the pam_mount.conf.xml file:

```

<volume options="user=%(USER),domain=DOMAIN,setuids,acl"
        fstype="cifs"
        server="my-pdc"
        path="home/%(DOMAIN_USER)"
        mountpoint="/home/DOMAIN/%(DOMAIN_USER)"
/>

```

However, periodically I get permission denied (code 13) when the user logs in, and the mount then fails.

Secondly, it would appear that Samba is still not mature enough to be used for this as all the files presented with the exact same permissions and ownership, regardless of what the actual ACLs are on the Windows Server - which borders on being useless as far as security goes :(

---

### Post by danboid on 2009-09-22
Hi mweichert and mbeierl - thanks for your quick responses!

mbeierl- I backed up my old /etc/security/pam_mount.conf.xml and replaced it with your code, albeit slightly modified so mine looks like this now:

```
<volume options="user=%(USER),domain=SERVER,setuids,acl"
        fstype="cifs"
        server="SERVER"
        path="home/%(DOMAIN_USER)"
        mountpoint="/home/SERVER/%(DOMAIN_USER)"
/>
```

Maybe I was meant to append something like that to the default config as I did that and rebooted but there was no sign of the network drive when I logged onto the domain. I've got libpam-mount, libpam-modules, libpam-runtime, libpam0g, libpam-krb5, libpam-gnome-keyring and libpam-ck-connector installed - might I need anything else or have I just configured it wrong? SERVER(.int) is the name of my domain btw.

Please be verbose as possible in your responses so laymen like me can understand and I won't have to bug you as much ;)

---

### Post by mbeierl on 2009-09-22
Right - the options to the pam.d modules:

Somewhere towards the bottom of /etc/pam.d/common-auth:
```

auth    optional                        pam_mount.so

```
and then BEFORE the "sufficient" line for pam_lsass in /etc/pam.d/common-session add:
```

session optional        pam_mount.so 

```

---

### Post by hostile on 2009-12-15
Sorry to bring up an old thread, but I too cannot mount remote directories using pam_mount and Likewise Open on Ubuntu 9.04. I have tried everything in this thread, as well as many, many others.

I have spent nearly two weeks trying to get this to work, but have been unsuccessful.

From dmesg: "CIFS VFS: cifs_mount failed w/return code = -13"

Here is what I have added to my pam_mount.conf.xml:

```


<debug enable="1" />
<mkmountpoint enable="1" remove="true" />
<volume
        options="user=%(USER),domain=DOMAIN,setuids,acl"
        fstype="cifs"
        server="server_name"
        path="%(DOMAIN_USER)"
        mountpoint="~/home"
/>

```

Note: "~/home" is actually "/home/<DOMAIN>/<USER>/home"

pam common-auth:

```

auth    [success=4 default=ignore]      pam_krb5.so     minimum_uid=1000
auth    [success=3 default=ignore]      pam_unix.so     nullok_secure try_first_pass
auth    [success=2 default=ignore]      pam_lsass.so    try_first_pass
auth    [success=1 default=ignore]      pam_ldap.so     use_first_pass
auth    requisite                       pam_deny.so
auth    required                        pam_permit.so
auth    required                        pam_mount.so

```

pam common-session:

```

session [default=1]     pam_permit.so
session requisite       pam_deny.so
session required        pam_permit.so
session optional        pam_krb5.so minimum_uid=1000
session required        pam_unix.so
session optional        pam_mount.so
session sufficient      pam_lsass.so
session optional        pam_ldap.so
session optional        pam_ck_connector.so nox11

```


What I think is happening is that the pam_mount.conf.xml file isnt even being parsed.

I say this b/c I am getting no debugging information, and second to that, the mount point dir is not being created, which is explicitly detailed in the file.

I also seem to be having a kerberos issue, b/c if I issue "klist <username>" from the command line, I am returned with klist: No credentials cache found (ticket cache FILE:<username>).

If anyone has any insight into this, it would be greatly appreciated as we would like to have this up for the beginning of the new year when the new semester starts.

Thanks.

---

### Post by mbeierl on 2009-12-15
I frequently get the error -13 as well.  I sent it off to Gerald Carter and the crew at Likewise, but have not heard back.  I'll try pinging them again.

---

### Post by hostile on 2009-12-15
> **mbeierl said:**
> I frequently get the error -13 as well.  I sent it off to Gerald Carter and the crew at Likewise, but have not heard back.  I'll try pinging them again.


That would be great.

I should be more explicit, in that mounting of the remote share *always* fails with this error.

I can never successfully mount the remote drive.

Does 9.04 even support passing kernel-level Kerberos to CIFS?

We would desperately like to get AD integration working, and if we cannot get Likewise to work within the next two weeks, we will most likely abandon the project, b/c mounting a simple share is taking far too much time to accomplish. :(

Thanks for the reply and the help, though.

I look forward to hearing if they have anything to say.

---

### Post by pwebster25 on 2010-03-08
Did any of you get it to work? I also would like to setup a script upon logon to automount home directories on a Windows share to mount when various domain users login.  My clients are Ubuntu 9.10 and they are on an Active Directory domain.  They are all properly joined by likewise open.  Users can navigate to their windows share in the "Network" under places.  However, the pathway to this is pretty complicated and is not doable for each user.  So, authentication is working.  It is just the automounting that I'm stuck on.

I'd like it to show up as a folder under their home directory or as a folder or drive on their desktop.

---

### Post by hostile on 2010-03-09
> **pwebster25 said:**
> Did any of you get it to work? I also would like to setup a script upon logon to automount home directories on a Windows share to mount when various domain users login.  My clients are Ubuntu 9.10 and they are on an Active Directory domain.  They are all properly joined by likewise open.  Users can navigate to their windows share in the "Network" under places.  However, the pathway to this is pretty complicated and is not doable for each user.  So, authentication is working.  It is just the automounting that I'm stuck on.

I'd like it to show up as a folder under their home directory or as a folder or drive on their desktop.


Nope.

I purchased a support contract with LikeWise, submitted a ticket, and all they did was shove some crap white paper back in my face which actually has little to do with this issue.

I have two labs of 70 to 100 computers in each lab, with the possibility of other faculties falling in line once this hurdle is cleared, so if this is what their support is like, I'll take my money elsewhere.

If I do come up with anything though, I will post back.

---

### Post by Likewise Username on 2010-07-19
People have found success in using pam_mount with Likewise for automounting network home directories at user login time.

Here are segments of the pam configuration files needed:

common-auth:
> # here are the per-package modules (the "Primary" block)
auth    [success=3 default=ignore]    pam_unix.so nullok_secure try_first_pass
# here's the fallback if no module succeeds
auth    required        /lib/security/pam_lsass.so try_first_pass
auth    sufficient      pam_mount.so
auth    requisite    pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required    pam_permit.socommon-account
> # here are the per-package modules (the "Primary" block)
account    [success=3 new_authtok_reqd=done default=ignore]    pam_unix.so 
# here's the fallback if no module succeeds
account    required            /lib/security/pam_lsass.so            unknown_ok
account    sufficient            /lib/security/pam_lsass.so
account    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account    required            pam_permit.socommon-pammount
> # Include this file in every /etc/pam.d/SERVICE you use for login:
# [...]
# @include common-auth
# @include common-session
# [...]
# # added for libpam-mount
# @include common-pammount
#
# Make sure that the common-auth and common-session includes are
# above the common-pammount include (just as in the example above).

# replace "optional" with "required" if a user must mount the specified
# volumes, for example the home directory

# make sure that there is no PAM module loaded with a "sufficient"
# priority before these entries, else the pam_mount module is not
# executed

# for configuration details about different login programs see
# /usr/share/doc/libpam-mount/README.Debian.gz

auth       optional   pam_mount.so use_first_pass
session    optional   pam_mount.socommon-session
> # here are the per-package modules (the "Primary" block)
session    [default=1]            pam_permit.so
# here's the fallback if no module succeeds
session    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
session    required    pam_unix.so 
session    optional    pam_mount.so 
session    optional            pam_ck_connector.so nox11
# end of pam-auth-update config
Here is pam_mount.conf.xml
> <?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<!--
    See pam_mount.conf(5) for a description.
-->

<pam_mount>


        <!-- Volume definitions -->


        <!-- pam_mount parameters: General tunables -->

<debug enable="1" />
<!-- <luserconf name=".pam_mount.conf.xml" /> -->

<!-- Note that commenting out mntoptions will give you the defaults.
     You will need to explicitly initialize it with the empty string
     to reset the defaults to nothing. -->
<mntoptions allow="nosuid,nodev,loop,encryption,fsck,nonempty,allow_root,allow_other" />
<!--
<mntoptions deny="suid,dev" />
<mntoptions allow="*" />
<mntoptions deny="*" />
-->
<mntoptions require="nosuid,nodev" />
<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path>

<logout wait="0" hup="0" term="0" kill="0" />


        <!-- pam_mount parameters: Volume-related -->

<mkmountpoint enable="1" remove="true" />

<volume user="*" mountpoint="/home/%(USER)" path="homes/%(USER)" server="lwdemodc02" fstype="cifs" options="nodev,nosuid,uid=%(USERUID),gid=%(USERGID),file_mode=0600,dir_mode=0700" />

</pam_mount>

---

### Post by ic3000 on 2011-11-13
Hi to all,

I'm trying to use the new Ubuntu 11.10 with pam_mount with a setup similar to this.

I'm using this setup on a school where i want to integrate more *nix machines to our network. Windows is only required on some classrooms because we have apps that dont run on linux but on all the others we would like to have linux.

I'm using 2 classrooms for trying to find a simple and efective way to accouplish this... One is using Likewise and the other is using Centrify Express that is now on the partners repository of oneiric...

With the 2 i was able to login on our AD domain and get libpam_mount to mount user directories...

With login there is no problems, but pam_mount is only possible if the user as already loged in from a windows machine who creates the user folders, but when the first login is made from a *nix machine pam_mount is unable to create the first folder on the server so it can mount it localy...

As anyone found a solution for this?

Thanks once again!

---

### Post by pwebster25 on 2011-11-13
> **ic3000 said:**
> With the 2 i was able to login on our AD domain and get libpam_mount to mount user directories...

With login there is no problems, but pam_mount is only possible if the user as already loged in from a windows machine who creates the user folders, but when the first login is made from a *nix machine pam_mount is unable to create the first folder on the server so it can mount it localy..

I don't have a solution for you but I'd be happy to help you work on it a little, as I would like to solve the same problem.  

A couple questions:
[LIST]
[*]Which one worked (the login), LWO or Centrify or both?
[*]What did you do to get the window's share mounted?
[*]What kind of windows share was it? What kind of file share?
[*]When you say that the pam_mount is unable to create the first folder, do you mean the first folder which is on the Windows server? If so, I don't really have an idea to solve this.  I don't know enough about running a Windows server.
[/LIST]

---

### Post by ic3000 on 2011-11-14
Hi,

Both solutions worked for me with Ubuntu 11.10. I would like more to use LikeWise Open because it's free and OpenSource but Centrify Express, wich is free but not Opensource, seems to be less buggy and simple to configure PAM to work with it...

Sometimes Likewise Open wont be able to login for the first 5 minutes. It seems that the service starts in offline mode and it takes 5 minutes to retry... Maybe there is a workaround for this but it shouldnt be that way... i have a standard Ubuntu 11.10 instalation and using Likewise from Ububtu Software Center as this is also the case for Centrify Express where i dont need to do any changes for it to work "out of the box"...

But as i said because Likewise Open is opensource i would love to use it... more...

To make the shares mount for the user on logon you only need to install libpam-mount and smbfs with Sofware Center or apt-get...

Configure Volumes to be mounted on pam_mount.conf.xml with something like this:

<!-- pam_mount parameters: Volume-related -->



<volume user="*" fstype="cifs" server="server" path="users/%(DOMAIN_USER)" mountpoint="~/Documents" />

This is the basics and maybe all you should do but for Likewise Open you can see the examples on Likewiseopen user post to configure PAM.

For Centrify Express its a bit more simple because you only need to edit /etc/pam.d/common-auth and make shure that the first 2 lines are as folow:

auth optional pam_mount.so
auth       sufficient     pam_centrifydc.so try_first_pass

It's curious that LWO and CE both add lines to PAM .conf files but we need to edit them for it to work... Couldn't this be done by the setup scrits as they add parameters to .conf files...

The shares i'm mounting are user shares for exemple Desktop, Documents, Downloads, etc... from the user personal folder.

All my users on Windows have this kind of folder redirected making possible for the user to logon on any windows machine and have the same files...

As i said on my previous post this is working also for *nix machines but if the user hadn't logon to a Windows machine first he wouldnt have the mount.

Windows clients on logon create this folders on the file server but with my setup *nix machines dont create this folders in the file server making it impossible to be mounted on ubuntu logon...

My question here is if anyone knows if PAM can be configured to create this folders on logon? I found that pam as a parameter (pam_mkhomedir.so) that seems to do this on logon if the AD user havent had is folders created on the share but i can't seem to get this to work...

Any ideas?

Thanks once again!

---

### Post by linuxnoob09 on 2011-11-14
**Domain User's to sudoers file** 			
 			 			 		   		 		 		Running 11.10 and have tried multiple edits with visudo to make my domain account a member.  Connection to AD using Likewise.

Have tried a few combinations

Added to Admin group

mydomain\myusername
mydomain\\myusername
%domain\users
%domain\\users

Tried an AD group I am a part of 

%domain\usergroup
%domain\\usergroup


I am pretty much stuck.  This and adding printers are the last two  configuration changes I need to make work in order to liberate myself  from the Windows mess.  Any help would be appreciated.


-Steve

---

### Post by ic3000 on 2011-11-16
I think that it should be:

%DOMAIN\\somegroup ALL = (ALL) ALL

---

### Post by markathon on 2011-11-21
> **ic3000 said:**
> 

Sometimes Likewise Open wont be able to login for the first 5 minutes. It seems that the service starts in offline mode and it takes 5 minutes to retry... Maybe there is a workaround for this but it shouldnt be that way... 

How do you have your network connection set up? If you are using Network Manager, I don't think it connects immediately on boot. I uninstalled Network Manager and modified /etc/network/interfaces so that the connection is started at boot.

---

