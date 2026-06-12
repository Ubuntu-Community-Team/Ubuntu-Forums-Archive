---
title: "trying to get network working with 2 ubuntu boxes and router"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by mattk132 on 2008-03-20
Hey all.  I am only 14 but I do know my way around ubuntu and xp.  I have an old machine my friend gave me.  I installed ubuntu on it and I am trying to get it into a small network with a router.  I don't have a switch or hub.  I only have a router.  When I plugged both in they had internet but simply didn't show eachother under places->network.  Any help is greatly appreciated.:)

---

### Post by drdos2006 on 2008-03-20
I believe you may have to :-

Add a Network User
On Linux, you need an additional step for each user who needs to be authenticated on the network. 

From the menubar, 
select “System” -> “Administration” -> “Users and Groups” -> “+Add User” -> “Account”. 
Add the new user and enter the password.
Select “User Priveleges” and select/de-select those items allowed for this user.
Select “Advanced” and enter the Home Directory for this user Close and save.

Do the same on the second machine for the first user.
Do the same on the first machine for the second user.

You may need to share a file or folder on each machine to see the opposite machine.

regards

---

### Post by mattk132 on 2008-03-20
Thanks.  Wow that was a quick response.  But, I have a question.  How do I share folders over the network.:)

---

### Post by drdos2006 on 2008-03-20
Try this.

Sharing Directories or Folders
To share an existing Ubuntu directory with Windows networking.
From the menubar, 
select “System” -> “Administration” -> “Shared Folders” -> “Shared Folders”.
Select the folder path to be shared, share through “Windows networks (SMB)”.
Select the properties name, for instance “Big Video”, (untick “Read Only” if you want Windows network users to add videos to the folder). Click “OK”.
Now select the “General Properties” and in the “Windows Sharing” section, enter the Windows Domain/Workgroup name of the Windows network group to connect to the Ubuntu box. For the “WINS server” address, the IP address of the Netgear router ( gateway ) was entered. Close the shared folder settings.

To create a new Ubuntu folder and share it with Windows networking.
From the menubar, 
select “Places”, browse to where the shared folder is to be created, create a folder to be shared with “File” -> “Create Folder”.
Go to “Sharing Directories or Folders” section above.

Rather than SAMBA for Windows sharing, "Share Through" Unix (NFS).
regards

---

### Post by mattk132 on 2008-03-20
Thanks for all your help I'll do these things over the weekend.  Kind of a silly question but I'm not that much of a network buff.;)

---

### Post by Eiríkr on 2008-03-20
Another potentially simpler option is to install the [font=courier]ssh[/font] package on both machines, and then access by typing into the location bar (hidden by default in Nautilus, but display-able by hitting Ctrl+L or clicking View -> Location Bar) [font=courier]sftp://IP.ADD.RE.SS[/font], replacing the caps with the numerical IP address of the other machine.  No configuration, no muss, no fuss.  8)

As Dr Dos notes, Samba is really best suited to sharing with Windows machines, and while it can be used for Lin -> Lin sharing too, configuration can be very complex, and the number of Samba-related help requests on this board should be one indication of the difficulty in getting it to work just so.  

Meanwhile, NFS is one of the original Unixy filesharing systems, first developed by Sun and IBM back in 1984 before the outbreak of the Unix Wars (history [here](http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29)), and is great for Lin -> Lin ([post=4387032]and even Lin -> Mac[/post]) sharing, but Nautilus in its current form **cannot** browse NFS shares unless they are first mounted onto the local filesystem, via the command line:
```
sudo mount -t nfs SERVERIP:/SHARE /MOUNTPOINT
```
See [font=courier]man nfs[/font] and [font=courier]man mount[/font] for details on the various options possible.  Also, the numerical user and group IDs must be identical on both machines (or mapped, which can get extremely complicated), or you'll get very wierd permissions behaviour.  You can check ID numbers by running:
```
id USERNAME
```

Cheers,

Eiríkr

---

### Post by mattk132 on 2008-03-23
Thanks for all your help but, I can't get this to work.  I think I know why though.  For my main pc I can share with smb.  But on my worse pc I can't share it with smb.  I am wondering how to get it so that I can share the files on my worse pc with smb.  And by the way I am sharing all files to both machines.  I don't have to worry about permissions.  Nobody but me is using these 2 machines.  Any help is greatly appreciated.:)

---

### Post by Eiríkr on 2008-03-23
Re-reading the thread, it occurs to me I'm a bit confused about your setup.  You have two computers; are both running Ubuntu, or is one of them an XP machine?  

Cheers,

Eiríkr

---

### Post by mattk132 on 2008-03-24
They are 2 ubuntu machines.  I just upgraded both of them last night to 8.04.  They are both plugged into one router.:)

---

### Post by Eiríkr on 2008-03-24
Note that for two-way sharing, you need Samba installed and configured on both machines.  

In your previous post when you said "I can't get this to work", what were you referring to?  SFTP is a pretty striaghtforward, no-muss-no-fuss sharing method between Unixy machines.  Or were you referring to something else?

Cheers,

Eiríkr

---

### Post by mattk132 on 2008-03-25
I was referring to the windows way of networking.  But I get it now.  So, I just configure samba on both machines and use my network through that right?  :) Thanks!

---

### Post by mattk132 on 2008-03-29
Thanks for all of your help so far.  But, I have a little problem again.  On my main machine I used to have a shared folders program under: System --> Administration --> Shared folders.  But now I don't it literally just dissappeared.:(

---

### Post by Eiríkr on 2008-03-29
Bear in mind that Ubuntu 8.04 Hardy Heron is **still in beta status**.  Beta builds are incomplete, and are released so that the user community can help *test* it.  This pretty much guarantees that a number of things are *not* going to work properly.  If you want a more stable and more functional Ubuntu install, replace your 8.04 installations with the current 7.10 version.  

Cheers,

Eiríkr

---

### Post by mattk132 on 2008-03-31
Look I just got it shared so that I can see the files from the machine I'm looking at under the network tab.  But, not from the opposite comp.  Also, another problem my shared folders program is nwo gone:(

---

### Post by Eiríkr on 2008-04-01
What do you mean by your "shared folders program is now gone"?  Is there a GUI menu you are referring to, or has the package been uninstalled somehow?  :confused:

Cheers,

Eiríkr

---

### Post by xeth on 2008-04-01
When I installed an alpha of Hardy I think it was incomplete, couldn't get file sharing to work. But anyway, if there was a chance that the package was broken or corrupted due to fiddling you could just always remove and reinstall it.

---

### Post by mattk132 on 2008-04-02
Sorry for making 2 posts about the same thing.  I didn't see there were 2 pages.  (WOW!).  Anyway, I'll just wait until hardy heron actually comes out to try to get my network configured.:)

---

### Post by mattk132 on 2008-04-06
Thanks all soo much.  Sorry I was away for a few days with the family.  I got the machines shared using samba!  I don't know how but when I rebooted the 2 machines after an update they showed eachother under Places-->Network!:)  My shared folders gui program is still gone but I don't care!:) Thanks all soo much!.

---

