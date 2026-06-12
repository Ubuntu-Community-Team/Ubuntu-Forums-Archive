---
title: "Can't access samba shares between Xubuntu and Windows 10"
date: 2023-02-18
forum: Networking &amp; Wireless
---

### Post by peyre on 2023-02-18
On my son's Windows 10 computer, I've shared C:\Hold.  On my computer I edited /etc/samba/smb.conf and added:

[HomeFolder]
   comment = Home folder share
   path = /home/leon
   read only = no
   browsable = yes

[Storage]
   comment = Storage share
   path = /media/Storage
   read only = no
   browsable = yes

and restarted the service.  Now in File Explorer, he can see my two shares, but gets challenged for credentials.  I've given rwx to those locations for me, my group, and others, but even when he enters *my* user name and password, it says access is denied.

From my side, trying to open smb://Gaming or smb://Gaming/Hold returns the following after it times out.

> Failed to open "File System".
Failed to mount Windows share: Network dropped connection on reset.

On his system, I have SMB 1.0/CIFS File Sharing Support installed.  I've also set AllowInsecureGuestAuth to 1 in the Registry, and set RequireSecuritySignature to 1.  But nothing seems to help.

---

### Post by TheFu on 2023-02-18
Try sharing all user's HOME directories instead:
```
[homes]
  comment = Home Directories
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```

Just replace the 1 stanza, not the entire file.
Also, don't forget to add the account you want to the samba password file.  This is separate from the normal passwd DB on Linux.  Use the **smbpasswd** tool. Probably want something like:
```
sudo smbpasswd -a leon
```
to add use leon to the default file.

BTW, why would you want out of data protocols enabled?  Samba and Win10 both speak CIFS v3.x which is faster AND more secure.  Use that instead. Put
```
min protocol = SMB3
```
into the [global] section and restart the dæmon.  systemctl or service can be used for that.

When ever editing system files, use **sudoedit**, BTW. Safer than most alternatives.

---

### Post by TheFu on 2023-02-18
BTW, CIFS used IP networking, so if the client cannot ping the server by name, then you'll need to correct that OR use the mdns name (xyz.local) OR use the IP address directly.

---

### Post by peyre on 2023-02-19
Sorry, there was a delay before I could try this out.  I added me as a samba user and modified my smb.conf and restarted, but am still getting Access denied messages when I try my credentials.  The smb.conf lines now show as follows; it's possible I got bits wrong here.

[HomeFolder]
   comment = Home folder share
   path = /home/leon
   read only = no
   browsable = yes
   guest ok = no
   writable = yes
   create make = 0644
   directory mask = 0755
   valid users = %S
   min protocol = SMB3

[Storage]
   comment = Storage share
   path = /media/Storage
   read only = no
   browsable = yes
   guest ok = no
   writable = yes
   create make = 0644
   directory mask = 0755
   valid users = %S
   min protocol = SMB3

---

### Post by TheFu on 2023-02-20
That isn't what I suggested.

---

### Post by peyre on 2023-02-20
That...isn't very helpful.

As you've no doubt noticed, I'm very new at working with smb.conf, so I don't know what I did wrong here.  Clearly I misinterpreted your post, but I'm not certain how.

---

### Post by Morbius1 on 2023-02-20
>  From my side, trying to open smb://Gaming or smb://Gaming/Hold returns the following after it times out.
And what happens when you address the Win10 machine this way:
```
smb://gaming.local/hold
```
*[COLOR="#0000FF"]I'm assuming here that "gaming" is the Win10 host name and the share is labeled "hold". And don't forget to add the **[COLOR="#0000FF"].local[/COLOR]** at the end of the host name.[/COLOR]*

For the samba server you've ended up with a sort of hybrid share definition there. Let's focus on the [Storage] share:

Change it back to the way you had it before please:
```
[Storage]
comment = Storage share
path = /media/Storage
read only = no
browsable = yes
```

That does not allow guest access so you will need to pass a user name and password to gain access. You can use your own Xubuntu user name I suppose as long as you added it to the samba password database which you said you did.

For Win10 to access that share go to explorer and enter:
```
\\xubuntu-host-name.local\storage
```

I don't know what the host name of your Xubuntu machine is so replace "xubuntu-host-name" with the real name - and again don't forget the **[COLOR="#0000FF"].local[/COLOR]** at the end.

As far as sharing your own home folder I can't imagine why you would want to share your entire home folder with anyone else but yourself on another machine. I try to answer the question asked rather than imposing my personal preferences on others but ... let's see how far you can get with the suggestion I gave first.

