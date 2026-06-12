---
title: "[SOLVED] Need to access files on computer blindly!  Important!"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by helixed on 2008-03-31
Hello everybody,

I woke up this morning and turned on my laptop, and instead of seeing a bios screen like I'm used to I only saw a blank white screen.  As far as I can tell the rest of my laptop is running fine except for the graphics card.  I'm going to take the laptop in tomorrow to see if they can determine the problem for sure, but for now I need to access my music files on the laptop's hard drive.  I booted off of an Ubuntu live CD, and I'm able to see the computer in my router's page and ping the computer.  

I need some way of setting up a share and accessing the computer blindly.  If I could even set up a VNC connection automatically some how that would be okay.  Please respond because I need this by tomorrow.

Thanks for the help in advance,

Helixed

---

### Post by Eiríkr on 2008-03-31
The only way to access anything on your machine without using the monitor is to do it via a remote service like VNC or SSH.  If something like this is not already configured on your machine, you're screwed, so far as I know.  :shocked:  The next best option is to get your hard drive out of your laptop and simply plug it into another machine, though I have no idea how difficult that might be -- depends on your laptop make and model, and how your hard drive is plugged in there.

Good luck,

Eiríkr

---

### Post by jetsam on 2008-03-31
Have you tried plugging in an external monitor?  It does seem like it would be really nearly impossible to set up any type of sharing on the machine without being able to see the terminal.  

Unless anybody knows about a linux distro boot disk that comes by default with ssh or telnet enabled...

---

### Post by dasunst3r on 2008-03-31
If you have easy access to your computer's IP address, then you're saved.  Once your computer finishes booting up:
[list=1]
[*] Hit Ctrl+Alt+F1 to access the console.
[*] Type in your user name and password
[*] Type in *sudo apt-get install openssh-server*
[*] Hit Enter.
[*] After the hard drive finishes doing stuff, hit Enter again, just to make sure.
[/list]
Using a shell client on a computer you can see stuff for, log in.  Another idea is that you could get a USB-to-IDE/SATA adapter for your hard drive and work from there.

---

### Post by jetsam on 2008-03-31
:)  Yeah.  Oddly enough, that could work.

---

### Post by warp99 on 2008-03-31
If the external monitor option is turned on in your bios you should be able to connect a monitor and boot into recovery mode.

---

### Post by helixed on 2008-03-31
Thanks for the quick replies.  I can't connect an external monitor.  I tired, but that too didn't work, which makes me think it's the graphics card.  For some reason I can't seem to get into ubuntu.  I tried installing the ssh server using the ctrl+alt+F1 method, but it failed.  I think that's the best way to do it though.  Does anybody know of a livecd which has ssh-server auto-enabled?

Thanks,

Helixed

---

### Post by helixed on 2008-04-01
anybody?

---

### Post by jetsam on 2008-04-01
Seems like the force was not with you on this one...

Is it still an active problem, or did you get the laptop fixed?  

Damn small linux can be booted from the livecd with sshd enabled, but you need to type some stuff (boot options "dsl ssh secure", then new passwords), and then I got stuck on trying to mount my hard drive when I was messing with it.

---

### Post by helixed on 2008-04-01
The problem's still active.  I'll get it fixed, but I want to make sure I have my music off of there first.  I tried creating a custom live cd with openssh-server preinstalled, and it worked, but since I was running off of a live cd, there was no user account to access.  If nothing else, is there some way I can configure the live cd to allow a ssh connection without requiring a password?

Thanks for the help,

Helixed

---

