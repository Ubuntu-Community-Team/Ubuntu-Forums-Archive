---
title: "tar directly across ssh link"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by finite9 on 2007-07-26
I want to use tar to create a backup but create the file directly on an ssh link as I have limited space on the PC I am backing up.

I have tried with stuff like:

```
tar -cvf ssh://k2/mnt/1394disk/tarfile.tar
```

which doesn't work.  How can I accomplish this?  Must I pipe tars output to scp and if so how?

```
tar -cvf /home | scp andrew@k2:/mnt/1394disk/
```

???

---

### Post by heimo on 2007-07-26
Something like this should work:
```
tar czvf - /path/to/files | ssh user@host dd of=/path/to/backup.tar.gz
```

---

### Post by jfreak0126 on 2008-04-21
I was having a similar issue and didn't feel like taking the time to setup nfs. Here is what I did (sucessfully).

1.) I did a graphical ssh login to my desktop (192.168.0.106) from my laptop. (Places --> Connect to Server... --> 'Server type' --> SSH, under 'Server' username@ip address --> click 'Connect')

2.) Afterwards, I stumbled across a hidden directory '.gvfs' in my laptops 'home' folder and mounted within it was none other than 'sftp on 192.168.0.106'.

3.) I then used this syntax in a terminal to copy pictures from my desktop to my laptop:

 tar -cvf steven.laptop.backup.tar /home/steven/.gvfs/sftp\ on\ 192.168.0.106/home/steven/Pictures/4-13-07/

(i just used the TAB button to autocomplete the 'sftp on 192.168.0.106' part in the terminal.)

My result was a nice tidy .tar archive of the folder '4-13-07' on my laptop.

Simplified Syntax:

tar -cvf 'desired output filename' /home/username/.gvfs/sftp on ip address/desired directory to archive

---

### Post by jfreak0126 on 2008-04-21
If for whatever reason you do not find a mounted sftp connection in the .gvfs folder here is what to do to get one.

1.) sudo apt-get install sshfs

2.) make a directory you want to mount in

3.) sudo adduser username fuse

RESTART COMPUTER

4.) sshfs ip.address:/directory you want to mount /full path to directory you created

My Example:

sshfs 192.168.0.102:/home /home/steven/sftp

Note:

You may have to repeat step 4 each time you restart your computer.

---

### Post by scorp123 on 2008-04-21
> **finite9 said:**
>  I have tried with stuff like:
```
tar -cvf ssh://k2/mnt/1394disk/tarfile.tar
``` 

which doesn't work.  How can I accomplish this?  Must I pipe tars output to scp and if so how? 

```
tar -cvf /home | scp andrew@k2:/mnt/1394disk/
```  You pipe through ssh ... not scp.

The thing here is you can decide what you want to do: Do you want the machine that is in need of having stuff tar'ed to write to the remote machine where the backup will end up on or do you want the machine where the backup will be stored on to login into the machine in need of a backup and grab stuff from there ... ?

Both ways are possible. Let me show you. To make things easier I will call the machine where the backup will end up on "server" (because it is hosting backup files it technically is a "backup server", OK?) and the machine in need of backup the "client".

_Example: _

The "server" grabs the files off the "client" via ssh ... We do that using the "blowfish" crypto algorithm which should work faster and help us keep the time this might take to a minimum. ```
ssh -c blowfish remoteuser@my.client.that.needs.a.backup "tar cvpz  /path/to/backup"  > ./remoteclient-backup.tar.gz

``` What happens here is that you login into the other machine via ssh and you remotely launch "tar" ... but you leave the "-f" parameter away. With this "tar" will stream back its data through the ssh connection to its origin, where we intercept the data via the ">" pipe and push it into a tar.gz file (which is on the server-side!)

The opposite way:

The "client" initiates the connection and writes its stuff remotely onto the "server":
```
tar -czpv /path/to/stuff/that/we/backup | ssh -c blowfish user@backup.server "dd of=/path/to/where/my/backup/goes/on/the/server/backup.tar.gz"

``` Here you again run "tar" without the "-f" parameter. Having not defined a file "tar" should store its stuff into it would now print out everything onto your console. But we stop it from doing that by piping what would now fly over your screen into a "ssh" connection to your backup server. SSH is told to immediately open "dd" and thus intercept the still flowing data stream of "tar" and write that stuff into a *.tar.gz file (or else whatever we pipe through that connection would end up as command on the remotely opened ssh shell ... )

These methods work and should do what you want.

---

### Post by finite9 on 2008-05-05
thankyou for the explanation!  I have one more question:  I will initiate the ssh connection from the client, but the client is a hardy heron laptop and the server is a CentOS 5.1 laptop.  Do I need to have tar on the CentOS server as well?  Does it matter if the version of tar on the server is different from that of the client?  I use features in tar that are only available in the latest versin of tar, and CentOS does not have this version in it's repositories.

I also have problems getting this command to log properly and use variables.  Here is the command I am trying to use, but it does not work with the variables, I have to hard code everything, and I cannot seem to get it to log the output with a >> redirector.  Do I need to pipe the redirector through ssh as well?:

```
tar -cvPf - --listed-incremental $SNARFILE /home | ssh k2 "(dd of=/mnt/mybook320/backups/$LVL-$STAMP.tar >> ${LOGDIR}/${LVL}-${STAMP}.log
```

---

