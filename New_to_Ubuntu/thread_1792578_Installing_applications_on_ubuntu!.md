---
title: "Installing applications on ubuntu?!"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by yesar92 on 2011-06-28
Hello

I have been trying to install applications to Ubuntu for a while now, I would always use the software center to do that. As you all know some programs are not available in the software center and thus have to be added manually to the application list on my natty ubuntu. 

When I often download them , they are either in **tar.gz** or **.deb** or **.rpm**. Can you please tell me in details how can I install them in ubuntu. One more question is why wouldn't you guys have an executable program installation like in windows? 

TQ

---

### Post by sanderd17 on 2011-06-28
.tar.gz is most of the time the source code, you should unpack it and see if there is a README file that tells you how to compile or check on the site.

.deb is an archive with installing script (comparable to exe on windows). You can just double click it. (if you get a complaint about not being executable, go to the file properties and mark it as executable).

.rpm is the same as .deb, but for red hat based distros instead of debian based like ubuntu.

We don't use that to much because the apt system used by the software center is a lot better. All programs depend on each other and if you install something, the needed libraries come with it. In windows, a programmer has to package all the libraries with his program. This can result in the same library being installed on your system a dozen times.

An extra advantage is that they are automatically updated, so the software developer doesn't have to spend his precious time on developing an update tool.

Most programs are in the software center or can be installed via adding an extra repository. Can you give me an example of a native linux program that isn't available in the USC or via an extra repository?

---

### Post by texaco on 2011-06-28
> **sanderd17 said:**
> ...
Most programs are in the software center or can be installed via adding an extra repository. Can you give me an example of a native linux program that isn't available in the USC or via an extra repository?

I agree.

Sometimes, you can find some programs with same features in software center.

It is easy and safety way to install software in linux/ubuntu.

---

### Post by haqking on 2011-06-28
> **yesar92 said:**
> Hello

I have been trying to install applications to Ubuntu for a while now, I would always use the software center to do that. As you all know some programs are not available in the software center and thus have to be added manually to the application list on my natty ubuntu. 

When I often download them , they are either in **tar.gz** or **.deb** or **.rpm**. Can you please tell me in details how can I install them in ubuntu. One more question is why wouldn't you guys have an executable program installation like in windows? 

TQ

The above posts answered most of your questions.

However as for why linux doesnt have a .exe like in windows is simply answered with Linux is not Windows and does not try to be ;-)

There are files like .deb which are packaged files which as stated above can be clicked for install and is comparable to a .exe.  The fact is in LInux you have more control and options instead of relying on someone else (the windows executable developer) to do it for you ;-)

Sometimes at first using Linux can seem difficult, sometimes even archaic because of the use of CLI but that is why it so powerful, because it gives you choices and options instead of tied in and closed source windows imprisonment ;-)

stick with it, you will learn to love the choices and control given to you with Linux, but remember that with great power comes great responsibility.

enjoy

---

### Post by Jerry N on 2011-06-28
> **sanderd17 said:**
> 
Can you give me an example of a native linux program that isn't available in the USC or via an extra repository?

Codeweaver's Crossover, NeroLinux

---

### Post by georgelab on 2011-06-28
Nice replies!

In fact I would suggest Ubuntu newbie users to check Ubuntu Software Center as a main source of applications. It's really easy to use, safe and quick.

---

### Post by Sombir.Sheoran on 2011-06-28
> **haqking said:**
> The above posts answered most of your questions.
 
However as for why linux doesnt have a .exe like in windows is simply answered with Linux is not Windows and does not try to be ;-)
 
There are files like .deb which are packaged files which as stated above can be clicked for install and is comparable to a .exe. The fact is in LInux you have more control and options instead of relying on someone else (the windows executable developer) to do it for you ;-)
 
Sometimes at first using Linux can seem difficult, sometimes even archaic because of the use of CLI but that is why it so powerful, because it gives you choices and options instead of tied in and closed source windows imprisonment ;-)
 
stick with it, you will learn to love the choices and control given to you with Linux, but remember that with great power comes great responsibility.
 
enjoy
 
 
The above reasons tell us how Windows sucks all the time,
and how well dressed is Linux.
Hats off to the Linux developers.
 
Thanks all for clearing the faint point.
@haqking: Your answers rock

---

### Post by dFlyer on 2011-06-28
> **Jerry N said:**
> Codeweaver's Crossover, NeroLinux

They both have deb file for download which can be double clicked to install, should you choose to install them.

---

### Post by gandaran on 2011-06-28
> One more question is why wouldn't you guys have an executable program installation like in windows? 
I don't think you would want that after comparing the way .deb files works to windows .exe files, to see what I mean download the the linux ubuntu "downloader installer" [here]("http://bluegriffon.org/pages/Download"), install with a double click (set the file executable in properties » permissions first) then click next and next and next just like in windows:D, when it's installed you'll see on your applications menu shortcuts just like in windows with uninstall and other options, you want that on linux? I hope not.

