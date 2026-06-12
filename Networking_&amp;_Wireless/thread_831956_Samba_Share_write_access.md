---
title: "Samba Share write access"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by Hackit on 2008-06-17
Sorry for the double post, Just realized i should not have hijacked the other post.


> **dmizer said:**
> i've never been able to get a functioning printer share via samba.  just use the cups interface.  with that in mind, i would suggest a smb.conf like so:

```
[global]
    ; General server settings
    netbios name = uShotgun
    server string = %h server (Samba, Ubuntu)
    workgroup = FREYHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[[COLOR="Red"]Ubuntu_Machine_Share[/COLOR]]
    path = [COLOR="Red"]/local/path/to/shared/directory[/COLOR]
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
    force group = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
```
be sure to edit the red variables in the above smb.conf so it fits your specific environment.

then add your ubuntu user to the samba group with teh following commands:
```
sudo smbpasswd -L -a UBUNTU_USERNAME
sudo smbpasswd -L -e UBUNTU_USERNAME
```

restart samba:
```
sudo /etc/init.d/samba restart
```
and you should be ready to go.

if you want to share more than one directory, simply include a second entry like so:
```
[[COLOR="Red"]Share_1[/COLOR]]
    path = [COLOR="Red"]/local/path/to/first/shared/directory[/COLOR]
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
    force group = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]

[[COLOR="Red"]Share_2[/COLOR]]
    path = [COLOR="Red"]/local/path/to/second/shared/directory[/COLOR]
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
    force group = [COLOR="Red"]UBUNTU_USERNAME[/COLOR]
```

to share your printer via cups,
go to: system > config > printer > Server Settings, and put a checkmark next to "Share published printers on the network".

Hi Dmizer / all,

I followed your smb.conf file and the only thing i wanted to change was the guest access, Dont want anyone in the house to access the share.

I can mount and write to the folder with ubuntu, but on my vista 64bit machine i'm unable to write to the share it say's you do not have permission.

I can see everything on the drive but i need to be able to have write capability on vista.

Here's my smb.conf file.

[global]
	workgroup = mine
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	null passwords = Yes
	passdb backend = tdbsam
	username map = /etc/samba/smbusers
	syslog only = Yes
	announce version = 5.0
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = CUPS

[my Folder]
	path = /media/disk/my Folder
	force user = me
	force group = me
	read only = No
	create mask = 0755
mine@Ubuntu-Server:~$ 


thanks for any help.

just so you know media/kevs folder. has read write if i run fstab

---

### Post by Hackit on 2008-06-17
Bump

---

### Post by Hackit on 2008-06-17
Does any body have any ideas?

I had this working with ubuntu 32 bit edition (hardy).

For some reason it just stopped working so rather than spending the time to figure it out.

 I figured what a better time to reinstall and go to hardy 64 bit.

I have made sure the drive is mounted and the user has rw in fstab.

I dont want to give guest access, I want to have to log on with a password.

My login name and the user name are different.

So i used my login name for both of these entries.

    force user = UBUNTU_USERNAME
    force group = UBUNTU_USERNAME

Example user name is bill smith and my login name is cheese.
I used cheese for the above 2 fields.

Thanks again for any assistance.

---

### Post by dmizer on 2008-06-18
the problem with vista is probably vista rather than your ubuntu setup.  your smb.conf file does not have a netbios name (like the example does), and this could cause problems with vista accessing your share.

for more information on setting up user based samba shares, see the link in my sig labeled "best samba server howto".

in your smb.conf file, the "force user" and "force group" options must be your ubuntu userid, never anything else.  these options provide for the correct local permissions on your server and has nothing to do with who is allowed or not allowed to access the share.

---

### Post by Hackit on 2008-06-18
Thanks for the response : )

I just read your smb help in your sig, and i want to know does my vistz box have to have the same password and user name as the ubuntu box?

Time to add yourself as an samba user.

NOTE: You will be asked for a password - make sure you use the same as you use for login!

Code:

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!

NOTE: Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box just press enter when prompted to enter a password for the user account you're about to create!

---

### Post by dmizer on 2008-06-18
> **Hackit said:**
> Thanks for the response : )

I just read your smb help in your sig, and i want to know does my vistz box have to have the same password and user name as the ubuntu box?
no, in fact you're better off if they are different.  just use the directions below to add each windows user account onto your ubuntu machine.

```
sudo useradd -s /bin/true [COLOR="Red"]windowsuser[/COLOR]
sudo smbpasswd -L -a [COLOR="Red"]windowsuser[/COLOR]
sudo smbpasswd -L -e [COLOR="Red"]windowsuser[/COLOR]
```

