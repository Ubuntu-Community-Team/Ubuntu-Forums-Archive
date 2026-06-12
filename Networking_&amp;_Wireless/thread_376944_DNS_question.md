---
title: "DNS question"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by Iesu on 2007-03-05
After installing Kubuntu 6.10 Edgy Eft, I had a hell of a time getting my update programs (aptitude, wget) to connect to my repos. I always had to ping the repos first. I have since solved the problem with the help of the Absolute Beginners Forum, by manually specifying my ISP's DNS servers.
So can anyone here tell me why using the router's DNS settings worked for ping and firefox etc but not for the update programs? I didn't have this trouble with openSUSE 10.2, and most of Kubuntu's internet programs worked "out of the box" so to speak. But having the update programs not work was really annoying. Is this a bug that needs reporting?

---

### Post by Buster95 on 2007-03-05
Hello Iesu,
I'm having the same problem.
What thread did you get your answer from?
Cheers

---

### Post by Mr. C. on 2007-03-05
Commodity routers often have very poor DNS implementations.  Your ISPs will have dedicated Bind or other name servers running, that perform exceptionally well, and provide reliable results.

Many linux distros come with caching name servers; these perform well.

Use your ISPs name server, or a caching name server running on your local box or LAN.

MrC

---

### Post by Iesu on 2007-03-06
Anything for a fellow Aussie Buster95. Mr.C. actually hit the nail on the head. You just need to manually specify your DNS servers. The link is [here]("http://www.ubuntuforums.org/showthread.php?t=358749")
The solution is the 8th post down.

---

