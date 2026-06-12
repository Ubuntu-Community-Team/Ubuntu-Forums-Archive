---
title: "Recreate 124 user accounts"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by theller on 2010-08-20
I have 124 user accounts I want to reinstall. Is there a way to not do this without typing in each user?

---

### Post by uRock on 2010-08-20
> **theller said:**
> I have 124 user accounts I want to reinstall. Is there a way to not do this without typing in each user?
I asked pretty much the same question recently and the only answer I got was to move all of the Home folders to another location, create the accounts, then merge the Home folders and chown them, which I think is way too much work for this number of accounts.

---

### Post by Iowan on 2010-08-20
Moved to new thread.

---

### Post by Vaphell on 2010-08-20
it's not too much work, just write a script to do all steps necessary in a loop

let's assume that your users have home dirs named with their names
copy /home to a new system

```

#!/bin/sh

for user in `ls -I lost+found old_home`
do
  sudo useradd $user
  sudo cp -r old_home/$user /home/$user
  sudo chown -R $user:$user /home/$user 
done

```

for every dir in a old_home dir (except lost+found that can be there) create a user with appropriate name, copy his dir to proper location (or move if you feel like it), change ownership recursively
If you want you can simply put everything in its final location in home (so ls ... /home instead of ls ... old_home) and reduce script to useradd+chown, with no cp/mv required

this script is written on a knee but it should create all homes and set ownership. Passwords would need sorting out though. I am sure it can be automated too but i don't know much about passwords in the system and don't feel like finding out :-)

edit: find replaced with simple ls

---

### Post by Seq on 2010-08-20
I do this a fair amount. If you're migrating users from one system to another (i.e. hardware replacement, etc), there are a few things you need:

[LIST]
[*]/home directories
[*]/etc/passwd (user) entries
[*]/etc/shadow (password) entries
[/LIST]

[LIST=1]
[*]Move all the relevant user directories from the /home on the old server to /home on the new server. Keep permissions.
[*]Pick out all the legitimate users from /etc/passwd. On Ubuntu, these users have a uid >= 1000. Other distros and operating systems may be >= 500. Append all those users to the end of your new /etc/passwd file
[*]Do the same thing you did for /etc/passwd, but for /etc/shadow.
[/LIST]

This assumes you haven't added new users to the new system that would potentially cause an overlap in uids.

---

### Post by theller on 2010-12-03
Thanks for the replies, my coworker said she used webmin and a spreadsheet. We left both servers running and users moved what they wanted to keep.

---

