---
title: "Touble seeing Ubuntu from my Windows Network"
date: 2023-08-22
forum: Networking &amp; Wireless
---

### Post by gymbo2 on 2023-08-22
Both are connected thru cat 5 cables.

From Windows "Select a shared folder" I get my Chrome Book, my office Windows computer, my router, and my wife's Windows computer, no Ubuntu. Is there a share I need to set up on Ubuntu to make it visible? I can ping Ubuntu's ip address from my Windows computer. Ant suggestions?

---

### Post by TheFu on 2023-08-23
> **gymbo2 said:**
> Both are connected thru cat 5 cables.

From Windows "Select a shared folder" I get my Chrome Book, my office Windows computer, my router, and my wife's Windows computer, no Ubuntu. Is there a share I need to set up on Ubuntu to make it visible? I can ping Ubuntu's ip address from my Windows computer. Ant suggestions?

GigE networks need to be connected via CAT5e cables, not CAT5. There is a difference.  If you connect them each to a router, things are even better, since it will handle routing between the systems. If you don't, then you have to manually tell each system how to find the other. People new to networking generally aren't ready for those manual commands.

Ah ... you seem to have a router. Good. That makes things easier.
Check that **avahi** is installed on Ubuntu.  This will advertise to other mDNS computers on the system that "I'm here, I'm here" every few minutes.  If the hostname for ubuntu is "desktop", then the mDNS name to be used will be "desktop.local".  Try using ping with that as the input, of course, you'll need to change it for your specific hostname.  

