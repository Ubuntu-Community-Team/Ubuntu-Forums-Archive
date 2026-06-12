---
title: "Installing tar.gz file"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by chris1950 on 2009-08-17
I downloaded a tar.gz file and need a step by step on how to install it - I tried before but couldn't get it to work.

---

### Post by cmannnn on 2009-08-17
tar.gz like log in screen?

if so fallow theis steps
1. open system>admin>login window
2. click on the local tab
3. click on the add button then find were you put the folder and click install

---

### Post by mthalis on 2009-08-17
[http://ubuntuforums.org/showthread.php?t=118208](http://ubuntuforums.org/showthread.php?t=118208)

---

### Post by Faud on 2009-08-17
This will talk about that and how to install different types of things.
[http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually](http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually)

---

### Post by trilobite on 2009-08-17
> **chris1950 said:**
> I downloaded a tar.gz file and need a step by step on how to install it - I tried before but couldn't get it to work.

Hi Chris! 

 Try this. Let's say the file that you downloaded is called "foo.tar.gz". You can adjust these instructions accordingly to match the actual file name. I'll assume that you've downloaded it into your "home" directory - that'll be something like /home/chris.  

a) "Extract" the file (in other words, "unzip" it) by typing the following command on the command-line - 
tar -zxvf foo.tar.gz  

That will "unzip" the file and will create a directory called "foo". If the file has a version number of some kind, say "foo-1.4.5.tar.gz", it will create a directory called "foo-1.4.5".  

b) Now, go into the just-created directory -
cd foo 

c) You can check that you are in the correct directory by typing "pwd" (without the quotes). That means "present working directory". It should give you something like /home/chris/foo 

Now, the rest of the instructions assume that you're asking not just how to extract the file, but how to install the app. 

Now, this may *look* intimidating, but it's not really! Once you've done this a few times, it becomes automatic, and you never forget the "./configure, make, su make install" dance...  

d) Type "ls conf*" (without the quotes). That will give you a list of files in the directory whose names start with "conf". There is often a "configure" file there, which is what we're looking for here. If there is, then continue with these instructions.  

e) Type ./configure   That will start the configure process. You'll see lots of odd-looking commands zooming past. That's normal. Warnings can be common as well, and are usually harmless, in my experience. 

f) After the configure has finished (in other words, when the messages have stopped and you have the command-prompt back again), type 
"make" (without the quotes). This will give another set of lots of messages. 

g) When those messages have finished, do this - type "su make install" (without the quotes). That will make you the "super-user" for the last part of the install - this is needed with almost all installs. You'll notice that the command prompt will change to a "#" - that's called the "root prompt". When you type the above command, it'll ask for your password - type that in and press Enter. You'll then get yet more commands zooming past. 

h) After that, type "make clean" (without the quotes). That cleans out all of the temporary files created during the install. After this, you're finished!  

i) Exit from being the super-user by typing "exit" (without the quotes). This should take you back to the normal "$" prompt. 

j) Try running the app by typing ./foo or foo.  

 Good luck - hope this helps!  
- trilobite

---

### Post by perce on 2009-08-17
Before installing, check if the program is available in synaptic (administration > synaptic package manager) in 8 years using Linux I have *never* had to install a tar.gz.

---

### Post by Viva on 2009-08-17
What program are you trying to install?

---

### Post by chris1950 on 2009-08-17
I am going to install VMware converter and homebank. Can I do this in Kommander or must I use the terminal? As I understand it I can type commands in Krusader.

---

### Post by 3rdalbum on 2009-08-17
Homebank is in the Ubuntu repositories, so install it from there.

A ".tar.gz" file is merely a compressed archive. It can contain anything - themes, login screens, compiled binaries, source code, or any sort of computer file.

If you need to download software from the web, you must follow the instructions that come with it as there's not one specific set of instructions that will work with everything. If it's a precompiled program then you need to run it as root. If it's source code you need to compile it. If it's something else then there's a different set of things that you might need to do.

---

