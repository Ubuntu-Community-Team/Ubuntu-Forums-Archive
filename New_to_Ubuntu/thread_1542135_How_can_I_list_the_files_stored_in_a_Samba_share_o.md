---
title: "How can I list the files stored in a Samba share on another computer?"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by johniathome on 2010-07-30
In a terminal session I can cd to a local directory (eg cd /home/user1) then ls.

The Location column in Nautilus shows the correct path.

However, the Location column in Nautilus shows the location of the share as 

	 smb://freenas.local/n-data-new/~~~N-DELTA

If I open a terminal session and try 
   	cd smb://freenas.local/n-data-new/~~~N-DELTA

...it says there is no such directory.

How can I cd into this directory? There must be a very simple answer to this question!

---

### Post by Naitsirhc Hsem on 2010-07-30
Samba has to be mounted manually in the CLI to be able to be accessed in the CLI.  There are plenty of forums here about this, try samba mount command in th search

---

### Post by johniathome on 2010-07-30
After a trawl I found the following useful links:

[http://www.debian-administration.org/articles/165](http://www.debian-administration.org/articles/165)


And from 2006, a cry for “*Gnome/Nautilus Needs to MOUNT Samba Shares to the Filesystem!” I agree!

[http://ubuntuforums.org/showthread.php?p=1748025#post1748025](http://ubuntuforums.org/showthread.php?p=1748025#post1748025)



Share name = n-data-new 
on server = freenas 
with user name = Administrator

This worked for me...

Install smbfs:
	sudo apt-get install smbfs

load the kernel module
	sudo modprobe smbfs

Create a new directory to be the mount-point:
	sudo mkdir -p /mnt/fn

To actually perform the mount we have to run
	sudo mount -t smbfs -o username=Administrator //freenas.local/n-data-new /mnt/fn  
Asks for password, so enter it.

Now we can:
	cd /mnt/fn
	ls

---

### Post by Morbius1 on 2010-07-30
If you are trying to access the remote share from a Terminal only and you have not already mounted the share locally then this will open up an ftp like session:

```
smbclient //192.168.0.100/sharename 
```It will ask you for a password:
If it's a public share just hit enter.
If it's an authenticated share then type the correct samba password
You should end up with a prompt in the terminal that looks like this: 
> [COLOR=Blue]smb:\>[/COLOR] Then type:
```
ls
```Note: Type [COLOR=Blue]**quit**[/COLOR] to end the smbclient session

If you've already mounted it using "Network" in Nautilus then it's mounted at /home/your_user_name/.gvfs. So to change directories you would:
```
 cd /home/your_user_name/.gvfs/"share_name on Server_name"
```[COLOR=Blue]EDIT: Or you could do it the way you just did it[/COLOR] :)

---

### Post by lkraemer on 2010-08-01
If the following are assumed:
1.  FreeNAS has CIFS/SMB "ENABLE" checked
2.  FreeNAS Share has been specified
3.  You know the FreeNAS IP Address (Default = 192.168.1.250)
4.  You can Ping the FreeNAS IP (Must be able to ping!!!)
5.  FreeNAS *WORKGROUP* and M$ *WORKGROUP* names **MATCH**

then you should be able to use:

1.  From your Browser use - smb://192.168.1.250
2.  In M$ Wonders click on NETWORK on the START Menu.  Wonders should
    scan for shared resources.  You should see your FreeNAS Share!
    Drill Down to where you want to go.
3.  Map a Network drive after following #2 above. 
4.  To Access the FreeNAS Share without using NETWORK on the Start Menu:
    Click START, and then type //*freenas * and press ENTER.
    (where *freenas* is the correct name of your Share!)

**REF: - FreeNAS Setup and User Guide  -  SUG**
[http://freenas.org/documentation:setup_and_user_guide](http://freenas.org/documentation:setup_and_user_guide)

lk

---

### Post by johniathome on 2010-08-10
Morbius1:
Thanks for your comment, especially about the .gvfs mount point. I think that solves it for now.

Ikraemer:
Thanks for your comment too.
However, my problem was accessing a Samba share from Ubuntu,
and your comment refers to Windoze.
BTW, I think freenas is absolutely marvellous, 
and I have had zero problems with it in Windoze.

---

