---
title: "unable Open and Bin file"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by Plovesen on 2010-11-12
Hej, im pretty new in ubuntu, and i just cant get this Bin file opened. I have read a lot of other Discussions about the subject but its doesnt work anyway..

Its a game file(unreal Tournament) ut.bin. 


Please help me :) Thx

---

### Post by Plovesen on 2010-11-12
lol sry its should have said : "Unable to open a .bin file"

---

### Post by sandyd on 2010-11-12
> **Plovesen said:**
> Hej, im pretty new in ubuntu, and i just cant get this Bin file opened. I have read a lot of other Discussions about the subject but its doesnt work anyway..

Its a game file(unreal Tournament) ut.bin. 


Please help me :) Thx

move the file to your desktop.
then run this.
```

cd ~/Desktop
chmod 777 ut.bin
gksudo bash ./ut.bin
```

---

### Post by bryangwilliam on 2010-11-12
What have you tried? 

As far as I know, all that generally needs to be done is to make it executable (chmod +x) and then run it.

---

### Post by ibizatunes on 2010-11-12
you need to make the .bin executable 
```
cd /your directory
``` change to that directoy
```
chmod 775 XZZ.bin
```

you may need sudo infront of the chmod if it need to run as root (but i dont know)

then you can double click it and it should work

---

### Post by Plovesen on 2010-11-12
peter@peter-desktop:~$ cd ~/Desktop
bash: cd: /home/peter/Desktop: No such file or directory
peter@peter-desktop:~$ chmod 777 ut.bin
chmod: cannot access `ut.bin': No such file or directory
peter@peter-desktop:~$ gksudo bash ./ut.bin
bash: ./ut.bin: No such file or directorypeter@peter-desktop:~$ 
peter@peter-desktop:~$ cd /desktop
bash: cd: /desktop: No such file or directory
peter@peter-desktop:~$ chmod 775 ut.bin
chmod: cannot access `ut.bin': No such file or directory
peter@peter-desktop:~$ sodu chmod 775 ut.bin
sodu: command not found
peter@peter-desktop:~$ ^C
peter@peter-desktop:~$ 

I tried to chmod +x as well but it doesnt work.. And the file is on Desktop.. 

toherwise thx for very fast respond :)

---

### Post by bryangwilliam on 2010-11-12
You don't have a Desktop folder? Just type "cd" to go to your home folder and then "ls" to show all folders there. Does it not have a directory for "Desktop" there?

---

### Post by tad1073 on 2010-11-12
> **bryangwilliam said:**
> You don't have a Desktop folder? Just type "cd" to go to your home folder and then "ls" to show all folders there. Does it not have a directory for "Desktop" there?

his terminal opens to his desktop

---

### Post by tad1073 on 2010-11-12
> **Plovesen said:**
> peter@peter-desktop:~$ cd ~/Desktop
bash: cd: /home/peter/Desktop: No such file or directory
peter@peter-desktop:~$ chmod 777 ut.bin
chmod: cannot access `ut.bin': No such file or directory
peter@peter-desktop:~$ gksudo bash ./ut.bin
bash: ./ut.bin: No such file or directorypeter@peter-desktop:~$ 
peter@peter-desktop:~$ cd /desktop
bash: cd: /desktop: No such file or directory
peter@peter-desktop:~$ chmod 775 ut.bin
chmod: cannot access `ut.bin': No such file or directory
peter@peter-desktop:~$ sodu chmod 775 ut.bin
sodu: command not found
peter@peter-desktop:~$ ^C
peter@peter-desktop:~$ 

I tried to chmod +x as well but it doesnt work.. And the file is on Desktop.. 

toherwise thx for very fast respond :)

run "ls" from the terminal and  see if the file is there.
that is a lower-case L by the way

---

### Post by lol768 on 2010-11-12
You can do this graphically if you wish (it might be easier :)).

1. Open Nautilus, the file manager (I'm assuming you are using GNOME) and find the file
2. Right click on the file and select properties
3. Click the permissions tab
4. Tick the "Allow executing file as program" box
5. Click close
6. Double click on the file and choose "Run in terminal" when prompted

Good Luck!
[B]
Edit: See the attached screenshot below
[/B]

---

### Post by bryangwilliam on 2010-11-12
> **tad1073 said:**
> his terminal opens to his desktop

I could be wrong, but I thought that "cd ~/Desktop" should not give a "No such file or directory" error no matter where the terminal opens to.

---

### Post by Plovesen on 2010-11-12
> **ibizatunes said:**
> you need to make the .bin executable 
```
cd /your directory
``` change to that directoy
```
chmod 775 XZZ.bin
```you may need sudo infront of the chmod if it need to run as root (but i dont know)

then you can double click it and it should work

Now i can open my directory (peter@peter-desktop:~/Skrivebord$) the danish word for desktop, and i can see the file by using the "ls" command. Then i try to do the 

chmod 777 ut.bin
gksudo bash ./ut.bin
and then this apears:

peter@peter-desktop:~/Skrivebord$ chmod 777 ut.bin
peter@peter-desktop:~/Skrivebord$ gksudo bash ./ut.bin
./ut.bin: ./ut.bin: cannot execute binary filepeter@peter-desktop:~/Skrivebord$

---

### Post by sandyd on 2010-11-12
> **Plovesen said:**
> Now i can open my directory (peter@peter-desktop:~/Skrivebord$) the danish word for desktop, and i can see the file by using the "ls" command. Then i try to do the 

chmod 777 ut.bin
gksudo bash ./ut.bin
and then this apears:

peter@peter-desktop:~/Skrivebord$ chmod 777 ut.bin
peter@peter-desktop:~/Skrivebord$ gksudo bash ./ut.bin
./ut.bin: ./ut.bin: cannot execute binary filepeter@peter-desktop:~/Skrivebord$

try just
```

./ut.bin

```

---

### Post by Plovesen on 2010-11-12
> **sandyd said:**
> try just
```

./ut.bin

```

peter@peter-desktop:~/Skrivebord$ ./ut.bin
bash: ./ut.bin: cannot execute binary file

---

### Post by tad1073 on 2010-11-12
```
chmod +x ut.bin
```

this will make the file executable

---

### Post by lobralleo on 2010-11-12
I am wondering if the file is corrupted? It should be already executable, because of "chmod 777 ut.bin".
Can you download again the .bin file and try to run it?

---

