---
title: "Finding the path to a windows shared folder"
date: 2018-09-26
forum: Networking &amp; Wireless
---

### Post by webmiester on 2018-09-26
Hi everyone,

I want to mount a folder located on a Windows computer through the command line.  I can do it through the GUI, but I want to do it via command line.

the command line is as follows (Samba is already installed):

sudo mount -t cifs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,iocharset=utf8,file_mode=0777,dir_mode=0777


On the GUI, when I click on "Network Connections", I Get a Folder named "Windows Network", then when I click on that, I get a computer named "Computer One", Then When I click on Computer One, I see the folder "For Sharing"

In the Command line though, How do I write this as netbiosname/sharename?  First off if I put "Windows Network/Computer One", It cuts the command line and the computer stops at "Windows"...  The other question is, do I need to still put "Windows Network", in the first place?

So going back to my question... How do I find the path I need to put in the command line to mount this folder?  Thank you very much

---

### Post by Morbius1 on 2018-09-26
[1] Linux doesn't like spaces in things. It can handle it but it requires the user to do something extra-ordinary. So something like this:
> sudo mount -t cifs //Computer One/For Sharing ....
Becomes this when you replace the space with a **\040 **- that's a zero4zero:
```
sudo mount -t cifs //Computer\040One/For\040Sharing ....
```
If you stop placing spaces in the name of things your life in Linux will be far less stressful.

[2] mount.cifs has no idea what a netbios name is. That is a samba client thing which is why it works from your file manager.

