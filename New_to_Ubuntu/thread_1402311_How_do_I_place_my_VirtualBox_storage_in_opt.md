---
title: "How do I place my VirtualBox storage in /opt?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by mikodo on 2010-02-09
So as to not have VirtualBox machines filling up my /home, I am trying to place an image in /opt. This from trying to do this from setting up a new VM. I have a permission problem as seen in the screenshot below. 

How can I do this?

Would this have to be done in sudo/root somehow, or by changing the permissions in /opt from root; or does that sound totally stupid?

Thanks.

EDIT:  I am not getting any takers on this for now. I'll check back later/tomorrow.

Mike

---

### Post by amsterdamharu on 2010-02-09
Not sure if this will work but you could try to create the file as root, change owner and then let virtualbox overwrite it:
```

sudo su
echo hi > /opt/Virtual\ Karmic.vdi
chown you:you /opt/Virtual\ Karmic.vdi
```

Now create the file in virtualbox, it should ask you to overwrite it.

---

### Post by mikodo on 2010-02-09
> **amsterdamharu said:**
> Not sure if this will work but you could try to create the file as root, change owner and then let virtualbox overwrite it:
```

sudo su
echo hi > /opt/Virtual\ Karmic.vdi
chown you:you /opt/Virtual\ Karmic.vdi
```

Now create the file in virtualbox, it should ask you to overwrite it.
Thank you for the response. When it comes to chown you:you... you: you would be my user name I suppose, right? 

This was just a test VM. When I get to configuring a real one I'll try the chown.

Thanks again,

Mike

---

### Post by amsterdamharu on 2010-02-09
The first you is the user "you" the second is the group "you", Ubuntu usually makes a group with the same name as the user so that's why I use you:you.

Not sure if it'll work but the user "you" who is running virtualbox should have permission to overwrite and change that file so the permission problem should be solved.

---

### Post by mikodo on 2010-02-09
> **amsterdamharu said:**
> The first you is the user "you" the second is the group "you", Ubuntu usually makes a group with the same name as the user so that's why I use you:you.

Not sure if it'll work but the user "you" who is running virtualbox should have permission to overwrite and change that file so the permission problem should be solved.
Thanks for the clarification. Not tonight, (I'm tired and need sleep), but I think I will try the test VM with the chown code you suggested and report back in the next few days.

Mike

---

### Post by mikodo on 2010-02-10
I'm sorry to report that the chown did not successfully change the ownership, and I got the same report telling me that "access was denied". I tried with "other" test VM images and got the same results, when trying to put them in /opt.

Thanks.

---

### Post by mikodo on 2010-02-10
I meant to include a screenshot of the files in /opt. See screenshot of them.

---

### Post by amsterdamharu on 2010-02-10
What's the output of the following command (you can copy and paste to and from the terminal using the right mouse button)?

ls -l /opt

---

### Post by mikodo on 2010-02-10
Sorry for the delay, I got reading a thread about rsync.

mikodo@mikodo-desktop:~$ ls -l /opt
total 32
-rw-r--r-- 1 mikodo mikodo 11 2010-02-10 01:20 New
-rw-r--r-- 1 mikodo mikodo 11 2010-02-10 01:17 New~
-rw-r--r-- 1 mikodo mikodo  3 2010-02-10 01:17 New Try.vdi
-rw-r--r-- 1 mikodo mikodo  3 2010-02-10 00:31 New Try.vdi~
-rw-r--r-- 1 mikodo mikodo  3 2010-02-10 01:17 Virtual Karmic2.vdi
-rw-r--r-- 1 mikodo mikodo  3 2010-02-10 00:59 Virtual Karmic2.vdi~
-rw-r--r-- 1 mikodo mikodo  3 2010-02-10 01:17 Virtual Karmic.vdi
-rw-r--r-- 1 mikodo mikodo  3 2010-02-10 00:43 Virtual Karmic.vdi~
mikodo@mikodo-desktop:~$

---

### Post by mikodo on 2010-02-10
Well I guess the permissions are set to my user for those files, but I still get a similar message as before. See again the screenshot of the first similar message.

---

### Post by mikodo on 2010-02-10
Well, just as last nite, I need to get to bed. Very nice to see your interest in this amsterdamharu. Here in Western Canada it is 02:24 and I have to get up in the A.M.

Sorry for starting this and then running off.

Mike

---

### Post by amsterdamharu on 2010-02-10
You can try to create a new harddisk, remove it from the list of known media (do not delete) and then copy it with root:

sudo cp /home/you//.VirtualBox/HardDisks/yourdisk.vdi /opt/

Then add that harddisk as known media (file -> virtual media manager).

I think copying it will copy permissions as well so no need to change them.

---

### Post by louieb on 2010-02-10
Your getting permission problems because you don't own /opt - and you should not. 
create a directory ```
sudo mkdir /opt/vb 
```
give full access to it ```
sudo chmod 777 /opt/vb
```

use /opt/vb  for your vdi files.

> I think copying it will copy permissions as well so no need to change them. 	

The person doing the copy owns the copy - copying with sudo changes the owner. Unless you use the** -a **option. See man cp.

---

### Post by mikodo on 2010-02-10
Thanks for the replies amsterdamharu and louieb. The mkdir and chmod way looks promising, at first blush. I suppose trying to own the sup-directory /opt as a user, poses an unnecessary security risk. I'm going to do some reading about them and cp commands; (newbie still). I'll report back any success/failures in the future. 

Mike

---

### Post by mikodo on 2010-02-11
Hello everyone,

Well, learning about perms brings with it a bit of a learning curve for me. Chmod numeric mode, with it's octal  digits (0-7), is for now confusing to me, until I am able to take the time to learn it.

I went ahead and used the code provided by louieb and was successful in placing a test vm image in /opt. Please see the screenshots of my file browser showing the test vm in /opt (vb vm test .vdi) and of VirtualBox with the vm (vm test) powered off.

Thank you.

EDIT:   The Windows 7 OS 64 bit vm presently resides in my /home. I hope to have it residing in /opt soon, until I install a second HD for it and other OS's/distro's.

---

### Post by mikodo on 2010-02-11
Here is the new file list for /opt and perms ( ls -l /opt). See screen shot

Thanks.

---

