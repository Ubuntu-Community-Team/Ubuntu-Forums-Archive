---
title: "not understanding jailbash/apparmor"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by judderwocky on 2011-06-10
I made a link to /bin/bash , /usr/local/bin/jailbash  , and set it as the shell for my guest account. 

I then created the appropriate apparmor app, and threw it into the /etc/apparmor.d/usr.local.bin.jailbash 

I reloaded all the profiles, and ended up restarting.

If I log into the desktop as my guest user, none of the profile restrictions are in effect

If I open up a terminal and do "su guest" 

All of the appropriate profile restrictions are in place. 

Does jailbash only work for command line interface? is there anyway to completely limit that user from those areas of the computer regardless of how they log on?

thanks

---

### Post by smurphy_it on 2011-06-10
How does the user logon ?  Remotely or at the computer scree ?

You could setup a chroot jail.  If it's remotely, you could bypass the chroot jail and just use rssh (assuming they login to get a shell that is).

---

### Post by judderwocky on 2011-06-10
> **smurphy_it said:**
> How does the user logon ?  Remotely or at the computer scree ?

You could setup a chroot jail.  If it's remotely, you could bypass the chroot jail and just use rssh (assuming they login to get a shell that is).

at the desktop ... 

when i'm logged in as my administrator account, and I do su in the commandline, all the jailbash restrictions are in effect... 

i just don't understand why the jailbash profile doesn't restrict them when that user logs in as a regular desktop user. 

commandline it all seems to work fine... its just when unity opens a program it doesn't seem to have the jailbash restrictions at all...

im just really confused because I thought the apparmor profile on jailbash completely limited the access a user had to the computer, regardless of how they are logged in....

could I have set it up incorrectly? or am i missing something conceptually?

thanks for helping :)

---

### Post by smurphy_it on 2011-06-14
I would assume you are referring to logging into the desktop, via xwindows.  In which case, I can't see how that user would be restricted.  They would have to be restricted within xwindows, and potentially within the application(s).

The bash (restrictions) shouldn't come into play until you open a command prompt.

The apparmor configuration (which I haven't played with much) is typically per application.  So you would have to limit each application you want restricted.

---

### Post by judderwocky on 2011-06-16
> **smurphy_it said:**
> I would assume you are referring to logging into the desktop, via xwindows.  In which case, I can't see how that user would be restricted.  They would have to be restricted within xwindows, and potentially within the application(s).

The bash (restrictions) shouldn't come into play until you open a command prompt.

The apparmor configuration (which I haven't played with much) is typically per application.  So you would have to limit each application you want restricted.

thanks, I think I see now...

---

### Post by jtarin on 2011-06-16
If you want to restrict a user to certain applications only, you could by the [usage of permissions and groups ]("https://help.ubuntu.com/community/FilePermissions")restrict them to only those groups you assign them and the permissions within that group.

---

