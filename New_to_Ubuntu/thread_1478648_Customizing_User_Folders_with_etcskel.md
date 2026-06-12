---
title: "Customizing User Folders with /etc/skel ?"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2010-05-09
I have an eeepc 901 which comes with a tiny 4GB SSD usually used for my system drive as it is the faster SSD in the system and a 16GB SSD for media files and downloads, and such which is slower and so is *not* recommended for use as /home.

Lately I've been partitioning my system as such:

4GB SSD
/---/4GBs
---/efi 8mbs

16GB
/----swap 1GB
/-------/usr/share 4GB
/---------data 11GB

What I'd like to do is map all the User Folders (Downloads, Public, Documents, Music, etc) for all users created to my /data transparently and without resorting to symbolic links.  IS this possible, perhaps with /etc/skel?

--bornagainpenguin

---

### Post by gzarkadas on 2010-05-10
/etc/skel is for new accounts only and it just lays a predefined set of files and directories. Since you want to access directories in another partition you are confined to symbolic links only (hard links do not work across partitions, neither can point to directories).

But if your users' number is small, you can make /data an extended partition, slice it to the desired number of "directories" and mount them in your /etc/fstab as subdirectories of your users' home folders. 

To avoid over-slicing, you may create a top-level data directory in each user's folder and put `Documents', `Images', etc inside it. 

Or, if there are just two users (a common case) you can go for the full number of 2 x 7 (?) logical volumes, but use the first 7 for one user and last 7 for the other and arrange the order of directories such that the ones that are more probable to get filled are adjacent to ones that are more probable to have free space. That way you will be able to resize partitions with gparted when the need arises.

---

### Post by bornagainpenguin on 2010-05-10
Thanks for the reply!

What you wrote sounds good, how do I do all this without screwing up permissions?  Heck, how do I do any of this at all!?  So far I've been just opening nautilus as sudo and setting permissions on the /data partition to my username as full read and write, then making symbolic links from there to my /home.  Sooner or later that is going to catch up to me though and I have no way of knowing if any of the various issues I have are related to this or not.  :(

It seems to me that a cleaner way would be to somehow set up the /data partition and then create links to the User Folders (Music, Videos, Public, etc) in /etc/skel allowing each new account to store media on /data and reserving the /home on the 4GB SSD for configuration files like .mozilla and so on.  Trying to simply mount the 16GB SSD as /home is out of the question due to the terrible slow down it causes thanks to the cheaper SSD used.

--bornagainpenguin

---

### Post by gzarkadas on 2010-05-11
The problem is that for each user you add you will have to create a directory tree in the data partition, which will depend on user's login name. So you need a script that will take the new user's login name as argument, will create the directory tree and will symlink to the directories inside user home folder. The script below (licenced under [GNU GPL v3]("http://www.gnu.org/licenses/gpl.html") or any later version) does this. 

The directories will be created with the default root's umask; if you want to use other set of permissions add an option -m MODE (set MODE to the desired permissions, such as 700, 750, etc) in each `mkdir' invocation. 

Name the script setuser.dirs or whatever you want it, make it executable and run it (as root with sudo) **right after** creating a new user account.

Script setuser.dirs :
usage:
    setuser.dirs LOGIN
LOGIN is the login name of the newly created account (ie the account must have already been created).

script contents:
```

#!/bin/bash

# $1 = user_login, $2 = directory (relative to user_login)
function prepare_user_dir()
{
    [ $# -eq 2 ] || return 1
    mkdir /mnt/data/${1}/${2}
    pushd /home/${1}
    ln --symbolic  /mnt/data/${1}/${2}  ${2}
    popd
}

mkdir /mnt/data/${1}

prepare_user_dir  ${1}  Documents
prepare_user_dir  ${1}  Music
prepare_user_dir  ${1}  Images
prepare_user_dir  ${1}  Videos
prepare_user_dir  ${1}  Public

chown -R ${1}:${1} /mnt/data/${1}

```In order for the script to work, you must mount your `data' partition in /mnt/data. Make as root a `data' directory inside /mnt and add this line to your /etc/fstab:

