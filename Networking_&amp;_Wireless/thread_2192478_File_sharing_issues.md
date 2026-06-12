---
title: "File sharing issues"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by threezero on 2013-12-08
New Ubuntu guy, 13.10.
I recently purchased a system76 computer and trying to share folders/files.  I have other Ubuntu and Windows systems on my home network so I've gone the samba route.  I've got all the other computers talking...except the new system76 computer.  I go though the normal routine (right click to sharing and set it up) and all seems normal but I continue to get an "Unable to access location, Failed to mount windows share: permission denied" error when trying to access the files from another ubuntu or windows system.
Ideas?

---

### Post by bab1 on 2013-12-08
> **threezero said:**
> New Ubuntu guy, 13.10.
I recently purchased a system76 computer and trying to share folders/files.  I have other Ubuntu and Windows systems on my home network so I've gone the samba route.  I've got all the other computers talking...except the new system76 computer.  I go though the normal routine (right click to sharing and set it up) and all seems normal but I continue to get an "Unable to access location, Failed to mount windows share: permission denied" error when trying to access the files from another ubuntu or windows system.
Ideas?

Did you make the share available to *everyone*?  Is the underlying file system set  to allow all to access to all users?  Post the output of this terminal command```
sudo net usershare info --long
```

---

### Post by threezero on 2013-12-08
BAB1, thanks for the response; I've tried multiple options of sharing including all users and guests, also tried changing folder settings and shortened the names.  the output is below:

info_fn: file /var/lib/samba/usershares/our documents backup 11022013 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[DocBackup]
path=/media/thirty/Extra Drive 1/DocBackup
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/ourphotosbackup is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/our docs backup 11022013 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[Dave's on Linux]
path=/home/thirty/Documents/Dave's on Linux
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Sharetest]
path=/home/thirty/Documents/Sharetest
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/our photos backup is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[PhotosBackup]
path=/media/thirty/Extra Drive 1/PhotosBackup
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by bab1 on 2013-12-08
> **threezero said:**
> BAB1, thanks for the response; I've tried multiple options of sharing including all users and guests, also tried changing folder settings and shortened the names.  the output is below:

[COLOR="#FF0000"]info_fn: file /var/lib/samba/usershares/our documents backup 11022013 is not a well formed usershare file.
info_fn: Error was Path is not a directory.[/COLOR]
[DocBackup]
path=/media/thirty/Extra Drive 1/DocBackup
comment=
usershare_acl=Everyone:F,
guest_ok=y

[COLOR="#FF0000"]info_fn: file /var/lib/samba/usershares/ourphotosbackup is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/our docs backup 11022013 is not a well formed usershare file.
info_fn: Error was Path is not a directory.[/COLOR]
[Dave's on Linux]
path=/home/thirty/Documents/Dave's on Linux
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Sharetest]
path=/home/thirty/Documents/Sharetest
comment=
usershare_acl=Everyone:F,
guest_ok=y

[COLOR="#FF0000"]info_fn: file /var/lib/samba/usershares/our photos backup is not a well formed usershare file.
info_fn: Error was Path is not a directory.[/COLOR]
[PhotosBackup]
path=/media/thirty/Extra Drive 1/PhotosBackup
comment=
usershare_acl=Everyone:F,
guest_ok=y
The shares with the error (in red) need to be corrected or the share removed.  I don't mean the data in the share but the share itself.

Let's look at  [Sharetest] to see what is wrong with that.  The share looks fine from this view.  What are the permissions all along the path.  Post the output of ```
ls -l /home/thirty

ls -l /home/thirty/Documents

