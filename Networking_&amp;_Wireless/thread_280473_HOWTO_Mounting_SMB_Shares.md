---
title: "HOWTO: Mounting SMB Shares"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by dbott67 on 2006-10-19
[I][B]Update: November 18, 2007

[/B][/I]A few of the downsides on the Nexstar LX NAS device that I purchased is that:
1. It does not support CIFS
2. It does not support SATA drives (IDE only)
3. It is 10/100 Mbps (no gigabit)
4. It does not have any fault tolerance.  

It is, however, an inexpensive device that can be used to share data among many computers.

Anyhow, I have been in the process of upgrading my home network to gigabit and wanted to purchase a better NAS device that had some redundancy & expandability, as well as support for gigabit, CIFS and SATA drives (hot-swappable, no less).  I ended up purchasing a [Netgear (formerly Infrant) ReadyNAS NV+ 4250]("http://www.netgear.com/Products/Storage/ReadyNASNVPlus/RND4250.aspx") and am providing an update to my original instructions using CIFS rather than smbfs:

Steps 1 and 2 remain the same.

In step 3, test mount the share using CIFS as noted:

```
dbott@gutsy:~$ sudo mount -t cifs //192.168.1.2/Music /home/dbott/Music -o iocharset=utf8,file_mode=0777,dir_mode=0777
```Step 4 remains the same.

Step 5, add the mount point(s) to your /etc/fstab file:
```
//192.168.1.2/Music /home/dbott/Music   cifs  credentials=/root/.credentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.2/dbott /home/dbott/Data   cifs  credentials=/root/.credentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.2/Archive /home/dbott/Archive   cifs  credentials=/root/.credentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```The only issue that I encountered was with regards to UIDs.  My user account on Ubuntu (dbott) has a UID of 1000, while my user account on the NAS has a UID of 1004.  To fix this, I changed my Ubuntu UID to match the UID on the Netgear NAS using the following command:
```
sudo usermod --uid 1004 dbott
```After a couple of minutes and a reboot, everything was working properly.

[I][B]
Original Post: October 2006[/B][/I]

I purchased a NexStar LX NAS device and wanted to mount some of the shares on my linux computers.  I configured my NAS device with a static IP (192.168.1.2) and created a number of shares to store my data.  This process can be used to mount any SMB or Windows shared folder:

1. Install '**smbfs**' & '**smbclient**' (Samba File System & Samba client)
```
sudo apt-get install smbfs smbclient
```After installing the above, issue the command **smbclient -L 192.168.1.2 -U%** to generate a list of available shares (replace 192.168.1.2 with the IP or name of your SMB server):
```
dbott@thedrake:~$ smbclient -L 192.168.1.2 -U%

        Sharename       Type      Comment
        ---------       ----      -------
        PUBLIC          Disk
        Data            Disk
        Archive         Disk
        Music           Disk
        IPC$            IPC

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

```2. Create new folder for the 'mount point'.  In my case, I wanted the shared music folder to be mounted to the following location **/home/dbott/music**
```
cd ~
mkdir music
```3. Mounting the share from the command line (to verify that it works):

```
sudo smbmount //192.168.1.2/Music /home/dbott/music -o username=dbott,password=mysecretpassword,uid=1000,mask=000
```4. Un-mounting the share from the command line:

```
sudo smbumount /home/dbott/music
```5. Add the mount point to fstab (making it 'automatic'):

*[COLOR=Red]The unsafe way (fstab is world-readable, meaning that anyone can see your SMB username and password):[/COLOR]*
```
//192.168.1.2/Music /home/dbott/music   smbfs  auto,username=dbott,password=mysecretpassword,uid=1000,umask=000,user   0 0
```*[COLOR=Red]The better way (storing your username & password in a file only readable by root):[/COLOR]*
```
//192.168.1.2/Music /home/dbott/music   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
```**/root/.credentials** is a text file that contains your smb username and password.  To create the file, type:
```
sudo gedit /root/.credentials
```and add the following text:
```
username=your_smb_username
password=your_smb_password

```Now, make the file only readable by root:
```
sudo chmod 600 /root/.credentials
```6. At this point, you can either **reboot** or **reload** your fstab:
```
sudo shutdown -r now
``````
sudo mount -a
```7. Now, when I browse to **/home/dbott/music**, I have access to all the shared MP3s on my NAS device.

-Dave

---

### Post by barq on 2006-10-20
Thank you, this was really useful to me.

---

### Post by dbott67 on 2006-10-26
**_BROWSING SHARES FROM A GUI_**

Depending on which version of Ubuntu you use (Gnome, KDE, XFCE, etc.), you may not be able to graphically connect to a Samba share.

If you just want to connect to one from a command line, you'll need 'smbfs' (SMB file System) and 'smbclient' (SMB client).  Nautilus does allow browsing but there appears to be some known bugs when browsing via 'workgroup' or by 'computer name'.  Apparently, browsing by IP address work okay.  You can try installing 'linneighborhood' or [pyNeighborhood]("http://pyneighborhood.sourceforge.net/") to see if works better than Nautilus for browsing via GUI.

```
sudo apt-get intsall smbfs smbclient linneighborhood
```

You should be able to browse SMB shares from the command line (just substitute 192.168.1.2 with the IP address or hostname of your SMB server), using the following command:

```
smbclient -L 192.168.1.2 -U%
```

```
dbott@thedrake:~$ smbclient -L 192.168.1.2 -U%

        Sharename       Type      Comment
        ---------       ----      -------
        PUBLIC          Disk
        Data            Disk
        Archive         Disk
        Music           Disk
        IPC$            IPC

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
```

If that command works, you should be all set with 'LinNeighborhood'.  I just installed it & everything seems to work... just type **LinNeighborhood&** from the terminal to get started (the trailing '&' puts the process in the background and returns control to the terminal window).  See attached screenshot.

-Dave

---

### Post by dbott67 on 2006-11-17
Also, some issues arise because of the way SMB shares "announce" themselves to the network.  Generally, connecting via IP address works properly, but browsing by 'computer name' can occasionally fail.  Windows uses WINS service to allow users to browse by computer name (also known in Windows-speak as Netbios name).  WINS binds the computer name to the IP address.  For the most part, this has been superceded by DNS, which binds the fully-qualified domain name to the IP address. The problem is that DNS resolution requires that:

a) You're running a DNS server
b) Each client is registered in the DNS server

The problem here is that most people don't run their own DNS server and if you have any Windows computers on the network (or Samba shares), you really should have a WINS server or 'winbind' installed.

There is a package in the repositories called 'winbind' that will allow you to browse by computer name.

This info is provided by 'featherking' from [this thread]("http://www.ubuntuforums.org/showthread.php?t=288022"): 

```
sudo gedit /etc/nsswitch.conf
```

find this line (it may not be exactly that)

```
hosts:          files dns mdns
```

and add wins, so now it looks like

```
hosts:          files dns mdns wins
```

then install winbind
```

sudo apt-get install winbind
```

Now trying connecting to "Places->Network Servers".

-Dave

---

### Post by DerHesse on 2006-11-30
A nice guide!!! Thank you.

...but what if the Server holding the shares is Window and is domain member.


I tried with a local account on the Windows machine, but no chance.

[COLOR="Silver"]sudo smbmount //192.168.1.2/Music /home/dbott/music -o username=dbott,password=mysecretpassword,[/COLOR]uid=1000,mask=000

doesn't really make sense.

Do you see any chance to get that working?

---

### Post by coln_panic on 2006-12-02
> **DerHesse said:**
> 
...but what if the Server holding the shares is Window and is domain member.


so to clarify, you want to connect your ubuntu machine(a) to a windows box(b) share, where the (b) is a member of a domain?  this certainly should be possible, especially if you have admin rights on (b).  what version of windows is (b) running, what kind of share are you trying to connect to and how to you want to authenticate who can connect to the share(none - share level access, local accounts okay, domain accounts okay, other?)?

you also said that
```
sudo smbmount //192.168.1.2/Music /home/dbott/music -o username=dbott,password=mysecretpassword,uid=1000,mask=000
```didn't make sense to you, why not?

include any other information that you think may be helpful,

jay

---

### Post by adamkane on 2006-12-03
Great HOWTO. Too bad the thread name is so generic.

---

### Post by dbott67 on 2006-12-04
> **DerHesse said:**
> A nice guide!!! Thank you.

...but what if the Server holding the shares is Window and is domain member.


I tried with a local account on the Windows machine, but no chance.

[COLOR="Silver"]sudo smbmount //192.168.1.2/Music /home/dbott/music -o username=dbott,password=mysecretpassword,[/COLOR]uid=1000,mask=000

doesn't really make sense.

Do you see any chance to get that working?

From **bmedwar** in this [thread]("http://www.ubuntuforums.org/showthread.php?p=1844391#post1844391"):

> **bmedwar said:**
> Thanks.  It would be awesome to integrate this with the Places -> Connect to server... (or make it more obvious that connect to server is not doing an smbmount)

Here is what I did to make this work with domain authentication.

Mounting SMB Shares with domain authentication
==============================================

Add line in /root/.smbcreds, 'domain = <domain name>'.  This is used by smbclient, but ignored by smbmount.  For smbmount specify the domain as the workgroup on the command line.

List the available shares (helpful for determining upper/lower case names):
```
sudo smbclient -L bedwards2 -U% -A /root/.smbcreds
```

Mount from command line:
```
sudo smbmount //bedwards2/C$ /mnt/bedwards2_c/ -o workgroup=INSIDE,credentials=/root/.smbcreds,dmask=777,fmask=777

```

Mount in /etc/fstab:
```
//bedwards2/C$  /mnt/bedwards2_c smbfs  auto,workgroup=INSIDE,credentials=/root/.smbcreds,uid=1000,umask=000,user   0 0

```

---

