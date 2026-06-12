---
title: "[SOLVED] Problem setting up Samba (Vista and Feisty)"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by JawsThemeSwimming428 on 2007-09-20
I am following this guide [http://ubuntu-unleashed.blogspot.com/2007/08/howto-quickly-easily-setup-samba.html](http://ubuntu-unleashed.blogspot.com/2007/08/howto-quickly-easily-setup-samba.html) on how to set up samba. I edited smb.conf and I am running testparm but it is coming up with boolean errors and I am not sure what it means or how to correct them. Here is the output:
hope@hubuntu:/etc/samba$ testparm

Load smb config files from /etc/samba/smb.conf

ERROR: Badly formed boolean in configuration file: "true ;; You want this b/c many people leave their passwords blank.".

lp_bool(true ;; You want this b/c many people leave their passwords blank.): value is not boolean!

ERROR: Badly formed boolean in configuration file: "no ;; Affects the address used to access the share folder on the Windows machine -- makes it".

lp_bool(no ;; Affects the address used to access the share folder on the Windows machine -- makes it): value is not boolean!

Processing section "[PUBLIC]"

ERROR: Badly formed boolean in configuration file: "yes ;; Whether or not users on the other end can browse the share folder.".

lp_bool(yes ;; Whether or not users on the other end can browse the share folder.): value is not boolean!

ERROR: Badly formed boolean in configuration file: "no ;; Whether or not users on the other end can change its contents.".

lp_bool(no ;; Whether or not users on the other end can change its contents.): value is not boolean!

Loaded services file OK.

Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions



[global]

        workgroup = WORKGROUP... ;; NAME OF HOME NETWORK (MAKE SURE IT'S THE SAME AS WHATEVER YOU SET IN WINDOWS).

        netbios name = hubuntu... ;; HOSTNAME (OPEN A COMMAND PROMPT; IT'S THE PART AFTER THE @).

        server string = ... ;; Description of host.

        passdb backend = tdbsam ;; The format Samba password info is stored in (don't have to touch).

        username map = /etc/samba/smbusers ;; Can leave alone (we won't be editing this anyway).

        syslog only = Yes

        announce version = 5.0

        name resolve order = hosts wins bcast ;; Don't know what this does.

        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192



[PUBLIC]

        comment = hubuntu... ;; Name that will appear when you run "net view" in Windows.

        path = /home/hope... ;; The share folder on this machine.

        force user = hope... ;; Who will end up owning the files that come in. Probably best to just use your username, since you're the one who'll be accessing this stuff :)

        force group = hope... ;; You can make this the same as the last.

        read only = No

        create mask = 0777

        directory mask = 0777

        browseable = No

        fstype = Samba ;; This will show up in the sidebar in Windows, it doesn't really affect anything.

Anyone that can give me a  hand I would be  very appreciative. I will be checking back all night. Thanks!

---

### Post by louieb on 2007-09-20
Haven't had a problem setting up samba since I found this
[HOWTO: Setup Samba peer-to-peer with Windows - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=202605&highlight=server")

---

### Post by JawsThemeSwimming428 on 2007-09-20
Thanks, I followed that and I was able to view and edit files on my Feisty machine from my Windows machine. However, after a Feisty reboot I can not access the mapped drive on Vista. It seems like it tries to find it and then it says the Network path was not found. Both of these machines have Static IP's. I am not sure, is there something else I need to do?

---

### Post by JawsThemeSwimming428 on 2007-09-20
One thing I did notice... I tried to share my home folder, but when I rebooted I was presented with the following message onces I typed my password and hit Enter to log in: 

     " User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

I am not quite sure what that means or what I should do to fix it (or if it has anything to do with my network folder access problem above... In smb.conf I elected to share /home/willy which is my home directory).

---

### Post by JawsThemeSwimming428 on 2007-09-22
I am still having issues. I tried some of the things I saw throughout Stormbringer's post and now my Vista machine can see Feisty but it wont open any shares when I try to map it. Also, that .dmrc error is still coming up when I log in (see: [http://ubuntuforums.org/showthread.php?t=556508](http://ubuntuforums.org/showthread.php?t=556508)).

---

### Post by JawsThemeSwimming428 on 2007-09-23
OK, I think I finally got it working. I think one of the main issues was Firestarter getting in the way. I also re-did my smb.conf. Thanks for the help!

---

