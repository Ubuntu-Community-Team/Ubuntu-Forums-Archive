---
title: "Access Samba-Shares with Authentication"
date: 2016-01-10
forum: Networking &amp; Wireless
---

### Post by johannes15 on 2016-01-10
Hi all,

I am trying to access samba-shares that I specified in my smb.conf:
```

[global]

        server string = UBUNTU
        bind interfaces only = No
        map to guest = Bad User
        syslog = 0
        unix extensions = No
        load printers = No
        printcap name = /dev/null
        disable spoolss = Yes
        registry shares = Yes
        idmap config * : backend = tdb
        guest ok = Yes
        printing = bsd
        print command = lpr -r -P'%p' %s
        lpq command = lpq -P'%p'
        lprm command = lprm -P'%p' %j
        wide links = Yes

[media]
        path = /media
        force user = myusername
        read only = No

```

Of course, myusername has been added to the smbpasswd-database.

So far, I managed to access \\UBUNTU\media from my windows 10 box. I can read and write files. 
However, this doesn't require any user authentication and I'd rather secure those files from any unwanted scumbags snooping around.

I've tried to add the line ```
guest ok = No
``` to the share-definition [media].
This results in a prompt by Windows, requiring username and password. However, when entering "myusername" and password, windows aborts with an error, saying:
"Can't access \\UBUNTU\media..."

If I instead try to access the very same share by typing the hosts IP-Address, I have no problems accessing the data, but I am again not prompted for username/password (like if I had allowed guest access)

As I said, I want noone to get access that easily. I have no idea where even to begin. I have experience with Linux, but at networking, I'm quite a newbie after all. Can anyone please help me find an approach to solve this problem? 
THANKS in advance.

---

### Post by SeijiSensei on 2016-01-10
You should get prompted for a password if you use \\ip.addr.of.server\media.  Do you?

You can fix the name resolution problem by configuring the server to become a "WINS" name server for the workgroup.  Usually this requires little more than adding the directive
```
wins support = yes
```
to smb.conf.  You'll need to specify a workgroup on both the server and the clients, too.  I recommend you read at least this chapter from the Samba manual: [https://www.samba.org/samba/docs/using_samba/ch03.html](https://www.samba.org/samba/docs/using_samba/ch03.html).

---

### Post by johannes15 on 2016-01-11
Thanks for the reply. I will take a look at this. 
> **SeijiSensei said:**
> You should get prompted for a password if you use \\ip.addr.of.server\media.  Do you?

At first, when I tried this, I was not prompted for password.
However, after restarting samba and/or windows (I'm uncertain about that) I **am **prompted, but only once. After typing in the correct login data, I can access all files as usual. So this seems to be no problem, obviously windows is just saving the login details.

---

### Post by johannes15 on 2016-01-11
> I recommend you read at least this chapter from the Samba manual: [https://www.samba.org/samba/docs/using_samba/ch03.html](https://www.samba.org/samba/docs/using_samba/ch03.html).
Okay, I've worked that through. I added the line ```
wins support = yes
``` to smb.conf. With "testparm" I verified that the configuration has been applied. Then I restarted samba. Also, on my Windows machine, I added the IP-address of the WINS-server to the configuration of my Wifi-Adapter (IPv4).

Sadly, after retrying to access the share [media] at \\UBUNTU\media, it shows the same error as before.
A look inside the smbd.log told me ```
guest user (from session setup) not permitted to access this share (media)
``` 

Then again, when I try to access the same share from my ubuntu box with smbclient, everything works fine. 
```
smbclient //UBUNTU/media -Umyusername%<passwd>
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.17-Debian]
smb: \>

```
Any ideas how to proceed? Why does samba think that I'm guest user, even after logging in with a valid samba username? 
Thanks in advance

---

### Post by SeijiSensei on 2016-01-11
> **johannes15 said:**
> Sadly, after retrying to access the share [media] at \\UBUNTU\media, it shows the same error as before.  A look inside the smbd.log told me ```
guest user (from session setup) not permitted to access this share (media)
```
Well it looks like name service is working correctly.  

I take it this is a problem with a Windows client? See if you can map a network drive letter to the share.  I'd try this from the Windows cmd.exe terminal program using the "net use" command so you can see what errors it throws.  My Windows is a bit rusty these days, so I'll leave it to you to determine the proper syntax.  Type "net use /h" at the prompt to get help.

---

### Post by johannes15 on 2016-01-11
Thank you for the reply.
> **SeijiSensei said:**
> See if you can map a network drive letter to the share.  I'd try this from the Windows cmd.exe terminal program using the "net use" command so you can see what errors it throws.

I've tried this:
```
net use K: \\UBUNTU\media /USER:myusername password
```
The following error was thrown:
```
System error 1219 has occurred.

Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again.
```

If I do the same thing elevated as admin:
```

C:\Windows\system32>net use K: \\UBUNTU\media /USER:myusername password
The command completed successfully.

C:\Windows\system32>cd /DK:\
K:\>dir
 Volume in drive K is media
 Volume Serial Number is F6B5-DCBE
 
 Directory of K:\

01/10/2016  11:09 PM    <DIR>          .
12/12/2015  01:26 AM    <DIR>          ..

K:\>notepad sample.txt

```
Everything works fine.
The problem is: I can only access the share that had just been mapped from this elevated command prompt! K:\ does not appear at "This PC"->"Network location" and any other non-elevated command prompt can't find the path when trying to access it. (cd /DK:\)

Maybe this is not the appropriate forum for this kinda problem... I'd be thankfull for any ideas what to try next though.

---

### Post by johannes15 on 2016-01-12
Okay, I think I've figured it out. 
I used the network share before as my backup-drive. After removing this (Control Panel -> System and Security -> File History -> Turn OFF) it worked fine, I was able to connect the drive from non-admin command promt as well as from the file explorer with no errors.
Thank you very much for helping!

---

### Post by SeijiSensei on 2016-01-12
> **johannes15 said:**
> 
The following error was thrown:
```
System error 1219 has occurred.

Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again.
```

That's a known "feature" of Windows.  Do a Google search for "[multiple connections to a server not allowed]("https://www.google.com/search?q=multiple+connections+to+a+server+not+allowed&ie=utf-8&oe=utf-8")," and you'll see a bunch of discussions of this issue.

---

