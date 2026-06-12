---
title: "Connecting NAS with nfs :connection refused"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by myotis on 2008-04-15
I have asked this in the beginners section (as that is what I am) but help has dried up, so I have moved it here.

Reading through other threads I have done the following:

sudo apt-get install util-linux
sudo apt-get install portmap
sudo apt-get install nfs-common

And get the following when I try to mount the NAS

graham@Antec-Linux:~$ sudo mount -t nfs 192.168.1.11:/public /media/public
mount.nfs: mount to NFS server '192.168.1.11' failed: System Error: Connection refused

I then ran

sudo /var/lib/dpkg/info/nfs-common.postinst

Then

sudo aptitude update
sudo aptitude safe-upgrade
sudo dpkg-reconfigure nfs-common
sudo aptitude reinstall nfs-common


Still getting the same Connection refused error. Its Ubuntu 7.1 and QNap 109 pro

I'm afraid that the massive thread on nfs, just confuses me after extracting these commands, and would appreciate some more focused help.

Can anyone suggest the next thing I can try.

Many thanks,

Graham

---

### Post by Rizla on 2008-04-15
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I sorta had thsi problem last night when i changed ip's on my nas.

try running this command 

```

sudo exportfs -a

```

---

### Post by myotis on 2008-04-15
> **Rizla said:**
> **This post could be related to an Ubuntu bug filed at**:  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I sorta had thsi problem last night when i changed ip's on my nas.

try running this command 

```

sudo exportfs -a

```

Thanks, but I got a command not found error when I tried this :-(

Graham

---

### Post by Rizla on 2008-04-15
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **myotis said:**
> Thanks, but I got a command not found error when I tried this :-(

Graham

I'll have to check on that when i get home.

**I double checked my history and that was the command I ran to rexport my nfs info.  THen I remounted on the client PC and it mounted successfully. Make sure you typed it correctly "sudo exportfs -a " (not in quotes, make sure its NOT exportNFS its exportFS)  Thats about all i can help with this, i'm not anywhere near guru level to help you troubleshoot farther.**

---

### Post by myotis on 2008-04-15
> **Rizla said:**
> **This post could be related to an Ubuntu bug filed at**:  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				

I'll have to check on that when i get home.

**I double checked my history and that was the command I ran to rexport my nfs info.  THen I remounted on the client PC and it mounted successfully. Make sure you typed it correctly "sudo exportfs -a " (not in quotes, make sure its NOT exportNFS its exportFS)  Thats about all i can help with this, i'm not anywhere near guru level to help you troubleshoot farther.**

I'm afraid I did type it correctly, but it seems from searching on this command that exportfs needs installed, but on the server,  and I'm back being out of my depth.

Thanks for trying :-)

Graham

---

### Post by Rizla on 2008-04-16
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **myotis said:**
> I'm afraid I did type it correctly, but it seems from searching on this command that exportfs needs installed, but on the server,  and I'm back being out of my depth.

Thanks for trying :-)

Graham

if its not on the server (not sure why)  type sudo apt-get install exportfs

get really comfy with:

apt-get install
apt-get remove
aptitude install
aptitude remove

Whenever you try to install something new and it says somethings missing, it usually tells you whats missing and you can apt-get install it.

---

### Post by myotis on 2008-04-16
Thanks again, but still struggling here:

graham@Antec-Linux:~$ sudo apt-get install exportfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package exportfs


Graham

---

### Post by Bosk22 on 2008-04-16
Graham

Sound to me like you have not added the entry to your /etc/export file ! 

Until there is a line in this file on the server in the /etc/exports file that refers to the directory clients PC are "allowed" to mount remotely it will not work 

The line should on the 192.168.1.11 server should simply be

/public

Edit the file with vi or gedit (if you are using Gnome) or Kwrite (if you are using KDE)
 
You will need to be the 'root' user to edit this file so in a terminal window type

gksu gedit /etc/exports 

or

sudo vi /etc/exports

or 

sudo kwrite /etc/exports  

Bosk

---

### Post by Rizla on 2008-04-16
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **myotis said:**
> I'm afraid I did type it correctly, but it seems from searching on this command that exportfs needs installed, but on the server,  and I'm back being out of my depth.

Thanks for trying :-)

