---
title: "Terminal commands for GUI mount"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Elysius on 2010-08-09
I was wondering what the terminal commands are for the GUI mount (in 10.04) via "Places - Connect to Server - Server Type = Windows Share.

Searched on the forums and found a lot of commands for this. Like mount, gvfs-mount, smb etc, which one exacty does the GUI use? :p

---

### Post by SlugSlug on 2010-08-09
you'd want to read up on smbclient

---

### Post by Elysius on 2010-08-09
Thanks that was it. :D

```

smbclient //hostname/share -U username

```

will get you into the share....

---

### Post by bodhi.zazen on 2010-08-09
The mount command also works

mount -t cifs //server/share /mount/point

See man mount for options (you may include username and password if you wish). 

You may also add an entry in /etc/fstab 

With all that in mind, I advise autofs :

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

Samba : [http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs](http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs)

autofs will mount "on demand" and is, IMO, very nice =)

---

### Post by Elysius on 2010-08-10
Thanks for the heads up, was a nice read about autofs. Works great as well.

---

### Post by bodhi.zazen on 2010-08-10
> **Elysius said:**
> Thanks for the heads up, was a nice read about autofs. Works great as well.

You are most welcome.

Everyone who has tried autofs likes it =)

It does require some reading, but it is straight forward to configure and I like the "on demand" qualities as well as the fact that it is invisible to users.

---

