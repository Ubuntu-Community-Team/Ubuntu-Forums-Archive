---
title: "How can I install the browser 'iron'"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by simpleblue on 2009-12-31
I have the link right here:
[http://www.srware.net/forum/viewtopic.php?f=18&t=835](http://www.srware.net/forum/viewtopic.php?f=18&t=835)

I download the file and then it extracts into a directory. That's it. I'm not sure what to do to install it once it's on my computer.

Is there a command or program I need to use? Such as terminal?

Thanx

---

### Post by s.fox on 2009-12-31
Hi,

Follow [these]("http://ubuntuforums.org/showpost.php?p=8511682&postcount=2") instructions and it should install fine.

If you have any trouble then please do post back.

-Silver Fox

---

### Post by ankspo71 on 2009-12-31
Hi,
If the iron-linux.tar.gz package has been extracted to your home folder, open a terminal and type:
```
~/iron-linux/iron
```Or you can do:
```
/home/yourname/iron-linux/iron
```Hope this helps.
this was for the 4.0.227 beta version btw

---

### Post by simpleblue on 2009-12-31
Thank you both so much. Almost there!

I've extracted it to a folder called iron-linux under my name.

I'm not sure how to change directories in terminal. If I could get help on that it would be much appreciated.

My terminal says: andre@andre-desktop:~$


It feels like we're sooooo close! :)

Thanks for your patience!

---

### Post by ChildOfMana on 2009-12-31
[quote="simpleblue"]I'm not sure how to change directories in terminal[/quote]

use the *cd* (_c_hange _d_irectory) command. E.g:

```
cd iron-linux
```

---

### Post by simpleblue on 2009-12-31
> **ChildOfMana said:**
> use the *cd* (_c_hange _d_irectory) command. E.g:

```
cd iron-linux
```
Thanks. This is what it says now:

andre@andre-desktop:~/iron-linux$


I tried entering in various commands, all of which likely were not the correct ones.

Where to do go from here?


Once again, thank you for your patience.

---

### Post by landersohn on 2009-12-31
in that directory you need to execute the following commands (like the instructions in an earlier post say):

./configure
make
sudo make install

If I can make a wild guess, you may not have the right compilers and support packages installed. So it's possible that the ./configure commands throws out a bunch of errors. Read the errors carefully and use

 sudo get-apt install <package name>

to install everything else you'll need.

---

### Post by simpleblue on 2009-12-31
> **landersohn said:**
> in that directory you need to execute the following commands (like the instructions in an earlier post say):

./configure
make
sudo make install

If I can make a wild guess, you may not have the right compilers and support packages installed. So it's possible that the ./configure commands throws out a bunch of errors. Read the errors carefully and use

 sudo get-apt install <package name>

to install everything else you'll need.
To show exactly what happens. I just entered in all the commands.

Here was the response:

andre@andre-desktop:~$ cd iron-linux
andre@andre-desktop:~/iron-linux$ ./configure
bash: ./configure: No such file or directory
andre@andre-desktop:~/iron-linux$ make
make: *** No targets specified and no makefile found.  Stop.
andre@andre-desktop:~/iron-linux$ sudo make install
[sudo] password for andre: 
make: *** No rule to make target `install'.  Stop.
andre@andre-desktop:~/iron-linux$ 

Any ideas?

---

### Post by landersohn on 2010-01-01
did you try following the adivse from ankspo71 earlier?

cd into your iron-linux and execute
./iron

and see what happens

---

