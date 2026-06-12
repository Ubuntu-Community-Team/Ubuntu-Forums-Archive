---
title: "samba help"
date: 2018-09-19
forum: Networking &amp; Wireless
---

### Post by steveo314 on 2018-09-19
I follow this tutorial:
[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html.en]("https://help.ubuntu.com/lts/serverguide/samba-fileserver.html.en")

And everything works perfect. But then when I add this in:
[https://help.ubuntu.com/lts/serverguide/samba-fileprint-security.html.en]("https://help.ubuntu.com/lts/serverguide/samba-fileprint-security.html.en")

Everything goes down the toilet.
Without the security part of the samba, I can get into the samba shares from Windows 7. But when I add the security part, I cannot get into the share from Windows 7. I get the "Windows cannot access <server name>" error after adding the security part. I am running Ubuntu 18.04 with the latest updates.

---

### Post by Morbius1 on 2018-09-19
I'm embarrassed to admit how long it took me to get a working knowledge of Samba but part of the lost time was following HowTo's like the ones you mentioned above.

The first HowTo created a share that will break the moment you add a client user to the samba password database. It's easy to fix but it should never have been presented that way.

The second HowTo lost credibility the moment it said this:
> 5. security = share: allows clients to connect to shares without supplying a username and            password.           
There is no such thing as share level security in the version of Samba that Ubuntu 18.04 provides. It hasn't been an option for some time. Then all this "stuff" about libpam-winbind, ACL's, and AppArmor .... Cheese and Crackers. GrandPa would start using phrases like "bunch of hooey" to describe all that.

Are you setting up a samba server in your own home network or is this something bigger?
Are you using Ubuntu Server 18.04 or Ubuntu Desktop 18.04 and using it like a server with a desktop?

---

### Post by steveo314 on 2018-09-19
I am trying to setup a file server at my place of employment. The old Win2000 file server needs to be retired. 
I am using Ubuntu Desktop 18.04. Plan on setting it up and setting it to the side with only accessing it with a mouse/keyboard for maintenance.
Would Ubuntu Server work better?

---

### Post by SeijiSensei on 2018-09-19
If you don't need a GUI, yes.  The Server version has much less overhead.

However, if you're not yet comfortable using the command line, then you might want to start with a desktop version.  I recommend trying to do everything from the command prompt, though.  You'll then be able to connect to the server over the network using SSH from any desktop running a Linux variant or from Windows desktops with a copy of [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") installed.

For access control, I use
```

        security = user
        passdb backend = tdbsam

```
in /etc/samba/smb.conf.  The tdbsam option is the default.  You then add users to the database with the "[smbpasswd]("https://linux.die.net/man/5/smbpasswd")" command.

You'll also want to have the server act as a "WINS" server so that the client Windows machines will register their names.  Use
```

        wins support = yes

        os level = 33
        preferred master = yes

```

The last two directives may already be active by default.

If you have a local DNS server on your network, add the directive
```

        dns proxy = yes

```

---

### Post by steveo314 on 2018-09-19
Made the couple changes you suggested, @SeijiSensei , and now I am getting an 'Failed to start Samba SMB Daemon' when i run 
    sudo systemctl status smbd.service

---

### Post by Morbius1 on 2018-09-20
This is just a suggestion and it is based on your original post:
> **steveo314 said:**
> I follow this tutorial:
[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html.en](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html.en)

And everything works perfect. 
Start over. You had a working samba server at one point but the inclusion of things like apparmor and even ACL is complicating things and I for one have no experience with how AppArmor interferes with things.

When you do start over I would make 2 shares: [Public] and [Private].

For the [Public] share keep it simple at first. I will correct the mistake in the HowTo:

```
[Public]
  path = /srv/samba/Public
  guest ok = yes
  read only = no
  force user = mork
```
[COLOR=#0000cd]*Change mork to your server login user name.*[/COLOR] Then make sure the shared folder is owned by mork:
```
sudo chown mork /srv/samba/Public
```
For the [Private] share - also keeping it simple:
```
[Private]
  path = /srv/samba/Private
  guest ok = no
  read only = no
```
For the time being set the Linux permissions on the Private folder to universal:
```
sudo chmod 0777 /srv/samba/Private
```

Only those users with samba credentials will be able to access the share so you will need to add them as local Linux users then add them to the samba password database. So for mork for example it would be:
```
sudo smbpasswd -a mork
```

There are different variations to how you can limit access to the Private share:

You can add a line to the share definition that limits it to specific users:
```
valid users = mork, mindy
```
Or to a group of users:
```
valid users = @plugdev
```

---

### Post by steveo314 on 2018-09-20
That got me to where I can get to the share. But it seems like the permissions are read only with the Private directory.

And then when I changed sub directories to 0777, I'm not able to access the share any longer.

---

### Post by Morbius1 on 2018-09-20
When mindy adds a file to the Private share it is read only to mork - mork as a samba client and mork as the local user on the server.

If you want a share where everyone who has access can read and write to everything within that share it can either be easy or complicated.

I will go with the easiest way first and it's going to use the same option as the Public share:
> [Private]
  path = /srv/samba/Private
  guest ok = no
  read only = no
  force user = mork 

It' not intuitive what's happening there but Samba will restrict who can access the share to those with proper credentials but once they are allowed they will all be recognized as mork. When mindy passes the credentials check and adds a file it will be saved with owner = mork. As long as all of the files in the share are owned by mork to begin with everything will work for all future users to this share.

There is a more complicated mechanism available - the more old-school approach that is detailed here: [https://askubuntu.com/questions/1020281/best-practice-for-shared-directory-on-server-samba-windows-10-clients/1020828#1020828](https://askubuntu.com/questions/1020281/best-practice-for-shared-directory-on-server-samba-windows-10-clients/1020828#1020828)

The one caveat to that approach is mentioned in the link: It will work for Ubuntu Server 18.04. It will work for Xubuntu Desktop 18.04. It will not work for Ubuntu Desktop 18.04 because they screwed up umask. The advantage though is that regardless of who owns the process on the server itself that may add files to the shared directory it will insure that everyone will have r/w/ access to the contents.

---

### Post by steveo314 on 2018-09-20
I'm going to start over with Ubuntu Server 18.04. I'll report back AQAP.

***UPDATE
I can get to the folder where the share is. Go to click on the share and it asks for the user and pass. I enter the user credentials that I setup and put in a samba group on Ubuntu Server and I get an error dialog that "<share> is not accessible. You might not have permission to use...."

Using Ubuntu Server 18.04 now.

---

### Post by Morbius1 on 2018-09-20
Post the output of this command so we can see how you are set up:
```
testparm -s
```

---

### Post by steveo314 on 2018-09-20
```
:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[SHARE]"
Loaded services file OK.
Server role: ROLE_STANDALONE

#Global parameters
[global]
   dns proxy = No
   log file = /var/log/samba/log.%m
   map to guest = Bad User
   max log size = 1000
   obey pam restrictions = Yes
   pam password change = Yes
   panic action = /usr/share/samba/panic-action %d
   password chat = *...*.
   passwd program = /usr/bin/passwd %u
   security = USER
   server role = standalone server
   server string = %h server (Samba, Ubuntu)
   syslog = 0
   unix password sync = Yes
   usershare allow guests = Yes
   workgroup = GROUP
   idmap config * : backend = tdb

[printers]
   browsable = No
   comment = All Printers
   create mask = 0700
   path = /var/spool/samba
   printable = Yes

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers

[SHARE]
   create mask = 0664
   force directory mode = 02775
   force group = input
   path = /srv/samba/iti
   read only = No
   valid users = @input
```

I have only added 1 user so far:
```
sudo useradd USER
sudo usermod -a -G input USER
sudo passwd USER
sudo smbpasswd -a USER
```

Set up the share:
```
sudo mkdir -p /srv/samba/iti
sudo chmod -R 2775 /srv/samba/iti
sudo chown root:input /srv/samba/iti
```

---

### Post by Morbius1 on 2018-09-20
As it turns out I have the same share definition on my test server ... well almost. The group I used was plugdev and I have a different path.

So I created the USER user which is something I wouldn't have done - all caps, etc...the same way you did except with a different group:
> sudo useradd USER
sudo usermod -a -G plugdev USER
sudo passwd USER
sudo smbpasswd -a USER
I can connect to the server with the USER user and when I add a file it saves the way I expected it to:
> ls -al /srv/PrivateSGID | grep USER
-rw-rw-r-- 1 USER    plugdev    0 Sep 20 17:54 USERfile.txt
That's a long winded way of saying I cannot reproduce your symptoms.

I see nothing wrong with what you have done or how your smb.conf is set up so I will have to think about this a bit to see how I can force my own setup to fail with your error message.

---

### Post by steveo314 on 2018-09-20
I didn't use USER for a username

I need to check the permissions on my share the way you did. That may be my issue.

---

### Post by steveo314 on 2018-09-21
When I enter this command using your example:
```
ls -al /srv/PrivateSGID | grep USER
-rw-rw-r-- 1 USER plugdev 0 Sep 20 17:54 USERfile.txt
```
I do not get any output for the samba user. if i change USER to the local server user i get the same output as you.

---

### Post by Morbius1 on 2018-09-21
Then it worked as expected.

---

### Post by steveo314 on 2018-09-21
I still cannot get into the share from the Windows 7 machine.

The local user is the user setup during install. The samba user is USER in the example commands

I can SSH in, but was looking to be able to use Windows Explorer

---

### Post by Morbius1 on 2018-09-21
Then I do not understand this post:

> **steveo314 said:**
> When I enter this command using your example:
```
ls -al /srv/PrivateSGID | grep USER
-rw-rw-r-- 1 USER plugdev 0 Sep 20 17:54 USERfile.txt
```
I do not get any output for the samba user. if i change USER to the local server user i get the same output as you.

---

### Post by steveo314 on 2018-09-21
If I use the Ubuntu user I get:
```
ls -al /srv/PrivateSGID | grep UUSER
-rw-rw-r-- 1 UUSER plugdev 0 Sep 20 17:54 USERfile.txt
```

If I use the user i added and added to the samba group I get:
```
ls -al /srv/PrivateSGID | grep USER
```

---

### Post by Morbius1 on 2018-09-21
I didn't understand that either.

Let's try this:

[1] Run this command on the server to find the permissions of the shared folder:
```
ls -dl /srv/samba/iti
```
It should come back with something like:
> drwxrwsr-x 3 root input .......
[2] Make sure that the user name you are using in Win7 to access the samba server is a member of the input group in Ubuntu:
```
id whatever-user-name-you-are-using-to-access-this-machine-from-Win7
```
[3] Make sure the user name you are using in Win7 to access the samba server is in the samba password database:
```
sudo pdbedit -L
```

That and samba actually running are all you need to access the share.

---

### Post by steveo314 on 2018-09-21
1.
```
drwxrwsr-x 2 root input 4096 Sep 21 13:55 /srv/samba/iti
```

2.
```
uid=1001(USER) gid=1001(USER) groups=1001(USER),104(input)
```

3.
```
USER:1001:
```

---

### Post by Morbius1 on 2018-09-21
Then you should be able to access the share from Win7.

The only other thing that can get in your way is name resolution or a firewall on Ubuntu. Turn your firewall off for now on Ubuntu and access the share from Win7 by it's ip address as in:
```
\\ip-address-of-Ubuntu-server\SHARE
```

---

### Post by steveo314 on 2018-09-21
ufw is disabled and I cannot login to the share with the ip either

---

### Post by Morbius1 on 2018-09-21
There is nothing left to do on the Ubuntu end of this. I cannot reproduce your symptom.

---

### Post by steveo314 on 2018-09-21
Are there any Windows settings that pop out at you that I could try?

---

### Post by Morbius1 on 2018-09-21
This is going to be a flat out guess. There is an issue with another Windows version - WinXP - not WIn7. WinXP is not able to connect to a modern samba server because the security modes are now incompatible.

For a WinXP client to a modern samba server to work you would have to set smb.conf back to where it was back then. See if it's the same problem with Win7.

Edit smb.conf and right below the "workgroup = GROUP" line add these two:
```
lanman auth = yes
ntlm auth = yes
```
Then restart smbd:
```
sudo service smbd restart
```
Try connecting to the server again and see if that did anything. It's easy enough to undo if it does nothing.

This is literally all I can think of at this point. The only Windows machines I have at this point are Win10 so there is no longer any way for me to test this.

---

### Post by steveo314 on 2018-09-24
I'll keep poking around with it. Since you mentioned the Windows version thing, I can get to it from Windows 10. 7 is still a no. I can try XP next. I added the two lines you mentioned. I have a Windows 2000 machine I can try from as well. We are a multi Windows version office.

---

### Post by steveo314 on 2018-09-24
Checking other PCs:
The Windows 7 machine I have been mentioning: no dice
Windows 2000 machine: Yahtzee!
Windows XP machine: Yathzee!
Different Windows 7 machine: Yahtzee!
Windows 10 machine: Yahtzee!

---

### Post by steveo314 on 2018-09-24
I have it figured out now. Thank you for all of you help, Morbius1.

---

### Post by Morbius1 on 2018-09-24
So what was it? Your situation my come up again here or some other forum.

---

### Post by steveo314 on 2018-09-24
Control Panel >> Network and Sharing >> Advanced Settings >> Home or Work >> Homegroup connections >> Allow Windows to manage...

---

