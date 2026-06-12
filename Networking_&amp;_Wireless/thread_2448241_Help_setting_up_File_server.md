---
title: "Help setting up File server"
date: 2020-08-04
forum: Networking &amp; Wireless
---

### Post by nimic2 on 2020-08-04
I'm trying to repurpose an old PC into a file server for a home network. I have followed several tutorials and no matter what I do I can't seem to make the connection. 
My current setup is: Fresh Install of Ubuntu 20.04.1 LTS with Gnome version 3.36.3. All I have done is install samba then used the gnome "files" gui to share a folder in my home directory. I get a green sharing icon next to the folder. That didn't work so I modified the smb config file to Homegroup=THEFORCE (name of my homegroup on the windows pc). 
On my windows PC (client) I have downloaded SMB share prot. and activated all sharing options. At the moment I'm not worried about passwords so all passwords are disabled. Weirdly I do detect the server in Windows Media Player, but I don't want to use Windows Media Player. 
Everything is hard wired right now. Both server and client connected through ethernet to my router. But I will be adding wireless clients eventually.

In the past I have tried: Configuring all of samba through terminal. Copy pasting smb configs from Git. Using Samba 4k. Set up a Plex Server (worked but not what I wanted). Several remote desktop options (some connect but again not how i want it setup). 

I'm new-ish to Ubuntu and seriously outdated on my server knowledge (circa 2000).

---

### Post by TheFu on 2020-08-04
What are each of the clients including OS versions?  Different clients work best using different protocols.
Will you ever want secure access from outside the home?

I've never seen any GUI for samba setup that worked well.  A minimal guest-only setup is pretty trivial. About 15 lines unless you must support win10.  msft changed some things to fix security issues they've had for years and the samba server guys changed some defaults too, which break most clients, at least from ubuntu samba versions.

[https://ubuntuforums.org/showthread.php?t=2434383](https://ubuntuforums.org/showthread.php?t=2434383) should be all you need.  To edit system files, use the **sudoedit** program.

---

### Post by nimic2 on 2020-08-04
1) The client I'm testing with is Windows 10 Home x64 Desktop (up to date).  I would like to add clients: dual boot Windows 10 Home x64 / Kubuntu 20.04 LTS desktop, Windows 8.1 x64 Tablet (I can upgrade to Win 10 just never bothered), Windows 10 Pro x64 Laptop, iOS Tablet (not sure the version), Snow Leopard Macbook Pro. (the two apple os I figure are a problem for another day.) Basically I need a simple catchall setup which is why I thought just Samba would be the ticket.
2) I have no intention to ever access this server outside of my home LAN. 

3) I actually ended up going back to the GUI setup because it was the only one that didn't throw a bunch of errors. But that may have just been my scripting.

I'll follow your linked instructions see how it goes. Thanks.
Stupid questions: 
a) When writing paths in linux do you start with a space? ei ( /home/share) or (/home/share) 
b) Then when I move that same path over to Windows do I keep the forward slashes as they are in linux or write the path in windows backslash format.

---

### Post by nimic2 on 2020-08-04
Okay so that worked. I can now see the shared drives in Windows. However now I have permissions issues. In the Windows permission setting it detects everyone has read/write permissions but i get this dialog box when i try to open:
"Windows cannot access \\hostname\disk1
You do not have permission to access\\hostname\disk1. contact your network admin to request access"

---

### Post by fragglebliss on 2020-08-04
I'm not trying to turn you away from Ubuntu or anything, but if the system is solely purposed as a file server on a network then you really should consider installing a dedicated Linux distribution designed for server use which you can then login and easily configure it for use via the web console through the browser. It makes everything so much easier.

Take a look at openmediavault.

---

### Post by TheFu on 2020-08-04
a) Those instructions are not mine. I barely use Samba or Windows the last 12 yrs or so. Prior to that, I was a power-user and developer for pretty much every popular platform except OSX/MacOS, though I did write code for MacOS decades ago.

b) Unix-to-Unix works best with NFS, not Samba, but there are multiple opinions about that.

c) Secured, remote access is actually much easier. Just use sftp or sshfs.  Windows supports sftp via the WinSCP tool. I doubt it supports sshfs which is available for all Unix systems.

For other questions ... Unix always uses forward slashes and all Windows programs will accept those too. In Unix, if you want a \, then you must use \\.  So the Windows \\ has to be \\\\ on Unix.  Much easier to just use // and / on all platforms.

Cannot help with other questions without seeing much more factual data.  Start with the output from **testparm**.  It is likely someone else will need to answer.  I can help with NFS and anything ssh-based, but not so much on CIFS/Samba.

