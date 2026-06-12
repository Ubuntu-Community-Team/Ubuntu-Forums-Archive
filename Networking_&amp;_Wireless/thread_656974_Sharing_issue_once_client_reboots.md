---
title: "Sharing issue once client reboots"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by MercJones on 2008-01-03
Hi there.

Heres a bit of background info:

I've got a linux server running Ubuntu, and a windows 2000 client pc.

Ive made a folder on the windows 2000 client pc and have shared that, and have then done the following in my terminal:

sudo smbmount //newit/sharetest /home/newit -o username=administrator,password=pass,dmask=777,fmask=777,rw

which worked fine, and basically /home/newit takes me to the client C:\sharetest  which is perfect.

All was going well until this morning.

I ssh'd to my linux server, went to /home and performed a "ls"

this took AGES...

I then connected via another client using winscp to my linux server, I can navigate to any directory fine, but as soon as I goto the /home directory I get:

says Host has not answered for more than 15 seconds. Still waiting...  followed by: Error listing directory '/home'. and Error changing directory to '/home'.

I know this is because the client(win 2000) pc has been rebooted, as ive just tested this again, but the linux server hasnt been rebooted..

I've got around this issue, well, managed to get it working by doing:

sudo smbumount /home/newit    to unmount it, and then remounting it again with the above command, and all is well again, I can do "ls" and its instant, and I can get in the home folder.

Any ideas why this is? or what I can do to stop it? client pcs get turned off each day, and to have this issue every day is going to be a real pain.

Any ideas please?

---

### Post by MercJones on 2008-01-07
anyone got any ideas at all? still struggling with this issue.

Cheers

---