just be sure to replace "[COLOR="Red"]windowsuser[/COLOR]" with the actual login for your vista box.

---

### Post by Hackit on 2008-06-19
> **dmizer said:**
> 
```
sudo useradd -s /bin/true [COLOR="Red"]windowsuser[/COLOR]
sudo smbpasswd -L -a [COLOR="Red"]windowsuser[/COLOR]
sudo smbpasswd -L -e [COLOR="Red"]windowsuser[/COLOR]
```


ok I just ctreated a new sam.conf file and followed your directions to add a windows user.

i just copied your smb.conf file and when i run 
sudo testparm

this is what i get:

Processing section "[my share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = mine
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	null passwords = Yes
	passdb backend = tdbsam
	username map = /etc/samba/smbusers
	syslog only = Yes
	announce version = 5.0
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = CUPS
	wins support = Yes

[my share]
	path = /media/disk/my share
	force user = hackitz
	force group = hackitz
	read only = No
	create mask = 0777
	directory mask = 0777
end


Ok it seems like some of the settings are not staying entered when i save my smb.conf file. like net bios.

also i do have a static ip address to my unbuntu box, acually all my computers have a static ip from my router.

I so wish samba was easier, Ha Ha Ha Ha

So i can see and browse my share with vist, but i'm unable to write it my share.

and of course I want to write to my share.

Thanks for the help so far.

---

### Post by dmizer on 2008-06-19
how are you editing smb.conf?

---

### Post by Hackit on 2008-06-19
gksudo gedit /etc/samba/smb.conf

---

### Post by dmizer on 2008-06-19
restart samba after each time you make a change:
```
sudo /etc/init.d/samba restart
```

---

### Post by Hackit on 2008-06-19
I actually stop it before i make changes then restart samba.

---

### Post by dmizer on 2008-06-20
if your changes are not getting applied, something fairly basic is amiss.

what's the output of:
```
ls /etc/samba
```

---

### Post by Hackit on 2008-06-20
> **dmizer said:**
> 

what's the output of:
```
ls /etc/samba
```

dhcp.conf  gdbcommands  smb.conf  smb.conf~  smb.conf_backup  smb.conf.ucf-old
user@Ubuntu-Server:~$

---

### Post by Hackit on 2008-06-21
bump

---

### Post by Hackit on 2008-06-22
bump

---

### Post by dmizer on 2008-06-23
i can only imagine a few situations where you would edit smb.conf and not have the changes appear.

1) you are not actually editing as root.
2) there was a typo in the directory/file name
3) not restarting samba after editing.
4) your login id does not have sudo ability.

if you're using gksudo gedit /etc/samba/smb.conf then you've eliminated potential problem number one.  you indicated that you stop samba when you edit, and restart it after you've made changes so that would eliminate potential problem 3.  if your user does not have sudo privileges, you should get an error when entering the command "gksudo". the only one i can't verify is a typo.

there are three locations for smb.conf:
/etc/samba/smb.conf <- this is the working smb.conf file
/usr/share/doc/smbldap-tools/examples/smb.conf <- this is an example
/usr/share/samba/smb.conf <- this is not used in peer to peer shares.

you can do a search in the command line (or in nautilus):
```
locate smb.conf
```
look at the output and see if you have one that doesn't match the above locations, and that may help you locate the mistake.

if you still cannot make changes to your smb.conf, i really don't know what to tell you, but i know that you've edited it successfully at least once.

---

### Post by Hackit on 2008-06-23
Thanks for all the input.

Ok I reinstalled hardy 64.

Belive it or not i am having the same problems.

when i update my smb.conf file not all the settings are saving.

Now the drive i want to share is on devb, it.s my second drive and if i click on properties of the drive it says the permissions can not be found.

But if i click on properties on the folder i want to share the permissions are OK and I can read write while logged into my account.

So I'm wondering if it's an issue with permissions of my drive.

Also when it did work on my first install of hardy 32 bit, i did not have an account on my box for the windows user. Only one account to log into my box. Do i need an account created for every user I want to sign on?

FYI, I want everyone to have to enter a password to login from the network.

Thanks Again for all the insight.

---

### Post by dmizer on 2008-06-23
> **Hackit said:**
> Thanks for all the input.

Ok I reinstalled hardy 64.

Belive it or not i am having the same problems.

when i update my smb.conf file not all the settings are saving.
this is your biggest problem.  you cannot solve anything else until you solve this.

try editing with a command line text editor instead of gui.  nano is a good tool for this:
```
sudo nano /etc/samba/smb.conf
```

---

### Post by Hackit on 2008-06-24
> **dmizer said:**
> 
```
sudo nano /etc/samba/smb.conf
```

Tried and same thing, when i run sudo testparm i'm missing some of my settings.

