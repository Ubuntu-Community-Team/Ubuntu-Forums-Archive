---
title: "Please tell me the chmod command"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Warpnow on 2009-02-06
I can't seem to figure it out...

When I log in, I get this message:

User's $home/,dmrc is being ignored. This prevents the default session and language from being saves. File should be owned by user and have 644 permissions. User's $home directory must be owned by user and not writable by others.

---

### Post by EmanresuusernamE on 2009-02-06
Looks like you edited the permissions of the home folder of your user there.  You'll need to give those permissions back for this error to go away.

Open up a command prompt, and type in something like this:
```
cd /home
sudo chown <USERNAME>|<USERNAME> <USERNAME>
sudo chmod 644 <USERNAME>
```Replace <USERNAME> with the username you're having an issue with.

That should get rid of that error for you.  I did that to one of my accounts that I created before the guest account came out to limit what would be saved with that account.  I still use it too when I want to test something since you can save stuff to different locations, and guest accounts can't save anything at all for the most part.

---

### Post by Warpnow on 2009-02-06
I'm in the home directory...the username is kuki, the folder kuki is there...

I type sudo chown kuki|kuki kuki

and I get

sh: kuki: not found


chown: missing operand after 'kuki'

Any idea why it won't work?

---

### Post by taurus on 2009-02-06
```
sudo chown -R kuki:kuki /home/kuki
sudo chmod 755 /home/kuki
sudo chmod 644 /home/kuki/.dmrc
```

---

### Post by Warpnow on 2009-02-06
haha, I think I might be in love with you :D

;)

Thanks, it worked obviously.

---

### Post by taurus on 2009-02-06
> **Warpnow said:**
> haha, I think I might be in love with you :D

;)

Thanks, it worked obviously.

Wow!  Easy there, tiger...

---

