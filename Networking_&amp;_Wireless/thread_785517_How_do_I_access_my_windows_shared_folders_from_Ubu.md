---
title: "How do I access my windows shared folders from Ubuntu 8.04?"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by ithinkthereforeiam on 2008-05-07
Hello.

I have installed Ubuntu 8.04 and downloaded and installed the SMB for file sharing. I can see the networks, but no pcs or folders on my windows network.

If I click System > Administration on the menu bar, there is no Share Folders as in 7.10. But if I click System > Administration > Services, and scroll down, Folder Sharing Services is listed and checked.

Can someone guide me step by step to achieve File Sharing to and from Ubuntu 8.04 on a windows network?

---

### Post by diaa on 2008-05-07
That's strange, it worked for me easily(but I had set it up manually back when I had Gutsy), are you sure samba service is running? try running *ps -A|grep smb* and if it says *smbd* then it's running.
You can share a folder from the GUI by installing the package *nautilus-share* from the repos and then when you right-click any folder you'll find an item in the menu called *Sharing Options*

---

### Post by ithinkthereforeiam on 2008-05-07
Hi Diaa,

Thank you very much for replying.  I did as you suggested and it came up with the following:

mum@harrielap:~$ sudo ps -A|grep smb
[sudo] password for mum: 
 5583 ?        00:00:00 smbd
 5625 ?        00:00:00 smbd
 7052 ?        00:00:00 gvfsd-smb-brows
 7054 ?        00:00:00 smbd
 7064 ?        00:00:00 smbd
mum@harrielap:~$ 


No idea what it means, but there it is.:(

I went to packages to install nautilus-share, and it was already installed, so I re-installed.

So nothings changed really.

---

### Post by prshah on 2008-05-07
> **ithinkthereforeiam said:**
> 
Can someone guide me step by step to achieve File Sharing to and from Ubuntu 8.04 on a windows network?

Step 1: Logout and log back in after installing Samba.

2: Alt+F2, ```
shares-admin
```, click "unlock", type your password, click "Authenticate"

3: Add your share(s) (folder, sharename), click OK/Close.

4: Check if you can access the share from Windows with [color=red]\\yourubuntupc-0\share1[/color] etc. Replace line in red with your actual pc and share name. Your pc name can be found with the command ```
hostname
```

To share your Windows folders, setup a share in the Windows PC, then use the "Connect to server..." command in the places menu. If your windows PC cannot be access by name, use the ipaddress; you can find the ipaddress with the command ```
ipconfig
``` on the _windows_ pc.

---

### Post by ithinkthereforeiam on 2008-05-08
WOW.. that was amazing!!!!  Thank you so much PR!  It worked a treat.  Thank you so much:popcorn:

---

### Post by Jay911 on 2008-05-08
> **prshah said:**
> To share your Windows folders, setup a share in the Windows PC, then use the "Connect to server..." command in the places menu. If your windows PC cannot be access by name, use the ipaddress; you can find the ipaddress with the command ```
ipconfig
``` on the _windows_ pc.

Sorry if this is considered a thread hijack, but can you shed some light on why one might not be able to access Windows shares by name, but only by IP? That's my situation right now; I have various XP and Vista machines (and one Linksys network storage device) that Ubuntu 8.04 will not find using smb://geofront (for example - one of the XP system's names) in Nautilus, but will happily access using its IP address. All the Windows machines can contact one another just fine using either share (computer) names or IP addresses.. it's just the Ubuntu machine that can't connect.

---

### Post by enstardavid on 2008-05-08
Hi,

THANKS - I have been searching for this answer for DAYS

---

### Post by jcmvp on 2008-05-08
Accidentally replied to the wrong post... this can be deleted.

---

