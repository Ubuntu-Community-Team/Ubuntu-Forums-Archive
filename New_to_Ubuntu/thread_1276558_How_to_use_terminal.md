---
title: "How to use terminal?"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by Lil Josh on 2009-09-27
Well, my terminal wasn't working at first. So, I did something, I really don't know what, and now it's working fine. But, when I tried to run a command such as:

>  
/RS3/Client/run.sh


I tried that and it didn't work. All it said was,

> 
bash: /RS3/Client/run.sh: No such file or directory


Any help?

---

### Post by themusicalduck on 2009-09-27
To run a shell script, you must use the sh command in front.

```
sh /RS3/Client/run.sh
```

---

### Post by Perfect Storm on 2009-09-27
```
cd RS3/Client
./run.sh
```

---

### Post by Lil Josh on 2009-09-27
Now it says:

> 
sh: /Can't open RS3/Client/run.sh


Now what? o.O

---

### Post by JillSwift on 2009-09-27
> **Lil Josh said:**
> Now it says:



Now what? o.O
Does that script exist?

______EDIT______

Make sure by ls -l RS3/Client/
or ls -l /RS3/Client/
Whichever actually points to a directory.

Make sure it's executable by you, too. (Post the results of the above if you need help reading the output to find if it's executable by you.)

---

### Post by Joeb454 on 2009-09-27
That command implies that the RS3 directory is in the / directory (root directory) of your drive.

Where on the disk is it located?

---

### Post by Lil Josh on 2009-09-27
It's on the desktop in a file. Want a screenshot? It's not a disk though.

---

### Post by grturner on 2009-09-27
chmod +x /RS3/Client/run.sh 

of course if the script wasn't executable

---

### Post by Joeb454 on 2009-09-27
If the file exists in your desktop directory, try running ```
sh ~/Desktop/RS3/Client/run.sh
``` That should work

---

### Post by grturner on 2009-09-27
if it is on your desktop...

the proper directory is /home/username/Desktop/RS3/Client/run.sh

---

### Post by Lil Josh on 2009-09-27
Still says,

> 
Can't open /home/gabe/Destop/RS3/Client/run.sh


---

### Post by grturner on 2009-09-27
what exactly are you trying to do? It sounds like the file doesn't exist.

---

### Post by Joeb454 on 2009-09-27
> **grturner said:**
> It sounds like the file doesn't exist.

+1

What's the output of ```
ls ~/Desktop
```?

---

### Post by grturner on 2009-09-27
if you had extracted the archive that contained RS3 using sudo tar, it would set the files to be owned by root not yourself and therefor you couldn't access them unless you fixed file ownership.

---

### Post by Lil Josh on 2009-09-27
I downloaded a Client to play on. Then I extracted it to winrar and extracted the files to my desktop. Then I clicked on, "run.sh" and nothing came up. I asked how to let it run on these forums I go on a lot and they said to let it run in terminal. I've been trying that and it doesn't seem to work. The run.sh is in my RS3ClientV12 File. So, now I'm stuck.

---

### Post by grturner on 2009-09-27
```
cd ~/Desktop/RS/ & ls -la 
```

post the output

---

### Post by Lil Josh on 2009-09-27
> **Joeb454 said:**
> +1

What's the output of ```
ls ~/Desktop
```?

ls: cannot access ~Desktop: No such file or directory

---

### Post by Perfect Storm on 2009-09-27
It's properly because you use another language than English, right?

If you use a diffrent language you have to switch the word Desktop out with the one with your language.

---

### Post by grturner on 2009-09-27
> **Lil Josh said:**
> ls: cannot access ~Desktop: No such file or directory

You didn't separate ~ and Desktop with / it needs to be

~/Desktop

---

### Post by Joeb454 on 2009-09-27
> **Artificial Intelligence said:**
> It's properly because you use another language than English, right?

If you use a diffrent language you have to switch the word Desktop out with the one with your language.

That, or it looks like you missed the / between ~ and "Desktop", which would also throw that error

Edit: Too late :)

---

### Post by Lil Josh on 2009-09-27
> **grturner said:**
> ```
cd ~/Desktop/RS/ & ls -la 
```post the output


Ugh, how would I post the outcome of this? I can't copy and paste it..

---

### Post by Joeb454 on 2009-09-27
You can, but if you prefer, run it again but as ```
cd ~/Desktop/RS/ & ls -la > ~/Desktop/output.txt
``` Then upload or copy/paste the contents of the output.txt file on your desktop :)

---

### Post by Bölvaður on 2009-09-27
> **Lil Josh said:**
> ls: cannot access ~Desktop: No such file or directory

lol I can see a big problem right there.



Lets say that it might be correct to use **sh** and lets assume that this is the correct file, but perhaps not at the same location as you might think or with different permissions.


1. Run the script:

- Copy the file (right click it and select copy) and open the terminal.
- type **sh** and right click and press **Paste Filenames**
- press enter


Did it work?
- Yes : good :)
- No : what did the error output say?

2. Give your self all permissions to do what ever you want with that file.

Change the owner of the file to you (just to be 100% sure)
```
sudo chown ***<your user name here!>**   <right click and press **Paste Filenames**>*
```
an example of this : $ sudo chown Bölvaður '/home/Bölvaður/Desktop/base.c'

and then allow your self to do what ever you want with it:
```
sudo chmod 777 <right click and press **Paste Filenames**>
```
Example: $ chmod 777 '/home/Bölvaður/Desktop/base.c' 

go to step 1.

---

### Post by Michael.Godawski on 2009-09-27
To copy from the terminal use:


[LIST]
[*]Ctrl+Shift+C
[/LIST]

---

### Post by jocko on 2009-09-27
> **Lil Josh said:**
> Ugh, how would I post the outcome of this? I can't copy and paste it..
Why can't you copy and paste it?

---

### Post by Lil Josh on 2009-09-27
> **grturner said:**
> ```
cd ~/Desktop/RS/ & ls -la 
```post the output

```

