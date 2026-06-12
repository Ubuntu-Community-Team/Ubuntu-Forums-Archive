---
title: "Samba force create/directory mode/mask not replicating in file system"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by flywushu on 2008-06-01
Hi All

I'm having an issue with Samba where despite having tried various file permissions permutations such as:

```
create mask = 0660
directory mask = 0770
force create mode = 0660
force directory mode = 0770
```

- or -

```
create mask = 0660
force create mode = 0
security mask = 0770
force security mode = 0
directory mask = 0770
force directory mode = 0
directory security mask = 0770
force directory security mode = 0
```

every directory and every file which is created in my server file system, by means of samba, has file permissions 755. I have googled-around for this issue and searched various forums but none of the suggestions I've found as yet have worked.

I've attached my smb.conf below. Thank you in advance of any suggestions.

```
[global]
   force group = sambashare
   workgroup = WORKGROUP
   netbios name = lancelot
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   socket options = TCP_NODELAY
   usershare allow guests = yes

#option a
;   create mask = 0660
;   directory mask = 0770
;   force create mode = 0660
;   force directory mode = 0770

[homes]
   comment = Home Directories
   browseable = yes
   writeable = yes   
   valid users = cai

[permissions-test]
   comment = Comedy
   path = /disk300-a/Comedy
   browseable = yes
   writeable = yes
   guest ok = no

# mask is the limit
# mode is the actual value to use  

#option b 
   create mask = 0660
   directory mask = 0770
   force create mode = 0660
   force directory mode = 0770

#option c
;   create mask = 0660
;   force create mode = 0
;   security mask = 0770
;   force security mode = 0
;   directory mask = 0770
;   force directory mode = 0
;   directory security mask = 0770
;   force directory security mode = 0
```

---

### Post by jamessnell on 2008-07-09
I have this same problem. Anyone have much luck finding a solution yet?

---

### Post by fcelda on 2008-07-29
The same problem... no solution so far?

---

### Post by jamessnell on 2008-07-29
I found the solution. The key is that the masks are logically ORed with things. You need to RTFM unfortunately. Though it only takes a few mins. :)
```
man smb.conf
```

---

### Post by dfreer on 2008-08-18
Here's what I use on my server, might be of more help then the above post:
```
[MyShare]
  comment = Read only share except for authorized users
  path = /mydata/mystuff/
  public = no
  guest ok = no
  read only = yes
  create mask = 0644
  directory mask = 0755
  force group = mygroup
  write list = myname, @mygroup

```

---

### Post by nivl4 on 2009-09-18
ignore that worthless RTFM suggestion.
try this[FONT=monospace] [/FONT]in /etc/samba/smb.conf:

unix extensions = no


works on Hardy LTS with Samba 3.0.28a

---

### Post by jamessnell on 2009-09-18
> **nivl4 said:**
> ignore that worthless RTFM suggestion.
try this[FONT=monospace] [/FONT]in /etc/samba/smb.conf:

unix extensions = no


works on Hardy LTS with Samba 3.0.28a

Lol, indeed - while that may well be a great solution.. If you're barely using the power of Samba and want to circumvent all sorts of functionality.

If anyone on my team ever rejected to the validity of RTFM, I'd seriously reconsider the quality of their judgments. And possibly replace them with a very small shell script. ;)

If you get things working by Guess & Check, you're sort of asking for pain. Though if you're just screwin around at home, as long as you have a good backup, I guess have at 'er... And maybe this is a lesson that every one just has to learn for themselves.

Blah, have fun everyone. If disabling "unix extensions" doesn't seem to hack it for you, once again, you can always read the documentation on how to use the thing you're working with. Or just blow-up in a puff of smoke & tears.

---

### Post by johnnyis42 on 2009-10-06
> **jamessnell said:**
> Lol, indeed - while that may well be a great solution.. If you're barely using the power of Samba and want to circumvent all sorts of functionality.

If anyone on my team ever rejected to the validity of RTFM, I'd seriously reconsider the quality of their judgments. And possibly replace them with a very small shell script. ;)

If you get things working by Guess & Check, you're sort of asking for pain. Though if you're just screwin around at home, as long as you have a good backup, I guess have at 'er... And maybe this is a lesson that every one just has to learn for themselves.

Blah, have fun everyone. If disabling "unix extensions" doesn't seem to hack it for you, once again, you can always read the documentation on how to use the thing you're working with. Or just blow-up in a puff of smoke & tears.

Well, your RTFM suggestion kinda neglected to see the simple fact that according to the M in RTFM, the OP's config should work.  For those of us with the same issue (seemingly correct configuration but unexpected file creation behaviour) it is not a very helpful suggestion.