---

### Post by createdcreature on 2011-06-28
apt-get is so much faster than the software center or synaptic

---

### Post by sanderd17 on 2011-06-28
> **Robert Moyse said:**
> apt-get is so much faster than the software center or synaptic

Agreed, but when I don't know the exact name of the package, I use the software center.

---

### Post by yesar92 on 2011-07-01
1. Well, I am installing most programs through the software center but the problem is not having the capability to download more than one program at the same time. When I try to download a new program through the SOFTWARE CENTER I get the following error while using terminal to download another or upgrade:

waiting for apt-get to exit

and when I exit the terminal the error stays the same! 

2. I tried to install programs that come in DEB format and they work like EXE in windows but the .tar.gz I unzipped them and added the files to the directories as in the compressed file but I get nothing! The program is either installed while not working or not installed in the first place. Also, every time I want to add the files from the extracted folder to the USR , BIN ....ect folders I have to login as root! 

3. I tried to install Adobe flash player by simple extracting the files from the .tar.gz archive to the root folders but the program was not added , although I can get into its settings but I still can not use it , I downloaded the 64 MB version through SOFTWARE CENTER and still no change! What to do!!!!

---

### Post by yesar92 on 2011-07-01
Can someone plz plz plz plz plz help me with the adobe flash problem .... it is killing me! 
and how can I install a free local server on my machine as I need to test some websites I am designing .... I usually use AppServ on windows but they seem not to have a version for linux. What about XAMPP ? should I go for it? I never use it? Is there any localhost machine on SOFTWARE CENTER ? pLZ HELP!

---

### Post by alphacrucis2 on 2011-07-01
> **yesar92 said:**
> 1. Well, I am installing most programs through the software center but the problem is not having the capability to download more than one program at the same time. When I try to download a new program through the SOFTWARE CENTER I get the following error while using terminal to download another or upgrade:

waiting for apt-get to exit

and when I exit the terminal the error stays the same! 

2. I tried to install programs that come in DEB format and they work like EXE in windows but the .tar.gz I unzipped them and added the files to the directories as in the compressed file but I get nothing! The program is either installed while not working or not installed in the first place. Also, every time I want to add the files from the extracted folder to the USR , BIN ....ect folders I have to login as root! 

3. I tried to install Adobe flash player by simple extracting the files from the .tar.gz archive to the root folders but the program was not added , although I can get into its settings but I still can not use it , I downloaded the 64 MB version through SOFTWARE CENTER and still no change! What to do!!!!

The software centre itself can download and install multiple packages at a time but as you have discoverd only one instance of apt-get, synaptic or sofware centre can be updating at the same time. This is to prevent corruption of the database used by the package management system.

For the tar.gz one of the extracted files should be called readme.txt or something like that which should give instructions on how to install. Sometimes they will tell you to make an included shell script executable and then to run it. Other times they contain source code which has to be compiled. To compile programs, you would first need to install the package called build-essential. I would be very wary out doing this as a noob. Even more wary of copying files into usr and bin if you don't know what you are doing or at least seek advice here first.

 For adobe flash just install the Firefox flashaid add on.

---

### Post by sanderd17 on 2011-07-01
> **yesar92 said:**
> Can someone plz plz plz plz plz help me with the adobe flash problem .... it is killing me! 
and how can I install a free local server on my machine as I need to test some websites I am designing .... I usually use AppServ on windows but they seem not to have a version for linux. What about XAMPP ? should I go for it? I never use it? Is there any localhost machine on SOFTWARE CENTER ? pLZ HELP!

What server do you need? You say server, but you probably mean a php server. In that case, just search "php5 server" in the software center and you'll find what you need. The server itself and all kinds of bindings to databases and other languages.

