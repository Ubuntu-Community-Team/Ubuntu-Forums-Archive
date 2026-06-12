---
title: "Confused about mount"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by EricBJ on 2009-01-25
I use Places > Network, I can see and access the Windows shares on the rest of my network.  I get an icon on my desktop which I am assuming is my mount point.  These shares show up in Nautilus.

The problem comes in when I want to access one of these shares with a program.  They can't see these Windows shares.

What am I missing?  How do I mount these shares so that my programs can see them too?

Thanks,
Eric

---

### Post by mikewhatever on 2009-01-25
No, an icon on the desktop isn't the mount point. Things are usually mounted under /media/something.

---

### Post by jerome1232 on 2009-01-25
Actually those should be mounted by gvfs.

To access them as a normal folder browse to ~/.gvfs you should be able to find them in there.

---

### Post by EricBJ on 2009-01-25
> **mikewhatever said:**
> No, an icon on the desktop isn't the mount point. Things are usually mounted under /media/something.

The only items in the /media folder are, 2 links to cdrom and floppy, and 3 folders cdrom0, cdrom1 and floppy0.

Thanks

---

### Post by EricBJ on 2009-01-25
> **jerome1232 said:**
> Actually those should be mounted by gvfs.

To access them as a normal folder browse to ~/.gvfs you should be able to find them in there.

The only .gvfs folder I could find was in my home folder /home/eric, is that the one you are talking about?

Also that folder was empty, even with "Show Hidden Files" turned on in Nautilus.

Thanks

---

### Post by mikewhatever on 2009-01-25
Odd, can you post the output of <df -h>.

---

### Post by EricBJ on 2009-01-25
> **mikewhatever said:**
> Odd, can you post the output of <df -h>.

...as requested...

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             19G   12G  5.9G  66% /
varrun                  759M  148K  759M   1% /var/run
varlock                 759M     0  759M   0% /var/lock
udev                    759M   56K  759M   1% /dev
devshm                759M  220K  759M   1% /dev/shm
lrm                      759M   39M  720M   6% /lib/modules/2.6.24-23-generic/volatile

What does this tell you?

Thanks

---

### Post by callan79 on 2009-01-25
> **jerome1232 said:**
> Actually those should be mounted by gvfs.
To access them as a normal folder browse to ~/.gvfs you should be able to find them in there.


Hello,

There's actually a better way to do this.

Basically 'connect to server' like you have done is OK if you want to browse files etc, but it doesn't really set it up as a 'drive' that the system can recognise.

If you have a network share that you'll be accessing all the time you really need to look at mounting it permanently.

Assuming the other machine is sharing a folder with Linux+Samba, or Windows XP file sharing, do this :


(1) Make a mount point called fred (change it to suit your needs) :

```

cd /media
sudo mkdir fred
sudo chown yourusername:yourgroupname fred
ls -l /media/

```

(2) Install smbfs :

```

sudo apt-get install smbfs

```

(3) Put the mount entries into /etc/fstab :

```

sudo nano /etc/fstab

```

Put the following in there. Naturally you have to change :
[LIST]
[*]192.168.1.1 to the remote computer's IP Address
[*]'sharename' to the name of the shared folder on the remote computer
[*]/media/fred to the mount point you created in (1) above
[*]YOURUSERNAME/YOURPASSWORD to your username/password on the remote computer
[*]YOURUSERNAME/YOURGROUPNAME to your user/group name on the local machine
[/LIST]

```

//192.168.1.1/sharedfolder /media/fred cifs auto,user=YOURUSERNAME,password=YOURPASSWORD,uid=YOURUSERNAME,gid=YOURGROUPNAME 0 0

```

(4) Try to mount it :

```

sudo mount -a

```

Then check it's mounted :

```

mount

```

Hopefully you get something like this in there :

```

//192.168.1.1/sharename on /media/fred type cifs (rw,mand)

```


So now the device is mounted permanently, and you should be able to access everything as normal :)

Good luck!

Callan

---

