---
title: "Sharing Files amongst users"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by steviefordi on 2011-09-01
This is going to seem like a stupid question to more experienced users out there...

I want each user on my laptop to share the same Music folder. I was going to create /usr/share/Music (to store the music in) and make ~/Music a symlink to that folder for each user.

Is this the right way to achieve my goal, or is there a more technically correct way of doing it?

---

### Post by Morbius1 on 2011-09-01
A symlink is as good a way as any other but I wouldn't have placed the share in "/usr/share" although I have to admit that would be the intuitive choice for something that is shared between users. That's a system directory so I would have put it in say ... /home/Music but that's up to you.

You will have to do one thing though to make this work. You will have to change permissions on the target folder to allow all users to access it. For example:

```
sudo chmod 0777 /usr/share/Music
```That will allow everyone to add to and delete files from that folder.

Or this:
```
sudo chmod 1777 /usr/share/Music
```The "1" is called a "sticky bit" and this will allow everyone to add to the folder but only the owner of the file ( or root ) can delete it.

---

### Post by steviefordi on 2011-09-01
Thanks Moribus1. I think I'll go with your suggestion and use /home, that seems to make sense to me. I've been using Ubuntu for a few years now and still struggle with the intended purpose of some of the pre-defined directories. Proper use of /usr/share is now clear to me.

---

### Post by steviefordi on 2011-09-02
Ok, previously I marked this thread as solved but then realised I had another problem when I implemented the solution.

To recap:
[LIST]
[*]Created /home/Music
[*]Moved all music from each users home folder into it
[*]Ran chmod 777 on all directories in /home/Music
[*]Ran chmod 666 on all files in /home/Music
[*]Changed ~/Music to a symlink pointing at /home/Music for all users
[/LIST]

All seems well, but if I rip a CD to this folder, other users only have read access - ie. I am the owner and group owner, and the permissions are 644 (rw-r--r--).

Obviously I can chmod the ripped files, but how do I make the permissions 666 happen naturally?

---

### Post by fdrake on 2011-09-02
> **steviefordi said:**
> Ok, previously I marked this thread as solved but then realised I had another problem when I implemented the solution.

To recap:
[LIST]
[*]Created /home/Music
[*]Moved all music from each users home folder into it
[*]Ran chmod 777 on all directories in /home/Music
[*]Ran chmod 666 on all files in /home/Music
[*]Changed ~/Music to a symlink pointing at /home/Music for all users
[/LIST]

All seems well, but if I rip a CD to this folder, other users only have read access - ie. I am the owner and group owner, and the permissions are 644 (rw-r--r--).

Obviously I can chmod the ripped files, but how do I make the permissions 666 happen naturally?


edit: same as Morbius1

Another solution would be to run a cron schedule every 10 min to change the permissions of the folder. But that's too time/resource consuming.

---

### Post by Morbius1 on 2011-09-02
When I posted my answer I figured it didn't really matter that the individual files would end up with 644 permissions since as a music file I didn't think anyone would write to one.

You've got a couple of options but one I would suggest is the following:

[1] Install bindfs
```
sudo apt-get install bindfs
```[2] Temporarily re-mount the /home/Music file using bindfs to make sure it's what you want:
```
sudo bindfs -o perms=0666:+X /home/Music /home/Music
```What should happen is this:

Every folder , current and newly added, will have permissions of 777.
Every file, current or newly added, will have permissions of 666.

[3] Make sure the symlink still works.

[4] To make that happen at boot time I would suggest creating your own upstart job:

* Create an upstart file:
```
gksu gedit /etc/init/music-bindfs.conf
```* With this content:
```
# Create a common Music directory using bindfs
description "Common Music Directory"

start on stopped mountall

script
  bindfs -o perms=0666:+X /home/Music /home/Music
end script
```* Save the file and remove the temporary manual mount:
```
sudo umount /home/Music
```* Then run the following command to start the upstart job:
```
sudo initctl start music-bindfs
```[COLOR=Blue]*Note: You can also add a line to fstab but I have been having serious problems with this traditional method in Ubuntu because of a bug in mountall. I would not recommend this method but if you want to try it the syntax in fstab looks like this:*[/COLOR]
```
bindfs#/home/Music    /home/Music    fuse    perms=0666:+X    0    0
```

---

### Post by btindie on 2011-09-02
The primary group a user is assigned to under Ubuntu is the same as the username. To get around this you can create a group that is used for your music that all users are a member of. That group then gets assigned to the music directory and the SETGID bit is set so that all new files created there inherit the group.