ls -l /home/thirty/Documents/Sharetest 
```

---

### Post by threezero on 2013-12-08
I'm surprised the shares is red showed up--they were different attempts I tried but none of those share ares "active" when i select them.

thirty@Linux76a:~$ ls -l /home/thirty
total 68
-rw-r--r-- 1 thirty thirty    0 Nov 11 13:05 0
drwxr-xr-x 2 thirty thirty 4096 Nov 12 22:11 Desktop
drwxr-xr-x 4 thirty thirty 4096 Dec  7 22:18 Documents
drwxr-xr-x 2 thirty thirty 4096 Nov 27 23:41 Downloads
-rw-r--r-- 1 thirty thirty 8980 Nov  2 16:00 examples.desktop
drwxr-xr-x 2 thirty thirty 4096 Nov 11 08:39 fvtmp
drwxr-xr-x 2 thirty thirty 4096 Nov  2 16:01 Music
drwxr-xr-x 2 thirty thirty 4096 Nov  2 22:58 Pictures
drwxr-xr-x 2 thirty thirty 4096 Nov  2 16:01 Public
drwxr-xr-x 2 thirty thirty 4096 Nov  2 16:01 Templates
drwxrwxr-x 2 thirty thirty 4096 Nov  2 19:51 Ubuntu One
drwxr-xr-x 2 thirty thirty 4096 Nov  2 16:01 Videos
thirty@Linux76a:~$ ls -l /home/thirty/Documents
total 8
drwxrwxrwx 2 thirty thirty 4096 Nov  2 20:02 Dave's on Linux
drwxrwxrwx 2 thirty thirty 4096 Dec  7 22:17 Sharetest
thirty@Linux76a:~$ ls -l /home/thirty/Documents/Sharetest
total 0
thirty@Linux76a:~$

---

### Post by bab1 on 2013-12-08
> **threezero said:**
> I'm surprised the shares is red showed up--they were different attempts I tried but none of those share ares "active" when i select them.

```
thirty@Linux76a:~$ ls -l /home/thirty
total 68
drwxr-xr-x 4 thirty thirty 4096 Dec  7 22:18 Documents

```

```
thirty@Linux76a:~$ ls -l /home/thirty/Documents
total 8
drwxrwxrwx 2 thirty thirty 4096 Dec  7 22:17 Sharetest
```

```

thirty@Linux76a:~$ ls -l /home/thirty/Documents/Sharetest
total 0
thirty@Linux76a:~$
```

After removing all the other data we have just the path to Sharetest.  It looks fine.  There are no file in this share however.

Post the output of this command```
smbtree
```

---

### Post by threezero on 2013-12-08
I put a file into sharetest.

thirty@Linux76a:~$ smbtree
Enter thirty's password: 
WORKGROUP
    \\LINUX76A               Linux76a server (Samba, Ubuntu)
        \\LINUX76A\Dave's on Linux    
        \\LINUX76A\Sharetest          
        \\LINUX76A\PhotosBackup       
        \\LINUX76A\EPSON-WF-3540-Series    EPSON WF-3540 Series
        \\LINUX76A\print$             Printer Drivers
        \\LINUX76A\IPC$               IPC Service (Linux76a server (Samba, Ubuntu))
    \\EPSON09DF32            
        \\EPSON09DF32\FAXRECV            EPSON
        \\EPSON09DF32\USBSTORAGE         EPSON
        \\EPSON09DF32\MEMORYCARD         EPSON
        \\EPSON09DF32\IPC$               IPC Service
    \\DOPTIPLEXD             DoptiplexD server (Samba, Ubuntu)
        \\DOPTIPLEXD\Documents          
        \\DOPTIPLEXD\WF-3540-Series     WF-3540 Series
        \\DOPTIPLEXD\print$             Printer Drivers
        \\DOPTIPLEXD\IPC$               IPC Service (DoptiplexD server (Samba, Ubuntu))
    \\APRECISIONA            
        \\APRECISIONA\OUR DOCUMENTS      
        \\APRECISIONA\D on aprecisiona    
        \\APRECISIONA\C$                 Default share
        \\APRECISIONA\ADMIN$             Remote Admin
        \\APRECISIONA\Our Pictures       
        \\APRECISIONA\Shared Documents    
        \\APRECISIONA\print$             Printer Drivers
        \\APRECISIONA\IPC$               Remote IPC
        \\APRECISIONA\30A_Printer        EPSON WF-3540 Series
MSHOME
    \\COPTIPLEXC             Kids Left
        \\COPTIPLEXC\C$                 Default share
        \\COPTIPLEXC\ADMIN$             Remote Admin
        \\COPTIPLEXC\SharedDocs         
        \\COPTIPLEXC\IPC$               Remote IPC
thirty@Linux76a:~$

---

### Post by bab1 on 2013-12-08
> **threezero said:**
> I put a file into sharetest.

```
thirty@Linux76a:~$ smbtree
Enter thirty's password: 
WORKGROUP
    \\LINUX76A               Linux76a server (Samba, Ubuntu)
        \\LINUX76A\Dave's on Linux    
       [COLOR="#FF0000"] \\LINUX76A\Sharetest [/COLOR]      
        \\LINUX76A\PhotosBackup       
        \\LINUX76A\EPSON-WF-3540-Series    EPSON WF-3540 Series
        \\LINUX76A\print$             Printer Drivers
        \\LINUX76A\IPC$               IPC Service (Linux76a server (Samba, Ubuntu))
    \\EPSON09DF32            
        \\EPSON09DF32\FAXRECV            EPSON
        \\EPSON09DF32\USBSTORAGE         EPSON
        \\EPSON09DF32\MEMORYCARD         EPSON
        \\EPSON09DF32\IPC$               IPC Service
    \\DOPTIPLEXD             DoptiplexD server (Samba, Ubuntu)
        \\DOPTIPLEXD\Documents          
        \\DOPTIPLEXD\WF-3540-Series     WF-3540 Series
        \\DOPTIPLEXD\print$             Printer Drivers
        \\DOPTIPLEXD\IPC$               IPC Service (DoptiplexD server (Samba, Ubuntu))
    \\APRECISIONA            
        \\APRECISIONA\OUR DOCUMENTS      
        \\APRECISIONA\D on aprecisiona    
        \\APRECISIONA\C$                 Default share
        \\APRECISIONA\ADMIN$             Remote Admin
        \\APRECISIONA\Our Pictures       
        \\APRECISIONA\Shared Documents    
        \\APRECISIONA\print$             Printer Drivers
        \\APRECISIONA\IPC$               Remote IPC
        \\APRECISIONA\30A_Printer        EPSON WF-3540 Series
