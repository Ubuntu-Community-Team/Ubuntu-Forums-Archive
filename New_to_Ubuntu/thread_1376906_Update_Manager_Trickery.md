---
title: "Update Manager Trickery?"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by biomedtech on 2010-01-09
Since installing Ubuntu 9.10 on my EeePC 901, all updates have been applied whenever Update Manager popped up a message. The system is installed on the 4GB SSD, and initially I had about 1Gig of empty space left.

Today I am almost out of room. Update Manager popped up a message, saying there were 45MBs of updates to install.  I authorized the updates to begin, and somehow lost 300MB of space after the reboot. 

Before today's update, I had 385MB of free space.  After the 45MB of updates, I now only have 87MB of free space left. What Gives?

I tried to use "Sudo apt-get clean", but it didn't help.

---

### Post by tad1073 on 2010-01-09
> **biomedtech said:**
> Since installing Ubuntu 9.10 on my EeePC 901, all updates have been applied whenever Update Manager popped up a message. The system is installed on the 4GB SSD, and initially I had about 1Gig of empty space left.

Today I am almost out of room. Update Manager popped up a message, saying there were 45MBs of updates to install.  I authorized the updates to begin, and somehow lost 300MB of space after the reboot. 

Before today's update, I had 385MB of free space.  After the 45MB of updates, I now only have 87MB of free space left. What Gives?

try:
```
sudo apt-get autoremove
```then:
```
sudo apt-get autoclean
```

that should remove all the old packages

---