[1] 8415
bash: cd: /home/gabe/Desktop/RS/: No such file or directory
total 412
drwxr-xr-x 46 gabe gabe  4096 2009-09-27 10:29 .
drwxr-xr-x  4 root root  4096 2009-09-11 00:07 ..
drwx------  5 gabe gabe  4096 2009-03-04 16:11 .adobe
-rw-------  1 gabe gabe    80 2009-09-27 09:49 .bash_history
-rw-r--r--  1 gabe gabe   220 2009-01-31 09:31 .bash_logout
-rw-r--r--  1 gabe gabe  2940 2009-01-31 09:31 .bashrc
drwx------  2 gabe gabe  4096 2009-02-08 21:07 .bogofilter
-rw-r--r--  1 gabe gabe   131 2009-09-23 02:34 Bored.html
-rw-r--r--  1 gabe gabe   145 2009-09-23 02:27 Bored.html~
drwxr-xr-x  8 gabe gabe  4096 2009-09-17 01:31 .config
-rw-r--r--  1 gabe gabe  9312 2009-09-15 00:07 CSS for DTAScape~
drwxr-xr-x  3 gabe gabe 12288 2009-09-27 10:41 Desktop
-rw-------  1 gabe gabe     2 2009-09-27 09:24 .dmrc
-rw-r--r--  1 gabe gabe    76 2009-09-26 20:57 document.js
-rw-r--r--  1 gabe gabe    76 2009-09-26 20:55 document.js~
-rw-r--r--  1 gabe gabe  3589 2009-09-17 20:34 Dragons.html~
-rw-r--r--  1 gabe gabe  3589 2009-09-17 20:32 Dragons.html~~
-rw-------  1 gabe gabe    16 2009-01-31 09:32 .esd_auth
drwxr-xr-x  8 gabe gabe  4096 2009-09-23 02:40 .evolution
drwxr-xr-x  2 gabe gabe  4096 2009-09-15 00:27 .fontconfig
drwx------  6 gabe gabe  4096 2009-09-27 09:24 .gconf
drwx------  2 gabe gabe  4096 2009-09-27 10:31 .gconfd
drwx------  2 gabe gabe  4096 2009-01-31 21:28 .ggz
drwxr-xr-x 22 gabe gabe  4096 2009-09-23 02:40 .gimp-2.4
-rw-r-----  1 gabe gabe     0 2009-09-20 03:04 .gksu.lock
drwxr-xr-x 20 gabe gabe  4096 2009-09-27 09:20 .gnome2
drwx------  2 gabe gabe  4096 2009-01-31 09:32 .gnome2_private
drwx------  2 gabe gabe  4096 2009-09-27 09:24 .gnupg
drwxr-xr-x  2 gabe gabe  4096 2009-09-10 00:40 .gpilotd
-rw-r--r--  1 gabe gabe     4 2009-09-10 23:07 .gpilotd.pid
drwxr-xr-x  2 gabe gabe  4096 2009-01-31 09:32 .gstreamer-0.10
-rw-r--r--  1 gabe gabe     0 2009-09-20 04:37 .gtk-bookmarks
dr-x------  2 gabe gabe     0 2009-09-27 09:24 .gvfs
-rw-r--r--  1 gabe gabe   108 2009-09-19 02:24 Halo 3:ODST.html~
-rw-------  1 gabe gabe  9300 2009-09-27 09:24 .ICEauthority
drwxr-xr-x  2 gabe gabe  4096 2009-01-31 17:06 .icons
-rw-r--r--  1 gabe gabe     0 2009-09-20 11:56 ItemColors.txt
drwxr-xr-x  4 gabe gabe  4096 2009-02-13 18:27 .jagex_cache_32
-rw-r--r--  1 gabe gabe    45 2009-09-27 02:59 jagex_runescape_preferences2.dat
-rw-r--r--  1 gabe gabe    38 2009-09-27 04:46 jagex_runescape_preferences.dat
drwxr-xr-x  3 gabe gabe  4096 2009-01-31 17:18 .java
drwx------  3 gabe gabe  4096 2009-01-31 09:35 .kde
drwx------  3 gabe gabe  4096 2009-01-31 09:32 .local
drwx------  3 gabe gabe  4096 2009-01-31 17:04 .macromedia
drwxr-xr-x  3 gabe gabe  4096 2009-01-31 09:37 .mcop
-rw-------  1 gabe gabe    31 2009-03-04 16:22 .mcoprc
drwx------  3 gabe gabe  4096 2009-01-31 09:32 .metacity
drwxr-xr-x  4 gabe gabe  4096 2009-02-08 20:57 .mozilla
drwxr-xr-x  3 gabe gabe  4096 2009-09-23 02:40 .nautilus
drwx------  3 gabe gabe  4096 2009-09-05 21:50 .openoffice.org2
-rw-r--r--  1 gabe gabe   598 2009-09-19 02:45 PoV.html~
drwxr-xr-x  2 gabe gabe  4096 2009-01-31 04:33 .ppracer
-rw-r--r--  1 gabe gabe   586 2009-01-31 09:31 .profile
drwxr-xr-x  2 gabe gabe  4096 2009-01-31 21:28 .pulse
-rw-------  1 gabe gabe   256 2009-01-31 09:32 .pulse-cookie
drwx------  6 gabe gabe  4096 2009-09-27 10:31 .purple
drwxr-xr-x  2 gabe gabe  4096 2009-01-31 09:36 .qt
-rw-------  1 gabe gabe  8742 2009-08-25 14:33 .recently-used
-rw-r--r--  1 gabe gabe 84391 2009-09-27 10:29 .recently-used.xbel
drwx------  2 gabe gabe  4096 2009-01-31 09:32 .ssh
drwxr-xr-x  2 gabe gabe  4096 2009-01-31 09:52 .stellarium
-rw-r--r--  1 gabe gabe     0 2009-01-31 09:32 .sudo_as_admin_successful
drwxr-xr-x  4 gabe gabe  4096 2009-02-01 19:03 .sudoku
drwxr-xr-x  2 gabe gabe  4096 2009-01-31 17:06 .themes
drwx------  5 gabe gabe  4096 2009-08-29 16:06 .thumbnails
drwxr-xr-x  5 gabe gabe  4096 2009-02-06 21:42 .transmission
drwx------  2 gabe gabe  4096 2009-09-22 19:04 .tsclient
drwxr-xr-x  2 gabe gabe  4096 2009-02-01 21:51 .tuxmath
drwxr-xr-x  2 gabe gabe  4096 2009-01-31 09:52 .tuxpaint
drwxr-xr-x  2 gabe gabe  4096 2009-02-08 20:54 .update-manager-core
drwx------  2 gabe gabe  4096 2009-02-08 21:00 .update-notifier
drwxr-xr-x  2 gabe gabe  4096 2009-08-29 16:08 .wapi
drwxr-xr-x  4 gabe gabe  4096 2009-09-27 09:25 .wine
-rw-------  1 gabe gabe   115 2009-09-27 09:24 .Xauthority
-rw-r--r--  1 gabe gabe 19896 2009-09-27 10:41 .xsession-errors
[1]+  Exit 1                  cd ~/Desktop/RS/

