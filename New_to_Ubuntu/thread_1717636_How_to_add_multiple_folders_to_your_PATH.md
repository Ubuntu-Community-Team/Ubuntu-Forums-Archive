---
title: "How to add multiple folders to your PATH ?"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by Ghost_Mazal on 2011-03-30
Lo Guys , I want to add some folders to my PATH variable in my ~/.bashrc file. It was quite easy by adding this :

```
PATH=$PATH:/home/backupuser
export PATH
```

But what must I add if I want to add 3 or 4 other folders as well ?

Thanx

---

### Post by Paddy Landau on 2011-03-30
You can abbreviate the command into a single one, as follows.
```
export PATH=${PATH}:/first/path:/second/path:/third/path
```

---

### Post by Ghost_Mazal on 2011-03-30
Doesn't work.

When I test with echo $PATH it still only shows just the first folder

---

### Post by Paddy Landau on 2011-03-30
Are you writing the PATH command in the same terminal session as you are using it? If you perform the PATH command, then close the terminal, the change is lost.

If you are using the same session, please post your exact command (cut-and-paste), followed by your echo command showing the results.

---

### Post by Ghost_Mazal on 2011-03-30
It is placed in my ~/.bashrc file and bashrc reloaded with

```
source .bashrc
```

Here is the extract from my .bashrc file

```
export PATH=${PATH}:/home/backupuser:/home/wikusv:/home/barrydk
```

I have read and write permissions to all those folders.

After I reloaded my .bashrc with

```
source .bashrc
```

I test it with

```
echo $PATH
```

And it only shows all the system defaults (the bin folders) and the very first folder there in the list. (/home/backupuser)
The other two are not shown at all.

---

### Post by Paddy Landau on 2011-03-30
I find this puzzling. I started a terminal session; copied your line into my .bashrc; ran *source .bashrc*; and it worked perfectly for me.


[LIST=1]
[*] In your .bashrc file, immediately after your export command, enter the following command:
```
echo 'Here I am'
```
[*]Save the file.
[*] Close your terminal.
[*] Open a new terminal. Do you see "Here I am"?
[/LIST]

---

### Post by Ghost_Mazal on 2011-03-30
Ok hang on. I completely logged out now and logged back in. Now it shows correctly. So it's the command

```
source .bashrc
```

That didn't load the changes correcly :confused:

Strange

---

### Post by Ghost_Mazal on 2011-03-30
That echo of yours works as well.

Anyway , your command in bashrc works thanx a lot.
It was just that I had to log out and log in again and not only run
the source command. ;)

---

### Post by Paddy Landau on 2011-03-30
It's hard to say in retrospect, but you have it now.

Usually, when I change .bashrc, I close the existing terminal and open a new one.

You shouldn't have had to log out and back in; I wonder if there was some error from a previous invocation?

---

### Post by M1GEO on 2011-07-08
Similar problem.  I adjusted the system path on my box to include the Android SDK stuff.  This is located on my machine in /opt/google/sdk, with the specific binaries in /opt/google/sdk/platform-tools/.

I edited the master path file, /etc/environment to reflect this:

```
george@diode:~$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/google/sdk/platform-tools"

```

This is then reflected after a reboot:

```
george@diode:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/google/sdk/platform-tools
```

Running a program, such as the Android Debugger Bridge (/opt/google/sdk/platform-tools/adb) as a normal user (here, "george") works fine

```
george@diode:~$ adb
Android Debug Bridge version 1.0.26
(... output chopped off ...)

```

**However, this needs to be run as root, and this is where I get problems...**

```
george@diode:~$ sudo adb
[sudo] password for george: *<super_secret_password>*
sudo: adb: command not found

```

*sudo* seems to see the right path, but never finds the application.  

```
george@diode:~$ sudo echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/google/sdk/platform-tools

```

Can anyone help with this?  It's not an issue, as I can *sudo -s* and set the path up manually, but every time I close the terminal (dropping sudo -s out), I obviously loose it.  Driving me mad!

Cheers all

---

### Post by wojox on 2011-07-08
Did you reload:

```
source /etc/environment
```

---

