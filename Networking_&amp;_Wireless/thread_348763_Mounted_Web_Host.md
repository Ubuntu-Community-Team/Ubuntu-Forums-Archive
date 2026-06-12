---
title: "Mounted Web Host"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by dmce on 2007-01-29
Hi

I can mount my web host using sshfs. I also have samba sharing some folders to a few windows  PCs. I though i might be able to share my mounted web share using samba, but windows just doesnt like it if i try to access that share.

Is this something that can actually be done?

---

### Post by dmce on 2007-01-30
bump

---

### Post by kebes on 2007-01-30
Can you explain in a bit more detail what you've already tried? Please specify the commands you used, and what they returned. I'm guessing you tried something like:

mounted your webhost using ssh to a location like:
/media/stuff/webhost/

Then you create a SAMBA share to the location:
/media/stuff/

then on Windows you go into the samba share... you see a directory called "webhost" and try to enter it. But this doesn't work? What error messages do you get?




Is the situation any different if you use symlinks instead? Like say you mount webhost to:
/media/webhost/

And then create a samba share at:
/media/stuff/

And then go make a symlink:
ln -s /media/webhost/ /media/stuff/webthings

Then when you check on the Windows machine, do you see the folder? Can you access it?



In all likelihood, the problem is a permission issue. The user that samba runs as is going to need access to the webhost folder. So make sure the webhost folder is mounted with the permissions needed. As a test, try mounting it as "world-readable" and see if you can at least browse it through samba on Windows.


I've created samba sharing which contained symlinks, and on windows machines that browse the share, they see the symlinks as normal folders. So, I think it can be done in your case too.

---

### Post by dmce on 2007-01-31
Hi

Thanks for the repsonse. As per your first detail, this is pretty much the way i created it.

Using sshfs, i mounted my web host to /media/remote/
I then had a specific entry in samba.conf for that location, for the user dmce. The one thing i did notice is that once mounted, the owner/permissions on these files and the folder remote related to user 32467.

I dont know how to make world readable.

I can see the folder on the network, but if i actually try to go into it i get no errors, windows just freezes up and i cant do much. Im currently sitting with a crashed explorer, but putty and firefox are still going :)

If i try with symlinks its pretty much the same situation.

I mounted to /media/remote, created a symlink (ln -s /media/remote/ /media/web/share/) and added an entry for that location (media/web/share/) in samba.conf again for user dmce, but the specific permissions for the actual files relate to 32467 so i would agree it seems like permissions. The folders, such as remote are owned by dmce until the remote host is mounted.

---

### Post by kebes on 2007-01-31
The permission problem could be either at the directory level (samba can't read the directory, so nothing logged into samba can, either...) or at the samba level (samba isn't giving out permissions...).

1. First off, I'm assuming samba is running as root, right? (It should be, unless you manually started it without using "sudo"... but if you did a normal samba install then it should be running as root.)

2. Can you properly use samba to share other directories? (Ones not mounted via sshfs or whatever...) If you can, then I guess samba is working...

3. Check the permissions on the directory you mounted sshfs to. When you use sshfs, you probably have options related to what permissions will be put on the newly mounted share. Once the ssh is mounted, check what the permissions are using:
cd /media/
ls -laF 

You'll see something like:
drwx------  9 user group 4096 2007-01-30 19:28 remote/

Make sure that "user" is the correct user and that the permission string at the start is "okay." You can use the command "chown" to change the user and "chmod" to change permissions, but doing so may or may not help, since the permission problem may be at the level of sshfs. Go into the folder and check again:
cd remote
ls -laF

Are those files owned by a different user or group? What are those permissions?

4. I think in the "smb.conf" file, there is a way to control the permissions and access for all the samba users. Take a look at the sama documentation (run "man smb.conf").

---

### Post by dmce on 2007-02-01
1. Samba runs as a daemon at boot, but if manually started i use (sudo /etc/rc.d/samba start)

2. I have another "normal" directory that is shared ok

3. After i have mounted the web share an example of permissions is:
[IMG]http://rockinchair.co.uk/simplegal/galleries/Misc/share.jpg[/IMG]
chown and chmod even when used with sudo dont have permission

4. Im unsure about the fact the user is 32467 on the mounted folders

---

### Post by kebes on 2007-02-01
I think you're right, the fact that those dirs are owned by user "32467" is likely the problem. Samba probably doesn't have authority to read them... but you can't use chown/chmod because they are under the control of sshfs.



1. Try changing the way you mount with sshfs. When you run the sshfs-mount command, do you run it as a normal user, or as root (using "sudo")? If you're running it as root, perhaps it would be better to run it as a normal user. Instructions for allowing a normal user to run sshfs can be found here:
[http://myy.helia.fi/~karte/mount_sshfs.html](http://myy.helia.fi/~karte/mount_sshfs.html)
(search for phrase "It is also possible to mount as a user.")

Alternately, perhaps change the way you use sshfs. On the [manual page]("http://huygens.ca.infn.it/cgi-bin/man/man2html?sshfs+1"), it lists options such as "allow_other" which might be what you need so that other users can access the mounted ressource.



2. Alternately, try changing the user for samba. On your machine, if you log in as the username that samba is using, do you have access to those directories? If not, that's a problem! You may need to add that user to a group that has access, or login using a samba user account that has more access. (Check the documentation for samba... also there is a web-based administration program called 'webmin' that can make it easier to configure samba.)


These are just some random ideas... I'm not sure if they'll help. Good luck.

---

### Post by jwynia on 2007-02-07
I ran across this thread trying to solve the same problem. I could use Samba to access the local files, but not the sshfs-mounted ones. What I needed to do was:

create the file:

/etc/fuse.conf

put this line in it:

user_allow_other

change my command to mount the remote directory to:

sshfs [email]user@example.com@example.com[/email]:/var/www/html /mnt/remote -o allow_other

2 notes on that above line. 1 is that my username on this server *is* my email address, so I need both "@" signs. 2nd is the "-o allow_other" goes on the end.

Then, on the Samba side, here's what my config (/etc/samba/smb.conf) for that directory looks like:

[remote]
  comment = sshfs mounted directory
  path = /mnt/remote/
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

If the sshfs filesystem isn't mounted, you just get an empty directory. Otherwise, it's working for me at this point.

---

### Post by dmce on 2007-02-10
Thanks for the help guys. Got it working using allow_other. The main difference was in my smb.conf.

To get it working all i used was
[remote]
   comment = remote host. sshfs shared
   path = /media/remote
   public = yes
   writable = yes
   only guest = yes
   printable = no

@jwynia: What do you do with regards to unmouting after you have edited? Do you make a point of issuing fusermount -u on the mount?

---

