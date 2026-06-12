---
title: "permissions on shared files"
date: 2014-11-17
forum: Networking &amp; Wireless
---

### Post by ghostofzuul on 2014-11-17
hello.

just upgraded to 14.04 lts. 

when i move files over my LAN from my mac to my linux box there is a lock on the files in Ubuntu. Media files in this case.

I can watch the media but I can not delete or move from the ubuntu machine. Only from the mac. When I check permissions it says you are not the owner or some such.

Any ideas? In the past i've been able to move files freely... modify files from any machine on network. Now i've got all these pesky locks on everything.

Thanks.

---

### Post by texpat on 2014-11-17
If the problem is due to ownership you can go to a terminal and type:

(The following changes ownership of all files in a directory, substitute [FONT=Courier New]/directoryname[/FONT] for [FONT=Courier New]filename[/FONT] if you want to do this for files)

```
sudo chown yourusername /mediadirectory
```

if there are subdirectories, type 

```
sudo chown -R [...]
```

---

### Post by houstonbofh on 2014-11-17
You are connecting to the Ubuntu server on the Mac as a different user than the one that you log into Ubuntu with.  If you use the same user, this problem goes away.  If that will not work you need to look into shared groups and umask to ally multiple users to have full access.

Right click on the locked file and go to properties to see what the user and group is.

---

### Post by ghostofzuul on 2014-11-17
interesting you should mention that... 

in the past i've been able to "connect as" a registered user when logging onto my Ubuntu machine from the mac.

Since i've upgraded to 14.04 I have not been able to. I know I am using the correct username and password and it will only connect to the ubuntu machine as "guest." 

I have given all the proper permissions to the folders on my Ubuntu machine for sharing... and as I mentioned I can read and write to the Ubuntu machine from the mac. And I can read the files from the ubuntu machine. I just can't modify those files at all (move delete). 

Any idea why I can no longer connect to the ubuntu machine as a registered user from the mac?

Thanks!

---

### Post by ghostofzuul on 2014-11-17
> **texpat said:**
> If the problem is due to ownership you can go to a terminal and type:

(The following changes ownership of all files in a directory, substitute [FONT=Courier New]/directoryname[/FONT] for [FONT=Courier New]filename[/FONT] if you want to do this for files)

```
sudo chown yourusername /mediadirectory
```

if there are subdirectories, type 

```
sudo chown -R [...]
```

the permissions on all the folders that i have marked as local shares are fine. 

the individual files that i moved from the mac to the ubuntu machine say:

owner: "nobody" and at the bottom it says "you are not the owner so you cannot change these permissions"

group: "nogroup"

thanks!

---

### Post by texpat on 2014-11-18
That's why I suggested using '[FONT=Courier New]**sudo**[/FONT]...' 

You should be prompted for your password and then the command ist executed as root.

---

### Post by Morbius1 on 2014-11-18
> **ghostofzuul said:**
> in the past i've been able to "connect as" a registered user when logging onto my Ubuntu machine from the mac.

Since i've upgraded to 14.04 I have not been able to. I know I am using  the correct username and password and it will only connect to the ubuntu  machine as "guest." 
If you are able to connect to the share as guest then your share isn't requesting credentials. The default user name for the guest in Samba is "nobody" and the group is "nogroup".
> Any idea why I can no longer connect to the ubuntu machine as a registered user from the mac?
Assuming you have any shares that required credentials you either don't have the mac user as a linux user and / or you didn't add him to samba:
```
sudo smbpasswd -a mac-user-name
```

---

### Post by Morbius1 on 2014-11-18
***

---

### Post by ghostofzuul on 2014-11-20
> **Morbius1 said:**
> If you are able to connect to the share as guest then your share isn't requesting credentials. The default user name for the guest in Samba is "nobody" and the group is "nogroup".

Assuming you have any shares that required credentials you either don't have the mac user as a linux user and / or you didn't add him to samba:
```
sudo smbpasswd -a mac-user-name
```

adding the user fixed the problem! thanks!

the locks all disappeared from the files when i did that and now i can modify files moved over from the mac. 

but this scenario has left me curious. in the past... going back to 8.04 all i've had to do is right click on the file go to properties>sharing and then click the box to share the folder. then when i would log in from my mac and "connect as" i would just connect with the username and password of the ubuntu machine. i never had to ad a user before. any idea why i did this time? 

also... and maybe for another post... from my "new" ubuntu machine i can see the 2 macs on my network but i can't see the "old" ubuntu machine. same when on the old machine. can see the macs but not the new machine... got me vexed....

thanks again.

---

### Post by Morbius1 on 2014-11-21
> but this scenario has left me curious. in the past... going back to 8.04  all i've had to do is right click on the file go to  properties>sharing and then click the box to share the folder. then  when i would log in from my mac and "connect as" i would just connect  with the username and password of the ubuntu machine. i never had to ad a  user before. any idea why i did this time? 
There is a package ( libpam-smbpass ) that automatically adds a local Linux login user to the samba password database and makes the local login password and the samba password match. It could be that you installed this package before or was installed for you when you first invoked nautilus-share. I always remove the package if it got installed somehow since i want to control which samba password is used not the system.
> also... and maybe for another post... from my "new" ubuntu machine i can  see the 2 macs on my network but i can't see the "old" ubuntu machine.  same when on the old machine. can see the macs but not the new  machine... got me vexed....
Since this is Linux to Linux can the old machine ping the new machine by an mDNS qualified host name:

Let's say the host name of the new machine is "newmachine". From the old machine run:
```
ping newmachine.local
```
[COLOR=#0000cd]*This requires port 5353 be open and the following service be running on both machines:*[/COLOR]
```
sudo service avahi-daemon start
```
[COLOR=#0000cd]*And don't forget the ".local" at the end.*[/COLOR]

If a ping that way is successful you can run this command from the old machine:
```
nautilus smb://newmachine.local
```
When nautilus opens up to that location bookmark it: Bookmarks > Add bookmark.

Then it will show up on the side panel sorta kinda like a "mapped drive" did on Windows or a server does under "Shared" in Finder.

[COLOR=#0000cd]*Side note*[/COLOR]: This will work with bookmarking an OSX machine as well although from your description it appears to be a non issue.

---

### Post by ghostofzuul on 2014-11-21
> **Morbius1 said:**
> There is a package ( libpam-smbpass ) that automatically adds a local Linux login user to the samba password database and makes the local login password and the samba password match. It could be that you installed this package before or was installed for you when you first invoked nautilus-share. I always remove the package if it got installed somehow since i want to control which samba password is used not the system.

Since this is Linux to Linux can the old machine ping the new machine by an mDNS qualified host name:

Let's say the host name of the new machine is "newmachine". From the old machine run:
```
ping newmachine.local
```
[COLOR=#0000cd]*This requires port 5353 be open and the following service be running on both machines:*[/COLOR]
```
sudo service avahi-daemon start
```
[COLOR=#0000cd]*And don't forget the ".local" at the end.*[/COLOR]

If a ping that way is successful you can run this command from the old machine:
```
nautilus smb://newmachine.local
```
When nautilus opens up to that location bookmark it: Bookmarks > Add bookmark.

Then it will show up on the side panel sorta kinda like a "mapped drive" did on Windows or a server does under "Shared" in Finder.

[COLOR=#0000cd]*Side note*[/COLOR]: This will work with bookmarking an OSX machine as well although from your description it appears to be a non issue.

all i had to do was ping the "new" machine and open a nautilus share and bookmark it as per your instructions and it worked great! first try!

i really appreciate your help and timely responses. thanks again. :guitar:

---