MSHOME
    \\COPTIPLEXC             Kids Left
        \\COPTIPLEXC\C$                 Default share
        \\COPTIPLEXC\ADMIN$             Remote Admin
        \\COPTIPLEXC\SharedDocs         
        \\COPTIPLEXC\IPC$               Remote IPC
thirty@Linux76a:~$
```
Do we have success?  I see the share (in red).

---

### Post by threezero on 2013-12-08
still getting the same error message when I attempt to access sharetest from another linux or windows computer...

---

### Post by threezero on 2013-12-08
don't know if this is a symptom of something else, but when I reboot, the sharetest folder reverts to not shared.

---

### Post by bab1 on 2013-12-08
> **threezero said:**
> don't know if this is a symptom of something else, but when I reboot, the sharetest folder reverts to not shared.

Yes that is a problem.  It should persist through re-boots.  Are you sure you are "Applying" the share and permissions and not just closing the sharing dialog box? I don't share data from my user home directory so I don't use usershares that often.  Maybe others can chime in here?

Do you know how to edit the smb.conf file?  I would try and create a share for Sharetest via smb,conf (after removing the usershare) and see if that works.  If it does then the directory structure and permissions are correct.  Just a thought is there an external mounted HDD involved in this configuration.

Post the output of these commands ```
df -h