---

### Post by peyre on 2023-02-20
Hey, that did something!  When I connect to smb://gaming.local/hold, I'm challenged for credentials.  I enter the user name for his account (xxx@yyy.com) with the password, and it says 

Failed to open "File System".
Failed to mount Windows share: Invalid argument.

I'm having more luck going the other direction though!  I modified smb.conf and restarted the service (sudo service smbd restart), and now from his computer, \\peyre.local shows my two share and I'm able to browse them.

---

### Post by Morbius1 on 2023-02-20
>  I enter the user name for his account (xxx@yyy.com) with the password, and it says 
You might want to edit your previous post and use something like [email]xxx@yyy.com[/email]. You don't want the whole world to know his email address.

---

### Post by Morbius1 on 2023-02-20
>  Failed to mount Windows share: Invalid argument.
That usually means an smb dialect mismatch which makes no sense. Um ... Did you make any other changes to smb.conf other than the share definitions?

Why not post the output of this command so we can see how things are set up now on the Xub machine:
```
testparm -s
```

---

### Post by peyre on 2023-02-20
Oh yeah, good call.  Fixed it.

Sounds good - here's my testparm:

> Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed

Server role: ROLE_STANDALONE

# Global parameters
[global]
	log file = /var/log/samba/log.%m
	logging = file
	map to guest = Bad User
	max log size = 1000
	obey pam restrictions = Yes
	pam password change = Yes
	panic action = /usr/share/samba/panic-action %d
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	passwd program = /usr/bin/passwd %u
	server role = standalone server
	server string = %h server (Samba, Ubuntu)
	unix password sync = Yes
	usershare allow guests = Yes
	idmap config * : backend = tdb


[printers]
	browseable = No
	comment = All Printers
	create mask = 0700
	path = /var/spool/samba
	printable = Yes


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[HomeFolder]
	comment = Home folder share
	path = /home/leon
	read only = No


[Storage]
	comment = Storage share
	path = /media/Storage
	read only = No


---

### Post by Morbius1 on 2023-02-20
I don't see anything wrong with any client settings ..........

When you passed the microsoft account name did you do it on one line in the username box or did you do it this way:
[ATTACH=CONFIG]291818[/ATTACH]

---

### Post by peyre on 2023-02-20
I did it as per the screenshot there.  It's a home network and I didn't bother changing the Workgroup name, so its name is "WORKGROUP".

---

### Post by Morbius1 on 2023-02-20
The reason I asked is because when WIn10 first came out it would get confused by the way Linux passes credentials in their file managers.

If you passed it this way:
username [email]xxx@yyy.com[/email]
domain WORKGROUP

It wouldn't work.

But if you passed it this way:
username xxx
domain yyy.com

it would work.

---

### Post by peyre on 2023-02-20
It seems to give the same result whether I enter username xxx/workgroup/password, xxx.gmail.com/workgroup/password, or xxx/gmail.com/password. :(

---

### Post by Morbius1 on 2023-02-21
I can't reproduce your error so let's try a different way to access the share:


[] Create a mount point under /media for the time being:
```
sudo mkdir /media/GamingHold
```
[] Make sure cifs-utils is installed:
```
sudo apt install cifs-utils
```
[] Then mount the share - **[COLOR="#0000FF"]temporarily[/COLOR]** - with this command:
```
sudo mount -t cifs -vv //gaming.local/hold /media/GamingHold -o username=xxx,domain=yyy.com,password=zzzz,uid=leon
```

Check /media/GamingHold to verify that it mounted. If not post the output of the mount command.

To unmount:
```
sudo umount /media/GamingHold
```

---

### Post by peyre on 2023-02-21
Hm, might have a problem with the mounting.  I keep getting **bash: !,uid=1000: event not found** - probably because his password ends with an exclamation point, due to gmail's complexity requirements.

---

### Post by TheFu on 2023-02-21
Try using single-quotes around the password if put in the command prompt.  If that doesn't work, try putting a \! instead of a !  For the long term answer, you'll want to setup a "credentials" file, where only root can read it which contains the login credentials.

---

### Post by peyre on 2023-02-21
Oh of course, use the backslash to escape out the character.  That got me one step closer; it at least asked for my password now, but still erroring out, now with

mount error: could not resolve address for gaming.local: Unknown error

---

### Post by TheFu on 2023-02-21
Try using the current IP address, until you can solve your lack of name resolution issues.

---

### Post by Morbius1 on 2023-02-22
So what happened between then:
> **peyre said:**
> Hey, that did something!  When I connect to smb://gaming.local/hold, I'm challenged for credentials.
And now:
> **peyre said:**
> mount error: could not resolve address for gaming.local: Unknown error

If Win10 is on a mobile device is it at all possible it didn't automatically switch to the Private profile:
[ATTACH=CONFIG]291821[/ATTACH]

---

### Post by peyre on 2023-02-22
That, at least, isn't the issue - since this is a home computer, a desktop in fact, which doesn't even move around.  It lives in the office and is connected by Ethernet cable (same as my computer).  So roaming profiles and WiFi won't be complications here.

---

### Post by peyre on 2023-02-22
Thanks, TheFu.  If I enter it with //*address*.local I again get **mount error: could not resolve address for 192.168.1.71.local: Unknown error**.  But if I leave off .local, it says

> mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)