Funny thing is the settings always show up when I tryu to edit smb.conf.

Must be something when i save it.

I remeber someone telling me that i should hit the tab key to enter a new line rather then the space bar to have the entries indented. I wonder is this messing it up?

Just about to give up and start all over.

---

### Post by dmizer on 2008-06-25
i see.

testparm will not output the entire smb.conf file.

here's the output of my testparm:
```
[global]
        workgroup = SHINKANSEN
        security = SHARE
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
        guest ok = Yes

[share]
        path = /home/dmizer/smb-share/
        force user = dmizer
        force group = dmizer
        read only = No
        create mask = 0644
```
here's my /etc/samba/smb.conf file:
```
[global]
    ; General server settings
    netbios name = kodama
    workgroup = sinkansen
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_S
NDBUF=8192

    security = share
    name resolve order = hosts wins bcast

    syslog = 1
    syslog only = yes
    guest ok = yes

[share]
    path = /home/dmizer/smb-share/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = dmizer
    force group = dmizer
```

---

### Post by Hackit on 2008-06-25
With guest turned on do you still need to enter a password from a windows machine when you try to sign on for the first time?

I'm going to try youe smb file.

Again thanks for the help dmizer

---

### Post by Hackit on 2008-06-25
NOTE: Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box just press enter when prompted to enter a password for the user account you're about to create!

In the following example we will add an user called "mark" ...

Example:

Code:

sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark

The "-s /bin/true" in the first line prevents the users from being able to access the commandline of your linux box ("-s" stands for "shell"). I strongly advise you to follow this recommendation! Don't change that setting to a valid login-shell unless you really know what you are doing!

Repeat this step until you configured all user accounts!

Now that we configured samba and created the user accounts we are done with the Linux-part - there's one more thing to do in Windows.


Does this mean i need to create another user on my linux box, the same as my windows user?

---

### Post by dmizer on 2008-06-25
> **Hackit said:**
> 
[snip]
Does this mean i need to create another user on my linux box, the same as my windows user?

yes.

just use the commands you posted, but replace "mark" with your actual vista login id.

---

### Post by Hackit on 2008-06-25
when i enter ( gksu gedit /etc/fstab)

this is the output: where is my second drive dev/sdb ?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6111a26b-be55-4bea-a790-0d48ddcb85d3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2f93cd0d-a04a-4cc4-9e63-15bcb213294d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by dmizer on 2008-06-25
use this command to list the hard drives attached to your computer:
```
df -h
```

---

### Post by Hackit on 2008-06-25
ok it is there.

i know the first time when i installed ubuntu, my second drive did not show so i had to change some settings for the drive to mount and then had to give me write access to it.

so i wonder after my reinstall with the 64 bit version the second drive showed up no problem, but i wonder if it is owned by my old user?

here's the out put 

hackitz@ubuntu-server:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G  2.9G  135G   3% /
varrun                499M  220K  499M   1% /var/run
varlock               499M     0  499M   0% /var/lock
udev                  499M   56K  499M   1% /dev
devshm                499M   12K  499M   1% /dev/shm
lrm                   499M   43M  457M   9% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      146G  2.9G  135G   3% /home/hackitz/.gvfs
/dev/sdb1             463G  400G   40G  92% /media/disk

---

### Post by Hackit on 2008-06-25
> **Hackit said:**
> NOTE: Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box just press enter when prompted to enter a password for the user account you're about to create!

In the following example we will add an user called "mark" ...

Example:

Code:

sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark

The "-s /bin/true" in the first line prevents the users from being able to access the commandline of your linux box ("-s" stands for "shell"). I strongly advise you to follow this recommendation! Don't change that setting to a valid login-shell unless you really know what you are doing!

Repeat this step until you configured all user accounts!

Now that we configured samba and created the user accounts we are done with the Linux-part - there's one more thing to do in Windows.


Does this mean i need to create another user on my linux box, the same as my windows user?


This did not work as my vista login has special characters and thats not allowed on linux.

ex: name a. last

---

### Post by dmizer on 2008-06-25
> **Hackit said:**
> This did not work as my vista login has special characters and thats not allowed on linux.

ex: name a. last

then you have three choices:
change your vista login, turn off authenticated windows shares for samba, or use a different file protocol (specifically ftp or scp).

---

### Post by Hackit on 2008-06-27
Thanks for all the help Dmizer

Well i renamed my vista machine user.
I reinstalled ubuntu64 - same name as windows.

now all is good, works like a charm.

Just anothoer quick question about periods in a user name, is there a way around this in linux.
I find it bizarre that a period is a special character.

Thanks again for all your time and help. You are a great ambassador of linux.

---

