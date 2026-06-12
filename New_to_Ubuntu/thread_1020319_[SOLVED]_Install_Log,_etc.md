---
title: "[SOLVED] Install Log, etc"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by sanubie on 2008-12-24
I'm working through an old video I found ages ago on Linux certification. It's old, and for another distro, but it still has a lot of usefulness. I'm just wondering about a few things. 

For one, on the terminal topic, in the video the dude uses some commands that don't work with Ubuntu. Most of it makes sense, like rpm commands are obviously for red hat. But are there some Ubuntu equivalent commands? 

For example: he types in 

```
rpm -qa
```

Which queries on all the rpm packages installed. Now obviously I haven't got any rpm packages installed on Ubuntu, but it looks like there would be a similar command. I tried  ```
deb -qa
``` no luck there. 

Another cool feature I saw in the video was the install.log file. I checked the root directory, but I didn't see any install.log file. Then there was the boot.log for see all the packages loaded at boot time, etc. 

PS: 

Yes, I know there's a pretty GUI Add/Remove program that tells me what is installed. That's boring. I want to use the terminal! Anyone know the Ubuntu equivalent commands and log files for what I specified?

---

### Post by scragar on 2008-12-24
```
dpkg -l
```or```
dpkg --get-selections
```
will list every installed package.

Most logs will go in /var/log try checking in there.

---