```That's the output.

> 
                     Originally Posted by **Joeb454**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8015153#post8015153")                 
                 [I]+1

What's the output of      Code:
     ls ~/Desktop[FONT=Verdana]
[/FONT]

[/I]
?
```

CoDMW2~            page1.htm~           POV.htm~    RS3ClientV12
Halo 3:ODST.html~  page2.htm~           PoV.html~   RS3ClientV12.rar
mainpage.htm~      Point of View.html~  PoV.html~~  WinRAR.desktop
output.txt         PoV.htm~             Prank.vbs~

```[quote=Bölvaður]
lol I can see a big problem right there.



Lets say that it might be correct to use **sh** and lets assume that this is the correct file, but perhaps not at the same location as you might think or with different permissions.


1. Run the script:

- Copy the file (right click it and select copy) and open the terminal.
- type **sh** and right click and press **Paste Filenames**
- press enter


Did it work?
- Yes : good :smile:
- No : what did the error output say?

2. Give your self all permissions to do what ever you want with that file.
[/quote]

```

Change DIR Value!
cd: 4: can't cd to /mnt/sda1/Users/Subasteve/Documents/Dev/NewStart
/home/gabe/Desktop/RS3ClientV12/run.sh: 5: function: not found
: not foundDesktop/RS3ClientV12/run.sh: 6: clear
---------------------[ Client Run ]--
Exception in thread "main" java.lang.NoClassDefFoundError: Bot
Caused by: java.lang.ClassNotFoundException: Bot
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
: not foundDesktop/RS3ClientV12/run.sh: 9: client
: not foundDesktop/RS3ClientV12/run.sh: 10: }
/home/gabe/Desktop/RS3ClientV12/run.sh: 11: function: not found
---------------------[ Client Compile ]--
/home/gabe/Desktop/RS3ClientV12/run.sh: 13: javac: not found
/home/gabe/Desktop/RS3ClientV12/run.sh: 41: Syntax error: "elif" unexpected (expecting "then")

