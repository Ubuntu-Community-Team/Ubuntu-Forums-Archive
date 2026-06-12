---
title: "Run script for wireless driver?"
date: 2018-12-26
forum: Networking &amp; Wireless
---

### Post by FrustratedPerson on 2018-12-26
I'm trying to install a driver for a new Wi-Fi Adapter. I have an "Install" file that's named install.sh.   But when I double click it, it opens up in a notepad. Even after I go into properties for the file and click the option to "allow executing file as a program" it still opens up in a text editor. when I double click it. 
I've tried opening it via Terminal by first being in the directory of the file, and then trying the following commands: 

Open install.sh              ---------- Results in "Couldn't get a file descriptor referring to the console"
Run install.sh ---------- Results in "Command 'run' not found.
xdg-open install.sh ----------- Results in the file being opened again in a text editor.
install.sh ----------- Results in "install.sh: command not found". 

Every piece of direction I've found suggest trying one of the above 4 methods, or they talk about things far beyond my comprehension. I do also see other files that end in .tar.gz  but there are no obvious install files in those. 

Any help will be greatly appreciated. Why can't I install this driver? The drivers sadly come with no directions (not even on the manufacturer's website) about installing on Linux.

---

### Post by QIII on 2018-12-26
Hello!

Have you tried going to the terminal and issuing 

```
chmod +x /path/to/yourscript.sh
```

followed by 

```
/path/to/yourscript.sh
```?

If you are in the current directory of the script, the latter command can be shortened to 

```
./yourscript.sh
```

(replace "yourscript.sh" with the actual name of the script.)

Notice that the path has to be qualified.

---

### Post by FrustratedPerson on 2018-12-26
The file is located in a folder called "linux" on my desktop. So the path should be (I would think) Desktop/linux/install.sh

I've tried the following just now: 

chmod +x /Desktop/linux/install.sh   ------------results in "chmod: cannot access '/install.sh' no such file or directory.
chmod +x Desktop/linux/install.sh    ------------results in "chmod: cannot access '/install.sh' no such file or directory.
chmod +x install.sh                          ------------results in "chmod: cannot access '/install.sh' no such file or directory.

But the file is literally in the linux folder on Desktop. When I do "ls" in my current directory, I see the install.sh file. 
This is what my terminal shows as the folder I have opened. 
ItsMe@ItsMe-ComputerModel:~/Desktop/linux$

---

### Post by QIII on 2018-12-26
The fully qualified directory would be

```
/home/yourusername/Desktop/ ...
```

or

```
./Desktop/ ...
```

To make this easier, and more "Linux-like", I'd suggest moving the file to your /home/username directory (that is, one directory "up" in your hierarchy) and then navigating there in the terminal and going with the 

```
./yourscript.sh
```

method above.

I never use stuff in the /Desktop directory because I am used to doing all of this as if there were no GUI (I started out as a Unix guy in the 70s) -- which is certainly the case when you are using a server.

---

### Post by FrustratedPerson on 2018-12-26
Ok, so somehow progress is made, but now it's a different problem. Now I'm getting the following after it seemingly runs the .sh file. 
It asks for a password, I enter the password, but then it says "bash: make: command not found". I entered my password, but then it asks for my password again. I enter it again, but then it gives me the same thing. I know I"m entering the password correctly. I even changed my password for the root login, despite being able to log in using the password that the terminal seems not to like. 

Authentication requested [root] for make clean:
Password: 
bash: make: command not found
Authentication requested [root] for make driver:
Password: 
bash: make: command not found
##################################################
Compile make driver error: 127
Please check error Mesg
##################################################

---

### Post by QIII on 2018-12-26
OK.  You'll have to install make.

But before we get into that, would you please post the output of the wireless script as described [here]("https://github.com/UbuntuForums/wireless-info")?

Now that this is effectively solely a wireless issue, moved to ***Networking & Wireless***.  Title changed.

---

### Post by praseodym on 2018-12-26
For what device?! We may find a newer one. Please show
```

lspci -nnk
lsusb
```

---