In fact, I'm using a share config that worked fine under 8.10, unfortunately I'm not sure if the samba version changed or if it's something else.

In my case, unlike the OP, what seems to be happening is that my read bits for the group and everyone permission are getting masked out.

After tearing my hair out I realised that this problem only affected one application: firefox.  On closer inspection (like the OP I was making random changes to the share config) I found that samba behaved exactly as I would expect it to, provided I wasn't downloading via firefox.

So my suggestion would be to try different methods of moving files and see if you get different behaviour.

---

### Post by jamessnell on 2009-10-06
Weird, I wonder if it's possible there were remotely significant changes to the manual in one of the more recent revisions?

I kind of doubt it.

Well, anyway, I read the manual until I found what I needed. I applied what I found and the issue I had appeared resolved after a reasonable wedge of testing.

At the end of the day that was now a long time ago, so I can't really contend anything as I usually solve problems, bookmark what I did (or document it otherwise) and move on. So I don't remember the details anymore, just that I was banging my head against the wall until I ran *man samba*.

Anyway, I'm glad to hear you resolved your problem too.

---

### Post by korsi on 2009-10-07
I don't understand why setting unix extensions = no would help in this case. In the manual it explicit says that these extensions are of no current use to Windows clients. So it shouldn't matter what you set this to.

What may actually help (which it did for me) is to validate the smb.conf file by running testparm
```
testparm -v /etc/samba/smb.conf
```

In my case I found that some map settings made problems:
```
[work]
  comment = workfiles
  path = /storage/work
#  map archive = yes
#  map hidden = yes
#  map system = yes
  inherit permissions = yes
  create mode = 0664
  directory mode = 0775
  valid users = @asd
  writable = yes

```

The map archive, hidden and system maps these file attributes to the execute bit. Then it doesn't matter if the create mode tries to mask away the execute bit.

---

### Post by thecaligarmo on 2010-02-01
> **jamessnell said:**
> I found the solution. The key is that the masks are logically ORed with things. You need to RTFM unfortunately. Though it only takes a few mins. :)
```
man smb.conf
```

How does 'RTFM' work exactly? I'm having the same issue and can't seem to get it to work properly. I get the whole OR'ed concept, but don't know wha tyou mean by 'RTFM'

Thanks!

New info: We were testing it out and it seems to be working when we are trying to create a directory using Windows (0770 appears perfectly), but it fails when we are using an apple computer (defaults to 0755). Can that be fixed with RTFM too?

---

### Post by miraculix125 on 2010-11-08
> **thecaligarmo said:**
> How does 'RTFM' work exactly? I'm having the same issue and can't seem to get it to work properly. I get the whole OR'ed concept, but don't know wha tyou mean by 'RTFM'

Thanks!

New info: We were testing it out and it seems to be working when we are trying to create a directory using Windows (0770 appears perfectly), but it fails when we are using an apple computer (defaults to 0755). Can that be fixed with RTFM too?

most things can be fixed by reading the manual.

---

### Post by AlexanderDGreat on 2011-01-01
Just want to take a NOTE, the SMB.CONF

create mask
directory mask

Will Be Applied To Windows Making A File / Folder on A WINDOWS Machine, not the other way around.

When you create a directory in Unix, this isn't followed at all. If you want Unix users automatic MASKS, you need to setup a crontab for that purpose or a script that scans the folder every 3 seconds and change the permissions.

---

### Post by julian.neil on 2011-02-03
I know this is an old thread.. but it took me a little while to find the answer.
you need to set force security mode and force directory security mode as well.
see [http://lists.samba.org/archive/samba/2010-August/157630.html](http://lists.samba.org/archive/samba/2010-August/157630.html)

---

### Post by techflat on 2011-09-30
Thanks julian.neil. This worked for me.

---

### Post by jolig on 2012-01-11
I have the same issue since yesterday wo modifying anything to my configuration.
I am running Ubuntu 11.10 since couple of months

Trying to se force security parameters didn't fix my problem 

Any hint ?

---

### Post by bab1 on 2012-01-11
> **jolig said:**
> I have the same issue since yesterday wo modifying anything to my configuration.
I am running Ubuntu 11.10 since couple of months

Trying to se force security parameters didn't fix my problem 

Any hint ?

You are better off starting your own thread and stating your *specific *problem.  What you have stated is way too non-specific for anyone to help with your problem.

---

### Post by bartabbas on 2013-02-08
I'd the same problem :

```
create mask = 0775
directory mask = 0775
```didn't work for me until I add this :

```
security mask = 0775
```

This line changes default umask for files/directories created by Samba.
Perhaps you can set it to 0777 and then adjust the rights with 'create mask' and 'directory mask' lines.

Regards,

---

### Post by wildmanne39 on 2013-02-08
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