```

/dev/sdb3     /mnt/data    ext3     defaults,relatime,errors=remount-ro   0  2

```if your `data' partition is not /dev/sdb3, then change this item accordingly. You can also change the directories names to your prefered locale ones, as well as add/remove directories to whatever suits you.

---

### Post by bornagainpenguin on 2010-05-11
> **gzarkadas said:**
> The problem is that for each user you add you will have to create a directory tree in the data partition, which will depend on user's login name. So you need a script that will take the new user's login name as argument, will create the directory tree and will symlink to the directories inside user home folder.

Is there any way to define things for all users and simply have directories and links mapped automatically as users are created?

> **gzarkadas said:**
> The script below (licenced under [GNU GPL v3]("http://www.gnu.org/licenses/gpl.html") or any later version) does this. 

The directories will be created with the default root's umask; if you want to use other set of permissions add an option -m MODE (set MODE to the desired permissions, such as 700, 750, etc) in each `mkdir' invocation. 

Name the script setuser.dirs or whatever you want it, make it executable and run it (as root with sudo) **right after** creating a new user account.

Script setuser.dirs :
usage:
    setuser.dirs LOGIN
LOGIN is the login name of the newly created account (ie the account must have already been created).

script contents:
```

#!/bin/bash

# $1 = user_login, $2 = directory (relative to user_login)
function prepare_user_dir()
{
    [ $# -eq 2 ] || return 1
    mkdir /mnt/data/${1}/${2}
    pushd /home/${1}
    ln --symbolic  /mnt/data/${1}/${2}  ${2}
    popd
}

mkdir /mnt/data/${1}

prepare_user_dir  ${1}  Documents
prepare_user_dir  ${1}  Music
prepare_user_dir  ${1}  Images
prepare_user_dir  ${1}  Videos
prepare_user_dir  ${1}  Public

chown -R ${1}:${1} /mnt/data/${1}

```In order for the script to work, you must mount your `data' partition in /mnt/data. Make as root a `data' directory inside /mnt and add this line to your /etc/fstab:

```

/dev/sdb3     /mnt/data    ext3     defaults,relatime,errors=remount-ro   0  2

```if your `data' partition is not /dev/sdb3, then change this item accordingly. You can also change the directories names to your prefered locale ones, as well as add/remove directories to whatever suits you.
Thank you for the script.  I'll be looking at it to see if I can figure it out, but I admit I don't know much (anything) about bash scripts.

--bornagainpenguin

---

### Post by gzarkadas on 2010-05-12
> **bornagainpenguin said:**
> Is there any way to define things for all users and simply have directories and links mapped automatically as users are created?

This can only work with shared directories, where all users can read/write everything in them; if you want to have separate folders for each user then you must create them on the fly when the user's login name becomes available.

A way to automate this without having to remember to run a script such as the one I posted after each user creation is to append these steps to the previous post's instructions:

1. Put the `setuser.dirs' script in `/usr/local/bin' and make it executable by all users 
```

sudo cp <your-local-copy-of-the-script> /usr/local/bin/setuser.dirs
sudo chmod 755 /usr/local/bin/setuser.dirs

```2. Add an empty file with name `.first-login' inside `/etc/skel'
```

sudo touch /etc/skel/.first-login
sudo chmod 644 /etc/skel/.first-login

```3. Modify the file `.bashrc' inside `/etc/skel'; use your editor of choice to add the following lines at the end of it:
```

# create user directories at first login
if [ -f ${HOME}/.first-login ] ; then
    /usr/local/bin/setusers.dir ${USER}
    rm ${HOME}/.first-login
fi

```

---

### Post by johnh10000 on 2010-10-17
This seems similar to what I want to do.  I have a small user base (4) at the moment!
In /etc/skel/ I have added Public /Public/ftp /Public/incomming

