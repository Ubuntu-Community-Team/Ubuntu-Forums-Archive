---
title: "how to use chown to password protect a file"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by DarinB on 2009-07-31
How do i use chown to protect a file, i have a computer that is unattended and i need to password protect a specific file?

---

### Post by Idefix82 on 2009-07-31
You can do
```
sudo chown root:root /full/path/to/file
sudo chmod 700 /full/path/to/file 
```

The first command makes root the owner of the file, the second command says that the owner can do anything with it, while everybody else can do nothing.

---

### Post by DarinB on 2009-07-31
i made a test folder on my desktop but the commands don't work this is what i did?
sudo chown root:root /home/darin/Desktop/test folder
sudo chmod 700 /home/darin/Desktop/test folder
any ideas????

---

### Post by Idefix82 on 2009-07-31
Firstly, do you want to protect the whole folder and its content? You were talking about a file initially. To do the same thing for the whole folder and everything inside it, you need to add the -R option:

```
sudo chown -R root:root /full/path/to/file
sudo chmod -R 700 /full/path/to/file

```

Secondly, does the folder name have a space in it? Then you need to 'escape' the space. Your command should read

```
sudo chown -R root:root /home/darin/Desktop/test\ folder
sudo chmod -R 700 /home/darin/Desktop/test\ folder
```

As a general rule, it's usually better to avoid spaces in folders and in file names if you want to be able to use the terminal more fluently.

---

### Post by aysiu on 2009-07-31
> **DarinB said:**
> How do i use chown to protect a file, i have a computer that is unattended and i need to password protect a specific file?
How unattended are we talking about? And for how long?

Who will be interacting with the computer (family members and friends, or strangers)? How sensitive are these documents?

If you're away from your computer for only a few minutes and your documents aren't that sensitive but you just want to keep family members and friends from accidentally wandering into them, a simple *chown* and *chmod* will do.

In any other situation, I would advise encrypting the folder contents using TrueCrypt.

---

### Post by Liolikas on 2009-07-31
chmod and chown is maybe the hardest to understand commands.

Look:
ls -l
Then
sudo chown root:root /home/darin/Desktop/test_folder
Then:
ls -l again.
You see difference and what this command does.

Second do not use 700 use:
u - user
g -group
o - others
+ - add rights
- - remove rights
r - read
w - write
x -execute
You will see rwxrwxrwx code with ls -l. Execute directory means enter into it.
So you have to remove x for others:
sudo chmod o-x test
----
Keep in mind that ones who have sudo password they can get inside folder an see contents.

---

### Post by DarinB on 2009-07-31
darin@darin-desktop:~$ sudo chown -R root:root /home/darin/Desktop/test\ folder
[sudo] password for darin: 
chown: cannot access `/home/darin/Desktop/test folder': No such file or directory
darin@darin-desktop:~$ 
humm this is harder than i thought

---

### Post by DarinB on 2009-07-31
The computer is an old p3 in a patient treatment room for the sole purpose to view patient xrays, that are now all on disk. i need to leave the pc on so i can access the xrays quickly, but due to privacy laws the file must be password protected some how.

---

### Post by DarinB on 2009-07-31
sorry i mean folder where i put all the disks

---

### Post by Liolikas on 2009-07-31
> 
arin@darin-desktop:~$ sudo chown -R root:root /home/darin/Desktop/test\ folder
[sudo] password for darin:
chown: cannot access `/home/darin/Desktop/test folder': No such file or directory
darin@darin-desktop:~$
humm this is harder than i thought

Stop at all using " " in file folder names. Use "_" instead.
Also show (and look) ls -l then chown even I would not be able to chown thing correctly without knowing what is set already.

---

