---
title: "Pidgin no longer launches"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by held7over on 2009-12-08
Running 9.10 Gnome

Pidgin has been working fine. I have added some applications. Then later noticed pidgin does not launch. I removed and replaced pidgin. 
I removed Empathy, thinking maybe they conflict.

I tried launching from terminal:

lucky@ispy:~$ pidgin
Illegal instruction
lucky@ispy:~$ ./pidgin
bash: ./pidgin: No such file or directory

How do I trouble shoot this situation? 

Or do I just remove programs I installed until pidgin works again or I run out of programs I downloaded?

Thanks! :)

---

### Post by RedSingularity on 2009-12-08
Have you tried deleting pidgin settings files?

---

### Post by sweet_cogito on 2009-12-08
The first thing you should do is make sure that it is still visible on the path.  The easiest way to do this would be to use the "which" command:
```
which pidgin
```
If pidgin is installed, it should tell you where it is.  If it is not installed nothing will be returned.  

From your error it sounds like it could be a permissions error.  If that is the case, find the location using which and then use a command such as chmod in order to change the permissions:

```
sudo chmod 775 /path/to/pidgin
```

That hopefully helps.

---

### Post by held7over on 2009-12-08
lucky@ispy:~$ which pidgin
/usr/bin/pidgin
lucky@ispy:~$ ls -l /usr/bin/pidgin
-rwxr-xr-x 1 root root 888152 2009-11-30 06:17 pidgin
lucky@ispy:~$ /usr/bin$ sudo chmod 775 /usr/bin/pidgin
lucky@ispy:~$ ls -l /usr/bin/pidgin
-rwxrwxr-x 1 root root 888152 2009-11-30 06:17 pidgin

lucky@ispy:~$ ./pidgin
bash: ./pidgin: No such file or directory
lucky@ispy:~$ ./usr/bin/pidgin
bash: ./usr/bin/pidgin: No such file or directory
lucky@ispy:~$

I renamed .purple to .purple-old, and tried to launch pidgin again.
Same results as above....it doesn't launch.

Weird! :D

---

### Post by held7over on 2009-12-11
One of the dependencies which "kdenlive" adds, caused this problem with pidgin. Just removing kdenlive did not help, but when I pasted all of its dependencies the terminal showed for kdenlive when it removed it, and removed them, pidgin launched just fine.

---

