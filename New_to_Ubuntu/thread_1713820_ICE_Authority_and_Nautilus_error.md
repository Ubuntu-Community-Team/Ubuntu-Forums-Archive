---
title: "ICE Authority and Nautilus error"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by travislam on 2011-03-24
Could not update ICEauthority file /home/test/.ICEauthority pops up. Followed by a nautilus access error. I tried sudo chown -R user:user /home/user/.* to no avail and what I've read of decrypting requires the loss of my data which I'd like to avoid. Also my cd drive kicked the bucket a bit ago so a solution to backup up my files sans Live CD would be boss

---

### Post by mikewhatever on 2011-03-24
The error seems to indicate the problem is with /home/test/.ICEauthority, but you, for some reason, chown a different location, /home/user/.*. Have you tried to chown /home/test/.ICEauthority?
How about something like this:
```
chown test:test /home/test/.ICEauthority
```

You can run a live session from USB, much faster the cdrom, and works the same.

---

### Post by chestyp on 2011-03-29
i recently started getting a similar ICEauthority error except the path is /var/lib/gdm/.ICEauthority

the second message is "a problem with the config server  sanity check 2 exited with status of 256"

I have just recently started playing with ubuntu so this is really new to me.

I have been searching for an answer but havent found one .  What should the defaul settings be (i.e. owner/group  permissions etc...)

tia

chestyp

---

### Post by travislam on 2011-03-30
The * switch is supposed to chown of all the subfolders of the chosen path right? Because I also get a nautilus error right afterwards which must also be fixed. When I try chown it says it can't find the folder... I'll try chowning that specific folder and see if it works. It seems like my folders are encrypted orsomething like that

---

### Post by alex_zaragoza on 2011-05-04
This happened to me when I installed veetle as root. It just changed the ownership of my home folder.

Try:
cd /home
sudo chown user:user user

where user should be your username.

---

