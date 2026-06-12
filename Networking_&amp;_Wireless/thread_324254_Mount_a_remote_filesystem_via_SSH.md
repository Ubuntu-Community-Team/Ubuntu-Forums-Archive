---
title: "Mount a remote filesystem via SSH"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by djRobbieF on 2006-12-23
This tutorial directly applies to Ubuntu Edgy (my test system), but will work with most modern Linux builds.

SSH allows us to securely connect to the filesystem of a remote computer.  In the past, it was primarily used as a secure replacement for telnet - but by using this simple tutorial, you will be able to easily mount your Linux filesystem for local browsing, file access, etc. 


**_SERVER-SIDE_**

Install SSH Server:
```
sudo apt-get update
sudo apt-get install ssh
```
 
 

**_CLIENT SIDE_**

* Throughout this tutorial, always replace *username* with your SSH server's username, and *ip-address* with its IP Address or domain.

Test your connection to the SSH server:
```
ssh username@ip-address
```

Install FUSE (Filesystem in Userspace), which gives us sshfs access:
```
sudo apt-get update
sudo apt-get install sshfs
sudo modprobe fuse
```


Configure your user to be a member of the fuse group:
```
sudo adduser username fuse
sudo chown root:fuse /dev/fuse
sudo chmod +x /dev/fuse
```
 

Because a new user group has been created, we must now logout and back into the system.  A reboot is not required; but a simple logout.  Before you logout, be sure to bookmark this tutorial so you don't lose your place.

When you have logged back in, we need to create a mountpoint within your home folder.  It is important to note that the mountpoint must be within a folder owned by your user; so the safest place to put the mountpoint will be in ~.
 

Let's call our mountpoint server:
```
mkdir ~/server
```

 
Now, let's mount the remote filesystem just to test:
```
sshfs username@ip-address:/ ~/server
```

Notice that the sudo command was not used for the sshfs command.  This is very important.  Also, a trailing / after the : is required to specify we are mounting the root of the filesystem we're connecting to. If you wished, you could change that to a different folder; say /home/username.  But that would only be if you specifically wanted to grant access to only a specific folder within the SSH server's filesystem.

If all went well, you should be prompted for your SSH user's password.

Once mounted, **cd ~/server** and **ls** to see your remote system's filesystem.
 

Let's now move on to automating this process, so we do not need to manually mount, or enter a password in the future.  Please note, this is not safe in some environments.  Please assess your security prior to moving forward.  Automating this process will only work if you mounted /, as per my example.  If you chose to mount a different folder (ie. /home/username), this will not work.
 

_Examples of when this is safe:_
- A home or small office network, where you'd like to mount another computer's hard drive through a LAN.
- A private, password-protected computer that only you have access to, connecting through the Internet to the SSH server.
 

_Examples of when this is not safe:_
- A laptop computer connecting to a remote SSH server through the Internet.  If your laptop got lost or stolen, the person who obtains the notebook will have access to your root filesystem on the SSH server (based on the permissions of your users' account).
- A public computer where multiple users access the same login. 


In order to automate the connection process, we basically have to set up a "trust relationship" between the SSH server, and your computer.  This is done by generating an SSH key for your computer, and then setting up the SSH server to always trust that key.  Guard this key with your life  ;)
```
cd ~
ssh-keygen -t rsa
PRESS ENTER THREE TIMES
```


Now, the key has been created on the local system, but we need to set up the SSH server to trust this key:
```
cd ~/server/home/username
mkdir .ssh
chmod 700 .ssh
cat ~/.ssh/id_rsa.pub >> .ssh/authorized_keys
chmod 600 .ssh/authorized_keys
```


Now, unmount the SSH filesystem:
```
sudo umount ~/server
```
 

Let's test to make sure our "trust relationship" is working.  Connect to the SSH server using your username, and you should get in no problem, without having to enter a password:
```
ssh username:ip-address
```
 

If that worked, type exit to close the SSH connection.
 

Now, test mounting the filesystem using our original sshfs command:
```
sshfs username@ip-address:/ ~/server
```

That should now mount the filesystem without any prompts.


Now, to automate the mount every time you login to your system:
```
gnome-session-properties
```
Click on the Startup Programs tab.
Click Add.
Enter **sshfs username@ip-address:/ ~/server**  of course, replacing username and ip-address with your own.
Hit OK, and then Close.


That's all there is to it.  From now on, any time you login as this user, you will have access to the remote filesystem at ~/server.

Have fun, and happy Linux-ing!


Thanks to [[Linux Journal]("http://www.linuxjournal.com/node/8904/print")] and [[How-To Geek]("http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/")].

---

### Post by --chris-- on 2006-12-25
Very cool. However I seem to be getting an error message from client to server

fusermount: failed to access mountpoint /home/xxxxx/server: Permission denied


I'm wondering if I missed something server side to make set the permissions properly...? It should be noted that I'm using a slow system as a test server with Xubuntu installed so it may not have the necessary components. Didn't see any errors up to the very end though. 

Also, where did you learn this code? I'd love to become more fluid with my command line understanding. 

Thanks for your help!

---

### Post by jdusablon on 2006-12-29
FUSE with SSHFS is cool and everything, but not extremely useful for sharing files.

- You still need modules to mount SMB or FTP or anything remotely exotic.
- Transfer speed is brutal, as in slooow.
- Large file transfers (like a 690MB iso) won't happen. You can even break the host file system by using SSHFS and copying to a larger file to a compressed filesystem.
- VERY insecure. Using SSHFS as a permanent mount point is only appropriate in closed networks like a small office or a home LAN.

SSHFS is really only useful in situations where SSH is the ONLY connection method.

---

### Post by janfsd on 2007-01-02
> **jdusablon said:**
> FUSE with SSHFS is cool and everything, but not extremely useful for sharing files.

- You still need modules to mount SMB or FTP or anything remotely exotic.
- Transfer speed is brutal, as in slooow.
- Large file transfers (like a 690MB iso) won't happen. You can even break the host file system by using SSHFS and copying to a larger file to a compressed filesystem.
- VERY insecure. Using SSHFS as a permanent mount point is only appropriate in closed networks like a small office or a home LAN.

SSHFS is really only useful in situations where SSH is the ONLY connection method.


By slow transfer speed you mean that with just sshfs? or it should be the same of for instance gftp?

---

### Post by aurelieng on 2007-01-03
@jdusablon: my feeling is that it's probably more secure than FTP, NFS, etc.... as the communication between the client and the server uses SSH and is thus encrypted. So, why did you say :

> **jdusablon said:**
> - VERY insecure. Using SSHFS as a permanent mount point is only appropriate in closed networks like a small office or a home LAN.

Or maybe you're not talking about security but reliability ? (and in this case, I do agree)

---

### Post by showe1966 on 2007-01-03
Did you guys try rsync to transfer files etc.?
It's awesome and you can use it with ssh:-

rsync -v --rsh=ssh  /home/foo/foobar.txt root@123.456.798.123:/var/www 

I know it won't mount remote files systems, but it sure as hell allows you to transfer data freely from and to remote files systems in a secure way.

---

### Post by motin on 2007-01-24
A similar thread: [http://www.ubuntuforums.org/showthread.php?p=2057908](http://www.ubuntuforums.org/showthread.php?p=2057908)

---

