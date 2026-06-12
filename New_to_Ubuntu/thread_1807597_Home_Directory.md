---
title: "Home Directory"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by orrymr on 2011-07-19
So, I know that ~ is synonymous with home directory; if I ```
 cd ~ 
``` it takes me to my home directory.
 I'm just a little confused about the terminology here since, if I cd ~, and I hit pwd, I'm shown that I'm in /home/username. So isn't cd ~/.. my home directory? Or does home directory here refer to the home directory of "username"? If I had another user on this machine, would I have another folder in /home? 

Thanks in advance!

---

### Post by gandaran on 2011-07-19
the home directory is always your username directory, just opening the terminal opens it in your /home/user already theres no need to use "cd ~"
> If I had another user on this machine, would I have another folder in /home?
check the root file system, "/home/user1" if there's another user there would also be a second user folder "/home/user2"

---

### Post by lmarmisa on 2011-07-19
Yes. 

The symbol ~ makes sense only in the scope of a user and its resolution is different for each user of a machine. But ~ or $HOME are useful because you can write commands or scripts with no absolute reference to the specific path of your user account. The same commands or scripts are valid for all users.

---

