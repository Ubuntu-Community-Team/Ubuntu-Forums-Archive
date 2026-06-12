---
title: "Help with ssh"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by Pitbull11188 on 2007-08-28
I was wondering if someone could link me to a site that would show me how to set up a secure ssh.

My intent is to be able to ssh from my laptop which is connected to my universities network, to an older computer I have that would be in my dorm room. Then I would primarily want to use wget or lynx to find a torrent online, and then transmission to begin downloading it.

The thing is idk if everything I initiated would end the minute I exit the ssh from my laptop.

To be honest I'm kind of looking for confirmation that this would work, and a couple links to information that may help me set it up.

---

### Post by thatswhatshesaid on 2007-08-28
To install an ssh server (simple; has worked for me)
```
sudo apt-get install openssh-server
```

To keep the process/program going after you end your session
normally you would type ```
./program
```
if you type ```
./program &
``` the process/program is given a process id and should remain open/running even after you close your ssh session.

I have to do this all the time with WebLogic start scripts (on solaris and linux), I don't have my buntu machine with me right now but I'd be surprised if this didn't work.

---

### Post by Pitbull11188 on 2007-08-28
Ok I will try this tomorrow thanks alot.

---

