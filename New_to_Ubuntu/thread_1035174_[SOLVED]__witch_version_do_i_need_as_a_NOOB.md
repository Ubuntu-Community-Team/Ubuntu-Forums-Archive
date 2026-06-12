---
title: "[SOLVED] ?? witch version do i need as a NOOB"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Sultanabdel on 2009-01-09
Hello Good people,

I'm new in this world (windows user), and just started a programming study. i was looking for easy to use OS to start with. Let me tell you there are A LOT of different free OS on the WWW! ;) so much that when i think i have one it wont work. i think the last one was a server edition of fedora.

This is what i have to work with:
- Laptop 
hp compaq 8710W
Type:  Intel Core 2 64bit T7700
GPU:  Nvidia Quadro FX 1600M 512 MB GDDR3
OS:  Vista (don't shoot me, it came with the laptop)

- Desktop
Core 2 Quad Q8300
GeForce 9800GTX
OS: Win XP

Can some one help me getting started? I need one OS for both systems. easy to get used with at start. here are some noob questions.

-What kind of OS do i need to download to start with as a noob????? (maybe a link and version)
-i386 vs i686??? is there a difference? is this 32bit vs 64 bit? (both system are 64bit)
-I want to start easy, visual window (point & click, not some terminal witch a lot of command lines) 
-Like windows, easy installation with no command line things. ( long time ago i had a free OS and i had to do some command lines before i could get on network etc... bad bad bad)

Thanks in advance

---

### Post by thegreenblob on 2009-01-09
Ubuntu 8.10 Intrepid should run great on both of those systems.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

And I would get 32 bit if you have 3GB of ram or less, and 64 bit if you have more than that.

---

### Post by bailbath on 2009-01-09
I would go with the lts 8.04 Ubuntu long term support as it is more friendly for Nvidia 3d driver.
Ian

---

### Post by Sultanabdel on 2009-01-09
thanks for the fast replay both of you!

I have 4GB on both systems so 64bit. But is 8.10 better version then 8.04? or at least updated version? why is there a difference in Nvidia 3d driver support?

Does it matter on what disk i burn it? because i saw some topic where people had problems with rewritable CD. I have only rewritable cd's home. is this a big enough problem to go and buy normal cd's?

Is Firefox pre installed on this Ubuntu? Properly need to download drivers first before installing? like my wifi etc... otherwise i wont have any help after installing.

I want to do this today and leave the MS time behind me. I don't want to re-install vista again, so i want/need it to work first time.

---

### Post by Dedoimedo on 2009-01-09
Definitely a 64-bit OS. Now, easy ones are definitely Ubuntu-based, so Ubuntu itself is a good choice. I'd also recommend the most recent version, as you're more likely to get more support in forums and more bugs fixed.

If you want to be as compliant as possible vis-a-vis coding, then I'd recommend either CentOS or Debian, but these are not the easiest to use.

Dedoimedo

---

### Post by beastrace91 on 2009-01-09
I do not have any issues with 3d support on 8.10... Everything runs great and def. get the 64bit version with 4gigs of ram.

~Jeff

---

### Post by namdung on 2009-01-09
I recommend the much stable Hardy Heron 8.04 LTS which is supported for 3 years. Intrepid may have more features but likely to have more bugs. The next release of Hardy 8.04.2 is out anytime now.

Support for 64 bit has increased in the recent past, hence shouldn't be a concern.

Installing and using Ubuntu is easier than Windows and command line is hardly needed. Power of Linux lies using the command line and I recommend u to learn the basic commands with time.

Find all answers to ur queries in this forum.

Good luck!!!

---

### Post by bailbath on 2009-01-09
> **Sultanabdel said:**
> thanks for the fast replay both of you!

I have 4GB on both systems so 64bit. But is 8.10 better version then 8.04? or at least updated version? why is there a difference in Nvidia 3d driver support?

Does it matter on what disk i burn it? because i saw some topic where people had problems with rewritable CD. I have only rewritable cd's home. is this a big enough problem to go and buy normal cd's?

Is Firefox pre installed on this Ubuntu? Properly need to download drivers first before installing? like my wifi etc... otherwise i wont have any help after installing.

I want to do this today and leave the MS time behind me. I don't want to re-install vista again, so i want/need it to work first time.

I used cd-rw and had no problems. It's a long term support version 8.04 so it tends to be a bit more stable. 8.10 is the latest but some users including me have had trouble with Nvidia's driver. I think it is more a case of the driver being not up with the latest Ubuntu release. it will catch up but don't know when.
Everything you need for your hardware will be in a the Linux Kernel of the os. 
Everything you need software wise will be in Ubuntu via the synaptic package manager.
I have not used MS for 5/6 years and don't miss a thing.
Ian

---

### Post by ibuclaw on 2009-01-09
The natural architecture I would go for is the 64bit version.

And to point out the difference:
Ubuntu Hardy Heron 8.04.1 = Stable + Long Term Support
Ubuntu Intrepid Ibex 8.10 = Testing + Newest Software Versions


=====
NVIDIA Hardware Support in Intrepid
=====
As a way to specifically target the proprietary nature of the NVIDIA drivers, the hooks that NVIDIA used in the kernel tree were dropped by the main kernel developers. So during the time of around May '08 till August/September time the NVIDIA drivers didn't work/worked very badly after a quick-fix patch was supplied in the then latest kernel tree (Ubuntu 8.04.1 is unaffected by this).
The next release, Jaunty, includes the newest version of Xorg, which due to the amount of changes in it, again breaks the NVIDIA drivers. So we'll just have to wait and see what happens there come April time.
But it does appear to me that NVIDIA isn't really pulling their weight in keeping up with the now ever quickening pace of development in the Linux community. But, at the end of the day, if they keep their proprietary nature, they won't progress anywhere.

Though, it works now for the time being in the 8.10 release, mind you. So there is nothing that you should be worried about. It installs and works just as you'd expect ... without any hassle :)


CD-RWs should work if you burn the image properly on the disk.

Firefox comes pre-installed.

What wireless card do you have?

Regards
Iain

---

### Post by SpenceMakesSense on 2009-01-09
I would definitely agree with them. 8.04 would be a good choice for a "noob"
Mostly because If you got 8.10 and had to upgrade it would be a hassle and if it fails your OS may become unusable.

---

### Post by bailbath on 2009-01-09
> **tinivole said:**
> 


=====
NVIDIA Hardware Support in Intrepid
=====
 

Though, it works now for the time being in the 8.10 release, mind you. So there is nothing that you should be worried about. It installs and works just as you'd expect ... without any hassle :)




Regards
Iain

I still have not got Nvidia 3d working in Intrepid so as a newbie is asking the question I suggest stay away from 8.10. It maybe my setup being sli or I'm being dense but I have got a 5/6 year experience of Linux and if I have trouble and can't find the solution for my setup how will a newbie get on?
Ian

---

### Post by ibuclaw on 2009-01-09
> **bailbath said:**
> I still have not got Nvidia 3d working in Intrepid so as a newbie is asking the question I suggest stay away from 8.10. It maybe my setup being sli or I'm being dense but I have got a 5/6 year experience of Linux and if I have trouble and can't find the solution for my setup how will a newbie get on?
Ian

Years of experience, although helps, means nothing in terms of knowledge.
In the team I work in, someone could be a Zen at NFS, IPTables, configuring Domains, DNS Servers and Security in Linux, but still not have a scooby on how Xorg works.

Ultimately, if NVIDIA doesn't work for you, it would all depend on what hardware you are using, what repositories you have enabled, what kernel you are running on, what version of the NVIDIA driver you have chosen to install, and how "up-to-date" you actually keep your system.

I don't know how you deal with upgrades/updates, but if something that I consider "mission critical" to my daily use is working, then I pin it, and only allow Security updates to upgrade over it.

Although, Ian, I do sympathise with you, I've had my fair share of X problems in the Alpha testing I've done, and I've mostly found that installing things myself do more good than waste, in the irony of it all.
Also, IMO, X.org are not doing any better either in getting drivers working. [Reason #1]("http://www.ubuntu.com/testing/intrepid/alpha4") To quote the page info on Intrepid Alpha4.
> 
X.Org server 1.5

The latest X.Org is available in Intrepid. This now also brings much better support for hot-pluggable input devices such as tablets, keyboards, or mice. At the same time this will allow the great majority of users to run without an "/etc/xorg.conf" file.

Is it just me or have they gone and deprecated the xorg.conf file?
How are we, the users, supposed to configure X now?

Regards
Iain

---

### Post by -kg- on 2009-01-09
> **tinivole said:**
> 

>  Originally Posted by bailbath  View Post
I still have not got Nvidia 3d working in Intrepid so as a newbie is asking the question I suggest stay away from 8.10. It maybe my setup being sli or I'm being dense but I have got a 5/6 year experience of Linux and if I have trouble and can't find the solution for my setup how will a newbie get on?
Ian

Years of experience, although helps, means nothing in terms of knowledge.
In the team I work in, someone could be a Zen at NFS, IPTables, configuring Domains, DNS Servers and Security in Linux, but still not have a scooby on how Xorg works.

Ultimately, if NVIDIA doesn't work for you, it would all depend on what hardware you are using, what repositories you have enabled, what kernel you are running on, what version of the NVIDIA driver you have chosen to install, and how "up-to-date" you actually keep your system.

I don't know how you deal with upgrades/updates, but if something that I consider "mission critical" to my daily use is working, then I pin it, and only allow Security updates to upgrade over it.

Although, Ian, I do sympathise with you, I've had my fair share of X problems in the Alpha testing I've done, and I've mostly found that installing things myself do more good than waste, in the irony of it all.
Also, IMO, X.org are not doing any better either in getting drivers working. [Reason #1]("http://www.ubuntu.com/testing/intrepid/alpha4") To quote the page info on Intrepid Alpha4.

[QUOTE]X.Org server 1.5

The latest X.Org is available in Intrepid. This now also brings much better support for hot-pluggable input devices such as tablets, keyboards, or mice. At the same time this will allow the great majority of users to run without an "/etc/xorg.conf" file.

Is it just me or have they gone and deprecated the xorg.conf file?
How are we, the users, supposed to configure X now?

Regards
Iain[/QUOTE]

Of course, Sultanabdel has stated that he has tried various installs, including Fedora server, and has not been able to get them to work.

I think that I would suggest *at least* starting with 8.04 Hardy.  You must admit that at the present time it has the fewest installation and configuration issues.  I have installed it on both my AMD64 desktop and Duo-Core laptop with very few issues.  Even the wireless in my laptop worked right out of the box.

I have an nVidia card in my desktop and, after installing the proprietary drivers, the 3D worked fine and they installed with no problems.

Perhaps once Sultanabdel gets used to Linux (and specifically Ubuntu), then he can upgrade his installation to 8.10 (or the next LTS release), but there's nothing like an installation that is mostly successful the first time, with as few issues as possible, to build the confidence in a brand new operating system that, naturally, you're going to have a large learning curve to become proficient in (as well as **un-** learning the old!).

Ubuntu is an excellent OS to start the learning process.  It is a very stable Linux OS and there are many, many people on these help forums who are quite eager to help (just look at the bottom of the Forums page to see how many people are generally logged on to the system at any time...literally hundreds).  I don't know (and I generally don't have time to check), but I would say that these forums are among the busiest (if not **the** busiest) help forums among any of the distributions out there.

Oh, and yeah, if you have 4 GB of RAM on both your systems, 64 bit is probably the way for you to go.  One thing, though:

> I'm new in this world (windows user), and just started a programming study.

I don't know what language you're studying, but if it's Visual Basic, I couldn't get the IDE (Gambas) to install on my desktop, which has the 64-bit version of 8.04.  It installs fine on my laptop, which has the 32-bit version.  However, the Visual C++ software (Anjuta) installed just fine on both.

I know that some have Gambas installed on 64-bit, but I don't know how they did it, and I have other concerns before me right now, so I'm letting it slide.  But doing a programming study, you might need to know this.

---

### Post by Sultanabdel on 2009-01-09
Ok for what i have read it's gonna be Ubtunu 8.04 64bit. But on this site i got from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) when i select "Ubuntu 8.04 LTS Desktop" the 64bit version. i get this file "ubuntu-8.04.1-desktop-amd64.iso" AMD64? is this ok????

[QUOTE=namdung]Power of Linux lies using the command line and I recommend u to learn the basic commands with time.[/QUOTE]

That's what i was planning to do, but i need a easy start first. something that just works and go from there.

[QUOTE=bailbath]Everything you need for your hardware will be in a the Linux Kernel of the os.
Everything you need software wise will be in Ubuntu via the synaptic package manager.[/QUOTE]

So i don't need any drivers after install? I'm worried about mine wifi, if i don't have that then i cant use the www to help fixing my problems (if they occur). That's why i started to build a USB boot thing but it wont work. i think i downloaded the server live cd.

[QUOTE=tinivole]What wireless card do you have?[/QUOTE]

I'm using my laptop with builtin wifi: Intel(R) Wireless WiFi Link 4965AGN.
intel site say's that driver has been merged into mainline kernel since 2.6.24. but i cant find wich version Ubuntu 8.04 is

[QUOTE=-kg-]I don't know what language you're studying, but if it's Visual Basic, I couldn't get the IDE (Gambas) to install on my desktop, which has the 64-bit version of 8.04. It installs fine on my laptop, which has the 32-bit version. However, the Visual C++ software (Anjuta) installed just fine on both.[/QUOTE]

I just started Embedded systems, my first 2 classes are: First clas I'm using Bordland for C++. But any kind of C++ will do i think. My second class is more embedded software but we start with learning about architecture of hardware etc... programming will start later this year.

---

### Post by ibuclaw on 2009-01-09
> **Sultanabdel said:**
> Ok for what i have read it's gonna be Ubtunu 8.04 64bit. But on this site i got from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) when i select "Ubuntu 8.04 LTS Desktop" the 64bit version. i get this file "ubuntu-8.04.1-desktop-amd64.iso" AMD64? is this ok????

AMD64 is the one you need, yes.
The Intel and AMD 64bit processors use the same opcode, so don't be put off by the name, it's called amd64 because AMD got there first, that is all :)
> 
I'm using my laptop with builtin wifi: Intel(R) Wireless WiFi Link 4965AGN.
intel site say's that driver has been merged into mainline kernel since 2.6.24. but i cant find wich version Ubuntu 8.04 is

Intel Wireless 4965 is one **beautiful** Wireless Card! It performs exactly how one should (it /actually/ picks up all WAPs in a 100ft radius)
I know, because I have one on my HP Pavilion... It works out-of-box. :)
> 
I just started Embedded systems, my first 2 classes are: First clas I'm using Bordland for C++. But any kind of C++ will do i think. My second class is more embedded software but we start with learning about architecture of hardware etc... programming will start later this year.
After installation, install the build-essential package:
```
sudo apt-get install build-essential
```
This is a small bundle of the gcc (C) and g++ (C++) compilers and a few build tools to help you get started in basic programming in Linux.