That will solve IP networking, but it doesn't solve MSFT's CIFS/Samba connections.  Those do something else as of a few years ago.  For many decades, MSFT used nmbd to broadcast about network shares and network printers.  Look for recent posts here my Morbius1 for which programs need to be installed and run on Linux to let MS-Windows see CIFS network shares.  Sorry, I don't recall the details, but I'll check my notes.
[Https://ubuntuforums.org/showthread.php?t=2477510&p=14106261#post14106261](Https://ubuntuforums.org/showthread.php?t=2477510&p=14106261#post14106261) 

I'm assuming you actually want to use CIFS for network shares.  If you don't, there are lots of other, more secure, protocols.  **sftp** is one, but on MS-Windows, you'll need to use either **WinSCP** or **Filezilla** to make an sftp connection.  sftp is an extremely standard protocol used worldwide.  MSFT only added it to Win10 after 20 yrs of ignoring the rest of the industry.  They added it as a CLI program only, **sftp.exe**, not to MS-Explorer, which it unfortunate.

**ssh, scp, sftp, rsync**, are how Unix-like computers communicate locally and around the world. Best to learn them. They've been around since the mid-1990s and are both convenience AND secure.  Most Linux file managers support sftp://  URLs.

---

### Post by SeijiSensei on 2023-08-23
[https://ubuntu.com/server/docs/samba-file-server](https://ubuntu.com/server/docs/samba-file-server)

I also share media files on one of my Linux boxes using minidlna. Many TVs and other devices have built-in support for the DLNA protocol. It's pretty trivial to configure.

[https://thepiguy.altervista.org/how-to-install-minidlna-in-ubuntu/](https://thepiguy.altervista.org/how-to-install-minidlna-in-ubuntu/)

It usually works better for streaming media than using a CIFS connection via Samba. However, the DLNA client in your TV may not have support for some things like formatted subtitles (.ass) or all video and media codecs.

---

### Post by TheFu on 2023-08-23
> **SeijiSensei said:**
> [https://ubuntu.com/server/docs/samba-file-server](https://ubuntu.com/server/docs/samba-file-server)

Those instructions lack the need for avahi and WS-Discovery that Win10+ require.

---

### Post by gymbo2 on 2023-08-23
I appreciate both of your comments/instructions, but I am a complete novice when it comes to Ubuntu.
> [COLOR=#000000]Check that [/COLOR]**avahi is installed on Ubuntu. ** I don't have a clue how to do that.

This is a new install of Ubuntu, replaced a much older computer. The older system worked very well, I used it backup my wife's and my Windows computers as well as using it as a second screen to view web pages, pdfs and the like. I haven't changed the CAT5 cables. The Device Name is Ubuntu, I can ping it from my Windows machine.

I guess what I need is a little bit of hand holding to get me through getting this setup.

---

### Post by TheFu on 2023-08-23
> **gymbo2 said:**
> <snip>
I guess what I need is a little bit of hand holding to get me through getting this setup.

I'll have to let others do that.  Helping beginners is not something I'm good at, for both of our sanity.
The instructions are there in Morbius's link. I don't know what more I can add to make it simpler.

---

### Post by gymbo2 on 2023-08-23
I did got through Morbius' instructions.

I've managed to get Windows to finally see Ubuntu and a folder I created called backups, but now when mapping that folder I get an access denied error. I've set the folder's Share name to backups, clicked Share this folder and allowed others to create and delete files in this folder. Access denied sound like an Ubuntu problem but it's probably Windows.

---

### Post by TheFu on 2023-08-23
Will you be posting the troubleshooting stuff that the provided link shows, but for your system?

---

### Post by Morbius1 on 2023-08-24
> **gymbo2 said:**
> I did got through Morbius' instructions.

I've managed to get Windows to finally see Ubuntu and a folder I created called backups, but now when mapping that folder I get an access denied error. **[COLOR="#B22222"]I've set the folder's Share name to backups, clicked Share this folder and allowed others to create and delete files in this folder.[/COLOR]** Access denied sound like an Ubuntu problem but it's probably Windows.
You have created what samba calls a usershare.

We need to see how and more importantly where that share was created. Posting the output of this command will help with that:
```
net usershare info --long
```

You might want to also post the output of this one to see how samba itself is set up:
```
testparm -s
```

---

### Post by gymbo2 on 2023-08-24
> **Morbius1 said:**
> You have created what samba calls a usershare.

We need to see how and more importantly where that share was created. Posting the output of this command will help with that:
```
net usershare info --long
```

Here the are:

```
[backups]
path=/home/jim/backups
comment=
usershare_acl=Everyone:F,
guest_ok=n
```   

You might want to also post the output of this one to see how samba itself is set up:
```
testparm -s
```

```
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed


Server role: ROLE_STANDALONE


# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb




[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes




[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
```

---

### Post by gymbo2 on 2023-08-24
I've added a password to samba, but still get the Access denied error trying to map that folder through Windows.

---

### Post by TheFu on 2023-08-24
Trying to share directories under a specific user's HOME isn't recommended for a few reasons.  Best to move those files elsewhere and use smb.conf to share them specifically.  Unfortunately, the GUI method of sharing has always had issues.

But it it your system. Fight the battles you want.

---

### Post by Morbius1 on 2023-08-24
> [backups]
path=/home/jim/backups
comment=
usershare_acl=Everyone:F,
guest_ok=n
The only user that can access that share is "jim" not because of samba but because the default permissions on one's home directory prohibit it.

You can force everyone to access that share using the username jim if you want. But you have to add jim to the samba password database:
```
sudo smbpasswd -a jim
```

Or you can force all your network users to appear to be "jim" - for your samba shares anyway - by adding this line under the workgroup = WORKGROUP line in /etc/samba/smb.conf:
```
force user = jim
```
Then restarting samba:
```
sudo service smbd restart
```

---

### Post by gymbo2 on 2023-08-24
I'll certainly try those options. FWIW this is a replacement of an older computer, this is the way I had it set up before, but I don't think I did either of those to get Windows to see the folder backups. 

How else can I set up a share between Windows and Ubuntu, how and where should I put the folder 'backups'?

---

### Post by TheFu on 2023-08-24
> **gymbo2 said:**
> I'll certainly try those options. FWIW this is a replacement of an older computer, this is the way I had it set up before, but I don't think I did either of those to get Windows to see the folder backups. 

How else can I set up a share between Windows and Ubuntu, how and where should I put the folder 'backups'?

If it were me, I'd put it into /media/backups/ 
and add a stanza to the /etc/samba/smb.conf like this:
```
[Backups]
  comment = Per-User Backups
  path = /media/backups/%U
  hosts allow = 127.0.0.1 192.168.55.0/24 
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S

```
Use smbpasswd to add a new account for each of the users on Windows, so they can copy over their files to the Share named "Backups". The way this is setup let's each user have a separate backup directory. They won't see each other's.
I don't know if you need to pre-create  /media/backups/jim and  /media/backups/bob and /media/backups/eileen. If it doesn't work, try creating those directories.  Since Samba runs as root, I don't think the actual owners for those directories matters.  If only Windows files will be stored there, the file system used probably doesn't matter too much, but if you intend to use this same disk for backups of Linuix/Unix computer files, then there are better methods than using Samba and the file system really needs to be native linux, like ext4 or xfs or something like that.

---

### Post by gymbo2 on 2023-08-24
Adding Jim to the samba data base:

```
sudo smbpasswd -a jim
[sudo] password for jim: 
New SMB password:
Retype new SMB password:
```

Didn't work, "Access denied"

```
jim@ubuntu:~$ force user = jim
Command 'force' not found, did you mean:
  command 'forge' from deb snap (2013-11-29-11)
  command 'zforce' from deb gzip (1.10-4ubuntu4.1)
Try: sudo apt install <deb name>

```

---

### Post by Morbius1 on 2023-08-24
> **gymbo2 said:**
> I'll certainly try those options. FWIW this is a replacement of an older computer, this is the way I had it set up before, but I don't think I did either of those to get Windows to see the folder backups. 

How else can I set up a share between Windows and Ubuntu, how and where should I put the folder 'backups'?
What version of Windows are you using?

---

### Post by Morbius1 on 2023-08-24
> Didn't work, "Access denied"

Code:

jim@ubuntu:~$ force user = jim
Command 'force' not found, did you mean:
  command 'forge' from deb snap (2013-11-29-11)
  command 'zforce' from deb gzip (1.10-4ubuntu4.1)
Try: sudo apt install <deb name>

It's not a command. You enter that line in /etc/samba/smb.conf under workgroup = WORKGROUP:
> #======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
**[COLOR="#FF0000"]force user = jim[/COLOR]**

---

### Post by gymbo2 on 2023-08-24
My biggest problem is I've never worked in Unix, or Linux, or Ubuntu except to use it for backing up a couple of Windows computers using File History, looking at web pages and an occasional pdf file, if my Windows window was over whelmed.

So if you could give me the command to perform this operation, i'd appreciate it, and if it works I'll quit bothering you.

---

### Post by gymbo2 on 2023-08-24
> **TheFu said:**
> If it were me, I'd put it into /media/backups/ 
and add a stanza to the /etc/samba/smb.conf like this:
```
[Backups]
  comment = Per-User Backups
  path = /media/backups/%U
  hosts allow = 127.0.0.1 192.168.55.0/24 
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S

```
Use smbpasswd to add a new account for each of the users on Windows, so they can copy over their files to the Share named "Backups". The way this is setup let's each user have a separate backup directory. They won't see each other's.
I don't know if you need to pre-create  /media/backups/jim and  /media/backups/bob and /media/backups/eileen. If it doesn't work, try creating those directories.  Since Samba runs as root, I don't think the actual owners for those directories matters.  If only Windows files will be stored there, the file system used probably doesn't matter too much, but if you intend to use this same disk for backups of Linuix/Unix computer files, then there are better methods than using Samba and the file system really needs to be native linux, like ext4 or xfs or something like that.


Windows only sees the backsup folder in Ubunbtu!

---

### Post by Morbius1 on 2023-08-25
> **gymbo2 said:**
> My biggest problem is I've never worked in Unix, or Linux, or Ubuntu except to use it for backing up a couple of Windows computers using File History, looking at web pages and an occasional pdf file, if my Windows window was over whelmed.

So if you could give me the command to perform this operation, i'd appreciate it, and if it works I'll quit bothering you.

This will allow you to edit smb.conf as root:

```
gedit admin:///etc/samba/smb.conf
```

[COLOR="#B22222"]NOTE: Whenever you edit smb.conf directly you need to save the file and run this:[/COLOR]
```
sudo service smbd restart
```

**[COLOR="#B22222"]NOTE2: You have in this thread 3 different solutions.[/COLOR]**

You need to pick one since they are beginning to conflict with one another.

My posts are about your original use case where you created a samba **usershare** of your **/home/jim/backups** folder.

If you have chosen to go a different path stop following my posts.

---

### Post by TheFu on 2023-08-25
> **Morbius1 said:**
>  
**[COLOR="#B22222"]NOTE2: You have in this thread 3 different solutions.[/COLOR]**

You need to pick one since they are beginning to conflict with one another.

My posts are about your original use case where you created a samba **usershare** of your **/home/jim/backups** folder.

If you have chosen to go a different path stop following my posts.

+1.  If I were you, I'd follow Morbius1's posts. He's much better at samba.

---

### Post by gymbo2 on 2023-08-25
Okay, I edited smb.conf, I added "force user = jim" after the line:

#change this to workgroup/NT-domain name your Samba server will part of workgroup = WORKGROUP

Saved the file and ran:
```
sudo sevice smbd restart
```

And still got 'Access is denied' trying to map ubuntu/backups.

Restarted both computers which didn't help.

---

### Post by Morbius1 on 2023-08-25
Let's see if we can't do this methodically:

[1] Make sure avahi is running on "server1":
```
sudo service avahi-daemon status
```
It should come back with something like this:
> &#9679; avahi-daemon.service - Avahi mDNS/DNS-SD Stack
     Loaded: loaded (/lib/systemd/system/avahi-daemon.service; enabled; vendor preset: enabled)
     Active: [COLOR="#008000"]active (running)[/COLOR] since Fri 2023-08-25 06:07:08 EDT; 6h ago
If it's not start it:
```
sudo service avahi-daemon restart
```
[2] If you have a firewall running stop it:
```
sudo ufw disable
```
[3] On server1 itself see if you can connect to your own share by running:
```
nautilus smb://server1.local/backups
```
[4] If that does not work find it's ip address:
```
hostname -I
```
THen connect to it with the ip address from that output. Something like this if the ip address was 192.168.0.101:
```
nautilus smb://192.168.0.101/backups
```

If [3] or [4] works try the same thing from Windows. In explorer:

If this is Win10 or Win11:
```
\\server1.local\backups
```
If it's something earlier:
```
\\192.168.0.101\backups
```

---

### Post by gymbo2 on 2023-08-25
```
sudo service avahi-daemon status 
```

returned this

```
&#9679; avahi-daemon.service - Avahi mDNS/DNS-SD Stack
     Loaded: loaded (/lib/systemd/system/avahi-daemon.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2023-08-25 08:53:34 PDT; 1h 13min ago
TriggeredBy: &#9679; avahi-daemon.socket
   Main PID: 456 (avahi-daemon)
     Status: "avahi-daemon 0.8 starting up."
      Tasks: 2 (limit: 9319)
     Memory: 2.4M
        CPU: 10.835s
     CGroup: /system.slice/avahi-daemon.service
             &#9500;&#9472;456 "avahi-daemon: running [ubuntu.local]"
             &#9492;&#9472;560 "avahi-daemon: chroot helper"


Aug 25 08:53:39 ubuntu avahi-daemon[456]: New relevant interface enp3s0.IPv6 for mDNS.
Aug 25 08:53:39 ubuntu avahi-daemon[456]: Registering new address record for fe80::1cc2:c15b:4cfa:c6a on enp3s0.*.
Aug 25 08:53:39 ubuntu avahi-daemon[456]: Joining mDNS multicast group on interface enp3s0.IPv4 with address 192.168.1>
Aug 25 08:53:39 ubuntu avahi-daemon[456]: New relevant interface enp3s0.IPv4 for mDNS.
Aug 25 08:53:39 ubuntu avahi-daemon[456]: Registering new address record for 192.168.1.100 on enp3s0.IPv4.
Aug 25 08:53:40 ubuntu avahi-daemon[456]: Leaving mDNS multicast group on interface enp3s0.IPv6 with address fe80::1cc>
Aug 25 08:53:40 ubuntu avahi-daemon[456]: Joining mDNS multicast group on interface enp3s0.IPv6 with address 2600:6c55>
Aug 25 08:53:40 ubuntu avahi-daemon[456]: Registering new address record for 2600:6c55:6500:dfd:524d:c956:9c2d:24ea on>
Aug 25 08:53:40 ubuntu avahi-daemon[456]: Withdrawing address record for fe80::1cc2:c15b:4cfa:c6a on enp3s0.
Aug 25 08:53:41 ubuntu avahi-daemon[456]: Registering new address record for 2600:6c55:6500:dfd:7299:60d6:b4df:3b23 on>
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1-23/23 (END)

``` Then Terminal  hung, wouldn't except anything, tried to turn it off and it said it's still running, will wait.

---

### Post by Morbius1 on 2023-08-25
hit: **[COLOR="#FF0000"]ctrl[/COLOR]** and **[COLOR="#B22222"]c[/COLOR]** at the same time

---

### Post by deadflowr on 2023-08-25
Pressing q should exit it as well.

---

### Post by gymbo2 on 2023-08-25
```
[COLOR=#000000][FONT=&quot]nautilus smb://server1.local/backups[/FONT][/COLOR]
``` 

It brought file manager with a popup error:

Oops something went wrong. Unhandled error message: failed to mount Windows share: invalid argument

Deleting the message left me in Home folder.

---

### Post by gymbo2 on 2023-08-25
```
nautilus smb://192.168.1.100/backups
```

brought up Authentication Required, clicked on registered user, twice it ignored the password, let it at anonymous kept getting the Connect button but wouldn't connect.
On cancelling it opened a folder in Home.

and after that this was in Terminal:
```
(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:04.527: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:04.528: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:04.528: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:15.982: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:15.983: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:15.983: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:15.988: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:15.989: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:15.989: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:26.080: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:26.081: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:26.081: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:26.081: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:51.107: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:51.108: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed


(org.gnome.Nautilus:4230): Gtk-CRITICAL **: 10:43:51.108: gtk_widget_set_sensitive: assertion 'GTK_IS_WIDGET (widget)' failed



```

---

### Post by Morbius1 on 2023-08-25
And what does this do in Windows explorer:
```
\\ubuntu.local\backups
```
Or this:
```
\\192.168.1.100\backups
```

---

### Post by gymbo2 on 2023-08-25
\\ubuntu and \\sever1.local asked to check spelling.

```
\\192.198.168.1.100\backups
``` asked for user name and password, but didn't accept jim and pw

---

### Post by Morbius1 on 2023-08-25
Is jim in the samba database. Does it show up here:
```
sudo pdbedit -L
```

---

### Post by gymbo2 on 2023-08-25
jim:1000:Jim Allen

---

### Post by Morbius1 on 2023-08-25
I can't help you.

Time for someone else.

---

### Post by gymbo2 on 2023-08-25
Thanks for trying.

---

### Post by TheFu on 2023-08-29
> **gymbo2 said:**
> Thanks for trying.

Did you give up or have you started over and tried what I suggested in post with the 10 line stanza?  If so, forget using the GUI to set this stuff up.

---

### Post by hifron on 2023-10-26
Something as making a user shared clicable nautilus dirs without executive permissions allowed from local network is maybe a headache for Samba devs...

---