### Post by marx2k on 2006-12-05
VERY basic question here...
I made a directory in ~/Desktop:
```

|-- RemoteShared
|   `-- UbuntuLivingroom
|       `-- Music
|           |-- Collection1
|           |-- Collection2
|           |-- Collection3
|           |-- Collection4
|           |-- Documents
|           |-- Pictures
|           `-- ReadWrite

```

My plan is to have one folder on my desktop with these remote SAMBA shares in it.

my /etc/fstab of the relevant section:
```

#SAMBA Shares
//192.168.11.8/MyMusic1 /home/marx2k/Desktop/RemoteShared/UbuntuLivingroom/Music/Collection1   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.11.8/MyMusic2 /home/marx2k/Desktop/RemoteShared/UbuntuLivingroom/Music/Collection2   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.11.8/MyMusic3 /home/marx2k/Desktop/RemoteShared/UbuntuLivingroom/Music/Collection3   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.11.8/MyMusic4 /home/marx2k/Desktop/RemoteShared/UbuntuLivingroom/Music/Collection4   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.11.8/MyDocuments /home/marx2k/Desktop/RemoteShared/UbuntuLivingroom/Music/Documents   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.11.8/MyPictures /home/marx2k/Desktop/RemoteShared/UbuntuLivingroom/Music/Pictures   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.11.8/shared /home/marx2k/Desktop/RemoteShared/UbuntuLivingroom/Music/ReadWrite   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0

