---
title: "WebDAV with SSL (davs) connection error in 8.04 Hardy, but worked in 8.10 Gutsy"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by andrewkk on 2008-05-16
This used to work fine in 7.10 Gutsy, but in a fresh installation of 8.04 Hardy when I try to access "davs://wuf-stuns.wuf.wwu.edu/oneNet/NetStorage" in Nautilus, the following error message appears immediately after the username and password prompt:

> **Couldn't display "davs://wuf-stuns.wuf.wwu.edu/oneNet/NetStorage".**

Error: HTTP Error: Internal Server Error
Please select another viewer and try again.

This is a really unhelpful error message. What steps should I take to try to solve this? (Is there log file I could look at somewhere? What has changed in Hardy that could have caused this?)

---

### Post by mcking on 2008-06-30
I experienced the same behavior.  I ended up using the fuse-dav to mount the share as a regular filesystem.  It doesn't work very well, but at least I can get to the files without using the web interface (which sucks).

I don't know what broke between 7.10 and 8.04, but it hurt me, since we use a DAV server for a lot of documents here.

---

### Post by andrewkk on 2008-06-30
Thanks for the suggestion, fusedav is working flawlessly. It'll just require a little script or two to be convenient for everyday use.

---

### Post by MountainX on 2008-07-18
Maybe this is my problem too. This was my post

[http://ubuntuforums.org/showthread.php?p=5412373#post5412373](http://ubuntuforums.org/showthread.php?p=5412373#post5412373)

Still looking for solution. May try fusedav next.

It is hard to believe a feature like this would remain broken in Hardy.

---

### Post by MountainX on 2008-07-18
Solved for me. 

I saw [this post]("http://ubuntuforums.org/showpost.php?p=4896041&postcount=6") and tried davs://theserver.com and it worked.

---

### Post by kevindontenville on 2008-08-04
I cant get webdav SSL or not to work properly in Hardy, was all set to blame the server as Ubuntu has worked fine in the past.

This is a big fat silly mistake, should be resolved for an LTS quicker than this. 

Any other short term solutions? I cant mount webdav with any of the suggestion here at all and it is a bit of a pain! Is it all down to GVFS?

---

### Post by MountainX on 2008-08-04
> **kevindontenville said:**
> I cant get webdav SSL or not to work properly in Hardy, was all set to blame the server as Ubuntu has worked fine in the past.

This is a big fat silly mistake, should be resolved for an LTS quicker than this. 

Any other short term solutions? I cant mount webdav with any of the suggestion here at all and it is a bit of a pain! Is it all down to GVFS?

I'm using WebDAV a lot now with both Windows and Ubuntu clients and both Windows and Linux servers. In my experience, Ubuntu works better than Windows. I have absolutely zero problems using Ubuntu for WebDAV (including the secure mode, once I learned about davs://).

Maybe you should give more details about your specific errors and such...

---

### Post by kevindontenville on 2008-08-04
Thanks, thats good to hear, has been my experience too. XP could be flaky and Vista more so. 

I can use the webdav server fine from Debs and old Ubuntu incarnations but even without ssl I still get no connection with Hardy and Nautilus. Normally it asks for user/password then tells me:

Error: HTTP Error: Found Please select another viewer and try again

Same process on other distros seems to work, this and other installs of Hardy dont.

There are bugs out on gnome vfs relating to the problems and I have added my voice to that too. Are you using Hardy Ubuntu? Kubuntu I presume wouldnt suffer.

---

### Post by MountainX on 2008-08-04
> **kevindontenville said:**
> 
Error: HTTP Error: Found Please select another viewer and try again

I did see that same error as I was trying to figure this all out...

> **kevindontenville said:**
> 
 Are you using Hardy Ubuntu?

Yes, I am using Ubuntu Hardy. It is updated to 8.4.1 now. I did not have to change a single thing to get WebDAV working. It was only a process of learning. I did find it very confusing that Nautilus will not work when you use the "connect to server" dialog box (for secure WebDAV). You have to just type in the URI in the address bar (using davs://), then it works fine (better than fine, actually because it works way better than Windows).

---

### Post by andrewkk on 2008-08-04
> **MountainX said:**
> Solved for me. 

I saw [this post]("http://ubuntuforums.org/showpost.php?p=4896041&postcount=6") and tried davs://theserver.com and it worked.

It sounds like you had a different problem, [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/222532](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/222532). Some of us cannot connect to WebDAV even over HTTPS.

> **MountainX said:**
> Maybe you should give more details about your specific errors and such...

Where should I look for more details?

Thanks.

---

### Post by MountainX on 2008-08-05
> **andrewkk said:**
> It sounds like you had a different problem, [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/222532](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/222532). Some of us cannot connect to WebDAV even over HTTPS.

When I read that bug report, it sounds exactly the same. That's why I said you cannot use the "Connect to Server" dialog.

---

### Post by kenklay on 2008-08-08
I found that in Nautilus to connect to a secure server you have to use "Custom location" when you use the "Connect to Server" option. Then for the URL you have to use:

davs://your.webdav.server/folder.

---