If you are lucky your router will convert the netbios name to a host name. You might even be able to make it work if you have NetBIOS over TCP/IP enabled on the Windows machine. Should this be a problem please see my post here: [https://askubuntu.com/questions/663090/smbclient-finds-nas-but-mount-cant-find-it/1073444#1073444](https://askubuntu.com/questions/663090/smbclient-finds-nas-but-mount-cant-find-it/1073444#1073444)

---

### Post by webmiester on 2018-09-27
Thank you Morbius 1.  Do I still need to put the "Windows Network" into the command line?

---

### Post by Morbius1 on 2018-09-28
Nope. 

"Windows Network" is the incorrect label that Nautilus gives for "smb:///". That has no meaning in mount.cifs.

---

### Post by TheFu on 2018-09-28
From a security standpoint, you probably don't want to put credentials into a command line.  And user on the system can see the complete command line, passwords and everything else.

mount has a way to read those from a file.  Just be certain that file it put somewhere that only people who already know the credentials can see and nobody else.

Add an option like this to the mount:
```
credentials=/root/samba/romulus-music.credentials
```
I like to name the credential files with the hostname and the contents in the name.

The cded file needs 2 lines.
```
username=
password=

```
Since mount always runs as root, I'd make root the owner and 600 for the permissions.
I don't know how to specify ActiveDirectory stuff.

And a shortcut to avoid netbios resolution problems is to use the IP address. It isn't ideal, but Windows has a long history of working on tiny LANs where broadcasting "I'm here, I'm here" to every other machine on the LAN is fine. That doesn't work for internet-scale needs. There wouldn't be any bandwidth left over to actually transmit data.

---

### Post by webmiester on 2018-09-29
> **TheFu said:**
> From a security standpoint, you probably don't want to put credentials into a command line.  And user on the system can see the complete command line, passwords and everything else.

mount has a way to read those from a file.  Just be certain that file it put somewhere that only people who already know the credentials can see and nobody else.

Add an option like this to the mount:
```
credentials=/root/samba/romulus-music.credentials
```
I like to name the credential files with the hostname and the contents in the name.

The cded file needs 2 lines.
```
username=
password=

```
Since mount always runs as root, I'd make root the owner and 600 for the permissions.
I don't know how to specify ActiveDirectory stuff.

And a shortcut to avoid netbios resolution problems is to use the IP address. It isn't ideal, but Windows has a long history of working on tiny LANs where broadcasting "I'm here, I'm here" to every other machine on the LAN is fine. That doesn't work for internet-scale needs. There wouldn't be any bandwidth left over to actually transmit data.

What will my command lines look like with these options?
First for the credentials will it look like this:

sudo mount -t cifs smb://netbiosname/sharename /media/sharename -o iocharse t=utf8,file_mode=0777,dir_mode=0777 credentials=/root/home/user/filename.credentials

Then if I use IP addresses, should it look like then?:

sudo mount -t cifs smb://192.123.123.12/sharename /media/sharename -o iocharse t=utf8,file_mode=0777,dir_mode=0777 credentials=/root/home/user/filename.credentials

Is this correct?  Thank you

---

### Post by webmiester on 2018-09-29
> **TheFu said:**
> From a security standpoint, you probably don't want to put credentials into a command line.  And user on the system can see the complete command line, passwords and everything else.

mount has a way to read those from a file.  Just be certain that file it put somewhere that only people who already know the credentials can see and nobody else.


Well if I put the command line into the cron of the root user, then only root has access to these command lines and no one should be able to see them right?  Or is Cron visible to everyone?

---

### Post by webmiester on 2018-09-29
Can I add one more question pls?  Since this is on a windows machine, and Ill be putting permissions like 777 or 444 or 400... Is the account who mounted this drive considered the owner, or is the owner the main user on the windows device?   Then who is group?  Since I didnt specify which groups should be given access.  Are all the groups where the owner is part of being referred to by the 2nd number or is the setting in some sort of file? 

Thanks so much

---

### Post by Morbius1 on 2018-09-29
I took the liberty of fixing your mount command for missing commas, removing the smb://, and based on the info you provided so far:

```
sudo mount -t cifs //192.123.123.12/For\040Sharing /media/For\040Sharing -o iocharset=utf8,file_mode=0777,dir_mode=0777,credentials=/root/home/user/filename.credentials

```
[COLOR=#0000cd]**Sorry**[/COLOR], I was in fstab mode there. A \040 is required in fstab a "\ " is required for shell or quotes as TheFu suggested below.
```
sudo mount -t cifs //192.123.123.12/For\ Sharing  /media/For\ Sharing -o  iocharset=utf8,file_mode=0777,dir_mode=0777,credentials=/root/home/user/filename.credentials
```

The credentials file I assume lists the username as winusername.

If you add a file to the Windows share from Ubuntu:

** On Ubuntu it will be owned by root but have permissions of 777.

** On Windows it will be owned by winusername because that is the user who provided the credentials that made it possible to access the share.

---

### Post by TheFu on 2018-09-29
From the mount.cifs manpage:
```

       credentials=filename
           specifies a file that contains a username and/or password and
           optionally the name of the workgroup. The format of the file is:

                         username=value
                         password=value
                         domain=value

           This is preferred over having passwords in plaintext in a shared
           file, such as /etc/fstab. Be sure to protect any credentials file
           properly.
```

Also, agree that avoiding spaces in most things is much easier to work with. But if you must use them, just "quote the string".
So /media/For\040Sharing would be "/media/For Sharing" . Nesting of quotes is solved by multiple methods, either switching between single-quotes and double-quotes (there are caveats) or by escaping the inner quotes with \" for each quote.  

It is much easier just to avoid spaces or other special characters.  Some scripts will break with spaces, just depends if the person who wrote the script caught 100% of the locations that needed to be in quotes inside their script, but if they are like most Unix people, we've learned over the decades just to avoid spaces in all names.

---

### Post by webmiester on 2018-09-30
Thank you Morbius and TheFu, you are great teachers!

---

### Post by TheFu on 2018-09-30
Most syntax/options questions are answered in the manpages already on the system.  The hard part is knowing how to find them ( man -k {search term} ) and the best terms to search using which really takes practice to learn.

---

### Post by webmiester on 2018-10-10
> **TheFu said:**
> Most syntax/options questions are answered in the manpages already on the system.  The hard part is knowing how to find them ( man -k {search term} ) and the best terms to search using which really takes practice to learn.


Yeah, i often look up the man pages, but there are 2 things with man page which I dislike:

1). It's sometimes written in a way that I find difficult to understand and that I can't ask questions to it.

2) it often has loads of information that I don't need, so it gets confusing just figuring out what information I do need.

Thanks so much for your inputs.  I really appreciate it.

---

### Post by TheFu on 2018-10-11
It took me about 6 months of being forced to read manpages by my peers before things "clicked."  After that, the genius of that format became clearer.  It definitely takes time to get there and some manpages are poorly written.   

I miss the old days when the manpages had examples, but lots of noobs would copy/paste examples leading to system failures, so removal was probably a good thing, overall.  There are online command/option explainers.  Enter a command with all the options and it makes a graph of what that exact line should do using the manpages as source.  

Plus the problem that Unix skills are built up from nothing, so basic skills are necessary before doing intermediate or advanced work. All that takes time with the system and time sleeping on problems.

---