### Post by mkjana on 2008-05-09
Earlier I was using Ubuntu 6.06 LTS and I could use folders on Windows machines. After loading Ubuntu 8.04 I am not able to access folders on Windows machines :(. SMB is running, I could see the PC in network, see the shared folder but not able to open. What is the problem? Anyone could help me in solving this. 

N.B: I don't want to share folder on Ubuntu to Windows but would like to access windows 98 folder on 8.04.

jana

---

### Post by simplysimple on 2008-05-09
I'm having the same issue....i can see the windows network but when I access it I see no folder or files? 

Any help would be appreciated!!

Thank you.

---

### Post by prshah on 2008-05-09
> **mkjana said:**
> After loading Ubuntu 8.04 I am not able to access folders on Windows machines
jana

Try these commands and see it if helps:```

sudo mkdir /media/network
sudo mount -t cifs //windowspc/sharename /media/network

```

If there are no errors, your windows share contents should be available at /media/network. Note that if the second "sudo" command asks you for a password, it is _not_ your sudo password but your sharename password. If you dont have a password for the share, just press enter. Replace "windowspc" with either your windows pc name or ipaddress, and "sharename"
 with the name of the share on your windows pc.

> **simplysimple said:**
> I'm having the same issue....i can see the windows network but when I access it I see no folder or files? 

Have you shared any folder on your Windows machine? To know, in windows, open a command prompt, and type the command```
net share
```

Any help would be appreciated!!

Thank you.

---

### Post by mkjana on 2008-05-10
Thank you, but it is not working with that. I understand there is a bug with Nautilus. I have come across lot of posting on this. Hope we get a fix soon.

jana

---

### Post by lausianne on 2008-05-16
I spent a long time trying to get this to work. Eventually I got to at least see my shared folders in Firefox (found a hint somewhere), but couldn't access them.

Eventually I got access with Nautilus like this:
File>Connect to Server ...
... then entering the server name and the share name. I think I tried that several times before, and it never worked. Now it works,  no idea why.

Things I tried included installing Samba (which I can't configure, because it crashes, and anyway, the docs say smbf would be enough) and adding the following line to ~/.ssh/config:   GSSAPIAuthentication no
I had to create config. Don't know what that means or if it helped.

This is 8.04. Getting more and more frustrated about all this.

---

### Post by Jovec on 2008-06-14
> **Jay911 said:**
> Sorry if this is considered a thread hijack, but can you shed some light on why one might not be able to access Windows shares by name, but only by IP? That's my situation right now; I have various XP and Vista machines (and one Linksys network storage device) that Ubuntu 8.04 will not find using smb://geofront (for example - one of the XP system's names) in Nautilus, but will happily access using its IP address. All the Windows machines can contact one another just fine using either share (computer) names or IP addresses.. it's just the Ubuntu machine that can't connect.

A workaround would be to add IP addresses to the hosts file on each machine.

In vista, this file is C:\Windows\System32\Drivers\Etc\lmhosts.txt and you will need to first run notepad as Adminstrator then browse to the file in order to save your changes.

In Linux the file is /etc/hosts

---

### Post by jriggz on 2008-07-22
> **lausianne said:**
> This is 8.04. Getting more and more frustrated about all this.

Exactly. All I wanted to do was listen to music over the network while I worked. 45 minutes later and still no viable (working) solution and guess what would've taken a lot less time?

Booting into XP, playing my music through the working samba network, and leaving it in XP.

These "little" things are showstoppers only because I wonder why I'm wasting the space on a partition for Hardy.

I apologize for ranting on this thread. I'll take it elsewhere.

---

### Post by Sevis on 2008-09-15
> **prshah said:**
> Try these commands and see it if helps:```

sudo mkdir /media/network
sudo mount -t cifs //windowspc/sharename /media/network

```

If there are no errors, your windows share contents should be available at /media/network. Note that if the second "sudo" command asks you for a password, it is _not_ your sudo password but your sharename password. If you dont have a password for the share, just press enter. Replace "windowspc" with either your windows pc name or ipaddress, and "sharename"
 with the name of the share on your windows pc.

I'm sorry for bursting into the thread like this, but I have the same problem. Currently trying:

```
sudo mount -t cifs //192.168.1.100 /media/Merry1
```

and

```
sudo mount -t cifs //Merry1 /media/Merry1
```

In return, I get:

```
Mounting the DFS root for a particular server not implemented yet
No ip address specified and hostname not found.
```

Any idea what I'm doing wrong? I'm in KDE, by the way, but have originally installed Ubuntu (with gnome).

---

### Post by gregphil on 2008-09-15
New bug in ubuntu 8.04.1 (they switched to using broken gnome library gvfs).  See:  (ignore ADS in titles)
[Bug #207072 in gvfs (Ubuntu): &#8220;nautilus does not display samba shares for machines inside an ADS network.&#8221;]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072") 
[Bug 524485 - nautilus does not display samba shares for machines inside an ADS network. (gvfs)]("http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26")

---

### Post by prshah on 2008-09-16
> **Sevis said:**
> 
```
sudo mount -t cifs //192.168.1.100 /media/Merry1
```
```
sudo mount -t cifs //Merry1 /media/Merry1
```


You cannot mount the "DFS Root" (meaning machine Merry1 in this case). You have to mount a SHARE on Merry1; eg. if Merry1 has a shared folder "test", you will mount it as 

```
sudo mount -t cifs //192.168.1.100/test /media/Merry1
```

---

### Post by tjoel99 on 2008-12-18
Hello.  I also upgraded to Ubuntu 8.04 from 7.04.  

In 7.04, I went to Places, Network, Windows Network, Workgroup,and I could see my networked Windows computers.  Now in 8.04, I see nothing.

What must I do?  It's a little discouraging to not be able to do this simple but important function.  I want to like Ubuntu and continue using it, and seeing my Windows network is essential.  Please help.  Thank you!

---

### Post by baryah on 2009-03-05
I think use the 'Connect to Server' method and add bookmark. That is the easiest way it appears in 8.04.

---

