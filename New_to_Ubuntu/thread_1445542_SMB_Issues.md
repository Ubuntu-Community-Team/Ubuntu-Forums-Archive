---
title: "SMB Issues"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by Jeffster999 on 2010-04-02
Ok I have been thru the threads and done what I thought the tips were saying to do...here is what I get when I try to create a folder on the shared directory

There was an error creating the directory in smb://bnhpc-1/ubusrv/

details said permission denied

---

### Post by KdotJ on 2010-04-02
Are you using samba? Have you set up samba users and permissions?

---

### Post by Jeffster999 on 2010-04-02
Yes I am. I neglected to mention that the shar directory I am trying to get access is on a win xp machine.

I even tried to setup filezilla  and having one hell of a time. 

My brain feels a bit like a scrambled egg and all the text is starting to read the same

---

### Post by KdotJ on 2010-04-02
Oh right, I have no experience trying to access shares on a windows box from a Linux box. Can you access the share ok?

---

### Post by Jeffster999 on 2010-04-02
I can see them but that is it. No joy on trying to view, create or anything.

I even installe Ubuntu on the other box but that is not practical since the other box has to run windows more often than not.

---

### Post by KdotJ on 2010-04-02
On the windows box, how Are the shares set up? As shared folders? What are the permissions set as?

---

### Post by CharlesA on 2010-04-02
As long as you have permissions set for the share (and NTFS permissions) you should be able to access the share with the right username/password.

Double check the NTFS and share permissions.

---

### Post by Jeffster999 on 2010-04-02
OK I got it.....

Not real sure why it worked. Here is what I did.

I went to the windows machine and removed the share that was set up BEFORE I configured everything on my Ubuntu box.

I then recreated a new share on the Windows box (on the same partition) once that was done I went to Places-->Networks-->Winows Networks--> My Share

Once there, I was able to do what I wanted to do.

Now I am going to read to see how to assign a drive letter to maybe automate some of what I want to do.

I sincerely thank you all for the help

---

### Post by CharlesA on 2010-04-02
Awesome. Picky share permissions apparently.

---

### Post by KdotJ on 2010-04-02
Well done :D glad you got it sorted

---

### Post by Jeffster999 on 2010-04-02
Again Thank You 

and I just saw the same issue here:

[http://ubuntuforums.org/showthread.php?t=1445619](http://ubuntuforums.org/showthread.php?t=1445619)

I sent him to my own threads.

---