Graham

if its not on the server (not sure why)  type sudo apt-get install exportfs

get really comfy with:

apt-get install
apt-get remove
aptitude install
aptitude remove

Whenever you try to install something new and it says somethings missing, it usually tells you whats missing and you can apt-get install it.

---

### Post by myotis on 2008-04-16
> **Bosk22 said:**
> Graham

Sound to me like you have not added the entry to your /etc/export file ! 

Until there is a line in this file on the server in the /etc/exports file that refers to the directory clients PC are "allowed" to mount remotely it will not work 

The line should on the 192.168.1.11 server should simply be

/public

Edit the file with vi or gedit (if you are using Gnome) or Kwrite (if you are using KDE)
 
You will need to be the 'root' user to edit this file so in a terminal window type

gksu gedit /etc/exports 

or

sudo vi /etc/exports

or 

sudo kwrite /etc/exports  

Bosk

I admit to being confused here on the assumption that by server you mean the QNAP NAS, I don't really know how to edit the software on it and I there seems to be no reference to this in the QNAP manual.

Graham

---

### Post by Bosk22 on 2008-04-16
Graham

I am assuming from your reply that your "NAS" is a dedicated piece of hardware you have bought then and not another PC running Linux.

If that is the case then can you answer the following please .

1) Does the NAS have support for "Windows file sharing"
2) Does the NAS have support for "NFS file sharing" (Linux)
3) is there a web management interface where you tell it what folders/subdirectories you want to share
4) Can you access this interface 
5) Have you shared the folder /Public on the 192.168.1.11 NAS
6) Have you created user name and password on the Nas for this public folder

A lot of NAS servers provide support only for Windows file sharing as this is what most people have and it keeps the price low. Assuming that it supports Windows file sharing only then you need to mount using "samba" and NOT nfs.

The command in that case would be something like 

sudo mount -t cifs //192.168.1.11/public /media/public -o user=<ServerName>/<username>%<password>'

Replace the bits in < > brackets with the Servers Name or IP address and the Username and Password created on the NAS thought the web management interface

Note you may or may not yet have samba install on your ubuntu box

Regards

Bosk

---

### Post by myotis on 2008-04-16
Bosk

>I am assuming from your reply that your "NAS" is a dedicated piece of hardware you have bought >then and not another PC running Linux. 

I did say in the initial post that it was a QNAP 109Pro, but I realise you joined the thread half way through.


>1) Does the NAS have support for "Windows file sharing"

Not entirely sure what that is, but it "just works" with my Windows and Mac boxes.

>2) Does the NAS have support for "NFS file sharing" (Linux)

Yes and its enabled.

>3) is there a web management interface where you tell it what folders/subdirectories you want to share

Yes

>4) Can you access this interface 

Yes

>5) Have you shared the folder /Public on the 192.168.1.11 NAS

The Public folder is a default share with the QNAP and allows access to all users

>6) Have you created user name and password on the Nas for this public folder

I don't think it is possible to create a user name/password
 for this public folder

>A lot of NAS servers provide support only for Windows file sharing as this is what most people >have and it keeps the price low. Assuming that it supports Windows file sharing only then you >need to mount using "samba" and NOT nfs.

The QNAP manual specifically says to use NFS with linux and the commands I initially used to mount the NAS came out of the QNAP 

Although I can't mount the share on the NAS I can access it through Nautalis, but only read files and not write them, if that give a clue.

Thanks for the detailed reply.

Graham

---

### Post by Bosk22 on 2008-04-16
Graham

Sorry i missed the beginning of the post - Sometimes I am not to bright.

OK things to try

1) The manual says to use NFS for linux but for experiment sack try the samba mount and see if that works - Linux is quite happy to work with Windows shares and the end result is the same - you get to read an write your files. -  What is the result ?

2) Are you sure the public folder is set for unlimited access by anyone?

3) Looking at the online manual for your nas it appears to have a IP Filter capability - Is this set to allow full access from any IP address 

4) When you say you can see the files using Nautilus are you using the menu option places/network ? 

5) if the answer to 4 is yes is the NAS showing up as a Windows network server?

6) The fact that Nautilus can see the files but not write suggests it is a permission problem - try creating for the sack of experiment a new folder and sharing it out - Can you connect to this new folder?