As for what text editor to use... there is an abundance of software to choose from, both terminal-based and GUI-based, such as vim, nano, gedit, scite, geany...
IMO, vim, once configured for C++ programming, is one of the most valuable tools in the Linux tool rack.
Though you may find it's usage a rather different and scary experience at first, but it is written with logic and optimal use in mind. So once you learn some advanced features, you'll find it eases a lot of workload.

You will may also find that vim is installed on everything ... Linux, UNIX, BSD, you name it :)

Regards
Iain

---

### Post by Sultanabdel on 2009-01-09
> **tinivole said:**
> AMD64 is the one you need, yes.
The Intel and AMD 64bit processors use the same opcode, so don't be put off by the name, it's called amd64 because AMD got there first, that is all :)

Ok thanks, just to be sure

> **tinivole said:**
> Intel Wireless 4965 is one **beautiful** Wireless Card! It performs exactly how one should (it /actually/ picks up all WAPs in a 100ft radius)
I know, because I have one on my HP Pavilion... It works out-of-box. :)

Now i happy :popcorn:

> **tinivole said:**
> After installation, install the build-essential package:
```
sudo apt-get install build-essential
```
This is a small bundle of the gcc (C) and g++ (C++) compilers and a few build tools to help you get started in basic programming in Linux.

ALLERT ALLERT!! noob question!
When i type this where will i find c++? or how i gonna start it?

