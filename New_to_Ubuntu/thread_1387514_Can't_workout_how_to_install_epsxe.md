---
title: "Can't workout how to install epsxe"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-01-21
ive been trying all night to get this installed, the guide on this site dosent work, none of the codes i enter in the terminal work for me. I have downloaded the linux file from the epsxe website and i still have no idea what im ment to do with it. 

Anyone who has set this up before help me? its very annoying.

---

### Post by user1397 on 2010-01-22
> **Rave Gloves said:**
> ive been trying all night to get this installed, the guide on this site dosent work, none of the codes i enter in the terminal work for me. I have downloaded the linux file from the epsxe website and i still have no idea what im ment to do with it. 

Anyone who has set this up before help me? its very annoying.
could you post the website link to the download?

---

### Post by Rave Gloves on 2010-01-22
> **ubuntuman001 said:**
> could you post the website link to the download?

 ePSXe v1.6.0	
180 KB
ePSXe executeable (Linux)

[http://www.epsxe.com/download.php](http://www.epsxe.com/download.php)

---

### Post by user1397 on 2010-01-22
Try this:

1. Download it again.
2. Extract the zipped file to your desktop.
3. Open a terminal and type:```
cd Desktop/epsxe160lin/
```
4. Type this to make the file executable: ```
chmod +x epsxe
```
5.Then type```
./epsxe
``` and post the results here.

---

### Post by 3rdalbum on 2010-01-22
This program is unmaintained; the last version was on my birthday (24 May) in 2008.

There's a Playstation emulator in the repositories.

For future reference, merely saying "the codes on the website don't work" is not enough for us to be able to help you. Which one doesn't work, and what error message is given? Have you navigated your terminal to the correct directory? (hint: type 'cd' and then hit Space, and then drag the directory to the terminal).

---

### Post by Rave Gloves on 2010-01-22
Cant seem to get any of them to work, 

```
andrew@andrew-laptop:~$ cd Desktop/epsxe160lin/
bash: cd: Desktop/epsxe160lin/: No such file or directory
andrew@andrew-laptop:~$ cd Desktop/installepsxe/
bash: cd: Desktop/installepsxe/: Not a directory
andrew@andrew-laptop:~$ chmod +x epsxe
chmod: cannot access `epsxe': No such file or directory
andrew@andrew-laptop:~$ ./epsxe
bash: ./epsxe: No such file or directory
andrew@andrew-laptop:~$ 





```

I thought i would change the name to the installepsxe and try that, still didnt work. Any ideas?

And i have tried the one in the add/remove and i couldnt get my ps3 controller to work with it.
I can understand what you mean, i did post to quick without any info i was really annoyed.

---

### Post by Rave Gloves on 2010-01-22
Bumppp

---

### Post by themusicalduck on 2010-01-22
Ok, first download or copy the file onto your desktop. Then right click on the zip file and pick Extract Here.

Now open a terminal and try this command ```
cd ~/Desktop/epsxe160lin
```

Then try steps 4 and 5 in ubuntuman001's post.

---

### Post by Rave Gloves on 2010-01-22
> **themusicalduck said:**
> Ok, first download or copy the file onto your desktop. Then right click on the zip file and pick Extract Here.

Now open a terminal and try this command ```
cd ~/Desktop/epsxe160lin
```

Then try steps 4 and 5 in ubuntuman001's post.

```
andrew@andrew-laptop:~$ cd ~/Desktop/epsxe160lin
bash: cd: /home/andrew/Desktop/epsxe160lin: No such file or directory
andrew@andrew-laptop:~$ 


```

Did exactly as you said, isnt working. 
The file name, epsxe160lin (1)
I shall try that.

Edit: ```
 andrew@andrew-laptop:~$ cd ~/Desktop/epsxe160lin (1)
bash: syntax error near unexpected token `('
andrew@andrew-laptop:~$ 

```

Renamed the file name not to have the (1), tried codes again got to the last stage before it failed.

```
andrew@andrew-laptop:~$ cd ~/Desktop/epsxe160lin
andrew@andrew-laptop:~/Desktop/epsxe160lin$ chmod +x epsxe
andrew@andrew-laptop:~/Desktop/epsxe160lin$ ./epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
andrew@andrew-laptop:~/Desktop/epsxe160lin$ 
```

---

### Post by 3rdalbum on 2010-01-22
> **Rave Gloves said:**
> 
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```
sudo apt-get install libgtk1.2
```

---

### Post by Rave Gloves on 2010-01-23
its booted though terminal but i cant see it on any of my application area.

do i need to boot it thought terminal everytime?

---

### Post by Komputor on 2010-07-27
I have a different problem.  Following the directions in this thread, I have re-downloaded epsxelin to my desktop, extracted the file to my desktop, chmod to be executable, and when I entered ./epsxe, I got the same error code: 
"error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

I tried apt-get install libgtk1.2 
Output:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk1.2

I tried apt-get install libgtk1.2.so.0
Output:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk1.2

I think the only thing missing is this gtk library but my computer can't find it for whatever reason.

I am running Ubuntu Lucid 10.4 in case anyone needs that info.  Please help, I love this emulator and just can't seem to get it to install and work properly on my machine.

---

### Post by NoTownKasper on 2010-09-15
Same broblem here exactly...apparently the libs aren't in the repo, and unfortunately, the emulator in the repos isn't exactly the most functional one out there...that's the problem with emulation.

Any suggestions on how to get this working?

---