7) Have you checked that the NFS Access Control on the NAS for the public folder is set to all (*) ?

Regards

Bosk

---

### Post by Rizla on 2008-04-17
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **myotis said:**
> I'm afraid I did type it correctly, but it seems from searching on this command that exportfs needs installed, but on the server,  and I'm back being out of my depth.

Thanks for trying :-)

Graham

if its not on the server (not sure why)  type sudo apt-get install exportfs

get really comfy with:

apt-get install
apt-get remove
aptitude install
aptitude remove

Whenever you try to install something new and it says somethings missing, it usually tells you whats missing and you can apt-get install it.

---

### Post by myotis on 2008-04-17
>Sorry i missed the beginning of the post - Sometimes I am not to bright.

Easy done

>OK things to try

>1) The manual says to use NFS for linux but for experiment sack try the samba mount and see if >that works - Linux is quite happy to work with Windows shares and the end result is the same - >you get to read an write your files. -  What is the result ?

sudo mount -t cifs //192.168.1.11/public /media/public -o user=<ServerName>/<username>%<password>'

Based on your earlier post I used this and it worked :-)

I have double clicked on a Open office file on the NAS, opened it, edited it, saved it, shut it down and reopened it.

Many thanks for this, it allows me to turn my dabble with Linux into a proper trial.

To stretch your help further, what do I need too add to the fstab file to make the sahre mount automatically.

Not sure how important the other questions are now, but I have answered them any way.

2) Are you sure the public folder is set for unlimited access by anyone?
Yes

3) Looking at the online manual for your nas it appears to have a IP Filter capability - Is this set to allow full access from any IP address 
Yes

4) When you say you can see the files using Nautilus are you using the menu option places/network ? 

I have used this and the server menu option

5) if the answer to 4 is yes is the NAS showing up as a Windows network server?


6) The fact that Nautilus can see the files but not write suggests it is a permission problem - try creating for the sack of experiment a new folder and sharing it out - Can you connect to this new folder?

I haven't tried this now as the Samba option seems to work and I can now read and write files to the NAS

7) Have you checked that the NFS Access Control on the NAS for the public folder is set to all (*) ?

Yes it is.


Many thanks again,

Graham

---

### Post by Bosk22 on 2008-04-18
Graham

Glad you got it working!!!!!

To answer your question about making it a permanent thing you need
to do the following

1) Create a text file somewhere on the local box (the root home director /root is best) containing the username and password to use (if any) for the remote share - Call it whatever you like.

2) Add a one line entry to the bottom of your /etc/fstab file as follows - But make a copy of it first just in case and be sure to change nothing else

//<ServerName Or IP address>/<sharename> <Path To Where You Want To Mount The Share Locally> cifs credentials=<Path To A File Containing Username And Password> 0 0

< > brackets are to be replaced with settings relevant to your systems

So for your system this would be something like this:-

//192.168.1.11/public /media/public cifs credentials=/root/passwordshares 0 0

"passwordshares" is the name of the text file in my example and takes the following form

username=myserver/myusername
password=mypassword

And thats it - To prove it works type "sudo mount -a" when or just reboot!!!!! 

Good luck 

Bosk

---

### Post by myotis on 2008-04-18
Thanks again,

Based on browsing the forum, I have actually added 

//192.168.1.11/Public /media/public  cifs username=*****,password=*****

to the fstab file, which is working fine, but I obviously don't have the  0 0 at the end and I have obviously added the user name and password directly into the fstab file.

Is there a "good practise" reason for storing the user name and password in a separate file?

Graham

---

### Post by Bosk22 on 2008-04-18
Graham

"Good practice reason"  - No - it just saves on the typing if you have a lot of mount points  and then change the password. By using a file as a reference you only have to make one change.

Also the /etc directory is usually readable (but not writable) by most users so its easy to learn the password stored in fstab - But if privacy is not an issue for you then either way works.

As to the 0 0 they are implied in your version of the line so do not worry about them. There just to much geek in my soul and I like to see them there is all - lol

Bosk

---

### Post by myotis on 2008-04-18
That all makes sense, but as I am a single user with a limited number of things to mount, it probably doesn't matter too much for me.

But good to know.

Thanks again,

Graham

---