### Post by bostonaholic on 2009-07-31
> **DarinB said:**
> darin@darin-desktop:~$ sudo chown -R root:root /home/darin/Desktop/test\ folder
[sudo] password for darin: 
chown: cannot access `/home/darin/Desktop/test folder': No such file or directory
darin@darin-desktop:~$ 
humm this is harder than i thought

can we see ```
ls -l /home/darin/Desktop
```

---

### Post by iponeverything on 2009-07-31
You can right click on the folder and go to encrypt.

---

### Post by DarinB on 2009-07-31
darin@darin-desktop:~$ ls -l /home/darin/Desktop
total 75236
-rw-r--r-- 1 darin darin     3176 2009-06-22 10:36 bni roster in csv format~
-rw-r--r-- 1 darin darin      403 2009-04-16 13:11 Dr Darin Burdman Sig1~
-rw-r--r-- 1 darin darin    15963 2009-07-23 08:03 ED teleconference.odt
-rw-r--r-- 1 darin darin  5355134 2009-07-30 12:13 every gen gets to change the world.mp3
-rw-r--r-- 1 darin darin  8189476 2009-07-27 01:34 ExcusesBegone18Affirmations.pdf
-rwxrwxrwx 1 darin darin 22784877 2009-03-22 12:43 Floola
-rw-r--r-- 1 darin darin      367 2009-03-10 13:47 Hava Sig~
-rw-r--r-- 1 darin darin 40560558 2009-07-29 12:44 oops_72809_01.mp3
-rwxr-xr-x 1 darin darin      408 2009-05-31 08:46 pidgin.desktop
drwxr-xr-x 2 darin darin     4096 2009-07-31 12:37 test folder 
-rwxr-xr-x 1 darin darin      509 2009-05-26 20:04 thunderbird.desktop
drwxr-xr-x 7 darin darin     4096 2009-07-27 11:20 You Tube
darin@darin-desktop:~$

---

### Post by aysiu on 2009-07-31
Does it help if you use tab completion?

```
sudo chown -R root:root ~/Desktop/te
``` then hit **Tab** twice before hitting **Enter**?

---

### Post by Liolikas on 2009-07-31
Strange do not mess around with this on desktop try this:
```

cd
(return to /home/darin/)
mkdir test
sudo chown -R root:root test/
sudo chmod o-x test/
cd test/
(no luck because no sudo)
sudo cd test/
(tadam no acess without sudo)

```

---

### Post by DarinB on 2009-08-01
i tried again with a new folder that contains a test.odt created in the home folder
I used 
sudo chown -R root:root /home/darin/test4
then 
sudo chmod -R 700 /home/darin/test4
how do i access it???
when i click on it with the gui it says 
[I]The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "test4".[/I]
i was hoping for a password box???

---

### Post by spiderbatdad on 2009-08-01
because the folder is now owned by root and only readable by root, you cannot browse to it except as root. Launch your file browser from the terminal```
gksu nautilus
```then navigate to /home/<user name>/test4 or whatever.
browsing the file system as root can be destructive. if for example you open a system file and inadvertently delete some text or add some text...when you close the file you would be asked to save, and if you did so, the system might not work properly.

---

### Post by ayenack on 2009-08-01
You can make a custom launcher for this.

If you want to do this.

1, Right click on one of your panel bar and select Add to Panel
2, Select Custom Application Launcher
3, Make sure Application is selected in the drop down menu
4, Chose a name and enter it in the name field
5, Then in the Command field put gksudo nautilus
6, Add a comment if you want
7, Now when you click on the new icon on the panel it'll ask for your password and you'll be able to browse to the folder.

May also be wise to set the screen saver to 5mins and make it lock the screen so it'll require a your password to log log back in.

---

### Post by HiImTye on 2009-08-01
open up your file browser.
go to the folder
to the left of the boxes describing the path, click the button. this will let you copy the full path (as paths are case-sensitive).
when entering the path into the terminal, encapsulate the path with ' so it will look like '~/documents/ test folder'
this should fix your problems.

note: to paste to the terminal, highlight the path in the file browser then middle click into the terminal

---

### Post by HiImTye on 2009-08-01
you can access your folder, in a terminal by typing 'sudo su' and hitting enter. this will ask you for your password. then you can access the folder in a terminal via 'cd /home/darin/whatever' when you are done type 'exit' and it will log your root account out. *always* log out of root when you are done or your efforts to password protect are moot.

---