```

There. Tell me what you guys think now.

---

### Post by Lil Josh on 2009-09-27
> **Bölvaður said:**
> 
Change the owner of the file to you (just to be 100% sure)
```
sudo chown ***<your user name here!>****   <right click and press **Paste Filenames**>*
```an example of this : $ sudo chown Bölvaður '/home/Bölvaður/Desktop/base.c'

and then allow your self to do what ever you want with it:
```
sudo chmod 777 <right click and press **Paste Filenames**>
```Example: $ chmod 777 '/home/Bölvaður/Desktop/base.c' 

go to step 1.

```

[sudo] password for gabe: 

```

It won't let me type the pass for gabe. It says Gabe because I'm using his access card from his laptop. Mine got fried, so I switched mine with his.

---

### Post by Joeb454 on 2009-09-27
> **Lil Josh said:**
> ```

[sudo] password for gabe: 

```

It won't let me type the pass for gabe. It says Gabe because I'm using his access card from his laptop. Mine got fried, so I switched mine with his.

The password is never shown, type in the password and hit enter, if it's correct, it will work :)

---

### Post by Lil Josh on 2009-09-27
> **Joeb454 said:**
> The password is never shown, type in the password and hit enter, if it's correct, it will work :)

I type in the password and it says nothing, but the title appeared only. Nothing else. Does that mean it worked or no?

---

### Post by Bölvaður on 2009-09-27
> **Lil Josh said:**
> 

```

