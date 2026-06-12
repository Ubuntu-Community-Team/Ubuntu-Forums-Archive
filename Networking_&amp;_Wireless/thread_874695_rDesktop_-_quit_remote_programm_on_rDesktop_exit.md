---
title: "rDesktop - quit remote programm on rDesktop exit?"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by DaVinciXL on 2008-07-30
Hey there.

I'm using rDesktop to work remotely on a windows machine from my Ubuntu box.
What I want is the following:
When I choose to exit rDesktop, I want it to send a signal to the remote machine, telling it to exit all running programs.

Is this possible at all? Couldn't find anything on the forums or via google.

Thanks in advance.

---

### Post by c2olen on 2008-07-30
Do you want to keep the session open or not?
Normally one would just logoff the RDP session, thereby termination all running apps.
Why stop all apps without logging off, or why keep the session open (and vulnerable) while there's noting to keep it open for? :confused:

You probably have a good reason, otherwise you would not post this question here.

If I remember correctly, you can set a lot of local policies on Windows regarding remote connections. Try looking there.

---

### Post by DaVinciXL on 2008-07-30
> **c2olen said:**
> Do you want to keep the session open or not?
Normally one would just logoff the RDP session, thereby termination all running apps.
Why stop all apps without logging off, or why keep the session open (and vulnerable) while there's noting to keep it open for? :confused:

You probably have a good reason, otherwise you would not post this question here.

If I remember correctly, you can set a lot of local policies on Windows regarding remote connections. Try looking there.

Well, actually I don't know much about rdesktop/rdp.
I'm connecting to the machine with the following command:
```
rdesktop $servername -d $domainname -u $username -p $password -g 90%
```

And I leave the machine again by just clicking on the x- (close-)button on top, which leaves all programs on the windows box running.

Security really isn't an issue for various reasons.

---

