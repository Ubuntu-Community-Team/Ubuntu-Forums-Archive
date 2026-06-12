---
title: "Mount nas drives"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by hvacr on 2008-05-20
I am trying to mount my Nas drive, so Amarok will see it. I followed the directions posted by user User #45536,here [http://forums.whirlpool.net.au/forum-replies-archive.cfm/971027.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/971027.html)

 which is

Just open a terminal and create the mount point:
sudo mkdir /mnt/NAS

Then set correct read/write permissions so mount point is accessible:
sudo chmod 777 /mnt/NAS

Then test that you can mount the NAS drive (Buffalo NAS HDD):
sudo mount -t cifs //192.168.0.103 /mnt/NAS -o rw,username=NASUSER,password=NASUS* ERPASSWORD

NOTE - NASUSER and NASUSERPASSWORD is a user added to your Buffalo NAS and it's password (if it has user management).

If that works, then unmount the NAS drive and edit your fstab so it mounts automatically at boot:
sudo nano /etc/fstab

Then add the lines:
# Add Buffalo NAS HDD mount
//192.168.0.103 /mnt/NAS cifs username=NASUSER,password=NASUSERP* ASSWORD,rw 0 0

Once you have added those lines, press the Ctrl + X buttons simultaneously and when prompted type y to accept the changes and write them.

Now to mount using your fstab settings, type:
mount -a

Hopefully it all mounts withou problems. If not, change all instances of cifs to smbfs and try again.

I followed this to a T, but cannot get it to work on my laptop, the desktop system works fine. I have the same stuff installed on both systems.

I get this error is I do a sudo mount -a

wrong fs type, bad option, bad superblock on \\192.168.1.104,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I have no idea why this will not work on the laptop. I can access the nas drives by connecting to server, but not this way.

---

### Post by jetsam on 2008-05-20
That error message happens when you don't have the smbfs package installed.

```
sudo apt-get install smbfs
```
...should get you past it.

---

### Post by hvacr on 2008-05-20
Thats the strange thing, it is installed on my laptop, but not on my desktop system. Not sure why it works on my desktop and not the laptop.

---

### Post by jetsam on 2008-05-20
Can you post the output of 
```
dpkg --list smbfs
```
Also, make the mount fail with **sudo mount -a** and post the output of:
```
dmesg | tail
```
It might also be useful to see your fstab file, but be sure to x out your username/password if you post it.

---

### Post by hvacr on 2008-05-24
Thanks for the help. I managed to get things to work, but only if I use sudo mount -a 
The nas drives show up then. I noticed while re booting one time that I was getting a mount error 113, which is destination unreachable. I believe this is because my laptop is wireless, and the mount is happening before the network connection is made. Is there a way to get the network to connect before the mount when booting.

---

### Post by jetsam on 2008-05-24
Hmmm...

Does it work if you add **mount -a** to /etc/rc.local?  After the comments, the script should read:
```
mount -a
exit 0
```

This idea was inspired by this thread, which has some more complex ideas on a similar problem:
[http://ubuntuforums.org/showthread.php?t=788146&highlight=mount+error+113+fstab]("http://ubuntuforums.org/showthread.php?t=788146&highlight=mount+error+113+fstab")

Changing rc.local to retry the mount is probably an easier solution then messing with the normal boot order, which is confusing (to me, anyway;)) and has potential pitfalls.

---

### Post by hvacr on 2008-05-24
Seems I had to use a combination of _netdev and putting mount -a in the rc.local file. I still see the error 113 when I shut down, but I can live with that. Seems like my wifi card is the last thing to boot.

Thanks for all your help on this one.

Seems I spoke to soon, tried this morning and still not working. Testing something I found about crontabs, but that does not seeem to want to work. Damn Linux can be stubborn at times.

---

### Post by jetsam on 2008-05-25
> Damn Linux can be stubborn at times. 

Yes...  yes, it can be.  It helps to get away from it for a while if you're doing this: ](*,)

The rc.local script should be running last in the init sequence.  But, I think what's happening is that your wireless is taking some time to negotiate so it still isn't necessarily ready when the **mount -a** gets run from rc.local.

Here's a possible, albeit hackish solution:

Make a file called **/usr/local/bin/delaymount** (You can do this with **gksu gedit /usr/local/bin/delaymount**).

Put this in it:
```
#!/bin/bash

sleep 10
mount -a
```

Change the file's ownership and permissions to root and executable:

```
sudo chown root:root /usr/local/bin/delaymount
```
```
sudo chmod 755 /usr/local/bin/delaymount
```

Then change your **/etc/rc.local** file to read like so after the comments:

```
/usr/local/bin/delaymount **&**
exit 0
```

That & is important to put the mount delay into the background so you don't hang your boot process.  You can experiment with the value of sleep in /usr/local/bin/delaymount.  It's set above to 10 seconds.  You might be able to shorten it, or you might need to lengthen it.  

And here's a solution to the shutdown problem:
[http://ubuntuforums.org/showpost.php?p=4913141&postcount=53]("http://ubuntuforums.org/showpost.php?p=4913141&postcount=53")

Hope that helps.  It's tough for me to test because I don't have the same problem.

---

### Post by hvacr on 2008-05-26
That worked. Hard to believe that everything else I tried failed, even crontab. I can set the sleep time to 0, and it still works. I use wicd for my wireless connection, not sure if that is the sore spot. 

Thanks for all your help.

---

### Post by jetsam on 2008-05-26
You're welcome.  Glad you got it working!

> I can set the sleep time to 0, and it still works.

lol.  Go figure.  I'm sure there's a reasonable explanation for that, but I haven't got a clue what it is.  :)

---

### Post by safinr on 2011-09-12
I tried all the things that were mentioned in the original post. I ended up getting it to mount with smbfs command line. After that I created an executable shell script file that I placed on my desktop that will connect to the NAS drive. 
If someone wants to try my solution, it may be simpler than the one given before.

Go to text editor (gedit will do)
Create a new file with the following text in it ```
#!/bin/sh
sudo mount -t smbfs '//192.168.1.980/NAMEOFDISK' /mnt/NAS -o rw,username=USERNAME,password=PASSWORD
```
Then click save and place it wherever convenient (I put it on desktop) and save it with .sh extension
After that right click on the file and go to the properties > permissions and check allow executing file as program
Now whenever you want to mount just double click on the file and run it in terminal

I'm clearly new to Ubuntu and not versed in IT stuff, but thought I would share what worked for me. Maybe someone will use this

---

