---
title: "Befuddled Network Map to XP Share"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by sendspalm on 2007-12-30
I've spent a fair amount of time Googling this to no avail. Here's the issue:

I have Ubuntu 7.10 installed on a new machine. I wish to access my "My Music" folder located on my Windows XP machine (separate from my Ubuntu machine). 

I'm unclear of the verbiage to access this share, especially since there is a space in the "My Music" share and I have a ! in my password. Can someone please assist?

I thought I should type:

sudo mount smbfs //192.168.1.101/My Music

but I get errors. Does Ubuntu not understand spaces?

Thanks for your help and looking forward to dumping Windows and promoting Ubuntu!

---

### Post by ultraloveninja on 2008-04-07
try to connect in nautilus 


smb://192.168.1.101/My Music

or

try to use the connect to server app and try to connect to it from there.

---

### Post by Eiríkr on 2008-04-07
If you need to mount the share, note that the **smbfs** filesystem type has been deprecated for some time and seems to be finally broken as of Samba version 3.024 or 3.026, or possibly even earlier.  You must now use the **cifs** filesystem type.  

Note also that you must specify the filesystem type using the **-t** flag, which your mount example is missing.  Likewise, you need to specify the path to an (ideally) empty directory to which the share will be mounted.  Please open a terminal and type the following to familiarize yourself with the **mount** and **mount.cifs** options.  
```
man mount
man mount.cifs
```

Ubuntu does understand spaces, but anything on the command line requires particular care (even in DOS, so no, it's not a Linux thing -- it's a space thing).  The mount command in your example (assuming you add the **-t** flag) parses the share path as "192.168.1.101/My", and then takes the next chunk after the space as the mount point for the local filesystem -- only a path of "Music" doesn't make any sense, since it isn't rooted anywhere.  

Spaces are handled differently in different cases, possibly by replacing them with %20, or possibly by escaping them with backslashes, such as /Sample\ Path\To\ Share/Data.  You might find it's safer to simply use double quotes.  

So after fixing the issues, your mount attempt should look like this:
```
sudo mount -t cifs -o rw,username=WINUSERNAME,password=WINPASSWORD,uid=UBUSERNAME,gid=UBGROUPNAME //192.168.1.101/"My Music" /PATH/TO/MOUNTPOINT
```

Replace the caps as appropriate.  The **uid** and **gid** options specify who will own the mounted directory; without these, it defaults to the user that ran the command, which is root when running as sudo.  Ownership by root means you'd need to sudo to add or edit anything in the share, which is quite inconvenient, so you're best off including these options.  

HTH,

Eiríkr

---

