---
title: "Having problems changing directories in Terminal"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Lostin60's on 2009-01-10
Adrian Nania has a post to help Evolution work with Yahoo.(I can send, but not recieve) Here is a bit of her post.
> # HOWTO: Send and Receive Yahoo through Evolution
# from [http://www.geocities.com/t_skariah/ypops/](http://www.geocities.com/t_skariah/ypops/)
cd /home/work/src/email/ypops/install
wget [http://tskariah.net78.net/t_skariah.asc.gpg](http://tskariah.net78.net/t_skariah.asc.gpg)
sudo apt-key add t_skariah.asc.gpg
sudo su
cat >>/etc/apt/sources.list<<"EOF"
deb [http://tskariah.net78.net/ubuntu](http://tskariah.net78.net/ubuntu) ubuntu main
EOF
exit
As you can see, the first command is to change dirs. I know this path exists, because I had to build it.  However..this is my prompt on a freshly opened terminal.
> daniel@GLENDA:~$ 

I assume the above is the root folder, and the equivalent of C: in Windows. Among the dirs in there is a folder called "root", I know. But I can't help but thinking of "file system" as root. I assume that one needs to go up the dir tree one dir at a time.  So, this
```
daniel@GLENDA:~$ cd /home
daniel@GLENDA:/home$ 

```
makes sense. As expected I am in "home", which contains only "daniel", which is why the following confuses me.
```
daniel@GLENDA:/home$ cd /daniel
bash: cd: /daniel: No such file or directory

```
or
```
bash: cd/home/daniel: No such file or directory
daniel@GLENDA:/home$
```
What am I doing wrong? I didn't think you could screw up a "cd" command, but here I am.  Any and all help will be appreciated. While I await an answer, I am going to go get a dunce cap.
[COLOR="White"]aa[/COLOR]

---

### Post by ShutterAce on 2009-01-10
Try cd daniel not cd /daniel

cd daniel = /home/daniel

cd /daniel = /daniel

---

### Post by JoshuaRL on 2009-01-10
And try just moving there directly.  You really don't need to change each directory individually.  So try:
```

cd /home/work/src/email/ypops/install

```

---

### Post by namdung on 2009-01-10
U need to get ur basics right on **Absolute** & **Relative paths**.
Read here:
[http://ubuntuforums.org/showthread.php?t=1022200&page=2](http://ubuntuforums.org/showthread.php?t=1022200&page=2)

Do write if u need more clarity on this concept.

---

### Post by Lostin60's on 2009-01-10
First off, thank you ShutterAce, your post put me right on track.  And the heck of it is, I already knew that. I mean I knew if you were in X and wanted to go to Y you would type "cd y" not "cd /y" I think my prob was that I didn't know I was in X.

To JoshuaRL
```
daniel@GLENDA:~$ cd /home/work/src/email/ypops/install
bash: cd: /home/work/src/email/ypops/install: No such file or directory
daniel@GLENDA:~$ 
```
I believe this is because at this prompt I am already at /home/daniel that is to say file system/home/daniel. If I reset and clear the terminal I have only a cursor which is file system or /, and from there this is needed
```
cd home/daniel/work/src/email/ypops/install
daniel@GLENDA:~/work/src/email/ypops/install$
```
No / in front of home, as it is the next dir up.

And to namdung, I feel I am correct in saying that an Absolute path is from / to X. X being the dir you want to get to. A Relative path is from "where you are" to X. Also, if you are half way to X already, you have to use a Relative path.  Examples from a freshly opened terminal
```
daniel@GLENDA:~$ cd home
bash: cd: home: No such file or directory
daniel@GLENDA:~$ 
```
Doesn't work because I am already in home/daniel
```
daniel@GLENDA:~$ cd /work
bash: cd: /work: No such file or directory
daniel@GLENDA:~$
```
Doesn't work, because work is in the daniel dir so no / is needed.
```
daniel@GLENDA:~$ cd work
daniel@GLENDA:~/work$ 
``` is correct
Now for a reset and cleared terminal
```
&#9612;
``` Above is my freshly reset terminal. At this point I am at /.
```
pwd
/
daniel@GLENDA:/$ 

```
Below is where I get confused
```
[COLOR="Red"]daniel@GLENDA[/COLOR][COLOR="DarkOrange"]:[/COLOR][COLOR="Yellow"]~[/COLOR][COLOR="Blue"]$[/COLOR] 
```
My assumptions on the above:
[COLOR="Red"]My username at my computer name[/COLOR] Just an identifier
[COLOR="DarkOrange"]A statement that the previous statement is true[/COLOR] From what I have read a ":" is the same as a return of true.
[COLOR="Yellow"]Indicates that I am 2 dirs above /[/COLOR]
[COLOR="Blue"]Is a variable, and I think it is defined by the previous character or word.[/COLOR]
 So the whole thing means I am daniel on the computer GLENDA...yes, that's true..I am in the dir home/daniel...In this instance I am defined by the previous dir, but can be defined by any dir. I think that is close anyway.  
So, my thanks to all who helped, it is greatly appreciated. And if you would comment on all this, namdung, I would be very grateful.
[COLOR="White"]aa[/COLOR]

---

### Post by HotCupOfJava on 2009-01-10
A couple more easy tips:

"cd .." takes you back up 1 directory.

"ls" will show you files and subdirectories in the current directory (so you can see what subdirectories you can "cd" too).

---

### Post by HotCupOfJava on 2009-01-10
The "name@name" is the HOME directory of the user that is logged in, but NOT the same as the root directory. You can navigate to directories above it by typing "cd ..".

You can return to the home directory from anywhere by typing "cd ~".

---

### Post by Slowspeed on 2009-01-10
> **Lostin60's said:**
> Adrian Nania has a post to help Evolution work with Yahoo.(I can send, but not recieve) Here is a bit of her post.

As you can see, the first command is to change dirs. I know this path exists, because I had to build it.  However..this is my prompt on a freshly opened terminal.

I assume the above is the root folder, and the equivalent of C: in Windows. Among the dirs in there is a folder called "root", I know. But I can't help but thinking of "file system" as root. I assume that one needs to go up the dir tree one dir at a time.  So, this
```
daniel@GLENDA:~$ cd /home
daniel@GLENDA:/home$ 

```
makes sense. As expected I am in "home", which contains only "daniel", which is why the following confuses me.
```
daniel@GLENDA:/home$ cd /daniel
bash: cd: /daniel: No such file or directory

```
or
```
bash: cd/home/daniel: No such file or directory
daniel@GLENDA:/home$
```
What am I doing wrong? I didn't think you could screw up a "cd" command, but here I am.  Any and all help will be appreciated. While I await an answer, I am going to go get a dunce cap.
[COLOR="White"]aa[/COLOR]

I find this to be a useful reference - [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

Regards,

---

### Post by handydan918 on 2009-01-10
Anytime you want to know where you are, do ```
pwd
```

(Print Working Directory)

If you start ssh-ing around you can even lose track of which machine you're on. Then you can ```
w
```

which will give you output like this:

```
daniel@500x2:~$ w
 23:04:15 up 2 days,  1:29,  2 users,  load average: 0.01, 0.04, 0.01
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
theresa  :0       -                Thu21   ?xdm?   1:15   0.02s /bin/sh /usr/bin/x-session-manager
daniel   pts/1    amdx2.local      23:04    0.00s  0.16s  0.00s w

```

I've gotten good and "bewildered" like that...

---

### Post by sp0nge on 2009-01-10
The list command has already been exposed here, but I have to reiterate and emphasize it a little more. I came to Ubuntu from a fairly extensive windows background and it took me a while to wrap my mind around the command line. 

ls, the list command, has been a life saver for me in terms of navigation. When I change directories, I obviously know where I want to go, so by cd'ing one directory at a time and ls'ing to see what's available I found my way. 

In addition to this, using the command updatedb will make the system aware of all current file locations. When you follow that up with locate <filename>, you can then identify the path you need, and move there one directory at a time until you are comfortable with directing the path in one command. 

I also have to mention that when you're navigating, use of the "tab tap" becomes quite useful. It goes like this:

```
[me@linuxbox me]$cd /home
[me@linuxbox home]$ls
Peter    Ringo   John    me
[me@linuxbox home]$
```

Now these are simple names, but directory and file can become long. Rather than having to type the whole thing out, simply input the first 3 letters, and "tab tap" (hit tab twice) to bring up the nearest corresponding file.

Learning the command line was difficult for me coming from a GUI world. But once I caught on, it was so liberating to cut multiple mouse clicks down to a line of code. 

I hope this helps.

---

### Post by bodhi.zazen on 2009-01-10
@ [Lostin60's]("http://ubuntuforums.org/member.php?u=711159")

The problem you are having is with typos.

Your home directory is /home/username 

or in your examples 

/home/daniel

/home/daniel can be abbreviated in a number of ways 

~
$HOME
~daniel

The full path starts with /

If you are in your home directory , ie /home/daniel

you can cd to /home**/daniel**/work/src/email/ypops/install

with

#Full path
cd /home/daniel/work/src/email/ypops/install

OR

#Relative path, ie relative to your current location, output of pwd
cd work/src/email/ypops/install


Also, to reduce typos

# this command will bring you from anywhere to your home directory
cd

# This will bring you to your last directory
cd -

**use tab completion**

ie, hit the tab key 

cd /ho<tab>jon<tab>work/src/em<tab> 

You get the idea, it reduces the errors you get from typos. Works for files as well.

---

### Post by Lostin60's on 2009-01-11
Wow! I haven't been back to this post in a few days.  My thanks to all for the great advice. Once I got myself on the right track, I pretty much learned the bulk of what is posted here. (That in no way diminishes my appreciation for the posts) I have a little file with handy things to know, and I plan to put a good bit of advice from this thread in it. I love the way folks respond to questions in here. I am beginning to learn C++, and plan to get conversant enough with Linux that I can ditch windows. These forums are Ringo's dream. I can get by with a little help from my friends..lol. Again, thanks to all.
[COLOR="White"]aa[/COLOR]

---