sudo blkid -c /dev/null -o list
```

---

### Post by threezero on 2013-12-09
That's why I'm thinking it may be some other more basic issue that I'm missing--I'm going to reinstall 13.10 and see if that solves it (since it works fine on the other computers).  and no, there just an internal SSD and HDD, nothing external.

---

### Post by bab1 on 2013-12-09
> **threezero said:**
> That's why I'm thinking it may be some other more basic issue that I'm missing--I'm going to reinstall 13.10 and see if that solves it (since it works fine on the other computers).  and no, there just an internal SSD and HDD, nothing external.
That would be what I would do.  If only to provide a known good baseline of the OS.

Edit: I assume the HDD is mounted at /home and it is formatted EXT4.

---

### Post by threezero on 2013-12-23
I was able to get the sharetest folder on the system SSD to share correctly when I reinstalled the OS.  However, still can't get the additional HDD to share.  I can see the HDD from the other XP and Ubuntu systems but then it asks for a user name and password (tried all them associated with the system without any luck).  I've read up on the smb.conf and added the line "usershare owner only=false" as recommended by the OS but still asks for password to access the drive/folder.

---

### Post by bab1 on 2013-12-23
> **threezero said:**
> I was able to get the sharetest folder on the system SSD to share correctly when I reinstalled the OS.  However, still can't get the additional HDD to share.  I can see the HDD from the other XP and Ubuntu systems but then it asks for a user name and password (tried all them associated with the system without any luck).  I've read up on the smb.conf and added the line "usershare owner only=false" as recommended by the OS but still asks for password to access the drive/folder.

Where does ""usershare owner only=false" as recommended by the OS" occur.  I've never seen that.   The man page says```
usershare owner only

    If set [COLOR="#FF0000"]only directories **[SIZE=2]owned[/SIZE]**[/COLOR] by the sharing user can be shared.
``` no false of true at all.Since you have made all of these changes you need to provide the new settings for us to continue.  Go back and find all the questions I asked and restate them with the current configuration.

---

### Post by threezero on 2013-12-24
when I tried to share the entire "Extra Drive 1" an error popped up and said something like "have the administrator add usershare owner only=false to the global section of smb.conf."  ...by the way, I'm now confortable editing the smb.conf!

The only share that wont work now is on the extra drive or folders on it.  when I ran smbtree, the shares appear normal but still can't access.  the path to the extra drive is /media/thirty/Extra Drive 1/fileserver.  Could the path be an issue?

[FileServer]
path=/media/thirty/Extra Drive 1/FileServer
comment=
usershare_acl=Everyone:F,
guest_ok=y

WORKGROUP
    \\SYSTEM76               System76 server (Samba, Ubuntu)
        \\SYSTEM76\Extra Drive 1      
        \\SYSTEM76\FileServer         
        \\SYSTEM76\HD2 SY76           
        \\SYSTEM76\Sharetest

---

### Post by threezero on 2013-12-24
This share to home works fine

[Sharetest]
path=/home/thirty/Documents/Sharetest
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by bab1 on 2013-12-24
> **threezero said:**
> This share to home works fine

[Sharetest]
path=/home/thirty/Documents/Sharetest
comment=
usershare_acl=Everyone:F,
guest_ok=y

The problem is for sure creating usershares outside of your home directory.  The update should be added back in and the system rebooted if user shared are what you want to use.  But I think you should learn how to make a test share via the smb.conf file.  You can just add them to the bottom of the smb.conf file with this format```

[name of share]
comment = Description of Share
path = /path/to/directory            #best if it has no spaces
guest ok = yes
create mask = 0664
directory mask = 0775

```

Try this simple share to see if it works.  Remember that the directory that you share has to have at least read and execute permissions and the files should at least be readable (664 or somesuch)

---

### Post by threezero on 2013-12-24
I'll add it in. and how do I access the entire samba manual?
btw, thanks for all your help

---

### Post by bab1 on 2013-12-24
> **threezero said:**
> I'll add it in. and how do I access the entire samba manual?
btw, thanks for all your help

The manual for Samba 3.X is at :[http://www.samba.org/samba/docs/Samba3-HOWTO.pdf]("http://www.samba.org/samba/docs/Samba3-HOWTO.pdf")

Here is a good howto called Samba by Example: [http://www.samba.org/samba/docs/man/Samba-Guide/]("http://www.samba.org/samba/docs/man/Samba-Guide/")

This is a listing of the Samba man pages in HTML format: [http://www.samba.org/samba/docs/man/manpages-3/]("http://www.samba.org/samba/docs/man/manpages-3/")

The man page for smb.conf in particular is: [http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")

All the man pages are available from the terminal using the command ```
man <subject>
```

Read the By Example howto at least the beginner parts after the install.  The install stuff is not needed.  Ubuntu packaging takes care of all that kind of stuff.

---

