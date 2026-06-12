---
title: "[SOLVED] Samba help wanted please!!"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by Rich930 on 2007-04-08
Hey, i have a linux machine running as a file server for windows using samba, but ive just remebered that theres two HDD's in my linux box. I found out how to format , and then enable the second one, but is there anyway for me to use it as additional space for windows? Like telling samba to write to it?

Thanks for any help.  XD

---

### Post by r00tintheb0x on 2007-04-08
Do these samba shares exist in an existing linux machine, or are you wanting to build a samba server?

---

### Post by dmizer on 2007-04-08
edit your /etc/samba/smb.conf file:
```
gksudo gedit /etc/samba/smb.conf
```

look toward the end of the file, and you should have a section that looks something like this (this is from my own smb.conf file):
```
[shared]
    path = [COLOR="Red"]/home/shared/[/COLOR]
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = dmizer
    force group = dmizer
```

you can do one of two things, you can change the line in red so it points to your second hard drive (change the location of your current share).  or, you can add another identical section that points to your second hard drive (two shares).  so the end of your smb.conf might look something like this:
```
[shared]
    path = /home/shared/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = dmizer
    force group = dmizer

[new_disk]
    path = /mnt/hdc1/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = dmizer
    force group = dmizer
```

if you have trouble with this, just post the contents of /etc/samba/smb.conf and we'll walk you through it.

---

### Post by Rich930 on 2007-04-09
> **dmizer said:**
> edit your /etc/samba/smb.conf file:
```
gksudo gedit /etc/samba/smb.conf
```

look toward the end of the file, and you should have a section that looks something like this (this is from my own smb.conf file):
```
[shared]
    path = [COLOR="Red"]/home/shared/[/COLOR]
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = dmizer
    force group = dmizer
```

you can do one of two things, you can change the line in red so it points to your second hard drive (change the location of your current share).  or, you can add another identical section that points to your second hard drive (two shares).  so the end of your smb.conf might look something like this:
```
[shared]
    path = /home/shared/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = dmizer
    force group = dmizer

[new_disk]
    path = /mnt/hdc1/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = dmizer
    force group = dmizer
```

if you have trouble with this, just post the contents of /etc/samba/smb.conf and we'll walk you through it.

so the "new-disk" part , will add my second HDD? , so when i access the machine, it will still have one IP adress from the windows box, but with double amount of storage?

If yes, please go through what i need to do again, im very n00bish with linux ;)

---

### Post by Robocoastie on 2007-04-09
just a note to let y'all know that dmizer's post helped me out with a samba question. Morale of the story is never be afraid to ask a question because you never know when at least part of the question or one of the threaded responses answers someone else's question.

> so the "new-disk" part , will add my second HDD? , so when i access the machine, it will still have one IP adress from the windows box, but with double amount of storage?

Rich, I think that will make 2 shares show up when you attempt to access the server via your xp box. Then your 'new" drive is completely shared (not just one folder which IMO it's still better to make and add a /shared in that path).

---

### Post by dmizer on 2007-04-09
as robocoastie indicated, this will give you two separate shares.  so when you go to "my network places" on your windows box, you will see two shares from your ubuntu box.  one named "shared", and one named "new_disk"

you can of course feel free to name "new_disk" whatever you like.  also make sure that the path = /mnt/hdc1 actually matches where you've mounted your second hard drive, because the above example is from my own machine, not yours.

---

### Post by Rich930 on 2007-04-10
ok thats fine, so could you please guide me through how i do this please, many thanks again :)

---

### Post by dmizer on 2007-04-10
no problem ... just post the contents of this file: /etc/samba/smb.conf

you can view this file by entering the following line into the terminal:
```
gksudo gedit /etc/samba/smb.conf
```

---

### Post by Rich930 on 2007-04-10
erm ok, but i typed that in , and it says:

"(gedit:16531): GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

Then the editor opens up blank :S

i typed "sudo gedit /etc/samba/smb.conf"  and it opened an editor with what i think is correct.

Is this right? 

The file starts out: "[global]
;General server settings
netbios name = Wardy"

and i did find, right at the bottom a bit that says: 

"[MyFiles]
path = /home/samba
browsable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = wardy
force group = wardy
avalible = yes
public = yes
writable = yes"

do i add the new_disk part under this?

thanks

---

### Post by dmizer on 2007-04-10
> **Rich930 said:**
> 
do i add the new_disk part under this?

thanks

yes ... add the "new_disk" part under that.  it will then look something like this:
```
[MyFiles]
path = /home/samba
browsable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = wardy
force group = wardy
avalible = yes
public = yes
writable = yes

[[COLOR="Red"]nameofshare[/COLOR]]
path = [COLOR="Red"]/path/to/newdrive[/COLOR]
browsable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = wardy
force group = wardy
avalible = yes
public = yes
writable = yes
```
you will have to change the red colored parts to match the needs of your computer.  the "nameofshare" can be ANYTHING you want, just avoid non ascii characters, as well as avoid using spaces.  "/path/to/newdrive" needs to point to where you have your second hard drive mounted.

save the file, and restart your samba server:
```
sudo /etc/init.d/samba restart
```
and you should be able to see two folders when you browse to wardy from your windows machine.

ps. if you're actually still using breezy ... please seriously consider an upgrade at least to dapper.  using breezy in ubuntu is the windows equivalent of using windows 98 as far as security is concerned.

---

### Post by Rich930 on 2007-04-13
> **dmizer said:**
> you will have to change the red colored parts to match the needs of your computer.  the "nameofshare" can be ANYTHING you want, just avoid non ascii characters, as well as avoid using spaces.  "/path/to/newdrive" needs to point to where you have your second hard drive mounted.

what do you mean by, where it is mounted? :P (im a real n00b at this lol)

and ok illl try ;)

thanks again

---

### Post by dmizer on 2007-04-15
> **Rich930 said:**
> what do you mean by, where it is mounted?
this means ... where you go to view the contents of the new drive.  or, if you went to: places > home ... where would you go next in order to get to your new drive?

if you're still having trouble, perhaps post the contents of this file: /etc/fstab

you'll have to be root to view this file, so something like this should work:
```
gksudo gedit /etc/fstab
```

>  :P (im a real n00b at this lol)
it's not necessary to apologize for being new.  many of us are.  i've only been at this for about a year, maybe a year and a half, and i still have so much to learn.

---

### Post by Rich930 on 2007-04-17
hi, thanks for your help, i will try this later.

:D :KS :popcorn:

---

### Post by Rich930 on 2007-04-17
YAY! IT WORKED!! finally, firstly i typed one of the "forced" words wrong, spelt it with an s without realising it  :P  lol!

then after creating random shares, i realsied my error, i can now wirte to my second hard drive thanks to you!

you've been a great help! thankyou so much!

cya round!

:KS 
:popcorn: 
:D 
:o 
:) 
:guitar:

btw, if you even need any help, i am quite good with hardware problems, just not much else, and especially in windows too!   :D

thanks again!

---