What I'd like is to is this, for existing users and users I may add in the future.

I run an sftp/ftp server, in these I have incomming (I know its spelt wrong)
in which there are folders jono johnh etc

I need incomming "mounted" in home/$user/Public/incomming and only $user incomming folder write-able by the owner.

At present I manually write the xtra bits to fstab.
```

/home/incomming /home/ftp/incomming none rw,bind 0 0
/home/ftp /home/jono/Public/ftp none rw,bind 0 0
/home/incomming /home/jono/Public/incomming none rw,bind 0 0
/home/incomming /home/johnh/incomming none rw,bind 0 0
/home/ftp/ /home/johnh/ftp none rw,bind 0 0
/home/incomming /home/jackief/incomming none rw,bind 0 0
/home/ftp/ /home/jackief/ftp none rw,bind 0 0
/home/ftp/ /home/annon none rw,bind 0 0
/home/ftp /home/jeffw/documents/ftp none rw,bind 0 0
/home/incomming /home/jeffw/documents/incomming none rw,bind 0 0


```

any clues as to how to automate this?

---

### Post by kernst on 2010-10-22
> **gzarkadas said:**
> A way to automate this without having to remember to run a script such as the one I posted after each user creation is to append these steps to the previous post's instructions:

1. Put the `setuser.dirs' script in `/usr/local/bin' and make it executable by all users 
```

sudo cp <your-local-copy-of-the-script> /usr/local/bin/setuser.dirs
sudo chmod 755 /usr/local/bin/setuser.dirs

```

I believe that /usr/local/bin/setuser.dirs would need to be a setuid root binary in order for this to work in the login scripts, otherwise any "chown"s or "chmod"s on the directories will likely fail.

There's this [nice little thread on Server Fault]("http://serverfault.com/questions/75620/ubuntu-let-a-user-run-a-script-with-root-permissions") ([http://serverfault.com/questions/75620/ubuntu-let-a-user-run-a-script-with-root-permissions](http://serverfault.com/questions/75620/ubuntu-let-a-user-run-a-script-with-root-permissions)) that covers most of the questions you'd have if you'd never heard of "setuid" programs. 

Basically what "setuid root" means in a nutshell: an executable (e.g., set a+x <filename>) binary that also has the "setuid" permissions bit set on it (e.g., with set u+s <filename>), which allows it to run with the permissions of the file's owner. In this case, root, the superuser. This only works for binaries--compiled programs--not scripts, as explained in the Server Fault link above.

Setuid programs are most always considered a security risk. Most sysadmins will recoil in horror upon hearing the phrase "setuid root," but its utility in some tightly controlled circumstances is undeniable, especially if "sudo" isn't an option. Any further discussion here is beyond the scope, so [http://lmgtfy.com/?q=why+are+setuid+scripts+bad](http://lmgtfy.com/?q=why+are+setuid+scripts+bad)

Nowadays, with "sudo" being a given on any Ubuntu system, you can probably accomplish the same with an entry in /etc/sudoers such as:

```
%cdrom    ALL = NOPASSWD: /usr/local/bin/setuser.dirs [\:alnum\:]*
# backslashes in "[\:alnum\:]" are intentional and required, since
# the colon (':') has special meaning in sudoers file
# see: man sudoers or http://www.sudo.ws/sudo/sudoers.man.html
```

What this means in English is: allow all users in the group "cdrom" ("%cdrom") on all machines ("ALL =") to run the command /usr/local/bin/setuser.dirs followed by one argument consisting of zero or more alphanumeric characters ("[\:alnum\:]*", i.e., a username), WITHOUT requiring a password ("NOPASSWD: ").

I used the group "cdrom" because most Linux distros do not add new users to the "users" group (although that would seem to make sense), but new users **do** get added to "cdrom" by default. (If you wanted to change this, modify the EXTRA_GROUPS option in /etc/adduser.conf and also set ADD_EXTRA_GROUPS=1 in that file.)