When you installed it, the website should be placed in /var/www and you should visit [http://localhost](http://localhost) to see the site.

To place the website in /var/www, you might need to learn about user rights: [http://linuxcommand.org/lts0070.php](http://linuxcommand.org/lts0070.php)

---

### Post by Ken UK on 2011-07-01
I don't know how it works but one problem I can see is the possibility that all the applications that require a certain library are removed and the library or other bits are left behind just leaving mess on your computer.

Plus what happens if a certain application hasnt been developed to work with the library installed on your machine? Sure in an idea world all applications work with the latest but if only some do?

Maybe Im talking rubbish but Im a newbie and it does worry me all these files going on and off my machine...

The only .deb application I have installed was Draftsight, it was the only way to get it but seems to work fine. The problem is that theres no clear list of what you have done.

---

### Post by jerome1232 on 2011-07-01
The package managers all take care of the leaving bits behind part, you can use apt-get autoremove to remove programs that are only there as dependencies of programs which have been removed, I'm sure the all powerful synaptic has the same capability if you prefer a gui.


Debian's package management systems is on of the best features of Debian based distro's imo. It's so easy and keeps everything very tidy. Particularly compared to the Windows way of handling things. (You know how alot of installers leave crap in the Windows registry)


Also I have seen alot of third party installers use binaries to do their work (this is equivelant of a .exe) the nvidia driver is a good example, alot of games do this as well.

Anyways they usually not as friendly as a .deb package is.

---

### Post by sanderd17 on 2011-07-01
> **Ken UK said:**
> I don't know how it works but one problem I can see is the possibility that all the applications that require a certain library are removed and the library or other bits are left behind just leaving mess on your computer.

That's why aptitude and apt-get mark a package as "autoinstalled". That means you didn't install it, but it came with something else. There are commands to mark something as autoinstalled or not.

If you remove a package, all the libraries it depends on are checked and if any "autoinstalled" libraries are found, they are also removed (after a check that no other program is using that library).
> 

Plus what happens if a certain application hasnt been developed to work with the library installed on your machine? Sure in an idea world all applications work with the latest but if only some do?


The main task of cannonical, debian, red hat and all other distro makers is to make sure the programs work with the libraries. That's why you have a 6-month release cycle. Every release, all libraries and programs are upgraded, so that they work again with each other. During the support period of the release, only bugfixes and security fixes are changed, there are no features added.
> 

Maybe Im talking rubbish but Im a newbie and it does worry me all these files going on and off my machine...

The only .deb application I have installed was Draftsight, it was the only way to get it but seems to work fine. The problem is that theres no clear list of what you have done.

---

### Post by Ken UK on 2011-07-01
> **jerome1232 said:**
> The package managers all take care of the leaving bits behind part, you can use apt-get autoremove to remove programs that are only there as dependencies of programs which have been removed, I'm sure the all powerful synaptic has the same capability if you prefer a gui.


Debian's package management systems is on of the best features of Debian based distro's imo. It's so easy and keeps everything very tidy. Particularly compared to the Windows way of handling things. (You know how alot of installers leave crap in the Windows registry)


Also I have seen alot of third party installers use binaries to do their work (this is equivelant of a .exe) the nvidia driver is a good example, alot of games do this as well.

Anyways they usually not as friendly as a .deb package is.

I thought that might be the case but just seems too good to be true, too intelligent :-D
One of my biggest hates of Windows is that when you install software and uninstall it your system is never the same. It leaves crap in folders all over the place and registry.

I'm glad you told me that anyway, I can reply with the same answer if any other Ubuntu newbies I know ask me now :-D

The only other little pet hate I have for some application is when they decide they can make a new folder in my home directory (lmms is the one I think of off the top of my head). You should get the option what to do when you first start or at least use the relevant folders eg. video editing in movies folder, music in music folder, images editing in photo folder etc.

---

### Post by bance on 2011-07-01
Have been searching for bin files, because I want to install MPlabX it's an IDE for micro-controllers. I downloaded from[COLOR=Red][ here]("http://ww1.microchip.com/downloads/mplab/X_Beta/installer.html")[/COLOR]. But how do I install it?....

 Although the programme is a beta I thought it might be a better bet than MPlab since it is linux compatible, and 10.04 has deprecated gtkextra, so it's not possible to use the graphical interface on the earlier version (MPlab.)

TIA Steve.

---

### Post by yesar92 on 2011-07-01
What I did (which seems to be worng anyway) is that I went to adobe's flash page and downloaded a .tar.gz archive from there then extracted it and started copying files inside the folders to the folders matching them on my system while being root (folders like bin , usr , .... etc) 

Afterwards, as that didn't workout and flash was not added to my machine , I went to the software center and installed the 65MB plugin. 
At the end! I can not use flash! Can you please tell me what should I do to clear the mess I did! Plz!

---

### Post by sanderd17 on 2011-07-01
Can you try this: [https://help.ubuntu.com/community/RestrictedFormats/Flash#Flash%20for%2064-bit%20%28x86_64%29](https://help.ubuntu.com/community/RestrictedFormats/Flash#Flash%20for%2064-bit%20%28x86_64%29)

The 64-bit installation method and later than 9.10. Maybe it will work. If you get any errors, do copy them here.

---

### Post by oldos2er on 2011-07-01
Flash is one file, libflashplayer.so. What is the name of the file you downloaded?

Click the FlashAid link in my sig for help installing flash.

---

### Post by yesar92 on 2011-07-02
I have installed flashaid. I un-installed adobe flash player through the software center and reinstalled the plugin again and it is working now. Hope this helps others. Thank you guys!

---

