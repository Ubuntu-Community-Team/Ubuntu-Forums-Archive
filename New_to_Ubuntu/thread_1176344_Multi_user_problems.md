---
title: "Multi user problems"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by John Hale on 2009-06-02
Hi I have ubuntu 8.04 and have myself and my mother as users, and the are some weird sharing issues for example if I log on as her and read a cd then log in as me and try to eject that cd I get I cannot unmount the device only ann can or if I copy files to a memory stick in her account I then can't read it in mine as I don't have the permissions, sometimes she wants to do something via my account like edit a document created in her account but also doesn't have the permissions is there a way to remove these?

Thanks

John

---

### Post by MichaelSammels on 2009-06-02
This is because the drive has been mounted by that user. Try installing Storage Device Manager:

```
sudo apt-get install pysdm
```
```
sudo pysdm
```

If you have a look at the options menu, you see options for owner/who can mount it, etc.

Good luck!

---

### Post by Cypher on 2009-06-02
You are probably familiar with Windows' multi-user environment where the enforcement of permissions for local users is a laxer than on Linux. That being said, by default when files are created, they are set to be read/write by the owner and read by others in your group or the world.

This is by design to ensure that only the owner of a file is allowed to modify the contents, while others can read the contents.

---

### Post by John Hale on 2009-06-02
Sorry cypher I sort of get that, but would really like to know how to remove it, as the only reason we have seperate accounts other than emails is that I've got a 13 year old nephew who will screw around with computer unless they are password protected

---

### Post by Cypher on 2009-06-02
One of the ways to circumvent this user-level permission restrictions is to modify the "umask" for file creation.

By default the umask file is set to 0022, which means that any files created are owned by the user and world readable as I said in the previous post.

If you change the umask to 0000, then the files will be owner and world read/write.

So edit the file ~/.bashrc and add the line "umask 0" and then logout and log back in. Open a terminal and type "umask" and it should show 0000, if so, if you create any new file, it will be able to be modified by any other user.

You can make subtle changes here. Set the umask to 0002 such that only the world can read, but people in your group can read/write. Then you can put yourself and your mother in the same group, while leaving your nephew in a different group.

---

