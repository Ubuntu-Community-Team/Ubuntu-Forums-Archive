---
title: "tryingto connect to share drive from XP"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by cbwaters on 2008-07-05
I'm a noob trying to set-up an older PC to be a file storeage and back-up server.  I've downloaded the latest Ubuntu Server and have been more or less following this how-to:  [[URL="how-to"]http://www.howtoforge.com/ubuntu-home-fileserver-p3]("http://www.howtoforge.com/ubuntu-home-fileserver-p3")[/URL]
It's taken me days to get this far, but I think I have Samba configured, the drive formated and mounted, and (and I think this is a pretty cool achievement) I can control the server wirelesly with my laptop using putty.

What I can't so yet is map the network drive from XP.  I get past the username and password request but then it kicks me saying that the path isn't valid.

so... if I did
 mkdir /media/store
and
 chmod 777 /media/store
and 
 mount /dev/sdb1 /media/store
and edited fstab so that it mounts on restart...
and my server computer is named fileserver1

can anybody help me figure out what the heck I need to type into the boxes in XP to see the drive?

I suppose there's a way in the server to actually check whether the drive is there and set for sharing... 

Thanks,
Cory

---

### Post by sea_monkey987 on 2008-07-05
Check your /etc/samba/smb.conf for your windows share configuration.  You have to make sure that the path is to /media/store and /media/store is mounted.  Here is a sample share defined at the bottom of /etc/samba/smb.conf

```

[Ubuntu Docs]
path =/home/user1/Documents
read only = no
guest ok = no
valid users = user1

```
This will show up as "Ubuntu Docs" when you browse to your server from the windows box.  When you enter it the folder that you will see from your windows box will be identical to the /home/user1/Documents directory.

Make sure that "user1" has been added to samba using
```

sudo smbpasswd -ae user1

```

---

### Post by cbwaters on 2008-07-05
At the bottom of the smb.conf I have this:
```
[hda public hard disk]
comment = Public Folder
path = media/store
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = no group
```

And I think I have the password part sorted because I seem to be getting past the username and password query in XP.  It gets past that and then hangs because the path to the drive or folder is wrong.

Thanks,
CW

---

### Post by sea_monkey987 on 2008-07-05
> **cbwaters said:**
> At the bottom of the smb.conf I have this:
```
[hda public hard disk]
comment = Public Folder
path = media/store
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = no group
```

And I think I have the password part sorted because I seem to be getting past the username and password query in XP.  It gets past that and then hangs because the path to the drive or folder is wrong.

Thanks,
CW

It needs to be
```
/media/store
```
not
```
media/store
```

---

### Post by cbwaters on 2008-07-05
> **sea_monkey987 said:**
> It needs to be
```
/media/store
```
not
```
media/store
```

Good catch.  Fixed that but still no joy connecting to the server from the XP client.

Anybody care to take a stab?

Cory

---

### Post by sea_monkey987 on 2008-07-06
Are you still getting the message saying the path isn't valid or is it something else now?  Also, did you restart your samba server?
```
sudo /etc/init.d/samba restart
```

---

### Post by cbwaters on 2008-07-06
> **sea_monkey987 said:**
> Are you still getting the message saying the path isn't valid or is it something else now?  Also, did you restart your samba server?
```
sudo /etc/init.d/samba restart
```

yeah, I'm still getting that invalid path or folder not present message.  
I'm really not sure about the syntax or content of what I'm supposed to be typing in the windows box or even if I'm trying this in the right spot.  
I'm in "My computer/tools/map network drives."  You can type a path in the "folder" window there or click on "connect to a network drive" which gives you the "add network place" wizard.  That asks for the network address...

I don't really know what to type into either of those locations.

FWIW, in "add network place", if I click browse for folder/entire network/Microsoft Windows network/MShome I do see my fileserver but there aren't any folders under it to click.
 

I did restart samba though.

---

### Post by sea_monkey987 on 2008-07-06
Try this:
go to My Computer.  in the address bar, type in "\\servername\hda public hard disk" without the quotes.  Make sure you substitute the your ubuntu box's name for servername.  This is to check that the share is indeed browseable.  Report back with the results.

---

### Post by cbwaters on 2008-07-06
A couple times I got the password prompt but it doesn't get any farther than that.  "Windows cannot find \\fileserver1\hda public hard disk"
I substituted sda, sdb, hdb, and sdb1 (my partition) but the same results each time.  Ecxcept I never got the password prompt for anything but hda.

CW

---

### Post by sea_monkey987 on 2008-07-06
Well you have to use hda because that is part of the name you defined in the samba configuration file.  Since you are getting the password prompt, that means windows can indeed find it.  I'm running out of ideas but there are three more things:

1) From your windows box, when you go to \\fileserver1 (or whatever the name of your ubuntu fileserver is), do you see your 'hda public hard disk' folder?
2) Can you browse your 'hda public hard disk' folder from the ubuntu box itself?  If you have the desktop environment, try typing in "smb://localhost/hda public hard disk" in nautilus's location box.
3) Do you mind attaching your /etc/samba/smb.conf file?