> **tinivole said:**
> As for what text editor to use... there is an abundance of software to choose from, both terminal-based and GUI-based, such as vim, nano, gedit, scite, geany...
IMO, vim, once configured for C++ programming, is one of the most valuable tools in the Linux tool rack.
Though you may find it's usage a rather different and scary experience at first, but it is written with logic and optimal use in mind. So once you learn some advanced features, you'll find it eases a lot of workload

Thanks a lot people! you're the best!

I have a secret, gues what my laptop is running right now?! :D
I installed 8.04.1 just now along side win xp. after +/-5 minutes i know for sure om gonna deleet windows and do a clean install! everything just works!!!!! and when it doesn't (like music player "codes") it just asks if i want to install it. my wifi worked direct! with XP i always needed a lot of drivers after new install. 

big thanks to this nice community, i will be back with more questions soon but i need to get used with this nice OS first so ill leave you this weekend in peace ;)

---

### Post by estyles on 2009-01-09
> **Sultanabdel said:**
> I have a secret, gues what my laptop is running right now?! :D
I installed 8.04.1 just now along side win xp. after +/-5 minutes i know for sure om gonna deleet windows and do a clean install! everything just works!!!!! and when it doesn't (like music player "codes") it just asks if i want to install it. my wifi worked direct! with XP i always needed a lot of drivers after new install. 