First you need to update the umask value for users so edit /etc/profile and remove the umask setting line at the bottom and replace it with:
```
if [ $UID -gt 199 ] && [ "`id -gn`" = "`id -un`" ]; then
    umask 002
else
    umask 022
fi

```That will give all normal users a default umask of 002 meaning new files will have the permissions rwxrwxr-x.

Next stage is to decide which group name you want to use, you could either use the group 'users' or create a new group 'music'
```
sudo groupadd -r music
```Every user on the system would have to be a member of this group to be able to read/write to the directory
```
for i in user1 user2 user3 user4; do
sudo usermod -a -G music $i
done
```Next, update the permissions on your Music directory
```
sudo chgrp -R music /home/Music
sudo find /home/Music -type f -exec chmod 0664 '{}' \;
sudo find /home/Music -type d -exec chmod 2775 '{}' \;
```You'll have to logout and back in again for the umask change to take effect. You can check that you've got the correct umask value (002) by typing umask from the terminal.

---

### Post by steviefordi on 2011-09-02
Thanks to both btindie and Morbius1 for taking time out to answer my query.

After researching both solutions, I'm going to try using bindfs. Although I liked the ideas put forward by btindie, I'm not that comfortable changing the umask for all files created in all directories. It also appears that this is the sort of situation bindfs is built for.

I really need to thank you guys for your time because you opened my eyes to things that inspired some google based self-learning. 

Before, umask was something I was only vaguely aware of - now I know what it is. bindfs looks like a really good tool, and flagging the setgid bit on directories is a technique I will use in the future.

Cheers
Steve.

---

### Post by Morbius1 on 2011-09-02
What btindie has posted is the classic way this is done. I tend to go a little outside the box :)

The classic way does have a flaw in it though. The setgid bit takes care of group membership as advertised but the "umask 002" only corresponds to new file creation. 

So if I have a file sitting at /home/morbius/Music/test.mp3 it will have:
owner:group = morbius:morbius
mode = 644. 

When I move it to /home/Music using the classic method it will have:
owner:group = morbius:music
mode = 644

Group did in fact change but nothing altered the existing permissions on the original file.

With bindfs the original file could be owned by root with permissions of 600 and yet it will appear to all users to have permissions of 666. 

BTW, there's nothing really wrong with changing umask to 002. For every new file outside a folder with the setgid bit set it will still have owner:group = user:user. Just make sure you don't set umask to 000.

---

### Post by azertyh on 2011-09-02
hello,
see my post in this thread [http://ubuntuforums.org/showthread.php?t=1580277&highlight=partage](http://ubuntuforums.org/showthread.php?t=1580277&highlight=partage)

---

### Post by Morbius1 on 2011-09-03
@azertyh

On your link you have this statement:
> in this case, the folder /home/Partage is sharing between john and mary. john and mary can create, modify, copy and delete files in this folder.They can do most of those things but not all. John and Mary can indeed create, copy, and delete any file in that directory. John and Mary can modify any new file either one of them creates in that directory or copies to that directory. But they cannot modify any of the original files they created before the "umask=002" change that they copied into that folder except their own. Nor will they be able to edit any file copied to it from a removable disk - depending on it's permissions.

If John has an old file in /home/john/Downloads it will have permissions of 644. After he copies it to /home/Partage it will still have have permissions of 644. Mary can move it, copy it, and even delete it but she cannot modify it directly. Ownership changes with a copy but permissions do not.

---

### Post by steviefordi on 2011-09-06
I implemented the bindfs solution suggested by Morbius1 and it's working like a charm.

The only thing I did differently was to create a "music" group and add all desktop users to it. Then I employed the setgid bit on the folder /home/Music to cascade the group owner of music down the tree. I also mounted the folder with permissions 0664 instead of 0666. I know I didn't need to do any of this, but for the benefit of clarity I wanted to.

I had a quick look at azertyh solution, which appears to be the same "classic" solution posed by btindie but implemented differently - umask affecting all users, not just uid of 200+.

I didn't use this as changing the umask for the benefit of one folder seemed a little like overkill to me.

Thanks to all who posted for your input....

---

### Post by Morbius1 on 2011-09-06
Just for completeness sake, if you wanted to incorporate a group into the bindfs mount the syntax would change from this:
```
bindfs -o perms=0666:+X /home/Music /home/Music
```To this:
```
bindfs -o perms=0664:+X,group=music /home/Music /home/Music
```Only members of the music group will have write access.
All files will save with: owner:group = username:music

It's the bindfs way of doing a setgid.

---

