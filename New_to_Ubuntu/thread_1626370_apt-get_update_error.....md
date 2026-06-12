---
title: "apt-get update error...."
date: 2010-11-20
forum: New to Ubuntu
---

### Post by Jesus's Homie on 2010-11-20
I have a quick question.
Every time I run $ sudo apt-get update it gives me this output..

Get:8 [http://packages.dfreer.org](http://packages.dfreer.org) gutsy/main i386 Packages
68% [8 Packages bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Err [http://packages.dfreer.org](http://packages.dfreer.org) gutsy/main i386 Packages
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 9,531B in 2s (3,418B/s)
W: GPG error: [http://packages.dfreer.org](http://packages.dfreer.org) gutsy Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.bz2](http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.



I have tried numerous fixes that I have found throughout ubuntu forums to no avail..
Can someone please give me abetter understanding on what is going on and how I can fix it.
Any help will be greatly appreciated.

---

### Post by northern lights on 2010-11-20
You appear to have some way old gutsy second-party repositories enabled.

Run```
gksu gedit /etc/apt/sources.list
```

Delete the line(s) with```
http://packages.dfreer.org ...
```

Save.

Update again.


P.S.
Please be patient in waiting for answers and refrain from posting multiple threads concerning the same subject. Thank you.

---

### Post by lol768 on 2010-11-20
What I think is happening is that the repository that you have added is depreciated and is therefore not active any more. Northern lights posted before me so just try the commands above.

Please try not to post more than one identical threads in the future. Maybe you clicked the submit button twice but it looks like you posted the second one a minute after the other. It's really confusing when searching the forums. If it was accidental (which it probably was) then don't worry too much about it, just be patient and wait for the thread to submit.

---

### Post by Jesus's Homie on 2010-11-20
Sorry for the late reply. Ive been out all day and just got a chance to get back to my computer.

I did what you said and it worked like a charm.

I really appreciate the help.

sorry about the double posting.

---