Change DIR Value!
cd: 4: can't cd to /mnt/sda1/Users/Subasteve/Documents/Dev/NewStart
/home/gabe/Desktop/RS3ClientV12/run.sh: 5: function: not found
: not foundDesktop/RS3ClientV12/run.sh: 6: clear
---------------------[ Client Run ]--
Exception in thread "main" java.lang.NoClassDefFoundError: Bot
Caused by: java.lang.ClassNotFoundException: Bot
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
: not foundDesktop/RS3ClientV12/run.sh: 9: client
: not foundDesktop/RS3ClientV12/run.sh: 10: }
/home/gabe/Desktop/RS3ClientV12/run.sh: 11: function: not found
---------------------[ Client Compile ]--
/home/gabe/Desktop/RS3ClientV12/run.sh: 13: javac: not found
/home/gabe/Desktop/RS3ClientV12/run.sh: 41: Syntax error: "elif" unexpected (expecting "then")

```

There. Tell me what you guys think now.

The problem isn't with the commands you enter. It's with the file.

Copy it to YOUR desktop, as it is currently located in /mnt/sda1/Users/Subasteve/Documents/Dev/NewStart
/home/gabe/Desktop/RS3ClientV12/, which I guess is on another harddisk you just plugged in.

ok now it is time to think. btw where can I find this file so I can test it out my self?

---

### Post by grturner on 2009-09-27
the proper directory that you need to be working in is ~/Desktop/RSClientV12/

we were working off the assumption that it was ~/Desktop/RS/

so my educated guess as to what the command would be is
```
cd ~/Desktop/RSClientV12/ & sh run.sh 
```

---

### Post by Bölvaður on 2009-09-27
> **Lil Josh said:**
> I type in the password and it says nothing, but the title appeared only. Nothing else. Does that mean it worked or no?

While you type your password it will not show you (or the person trying to see your password over your shoulder) if you press a key or not, it will just remember what you wrote but not show any sign of you typing anything.

Example:

Bölvaður@Friday:~$ sudo su
[sudo] password for Bölvaður:
root@Friday:/home/Bölvaður# 

notice that in the middle where I am asked to type in password it doesnt show anything. I **blindly type** the password and press enter.

---

### Post by Lil Josh on 2009-09-27
> **grturner said:**
> the proper directory that you need to be working in is ~/Desktop/RSClientV12/

we were working off the assumption that it was ~/Desktop/RS/

so my educated guess as to what the command would be is
```
cd ~/Desktop/RSClientV12/ & sh run.sh 
```

Question. Why do all of you keep saying, "cd", when I didn't even use CD to install Ubuntu onto my laptop?

Also, the code didn't work. I also tried, 

```

cd ~/Desktop/RS3ClientV12/ & sh run.sh 

```

And got;

```

[1] 5935
sh: Can't open run.sh
[1]+  Done                    cd ~/Desktop/RS3ClientV12

```

Anything else I could do to fix it?

---

### Post by Perfect Storm on 2009-09-27
cd is a command.

cd = change directory

---

### Post by Lil Josh on 2009-09-27
> **Bölvaður said:**
> The problem isn't with the commands you enter. It's with the file.

Copy it to YOUR desktop, as it is currently located in /mnt/sda1/Users/Subasteve/Documents/Dev/NewStart
/home/gabe/Desktop/RS3ClientV12/, which I guess is on another harddisk you just plugged in.

ok now it is time to think. btw where can I find this file so I can test it out my self?

Ugh.. Is it advertising if I do put the link here to get the file? 

Here it is:

[http://uppit.com/v/9UKATY7N](http://uppit.com/v/9UKATY7N) 

After clicking download, select open. Your download will begin straight away. After your download is complete, you should see a screen: When this opens, just select extract to. After selecting extract to; you will see a box pop up. Just select desktop and then click ok. After clicking ok, your downloaded client will be on your desktop under the name of, "rs3clientv12".

If you could find a way to open it when it says, "run.sh", I would more than appreciate it. Thanks.

> 
The problem isn't with the commands you enter. It's with the file.

Copy it to YOUR desktop, as it is currently located in /mnt/sda1/Users/Subasteve/Documents/Dev/NewStart
/home/gabe/Desktop/RS3ClientV12/, which I guess is on another harddisk you just plugged in.


What do you mean? Copy what to my desktop? The run.sh file?

---

### Post by Lil Josh on 2009-09-27
Ugh.. Would anybody be able to help me out with it? Sorry for double posting. Just read the previous post to know what I need help with.

---