big thanks to this nice community, i will be back with more questions soon but i need to get used with this nice OS first so ill leave you this weekend in peace ;)

A bit of advice - leave Windows on at least one of the computers.  After all, you paid for it (even if it came "free" on the computer, you still paid for it), and you might find that you need it at some point, for games, some particular program, etc.  And if you have untenable problems at some future point and want to switch back, you'll be less frustrated if you can just boot into windows instead of having to uninstall/reinstall.  Also, if you have the install CD for either Vista or XP, you might want to run Windows in a virtual machine at some point.  Running a VM fullscreen on one side of a compiz desktop cube is pretty sweet... :D

---

### Post by Sultanabdel on 2009-01-09
> **estyles said:**
> A bit of advice - leave Windows on at least one of the computers.  After all, you paid for it (even if it came "free" on the computer, you still paid for it), and you might find that you need it at some point, for games, some particular program, etc.  And if you have untenable problems at some future point and want to switch back, you'll be less frustrated if you can just boot into windows instead of having to uninstall/reinstall.  Also, if you have the install CD for either Vista or XP, you might want to run Windows in a virtual machine at some point.  Running a VM fullscreen on one side of a compiz desktop cube is pretty sweet... :D

well i did pay for one, desktop build that my self and didn't buy OS with it, and i don't like using illegal software, so desktop is gonna be Ubtunu 100%. But I using the laptop for work related thins to so on this one i will use dual boot.

