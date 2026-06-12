---
title: "Hangs during shutdown (CIFS VFS)"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Pas_sa on 2009-04-26
Hi folks.

When rebooting/shutting down, the entire system locks up for 3-4 minutes with the text:
```
[187.200076] CIFS VFS: server not responding
[187.200120] CIFS VFS: No response for cmd 50 mid 738
```

I have shares that automatically mount, thanks to a popular guide on this forum. I changed them in fstab from using 'cifs' to using 'smbfs' but that didn't help (and I'm not sure what the difference was).

---

### Post by jmail524 on 2009-04-26
Hi Pas_sa,

I had the same problem and found that the instructions, in the link below, fixed the problem.  I don't know if it is the best way to correct the problem but it worked.

[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

Good luck.



Brian

---

### Post by Pas_sa on 2009-04-27
I did that but it still hangs, if anything for longer.

All it does now is say it's running the unmount script.. then shows the CIFS error anyway.

---

### Post by Lotekk on 2009-07-30
> **Pas_sa said:**
> Hi folks.

When rebooting/shutting down, the entire system locks up for 3-4 minutes with the text:
```
[187.200076] CIFS VFS: server not responding
[187.200120] CIFS VFS: No response for cmd 50 mid 738
```

I have shares that automatically mount, thanks to a popular guide on this forum. I changed them in fstab from using 'cifs' to using 'smbfs' but that didn't help (and I'm not sure what the difference was).

Howdy, I had this issue at one point, it is caused by the network being shut down before your samba shares are unmounted.

To fix it, I just moved the unmounting before the network shutdown in the shutdown list. Here is how:

Change directory to /etc/rc6.d and list it's contents.
```

cd /etc/rc6.d
ls -la

```

You are looking for S#wpa-ifupdown and S#umountnfs.sh. wpa-ifupdown's # is normally 15, umountnfs.sh's # is normally 31. 

So you should see these two amongst your listing: 
```

S15wpa-ifupdown
...
S31umountnfs.sh

```

If these numbers are the same in your case, you can now type:
```

sudo mv S31umountnfs.sh S14umountnfs.sh

```

This moves your samba share unmounting to an "earlier" position in the shutdown list which *should* get rid of the annoying hangs in the shutdown process, it cleared my hangs up.

---

### Post by androomc on 2009-12-02
Thanks for this tip. This was bugging me for months and has been around since at least 8.04 (I'm now running 9.04)

P.S. I also changed the order in rc0.d so that it no longer hangs during a shutdown. It seemed rc6.d only fixed it for rebooting.

---

### Post by 5ulo on 2009-12-02
this workaround is not working in 9.10. I tried rename the S31 to S14 and lower and K00... but without any results. In 9.04 works this workaround like a charm

---

### Post by msimon1960 on 2009-12-02
Lotekk's solution worked for me -- I'd consider this a bug.  Lotekk -- have you reported this as a bug fix for Koala?

The essence of the solution is that Jaunty is stopping services in the wrong order.  Resequencing them as described here corrects that problem.

Matthew.


> **Lotekk said:**
> Howdy, I had this issue at one point, it is caused by the network being shut down before your samba shares are unmounted.

To fix it, I just moved the unmounting before the network shutdown in the shutdown list. Here is how:

Change directory to /etc/rc6.d and list it's contents.
```

cd /etc/rc6.d
ls -la

```

You are looking for S#wpa-ifupdown and S#umountnfs.sh. wpa-ifupdown's # is normally 15, umountnfs.sh's # is normally 31. 

So you should see these two amongst your listing: 
```

S15wpa-ifupdown
...
S31umountnfs.sh

```

If these numbers are the same in your case, you can now type:
```

sudo mv S31umountnfs.sh S14umountnfs.sh

```

This moves your samba share unmounting to an "earlier" position in the shutdown list which *should* get rid of the annoying hangs in the shutdown process, it cleared my hangs up.

---

### Post by Lotekk on 2009-12-03
> **msimon1960 said:**
> Lotekk -- have you reported this as a bug fix for Koala?


No sir I have not - wouldn't know where or how to do such a thing. I'm sure someone else has already and if not, will soon.

---

### Post by ubradford on 2009-12-06
I found a fix that works on Karmic while using wireless (WPA). I posted it here:
[http://ubuntuforums.org/showthread.php?p=8449027#post8449027](http://ubuntuforums.org/showthread.php?p=8449027#post8449027)

---