### Post by EricBJ on 2009-01-25
Thanks Callan for the suggestion, it seemed to go well.

I figured as a final test to make sure that it was working fine, I threw a file in the folder from a different machine.  Then I checked that folder from my Ubuntu system.  No file...

I go to Places > Network and I access the folder as I had before...   ...there is the file.

I don't understand...

---

### Post by EricBJ on 2009-01-25
> **EricBJ said:**
> Thanks Callan for the suggestion, it seemed to go well.

I figured as a final test to make sure that it was working fine, I threw a file in the folder from a different machine.  Then I checked that folder from my Ubuntu system.  No file...

I go to Places > Network and I access the folder as I had before...   ...there is the file.

I don't understand...


I had a thought that I should try the reverse...

I attempted to put a file in the folder from my Ubuntu system.  I got "permission denied".

I must have messed up a setting.  The only thing about that fstab statement that I'm not completely certain about is the "user group name" on the local machine.  How do I determine what my "user group name" is?

Thanks,
Eric

---

### Post by callan79 on 2009-01-26
> **EricBJ said:**
> I attempted to put a file in the folder from my Ubuntu system.  I got "permission denied".

I must have messed up a setting.  The only thing about that fstab statement that I'm not completely certain about is the "user group name" on the local machine.  How do I determine what my "user group name" is?



Hey Eric,

You can find your username and group name with the 'id' command (the 'whoami' command is useful too, but only shows your username).

Here's what my 'id' command shows up ... you'll see that my username and group name are the same, which is actually pretty much system default in Ubuntu.

```

callan@brutis:~$ id
uid=1000(callan) gid=1000(callan) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(callan)

```

So you can pretty much ignore everything except the uid and gid.

With the /etc/fstab thing that I mentioned earlier, the uid and gid are quite important ... they don't have anything to do with the way you *connect* to the share, but they do control how the mount appears to you on the local machine. So if you present the wrong uid and gid, you won't have permission to access it.

If you still have issues, please send output from these commands :

```

mount

```

```

ls -l /media/

```

Good luck :)

Callan

---

### Post by EricBJ on 2009-01-26
> **callan79 said:**
> Hey Eric,

You can find your username and group name with the 'id' command (the 'whoami' command is useful too, but only shows your username).

Here's what my 'id' command shows up ... you'll see that my username and group name are the same, which is actually pretty much system default in Ubuntu.[INDENT]That's good to hear, I was really starting to wonder when my username and group name were both "eric".
[/INDENT]> ```

callan@brutis:~$ id
uid=1000(callan) gid=1000(callan) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(callan)

```So you can pretty much ignore everything except the uid and gid.

With the /etc/fstab thing that I mentioned earlier, the uid and gid are quite important ... they don't have anything to do with the way you *connect* to the share, but they do control how the mount appears to you on the local machine. So if you present the wrong uid and gid, you won't have permission to access it.[INDENT]Ok, then it looks like it is mounting properly and I am also getting an icon on the desktop which I assume represents the folder the share is mounted in.
[/INDENT]> If you still have issues, please send output from these commands :

```

mount

``````

ls -l /media/

```Good luck :)

Callan[INDENT]Thanks you were a great help.

Just one more question, at the end of the statement in fstab, what does "0 0" mean?

[/INDENT]Thank you again, I really appreciate your assistance.
Eric

---

### Post by callan79 on 2009-01-27
> **EricBJ said:**
> it looks like it is mounting properly and I am also getting an icon on the desktop which I assume represents the folder the share is mounted in.
Just one more question, at the end of the statement in fstab, what does "0 0" mean?


Hi Eric,

That specifies certain attributes regarding auto-checking of filesystem integrity etc. I haven't really messed with these too much, I just put 0 0 for network mounts, and 0 2 for local mounts (I copied what I saw already there).

For a more detailed explanation, do a 'man fstab' in your terminal, and check out lines 67 onwards ("the fifth field..." and "the sixth field...")

Cheers
Callan

---

