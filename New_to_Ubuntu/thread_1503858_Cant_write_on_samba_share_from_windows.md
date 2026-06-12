---
title: "Cant write on samba share from windows"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by mlmpihl on 2010-06-07
Hi.

I created a samba share with ubuntu konfiguration of samba in the graphic envirement.

I can acces it from my windows, but I can not write to it

I use latest ubuntu 10.04 LTS desktop

Hope someone can help me
Best regards
Kenneth

---

### Post by NT4usB on 2010-06-07
I'd guess permissions.
Did you grant read/write permission to others?

---

### Post by jerenept on 2010-06-07
open a terminal. (Applications>Accessories>Terminal)
enter
```
sudo apt-get install system-config-samba
```

type in your password.

After this is installed, go to 
System>Administration>Samba and enter your password when prompted.

You can edit Windows shares graphically from there.

---

### Post by mlmpihl on 2010-06-08
Thanks for the answers. I already installed samba, and also used the graphical setting tool that is on the menubar (system/administration/samba)

I also have acces to Samba from my windows pc's. All the users are also able to acces and see the share. But no users are granted permission to write.

As for now, we have a share, with no files (need to move files from windows pc), we can see the share from windows, acces it, but can write to it.

Would it be an idea maybe to put the configuration in smb.conf in this thread?

/Kenneth

---

