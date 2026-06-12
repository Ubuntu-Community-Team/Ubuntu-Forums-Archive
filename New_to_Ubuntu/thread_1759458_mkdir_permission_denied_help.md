---
title: "mkdir: permission denied help"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by dmster^ on 2011-05-15
Hello everyone, scrub here, 
I'm having issues regarding permissions when I try to create a directory from /home. 

user@ubuntu:/home$ mkdir playground
mkdir: cannot create directory 'playground': Permission denied

I've changed my user settings to admin and i still can't create a directory, I would really appreciate it if i can get some info on how I could resolve this problem. 
Thanks.

---

### Post by Hedgehog1 on 2011-05-15
Unless you are in your home direrctory:

```
mkdir /home/**hedgehog**/newplace
```

you will need to create the direcroty using 'sudo':

```
sudo mkdir /home/newplace
```

***The Hedge***

:KS

---

### Post by Rocket2DMn on 2011-05-15
This question is best responded to by asking you a question - why would you want to create a directory directly in /home? This is for user's home directories.  If you want to make a folder for yourself to access, you should create it in your own personal home directory, e.g. in "/home/dmster".
```
cd ~
mkdir playground
```
Now you have "/home/dmster/playground".

---

### Post by dcsoldschool53 on 2011-05-15
> **dmster^ said:**
> Hello everyone, scrub here, 
I'm having issues regarding permissions when I try to create a directory from /home. 

user@ubuntu:/home$ mkdir playground
mkdir: cannot create directory 'playground': Permission denied

I've changed my user settings to admin and i still can't create a directory, I would really appreciate it if i can get some info on how I could resolve this problem. 
Thanks.

If I understand you correctly, you were trying to create a folder in the /home directory not /home/user-name directory. try ```
cd /home/your-user-name && mkdir playground
```see if that works.

---

### Post by dmster^ on 2011-05-15
Thank you. 
I was following The Linux Command Line by Shotts and it didn't specify that i couldn't make it directly in /home. 
but /home/me/playground worked.

---

