---
title: "OK, how &amp; what do I do???  Here is the senerio."
date: 2011-03-04
forum: New to Ubuntu
---

### Post by TAspr on 2011-03-04
I have to download a .tar.gz file.  Then I have to extract it or open it.  Where does it go, and what do I do once I get the files extracted?  How do I launch the program?  I am noticing that many programs are not native to the package manager.

---

### Post by ubudog on 2011-03-04
Don't worry, this is very easy, and it won't take that long.  :-)

First, after downloaded, put it on the Desktop.  Double click on it, then select "Extract".  Go through everything after that, leaving defaults.

Second, open a terminal (Applications>Accessories>Terminal).
In the terminal, type the following code.
```
cd Desktop
```
(go to the desktop)
```
cd extractedfoldername
```
(go to the extracted folder)
```
./configure && make && sudo make install
```
(start the process of installing, this may take a while, and you will have to enter your password at the end (it will be blank, that's normal))

Then to run it, open a terminal and type the name of the program into the terminal. 

Eg,
```
myinstalledprogram
```

If you get any errors during the install, please post them, and maybe I can help.  Hope this helps, and good luck.  :)

---

### Post by TAspr on 2011-03-04
Thanks Buddy, I will try this and see how far I get.

---

### Post by TAspr on 2011-03-04
Ok, so now, how do I put the icon to launch it?  Will it automatically launch?  

Here is the code I received;

[FONT=monospace]PC:~$ cd pulseaudio-0.9.22
PC:~/pulseaudio-0.9.22$ ./configure && make && sudo make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc option to accept ISO C99... -std=gnu99
checking whether gcc -std=gnu99 and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc -std=gnu99 needs -traditional... no
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for gm4... no
checking for m4... no
configure: error: m4 missing
PC:~/pulseaudio-0.9.22$ myinstalledprogram
myinstalledprogram: command not found
PC:~/pulseaudio-0.9.22$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
PC:~/pulseaudio-0.9.22$ ^C
PC:~/pulseaudio-0.9.22$ 
[/FONT]

Now, does this automaically launch the program?  How does it know what needs to be placed where, another words, how does it know it should go into a certain directory?  Is there a safe way to delete the files after it has been installed?

---

### Post by maqtanim on 2011-03-04
Well... the problem with your command is with the following lines
```
[FONT=monospace]user@user-HP-Compaq-8000-Elite-CMT-PC:~/pulseaudio-0.9.22$ myinstalledprogram
myinstalledprogram: command not found
user@user-HP-Compaq-8000-Elite-CMT-PC:~/pulseaudio-0.9.22$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
PC:~/pulseaudio-0.9.22$ ^C
PC:~/pulseaudio-0.9.22$ [/FONT]
```

Instead of **[FONT=monospace]myinstalledprogram, [/FONT]**[FONT=monospace]you should write your program name. In this case it is **pulseaudio **

By the way... [/FONT]Is not Pulse Audio already installed in your system? Why do you want to install it?

---

### Post by TAspr on 2011-03-04
> **maqtanim said:**
> Well... the problem with your command is with the following lines
```
[FONT=monospace]PC:~/pulseaudio-0.9.22$ myinstalledprogram
myinstalledprogram: command not found
PC:~/pulseaudio-0.9.22$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
PC:~/pulseaudio-0.9.22$ ^C
PC:~/pulseaudio-0.9.22$ [/FONT]
```Instead of **[FONT=monospace]myinstalledprogram, [/FONT]**[FONT=monospace]you should write your program name. In this case it is **pulseaudio **

By the way... [/FONT]Is not Pulse Audio already installed in your system? Why do you want to install it?


The "myinstalledprogram" was a mistake on my part.  Does this put the icon areas where they should go and the programs where they should go?  How do you know where they should go?  Is there also a safe way to delete the programs after they installed?

---

### Post by NCLI on 2011-03-04
> **TAspr said:**
> The "myinstalledprogram" was a mistake on my part.  Does this put the icon areas where they should go and the programs where they should go?  How do you know where they should go?  Is there also a safe way to delete the programs after they installed?
Could you please explain why you're installing pulseaudio, when it's already installed on your system?

---

### Post by TAspr on 2011-03-04
Well, while I was installing my Logitech Quickcam 9000, it said that I needed these files, and at this point, I did not know I had them.  Now, the other thing is to get the Quickcam Pro 9000 working.  Do you have any suggestions as to what I should be using to do this?

---

### Post by maqtanim on 2011-03-04
[QUOTE=TAspr]Does this put the icon areas where they should go and the programs where they should go?[/QUOTE] 
Did not understand what did you ask? Can you please clarify more?
[QUOTE=TAspr] How do you know where they should go?[/QUOTE]  
all the user related applications will be found in the **/usr** directory. For knpwing more about the Linux File Systems, visit [this page]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview").
[QUOTE=TAspr]Is there also a safe way to delete the programs after they installed?[/QUOTE]
Always Install/Uninstall any program with Ubuntu Software Center. This is the safest way!
[QUOTE=TAspr]Well, while I was installing my Logitech Quickcam 9000, it said that I  needed these files, and at this point, I did not know I had them.  Now,  the other thing is to get the Quickcam Pro 9000 working.  Do you have  any suggestions as to what I should be using to do this?[/QUOTE]
Please, post separate thread for separate problem.

---

### Post by NCLI on 2011-03-04
> **TAspr said:**
> Well, while I was installing my Logitech Quickcam 9000, it said that I needed these files, and at this point, I did not know I had them.  Now, the other thing is to get the Quickcam Pro 9000 working.  Do you have any suggestions as to what I should be using to do this?
Start by posting a new thread called something like: "Need help getting Logitech Quickcam Pro 9000 to work", then describe your problems there.

---

### Post by TAspr on 2011-03-04
> **NCLI said:**
> Start by posting a new thread called something like: "Need help getting Logitech Quickcam Pro 9000 to work", then describe your problems there.


Got it guys, thanks for all your help, seriously.

---

### Post by ubudog on 2011-03-07
> **NCLI said:**
> Start by posting a new thread called something like: "Need help getting Logitech Quickcam Pro 9000 to work", then describe your problems there.

I agree, you could get much more help by doing this.

If you like, if you create the new thread, post a link to it here, so that people like me wandering around may be able to help too.  :-)

