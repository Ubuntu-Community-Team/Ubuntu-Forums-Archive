---
title: "Delete files in tmp folder"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by titus2020 on 2010-01-17
Hello 

I have 2 questions: 

Q1) I am a new user. Whenever i write a cd, the data is automatically getting stored in tmp folder. I want to know the method to delete the files in the temp folder.

Q2) when booting i see a lot of options 
"linux grub version some numbers"
altogether i see six options something like the above
is it normal and is there anyway to remove those options.

Thanks for the help

---

### Post by Mornedhel on 2010-01-17
> **titus2020 said:**
> Q1) I am a new user. Whenever i write a cd, the data is automatically getting stored in tmp folder. I want to know the method to delete the files in the temp folder.

You can remove files in /tmp just as any normal files (assuming you own them). Some may be necessary to the execution of currently running programs, so it may not be a good idea. Also, /tmp gets purged every time you shutdown, and possibly on a regular schedule as well (not sure).

> **titus2020 said:**
> Q2) when booting i see a lot of options 
"linux grub version some numbers"
altogether i see six options something like the above
is it normal and is there anyway to remove those options.

Yes, it is normal. There is one entry for each kernel you have installed. The latest one is booted by default. This is useful when a new kernel breaks things on your system -- you can boot into an older version which you know works.

You can remove the packages for older kernels in Synaptic, and the entries in GRUB should go away.

---

### Post by HermanAB on 2010-01-17
Howdy,

The /tmp directory should be configured with tmpfs which is a RAM disk.  So the contents is lost each time you cycle power on the machine.

---

### Post by titus2020 on 2010-01-17
Thanks for the answers.

I am not sure if my tmp files are deleted on reboot. Because today i wrote a cd and before writing the tmp folder occupied 11.6 GB and after writing was completed it showed as 12.6 GB. I tried the methods in the following link and even after that the size of tmp folder is 12.6 GB.

---

### Post by ajgreeny on 2010-01-17
There must be something wrong, or are you perhaps using some backup application that puts permanent files into tmp.  Either way it should not happen that way.

My tmp folder is about 70kb unless I have downloaded some flash video files which sit there until that firefox flash page is closed, or I have an application open which uses tmp as a temporary cache.  Note the word "temporary".

---

### Post by SOULRiDER on 2010-01-17
> **titus2020 said:**
> Hello 

I have 2 questions: 

Q1) I am a new user. Whenever i write a cd, the data is automatically getting stored in tmp folder. I want to know the method to delete the files in the temp folder.

Q2) when booting i see a lot of options 
"linux grub version some numbers"
altogether i see six options something like the above
is it normal and is there anyway to remove those options.

Thanks for the help

You shouldn't worry about /tmp. What you could do (and it would be great if someone double checked this) is boot into a live CD and empty the directory. The liveCD part is so you dont affect any running applications.

---

### Post by fooman on 2010-01-17
bleachbit can clean your temp files as well as a mess of other stuff....all configured by the user.

it is available in the repos,  or in a terminal:

```
sudo apt-get install bleachbit
```

---

### Post by titus2020 on 2010-01-17
I tried using bleachbit, it did not help. the space occupied by tmp folder is still same. I have downloaded songs from youtube as flash songs but i deleted all of them manually. Not sure if this is the reason.

---

### Post by egalvan on 2010-01-17
You can change the number of kernels by directly editing GRUB files,
or you can use StarpUpManager.

the first way is more informative, challenging, and educational.
the second way is merely easy, and fairly fool-proof.

---

### Post by warfacegod on 2010-01-17
> **egalvan said:**
> You can change the number of kernels by directly editing GRUB files,
or you can use StarpUpManager.

the first way is more informative, challenging, and educational.
the second way is merely easy, and fairly fool-proof.

In 9.10 the start up manager no longer exists. It has been replaced login manager which has basically no functionality.

I have found that the safest way to remove those lines is to ubuntu tweak and actually remove the kernels from the computer.

---

### Post by warfacegod on 2010-01-17
As far as your tmp folder goes, if deleting its contents doesn't work normally then hit Alt+F2 and type gksudo nautilus and use that file browser to go to tmp and delete what you wish.

gksudo nautilus can also be started from the Terminal if you prefer.

FYI When you stream something from the net the data goes to the tmp folder. if you want to keep what you streamed, go into that folder and move the file to your home folder.

---

### Post by fooman on 2010-01-17
how about:

```
sudo rm -rf /tmp/*
```

WARNING,  be *very* careful using that "rm -rf" command!

---

### Post by warfacegod on 2010-01-17
> **fooman said:**
> how about:

```
sudo rm -rf /tmp/*
```

WARNING,  be *very* careful using that "rm -rf" command!

Personally if I feel the need to post a warning about a command, I don't post it unless it's the only solution.

---

