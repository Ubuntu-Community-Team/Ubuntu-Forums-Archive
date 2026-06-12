---
title: "Ubuntu virtualization problems &amp; questions."
date: 2010-03-10
forum: New to Ubuntu
---

### Post by VIKINGS on 2010-03-10
Ok so I took [quinnten83]("http://ubuntuforums.org/member.php?u=291401")'s advice and installed ubuntu under Windows 7 using Virtualbox. Got some problems I would really apreciate help with so lets get started.

1. As you can see in this [http://img130.imageshack.us/img130/8678/ubuntu910.jpg](http://img130.imageshack.us/img130/8678/ubuntu910.jpg) screen I can't make the ubuntu enviroment the same size as the Virtualbox window. I clicked auto-resize guest display nothing happened.
2. From the same screen you can see ubuntu won't detect my monitor, so I am stuck with that low resolution and refresh rate. I am using a Compaq P1220 22'.
3. While the virtual enviroment is working my windows browser(Wyzo) and probably my hole windows internet(havent tested other applications yet) won't work. The firefox inside Ubuntu seems to work, but I would like to be able to use both windows and ubuntu net at the same time. Hm, so I restarted the virtual machine and the second time my windows browser worked while ubuntu was running, let's hope it won't happen again but I will leave this here since I am still fuzzy about this.
4. I've been planing to start with the [Free Ubuntu Pocket guide by Keir Thomas. ]("http://www.ubuntupocketguide.com/")[Will that guide still server me well if I am runing a virtual ubuntu?]("http://www.ubuntupocketguide.com/")
5. Can you please remind me how to add repositories?
6. Ok so I started to learn about python since thats what I plan to use linux for most and i got to this page [http://wiki.python.org/moin/PythonEditors](http://wiki.python.org/moin/PythonEditors) I had no ideea there are so many, so which python editor should I use? I was thinking about Vim, is that a good choice?
7. I'm sure more will come, specially since I started learning python. Thank you for all the help people.

---

### Post by mikewhatever on 2010-03-10
Hi and welcome,:)

here are my 0.02:

1. You need guest additions installed. Once done, the resolution will autoresize as you resize the virtual machine's windows.

[http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/](http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/)

2. That's usually not a problem, as it doesn't matter if Ubuntu sees your monitor as Compaq, Dell or Fujutsu. Chances are, all three came off the same production line and just got branded differently.

4. Probably a good book, I don't know.

5. You probably shouldn't need any third party repositories, but since you asked....
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by VIKINGS on 2010-03-10
Cool thank you, I'll get right on that after school, what about question number 6? What editor should i use for python, is Vim good?

---

### Post by undecim on 2010-03-10
1: Install guest additions as per mikewhatever's link.
2: In VirtualBox, the guest OS never sees your real monitor. You need guest additions to get all your graphical settings
3: This is probably just a coincidence.
4: Any information about Ubuntu should apply in a VM just as much as a real machine
5: See mikewhatever's link
6: Check out IDLE. It's available in the repositories and is an excellent python editor


I would also like to suggest an alternative to using VirtualBox that you might find works a little better. Portable Ubuntu: [http://portableubuntu.demonccc.com.ar/](http://portableubuntu.demonccc.com.ar/)

The great thing about it is that you can put it on a thumb drive and run it on any Windows machine.

---

### Post by VIKINGS on 2010-03-10
Ok I installed the guest additions and it's much better except one problem, I still can't set the refresh rate to more then 60Hz, and it's kinda hurting my eyes.:( Thx for the info undecim, but for now I think i'll keep virtualbox.

---

### Post by undecim on 2010-03-10
> **VIKINGS said:**
> Ok I installed the guest additions and it's much better except one problem, I still can't set the refresh rate to more then 60Hz, and it's kinda hurting my eyes.:( Thx for the info undecim, but for now I think i'll keep virtualbox.

The refresh rate inside a virtual machine won't change anything that shows on your monitor. It's still all through VirtualBox's fake video card and VB just draws it to the window.

---

### Post by VIKINGS on 2010-03-10
Ok, thank you. So i decided to install vim after all(I want the interface too) can anyone please guide me on how to do this? I checked the vim page but its very confusing.

---

### Post by undecim on 2010-03-10
to install vim in Ubuntu. run this command from a terminal:
```
sudo aptitude install vim
```

---

### Post by VIKINGS on 2010-03-10
Didn't work.
vikings@VIKINGS-desktop:~$ sudo aptitude install vim
[sudo] password for vikings: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
No candidate version found for vim
No candidate version found for vim
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

vikings@VIKINGS-desktop:~$

---

### Post by cygnus-X1 on 2010-03-10
> **undecim said:**
> The refresh rate inside a virtual machine won't change anything that shows on your monitor. It's still all through VirtualBox's fake video card and VB just draws it to the window.

Oka-a-ay... Not to thread jump, I *just* tried to install 2K onto VB on a system that has 9.04 with an old ATI Radeon AIW card in it, just for running the TV part of the card. (I think it's 32M.) Myth doesn't work with that card, (as well as everything else in the repositories). So I thought I could stick 2K onto VB and run the ATI TV through there. Nothing loads, except DX. Is this because of the "fake video card" or might there be some other problem that needs tweaked in VB? 

Big Thanks!
[COLOR="White"]-[/COLOR]

---

### Post by undecim on 2010-03-10
@cygnus-X1: The guest OS cannot access any of the hardware on the host OS (with the exception of CD/DVD/BD drives, if you enable passthrough)

Everything is virtual.

There is a virtual video card, virtual sound card, virtual network card, etc. (some of them you can even choose which card models to emulate)

A virtual machine is a cage. Nothing gets in, and nothing gets out, except for for TCP/IP packets (internet connection) and mouse/keyboard input

---

### Post by VIKINGS on 2010-03-10
Ok, so I've managed to instal vim(not sure which version or if I have graphical interface too) anyhow I started to configure it so after I've modified the vimrc file(located in etc/vim) I tried to save it but it won't let me. It says "You do not have the permissions necesary to save the file". So I went to System>Administration>Users and Groups and enabled all the user privileges to both vikings and root. Tried again still wont let me save the file. What am I doing wrong? How am I supposed to work in ubuntu if the system won't let me change anything...?
Pfffff, can't create symbolic links, can't do anything!:( Won't someone please help me?!

---

### Post by NightwishFan on 2010-03-10
I have never used vim, but generally if you lack permissions you need to be root to solve them. Make sure you are running it as a standard user to begin with as well.

As for python editors, I prefer Kate and Gedit on the GUI. The only thing I use on the CLI is Nano, but not for programming.

---

### Post by VIKINGS on 2010-03-10
I am runing a standard account(the only account) and like I said I've enabled all the permissions I could see for both myself and root, what more can I do? How do I get root priviledges?... Maybe some screens would help.
My account:[http://img163.imageshack.us/img163/8775/vikingsaccount.jpg](http://img163.imageshack.us/img163/8775/vikingsaccount.jpg)
Root account:[http://img251.imageshack.us/img251/2795/rootaccount.jpg](http://img251.imageshack.us/img251/2795/rootaccount.jpg)
The way it treats me:[http://img94.imageshack.us/img94/6637/tletme.jpg](http://img94.imageshack.us/img94/6637/tletme.jpg)

P.S. If my own system doesn't trust me then I've really hit rock bottom.:((

---

### Post by VIKINGS on 2010-03-10
Still nothing?:( Oh well... *bump*.

---

### Post by undecim on 2010-03-10
If you need to edit a file with root privileges, use "sudo vim file"

---

### Post by mikewhatever on 2010-03-11
**gksudo gedit /etc/vim/vimrc**

This will let you edit and save the file. The question is, whether there is a local profile you should be editing, something in your home folder, .vimrc or similar.

---

### Post by VIKINGS on 2010-03-11
Thank you, abit late though. I managed to edit it yesterday by opening a nautilus window. Olso managed to install Komodo.However I am getting more confused by the minute by that guide. First it told me to install which ever editor I want, and then a few rows down they told me to install Komodo so I can follow the exercises. So what I need help with now:
1. Made symlink(using the command "ln -s <installdir>/bin/komodo /usr/local/bin/komodo") so I can just type Komodo in the terminal and the program should open. Made the link, but when I type komodo it says "command not found".Help.:(
2. Is there anywhere a comprehensive list of terminal commands and what they do? It would really help a beginner like me.
3. How can I install one of those cool themes with the buttons in the mid bottom part of the desktop? Something like this for example: [http://www.technobuzz.net/wp-content/uploads/2008/10/ubuntu-hardy-theme-2-400x250.jpg](http://www.technobuzz.net/wp-content/uploads/2008/10/ubuntu-hardy-theme-2-400x250.jpg)
4. More to come I'm sure.:P Thank you.

---

### Post by VIKINGS on 2010-03-11
*bump*

---

### Post by undecim on 2010-03-11
@VIKINGS:
1: did you double-check your path? make sure you use absolute paths (i.e. paths that start with /) just to be sure. Also, I've had problems with starting programs from links in other directories (xmind+symlink=segfaults galore). I fixed that by making a script to launch the real program. For example, my /usr/local/bin/xmind looks like this:
```
#!/bin/sh
exec /usr/local/xmind/xmind
```
Just make sure that after creating a script like this, you run chmod a+x on it to make it executable
```
sudo chmod a+x /usr/local/bin/xmind
```

2: There are plenty of guides online. This one for example: [http://ss64.com/bash/](http://ss64.com/bash/)

If you ever need to figure out what a command does, just run "man command" to view the manual for that command.

3: Those buttons are actually part of a separate program called a dock bar. There are several dock bars in the Ubuntu repositories: cairo-dock, avant-window-navigator, and gnome-do (with the "docky" theme; gnome-do and docky should be split up into two separate programs in 10.04)

---

### Post by VIKINGS on 2010-03-11
Thank you udecim:
1. I did use absolute paths and like I said if I try to run the command again it tells me that it has already been added to bin, problem is when I type komodo it tells me command not found. Is there any way to delete it and try again? Or how should I approach this matter...
2. Nice, it's a good start, should keep me busy for a spell.
3. Cool, I'll check the repositories and add them right now.:)

---

### Post by undecim on 2010-03-11
If the link is already there, then you will have to remove it first ```
sudo rm /usr/local/bin/komodo
```

---

### Post by VIKINGS on 2010-03-11
Thank you, I removed it, added it again same problem if I type komodo I get "command not found" but if i try to add it again I get "ln: creating symbolic link `/usr/local/bin/komodo': File exists" so I'm out of ideeas.:( Sorry but I didn't understand what you meant with the script, I'm new with this whole linux thing, I don't know how to make scripts yet. Anyway now that I have the dock installed(managed to do that:P) I don't think it matters anymore as I can just open it from there. Too bad, it's cool working on the terminal, and I would have liked to add it to my "things learned today" list. Oh well, I'll be back with more questions soon, I'm sure trouble is waiting for me right around the corner.:)

---

### Post by undecim on 2010-03-11
Is the komodo binary executable? run "sudo chmod a+x <installdir>/bin/komodo" to make sure, and try it again.

---

