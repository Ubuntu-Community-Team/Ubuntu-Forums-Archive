---
title: "Setting up a file server, need help"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by seepage87 on 2007-12-28
I've built a file server (currently using a full ubuntu install) and have set up Samba to let all my roommates (all windows users and not tech savy) access the share without having to jump through any permission hoops.  I have one problem that I need to fix and want to accomplish one task.

The problem:
If I move or create files in the shared directory then  my roommates lose permission even to read those files.  I'd like them to be able to rwx them so they can use them and help maintain them.  Basically, I need to know how to make sure everything under /mnt/shared always has full permissions for people accessing them within the network.

The task:
I want to set up my server so any of my roommates can access it as a network drive over the internet.  I think I basically want to set up an FTP server and be able to have them map a network drive on their laptops to the server.  I don't know what steps need to be taken to do that, or what FTP server program to use, so advice would be great.  Also the permission thing would apply here to, but I guess all the users would belong to the same group and I'd just need to make sure everything under /mnt/shared belongs to that group.  I think I have that part right.

Still a little of a noob to this whole linux server thing, so even a point in the right direction would help greatly.

thanks

---

### Post by seepage87 on 2007-12-28
Anyone?

---

### Post by P5ych0Gigabyte on 2007-12-28
I've had the same problem with my samba server and would like to see an answer as well. So heres a little bump for you. :)

---

### Post by banjo man on 2007-12-30
I as well would like to see this resolved...

---

### Post by seepage87 on 2008-01-07
I have a theory that my Bittorrent method was breaking Samba.  I was downloading on one computer and saving to the Samba server.  Since I stopped it hasn't crashed.

---

### Post by jetsam on 2008-01-08
You can get Samba to force permissions by adding the following under your share in your smb.conf:

```
create mask = 0777
force create mode = 0666
force security mode = 0666
directory mask = 0777
force directory mode = 0777
force directory security mode = 0777
```

What these properties do:[LIST]
[*]create mask = 0777:  Allows samba clients to set full permissions on files.
[*]force create mode = 0666: Forces files created by some Samba clients (windows) to have read and write permissions set for user, group and others. 
[*]force security mode = 0666: Forces files created by some other Samba clients (specifically cifs) to have full read and write permissions.
[*]directory mask = 0777:  Allows samba clients to set full permissions on directories.
[*]force directory mode = 0777: Forces directories created by some Samba clients (windows)  to have read, write, and execute permissions set for user, group and others. 
[*]force directory security mode = 0777: Forces directories created by some other Samba clients (specifically cifs) to have full read, write, and execute permissions.
[/LIST]

These properties only work for files created through Samba.  If you do anything locally on the server itself, you'll be using normal Unix permissions and you'll have to remember to set the permissions manually.  

You'll need to restart Samba after you make these changes for them to take effect.

It's sort of a blunt instrument, but I think it will work for what you want and your roommates can just use normal Windows filesharing.

---

### Post by andguent on 2008-01-08
For remote access outside of the building, you might want to check out WinSCP. 

If you can get SSH access from outside the apartment, you should be functional. Just port forward some non standard port through your router to your server for SSH access. WinSCP is a nice GUI that will allow users to get to any directory that their UNIX side account gives them access to.

As an addition to jetsam above, another blunt force option is:
force user = root

This will allow all users to access basically all files on the share as root, but no root access to anything else. This is only advised for low security uses, or if you are 100% certain that your initial methods of authentication are strong. Using this in combination will the create mask options above will allow later WinSCP users to still access the files too (and delete them if they really feel like it).

---

### Post by Lostincyberspace on 2008-01-08
You could make a script that will automatically do it every time you login and off or something similar.

---

### Post by seepage87 on 2008-01-09
Thanks, I'll try those when I get home tonight.

I'm not sure about wanting to use WinSCP for remote access though.  The hope is to be able to mount it as a network drive and stream content.  My experience with winSCP is that one would have to copy the content first then play it.  Also, the less software I can get in the way of the people who will be accessing the share remotely the better.  I don't mind, but I'm fairly certain my girlfriend isn't going to want to use an unfamiliar program.

---