**NOTE: I have not tested any of this.**

Very useful, thread. Hope my contribution helps *someone*. Not as straightforward a solution as you'd imagined, eh, bornagain?

---

### Post by kernst on 2010-10-22
> **gzarkadas said:**
> This can only work with shared directories, where all users can read/write everything in them

Or perhaps *that's* how you intended to get around the chown/chmod problem. It would work, but chmod'ing folders to wide-open "777" (ugo+rwx) is probably a bad practice to default to when you're having problems with permissions. On your home PC, behind a firewall--meh, maybe no big deal. But just sayin'...

If anyone is serious about cobbling together a working solution from the suggestions in this thread, I'd recommend looking into "sudo" with the "NOPASSWD:" option, rather than fiddling with permissions on the theoretical /mnt/data partition (to get around the need for superuser privileges to set directory owners and permissions).

---

### Post by gzarkadas on 2010-10-24
There is no need for a setuid script, not even for changing /etc/sudoers (which is indeed a better approach); /mnt/data permissions can simply be set as drxwrwxrwt (ie set the sticky bit), just like those of /tmp. Then each user can create a top-level directory within /mnt/data and no other users can fiddle with its contents. 

Also since the script is executed from within the user's startup command file, the `chown ...' line in the script is not needed; the user is already the owner.

---

### Post by gzarkadas on 2010-10-24
> **johnh10000 said:**
> This seems similar to what I want to do.  I have a small user base (4) at the moment!
In /etc/skel/ I have added Public /Public/ftp /Public/incomming

What I'd like is to is this, for existing users and users I may add in the future.

I run an sftp/ftp server, in these I have incomming (I know its spelt wrong)
in which there are folders jono johnh etc

I need incomming "mounted" in home/$user/Public/incomming and only $user incomming folder write-able by the owner.

At present I manually write the xtra bits to fstab.
```

/home/incomming /home/ftp/incomming none rw,bind 0 0
/home/ftp /home/jono/Public/ftp none rw,bind 0 0
/home/incomming /home/jono/Public/incomming none rw,bind 0 0
/home/incomming /home/johnh/incomming none rw,bind 0 0
/home/ftp/ /home/johnh/ftp none rw,bind 0 0
/home/incomming /home/jackief/incomming none rw,bind 0 0
/home/ftp/ /home/jackief/ftp none rw,bind 0 0
/home/ftp/ /home/annon none rw,bind 0 0
/home/ftp /home/jeffw/documents/ftp none rw,bind 0 0
/home/incomming /home/jeffw/documents/incomming none rw,bind 0 0


```any clues as to how to automate this?

I haven't set up an ftp server yet, so I don't know whether there are specific needs regarding how you set permissions to directories underneath the ftp server's tree. If there aren't any, then simply setting permissions as needed for your users' directories inside /home/incomming/ and putting something like the following inside the /etc/skel/.bashrc

```

if [ ! -e ${HOME}/Public/ftp ] ; then
    ln -s /home/ftp/ ${HOME}/Public/ftp
fi
if [ ! -e ${HOME}/Public/incomming ] ; then
    ln -s /home/incomming/${USER} ${HOME}/Public/incomming
fi

```would do the trick. You still need a way to make the folders inside /home/incomming, but this can be wrapped around the `adduser' command (for example by creating a wrapper script that first makes the folders, then adds the user) so that they can be executed as part of the account creation process.

---

### Post by kernst on 2010-11-05
> **gzarkadas said:**
> There is no need for a setuid script, not even for changing /etc/sudoers (which is indeed a better approach); /mnt/data permissions can simply be set as drxwrwxrwt (ie set the sticky bit)

Ah, yesh, yesh, the sticky bit. You're right: much less fuss that way.

I rescind my previous remarks about sudo and the "NOPASSWD:" option. Though I do hope that post was at least educational for *some*one. ;)

---

