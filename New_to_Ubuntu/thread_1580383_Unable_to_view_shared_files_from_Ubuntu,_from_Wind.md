---
title: "Unable to view shared files from Ubuntu, from Windows 7 PC"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by adriancollins on 2010-09-23
Hi,

I am attempting to share my Home folder from Ubuntu 10.04, so that I can access it from my Windows 7 PC on my LAN.

(Note I am able to access data from the Windows PC from Ubuntu, ie: the 'other way around' without a problem)

Potentially sharing from Ubuntu seems very simple. right click on the folder - sharing options, and giving it a share name etc. Then connect to it from the Windows PC.

After looking at lots of forum posts (many seem out of date etc) the only thing I found was that when I first set up the share it did not prompt me to install the 'Shared services' as I believe it should. I did at one point see this prompt briefly but I am not sure how to check whether the SMB service is installed and working correctly?

Just for info, I then try to connect via my windows 7 PC by mapping a drive in the format of //mypcname/sharename.

I would really appreciate some help on this, thanks !

Adrian

---

### Post by migs73 on 2010-09-23
I did the same thing in XP but to get access to the shared folder i just looked at network places and it was there. Can't remember how or if I had to set up the SAMBA on my buntu machine.

---

### Post by sydbat on 2010-09-23
I'm pretty sure SAMBA is involved. Windows cannot read Linux file systems (or any other file system that is not from Windows/Microsoft) without help. However, as the OP pointed out, Linux can read Windows file systems pretty much OOTB.

Go to System > Administration > Synaptic and install SAMBA from there. This will ensure all the dependencies are installed too. Configuring it is something beyond my purview, as I have never used it. It should be pretty straight forward though.

---

### Post by migs73 on 2010-09-23
I'm pretty sure 10.04 has SAMBA installed as default.

---

### Post by adriancollins on 2010-09-23
Hi, thanks for both of your posts: 

Network Places does not work for me (either browsing from Windows, or 'Network' from Ubuntu) - from Ubuntu I get the message 'Unable to mount location' 

Maybe this has to do with Windows 7 as Workgroup is no longer the default name.

I have reinstalled SAMBA again from Synaptic. As you say presumably this will install all required files (Although on other tutorials it still shows that SAMBA prompts to install services such as SMB for Windows when first sharing out the folder)

I still believe it is because SMB services are NOT installed by SAMBA (How do I check this?) OR something to do with Windows 7. Just wish I had an old XP machine kicking about to test further

Cheers

Adrian

---

### Post by egalvan on 2010-09-23
What method of samba did you use - there are two.
Classic and Simple
 Post the output of these commands so we can see what method you are using and how you are using it:

Code:
 ```
 net usershare info
  sudo net usershare info
  testparm -s
```

---

### Post by adriancollins on 2010-09-23
Thanks for your reply, I was not aware that there are 2 methods.

I have posted the responses in full below

net usershare info
[home]
path=/home/adriancollins
comment=
usershare_acl=Everyone:R,
guest_ok=n

[documents]
path=/home/adriancollins/Documents
comment=
usershare_acl=Everyone:R,
guest_ok=n

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = HOMEGROUP
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    comment = Home Directories

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    read only = No
    guest ok = Yes

---

### Post by adriancollins on 2010-09-28
Hi, this thread was going brilliantly but then nothing......could someone else please help me with this issue, thank you

---

### Post by adriancollins on 2010-10-04
time for a bump please...

---

### Post by sandyd on 2010-10-04
> **adriancollins said:**
> Hi, this thread was going brilliantly but then nothing......could someone else please help me with this issue, thank you
```

sudo apt-get install system-config-samba samba
gksudo system-config-samba

```add the shares using the "+" sign.
Make you set the shares to visible and allow access to everyone.

also, 
```

sudo nano /etc/samba/smb.conf

```
there should be a line starting with "security"
change the line to
```

security = share
```
if theirs a semi collon on front of it, remove it.

Then, make sure your workgroup is set correctly;
the 
```

WORKGROUP
```
shoud be set to your network's workgroup (they have to be the same)
fpr example, if my workgroup was sandy, then the line should read
```

 workgroup = SANDY
```

---

### Post by Jerry N on 2010-10-04
> **sydbat said:**
> I'm pretty sure SAMBA is involved. Windows cannot read Linux file systems (or any other file system that is not from Windows/Microsoft) without help. 

Sending data across a network has nothing to do with Windows trying to read a Linux file system.    

With Ubuntu 10.04/Mint 9, you should be able to right click on the folder to be shared and select "Sharing Options".  Select "Share This Folder" and check the two boxes to "Allow others.." and "Guest ..." (it might not be necessary to do both).  If Samba is not installed, the system should offer to do so.  I told Mint 9 (already sharing one folder) to share another folder while I was writing this and it showed up right away on the Windows 7 machine.  I do recall that sometime back I was thinking that it was a little easier with Mint than Ubuntu but there is an Ubuntu 10.04 machine upstairs that is also sharing without difficulty.  I tried Pinguy Linux a couple of days ago and it shared immediately - I think Samba is pre-installed.  Sharing is a lot easier now than it was on Ubuntu 7.xx and 8.xx.

Jerry

---

### Post by Morbius1 on 2010-10-04
Installing system-config-samba will install a gui to create [COLOR=Blue]Samba Classic-shares[/COLOR]. Nothing wrong with that but you already created [COLOR=Blue]Samba Nautilus-shares[/COLOR]. It's best not to use both methods at the same time especially on the same target folder. If you are going to go down that route I suggest you "unshare" the nautilus-shares first.

If you still want to peruse the Nautilus-share route:

From your nautilus-share definitions it looks like you are not allowing guest access. This means the remote user will have to supply a username and password to gain access. Did you create a user and samba password for the remote user to use?

Why not change one of them to allow guest access to see if the problem is something else.

There's also a couple of bugs introduced in the latest Ubuntu so you might want to make sure the following services are actually running:
```
sudo service smbd status
sudo service nmbd status
```If they are not running start them:
```
sudo service smbd start
sudo service nmbd start
```

---

### Post by Aetixintro on 2010-10-04
A little bit uncertain, but it may be an idea to make sure that the shared partition is _mounted_ as _/mount/share_ or something that I've seen in Lucid Lynx. So my suggestion is, that the mount point should be properly set in Ubuntu. Am I out of place?

At least, good luck with your LAN computing! :)

---

### Post by adriancollins on 2010-10-06
Thanks for all your info guys, but after trying everything suggested to me I am still unable to connect from Windows 7 to my Ubuntu Laptop (Other way still works fine at least)

Jerry N - this is exactly what I thought and I realise it should be very easy, and yes the services are running in Ubuntu.

I will take another look in more detail when I have a little more time.

Thanks again, appreciate all of your time....

---

### Post by adriancollins on 2010-10-06
SOLVED!

Unknown to myself it was being blocked by a firewall (Firestarter) on the Ubuntu PC.
Once I had found that and disabled it it worked like a dream

BRILLIANT !

Thanks guys....!

---

