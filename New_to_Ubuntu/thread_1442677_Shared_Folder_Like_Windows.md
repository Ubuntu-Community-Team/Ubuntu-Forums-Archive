---
title: "Shared Folder Like Windows?"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by Duck86 on 2010-03-30
Is there an option on Ubuntu 9.10 to have a shared folder between profiles like there is on widows? If so, where is it/how do you set it up?

---

### Post by spartan_87 on 2010-03-30
Go to System -> Administration -> Users and Groups -> Manage Groups. Create a new group and put you and any other users you want to share with in it.

Then create a folder somewhere, like on your desktop. Right click on it and go to Properties -> Permissions. Under Group select the group that you just created and then give it the read/write permissions you want.

Now all the users in that group should be able to access the folder by browsing to the location you put the folder.

---

### Post by coffeecat on 2010-03-30
> **spartan_87 said:**
> Now all the users in that group should be able to access the folder by browsing to the location you put the folder.

I may be wrong - I haven't tried this yet - but if you put the shared folder in, say, fred's desktop, it would be /home/fred/Desktop/shared-folder. But if Bill, whose ~ is /home/bill, tried to navigate there, he might get an access denied at the /home/fred stage when double-clicking on fred's Desktop folder.

One slightly more elegant solution, but more fiddly to set up, would be to put 'shared-folder' directly in /home. Adjust permissions accordingly, and then set up symlinks to 'shared-folder' in /home/fred and /home/bill. And, of course, you would need sudo rights to create and chmod the shared-folder in /home.

@Duck86, if that last bit is beyond you, and you need to try it, just post back.

---

### Post by spartan_87 on 2010-03-30
[QUOTE=coffeecat]I may be wrong - I haven't tried this yet - but if you put the shared folder in, say, fred's desktop, it would be /home/fred/Desktop/shared-folder. But if Bill, whose ~ is /home/bill, tried to navigate there, he might get an access denied at the /home/fred stage when double-clicking on fred's Desktop folder.[/QUOTE]

Yeah your right, I didn't think about that. So yeah the /home directory would work better. Thanks.

---

### Post by Duck86 on 2010-03-30
Could I get a step by step on that last post please?

Many Thanks!

---

### Post by coffeecat on 2010-03-30
> **Duck86 said:**
> Could I get a step by step on that last post please?

Many Thanks!

I **will** get back to you on that, but I need to log off for a few hours. Perhaps some other kind soul will take you through the steps first but, if not, I'll post something. :)

---

### Post by charliehorse55 on 2010-03-30
Open a terminal and type these commands. You'll need to type your password when it asks you.

Lets go the directory we will be working on:
```
 
cd /home

```


Make the directory to which you will put the shared files.
```

sudo mkdir Shared

```
NOTE :You can replace the word "Shared" with the name of your folder

Allow anyone to modify the folder
```

sudo chmod 777 Shared

```


That should be all you need to do.

---

### Post by spartan_87 on 2010-03-30
> **charliehorse55 said:**
> Allow anyone to modify the folder
```
sudo chmod 777 Shared
```

This will do exactly what charliehorse55 said "Allow anyone access to the shared folder." Which is fine if thats what you want. But if you want to just allow certain users you can create a group and add the users you want to the group, like I showed in my first post.

Then give the group ownership of the share.
```
sudo chown :group-name -R /home/Shared
```

Then set the permissions so the owner and only users that are in that group can access it.
```
sudo chmod 770 /home/Shared
```

---

### Post by coffeecat on 2010-03-30
I think the others have covered it all except the symlink bit, which is the icing on the cake! :wink:

I'll assume that the administrator account is "fred" and the other account is "bill", that you want both fred and bill to have symlinks and that you've added both fred and bill to the "group-name" group. Substitute your names in the instructions below as appropriate.

Log in to the "fred" administrator account.

1 - Set up fred's symlink.

```
sudo ln -s /home/Shared /home/fred/Shared
sudo chown fred:group-name /home/fred/Shared
```2 - Set up bill's symlink.

```
sudo ln -s /home/Shared /home/bill/Shared
sudo chown bill:group-name /home/bill/Shared
```Now both Fred and Bill will see a symlink folder in their respective homes which link to the contents of the "Shared" folder. Makes it a bit easier finding the folder.

Would spartan_87 and charliehorse55 be so kind as to double-check the above to make sure I haven't forgotten something or got something wrong?

---

### Post by Morbius1 on 2010-03-30
It all depends on your definition of "Shared"

Let's say you create a directory at /home/Shared and do a sudo chmod 0777 /home/Shared.

Both John and Mary will be able to add and delete files to that directory. But if John creates and saves a john.txt file to that directory it will have permissions of 0644. John has full access but Mary can only read. Mary can read the file, edit it, and save it to mary.txt but not to john.txt. That may very well be the way you want it to work since you'll be able to keep track of who's doing what to who. But if you want Mary to write to and save a john.txt something else is required.

One way to do this is with BINDFS:


1. install bindfs:
```
sudo apt-get install bindfs
```2. create a hidden & a visible directory for the files:
      ```
sudo mkdir /home/.Shared
sudo mkdir /home/Shared
```3. edit the fstab file:
      ```
gksu gedit /etc/fstab
```4. add a new entry at the end of the file:
```
bindfs#/home/.Shared    /home/Shared    fuse    group=plugdev,perms=g=rwx
```5. mount the filesystems menitioned in fstab:
```
sudo mount -a
```6. move the files you want to share in the /home/Shared directory

In case you're wondering about the group=plugdev, all local users are members of the plugdev (46) group by default. When Mary and John save a file it will save with permissions of 0664 and group ownership = plugdev.

I found this technique together with a more detailed example from a post by [COLOR=Blue]**sisco311**[/COLOR] here: [http://ubuntuforums.org/showpost.php?p=8983087&postcount=25](http://ubuntuforums.org/showpost.php?p=8983087&postcount=25)

---

