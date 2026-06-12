---
title: "It says permission denied opening a.out or anything"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Channi on 2011-04-03
Hey friends,
I have installed Ubuntu using wubi 4 days back. It is first linux OS I m trying.
Whenever I tried opening a.out file I compiled using g++, it says permission denied. I tried using as admin even ,it is same every time.
It is not running any script files using terminal. I tried installing WINE from its source code, and it says same "Permission Denied" when I tried to compile the code as the instructions given with source. 

Please help....:)

---

### Post by rosencrantz on 2011-04-03
Check the permissions on the a.out file with ls -l a.*
You should get something like
-rwxr-xr-x 1 username username size date time a.out
if there is no x in the first entry, do chmod a+x a.out (if there's a root instead of your user name, do sudo chmod a+x a.out)

Cheers,
rosencrantz

---

### Post by Channi on 2011-04-03
It don't work friend. In permissions it says
-rw------- l usrname ........
and does nothing when I try chmod.
I even tried changing permissions usng GUI, to allow executing it, but the check mark is removed by itself. I've logged in as admin.

---

### Post by praneet_223 on 2011-04-03
check the permission of a.out
i think it is denied in your ubuntu

---

### Post by Channi on 2011-04-03
it has permissions to read and write. But I can't make it to be executable as program. Can u help.....

---

### Post by rosencrantz on 2011-04-03
Hmmm, sadly I've never used Wubi. Logging in as root is not a very good idea, so try using sudo as much as possible -  it should be adequate for changing permissions. Can you change permissions for other files? The file might just be corrupted (I think you should be able to change permissions on corrupted files, but you never know). Try to delete the file and to recompile.
By the way, do you have any reason to compile Wine from source? On any fairly recent Ubuntu, you can install it via package manager by adding the ppa as described here:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Channi on 2011-04-03
I am unable to change permissions for any files(not even .txt files). I can't install softwares from .deb packages even(it says permission denied), but I can install using Ubuntu software center and apt-get by downloading it from Internet.
Should I reinstall Ubuntu directly from live CD(I don't want to lose Windows OS right now as I m not that good with linux) ???

Thanks  rosencrantz  for ur opinion, I'll take care.

Is there any other solution to my prob.

---

### Post by simar.mohar on 2011-04-03
try using this in your command prompt and it should work in all cases..
 
```
 
$sudo ./a.out

```

---

### Post by Channi on 2011-04-03
No friend, it don't work in my case. :(:(

---

### Post by rosencrantz on 2011-04-03
Hmmm... Nothing found resembling your issue on Google. Did you have any problems during your Wubi install? 
I'd try uninstalling and reinstalling the Wubi Ubuntu first (do you need to back up user data?)
Doing a proper non-virtualised Ubuntu install is a good idea if you want to use Ubuntu a lot, but if you haven't a free partition at the ready, you should definitely back up your Windows partition before you start resizing and installing.
BTW, another way to play with Ubuntu is using a live USB drive.

---

### Post by Channi on 2011-04-03
I tried to google it before joining the forum, but found nothing. 
I'll try  reinstalling Ubuntu. Is it possible to keep the installed softwares to new installation of OS?? I don't want to download all of them again, it takes a lots of time downloading them.

Once again thanks rosencrantz for ur help!! :)

---

### Post by Daniel0108 on 2011-04-03
> **simar.mohar said:**
> try using this in your command prompt and it should work in all cases..
 
```
 
$sudo ./a.out

```

Don't use sudo, only if it's really really required!

```
chmod +x ./a.out
```
This line should work. Just cd to the directory where your a.out file is, and enter this code.
Then start the program with
```
./a.out
```
And it should start. If it doesn't start, copy the whole error message,
Daniel

---

### Post by Channi on 2011-04-03
> **Daniel0108 said:**
> Don't use sudo, only if it's really really required!

```
chmod +x ./a.out
```
This line should work. Just cd to the directory where your a.out file is, and enter this code.
Then start the program with
```
./a.out
```
And it should start. If it doesn't start, copy the whole error message,
Daniel

It is still saying permission denied. I m unable to run any files(scripts) including .deb and .sh. It even don't let me change permissions to the file to allow it executing as a program.

---

### Post by Learning Linux 2011 on 2011-04-03
Maybe I am misreading, but normally if you want to compile a program, you do it this way:
```

gcc [COLOR=Sienna]*whatever.c*[/COLOR] -o [COLOR=Sienna]*whatevernameyouwant*[/COLOR]

```which produces an executable called [I][COLOR=Sienna]whatevernameyouwant[/COLOR]

[/I]Then you type the following to run it:```

./[COLOR=Sienna]*whatevernameyouwant*[/COLOR]

```

Also, I assume you are doing that in your Home directory.

---

### Post by Channi on 2011-04-03
I can successfully compile files, but the problem is I can't execute the compiled binary. There r sm permission issues that I m unable to resolve. 
Have any ideas for that....?

---

### Post by Daniel0108 on 2011-04-03
> **Learning Linux 2011 said:**
> Maybe I am misreading, but normally if you want to compile a program, you do it this way:
```

gcc [COLOR=Sienna]*whatever.c*[/COLOR] -o [COLOR=Sienna]*whatevernameyouwant*[/COLOR]

```which produces an executable called [I][COLOR=Sienna]whatevernameyouwant[/COLOR]

[/I]Then you type the following to run it:```

./[COLOR=Sienna]*whatevernameyouwant*[/COLOR]

```

Also, I assume you are doing that in your Home directory.

If you don't specify an output file, it links the executable to a.out ;)
Daniel

---

### Post by Bölvaður on 2011-04-03
I was starting to think your (virtual) harddrive is messed up, as sometimes it will act as read-only device. But if you can create files then it starts being a mystery.

What happens if you copy your compiled program onto the desktop and give it all permissions

```
chmod 777 a.out
```

Please say if you need to use super in the beginning of the command or not.
Can you also start copy and pasting more of the commands you use and the outputs you get.

Oh check if you own your own home and what the permissions are there.

---

### Post by Channi on 2011-04-03
> **Bölvaður said:**
> I was starting to think your (virtual) harddrive is messed up, as sometimes it will act as read-only device. But if you can create files then it starts being ................................

It works when I copied the file to desktop. Other files also started working when copied to desktop. 
I have read-write-execute permissions for home, and all the folders and drives, but only read-write permissions for files. 
Can u please state what is wrong and how to resolve this.
and

THANKS A LOT Bölvaður :D,

at least I can resume my programming on Linux.

---

### Post by Channi on 2011-04-03
I am still without a solution, I've to copy everything to Desktop before making it run...... :(

---

### Post by Bölvaður on 2011-04-03
Show me the output of ```
ls -l
``` for the directory where you compile the files to.
Then show me the command you use to compile and the ls -l of this file.
Now show me you trying to run it but fail.
To end this show copy here the commands with you moving the executable to the desktop and running it successfully.


I cannot see how it can go from being unable to run to being able to run just by moving it like this, there must be problem with who owns what or how files are created.

I dont know how comfortable you are with the command line so here is the command to move (do it so I can see everything you do)
```
mv a.out /home/bölvaður/Desktop
```

---

### Post by Channi on 2011-04-03
I m quite comfortable with CLI. Here is what I do::
```

channi@ubuntu:~$ cd /media/2644016B44013F55/My\ Documents/
channi@ubuntu:/media/2644016B44013F55/My Documents$ g++ test.cpp
channi@ubuntu:/media/2644016B44013F55/My Documents$ ./a.out
bash: ./a.out: Permission denied
channi@ubuntu:/media/2644016B44013F55/My Documents$ ls -l a.out
-rw------- 1 channi channi 7980 2011-04-03 10:03 a.out
channi@ubuntu:/media/2644016B44013F55/My Documents$ chmod a+x ./a.out
channi@ubuntu:/media/2644016B44013F55/My Documents$ ls -l ./a.out
-rw------- 1 channi channi 7980 2011-04-03 10:03 ./a.out
channi@ubuntu:/media/2644016B44013F55/My Documents$ mv a.out /home/channi/Desktop/

```
And then after changing permissions again

```
channi@ubuntu:~/Desktop$ chmod a+x ./a.out
channi@ubuntu:~/Desktop$ ./a.out
Enter size of matrix: "IT IS RUNNING HERE"   
```

ANY IDEA wat is going on!!!!

---

### Post by rosencrantz on 2011-04-03
As it is in /media, is your files' original location on a different partition? Could you post your fstab file for us (output of 'cat /etc/fstab')? Maybe the permissions  for the whole drive are screwed up, although it's still weird that you seem to be able to compile but not to change permissions.
Are you able to create and modify files?

---

### Post by Bölvaður on 2011-04-03
> **rosencrantz said:**
> As it is in /media, is your files' original location on a different partition? Could you post your fstab file for us (output of 'cat /etc/fstab')? Maybe the permissions  for the whole drive are screwed up, although it's still weird that you seem to be able to compile but not to change permissions.
Are you able to create and modify files?

Induction tells me this drive you mount is not a filesystem that has users or any privileges for the users and this is why you cannot change the permissions.

If I had to guess you are mounting your windows partition or ntfs or fat32 usb where you keep your source code.
Please either change the compilation command to specify a different location (your virtual harddrive which ubuntu is on) OR you should just move everything you are doing onto the ubuntu partition where user privileges are honored.


I might have phrased this in a weird way but I hope you understand. The problem is that the partition you are currently using doesnt allow for any read/write/executable/users... etc

---

### Post by bcbc on 2011-04-03
[HOWTO: Mount NTFS partitions with specific ownership/permissions]("http://ubuntuforums.org/showthread.php?t=1604251")

---

### Post by Learning Linux 2011 on 2011-04-03
What are you actually compiling?  Is it a program you wrote?  Is that program trying to do something to the hardware like write to a file or something?

---

### Post by Learning Linux 2011 on 2011-04-03
Try compiling something else like:

```

#include<stdio.h>

main()
{
    printf("Hello World");
}


```

Then try running that.  Then you will see if it is a permissions issue or something else.

---

### Post by Learning Linux 2011 on 2011-04-03
Also, Wubi is essentially running on an NTFS partition right?
Seems to me that would be a problem.

---

### Post by Bölvaður on 2011-04-03
> **Learning Linux 2011 said:**
> Also, Wubi is essentially running on an NTFS partition right?
Seems to me that would be a problem.
no there is no problem because it's running of a virtual hdd that is basically a file which got some partitions on it.

also they wouldnt be shipping wubi if there was a problem.
the only problem with wubi is that it's a file, so everything done on the hdd will be much shower than if it would be installed normally. For most users it will not matter, but for those who write/read a lot onto hdd then it matters.

---

### Post by Learning Linux 2011 on 2011-04-03
Maybe I won't be of much help, partly because I don't have any real experience with Wubi,
but I can tell you that in my Ubuntu Linux install, the "/media" folder requires root access.  If I am trying to run a program in the "/media" folder in my installation it won't work because I wouldn't have permissions.

It would work on my desktop because I have permission to use my own desktop.

Does the "/media" folder on your Wubi installation require root privileges?


In Windows you cannot change the file permissions to be greater than the folder permissions, which I would guess would be true in Linux.  It probably doesn't do any good to change your file permissions because the folder permissions would override the file permissions.  You would have to change the /media folder permissions first.  

Changing the permissions of the file(s) themselves wouldn't matter  because the /media folder would essentially say, "sorry, you have no  permission to execute in this folder".

You do have read and write permissions, so that would explain why you can compile, but not execute.


Why are you trying to compile in the /media folder anyway?  Why not compile in your /home directory?


I would guess you can't get the execute permission because of the /media folder requiring root privileges.

---

### Post by bcbc on 2011-04-03
> **Learning Linux 2011 said:**
> Maybe I won't be of much help, partly because I don't have any real experience with Wubi,

This isn't a wubi issue. It's an ntfs issue. If you look at that howto I linked to it explains what needs to be done. If the OP was compiling and running code on the /host ntfs partition, then it would be a wubi issue and in that case you would probably need to modify the kernel boot options to give your user the correct (simulated) permissions on /host, but in this case you can modify /etc/fstab to resolve the issue.

---

### Post by Learning Linux 2011 on 2011-04-03
> **bcbc said:**
> This isn't a wubi issue. It's an ntfs issue. If you look at that howto I linked to it explains what needs to be done. If the OP was compiling and running code on the /host ntfs partition, then it would be a wubi issue and in that case you would probably need to modify the kernel boot options to give your user the correct (simulated) permissions on /host, but in this case you can modify /etc/fstab to resolve the issue.

NTFS was one of my first thoughts too.

It can also be solved by compiling and executing in his /home folder, which he seems to have read, write, and execute permissions for.

---

### Post by Channi on 2011-04-04
> **bcbc said:**
> [HOWTO: Mount NTFS partitions with specific ownership/permissions]("http://ubuntuforums.org/showthread.php?t=1604251")

Thanks man, it is working now. The problem was with file system.

---