### Post by Paddy Landau on 2010-06-08
> **mlmpihl said:**
> Would it be an idea maybe to put the configuration in smb.conf in this thread?
Yes, OK. Remember to wrap [ code] and [/ code] around it (press the # button on the toolbar).

Did you make your directory writeable by everyone?

In the Samba GUI, did you set the share to *Writable* and *Allow access to everyone*?

---

### Post by NT4usB on 2010-06-08
[wag]
I've never tried ext4. Can Windows write to an ext4 share? Are you using ext4?

---

### Post by pricetech on 2010-06-08
It doesn't matter what the file system is on the Linux box, Samba shares it as a windows share.

It's probably permissions, adjustable in the configuration tool.

---

### Post by Nixie Pixel on 2010-06-08
I have found that creating directories or copying/moving files to the share from Ubuntu sometimes creates restrictive permissions, when doing the same from Windows does not. So on my Ubuntu file server if I were to create a directory or put, say, images on the shared drive, I could then read them from windows machines, but not write/modify.

I think I found chown to be useful here.

---

### Post by NT4usB on 2010-06-08
> **Nixie Pixel said:**
> I have found that creating directories or copying/moving files to the share from Ubuntu sometimes creates restrictive permissions, when doing the same from Windows does not. So on my Ubuntu file server if I were to create a directory or put, say, images on the shared drive, I could then read them from windows machines, but not write/modify.

I think I found chown to be useful here.

Interesting...
I was surprised to find Linux respecting Windows permissions.
Whenever I copy from XP/2K to Ubuntu, I have to chown/chmod the files in order to to edit them.
All my Linux boxes have the same username so moving files between them is a non issue.

---

### Post by stevewasiura on 2010-06-15
I'm having the same problem.
 
On winxp i can open a file explorer window to the share on xUbuntu, 
I can open a file for editing,
but I cannot save the file
 
Please advise:
**1. how can I tell which xubuntu user account I am connecting to xubuntu with?**
(I looked in /var/log/samba, found the file named after my windows machine, opened it, one of the lines contained
```
 
connect to service ubuntu_www (the name of the share) initially as user nobody (uid=65534, gid=65534) (pid 4101)

```
 
It appears to me that my connection is not using a valid account, therefore I assume permissions are not being applied. 
 
**2. How can I force winxp to connect to the xubuntu share using an account name and password on xubuntu? **
I've tried to map a drive on winxp and connect using a different username UBUNTU\username and password, but winxp fails to map the drive because the user account password doesn't connect.
 
Thanks in advance.

---

### Post by Paddy Landau on 2010-06-15
Refer to:

[LIST]
[*][How to File Share in Ubuntu 10.04 Easily and using GUI's only]("http://ubuntuforums.org/showthread.php?t=1502265"), [post #1]("http://ubuntuforums.org/showthread.php?p=9414468#post941446")
[*]If it still doesn't work, see the [workaround in post #2]("http://ubuntuforums.org/showthread.php?p=9414727#post9414727"). If the workaround works for you, please [vote for the reported bug]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610").
[/LIST]

---

### Post by Morbius1 on 2010-06-15
> I can acces it from my windows, but I can not write to it> On winxp i can open a file explorer window to the share on xUbuntu, 
I can open a file for editing,
but I cannot save the fileBoth the original post and the one by stevewasiura appears to me ( as others have noted above ) to be linux permissions problems not Samba authentication problems. [COLOR=Blue]Both these posters can see the share and can even access the share, they just can't edit the share.[/COLOR] Why not post the output of the following commands so we can see how you are configured. Then we'll have some facts to work with:

```
net usershare info
sudo net usershare info
testparm -s
```

---

### Post by stevewasiura on 2010-06-17
I tried net, it said program 'net' cannot be found in samba-common-bin and samba4-clients
i tried apt-get and it could not find package net
thanks, please advise what to try next

---

### Post by stevewasiura on 2010-06-17
I don't want to try that method because it says it's unsecure, and my machine is open to the world for www test development
 
i want to force user level security, that's why i was asking how to tell which user the windows machine is connecting as.
 
should i try the unsecure method first to learn or understand how it works, and then turn it off, and try a more secure method? i don't know how yet, but i'll await for more help, thanks.

---

### Post by Morbius1 on 2010-06-17
And "testparm -s"

What is it's output?

[COLOR=Blue]EDIT: You know I really should learn to read to the end of the sentence.[/COLOR]

You're running samba on a machine connected directly to the internet?

---

### Post by stevewasiura on 2010-06-18
adding testparm -s doesn't fix the problem that says net is not a vaid program
 
i'm going to uninstall samba and start over

---

### Post by Morbius1 on 2010-06-18
**testparm -s **isn't an option you add to smb.conf. It's a command that you issue in a terminal and it's output will list any errors it sees in smb.conf plus a very concise rendering of smb.conf without all it's comments.

---

### Post by stevewasiura on 2010-06-18
i might know how you feel because i've been on that side when trying to help windows users. unfortunately this ubuntu & samba stuff is really frustrating to me because it's confusing, all the examples I read say "this setup config is not secure", etc..., so I don't want to set it up that way. the ubuntu machine is connected to a dsl router with a firewall and port 80 is pointed to the ubuntu server. i don't know if that's secure enough for samba, so I'm trying to play it safe....



i didn't add testparm -s to the smb.conf file, i added it to the end of the net command in terminal. of course that didn't work because it says net was not a program, etc.

in the meantime, i opened synaptic pkg mgr and searched for samba and started marking items for uninstall completely, but there were so many listed and i wasnt sure what was really samba, so I quit without uninstalling anything.

i open the samba GUI Applications > System >Samba

i tried again after your email. opened terminal, typed testparm -s
and it said

the program 'testparm' can be found in  
samba-common-bin
samba4-common-bin

that was never shown before when I typed net usershare info

i don't know if samba did uninstall itself or it was never installed correctly...
so I apt-get the samba-common-bin and samba4-clients

and ran the command again, and it output a lot of stuff.

I'll have to login to the forum from the ubuntu machine and paste the output into a new reply. hang tight, and thanks for sticking with me

---

### Post by stevewasiura on 2010-06-18
here is the output from terminal

steve@xubuntu:~$ sudo net usershare info
steve@xubuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = UBUNTU
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
    load printers = No
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    valid users = %S
    create mask = 0775
    directory mask = 0775

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

---

### Post by Morbius1 on 2010-06-18
If you have both samba3 and samba4 installed I don't know what you've got. 

Trying to use samba across the Internet is not recommended and I for sure have no experience in doing that.

You have no shares defined.

---

### Post by stevewasiura on 2010-06-18
Huh? 
Why do you think I have Samba 3 AND 4 installed? Does it say that in the log somewhere? I don't see it.
 
I'm not trying to use Samba across the Internet, did I say that somewhere? 
I'm trying to use Samba to allow a Windows XP machine on the LAN to connect to the Ubuntu machine to read and write files for the test web server, which is open to the world through port 80, so clients can view web pages and comment on them. 
 
See why I'm getting so insane about this? Comments and replies on forums are not explained enough for a Ubuntu newbie to understand.
 
I had shares defined, I don't know why they disappeared? Maybe the reinstall or updates I did through apt-get erased them.
 
I setup a new share through the GUI, I made it writable and visible, and allowed access to everyone, restarted samba, and my winxp machine ON THE LAN still can't connect.
 
F my life today

---

### Post by Morbius1 on 2010-06-18
> **stevewasiura said:**
> Huh? 
Why do you think I have Samba 3 AND 4 installed?
Answer:
> so I apt-get the samba-common-bin and samba4-clients
 samba4-clients brought with it a bunch of stuff and deleted smbclient for some reason. Not familiar enough with the changes samba is making to V4.
> I'm not trying to use Samba across the Internet, did I say that somewhere? > I'm trying to use Samba to allow a Windows XP machine on the LAN to connect to the Ubuntu machine to read and write files for the test web server, which is open to the world through port 80, so clients can view web pages and comment on them. > I setup a new share through the GUI, I made it writable and visible, and allowed access to everyone, restarted samba, and my winxp machine ON THE LAN still can't connect.
 From the WinXP machine open Command Prompt and issue the following command:
```
net view
```Then:
```
net view \\ubuntu-server-name
```If it produces error messages then you have something you can research.

BTW, you have to feel sorry for mlmpihl. He never did get his issue resolved.

---

### Post by stevewasiura on 2010-06-21
the latest research I found a ref to chown the folder to nobody:nogroup
 
I think I understand it to mean that it sets ownership to a low level security group, which allows everybody access RWX to those files
 
can someone please explain if this is a security risk?
 
even if I trust everyone on the LAN, and they have RWX access to these files, is there a chance that an attack from outside could get in? of course there is a chance...
 
is there a better way to do this, i.e. couldn't i chown the folder to the name of a ubuntu group, and then when accessing the files from winxp, it would prompt me to login with a ubuntu username & password, and then i would have RWX access to the files?
 
or do they have to be CHOWN to nobody:nogroup because samba handles the security access to those files, and samba will only let through the appropriate users?
 
 
i checked ownership of the folder /home/username/www using the command ls -al 
 
drwxrwxr-x username usergroup
 
so ownership is already set for the user, but i still don't have access from winxp, even after it prompts me for username / pwd , but it doesn't let me through
 
the folder i want to share is also used to serve web page scripts using php, so that is why i'm hesitant to set ownership to nobody:nogroup
 
thanks again

---

### Post by Paddy Landau on 2010-06-21
> **stevewasiura said:**
> the latest research I found a ref to chown the folder to nobody:nogroup
I don't think that this makes any difference. My public folder is owned by root, and its permissions are read-write-access to everyone. The result is that everyone has access within the folder, but only root can delete the folder.

As I understand it, Samba provides access, and it's through Samba that people get access; either guest access, which means anyone with access to the LAN, or on a user-by-user basis.

---

### Post by Morbius1 on 2010-06-21
Samba determines what a remote user MAY do.
Linux file permissions determine what a remote user CAN do.

If you have a folder that has these permissions:
>  drwxrwxr-x username usergroupand then you share it to allow guest access with write permissions it won't work. The last three letters governs linux permissions to "others" or in this case "guests" and there is no "w" or write so samba says a guest can write and linux says no they can't. Linux always wins these arguments.

In your particular case you say that you are trying to access a share with the following ownership and permissions:
>  drwxrwxr-x username usergroupYou further claim that you are accessing that share using the name "username". What password are you using to authenticate? Or to put it another way, did you create a samba password for "username"?
```
sudo smbpasswd -a username
```

---

### Post by stevewasiura on 2010-06-22
sorry for the delayed response, I did not rcv email notification of your replies.
 
yes, that makes sense that it is a Ubuntu permissions problem, thank you. 
I believe this is what you started saying way back when, but your most recent explanation teaches the lesson.
 
i did use smbpasswd to create a password for the username. I set the password to be the same as the Ubuntu username's password. I also had some settings in the smb.conf file turned on that was supposed to syncronize any changes in the ubuntu password, but I haven't changed the ubuntu pwd at all, so hopefully that is not a concern.
 
As of 5 minutes ago, I edited the smb.conf file again, changed security=user to security=share, just to get access to the files from winxp. I restarted samba, and I could browse the folders and view the files without any authentication prompts from windows. 
 
But I still could not write a new file to the folder. So I checked the permissions of the folder, and "others" is set to read only. That made sense when I was using security=user, since I assumed the winxp machine would connect to the share, prompt for authentication, enter the samba username and password, and it would let me in, and I should have been able to read & write. 
 
But now that I am using securty=share, I think the winxp machine is connecting as a guest, because it is not being prompted for authentication when connecting to the samba share. So I changed the permissions of the folder to allow "guest" to read & write, and I was able to write.
 
But this is not how I want it to be, as I assume it is not secure, i.e. if someone somehow broke into the ubuntu server as the www user, then they would have write access to the folder and could mess things up. Is my thinking correct?
 
So I'm still confused about the security-user setting, and hope you can teach me more about how I could write to the directory if I am connecting as the samba user. 
 
For example, when I'm connecting from winxp and it prompts me for authentication, I enter the samba username and samba password. That gets me connected to the ubuntu machine, but what ubuntu user am I connected as? When I looked at the samba log it shows the user nobody.
 
Now I edited smb.conf again, changed security=user, and saved. I also found a website that said to add a line below security=user.
username map = /etc/samba/smbusers
 
Then create a file named /etc/samba/smbusers, and in that file, type the samba username = ubunutu username, to force the proper mapping. this may be unnecessary but you are welocme to try it if nothing else works.
 
on winxp, i ran cmd, then typed net use to see any shares that were setup. i had 1 pointing to ubuntu. I wanted to delete it to start over fresh, in case it was trying to connect to the Ubuntu server with an incorrect username. I only had one share shown, so I typed net use * /delete, to delete all, then confirmed my choice. 
 
back to the ubuntu machine. i restarted samba. 
back to winxp. opened file explorer to [\\ubuntu\sharename]("file://\\ubuntu\sharename") and it prompted me to authenticate. I entered my samba username & password
I could browse the files
I right clicked and chose create new test file. It worked!
 
back to the ubuntu machine. i opened the samba log file for my winxp machine name, and it said i was connecting as the correct user, so that is how the permissions were working correctly.
 
I don't really know which step was the magic one, maybe I had something else wrong in my smb.conf file and re-commenting everything related to password syncronization helped. 
I'm just glad to get this over with so I can move on.
 
Thanks again for all your help, and I hope my bout with insanity and complaints about nothing being explained well enough for newbies was taking with a grain of salt. That was my intent with this super long message, to help others learn too.
 
 
another note: while i was testing security=share and a mac osx computer was connected as nobody, it saved a file. the ownership of that file was nobody, and it screw up access for a second, so be sure to check that also, and learn about chown to change the permissions.

---

### Post by doas777 on 2010-06-22
> **NT4usB said:**
> [wag]
I've never tried ext4. Can Windows write to an ext4 share? Are you using ext4?
nope, samba abstracts the native file system away from the network interface, so that the client doesn't care about the fs on the server (and the server never really sees the clients OS, beyond the server string).

---

### Post by doas777 on 2010-06-22
> **Paddy Landau said:**
> I don't think that this makes any difference. My public folder is owned by root, and its permissions are read-write-access to everyone. The result is that everyone has access within the folder, but only root can delete the folder.

As I understand it, Samba provides access, and it's through Samba that people get access; either guest access, which means anyone with access to the LAN, or on a user-by-user basis.

that is not consistent with my findings, on any platform. share permissions stack atop filesystem permissions, so the user needs to be able to access the share for their access mode (R/W) and needs to have FS permissions that provide those privileges. what samba does do, is take over the create masks for new files and directories created within shares by a samba client.

perhaps nautilus-share is different, but this is the way it has always worked for classic smbd.

---

