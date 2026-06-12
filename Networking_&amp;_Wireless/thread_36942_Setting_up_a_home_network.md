---
title: "Setting up a home network"
date: 2005-05-25
forum: Networking &amp; Wireless
---

### Post by mwdowns on 2005-05-25
Hello all. :)

I'm really interested in networking my two computers.  The problem is i really have little to no idea how to go about doing this.  I guess first I should tell you the setup for the network, and then I will tell you what I want to do with it.  Hopefully y'all can help out me set it up (or tell me that it's not really possible;))  This computer also is connected to a HP Deskjet 610C printer.

Computer 1: This is my main computer.  The specs: Asus A7V8X-MX mobo, Athlon XP 2500+, 512 MB RAM, 80 gig HD, Radeon 9200 SE, onboard sound, VIA Rhine II Fast Ethernet Adapter.  The HD is split into three partitions: 10 gigs with Win XP Home, 20 with SuSE 9.1 Pro, 50 gigs storage (formatted FAT32).  I dualboot Windows and SuSE (thinking about adding Ubuntu;))

Computer 2: Dell Dimension 4100, Pentium III 886 Mhz, 512 MB RAM, Radeon 850 LE, SoundBlaster Live!, HD 1 is 20 gigs with Windows XP Home, HD 2 is 40 gigs with Ubuntu 5.04, Realtek Ethernet adapter.  I dualboot Windows XP and Ubuntu (but, basically, this computer will use Ubuntu only).

Router: Gigafast 4-Port Ethernet Router EE400-R

I want to do a couple things.  One, i just want to set up a normal network between the two computers (i.e. sharing files and such).  Two, I would like for Computer 2 to have access to the storage drive on Computer 1 (that's where I keep my music).  Three (and this is a minor point), I'd like to let Computer 2 use Computer 1's printer.

As per my habits with the various OSes I have running...I am using Windows less and less these days.  I am mostly in SuSE and Ubuntu.  I still use Windows to play a couple games and various other things.  But, mostly I use Linux.


So, I guess, I want to know if what I want to do is possible?  And if it is, could you help me set it up?

Thanks a bunch.

---

### Post by mwdowns on 2005-05-25
One thing, I should mention...

I kinda know how to do this in Windows (i.e. I know where to go and what to click on an stuff), but I am lost on Linux (i.e no idea where to go and what to click on.)

---

### Post by KiwiP on 2005-05-25
The first thing is to decide exactly you mean by network.
It's seems both computers are active workstations, as opposed to one being a server. Therefore you want to setup a "workgroup" (in windows talk).

I assume you will be using the router to contect the PC's.

The simple approach is share the folders you want to share. This is done in properties.
Then use Samba to locate the other PC, and the shared folders. Oncethis is done, all you should need to do is to enter the requried login and password to gain access to that folder.

To use the printer, ensure both PC's and the printer are turned on, and it should then be possible to set the printer up on the second PC by using the normal print manager. I don't think there is any need to share the printer etc.


Hope this helps and have fun.

KiwiP

---

### Post by YaAqoB on 2005-05-26
Hello.
I was wondering if you could help me.
I have one PC running Linux and the other Windows XP Pro.
I have installed Samba on Ubuntu and setup the /mnt/Stuff drive to share and set the workgroup.
Now on the windows machine when I click "view Workgroup Pc's"  I can see the Ubuntu machine. When I click on it it asks for a password and login.
How to I setup that login and password?

---

### Post by phen on 2005-05-26
Hello!

about the samba configuration: I am not a security/networking guru, but i managed to set up a fileserver ages ago. I allowed guests to do all they want. Thats ok, because i restricted access to the nic used by my homenet and the guests are mainly me and some friends.

i hope i don't miss important stuff:

smb.conf:

-------------------------
# Guest account
  guest account = Gast

#Security mode
 security = share


####shared folders####

#user dir, password needed!
[%m]
  comment = User Dir
  path = /home/%m
  public = no
  writable = yes


#free for all
[mp3]
   path = /store/mp3
   public = yes
   only guest = yes
   writable = yes
   printable = no
   create mask = 0775

--------------------------

[root@server samba]# cat smbusers
# Unix_name = SMB_name1 SMB_name2 ...
root = administrator admin
nobody = guest pcguest smbguest

smbpasswords is filled with passwords for all users having a home dir.

dont remember what the "security=" thing is for.

the guest account "Gast" is the german windows standart for guest. Don't know if that is of importance. the shared folder options are important, though. 

Just take this as a starting point and do a little trial and error.

cheers,
kai

---

### Post by mwdowns on 2005-05-26
Thanks for the replies.

One thing I am a little confused about is how to use Samba?  I don't see an icon for it in any of the menus.  Or, is this a command line thing I should be doing?

On my SuSE machine, I've set up the /windows/D drive as shared.  But, I don't know how to even look for that using my Ubuntu machine.  And I'm not so knowledgable with how to work SuSE's networking either (did I mention I was a newb?!).

---

### Post by YaAqoB on 2005-05-26
I know this is very unlinux of me, but is there a point and click menu where I can create Samba users and passwords?

---

### Post by YaAqoB on 2005-05-27
Why is this so freakin difficult. I can see my Ubuntu Shares from the Windows PC but it keeps aking for a flippin login and password. I can't figure out how to create one and no one seems to be able to tell me.
There don't seem to be any thing on the Net that simply tells me where and how to create a samba user and password. Stuff it I don't want them to have logins and passwords I know who they are and don't care if the browse my shares.
Can anyone please tell me how to create a Samba login and password.

---

### Post by DracosX on 2005-05-27
Try this:
```

sudo smbpasswd -a username

```

---

### Post by YaAqoB on 2005-05-27
ok that ceated a user and password and I got a step further. When I try to acces the shared stuff on the ubuntu machine it says that I don't have permission to access the shared directory.
Do I have to start the samba server every time?
Or is it started on boot up?

---

### Post by DracosX on 2005-05-27
Ensure the user has read/write permissions for the folder:
Since your user is probably in the "users" group, this should do just that.
```

sudo chgrp users -R /path/to/share
sudo chmod 0775 /path/to/share

```
Samba should (IIRC) start at boot by default on ubuntu.

Here's all the samba docs you should ever need:
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by mwdowns on 2005-06-01
OK, well, I'm looking back over this thread after taking some time away from the computers.  And, frankly, I still have no idea what to do.  I have got my SuSE machine working fine (the folders are shared and the Network Browsing is set up).  But, as far as Ubuntu goes, I have no clue as to where to start.  Is there a menu item I click on to start Samba?  I think I know how to set up a shared folder (but really, I don't care so much about setting up a shared folder for Ubuntu).  What I want to do is have access to that shared folder on SuSE.  How do I do that?

---

### Post by theking2 on 2006-05-01
```

```[QUOTE=DracosX]Try this:
```

sudo smbpasswd -a username

```[/QUOTE]
This is a great help. Although I'm a bit lost with the number of user accounts and passwords. (This is just so much simpler on Windows :) ) 
So correct me if I'm wrong: the ubuntu username space is something else as the samba username space? In other words I have a user "blurb" on my ubuntu system but in order to connect from an XP box I still have to add (another?) smba user with: ```
sudo smbpasswd -a blurb 
```

---