Is it easy to install and play games? i heard of wine (if i spelled it correct)but never seen or use it.

PS: is there a easy way to authorize my self? i need to type my password 100 times when i'm changing things

---

### Post by estyles on 2009-01-09
> **Sultanabdel said:**
> well i did pay for one, desktop build that my self and didn't buy OS with it, and i don't like using illegal software, so desktop is gonna be Ubtunu 100%. But I using the laptop for work related thins to so on this one i will use dual boot.

Is it easy to install and play games? i heard of wine (if i spelled it correct)but never seen or use it.

While wine is an incredible piece of software, it's far, far from perfect.  I would bet that less than 50% of games work perfectly with it (my guess would be less than 25%, but that's just a guess), and many games just don't work at all.  For playing games, you're just better off with Windows (which still sounds funny to me - it's such a bloated OS, and for a long time games still ran in DOS-mode under Windows... it would be nice if there were an OS which was specifically designed for gaming - stripping out some of the unnecessary bloat, though it would still have to support a lot of Windows APIs, because that's what games are mostly written for).

If you're going to try a game in Wine, check out the App DB at winehq.com.  You'll get a sense for how easy or hard it is to run certain games under wine.

---

### Post by estyles on 2009-01-09
> **Sultanabdel said:**
> PS: is there a easy way to authorize my self? i need to type my password 100 times when i'm changing things

