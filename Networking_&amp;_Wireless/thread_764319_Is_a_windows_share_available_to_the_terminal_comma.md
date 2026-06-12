---
title: "Is a windows share available to the terminal command line?"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by PaulHuffman on 2008-04-23
I have some big txt files on an XP that I am processing on my Linux machine with sed.  I made a connection to the windows share with Nautilus, and drag them over to the Linux file system for processing, then drag them back. When I make a connection to windows like that, is that window file system mounted somewhere in the Linux file tree so that I can go to a terminal window and invoke my sed script on the files with a linux path so that my scripts acts on those files through the mount in their location in windows so I don't have to move them?

---

### Post by RealPSL on 2008-04-23
Based on your need I would suggest that you look at 2 commands ```
smbclient
```
and
```
smbmount
```
The first will allow you to connect directly to the windows share from the the terminal. The second will allow you to mount the share just like any other file system.

---

### Post by PaulHuffman on 2008-04-23
Thanks for the quick reply.  So I guess Nautilus hasn't made those mounts for me.  

I've used smbclient and smbmount on my Solaris machine, so I have some background in this. On this Ubuntu system, I can find smbclient, but whereis can't find smbmount, and that's probably what would work best for me. Do I have to get it and install it?  How about using PyNeighborhood?

---

### Post by Iowan on 2008-04-23
The results of my attempt to run **smbmount**:```
The program 'smbmount' is currently not installed.  You can install it by typing:
sudo apt-get install smbfs
bash: smbmount: command not found

```

---

### Post by dmizer on 2008-04-24
for more details, you can see the "mounting samba shares" link in my sig.

---

### Post by PaulHuffman on 2008-04-24
Cool. I have my smbmounts set up and in production now.  The samba mounts also show up in the Nautilus file browser.

That's a cool feature of Linux, or is it just ubuntu, that when I type smbmount, I get the report that it is currently not installed and gives you the way to install it. Linux knows what it doesn't know. When I type smbmount on Solaris 9, I just get command not found. 

I was just going to ask how I can make my mounts persistent, but I see that dmizer's write up covers that. You edit the smb mounts into fstab. I'll try that next. 

Thanks for getting me on my way.

---

### Post by PaulHuffman on 2010-08-23
That worked great for a couple years. I upgraded now to 10.04. Rather than editing fstab,  I made some little desktop scripts and put them in launchers so I could make the mounts just when I needed them and when I knew they were available.  In my launchers, I have lines like  
smbmount //paule6500/docs /home/paul/pauldocs -o username=xxxx,password=xxxxx.

However, this morning they wouldn't run.  I just got a message "mount error(1): Operation not permitted
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)" I played around with it for a little bit and discovered that the same syntax works if I preface it with sudo. Did that just change with the system updates I ran this morning?  Did we discover a security hole?

---

### Post by PaulHuffman on 2010-10-20
And now it's worse.  Now I find that I can't write to the windows share. Says "Permission denied".  Same if I make a share with the Nautilus GUI. Now what's going on?  Now that sudo seems to be required, the mounted folders are all owned by root?

---

