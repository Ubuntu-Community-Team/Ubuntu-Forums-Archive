---
title: "[SOLVED] Another Noob needing Samba Help..."
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by halloween2311 on 2008-04-15
Greetings Everyone!

I know there are hundreds of posts concerning Samba on the forums and I have searched them but have not found one that deals with the issue I keep having.  (If I missed one, please feel free to direct me to it and accept my apologies)

I have Ubuntu 7.10 running on an old Dell desktop (pentium 4, 256 meg of ram) and on a new Gateway laptop (Centrino Duo, 2 gig of ram).  My wife also runs two Win XP machines and we would like to have all of these communicate with each other so I tried to set up Samba.  My first goal is to get the two Ubuntu machines talking to each other before attempting to network the XP machines in. 

I have Samba installed and running on both machines, I have also set the Samba policy in firestarter in both.  When I go to "places - network", both computers are shown.  Now here comes the problem; when I click on either computer (EG from the laptop I click on the desktop) I always receive he same error message: 

"The folder contents could not be displayed.  Sorry, couldn't display all the contents of "Windows Network: spudette"."

With spuddette being the name of my desktop.

I'm sure there is something simple I am missing but I can't seem to find it.  As always, any guidance will be welcome.  Also if you need me to post any more info, just let me know.  Thanks.

---

### Post by Iowan on 2008-04-15
You have set up users via smbpasswd?
Sometimes, I have better luck using the Places>Connect to Server option.

---

### Post by halloween2311 on 2008-04-15
Greetings Iowan,

Thank You!  The connect to server option worked perfectly!

---

### Post by Iowan on 2008-04-16
Wish I knew why it matters - suffice it to say  - it works. Mark this one SOLVED (Thread tools).

---

### Post by halloween2311 on 2008-04-16
Thanks, Done!  :)

---