---

### Post by slooksterpsv on 2011-03-07
```

checking for m4... no
configure: error: m4 missing

```

Umm... here's the issue:

1. You'll need to install m4 - sudo apt-get install m4
2. You'll need to run ./configure again and make sure it doesn't give you any more errors.
3. After ./configure run make && sudo make install
OR
3. After ./configure run make - and the program should be in the root of the directory, usually you'll wnat to do make install to install it to your system in its own location.
4. Run said program, in this case pulseaudio, you'll want to do make install not just make. NOTE: sudo make install

I can't believe no one else caught that ./configure was exiting prematurely due to m4 not being installed. Weird...

---

### Post by 3rdalbum on 2011-03-07
> **slooksterpsv said:**
> ```

checking for m4... no
configure: error: m4 missing

```

Umm... here's the issue:
...

I can't believe no one else caught that ./configure was exiting prematurely due to m4 not being installed. Weird...

I'm pretty sure other posters caught it, but the main problem is that Pulseaudio is already installed on Ubuntu, so the whole "troubleshoot why this isn't compiling" was completely unnecessary.

---

### Post by TAspr on 2011-03-09
> **ubudog said:**
> Don't worry, this is very easy, and it won't take that long.  :-)

First, after downloaded, put it on the Desktop.  Double click on it, then select "Extract".  Go through everything after that, leaving defaults.

Second, open a terminal (Applications>Accessories>Terminal).
In the terminal, type the following code.
```
cd Desktop
```(go to the desktop)
```
cd extractedfoldername
```(go to the extracted folder)
```
./configure && make && sudo make install
```(start the process of installing, this may take a while, and you will have to enter your password at the end (it will be blank, that's normal))

Then to run it, open a terminal and type the name of the program into the terminal. 

Eg,
```
myinstalledprogram
```If you get any errors during the install, please post them, and maybe I can help.  Hope this helps, and good luck.  :)

Hello again, I tried to do this with a Linux Driver for a printer, but it did not work installing the drivers.  Is there an alternate way to do this?

---

### Post by ubudog on 2011-03-10
> **3rdalbum said:**
> I'm pretty sure other posters caught it, but the main problem is that Pulseaudio is already installed on Ubuntu, so the whole "troubleshoot why this isn't compiling" was completely unnecessary.

Exactly.

---

### Post by ubudog on 2011-03-10
> **TAspr said:**
> Hello again, I tried to do this with a Linux Driver for a printer, but it did not work installing the drivers.  Is there an alternate way to do this?

Umm, could you post the errors please?

---

### Post by HC48 on 2011-03-15
Thank you ubudog for your simple explanation!!!

HC  :)))

---

### Post by ubudog on 2011-03-15
> **HC48 said:**
> Thank you ubudog for your simple explanation!!!

HC  :)))

No problem.  :)

---

