---
title: "open office template packs"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by kd0afk on 2009-08-04
How do you import the open office template packs with an .oxt extension into open office?

---

### Post by jmszr on 2009-08-04
kd0afk,

First, you need to install:```
sudo apt-get install openoffice.org-java-common
``` and then the template packs from here: [http://extensions.services.openoffice.org/](http://extensions.services.openoffice.org/) . Download the pack and then in Writer go to Tools > Extension Manager > click Add and then find the pack where you downloaded it to, click on it, and click Open. That should do it.

---

### Post by kd0afk on 2009-08-04
Thank, I'll give that a try.

---

### Post by kd0afk on 2009-08-04
Tried it and here is the return:

```
shawn@ubuntu:~$ sudo apt-get install openoffice.org-java-common
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
shawn@ubuntu:~$ 

```Then, I ran:
```
shawn@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
shawn@ubuntu:~$ ********
bash: *******: command not found
shawn@ubuntu:~$
```

---

### Post by jmszr on 2009-08-04
kd0afk,

Run:```
sudo dpkg --configure -a
```
 Then:```
sudo apt-get install openoffice.org-java-common
```
You can also go to System > Administration > Synaptic Package Manager > Search > openoffice.org-java-common > Right click on it and "mark for installation" > Apply.

Note: Before you go to Synaptic you still will need to run "sudo dpkg...."

---

### Post by kd0afk on 2009-08-07
Good to go. Thanks.

---

### Post by Crunchy the Headcrab on 2009-08-07
You need to use sudo before a command that requires root privileges.  I do believe you just posted your password on the forum because you tried to enter your password without being prompted for it by using sudo.

---

### Post by kd0afk on 2009-08-07
> **Crunchy the Headcrab said:**
> You need to use sudo before a command that requires root privileges.  I do believe you just posted your password on the forum because you tried to enter your password without being prompted for it by using sudo.
Pretty sure I didn't reveal my password. Please let me know when I did this.

---

### Post by HotShotDJ on 2009-08-07
> **kd0afk said:**
> Pretty sure I didn't reveal my password. Please let me know when I did this.
Yep... you sure did.  Post #4, second code box, 4th line.

BTW, if that is also the password you use for your ubuntuforums.org account, I recommend that you change it right now... before doing anything else.

---

### Post by kd0afk on 2009-08-08
> **HotShotDJ said:**
> Yep... you sure did.  Post #4, second code box, 4th line.

BTW, if that is also the password you use for your ubuntuforums.org account, I recommend that you change it right now... before doing anything else.
WOW, I sure did. I made a point of "****" it out but I didn't catch the Bash return. Thanks for pointing that out. I fixed everything.
Also, if terminal would have hinted at it, I would have used the sudo command. I know at least that much about linux at this point but thanks for the help on it nonetheless.

---