### Post by chris1950 on 2009-08-17
Ref - VMware install, everything was going fine untill step #4

(1) Download the latest Linux version of Converter Standalone from the VMware Web site. 
The Linux installer file name is VMware-converter-4.0.1-xxxxxx.tar.gz 
Where <xxxxxx> is the build number. 
 
(2) Unpack the tar.gz file: 
tar -xvf VMware-converter-4.0.1-xxxxxx.tar.gz 
 
(3) In terminal, navigate to the unpacked directory: 
cd vmware-converter-distrib 
 
(4) Run the installation executable file: 
./vmware-install.pl 
 
To view the VMware's patent list, press Enter.

[COLOR=Red]I can not get it to install see commands used below -[/COLOR]

chris@Compaq-Laptop:~/Desktop/vmware-converter-distrib$  ./vmware-install.pl
Please re-run this program as the super user.

Execution aborted.

chris@Compaq-Laptop:~/Desktop/vmware-converter-distrib$ su ./vmware-install.pl
Unknown id: ./vmware-install.pl
chris@Compaq-Laptop:~/Desktop/vmware-converter-distrib$ sudo su ./vmware-install.pl
Unknown id: ./vmware-install.pl
chris@Compaq-Laptop:~/Desktop/vmware-converter-distrib$ pwd
/home/chris/Desktop/vmware-converter-distrib
chris@Compaq-Laptop:~/Desktop/vmware-converter-distrib$ 

What am I doing wrong?

Also what do the different colours mean after doing a (ls) I see Blue ,Green,Black, and Red in file and directory names?

---

### Post by mrbiggbrain on 2009-08-17
> **3rdalbum said:**
> Homebank is in the Ubuntu repositories, so install it from there.

A ".tar.gz" file is merely a compressed archive. It can contain anything - themes, login screens, compiled binaries, source code, or any sort of computer file.

If you need to download software from the web, you must follow the instructions that come with it as there's not one specific set of instructions that will work with everything. If it's a precompiled program then you need to run it as root. If it's source code you need to compile it. If it's something else then there's a different set of things that you might need to do.

THis can become really true really quick, there are all kinds of things that MIGHT need to be done, from installing shared librarys, test suites, making librarys, creating symbolic links, ext ext.

---

### Post by matthewbpt on 2009-08-17
> **chris1950 said:**
> Ref - VMware install, everything was going fine untill step #4

(1) Download the latest Linux version of Converter Standalone from the VMware Web site. 
The Linux installer file name is VMware-converter-4.0.1-xxxxxx.tar.gz 
Where <xxxxxx> is the build number. 
 
(2) Unpack the tar.gz file: 
tar -xvf VMware-converter-4.0.1-xxxxxx.tar.gz 
 
(3) In terminal, navigate to the unpacked directory: 
cd vmware-converter-distrib 
 
(4) Run the installation executable file: 
./vmware-install.pl 
 
To view the VMware's patent list, press Enter.

[COLOR=Red]I can not get it to install see commands used below -[/COLOR]

chris@Compaq-Laptop:~/Desktop/vmware-converter-distrib$  ./vmware-install.pl
Please re-run this program as the super user.

Execution aborted.

chris@Compaq-Laptop:~/Desktop/vmware-converter-distrib$ su ./vmware-install.pl
Unknown id: ./vmware-install.pl
chris@Compaq-Laptop:~/Desktop/vmware-converter-distrib$ sudo su ./vmware-install.pl
Unknown id: ./vmware-install.pl
chris@Compaq-Laptop:~/Desktop/vmware-converter-distrib$ pwd
/home/chris/Desktop/vmware-converter-distrib
chris@Compaq-Laptop:~/Desktop/vmware-converter-distrib$ 

What am I doing wrong?

Also what do the different colours mean after doing a (ls) I see Blue ,Green,Black, and Red in file and directory names?

You need to do
```
sudo ./vmware-install.pl
```

---

### Post by chris1950 on 2009-08-17
Thx got it

---

