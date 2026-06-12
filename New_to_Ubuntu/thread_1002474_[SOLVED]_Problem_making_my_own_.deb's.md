---
title: "[SOLVED] Problem making my own .deb's"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-12-05
I'm compiling my own .deb's with this tutorial:

[http://open.vitaminap.it/en/linux_howtos.htm#package](http://open.vitaminap.it/en/linux_howtos.htm#package)

But I run into a problem after sudo checkinstall, I get this in Terminal:

Please write a description for the package.
End your description with an empty line or EOF.

So I type Soundconverter, hit enter, and nothing happens. So I must be inputing it wrong. What exactly does "End your description with an empty line or EOF" mean?

Thank you.

---

### Post by yellowaeroplane on 2008-12-05
hey there,

I checked out the site you posted and saw this line:
> right click upon the folder containing the source code files and choose "open in terminal"

**So what it's assuming is that you've already cd'd to the file.**

Just put the .deb or .tar or whatever it now is in your home directory and  type this: 
```
cd yourfilename.deb
```

then just follow the instructions on that site

good luck!

---

### Post by h8uthemost on 2008-12-05
Well, I'm running into all kinds of problems now. Now it just tells me:

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

So, when I extracted the Soundconverter .tar, I got a folder named Soundconverter, with a bunch of files and folders in it. Is that the folder I'm suppose to right-click on to open into Terminal? Or is there a file or folder inside the Soundconverter folder that I'm suppose to open in Terminal?

Grr...I can't believe how hard Linux makes it just to install an app.

EDIT: And by the way, I have no idea what cd'd the file is. I see cd'ing a file all the time and have no idea what it means. But thank you for the reply.

---

### Post by sdennie on 2008-12-05
> **h8uthemost said:**
> 
Please write a description for the package.
End your description with an empty line or EOF.

So I type Soundconverter, hit enter, and nothing happens. So I must be inputing it wrong. What exactly does "End your description with an empty line or EOF" mean?


It means after hitting enter on a line with information, then hit enter or Ctrl-D (EOF) on the blank line.

---

### Post by yellowaeroplane on 2008-12-05
ha, no problem... we've all been there.

Okay, I just downloaded it and got it working... so this what I did:

First of all, forget about trying to turn it into a .deb... you don't need to.

Download the tar.gz and make sure it's in your home directory. Right click on the file and choose "extract here" then run these commands in this order:

```

cd soundconverter-1.4.0
./configure
make
make install
make clean
make distclean

```

And you should be good to go!

---

### Post by xjcannonx on 2008-12-05
so to "cd" means to change directory, it is the directory you are working in, so for example if you downloaded something to your desktop and needed to create a .deb from a file there you will need to cd (change directory) to that folder with this command:
```
cd Desktop
```
dont forget the capital letters, you can then cd into the file you need to be in
```
cd yourfilename
```
 Oh and to go back a level just do this
```
 cd ..
```

---

### Post by yellowaeroplane on 2008-12-05
and to go back to "normal" just do this:
```
cd ~
```
;)

---

### Post by h8uthemost on 2008-12-05
Man, that didn't work either. This is the error I'm getting when I put all of that into Terminal at once(by the way I changed it to 1.4.1 since that's the version I'm trying to install):

scott@scott-desktop:~$ cd soundconverter-1.4.0
bash: cd: soundconverter-1.4.0: No such file or directory
scott@scott-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
scott@scott-desktop:~$ make install
make: *** No rule to make target `install'.  Stop.
scott@scott-desktop:~$ make clean
make: *** No rule to make target `clean'.  Stop.
scott@scott-desktop:~$ make distclean

And this is the error I get when I only put in the cd command:

scott@scott-desktop:~$ cd soundconverter-1.4.1
bash: cd: soundconverter-1.4.1: No such file or directory
scott@scott-desktop:~$ 


And I did put the .tar.gz into my Home directory.

EDIT: Thank you for the info on "cd". And thank you vor.

---

### Post by sdennie on 2008-12-05
Is there a particular reason you need to compile this yourself?  The soundconverter package is already available in the repos:

```

sudo apt-get install soundconverter

```

---

### Post by xjcannonx on 2008-12-05
could you type in a command prompt ```
ls
``` please so we can see if the file is listed in the directory you are in?

---

### Post by h8uthemost on 2008-12-05
My bad yellowaeroplane, I didn't see you said to extract the file. I'll try that.

And vor, the reason I need 1.4.1 is because in the repos there is only 1.3.2, and 1.3.2 won't let me convert into 320kbps bitrate. Only 256. 1.4.1 will let me go to 320.

---

### Post by yellowaeroplane on 2008-12-05
did you extract it?...