The main issue with all-file-server-only setups is they don't like when we try to use the same computer for general use needs. As fast as most computers are the last 10 yrs, samba is really a minor use and 50 other things, properly segmented via containers or VMs, can almost always be run.  I have a few Dual-Core systems running 8+ services in containers and VMs while also being the main NFS server for the house. It isn't busy 99% of the time. Heck, most people would be fine with a Raspberry Pi v2 as their home file server - aren't those like $20 now? Sure, the networking is slow, so I wouldn't use a r-pi as a backup server, but for typical file access and video streaming, sure. It would easily handle that.

---

### Post by Morbius1 on 2020-08-05
> All I have done is install samba then used the gnome "files" gui to share a folder in my home directory.
You would have had a fighting chance but then you did this:

> I modified the smb config file to Homegroup=THEFORCE (name of my homegroup on the windows pc).
There is no such thing as a homegroup in Win10.
> On my windows PC (client) I have downloaded SMB share prot. and activated all sharing options. 
I have no idea what that is.
> At the moment I'm not worried about passwords so all passwords are disabled.
Does that mean you created all guest accessible shares?
> Copy pasting smb configs from Git.
Really bad idea
> Using Samba 4k
You mean SMB4k? That is a client utility not a server utility.

We need to understand the amount of damage so far so please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```
And as a side note: Make sure avahi is installed:
```
sudo apt install avahi-daemon
```

---

### Post by nimic2 on 2020-08-05
> **Morbius1 said:**
>  There is no such thing as a homegroup in Win10. 
Sorry I misspoke my windows workgroup is the THEFORCE in smb.conf the script i changed was:
[global]
workgroup = THEFORCE

> **Morbius1 said:**
>  I have no idea what that is. 
 In Windows: Control Panel -> Programs and Features -> Turn Windows features on or off -> SMB 1.0/CIFS File Sharing Support: Automatic Removal, Client, and Server

> **Morbius1 said:**
>  Does that mean you created all guest accessible shares? 
Yes, everything is set to guest and disabled any passwords short of the user password.

```
 testparm -s Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
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
    workgroup = THEFORCE
    idmap config * : backend = tdb

```


```
 net usershare info --long 
[Childrens]
path=/media/callista/Movie Vault/Childrens
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/fiction is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[Eye Drive]
path=/home/callista/Eye Drive
comment=
usershare_acl=Everyone:F,
guest_ok=y

[TV]
path=/media/callista/TV Vault/TV
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

Since my first post I got "Eye Drive" in /home/callista working completely. I didn't change anything on it specifically so not sure how or why.
I tried sharing via gui  /media/callista/Movie Vault/Childrens and /media/callista/TV Vault/TV both show up on the client but I don't have permission to access. 
I added the following to the bottom of the smb.conf file:
[Documentaries]
path = /media/callista/Docu Vault
read only = no
guest ok = yes

[TV Shows]
path = /media/callista/TV Vault
read only = no
guest ok = yes

These drives also show up in the client but  I don't have permission to access. 

 I checked  avahi is installed.

---

### Post by SeijiSensei on 2020-08-05
The easiest method to solve Samba authentication problems with a small number of users is smbpasswd.  To add a user to Samba's database run

```
sudo smbpasswd -a username
```

The username should match a Linux user.  You'll be prompted to give the account a password.

If you want to add multiple new users to Samba, create Linux accounts for them on the server first.

```
sudo useradd username1
sudo passwd username1
sudo smbpasswd -a username1
[etc.]

```

---

### Post by Morbius1 on 2020-08-06
>  /media/callista/Movie Vault/Childrens and /media/callista/TV Vault/TV  both show up on the client but I don't have permission to access. 
No one can access "Childrens" or "TV Vault" or any of the other ones under /media/callista  except callista.

If you want to keep your shares as accessible to guests:

Edit /etc/samba/smb.conf and right under your **workgroup = THEFORCE **line add this one:
```
force user = callista
```
Then restart smbd:
```
sudo service smbd restart
```

There was no need to enable smb1 on WIn10. All you needed to do is access this ubuntu server explicitly by its hostname.local:

*** On your Ubuntu server find its host name:
```
hostname
```
*** On the Win10 machine open explorer and enter - using the hostname you found above - and don't forget the .local:
```
\\ubuntu-host-name.local
```
[COLOR=#ff0000]* Once it opens showing you the shares you can "pin" it to to your Start menu or to your "Quick Access" list so that it is always available.*[/COLOR]

This will bypass SMB1 and you will connect to the Ubuntu server using SMB3.

---

### Post by nimic2 on 2020-08-06
Awesome it works now. I got all my clients connected including the iOS ones. Thank you so much.
It was such a simple step that I was missing but I was missing it so thanks.
Just to clarify if I want to take the folders off guest access I would uncheck the "Guest access" box. Then use the samba password process that seijisenei posted. Then I could login using those credentials on any device.

---

