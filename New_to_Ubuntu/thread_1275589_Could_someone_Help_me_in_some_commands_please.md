---
title: "Could someone Help me in some commands please?"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by vlad1975 on 2009-09-26
Hello,

Im trying to get to a directory in wine

This is what i tried

ed@ed-desktop:~$ cd /home/ed/.wine/dosdevices/c:/Program Files/City of Heroes
bash: cd: /home/ed/.wine/dosdevices/c:/Program: No such file or directory
ed@ed-desktop:~$ cd /home/ed/.wine/dosdevices/c:/
[email]ed@ed-desktop:~/.wine[/email]/dosdevices/c:$ \Program Files
bash: Program: command not found
[email]ed@ed-desktop:~/.wine[/email]/dosdevices/c:$ /Program Files
bash: /Program: No such file or directory
[email]ed@ed-desktop:~/.wine[/email]/dosdevices/c:$ ls
~GLHTTP1.TMP  Program Files  windows
[email]ed@ed-desktop:~/.wine[/email]/dosdevices/

The Full Path that im trying to get into is /home/ed/.wine/dosdevices/c:/Program Files/City of Heroes/

I am trying to run it in Terminal so i can see where the error is coming from as when i attempt to run it it crash on update..


Could someone help me please?

---

### Post by elliotn on 2009-09-26
isnt it```
wine gamename
``` i dont know am not sure

---

### Post by Cresho on 2009-09-26
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2980](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2980)

here is how you execute it..

so you cd into that directory where you want to execute the file

then you do an ls to make sure you can see your files or exe.  if it displays it in the terminal, then your good to go

then you ```
cd "/home/ed/.wine/dosdevices/c:/Program Files/City of Heroes/"
ls
gnome-terminal --execute wine VirtualDub.exe
```

change virtualdub to your game exe name

---

### Post by vlad1975 on 2009-09-26
Cresho thanx dude but im still not able to get to the folder where the CityOf Heroes.exe is in

the furthest i can get in to is 
ed@ed-desktop:~$ cd /home/ed/.wine/dosdevices/c:
and it takes me here
ed@ed-desktop:~$ cd /home/ed/.wine/dosdevices/c:


But when i try to get in to 
cd /home/ed/.wine/dosdevices/c:/Program Files
gives me this error
bash: cd: /home/ed/.wine/dosdevices/c:/Program: No such file or directory

---

### Post by Cresho on 2009-09-26
ya you got to learn how to follow directions.  Look at my command

if you see cd /dir/dir then you get the dir dir

but

if you see cd /dir/d i r  you will get error because spaces.

so

you cd "/dir/d i r"  and it will take you to the directory

notice i put quotation marks.  look closer and you will get there

now a new one for you, if you ever see a 

#cd /dir 

the pound sign prevents the command from executing so sometimes you will see people type like

#cd /home

instead of
cd /home/username
or
cd ~

if you ever save commands in gnome, you can execute a txt file when the pop up windows asks you so it is always safe to put pound infront of the line to prevent if from executing.

I once had this command that copied useless stuff to my home directory and that was a mess.  Total mess.

---

### Post by vlad1975 on 2009-09-26
Sorry did not see the space and dot on the command
cheers i got what i need..

Processing argument list:
Patchserver: cohupdate.coh.com

fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
fixme:wininet:InternetLockRequestFile STUB
Handling full manifest
Fixing files: piggs/misc.pigg4G 731901:01:46 Remaining
Error calling setsockopt, ending socket buffer size is not what we told it! (16384!=32768)
Error calling setsockopt, ending socket buffer size is not what we told it! (32768!=65536)
Error calling setsockopt, ending socket buffer size is not what we told it! (65536!=131072) 

Gonna bug Wine community now :) thanx again sorry if i irritate u

---

### Post by scorp123 on 2009-09-26
> **vlad1975 said:**
>  But when i try to get in to 
cd /home/ed/.wine/dosdevices/c:/Program Files

gives me this error
bash: cd: /home/ed/.wine/dosdevices/c:/Program: No such file or directory Of course it does. Because the space between "Program" and "Files" is being misinterpreted. Either 'escape' that space or put stuff in quotation marks. Or even easier -- start typing and then hit the *TAB* key and the shell will automagically guess what you're trying to type.

Escaping the space:
```
cd /home/ed/.wine/dosdevices/c:/Program\ Files
``` Yes, that's a backslash. It "escapes" the space that follows it and tells the shell "don't interpret this as a separate command, just keep going".

Quotation marks:
```
cd "/home/ed/.wine/dosdevices/c:/Program Files"
```

TAB key trick:
```
cd "/home/ed/.wine/dosdevices/c:/Progr {....Hit the TAB key here! ....} 
``` If you hit the TAB key the shell should be smart enough and then suggest the escaped directory name as result (see above).

---

### Post by 3rdalbum on 2009-09-26
Don't go to ~/.wine/dos_devices/c:/, just go straight to ~/.wine/drive_c/. It's quicker to type.

Also note that you can drag a file or folder onto the terminal and it will fill in the path for you.

---

