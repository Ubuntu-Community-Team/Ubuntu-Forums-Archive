---
title: "LXDE network file/folder sharing with XP machine..."
date: 2011-01-02
forum: New to Ubuntu
---

### Post by ~Maxx on 2011-01-02
Hello all.  I just installed Lubuntu a few days ago, and am coming along with general setup and tweaking in my spare time.  This weekend I decided to tackle getting my home network established with my Windows machine.  Here's where I'm at...

I've installed all Samba packages, Gigolo, and gvfs-fuse.  In Samba I've added my Home folder, made it writable and visible, and set the access options (more on that in a minute).  As far as I can tell my shared folders are set up properly in XP (had another XP machine networked to it previously).  I can now access my shared Lubuntu folder(s) from my XP machine.  The only quirk I'm seeing is that when I have the access option in Samba set to "only allow access to specific users", with my user name and/or "nobody" ticked below then XP requires a user name and password to access the folder.  The problem is that it doesn't seem to accept what I give it.  It just reloads the pop-up with my password hilighted, as if it wants different information.  I know my password is correct, as I've had to use it constantly while tweaking Lubuntu.  And I'm %99.99999 certain of my user name.  Anyway - I can change the Samba settings to "Allow access to everyone", and it lets me in without a fuss.  But I'm really wondering why it won't take my info.  Any ideas?

As far as accessing my Windows files from Lubuntu, I've hit a bit of a wall.  Apparently pcmanfm doesn't have an implementation for an equivalent to Windows "Network Places", and I couldn't get Samba to show my XP machine at all.  So based on [this thread]("http://ubuntuforums.org/showthread.php?t=1559541&highlight=lubuntu+network+file+sharing+windows+xp") (<--link) (post #6) I installed Gigolo and gvfs-fuse.  I think the Gigolo package is over my head though, as I can't seem to figure out how to use it.  It shows my XP computer, but says that "no shares are found".  Unfortunately I have no idea what to do with it from here.  The help file is obviously not geared toward newbs, and I can't seem to find any kind of tutorial online.  Do I need both Samba and Gigolo?  

Any advice here would be much appreciated.  Thanks!

---

### Post by bioterror on 2011-01-02
sudo apt-get install gvfs-backends

---

### Post by ~Maxx on 2011-01-02
Thanks bioterror.  But gvfs-backends is already installed.  Are the gvfs packages all part of Gigolo?  I have gvfs, gvfs-backends, gvfs-bin, and gvfs-fuse.  My assumption is that I need to do something with the connection settings in Gigolo.  After I choose "connect" I don't ahve a clue what to enter in the options panel that comes up.  I've tried several configurations, but they all seem to fail.

---

### Post by ~Maxx on 2011-01-02
Ugg...  I don't mean to bump, but this is driving me nuts.  I think I'm inches away from having this working, but can't take the last step.

In Gigolo I highlight my Windows machine in the sidebar and click the connect button above.  This gives me the "connect to server" options dialog.  For the "server type" I choose "Windows Share" (don't see how I could be wrong about that one), and for the "server" option I wasn't sure if that was the name of the pc I'm trying to access, or the name of the networks work group.  Tried both - no dice.  Under the "share" option I assumed that this wanted the name of the folder I'm trying to access (assuming permissions are set up correctly in Windows - which they should be).  But do they want the full path?  Or just the name of the folder (or in my case the name of the drive)?

If anyone has any insight into this I'd sure appreciate the help.  Thanks in advance.

---

### Post by cavalier911 on 2011-01-02
> I can now access my shared Lubuntu folder(s) from my XP machine. The only quirk I'm seeing is that when I have the access option in Samba set to "only allow access to specific users", with my user name and/or "nobody" ticked below then XP requires a user name and password to access the folder. The problem is that it doesn't seem to accept what I give it. It just reloads the pop-up with my password hilighted, as if it wants different information. I know my password is correct, as I've had to use it constantly while tweaking Lubuntu. And I'm %99.99999 certain of my user name. Anyway - I can change the Samba settings to "Allow access to everyone", and it lets me in without a fuss. But I'm really wondering why it won't take my info. Any ideas?

Samba requires that you explicitly set the same unix/linux username and password into it's own database for smb access.

```
sudo smbpasswd -a username
```

> In Gigolo I highlight my Windows machine in the sidebar and click the connect button above. This gives me the "connect to server" options dialog. For the "server type" I choose "Windows Share" (don't see how I could be wrong about that one), and for the "server" option I wasn't sure if that was the name of the pc I'm trying to access, or the name of the networks work group. Tried both - no dice. Under the "share" option I assumed that this wanted the name of the folder I'm trying to access (assuming permissions are set up correctly in Windows - which they should be). But do they want the full path? Or just the name of the folder (or in my case the name of the drive)?

Gigolo/pcmanfm connect a.k.a. mount the share not the server.
Open pcmanfm,menu:Go/Network Drives,Dbl click the Windows Network icon on Right pane(Ignore the server icons),Dbl click the workgroup named folder,dbl click the share name folder. If your share is password protected it will ask you for the password before access. Gigolo does the same thing with a slightly different gui and relies on pcmanfm to display share contents.Set the view as Detailed list,there are rt click menu's and buttons to connect,bookmark shared folders.It does have the advantage of the refresh networks button. You may have to reboot and start lubuntu after your windows box offering the shares before it will see them without Gigolo refresh.
Mount location  is ~/.gvfs

---

### Post by ~Maxx on 2011-01-02
> **cavalier911 said:**
> Samba requires that you explicitly set the same unix/linux username and password into it's own database for smb access.

```
sudo smbpasswd -a username
```
How did I not come across that in all the reading I did?  Hmm...


> **cavalier911 said:**
> 
Gigolo/pcmanfm connect a.k.a. mount the share not the server.
Open pcmanfm,menu:Go/Network Drives,Dbl click the Windows Network icon on Right pane(Ignore the server icons),Dbl click the workgroup named folder,dbl click the share name folder. If your share is password protected it will ask you for the password before access. Gigolo does the same thing with a slightly different gui and relies on pcmanfm to display share contents.Set the view as Detailed list,there are rt click menu's and buttons to connect,bookmark shared folders.It does have the advantage of the refresh networks button. You may have to reboot and start lubuntu after your windows box offering the shares before it will see them without Gigolo refresh.
Mount location  is ~/.gvfs
Again - why was this not mentioned in anything I read?  Seems somewhat obvious now.  Works great!  In fact it seems that I could probably uninstall Gigolo.  We'll see.  Thanks so much!

---