Even though I included his full user name (with @gmail.com), domain=workgroup, and his password with the exclamation point escaped out (\!).

---

### Post by TheFu on 2023-02-23
.local is added to a hostname under mdns/avahi.
Use just the IP address and try again.

If you cannot **ping** it, then it won't work. ping is a common network command across all platforms that support IP networks.

---

### Post by peyre on 2023-02-25
> **TheFu said:**
> .local is added to a hostname under mdns/avahi.
Use just the IP address and try again.

If you cannot **ping** it, then it won't work. ping is a common network command across all platforms that support IP networks.

I know, pinging is the simplest thing in the world, networking wise.  Yet sometimes it doesn't work when it should.  Just last night during LAN maintenance I had rebooted one of our Hyper-V machines and had a ping -t running so I'd know when it came back up, but it kept getting my response.  When I mentioned that to the others, it turned out one of the guys had already remoted into it.  Still don't know why it wasn't responding to a ping.

Also, now for some reason I'm able to ping the machine either by IP address or hostname.

---

### Post by TheFu on 2023-02-25
If you can't ping, that's a Windows issue or a firewall issue.  Ubuntu doesn't enable a firewall by default, because it doesn't have any listeners enabled by default.  If you add network listeners, YOU are expected to know better and setup the firewall.

Unix-like OSes expect the admin to be cognizant of security considerations.

If you don't show the exact commands, there's little option for us to be helpful.  People often misinterpret commands, options, and output.

---

### Post by peyre on 2023-02-25
As I mentioned, I am currently able to ping.  I don't know what was wrong before.

---

### Post by TheFu on 2023-02-25
> **peyre said:**
> As I mentioned, I am currently able to ping.  I don't know what was wrong before.

Please mark solved threads as "SOLVED" using the thread tools button, so people don't waste time.

---

### Post by peyre on 2023-02-25
Except it's not solved.  I still can't connect to shares on the Windows machine, though I can connect from the Windows machine to this one.

---

### Post by Morbius1 on 2023-02-26
I have a Win10 machine with a user that has a Microsoft account name:

host name == vwin1064
user == [email]xxx@gmail.com[/email] with a password of yyy

I created a folder off C: labeled Hold

I right clicked the Hold folder > **Properties** > **Sharing** Tab:

Made sure I was listed as the owner then selected **Share**.

I then went to my Linux machine:

Created a mount point at **/media/Temp**

Created a credentials file to house my MS Account name at **/etc/samba/vwin1064cred** with this content:
```
username=xxx
domain=gmail.com
password=yyy
```
I then mounted that share to Temp using that credentials file:
```
sudo mount -t cifs //vwin1064.local/hold /media/Temp -o credentials=/etc/samba/vwin1064cred,uid=tester
```

I checked the contents of that share:
> tester@vxub2204:~$ ls -l /media/Temp
total 0
It was empty so I added a file from Xubuntu to Win10:
> tester@vxub2204:~$ touch /media/Temp/fromXubuntu.txt
Then checked the contents again:
> tester@vxub2204:~$ ls -l /media/Temp
-rwxr-xr-x 1 tester root 0 Feb 26 12:06 fromXubuntu.txt

And confirmed the file was in fact on Win10:
[ATTACH=CONFIG]291840[/ATTACH]

This thread has been going on for a week now and as you can see above I simply cannot reproduce your symptoms.

Good Luck.

---

### Post by peyre on 2023-02-26
Strange!  It's still being stubborn here; must be something peculiar to our setup.

Well, we got the connection working one way, anyhow, which was the main thing.  I can get by as long as I can go Windows-Linux even if Linux-Windows is being difficult.  So I'll call this one solved then.

Thanks for your time and efforts on my behalf!

---