### Post by jetsam on 2008-04-01
I'm not sure.  This is getting well out of the way of stuff I've done before.  I was wondering about customizing a live cd.  I guess you did something like the process here: [https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization").

I googled the default username for the live cd, and ran across a few threads that said it was username "ubuntu" and a blank password.  That might be worth a shot.  I'm not sure if ssh allows blank passwords or not.  

This same isssue is why I used the "secure" boot option with DSL.  It allows you to specify passwords for the root user and default "dsl" user.

---

### Post by jetsam on 2008-04-01
Right.  Sshd doesn't allow empty passwords by default.  If you can change /etc/ssh/sshd_config in your boot disk, you can set "PermitEmptyPasswords" to "yes".  This will allow you to ```
ssh ubuntu@<your_borked_laptops_ip>
```
and log in automatically with full sudo access.  You will then have the least secure laptop ever.

---

### Post by helixed on 2008-04-02
Yup, that's the exact guide I used.  I'll try another live cd with the sshd file shortly.  Do you know how I can mount, access, and copy those files?  I'm not experienced with using only command line to access a file system.  I could either copy it onto my external, which is ntfs, or straight over the ssh connection.  Or, if there's an easy way to enable VNC over command line, then I could actually see what I'm doing.

Thanks,

Helixed

---

### Post by ryanhaigh on 2008-04-02
When you boot into ubuntu with the ssh server working, do the ctrl-alt-F1 thing again (press enter a couple of times before hand) and use the command ```
passwd
``` to set a password for the user ubuntu.
[LIST]
[*]Type passwd
[*]Hit enter
[*]Enter a password (not too short or simple)
[*]Press enter
[*]Repeat the password
[*]Press enter
[/LIST]

Your password should now be set and you should be able to login using that through ssh. Once logged in you will need to mount the drives using 
```
sudo mount /dev/sd* /mnt #where sd** denotes the drive and partition 
```
You could then use winSCP to copy the files over the network using the ssh server.

Just a note, I think you would find it easier to boot your installed ubuntu system, install the ssh server using as mentioned above and then connecting using your username, that way you know all partitions are mounted and you dont need to worry about that step.

note: to confirm that ssh server installed you might want to do something like
```
sudo apt-get install openssh-server && espeak "ssh installed"
``` this assumes that audio is working on your install and will make the computer say ssh installed.

---

### Post by helixed on 2008-04-02
Okay, SSH works!  I made a custom Ubuntu distro, and I changed the config file, and now it works!

Okay, so on to a new set of problems.  I tried mounting the hard drive like ryanhaigh said, but instead of doing anything it just listed all of the parameters which could be used with the mount command.  Either I need some way of mounting the filesystems, or I need some way of enabling vnc through command line.  If I can do it through command line I can always make one more custom live cd.

Thanks for the help,

Helixed

---

### Post by ryanhaigh on 2008-04-02
tightvncserver - virtual network computing server software

although it may just be easier if you post the command you used to try to mount your filesystems and the output you got back.

---

### Post by Eiríkr on 2008-04-02
Once you've got ssh up and running, you should be able to just type [font=courier]sftp://IP.ADD.RE.SS[/font] into Nautilus or Konqueror, and Bob's your uncle, you've got the filesystem right there without having to go through the CLI.  

Cheers,

Eiríkr

---

### Post by helixed on 2008-04-02
@ ryanhaigh

Here's what I typed and the output:

helixed@helixed-desktop:~$ ssh ubuntu@192.168.1.129 sudo mount /dev/sd* /mnt
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

@ Eiríkr

I tried this command, and it worked, but it only allowed access to the live cd's filesystem, and since the hard drive wasn't mounted, I couldn't get anything off of it.

Thanks for the replies,

Helixed

---

### Post by Whiffle on 2008-04-02
Should be able to do this:
 ssh ubuntu@192.168.1.129 
ls /dev/sd*
mkdir /mnt/disk
mount /dev/sda1 /mnt/disk

(where sda is the drive you're trying to get to)

---

### Post by helixed on 2008-04-02
Awesome, that did the trick.  The directory is now mounted and I can see the contents of my home folder!  There's only one problem left:  The ftp won't allow me to copy anything outside of the ubuntu user home folder.  Any suggestions?

Thanks,

Helixed

---

### Post by Eiríkr on 2008-04-02
> **helixed said:**
> I tried this command, and it worked, but it only allowed access to the live cd's filesystem, and since the hard drive wasn't mounted, I couldn't get anything off of it.

Interesting, I thought the live CD mounted the hard drive (if there is one) as part of bootup.  I don't suppose you could ssh in via a terminal, mount the hard drive, then use sftp via the GUI?  I've not tried what you're doing, but in a usual ssh / sftp setup, you get access to the whole drive, not just the user's home directory.

Good luck,

Eiríkr

---

### Post by Whiffle on 2008-04-02
try doing sftp://ubuntu@192.168.1.129  in the address bar of nautilus or konqueror, you should be able to get to any file that wya.

---

### Post by helixed on 2008-04-02
Awesome, I figured it out!  I established a ssh connection from my desktop to my laptop and then ran sudo scp /mnt/disk/home/ helixed@myipaddress:/home/helixed/backup.  It worked perfectly, and all of my files are copying right now.  Thanks for all of the help everybody.

Helixed

---

### Post by Eiríkr on 2008-04-02
Great news, Helixed!  :D  If that does it for you in this thread, please marked it as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Thanks,

Eiríkr

---

### Post by jetsam on 2008-04-02
=D>Well done!  That was a complicated one.

When you shut down, be sure to shut down properly now you've got drives mounted.  From the ssh client, you can do:

```
sudo shutdown -h now
```

You should redistribute your distro and call it MeOwnBunto, or maybe OwnMeBuntu...

OwnMeOwnBuntu?

---

### Post by helixed on 2008-04-02
You know, that is a good point.  It would be kind of nice to have a distro specifiically designed to fix problems like this.  It could have vnc and ssh auto-enabled, and it could have all of the diagnostic tools right there.  I don't know how many other people have had this problem, but if something like that were out there I could have saved a couple of days on this.

Helixed

---