```

And everything mounts fine.  However, instead of just the one folder with everything in it, I get that folder with everything in it PLUS a drive icon for each share that I mount on my desktop in random locations.

How do I keep Ubuntu from throwing those extra icons on my desktop automatically?

---

### Post by dbott67 on 2006-12-06
There is a setting in **gconf-editor** that allows volumes to be hidden/visible on the desktop.  From a terminal, type:
```
gconf-editor
```

Browse to **/apps/nautilus/desktop** and uncheck "**volumes_visible**" (see attached screen shot).

-Dave

---

### Post by marx2k on 2006-12-07
A-ha! That did help. Thank you! I appreciate the support.

---

### Post by zisteph on 2007-01-25
Hi,

First of all, thanks for sharing that, it's been a great help to the newbie that I am! :o 

I've encountered one issue though... The mounting worked beautifully when I was "on site" (i.e. on the campus, where the server is located and where I am able to access it through the local network) but the connexion fails when I am at home... The connexion fails when I do it manually, or times out at boot.

Any idea why it should fail? Any way of fixing it?

Thanks a lot,

Stephane

---

### Post by dbott67 on 2007-01-26
Unless you have some sort of direct connection to the campus LAN (via VPN or other sort of connection) your computer would not be able to "see" the campus servers, as they would be protected by some sort of firewall.

The only way to "fix" it, is to find out if the campus has some sort or remote access.  For this, you would need to talk to the network admins at the university.

-Dave

---

### Post by zisteph on 2007-01-26
yep, that's what I just did and it turns out that's exactly what it is... :) 

Thanks a lot for your answer and your patience with my lack of knowledge... Sounds like I'll learn plenty of things just because I switched to Linux! :P

---

### Post by oscarmiranda on 2007-02-23
I am having problems to mount...
if i do
[B]$ sudo smbmount //machine/g$ /mnt/g/ -o username=administrator,workgroup=workgroup,password=<thepassword>,uid=1000,mask=000
[/B]
cli_negprot: SMB signing is mandatory and we have disabled it.
1477: protocol negotiation failed
SMB connection failed


but when I try the smbclient stuff like this:
$ smbclient //machine/g$ -U administrator -W workgroup
it works. Anyone know what's the problem? and how to make the smbmount work?

---

### Post by steve101101 on 2007-02-25
This is what i get after typing the following #smbclient -L SERVER -U%

steve@steve-desktop:~$ smbclient -L SERVER -U%
Connection to SERVER failed
steve@steve-desktop:~$ smbclient -L 192.168.1.101 -U%
Domain=[MARCUSHOUSE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 132.128.1.141 failed (Called name not present)
session request to 132 failed (Called name not present)
Domain=[MARCUSHOUSE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            ------
        SERVER                     server
        STEVEN               Steve's Computer

        Workgroup            Master
        ---------            -------
        MARCUSHOUSE          SERVER


PLEASE HELP

---

### Post by steve101101 on 2007-02-26
i figured it out. i had a bad password so my windows computer kept blocking my access. thanks for a great guide.

---

### Post by steve101101 on 2007-02-26
When i am trying mount a shared folder i get...

root@steve-desktop:~# sudo smbmount //Server/SharedDocs /home/steve/music -o username=secret,password=secret
5444: Connection to Server failed
SMB connection failed


please help

---

### Post by steve101101 on 2007-02-27
In order to use windows names instead of ip address you need to go to this site for a step by step directions.

[http://ubuntuforums.org/showthread.php?t=88206&highlight=resolve+netbios+hostname](http://ubuntuforums.org/showthread.php?t=88206&highlight=resolve+netbios+hostname)

---

### Post by Jeremiah478 on 2007-03-08
:)  Thanks for the HowTo, it was a great help!

---

### Post by dimeotane on 2007-03-09
Yea.. some good info here.  This is the first time I've come across the info on needing to edit  /etc/nsswitch.conf to add wins to the hosts line.  

I think smb is an aspect of Ubuntu that is still rather flakey... users migrating from windows are going to be very frustrated that it doesn't "just work".


If I access my sharing through places-->network servers I can see the files, but it won't let me play videos from my old windows XP share.  I find it needs to be mounted to work properly. 

I've been trying to make a launcher on my desktop to mount my sharing from my windows box.  I made a launcher icon with this command:

$ sudo smbmount //VAIO/vaio-shared /mnt/VAIO/ -o username=dimeo,password=secret,uid=1000,mask=000

It crashed my laptop when I double clicked on it.  The whole system froze and I had to hold down the powerbutton to reboot.  The same command works like a charm when entered directly into the terminal command line.  

I don't want to have to type the command every time, and my launcher crashes the system, so next I suppose I can try adding the file share to my fstab?!

Ubuntu appears to be promoting itself to the average windows user to "make the switch".... Ubuntu has a lot going for it... but not smb 
after doing a right click "share" in windows and then on Ubuntu finding they have to text edit kinds of config files... they're gonna switch back to windows!

---

### Post by jgpaiva on 2007-03-14
Great HOWTO, thanks a lot!!
I only have one question. By following this howto, i can mount my windows disk on my ubuntu machine and i can read it. The problem is that to write to it, i need to *sudo*.
So, how can i change the write/read privileges for my user so that i can write without being logged in as root? (notice that chmod apparently has no effect on a mounted disk)

---

### Post by jgpaiva on 2007-03-14
Ok, found the solution by reading the *smbmount* manual.
For reference, here's how i did it:

sudo smbmount //name-of-remote-computer/name-of-folder /home/my-user/folder -o **uid=name-of-linux-user**

---

### Post by bananabob on 2007-03-25
Thanks so much. Samba has always been a mystery to me. But with a fresh install of Ubuntu on two "new" machines and following your instructions I now understand how it works.

---

### Post by bananabob on 2007-03-30
Well I understand the Samba bit. But now I am having trouble with my mounts
In /etc/fstab I have the following

> //thorium/bananabob /mnt/thorium smbfs auto,credentials=/root/.credentials,uid=1000,umask=000,user 0 0

But the automount does not work.
When I type in 

> sudo smbmount //thorium/bananabob /mnt/thorium -o credentials=/root/.credentials,uid=1000,mask=000

The mount works.

So what is wrong with the /etc/fstab?

---

### Post by mynis on 2007-06-11
```
daniel@daniel-desktop:~$ smbclient -L 192.168.1.101 -U%
Domain=[MSHOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine 192.168.1.101.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.1.101 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[MSHOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------
        SERVER-X             server

        Workgroup            Master
        ---------            -------
        MSHOME               SERVER-X
daniel@daniel-desktop:~$ 
```

i know someone posted this error already but my windows isn't passworded

---

### Post by twistedtwig on 2007-07-14
Hi all,

I have the smb connection working great.  I can auto mount it and view all the files, but I can not delete them.  I have even tried using the username root with the admin password of the server.  also used the username and password of the normal user on the server.

//192.168.10.1/media /media/bettyMount smbfs auto,username=root,password=123456t,uid=root,umask=777,user=root

this will let me in but not edit or delete the files.

Sorry to not be able to sort this.  Hope some can help me.

thanks

---

### Post by dbott67 on 2007-07-14
What is the file-system that you are trying to mount (ext3, FAT, NTFS, etc.)?

-Dave

---

### Post by jdburto on 2007-07-14
Before mounting SMB shares, be sure that the smbfs package is installed. 

This should be obvious, but if you don't have it, you will get the following non-obvious error message about it when you check dmesg.

**smbfs: mount_data version 1919251317 is not supported**

Thanks to debian-adminstration.org for the advice.

[http://www.debian-administration.org/articles/165](http://www.debian-administration.org/articles/165)

---

### Post by twistedtwig on 2007-07-16
Hi,

thanks for the quick response... sorry was doing a charity bike ride yesterday so was not able to reply...

its is an ext3 file system on the server which is accessible from a windows share:

[media]
comment=bleh
path = /mnt/media
public = yes
read only = no
writeable = yes



Thanks for the help

---

### Post by charles.g.moore on 2007-07-16
Could someone please take a look at my post here:
[http://ubuntuforums.org/showthread.php?t=502378](http://ubuntuforums.org/showthread.php?t=502378)

Tell me what you think...

---

### Post by twistedtwig on 2007-07-20
Hi I have given the drive info... if you have time would you be able to look at this please?

Thank you kindly for your time and effort.

:)

---

### Post by Krydahl on 2007-07-22
Hi - followed your howto and it worked fine, thanks. It did create a link on the desktop to the server which I don't really want. Is there any way to remove this?

---

### Post by dbott67 on 2007-07-22
@krydahl: Follow the steps in post #10 in this thread:
[http://ubuntuforums.org/showthread.php?p=1852633#post1852633](http://ubuntuforums.org/showthread.php?p=1852633#post1852633)

@twistedtwig: Sorry for the delay.

Can you post a permissions/owner/group listing of some of the files on the shared directory using the command **ls -all**?

Note that I am logged in as 'dbott' and my permissions are 'rwx'

```
dbott@feisty:~/data$ ls -all
total 218165
drwxr-xr-x   1 dbott root      4096 2007-07-22 06:39 .
drwxr-xr-x 103 dbott dbott     8192 2007-07-22 08:45 ..
-rwxr-xr-x   1 dbott root    936061 2004-02-21 12:22 2000-2003 Library Board_NoClock.jpg
-rwxr-xr-x   1 dbott root     79712 2005-02-25 07:35 2004_T4.jpg
-rwxr-xr-x   1 dbott root     16896 2005-03-11 00:17 2004 Tax Slips & Donations.xls
-rwxr-xr-x   1 dbott root      6125 2005-07-01 23:54 50000 Loan.txt
-rwxr-xr-x   1 dbott root     82432 2005-08-03 08:14 50000 Loan.xls
-rwxr-xr-x   1 dbott root       629 2003-07-07 03:20 Remote-5900.vnc
-rwxr-xr-x   1 dbott root   1322296 2004-12-25 16:31 6_917282c.pdf
drwxr-xr-x   1 dbott root      4096 2006-01-01 01:59 Adobe
-rwxr-xr-x   1 dbott root     50688 2004-09-07 00:07 Alcatel.doc
-rwxr-xr-x   1 dbott root   9527821 2003-11-18 22:44 allied_forces_512k.wmv
-rwxr-xr-x   1 dbott root   3344384 2005-06-25 05:17 Apple_Switch_Parody_DivX.av
```

You need to make sure that at least one of the following conditions are true:

1. You are the owner of the file and have RWX permissions.
2. You are in a group that has RWX permissions.
3. You set the 'others' permission to RWX.

The 2 commands required would be chown (to change ownership) and chmod (to change permissions).  Refer to the man pages for full details.

-Dave

---

### Post by Krydahl on 2007-07-22
Excellent, thanks. I should have read the thread more thoroughly.

---

### Post by jimrz on 2007-07-22
great HOWTO ... thank you ):P

---

### Post by twistedtwig on 2007-07-23
Hi,

I had them set up like my web server to start with the ls for two folders are:

drwxr-xr-x 25 nobody nogroup    4096 2007-07-21 09:44 .
drwxrwxrwx 12 nobody nogroup    4096 2007-07-20 23:16 ..
drwxr-xr-x  3 nobody nogroup    4096 2007-04-08 09:16 ACE
drwxr-xr-x  2 nobody nogroup    4096 2007-05-13 14:15 Arun House
drwxr-xr-x  2 nobody nogroup    4096 2006-11-06 10:03 Boys-Maths
drwxr-xr-x  2 nobody nogroup    4096 2007-05-02 17:12 Car Crash pegeot 205
-rwxr--r--  1 nobody nogroup 1354761 2007-05-02 20:21 Connect.pdf
drwxr-xr-x  2 nobody nogroup    4096 2007-05-22 21:25 Copy of My Received Files
drwxr-xr-x  3 nobody nogroup    4096 2007-05-22 21:25 Copy of Visual Studio 2005
drwxr-xr-x  2 nobody nogroup    4096 2007-07-21 10:30 CV
-rwxr--r--  1 nobody nogroup     195 2006-12-31 15:22 dale music list.txt
drwxr-xr-x  2 nobody nogroup    4096 2006-12-17 15:09 Dale Yu Gi Oh pics
-rwxr--r--  1 nobody nogroup    1680 2007-07-19 23:27 Default.rdp
-rwxr--r--  1 nobody nogroup      74 2007-05-22 21:25 desktop.ini
drwxr-xr-x  4 nobody nogroup    4096 2006-11-05 12:35 education
drwxr-xr-x  2 nobody nogroup    4096 2007-02-15 23:14 House 30 oak tree way
-rwxr--r--  1 nobody nogroup 2169910 2007-05-02 20:02 Manual_DP500_English.pdf
drwxr-xr-x  2 nobody nogroup    4096 2007-05-22 21:25 My Music
drwxr-xr-x  2 nobody nogroup    4096 2007-05-22 21:25 My Pictures
drwxr-xr-x  2 nobody nogroup    4096 2007-05-14 19:29 My Received Files
-rwxr--r--  1 nobody nogroup     392 2007-07-19 07:32 My Sharing Folders.lnk
drwxr-xr-x  2 nobody nogroup    4096 2007-05-14 19:29 My Videos
drwxr-xr-x  4 nobody nogroup    4096 2007-05-22 21:35 Norton Ghost V10 - Recory Images
drwxr-xr-x  4 nobody nogroup    4096 2007-07-21 09:44 personal
drwxr-xr-x  4 nobody nogroup    4096 2007-05-22 21:56 RECYCLER
drwxr-xr-x  2 nobody nogroup    4096 2007-02-26 19:55 Ring tunes - theme tunes
drwxr-xr-x  2 nobody nogroup    4096 2007-05-13 15:36 shak images
drwxr-xr-x  2 nobody nogroup    4096 2007-05-13 19:43 Ubuntu images
drwxr-xr-x  2 nobody nogroup    4096 2007-05-25 20:01 Updater5
drwxr-xr-x  2 nobody nogroup    4096 2007-06-06 18:16 Vectra Sale 07
drwxr-xr-x  8 nobody nogroup    4096 2007-06-05 19:43 Visual Studio 2005



drwxrwxrwx  12 nobody nogroup  4096 2007-07-20 23:16 .
drwxr-xr-x   4 root   root     4096 2006-08-28 17:31 ..
drwxr-xr-x   8 nobody nogroup  4096 2007-06-01 19:57 Charlotte
drwxr-xr-x   4 nobody nogroup  4096 2007-04-30 16:24 Dale
drwxrwxrwx   4 nobody nogroup  4096 2007-07-19 21:05 downloaded
drwxr-xr-x  25 nobody nogroup  4096 2007-07-21 09:44 Jon
drwx--x--x   2 nobody nogroup 16384 2006-08-24 22:39 lost+found
drwxrwxr-x 696 nobody nogroup 16384 2007-06-27 07:46 Music
drwxrwxr-x  15 nobody nogroup  4096 2006-12-25 10:53 Photos
drwxrwxr-x   5 nobody nogroup  4096 2007-06-18 22:02 Pictures
drwxrwxrwx   2 nobody nogroup  4096 2007-07-19 21:05 runningtorrent
drwxr-xr-x   5 nobody nogroup  4096 2007-05-02 22:13 Videos

I am at a bit of a loss.. will have a play with those permissions very soon

Thanks

---

### Post by dbott67 on 2007-07-23
> **twistedtwig said:**
> Hi,

I had them set up like my web server to start with the ls for two folders are:

drwxr-xr-x 25 nobody nogroup    4096 2007-07-21 09:44 .
drwxrwxrwx 12 nobody nogroup    4096 2007-07-20 23:16 ..
...

I am at a bit of a loss.. will have a play with those permissions very soon

Thanks

I think this is your problem.  By design, Apache creates the user 'nobody' and the group 'nogroup' and assigns them as the default owner to any website you create.

I'm no expert in this area and what I'm proposing may have severe security repercussions if the web server is 'facing the internet' (i.e. anyone on the internet can access it), so take this advice for all that you paid for it! :)

There are a few options available:

1. Change ownership of the files & folders to your user
2. Add your user account to the 'nogroup' group and then use chmod to allow the group 'nogroup' RWX access.

You might also want to create a new thread called "permissions help" and pose a new question similar to this:

[I]I have a website that contains a bunch of files that I wish to also mount as a SMB directory according to the HOWTO in this thread (link back to this thread).

The default ownership & permissions are as follows:

```
 drwxr-xr-x 25 nobody nogroup    4096 2007-07-21 09:44 .
drwxrwxrwx 12 nobody nogroup    4096 2007-07-20 23:16 ..
drwxr-xr-x  3 nobody nogroup    4096 2007-04-08 09:16 ACE
drwxr-xr-x  2 nobody nogroup    4096 2007-05-13 14:15 Arun House
drwxr-xr-x  2 nobody nogroup    4096 2006-11-06 10:03 Boys-Maths
drwxr-xr-x  2 nobody nogroup    4096 2007-05-02 17:12 Car Crash pegeot 205
-rwxr--r--  1 nobody nogroup 1354761 2007-05-02 20:21 Connect.pdf
drwxr-xr-x  2 nobody nogroup    4096 2007-05-22 21:25 Copy of My Received Files
drwxr-xr-x  3 nobody nogroup    4096 2007-05-22 21:25 Copy of Visual Studio 2005
drwxr-xr-x  2 nobody nogroup    4096 2007-07-21 10:30 CV
-rwxr--r--  1 nobody nogroup     195 2006-12-31 15:22 dale music list.txt
drwxr-xr-x  2 nobody nogroup    4096 2006-12-17 15:09 Dale Yu Gi Oh pics
-rwxr--r--  1 nobody nogroup    1680 2007-07-19 23:27 Default.rdp
-rwxr--r--  1 nobody nogroup      74 2007-05-22 21:25 desktop.ini
drwxr-xr-x  4 nobody nogroup    4096 2006-11-05 12:35 education
drwxr-xr-x  2 nobody nogroup    4096 2007-02-15 23:14 House 30 oak tree way
-rwxr--r--  1 nobody nogroup 2169910 2007-05-02 20:02 Manual_DP500_English.pdf
drwxr-xr-x  2 nobody nogroup    4096 2007-05-22 21:25 My Music
drwxr-xr-x  2 nobody nogroup    4096 2007-05-22 21:25 My Pictures
drwxr-xr-x  2 nobody nogroup    4096 2007-05-14 19:29 My Received Files
-rwxr--r--  1 nobody nogroup     392 2007-07-19 07:32 My Sharing Folders.lnk
drwxr-xr-x  2 nobody nogroup    4096 2007-05-14 19:29 My Videos
drwxr-xr-x  4 nobody nogroup    4096 2007-05-22 21:35 Norton Ghost V10 - Recory Images
drwxr-xr-x  4 nobody nogroup    4096 2007-07-21 09:44 personal
drwxr-xr-x  4 nobody nogroup    4096 2007-05-22 21:56 RECYCLER
drwxr-xr-x  2 nobody nogroup    4096 2007-02-26 19:55 Ring tunes - theme tunes
drwxr-xr-x  2 nobody nogroup    4096 2007-05-13 15:36 shak images
drwxr-xr-x  2 nobody nogroup    4096 2007-05-13 19:43 Ubuntu images
drwxr-xr-x  2 nobody nogroup    4096 2007-05-25 20:01 Updater5
drwxr-xr-x  2 nobody nogroup    4096 2007-06-06 18:16 Vectra Sale 07
drwxr-xr-x  8 nobody nogroup    4096 2007-06-05 19:43 Visual Studio 2005



drwxrwxrwx  12 nobody nogroup  4096 2007-07-20 23:16 .
drwxr-xr-x   4 root   root     4096 2006-08-28 17:31 ..
drwxr-xr-x   8 nobody nogroup  4096 2007-06-01 19:57 Charlotte
drwxr-xr-x   4 nobody nogroup  4096 2007-04-30 16:24 Dale
drwxrwxrwx   4 nobody nogroup  4096 2007-07-19 21:05 downloaded
drwxr-xr-x  25 nobody nogroup  4096 2007-07-21 09:44 Jon
drwx--x--x   2 nobody nogroup 16384 2006-08-24 22:39 lost+found
drwxrwxr-x 696 nobody nogroup 16384 2007-06-27 07:46 Music
drwxrwxr-x  15 nobody nogroup  4096 2006-12-25 10:53 Photos
drwxrwxr-x   5 nobody nogroup  4096 2007-06-18 22:02 Pictures
drwxrwxrwx   2 nobody nogroup  4096 2007-07-19 21:05 runningtorrent
drwxr-xr-x   5 nobody nogroup  4096 2007-05-02 22:13 Videos
```What's the best way to allow myself RWX access but keep the website safe from the bad guys?[/I]   

Hope this helps

-Dave

---

### Post by NeillHog on 2007-07-23
Thanks

I got as far as mounting and received the following message
7002: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

I know that the user name and password are correct as I use them when I visit the share from network places. Here is the output from

smbclient -L 192.168.178.29 -U%

Domain=[HOGARTH] OS=[Unix] Server=[Samba 3.0.11]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN 1         Disk
        DISK 1          Disk      For everyone
        music           Disk      All our music
        ADMIN 2         Disk
        DISK 2          Disk      For everyone
        music~1         Disk      All our music
        IPC$            IPC       IPC Service ()
        ADMIN$          IPC       IPC Service ()
Domain=[HOGARTH] OS=[Unix] Server=[Samba 3.0.11]

        Server               Comment
        ---------            -------
        NSLU_1

        Workgroup            Master
        ---------            -------
        HOGARTH              NSLU_1
        MSHOME               NEILLSPC


Thanks for any help.

Neill

---

### Post by NeillHog on 2007-07-23
Sorry posted to the wrong thread
Neill

---

### Post by maharbA on 2007-07-26
Great HowTo -- exactly what I need.

One problem, though :(
When I type "sudo mount -a" my windows share is mounted (thanks to you all) exactly where I want it, how I want it.
But when I reboot, the share is not mounted. In other words, every time I restart my computer, I have to open a terminal and type "sudo mount -a" and enter my password.

What can I do to auto-mount on startup?

PS: here is the relevant line in my /etc/fstab"
//new_dell/EXTERNAL\040(G) /home/ganco/G_Drive   smbfs  auto,defaults,user,uid=ganco   0 0

(from what I understand, "**auto**" is supposed to mount the share on startup, "**defaults**" is used because the share  does not require a password, "**user**" because I don't want to have to be root, and "**uid=ganco**" gives me (ganco) read/write privileges.)

PPS: for anyone who is trying to access a windows share with funky characters in its name (in my case, the share is called EXTERNAL (G) ):
In the terminal, try putting quotes around the share's name (eg: //new_dell/"EXTERNAL (G)" )
In fstab, try putting \040 (backslash zero four zero) instead of a space

---

### Post by gangolli on 2007-07-26
Others (see [this thread]("http://ubuntuforums.org/showthread.php?t=331661")) have reported that using either of the two forms of specifying authentication in /etc/fstab seems to be required in order for the boot-time smbfs mounts to work.

---

### Post by nmenefee on 2007-08-02
I'm a beginner Ubuntu user, and have been working with it for about a week.  

I need some help permanently mounting my SMB shares.  I've attempted to mount them through the command line, using the instructions in this post, and have also tried LinNeighborhood with no success.  I think the fact that my SMB shares lie within a workgroup may be causing the difficulties.  

I can mount the shares through the Network File Browser within Ubuntu, and they can be located and navigated to.  But of course that doesn't get them mounted to a directory.  

Details on what I am trying to mount - 
External Hard Drive which is shared from a Mac within a Workgroup.  

Thanks in advance!

---

### Post by thexaspect on 2007-08-04
Hey there, thanks for the guide, I'm having a bit of a problem, though. I've got smbfs and smbclient installed and whatnot, i can read my server via the Places > Connect to server > (i can mount my server to a folder on the desktop). i've since unmounted it from there to try this, and when i input:
```
smbclient -L 192.168.2.6 -U%
```

it spits out:
```
Domain=[BOB] OS=[Unix] Server=[Samba 2.2.8a-ja-1.1]

        Sharename       Type      Comment
        ---------       ----      -------
        lp              Printer   Network Printer for Windows
        info            Disk      TeraStation utilities
        share           Disk      TeraStation folder
        IPC$            IPC       IPC Service (TeraStation)
        ADMIN$          IPC       IPC Service (TeraStation)
Domain=[BOB] OS=[Unix] Server=[Samba 2.2.8a-ja-1.1]

        Server               Comment
        ---------            -------
        SPACIOUSNESS         TeraStation
        TRANQUILITY          

        Workgroup            Master
        ---------            -------
        BOB                  SPACIOUSNESS

```

as you can see, i'm using a terastation, and i can't seem to get it to find the share. when i try, it gives me this:

```
x@tranquility:~$ sudo smbmount //192.168.2.6/Share/music/ /home/x/music -o uid=1000,mask=000
Password: 
9948: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

```

any ideas?

edit: PS i've tried all kinds of different combinations of server names/ip's/folders/etc. the server is also setup to have no password for internal network users and has a static ip. thanks =)

---

### Post by Hase on 2007-08-04
Great tutorial! Thanks!

---

### Post by jbysmith on 2007-08-23
Good tutorial.  Normally I'd just connect via Nautilus and go, but going that way doesn't let most programs work properly.  (Opening an MP3 on a network share for example)  This way lets me access remote files just like normal.

I do have one question though.  When I create a SMB connection via Nautilus, it allows me to give it a custom name aside from the share name.

I have three file servers, all of which have a general purpose share called "Storage".  With Nautilus, I'd just call the connections "Storage on Server1" and so on.

Mounting via fstab however only gives the share name.  It comes back as "storage", "storage (2)', and "storage (3)".   A little confusing. 

Is there any way to make it show a custom name for that?

*Edit:  Ignore this question.  Instead of going via fstab, I made a boot script to execute the smbmount command as you explained originally.  Nautilus is playing nicely now.*

---

### Post by maharbA on 2007-08-26
Something weird:

I followed this guide and, with a bit of help from others, got my 2 shared network drives to mount automatically on login. Great.

Recently, though, one drive does not want to mount on login. I can use "sudo mount -a" and it pops up. It's weird because the other drive _does_ mount automatically -- and their fstab entries are identical.

The only thing that has changed (and I can't be sure it happened at the same time) is that I have installed Compiz Fusion using XGL (on ATI vid card). But still, if one drive mounts, shouldn't they both mount?

Weird

---

### Post by punkrokk on 2007-08-26
awesome post dbott67,

---

### Post by senor_smile on 2007-08-27
> **dbott67 said:**
> From **bmedwar** in this [thread]("http://www.ubuntuforums.org/showthread.php?p=1844391#post1844391"):

I have tried this yet am still unable to get a share mounted from a computer on a domain.

```
shaun@shaun-laptop: sudo smbclient -L //10.1.1.131 -U% -A /root/.smbcreds
Domain=[PERFORMANCE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 10.1.1.131 failed (Called name not present)
session request to 10 failed (Called name not present)
Domain=[PERFORMANCE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------
        Workgroup            Master
        ---------            -------

```

when I try the smbmount it asks me for the password but no username, and tell me once again that authentication has failed.  HELP!

My laptop is connected to the same network, yet obviously not authenticated on the windows Network.  The server is running Windows 2003 and the computer that I'm trying to connect to is running windows xp.  I am able to do a "connect to server" entering the domain, user and pass and can access that way.  

thanks

---

### Post by saj0577 on 2007-08-29
ERROR MESSAGE IN TERMINAL:

saj@saj-laptop:~$ sudo smbmount //192.168.0.12/disk /media/shared/ -o username=mine,password=thepassword,uid=1000,mask=000
7821: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


saj@saj-laptop:~$ sudo smbmount //192.168.0.12/disk /media/shared/ -o username=mine,password=thepassword
7821: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


Anyone know where i went wrong? On this machine i have smbfs smbclient but on the server one i only installed smbfs is that my problem?

Thanks In advance
Saj

---

### Post by saj0577 on 2007-08-29
I right clicked the folder and clicked connect has this mounted the folder or if the computer that has the folder on it is turned off will i have to re-connnect it this way everytime i want to use those files?

Saj

---

### Post by d_b on 2007-09-16
I have the same enclosure (Vantec NexStar LX).   I can mount the drive fine using smbmount or Nautilus, but the transfer speeds are terrible!

It takes about 1/2 hour to copy a 180mb file from the NAS to my local hard drive (I'm getting around 150kb/s download rates).   Copying files over to the NAS drives is also terribly slow (copying my USB backup drive (about 40gb) took about 36 hours.    Loading up my music library in QuodLibet takes all day, and I can hardly stream MP3s without hearing breaks in the music once in a while. 

Any thoughts on why the speed is so bad?  The same drive accessed from a Windows box performs much better (I'd say around 2-3MB/s)

My setup is the following:

Vantec NexStar LX --> Linksys WR45G router --> Thinkpad X60 (Intel Pro Wireless)

d.

---

### Post by PryGuy on 2007-09-17
Hello there! Nice tutorial but I have a problem here. smbmount ```
sudo smbmount //192.168.0.1/Bases /media/bases -o username=username,password=password,uid=1000,mask=000

```works smooth but when I try to mount the same resource with fstab ```
//192.168.0.1/Bases /media/bases smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
```sudo mount -a says 'Could not resolve mount point /home/peter/bases'. Where's my problem?

192.168.0.1 is Ubuntu Feisty, share is on FAT32 if it is important. security=share

---

### Post by offchance on 2007-09-17
I get the following message for every attempt to mount my smb share.

```
23992: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
```

I can mount it in pyNeighborhood but I can't use that to see/access any files. 

any suggestions?

---

### Post by senor_smile on 2007-09-17
I'm no expert, but I think someone will be able to help with a little more information.  

Let us know:

-what exactly are you typing to try to mount it.  
-where is the disk that you're trying to mount? (i.e. on a Windows XP home machine with file sharing on, in a Windows Domain on a server, etc.)

I know we'll be able to give some suggestions based on my experience in the past with other ubuntu forum members.  

-shaun

---

### Post by kooldino on 2007-09-26
This works well, thanks.

I just have one issue.  When my windows server is inaccessible for whatever reason (be it  powered off, etc) my Kubuntu box will hang during boot due to not being able to access the share.

Is there some kind of timeout or bypass I can easily set up to fix this?

---

### Post by kooldino on 2007-09-29
Hello?

---

### Post by dbott67 on 2007-09-29
I don't know anything about this, but I did find a similar app called 'autofs' that has a couple of similar options that may be useful:
--timeout 
--ghost

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

[http://gentoo-wiki.com/HOWTO_Auto_mount_filesystems_(AUTOFS](http://gentoo-wiki.com/HOWTO_Auto_mount_filesystems_(AUTOFS))

The **--timeout** option in auto.master tells the automounter to unmount the file systems after (in this case) 5 seconds of inactivity. There are many discussions on the internet about whether this should be very short (several seconds) or long (a minute or more). That discussion is outside the scope of this document. 
The **--ghost** option tells the automounter to create "ghost" versions (i.e. empty directories) of all the mount points listed in the configuration file (in this case [COLOR=green][FONT=monospace]/etc/autofs/auto.auto[/FONT][/COLOR]), regardless of whether any of the file systems is actually mounted or not. This is very convenient and highly recommended, because it will show you the available auto-mountable file systems as existing directories, even when their file systems aren't currently mounted. Without the --ghost option, you'll have to remember the names of the directories. As soon as you try to access one of them, the directory will be created and the file system will be mounted. When the file system gets unmounted again, the directory is destroyed too, unless the --ghost option was given.



Other than that, you could always remove the entries from fstab and create a little shell script that you could run after logging in.


-Dave

---

### Post by alsehendo34 on 2007-09-29
My example:
 
smbmount //192.168.0.100/share_name /mnt/directory -o username=root,password=xxxxxxxx,uid=yyy,rw

yyy being the user name you are operating under @ the tme giving you ownership of the mounted directory and thus read write.
root smb user added to the samba server
password not the root password but smb password for root smb user.

Adding SMB user
[root@server2 samba]# smbpasswd &#8211;a root
	New SMB password: xxxxxxxx
	Retype new SMB password:xxxxxxxx

---

### Post by piagent on 2007-10-01
> **dbott67 said:**
> I don't know anything about this, but I did find a similar app called 'autofs' that has a couple of similar options that may be useful:
--timeout 
--ghost
.........
Other than that, you could always remove the entries from fstab and create a little shell script that you could run after logging in.
-Dave

Thank you for this information. Maybe this will help me.  I’ve posted this kind of problem in other forums with no answers:

[http://ubuntuforums.org/showthread.php?p=3453758#post3453758](http://ubuntuforums.org/showthread.php?p=3453758#post3453758)

[http://ubuntuforums.org/showthread.php?p=3450943#post3450943](http://ubuntuforums.org/showthread.php?p=3450943#post3450943)

I've been working on a script to solve the same problem.  My share works well when the sharing machine is up but if it comes up late or goes down I lose the share and it never comes back.  I can non-root smbumount and smbmount again or restart my session to get it back.  I'm looking for an active sustainable connection.

What is frustrating is Gnome network sees it go away and come back but I'm not able to use the Gnome Network path (smb:) via a sym-link or another way for may application.

Although I don’t understand how it works yet, I have done a mount manually then saved my gnome session and I always get the mount back on a new session with out the need to smbmount. (note: to make this work you need a chmod u+s smbmnt  ) I’ve wanted to look into this.

The scripts I’m working on are patterned after the idea of “map network drive”.  It doesn’t do much but capture in background all the currently non fstab mounts in two lists: those that are in the Gnome session save (the reconnect at logon) and those just manually done (do not reconnect at logon).  The main work of the script is to maintain the list and try to remount anything that has gone away.  It assume those in fstab are the systems problem.

Sounds like autofs might just do this for me without all my voodoo….. Although it is a learning experience.

---

### Post by usser on 2007-10-21
> I've been working on a script to solve the same problem. My share works well when the sharing machine is up but if it comes up late or goes down I lose the share and it never comes back. I can non-root smbumount and smbmount again or restart my session to get it back. I'm looking for an active sustainable connection.

Same here smbmount hangs when server from which i mount is restarted.
i found that mount command reconnects if the share becomes available again
ie. instead of smbmount i use 
```
mount -t cifs -o username=whatever,password="somepass",uid=1000,gid=1000 //servername/sharename /local/mountpoint
```

Oh and one more thing. I could never figure out how to mount smb on startup in such a way that if the server is not online, it'd keep trying to mount until suceeded.
So i wrote this sloppy script that i run through init.d
```

#!/bin/bash

mount -t cifs -o username=name,password="",uid=1000,gid=1000 //server/share /mnt
while [ "$?" != 0 ] ; do
  sleep 20
  mount -t cifs -o username=name,password="",uid=1000,gid=1000 //server/share /mnt
done


```
 anyone care to comment suggest how it can be done otherwise

---

### Post by multi on 2007-10-22
I worked my way through the howto and it works like a charm, though I get some error messages in /var/log/messages. Should I be worried about these?

```
Oct 22 15:46:06 P01 kernel: [ 3550.432581] smbfs: Unrecognized mount option noexec
Oct 22 15:46:06 P01 kernel: [ 3550.487383] smbfs: Unrecognized mount option noexec
```

I'm trying to mount 2 folders on an EXT3 partition on a Feisty machine from Gutsy.

These are the lines I added to fstab:
```
//192.168.0.4/Downloads /media/GAL-Downloads   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.0.4/torrents /media/GAL-torrents   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
```

---

### Post by dmizer on 2007-10-22
> **multi said:**
> These are the lines I added to fstab:
```
//192.168.0.4/Downloads /media/GAL-Downloads   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.0.4/torrents /media/GAL-torrents   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
```

to get rid of the smbfs error, use cifs instead.  try these lines:
```
//192.168.0.4/Downloads /media/GAL-Downloads   cifs auto,rw,credentials=/root/.credentials,file_mode=0777,dir_mode=0777,user   0 0
//192.168.0.4/torrents /media/GAL-torrents   cifs  auto,rw,credentials=/root/.credentials,file_mode=0777,dir_mode=0777,user   0 0
```

---

### Post by jamiltonio on 2007-10-23
I also seem to be getting the problem:

hamilton@hamilton-laptop:~$ smbclient -L 192.168.2.3 -U%
Domain=[MSHOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine 192.168.2.3.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.2.3 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[MSHOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------
        SLURK                SLURK

        Workgroup            Master
        ---------            -------
        MSHOME               SLURK


Do you have any idea why this is happening; what am I doing wrong?

---

### Post by dmizer on 2007-10-23
> **jamiltonio said:**
> I also seem to be getting the problem: [...]

fix here: [http://ubuntuforums.org/showthread.php?p=3605477](http://ubuntuforums.org/showthread.php?p=3605477)

---

### Post by petersfreeman on 2007-10-23
I have a second 80GB hard disk that is empty and I want to mount it and share it so I can store multimedia files.  I am running Samba and I have configured the smb.conf file to share the CDROM drive successfully, however I need to mount the second hard disk and I need to know its name so I can path to it.  Hod do I go about this?  Is it called disk1?

Thank you,

Peter

---

### Post by multi on 2007-10-23
> **dmizer said:**
> to get rid of the smbfs error, use cifs instead.  try these lines:
```
//192.168.0.4/Downloads /media/GAL-Downloads   cifs auto,rw,credentials=/root/.credentials,file_mode=0777,dir_mode=0777,user   0 0
//192.168.0.4/torrents /media/GAL-torrents   cifs  auto,rw,credentials=/root/.credentials,file_mode=0777,dir_mode=0777,user   0 0
```

Thanks, that did the trick for me! :)

---

### Post by petersfreeman on 2007-10-23
I figured out how to mount my second hard drive and I edited the fstab file with the mount points etc and it is mounting correctly.  Now, how do I work with it?  In windows, you change from C drive to D drive drives by just typing d:.  How do I change from the default partition to the main partition on the new drive?  (from hda3 to hdb1)?

Thanks,

Peter

---

### Post by jamiltonio on 2007-10-23
> **dmizer said:**
> fix here: [http://ubuntuforums.org/showthread.php?p=3605477](http://ubuntuforums.org/showthread.php?p=3605477)

the file system for the drive I want to mount is FAT32, not NTFS -- i don't have the entry described in the link you sent me.  maybe i need to put it in?

---

### Post by mr tim esquire on 2007-10-23
can anyone help here?
other machine is running XP this one Fiesty
```
mouse@mouse-machine:~$ smbclient -L 192.168.1.10 -U%
Domain=[MOUSENET] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine 192.168.1.10.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.1.10 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[MOUSENET] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------
        COMPUTIM             computim
        MOUSE_MACHINE        

        Workgroup            Master
        ---------            -------
        MOUSENET             COMPUTIM

```
thanks

---

### Post by decatett on 2007-10-24
i resolv the problem with:

"ERRHRD - ERRgeneral (General failure.) SMB connection failed"
" server: Permission denied"


in my computer .. /etc/fstab .. i add: 

"

//192.168.1.65/ubuntu12523145324532465 /media/ubuntu12523145324532465 smbfs username=ubuntu12523145324532465,password=ubuntu12523145324532465,workgrup=ubuntu12523145324532465,umask 022 0 0

'

and to server in smb.conf i add:

"
[global]
    ; General server settings
    netbios name = ubuntu12523145324532465
    server string =
    workgroup = ubuntu12523145324532465
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[ubuntu12523145324532465]
    path = /media/ubuntu12523145324532465/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755

"



and work great :guitar: naw

---

### Post by redz1234 on 2007-10-24
Thanks for the great walk through. As a Kubuntu newbie this walk through made everything so much easier.

---

### Post by ryanchew on 2007-10-25
Hey guys,

I created some nautilus scripts to mount SMB shares and ISO/UDF files with a simple GUI interface using Zenity.
**Requirements:** zenity, smbfs (zenity should be included in a default Ubuntu installation)
**Installation:** Just pop them in your ~/.gnome2/nautilus-scripts folder and you should be able to use them. If you don't have smbfs, just run this command.
```
sudo apt-get install smbfs
```
```

**Instructions:**
*Mounting*
[LIST]
[*]Right click on SMB folder or ISO/UDF file
[*]Scripts -> mount.sh
[*]Select mount point
[*]Mount as read-only?
[*]Type in SMB user name (SMB only)
[*]Type in SMB password (SMB only)
[*] You're done :)
[/LIST]

*Unmounting*
[LIST]
[*]Right click anywhere
[*]Scripts -> unmount.sh (script scans for mounted smb and iso/udf files)
[*]Select volumes to unmount
[*] You're done :)
[/LIST]
```

Download:
[http://ubuntustuff.chewablestudios.com/mount.sh](http://ubuntustuff.chewablestudios.com/mount.sh)
[http://ubuntustuff.chewablestudios.com/unmount.sh](http://ubuntustuff.chewablestudios.com/unmount.sh)

These scripts were tested in Gutsy so please do let me know if you encounter any problems or improvements/optimisations for the scripts. Feedback is very welcome :)

---

### Post by CoolDreamZ on 2007-10-26
To mount the share anonymously (without the need for a password) this worked for me in my peer-peer network (with share on Windows XP). Entry from /etc/fstab:

```
//server/share /mountpoint smbfs username=guest 0 0
```

---

### Post by JoaoCarlosCorreia on 2007-10-26
I guess this will sound wierd but I can't really solve this.

I want to make a smbmount with a Windows directory say //Netsharer/Shared

I use the line: sudo smbmount //Netsharer/Shared /home/user/shared -o username=user,password=mysecretpassword,uid=1000,mask=000

It works fine.

If I use a bigger directory tree in the windows side it doesn't work!!!! Something Like

sudo smbmount //Netsharer/Shared/music /home/user/shared -o username=user,password=userpassword,uid=1000,mask=000

allways return:
5440:  tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

The problem is that this share exists in my Netsharer!!

Can someone help me here?

TIA,

João

---

### Post by CoolDreamZ on 2007-10-26
My guess is that the problem is because you trying to mount a folder within a share i.e. //server/share/folder. Try going to the Windows server (Netsharer) and sharing the folder "music". Then you should be able to use //Netsharer/music instead.

As you have successfully mounted the share //Netsharer/Shared another solution would be to create a symbolic link to /home/user/shared/music (use the** ln** command)

---

### Post by dbott67 on 2007-10-26
*EDIT: Yes, just like CoolDreamZ said.*

@JoaoCarlosCorreia:

I believe you can only mount a "share" (i.e. \\servername\sharename) and not to a *sub-directory* of a share (i.e. \\servername\sharename\*[COLOR=Black]subdirectory[/COLOR]*).

If you need to mount a sub-folder, try creating a unique share for the sub-folder and see if that works.

-Dave

---

### Post by yoppa on 2007-10-26
Thank you so much for your time, really THE guide ive been looking for  :)
But I've got a problem, it freezes when I browse or try to read a file. If I wait for some time I can try and force quit the browser, but the system hangs... any ideas!?

(Ive added the share in fstab, and I browse to it by /home/na/data which is the mountpoint.)

---

### Post by John Harrington on 2007-10-27
I'm having a problem with my smb mount which seems to have started when I upgraded to gutsy.  The windows share continues to mount and I can browse and open files in the mounted directory, but with most applications trying to save a file just doesn't do anything, or I get a permission denied error (nautilus, GIMP, Open Office).  Oddly, Thunderbird continues to work just as it used to do with shared mailboxes located on the Windows computer in the same mount path.  I can still download, delete, move emails. I don't know much about troubleshooting this and would appreciate any ideas.  Also, my ability to print to a printer attached to the Windows computer seems to have broken at the same time.

---

### Post by John Harrington on 2007-10-27
I solved my problem.  Problem was with permissions on the Ubuntu computer.  I had been mounting on /mnt which is owned by root, even when a file system is mounted using "-u <user>" flag.  I am not permitted to change owner even when operating as root.  Users have "file access" permission.  This can't be changed to read/write permission.  For some reason this apparently prevented any program other than Thunderbird from writing to the mounted files unless it were running as root.  I don't understand this at all or why it changed with Gutsy.  However, by mounting to a mountpoint in my home directory owned by me I can now run programs as an ordinary user and write to files in the mounted directory.  

My printer problem may be completely unrelated. It seems to be broken.

---

### Post by bayvista on 2007-11-03
I am trying to mount a Windows share on Ubuntu. I have followed everything in this thread, but still get this message;

david@david-laptop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on //davidspc/My Pictures,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is my fstab:

# mod 071022 - dml- add hda3
#
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=7c6572fb-6760-4301-8ea2-478c4c94db5b / ext3 defaults,errors=remount-ro 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=7c9856d2-f6f9-4567-bbfd-e44825f03e10 /storage ext3 defaults 0 0
# /dev/hda5 -- converted during upgrade to edgy
UUID=717b1e87-9c77-4a76-99e0-e6a4a4058666 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0 

I can see and access the share through the file browser, but not through Picasa or any other application.

Any suggestions most welcome.
//davidspc/My\040Pictures /davidspc cifs credentials=/home/david/.smbcredentials,uid=1000 0 0

---

### Post by CoolDreamZ on 2007-11-04
> **bayvista said:**
> 
//davidspc/My\040Pictures /davidspc cifs credentials=/home/david/.smbcredentials,uid=1000 0 0

I could not get this to work using filesystem type cifs, try smbfs instead like this:


//davidspc/My\040Pictures /davidspc **smbfs** credentials=/home/david/.smbcredentials,uid=1000 0

---

### Post by bayvista on 2007-11-04
It gives exactly the same error with smbfs. Have i a syntax error?

---

### Post by CoolDreamZ on 2007-11-04
What happens if you try to mount the share like this:

sudo smbmount //davidspc/My\040Pictures /davidspc -o username=user,password=mysecretpassword,uid=1000,mask=000

---

### Post by bayvista on 2007-11-04
sudo: smbmount: command not found

---

### Post by CoolDreamZ on 2007-11-05
Did you install **smbfs** and **smbclient**?

---

### Post by bayvista on 2007-11-05
I solved the problem. It was the "credentials" file. When I replaced this with "username" and "password", my share was mounted. I  don't like having details like username and password floating around in fstab, so I'll pursue this one further and try to get the credentials file working. My feeling is that it MUST be in the root directory.

Thanks for your interest.

---

### Post by marf88 on 2007-11-11
ok here goes. I followed everything in this tutorial and links. I threw the stuff in my fstab, made the .credentials, and it all works, except I have read only access.

Here is my line in fstab

```
//192.168.0.XXX/MyShare /home/mike/Share cifs auto,uid=mike,gid=mike,credentials=/root/.credentials,file_mode=0777,dir_mode=0777,user 0 0
```

The mount works, and I can read and Write everything in it. However I cannot delete or Edit. So I do some more digging, I open up Terminal, and browse to the path /home/mike/Share/ 
I then type 'sudo rm filename.txt ' and it works. 
So the mount is fine, I can read/write/execute through terminal as root. However through the GUI nautilus as mike (my account) I only have read access. I see other people have this problem, but they all say that when they did uid=mike it would all of a sudden work, but mine has been like so for the whole time.

On a side note,

When I click in the top taskbar " Places > Connect to Server.. "
I fill in the information for Windows Share, and when It mounts the share with that, I have read/write/execute access that way through the GUI nautilus. I however cannot watch any videos through this, because VLC cannot open them, however it can through the manual mount. 

So as of now I'm using the /home/mike/Share to view my videos and such, however I'm using the ubuntu " Places > Connect to Server..." to actually delete and edit files. Very annoying.

Please, any insight. If you want me to paste ls -l I can.

Thanks, and hopefully somebody can tell me how to fix this.

EDIT** His problem is identical to mine. Too bad theres no solution posted [http://www.linuxquestions.org/questions/linux-hardware-18/mount-smb-share-with-readwrite-permissions-531991/](http://www.linuxquestions.org/questions/linux-hardware-18/mount-smb-share-with-readwrite-permissions-531991/)

---

### Post by manemannen on 2007-11-13
Thanks for the nice guide. Worked perfectly with my LaCie NAS.

---

### Post by alls0p69 on 2007-11-13
Exactly what I needed to add a Win network drive to ubuntu ftp server!
Kudos

---

### Post by manemannen on 2007-11-13
Ok I got it working but how do I get rid of the icons that popped up on my desktop (and on all other users desktop for that matter)?

---

### Post by dbott67 on 2007-11-13
> **manemannen said:**
> Ok I got it working but how do I get rid of the icons that popped up on my desktop (and on all other users desktop for that matter)?

Check post #10:

[http://ubuntuforums.org/showpost.php?p=1852633&postcount=10](http://ubuntuforums.org/showpost.php?p=1852633&postcount=10)

-Dave

---

### Post by manemannen on 2007-11-14
oh ok, sorry should have read the whole thread :oops:. Thanks for the help!

---

### Post by 8daysaweek.co.uk on 2007-11-14
OK, everything was going great, I followed the instructions and am able to mount and unmount the share using
> **dbott67 said:**
> 3. Mounting the share from the command line (to verify that it works):
```
sudo smbmount //192.168.1.2/Music /home/dbott/music -o username=dbott,password=mysecretpassword,uid=1000,mask=000
```

4. Un-mounting the share from the command line:
```
sudo smbumount /home/dbott/music
```

The following is where I'm having problems.
> **dbott67 said:**
> 5. Add the mount point to fstab (making it 'automatic'):

*[COLOR="Red"]The better way (storing your username & password in a file only readable by root):[/COLOR]*
```
//192.168.1.2/Music /home/dbott/music   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
```

**/root/.credentials** is a text file that contains your smb username and password.  To create the file, type:
```
sudo gedit /root/.credentials
```
and add the following text:
```
username=your_smb_username
password=your_smb_password

```

Now, make the file only readable by root:
```
sudo chmod 600 /root/.credentials
```
I've created the /root/.credentials file no problem, but whenever I enter the command to add the mount point to fstab, using either the device name (which works above) or the IP address I get: > bash: //192.168.0.113/folder: No such file or directory

So, I haven't tried the rest (from point 6 onward) yet.  Any idea why it is telling me "No such file or directory"?  I'm using Gutsy/Gnome.

TIA,

---

### Post by Skip Da Shu on 2007-11-15
OK, I've tried and tried but now don't feel like I'm learning anymore...  These fstab enties all seem to work about the  same:
```
#//C17-E64desktop/xfer /home/c17xfer smbfs credentials=/home/skip/.smbcredentials,1000 0 0
#//C17-E64desktop/xfer /home/c17xfer smbfs username=guest,password=,uid=1000,gid=1000 0 0
#//C17-E64desktop/xfer /home/c17xfer smbfs username=guest,password=,uid=1000,gid=1000,defaults,umask=777  0  0
//C17-E64desktop/xfer /home/c17xfer smbfs username=guest,defaults,umask=777  0  0
```

No errors in /var/log/samba/log.smbmount.  

When I get to the desktop /home/c17xfer is empty until I enter a terminal and do ```
sudo mount -a
``` then all is good.

I've decided that having the share mount from a desktop icon would really be the best anyway.  I thought that would be easy but I haven't even been able to do that :-(

Could someone advise me **how to create a desktop icon that'll do the mount**.  I tried to create one with "create launcher" but no go.  Xubuntu Gutsy 64b

Any and all help much appreciated and thanx for getting me this far with the tutorial.

Skip

Next: tackle command that starts a x11vnc server that works in terminal but not in rc.local

---

### Post by midtown on 2007-11-16
Thanks for this great little guide, worked perfectly! :popcorn:

---

### Post by UponFirstListen on 2007-11-16
I'm completely stuck and have been frustrated for several hours now on a Samba (?) problem. Let me explain my setup a bit.

Ubuntu Feisty as MythTV front and backend with media storage for all of my videos
Kubuntu Feisty on Desktop with media storage for all of my music
Kubuntu Feisty on Laptop, connecting to each of the above machines

This has worked perfectly and I use my laptop as my main machine, but the storage on the other 2. Until tonight. I usually use the laptop to my big screen TV via the s-video out to stream videos. But for some reason I couldn't see any of the files. Not a big deal as this seems to happen now and again. I reboot and walk away, but when I return the problem hasn't corrected itself. I tried several things, all to no avail. When I mount the share and 'ls' I get an input/output error. When I browse in Konqueror, a la smb://, everything works fine. I've tried searching to no avail and tried several different configurations in my /etc/fstab. The share mounts fine, but I can't access the files at all.

My smb.conf:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0d7eb975-2aa6-4120-b07d-dda8452effd8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=762009af-3c84-4d14-929f-a1e9f726e02b none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.1.2/UFL /home/jason/UFL cifs dir_mode=0777,defaults,auto,user,username=nobody,rw 0 0
# //192.168.0.3/Downloads /home/jason/Downloads/Desktop cifs dir_mode=0777,defaults,auto,user,username=nobody,rw 0 0
//192.168.1.2/Music /home/jason/Media/Audio cifs dir_mode=0777,defaults,auto,user,username=nobody,rw 0 0
//192.168.1.2/Documents /home/jason/Documents cifs noperm,file_mode=0777,dir_mode=0777,defaults,auto,user,username=nobody,rw 0 0
//192.168.1.6/Video /home/jason/Media/Video smbfs dmask=777,defaults,auto,user,guest,rw 0 0
//192.168.1.6/Pictures /home/jason/Media/Pictures smbfs dmask=777,defaults,auto,user,guest,rw 0 0
# //192.168.1.6/Video /home/jason/Media/Video cifs noperm,file_mode=0777,dir_mode=0777,defaults,auto,user,username=jason,rw 0 0


As you can see by the lines commented out, I've tried both CIFS and SMB. It was previously working with SMB. Nothing changed from the last time I used it. Yesterday, it was fine, this morning it was fine, tonight it's busted. Any advice?

---

### Post by dbott67 on 2007-11-18
[I][B]I've added these instructions to the original post:

[/B][/I]A few of the downsides on the Nexstar LX NAS device that I purchased is that:
1. It does not support CIFS
2. It does not support SATA drives (IDE only)
3. It is 10/100 Mbps (no gigabit)
4. It does not have any fault tolerance.  

It is, however, an inexpensive device that can be used to share data among many computers.

Anyhow, I have been in the process of upgrading my home network to gigabit and wanted to purchase a better NAS device that had some redundancy & expandability, as well as support for gigabit, CIFS and SATA drives (hot-swappable, no less). I ended up purchasing a [Netgear (formerly Infrant) ReadyNAS NV+ 4250]("http://www.netgear.com/Products/Storage/ReadyNASNVPlus/RND4250.aspx") and am providing an update to my original instructions using CIFS rather than smbfs:

Steps 1 and 2 remain the same.

In step 3, test mount the share using CIFS as noted:

```
dbott@gutsy:~$ sudo mount -t cifs //192.168.1.2/Music /home/dbott/Music -o iocharset=utf8,file_mode=0777,dir_mode=0777
```Step 4 remains the same.

Step 5, add the mount point(s) to your /etc/fstab file:
```
//192.168.1.2/Music /home/dbott/Music   cifs  credentials=/root/.credentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.2/dbott /home/dbott/Data   cifs  credentials=/root/.credentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.2/Archive /home/dbott/Archive   cifs  credentials=/root/.credentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```The only issue that I encountered was with regards to UIDs. My user account on Ubuntu (dbott) has a UID of 1000, while my user account on the NAS has a UID of 1004. To fix this, I changed my Ubuntu UID to match the UID on the Netgear NAS using the following command:
```
sudo usermod --uid 1004 dbott
```After a couple of minutes and a reboot, everything was working properly.

-Dave

---

### Post by candtalan on 2007-12-01
Thanks Dave (and other contributors) for a really, really useful thread!

---

### Post by j.daniel on 2007-12-08
**Thank you Dave!**

As a novice Linux-convertee I have tried and tried to get my NAS up and running properly and scoured tons of websites both for openSUSE and ubuntu before I stumbled on this thread. Since I have tried pretty much everything I would like to share my expereince with you in the hope that some other lost soul stumbles on this.

First a bit about my setup: I have two Linux computers (+a few Windows boxes) connected to an internal network (192.168.1.xxx range) where a LaCie EdMini NAS is attached. One Linux is openSUSE and the other one is running Ubuntu (I'm checking out different distros, and Ubuntu is winning hands down right now).

I have been running around in the Samba jungle and tweaked config files and generally bashing (pun intended) my head against the wall. After a while I managed to connect, but where only root could create files (other users could actually change them...ahem). I tested all kinds of different solutions (chmod +s /sbin/mount.cifs and others) until everything just fell into place with this one. All of a sudden I could connect and read/write without having to go via 'su root' (openSUSE) or 'sudo' (ubuntu). Victory!

Since I managed to screw up my ubuntu system beyond recognition and made a fresh install, I tried to do as little as possible to get the NAS up and running - just to see how much I actually needed to do.

Here is the way I got it up and running on my fresh ubuntu system:

First a few notes: samba as such is not needed to access the NAS - only the smbfs. The samba daemon is not required unless you want to share files from the linux computer AFAIK.

Some general other prerequisites which I have made on my system, probably not all of them are required or desired on your own system:

- The LaCie EdMini NAS is configured to run a "Windows file server" on a static IP (192.168.1.YYY) and I have set up an account with read/write access with the a user name, lets call it "ubuntu" and the password "somepass". Let's call my main account on the ubuntu-machine "daniel". The share is called... 'share' :)
- On the ubuntu machine - in [System]->[Administration[->[Network] - I have set my wired connection to use a static IP in the 192.168.1.XXX range and set up an alias for the EdMini in the "Hosts" tab so I can use the name "edmini" instad of "192.168.1.YYY".

Then to the actual connection, in large part a repeat of the original post, but I just wanted to walk through what I did:
- First I installed only the **smbfs** via '**sudo apt-get install smbfs**' (all I want is the mount.cifs command really)
- Then I added a new directory via '**sudo mkdir /NAS**' to be my mount-point
- Then one crucial point: I changed the ownership of the /NAS directory to daniel via '**sudo chown daniel:daniel /NAS**'. Without this, you can only write to the NAS as root. This was by the way the final thing that made all pieces go 'click' for me.
- After this I added a line to the /etc/fstab (via '**sudo gedit /etc/fstab**' - **vi** in ubuntu just makes me go ballistic, here is one thing where openSUSE 10.3 is better:) )
  **//edmini/share   /NAS   cifs   noauto,user,credentials=/root/.nas_credentials  0  0**
Note: you can probably set "auto" instead of "noauto" if you wish, but I do not always have the NAS running, so... Note2: 'iocharset=utf8' does not seem to be required, but I have after this added that requirement - can't do much harm... Also the file_mode and dir_mode statments do not seem to be required. Probably stepping in something smelly here, but it works so far...
- Then via a '**sudo gedit /root/.nas_credentials**' I created a file with the two lines:
  **username=ubuntu**
  **password=somepass**
 - a quick '**sudo chmod og-r /root/.nas_credentials** later to protect the info I am up and running.
 - As user daniel I can now run '**mount /NAS**' and read, write and do whatever I want. YES!

As an interesting side-issue, this does not work as well on my openSUSE-box. There I have to specifically set the user to be 'daniel' in the fstab file by adding this to the entry 'noauto,... etc ...,uid=daniel,gid=users'... (note: openSUSE puts all users in the 'users' group instead of as in ubuntu creating one group per user) there are probably tons of openSUSE gurus out there whou can point out what I have done wrong there, but this is not the forum for that.

Anyway: I just wanted to post my experience in case some other poor Linux novice might have use for it.

Cheers!
/ Daniel

---

### Post by bayvista on 2007-12-09
Thanks, Daniel

I tried your suggestions but without luck. Here is the output of my 'mount' command, and a listing of my FSTAB

david@david-desktop:~$ mount /laptop
mount: wrong fs type, bad option, bad superblock on //hp-laptop/Documents,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

david@david-desktop:~$ so
bash: so: command not found
david@david-desktop:~$ dmesg | tail
[   66.305952] [drm] Loading R300 Microcode
[   66.305995] [drm] writeback test succeeded in 1 usecs
[  541.469347] ppdev0: registered pardevice
[  541.519750] ppdev0: unregistered pardevice
[  541.626622] drivers/usb/class/usblp.c: usblp0: removed
[  558.050255] input: AT Translated Set 2 keyboard as /class/input/input5
[ 1739.573938] smbfs: mount_data version 1919251317 is not supported
[ 2598.966060] smbfs: mount_data version 1919251317 is not supported
[ 3922.306895]  CIFS VFS: No username specified
[ 3922.306903]  CIFS VFS: cifs_mount failed w/return code = -22
david@david-desktop:~$ 

FSTAB----


# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda5 :
UUID=def19f2f-ae04-4a91-927f-13d99ad66e61 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
UUID=24F4B62EF4B6025A /media/hda1 ntfs-3g defaults,locale=en_AU.UTF-8 0 0
# Entry for /dev/hda3 :
UUID=14203FD2203FB996 /media/hda3 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/hda6 :
UUID=CA246D23246D142B /media/hda6 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sda1 :
UUID=02505FF0505FE945 /media/sda1 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=13D61B93DEF50771 /media/sda5 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/hda7 :
UUID=f6b50d1f-8037-4c8c-b858-15a21f42bc46 none swap sw 0 0
# Entry for /dev/sda6 :
UUID=3e2dfddd-5548-7a88-2420-b67970126ad9 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
# entry for hp-laptop
//hp-laptop/Documents /laptop  cifs noauto,user,credentials=/root/.hp_credentials 0 0


Any help really appreciated..Dave

---

### Post by bayvista on 2007-12-10
OK Guys. Forget this crap.

I had recently switched my Notebook from Wired to Wireless and my Desktop was not part of the Wireless Network. When I find out how to do this, I'll try again.

I can access the Notebook from the Desktop using 'Wired' because they are both part of the same Workgroup. However, Wireless has tighter security and there must be some clever way of adding a Ubuntu PC to a wireless network. That is, one connected via a Router which supports both.

Dave

---

### Post by xfile087 on 2008-03-26
I just wanted to post something in case anyone else has the same problem.

Everytime I tried to mount my network drive I kept getting the error:

> mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)


I've searched google and everywhere I could think of but I still couldn't get it working with my network drive. As it turns out the fix is so simple you need to do is add the option "nounix" and it will mount perfectly.

**For example I use the following to mount a share**

>  mount -t cifs //192.168.1.110/videos /media/bluerea/videos/ -o nounix

**And to add it to fstab (I don't use credentials but you might so you will need to add them)**

> //192.168.1.110/videos /media/bluerea/videos   cifs nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0



I'm not very good at explaining things, though I hope this will be of use to some people.

---

### Post by bayvista on 2008-04-09
FSTAB - 

After wrestling with this for months without success, I found a solution that does work. There is a file called /etc/rc.local. Just add your working MOUNT command to the end of this and Bingo. Mine looks like this:

mount -t cifs //HP-Laptop/Users /media/HP-Laptop -o username=david,password=********,file_mode=0777,dir_mode=0777
exit 0

---

### Post by harmlessdrudge on 2008-04-12
I want to connect to my Infrant ReadyNAS (running 4.0 Radiator) from Ubuntu and to see it as a single volume. The 4.0 software supposedly added the possibility to see the NAS as a single volume. So far, however I haven't succeeded. I can access shares easily enough with

sudo smbmount //<ip>/share /mnt/readynas -o username=Admin,workgroup=groupname,password=adminpwd,uid=1000,mask=000

(I tried the reserved share names 'c' and 'C$')

trying to use 

sudo mount -t nfs

didn't work and I was told by Netgear that this wouldn't work 

(see [http://www.readynas.com/forum/viewtopic.php?f=23&t=17678](http://www.readynas.com/forum/viewtopic.php?f=23&t=17678))

So I am still in the dark. TIA for any assistance.

---

### Post by harmlessdrudge on 2008-04-12
.

---

### Post by harmlessdrudge on 2008-04-12
From [http://www.readynas.com/forum/viewtopic.php?f=17&t=15058](http://www.readynas.com/forum/viewtopic.php?f=17&t=15058)

> CHANGES SINCE 3.01 

3. Remote SSH for Support is disabled by default. If you wish to enable SSH access for Support, you&#8217;ll need to install the ToggleSSH add-on.
4. Root SSH support. With the EnableRootSSH add-on, you can now remote login to the ReadyNAS RAIDiator shell as a root user. Initial password for root will be the same as the current FrontView admin password. Please keep in mind that NETGEAR may deny support if you&#8217;ve enabled root access.
.
.
8. Root of volumes can now be accessed by the admin user for easier volume-wide backups.

Seems I need to EnableRootSSH then ToggleSSH ... 

The add-ons can be found here: [http://www.readynas.com/?page_id=95](http://www.readynas.com/?page_id=95)

but the installation instructions don't mean much yet

> To install the add-on, you will need to download the add-on image and install it in the System/Update/Local tab. You will need to reboot after each add-on installation.

To install a file in the system directory I need to login as root, so this seems a catch22...

Wait, just found this:

» How do I install/remove an add-on?
Simply download the add-on and upload it from FrontView System&#8594;Update&#8594;Local tab. You will need to reboot before the add-on is installed. 

OK...

So I installed EnableRootSSH then ToggleSSH

and I am told "SSH accesss disabled"

I misunderstood some posts on the netgear forum to mean first install the EnableRootSSH plugin then turn it on, in fact it seems that ToggleSSH = DisableSSH (correction: it's a toggle, it switches SSH off if on and vv)

Obvious when you but not to a new user with no documentation<sigh>

Would still like to see a step by step guide. If I figure it out I''ll post it.

---

### Post by harmlessdrudge on 2008-04-12
Progress:

with ssh enabled I've been able to connect to the ReadyNAS as follows

Places
Connect to Server

Service type: SSH
Server: 192.168.1.xxx
Folder: /c
User: root
Name to use: ReadyNAS

Finally, this will allow me to copy all shares easily.

Should I backup the entire system from the root folder?

I need to find a simple backup and restore/disaster recovery routine that doesn't involve buying another ReadyNAS.

---

### Post by harmlessdrudge on 2008-04-12
This 

[http://www.debianadmin.com/mount-a-remote-file-system-through-ssh-using-sshfs.html](http://www.debianadmin.com/mount-a-remote-file-system-through-ssh-using-sshfs.html)

and this

[https://lists.ubuntu.com/archives/ubuntu-users/2006-June/080743.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-June/080743.html)

finally helped me get the ReadyNAS mounted at /mnt/readynas

Surprised to see the /dev/fuse permission denied error still there after nearly two years, though perhaps it was because I didn't log out then in again; I used the fix posted in the Ubuntu archives (2nd link).

---

### Post by timboe on 2008-06-22
Thanks, nice how to, Amarok wasn't adding my music though the "connect to server" share, but worked perfectly after mounting it as a mount point.:guitar:

---

### Post by fiddledeedee on 2008-07-08
Please see this wiki page as a guide instead of searching through a huge thread:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