and this is my bad (I edited it right after)... the first step is "./configure," not "make". Here is everything again (with the full path to your home, but it shouldn't matter):

```

cd /home/scott/soundconverter-1.4.1
./configure
make
make install
make clean
make distclean

```

**but once again, make sure you extract the tar.gz to your home directory first!**

---

### Post by h8uthemost on 2008-12-05
Ok xjcannonx, I typed ls and the file is indeed in the home directory after I extracted(that was my bad).

yellowaeroplane, your new commands seemed to work. Terminal went through all the motions. But...Soundconverter is not showing up in my Sound & Video tab, or any other tabs for that matter. 

So, when I type soundconverter into Terminal and hit Enter, this is what I get:

scott@scott-desktop:~$ soundconverter
The program 'soundconverter' is currently not installed.  You can install it by typing:
sudo apt-get install soundconverter
bash: soundconverter: command not found
scott@scott-desktop:~$ 

So it looks like it wasn't installed.

EDIT: I just tried it again, and Terminal stops at the distclean. Then I hit Enter, and Terminal goes some more, then that's it.

---

### Post by yellowaeroplane on 2008-12-05
haha, this is turning into an adventure. As long as you didn't get any error messages while entering those commands, it should have installed.

That's exactly what I did and it magically appeared in my "Sound & Video" tab.

BUTTTT

I didn't have it installed previously, so you'll probably need to remove your previously installed version then just repeat those commands.

either do it in Synaptic or with:
```
sudo apt-get remove soundconverter
```

---

### Post by gandaran on 2008-12-05
> **yellowaeroplane said:**
> did you extract it?...

and this is my bad (I edited it right after)... the first step is "./configure," not "make". Here is everything again (with the full path to your home, but it shouldn't matter):

```

cd /home/scott/soundconverter-1.4.1
./configure
make
make install
make clean
make distclean

```

**but once again, make sure you extract the tar.gz to your home directory first!**
if you extract the package to home directory you don't have to cd to that folder, you just open terminal and run the configure (./confirure soundconverter-1.4.1)  and make commands but if the package is on desktop  you have to cd the full path (/home/'user'/Desktop) or it won't work

---

### Post by xjcannonx on 2008-12-05
you will need to put the command```
sudo
``` before make and make install

---

### Post by h8uthemost on 2008-12-05
I already removed my previous soundconverter that was installed before I even tried making the .deb package. :( So yes, this is turning into an adventure. I apologize for being a pain.

And gandaran, if I don't cd it first, and just enter, I get:

bash: ./configure: No such file or directory

---

### Post by gandaran on 2008-12-05
> **xjcannonx said:**
> you will need to put the command```
sudo
``` before make and make install
not on make, only on make install

---

### Post by h8uthemost on 2008-12-05
Yes xjcannonx! That did it! I put sudo before both and soundconverter is now in my sound and video tab. :)

---

### Post by gandaran on 2008-12-05
> **h8uthemost said:**
> I already removed my previous soundconverter that was installed before I even tried making the .deb package. :( So yes, this is turning into an adventure. I apologize for being a pain.

And gandaran, if I don't cd it first, and just enter, I get:

bash: ./configure: No such file or directory
try ./confirure soundconverter-1.4.1

---

### Post by h8uthemost on 2008-12-05
Everyone that contributed to this thread...I have to give a HUGE THANKS to you. This community is great. You guys stuck with me through the whole way. Lol.

Now, I have one final question. Can I use the above method to install **any** .tar.gz that I want?

---

### Post by xjcannonx on 2008-12-05
yeah well my bad, just maybe a habit, thanks for the correction, but yeah if you don't put "sudo" in front of "make install" then you won't have the correct permissions needed for the install and it wont install

I don't think this method works for everything but most it will, usually there are some readme files inside of a programs folder that will tell you how you should do it,

---

### Post by yellowaeroplane on 2008-12-05
hah, cool.

My bad, I didn't even realize I wasn't adding the "sudo" part... it's kind of like second nature to me... which is kind of sad I guess...

but glad you got it working, these things can be hell sometimes.

---

### Post by h8uthemost on 2008-12-05
Ok guys. Well now that I now how cd and ./configure works(I never knew what they meant about these in the readme's included in the .tar.gz), I think I'll be able to figure out how to install now.

You guys are great.

Thank you.

---

### Post by gandaran on 2008-12-05
> **h8uthemost said:**
> Everyone that contributed to this thread...I have to give a HUGE THANKS to you. This community is great. You guys stuck with me through the whole way. Lol.

Now, I have one final question. Can I use the above method to install **any** .tar.gz that I want?
not allways, different applications have different install commands, just unpack the package and read the readme file for instructions

---