EDIT : BTW, what did you put in your password prompt?  did windows also ask for the user or was "nobody" already selected for you.  I'm suspecting that "nobody" is supposed to be a guest account and it doesn't actually exist on your ubuntu server as a user you can log in as (which is why you are getting these problems).  Find a line beginning with "guest account" in your /etc/samba/smb.conf file.  Uncomment it and change the line to
```
guest account = nobody
```
Restart samba.  This should get rid of the password prompt.  I do not get the prompt when I do this.

---

### Post by cbwaters on 2008-07-06
OK. I added "browseable= yes" to the smb.conf and restarted samba. Now I can see and add the HDA public hard sisk to my network places.  Can't get into it though for permissions... but it's a start.

I'm using nano to edit the smb.conffile.. how would I copy/paste or attach the tile to this forum?

---

### Post by sea_monkey987 on 2008-07-06
I have one more suggestion.  Let's try making a new share in samba.  I'll post the lines I use that I know to work.  Please note that samba still enforces file permission so you will not have write permissions to /media/store without using chmod or chown.
```

[shareddocs]
path =/media/store
read only = no
guest ok = yes
valid users = nobody

```

Make sure "guest account = nobody" is there as described in my last post.

---

### Post by sea_monkey987 on 2008-07-06
> **cbwaters said:**
> OK. I added "browseable= yes" to the smb.conf and restarted samba. Now I can see and add the HDA public hard sisk to my network places.  Can't get into it though for permissions... but it's a start.

I'm using nano to edit the smb.conffile.. how would I copy/paste or attach the tile to this forum?

That is indeed great progress.  I think the invalid path issues are gone.  Only thing you need to do know is fix the credentials for samba.

Do you have a desktop environment installed on your ubuntu server (i.e. if you are writing to the forum from your ubuntu box then the answer is yes) or do you just have the terminal?

If you have the desktop environment installed then reply from the ubuntu server and click on the little paper clip on the reply to thread screen.  It's right beside the smiley face.  That'll open a new window where you can specify your file.

---

### Post by jbinc1 on 2008-07-06
cbwaters,

I was having the same issue that you are with the smb.conf file. Give this a try.

```
[Share]
   comment = Share
   path = /media/store
   valid users = user
   public = no
   writable = yes
   printable = no
   create mask = 0777

```Mine is now working properly.

---

### Post by cbwaters on 2008-07-06
That appears to work!
I think I've copied a file to it and everything!!!!
I just did ```
cd /media/store
ls
``` and I can see the file I copied there!!!
I'm pretty freaking excited.

Thanks sea_monkey!!! 
(that sounds weird)

> **sea_monkey987 said:**
> I have one more suggestion.  Let's try making a new share in samba.  I'll post the lines I use that I know to work.  Please note that samba still enforces file permission so you will not have write permissions to /media/store without using chmod or chown.
```

[shareddocs]
path =/media/store
read only = no
guest ok = yes
valid users = nobody

```

Make sure "guest account = nobody" is there as described in my last post.

---

### Post by sea_monkey987 on 2008-07-06
you're welcome.  If that is all, could you please mark the thread as [solved]

---