Didn't notice this first time...  After you type your password, it should store it for a while.  You're really better off not trying to disable that.  Once you have your system set up, you'll have to use sudo less frequently, and it will become a habit with certain commands (as far as I'm concerned, "sudo apt-get install" is all one command).

---

### Post by thinking2loud on 2009-01-09
> **Sultanabdel said:**
> 
ALLERT ALLERT!! noob question!
When i type this where will i find c++? or how i gonna start it?


Next noob lesson--type the following into a terminal:
```
whereis gcc

```

I get:
```
gcc: /usr/bin/gcc /usr/lib/gcc /usr/share/man/man1/gcc.1.gz

```

I expect you will get the same.  This tells you what command you are really running.  If you get a vague clueless blank, you need to install something.

---

### Post by Sultanabdel on 2009-01-10
> **thinking2loud said:**
> Next noob lesson--type the following into a terminal:
```
whereis gcc

```

I get:
```
gcc: /usr/bin/gcc /usr/lib/gcc /usr/share/man/man1/gcc.1.gz

```

I expect you will get the same.  This tells you what command you are really running.  If you get a vague clueless blank, you need to install something.

well Im getting the same but how do i start it? im getting premision error.

---

### Post by estyles on 2009-01-10
> **Sultanabdel said:**
> well Im getting the same but how do i start it? im getting premision error.

Do you have a .c or .cpp to compile with gcc?  Do some research.  GCC is a compiler, it's not an integrated coding environment like Visual Studio.  Take a look around the web for beginner programming guides and "teach yourself c++ in 20 years" or whatever...  Or pick a different language, but search out some instruction, because it doesn't really sound like you know where to start.

Note that if you're looking for an integrated coding environment like Visual Studio - I doubt you'll find a complete replacement, but you might be able to search or ask in the programming forum about a linux VS-type program.  I'm sure that something like it exists, though not exactly the same thing.  Me, I do my coding at work, in Windows, so I haven't yet tried to find anything like VS for Linux.  If you are actually used to VS, don't expect anything for Linux to be exactly the same, or likely even very close.

---

### Post by thinking2loud on 2009-01-10
paste the following into a terminal
```
echo "#include <stdio.h>" > hello.c
echo "main() { printf(\"hello, world\\n\"); }" >> hello.c
gcc -o hello hello.c
./hello

```

If you don't get a friendly greeting, you have a problem with gcc or libraries; start a new thread.

As mentioned by other esteemed contributors, gcc is just a part of the development environment.  This is the command-line command to get to the compiler and linker.  Big development projects have a complex tool chain.  This is merely the underlying command that graphical development environments (if you have one) invoke to build your program.

---

### Post by ibuclaw on 2009-01-10
> **Sultanabdel said:**
> 
ALLERT ALLERT!! noob question!
When i type this where will i find c++? or how i gonna start it?

You open up a terminal, and paste it in:
**Applications->Accessories->Terminal**
```
sudo apt-get install build-essential
```
Enter your password, and apt will download and setup the packages for you.

The C++ is names **g++**, all it is, is a compiler/linker.

If you feel that using the command-line is a too much of a big step, geany should be more than ample to suit a beginner's needs to learn C++.

Again, in the terminal:
```
sudo apt-get install geany
```
Or click [here.]("apt:geany")

At this point, you may have some questions about what has been discussed. Such as:
What is **sudo**? What does it do? Why do we use it? **apt-get** has already been mentioned before. What is it? What is so special about it?

**Sudo** is essentially "Super User DO". the superuser is the owner of the computer, he who has permissions to run commands as the super-user has access to the entire system, but as a security set default, Ubuntu is setup not to allow users to login as the superuser (or **root**, as we call him), as it is considered a major vulnerability, anything can maliciously modify/delete anything if you are careless.
So instead of logging in as root to carry out administrative tasks, sudo allows you to allow processes (as identified by process IDs) to run tasks for a period of time (15 minutes without a request to run a task is the default limit).

