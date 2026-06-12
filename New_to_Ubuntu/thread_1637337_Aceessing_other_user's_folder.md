---
title: "Aceessing other user's folder"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by jaezcurra on 2010-12-04
Hi, I have created a 2nd user for the first time in my computer running Maverick.
I would like to let this user see (read, but not write) some of my Home folders.
How can I achieve this?

---

### Post by krishnandu.sarkar on 2010-12-04
For all folders : chmod -R a+r /home/user/

And for specific folders you need to mention them like /home/user/Videos

---

### Post by jaezcurra on 2010-12-04
Thanks a lot.  And how can I make this appear in his own Nautilus?
I mean, creating an access in his Videos folder pointing to my Videos folder?

---

### Post by jplo on 2010-12-04
Make a link by clicking on the folder/file you wish to link to. Then go to Edit>Make Link

This will create a link. Then copy/paste the link into the folder you want it to be. 

take a look at nautilus help; 6.6.13

---

### Post by krishnandu.sarkar on 2010-12-04
Or if you want it in geeky way then the syntax is:
ln -s /path/to/real/file /path/to/non-existant/file

To be more precise ln -s /home/user/Videos /home/user1/Vidoes or vice-versa for the reverse

---

### Post by SeijiSensei on 2010-12-04
Unix groups are designed precisely for this.  

Create a group for yourself and the other user, then grant the group read-only rights to your home directory.  Here's a quick overview:

```

sudo groupadd mygroup
sudo usermod -G mygroup -a yourusername
sudo usermod -G mygroup -a otherusername
cd /home/yourusername
chgrp -R mygroup .
chmod g+r -R .

```

This creates a group called "mygroup" and places the two usernames in it.  Then it runs "chgrp" to make this the group that owns files in /home/yourusername.  The "chmod" command enables members of the group to read the files in your directories and subdirectories.

You can see what groups a user belongs to with the "groups username" command.

---

### Post by jaezcurra on 2010-12-04
> **krishnandu.sarkar said:**
> Or if you want it in geeky way then the syntax is:
ln -s /path/to/real/file /path/to/non-existant/file

To be more precise ln -s /home/user/Videos /home/user1/Vidoes or vice-versa for the reverse

Well, it does not work at all, as clicking the symbolic link from the 2nd user's Videos folder gets a "broken link" message ¿?¿?¿?¿?

---

### Post by jaezcurra on 2010-12-04
> **SeijiSensei said:**
> Unix groups are designed precisely for this.  

Create a group for yourself and the other user, then grant the group read-only rights to your home directory.  Here's a quick overview:

```

sudo groupadd mygroup
sudo usermod -G mygroup -a yourusername
sudo usermod -G mygroup -a otherusername
cd /home/yourusername
chgrp -R mygroup .
chmod g+r -R .

```

This creates a group called "mygroup" and places the two usernames in it.  Then it runs "chgrp" to make this the group that owns files in /home/yourusername.  The "chmod" command enables members of the group to read the files in your directories and subdirectories.

You can see what groups a user belongs to with the "groups username" command.

Did it, but cannot access folders within first user's Home from 2nd user session.

---

### Post by jaezcurra on 2010-12-04
Briefly: whatever I do, I always get that "broken link" message :confused:

---

### Post by krishnandu.sarkar on 2010-12-05
> **jaezcurra said:**
> Briefly: whatever I do, I always get that "broken link" message :confused:
Using GUI also?? Looks like it's another problem, did you assigned necessary permission??

---

### Post by jaezcurra on 2010-12-05
Well, the folder belongs to a specific group created only for this purpose and whose members are both users.
The folder belongs to the 1st user and the group members have Read permission (as I just want that the 2nd user could only see the contents of the folder).

---

### Post by SeijiSensei on 2010-12-05
Sounds like the link is wrong.  If you look at the directory in a terminal window and see a flashing link, it points to a non-existent target.

Another possibility concerns the permissions on /home/user1 and /home/user2.  If they don't have at least 0750 permissions, assuming they are in the same group, one user won't be able to see the contents of the other's directory at all.

---