**Apt-Get** is a command-line front end to dpkg, a Debian Package Manager. A Package Manager is a software tool that manages all installed software on your system, and the installation/removal of it. Apt goes that one step further by bringing the idea of **repositories** into the equation, where you have a sources list (contains the list of sites to pull the software from) which contains several thousand software packages freely available for you to install (but don't install them all ;)) and you simply search and install the software you need/are looking for (see Synaptic, in **System->Administration->Synaptic Package Manager**).
But via apt isn't the only way to get packages. for example, I get most my games from [http://getdeb.net](http://getdeb.net) ... and Ubuntu has an abundance of ppa's (Personal Package Archives) which are Ubuntu developers own personal repositories which contain software that they keep up to date. But, as discussed earlier, up to date software doesn't necessarily mean the most stable, but that also don't mean that it won't be unstable or full of bugs either :).


Anyway, back to Geany, once you install it, go into **Applications->Programming->Geany**
You'll be shown a blank editor.
Click the down arrow next to **New** and select **C++ source file**
(Note, I am in a verbose mood at the moment, so I've given pictures :P)
[http://ubuntuforums.org/attachment.php?attachmentid=99399&stc=1&d=1231621055](http://ubuntuforums.org/attachment.php?attachmentid=99399&stc=1&d=1231621055)

Insert your helloworld code into the template.
[http://ubuntuforums.org/attachment.php?attachmentid=99401&stc=1&d=1231621055](http://ubuntuforums.org/attachment.php?attachmentid=99401&stc=1&d=1231621055)
If you can't read it, here it is:
```

#include <iostream>
using namespace std;

int main(int argc, char** argv)
{
    // Print Hello World!
    cout << "Hello World!" << endl;
    // Emulate the Windowsy system("PAUSE");
    cin.ignore(cin.rdbuf()->in_avail() + 1);
    return 0;
}

```
Then click "**Save**"
Now what I prefer to do is save all my source files inside a folder called **src**, you may prefer something different, but at least it keeps all my clutter away from my other documents ;)
Name the file **helloworld.cpp**
[http://ubuntuforums.org/attachment.php?attachmentid=99402&stc=1&d=1231621141](http://ubuntuforums.org/attachment.php?attachmentid=99402&stc=1&d=1231621141)

Once saved, we are ready to build the application, click **Build->Build** or press the **F9** key, and you'll see on the bottom dialogue box "**Compilation finished successfully**".
[http://ubuntuforums.org/attachment.php?attachmentid=99403&stc=1&d=1231620981](http://ubuntuforums.org/attachment.php?attachmentid=99403&stc=1&d=1231620981)

Now, click on the **Execute** button and a new terminal window will open with your compiled application.
[http://ubuntuforums.org/attachment.php?attachmentid=99404&stc=1&d=1231620533](http://ubuntuforums.org/attachment.php?attachmentid=99404&stc=1&d=1231620533)

Ain't that lovely :)

Anyways, hope that is enough for you to get started on your Ubuntu journey. Feel free to come back to the forums whenever you like if you have any questions to ask.

Regards
Iain

---

### Post by -kg- on 2009-01-10
> Intel Wireless 4965 is one beautiful Wireless Card! It performs exactly how one should (it /actually/ picks up all WAPs in a 100ft radius)
I know, because I have one on my HP Pavilion... It works out-of-box.

I'll second that.  I have this wireless card (chipset, actually...it's built in) on my laptop as well, and as tinivole said, it picks up wireless signals from all around (I can see my neighbor's) and works out of the box.

One thing, though; don't be put off if you boot to the Live CD and it won't hook to your network.  I found that I couldn't, and the reason was that I had WEP security set up on my router.  You can't set up a secure connection from the Live CD because you can't store the encryption key.  Once you install it to your hard drive, you can set it up and it works like a champ.

---

### Post by estyles on 2009-01-11
> **tinivole said:**
> At this point, you may have some questions about what has been discussed. Such as:

...followed by a lot of other very good information...

I don't know if you copy/pasted that from another thread or not, but that's some useful general knowledge info that should be useful to a lot of people.  If you didn't copy/paste it from somewhere, it would be a shame for it to be buried in this thread on a totally different subject...

---

