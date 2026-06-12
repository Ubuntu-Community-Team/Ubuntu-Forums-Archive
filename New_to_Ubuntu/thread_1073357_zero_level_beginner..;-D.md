---
title: "zero level beginner..;-D"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by abhigyan91 on 2009-02-18
hey evry1.. i just installed ubuntu 8.10 last week and i have to say... im pretty impressed by the first luk and feel of linux. i've been using windows all my life.. but id like to have a little clarification on sum really basic doubts:

1. is it true that in order to use linux u have to know a lot of coding etc? because the whole terminal thing kinda gives me the goosebumps.. like i dunno wt to with it since i know absolutely nothing about how to start off using the terminal. is there a publication or a ebook that can help me get started on the keywords(like sudo..stuff like that)? 

2. y is it that the system keeps asking me the password evry 2mins??? i didnt know about this so i put like a gigantic password.. now i dunno how to change the password..its kind of pain...
i tried sudo password... will that work?

3. in windows... u know the exact path of the folders etc.. like program files in c:..etc 
id like to know wher the program files in linux r saved.. 
for example... i installed linux dc++ or linuxdpp.. but i couldnt find out wher the actual linuxdpp program was saved!!

thanks a lot..looking forward to using linux..

abhigyan

---

### Post by binbash on 2009-02-18
1-No you can use the linux just like windows if you dont know the coding or any terminal commands.But with terminal com2-mands you can do things 10 12x faster than windows.Also you will need terminal commands if you have problem.But as long as you open a topic when you have problems, the community will help you to solve your problems , and also you start learning bash commands etc
2-You can disable sudo password but i dont suggest it, it is not secure.You can also use autologin but i also don't suggest it
3- program files are saved under /usr/bin /usr/local/bin or /usr/sbin under linux BUT DONT think the windows way.The file system is different.You don't know the where it is saved just press altf2 or open a terminal and write linuxdpp.You will not navigate to program files etc like windows to run the program

---

### Post by fuzzyk.k on 2009-02-18
about the root password
open the terminal
applications >Accessories>terminal
type 
sudo su

to switch to super user mode

then type passwd as the super user
it will ask you for the new password and confirmation
am not sure about sudo passwd root so i recommend the first method

---

### Post by jerome1232 on 2009-02-18
> **abhigyan91 said:**
> 
1. is it true that in order to use linux u have to know a lot of coding etc? because the whole terminal thing kinda gives me the goosebumps.. like i dunno wt to with it since i know absolutely nothing about how to start off using the terminal. is there a publication or a ebook that can help me get started on the keywords(like sudo..stuff like that)? 

Pscyocats guide is pretty nice
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

> **abhigyan91 said:**
> 
2. y is it that the system keeps asking me the password evry 2mins??? i didnt know about this so i put like a gigantic password.. now i dunno how to change the password..its kind of pain...
i tried sudo password... will that work?

System-Administration-Users and Groups-Click "Unlock", select your user, click "Properties", then change the password.

The reason you get asked for your password is your account is a normal account, in order to install software or do system wide administration tasks you must authenticate with your password, this is to prevent malware and etc from doing damage to the system.

> **abhigyan91 said:**
> 
3. in windows... u know the exact path of the folders etc.. like program files in c:..etc 
id like to know wher the program files in linux r saved.. 
for example... i installed linux dc++ or linuxdpp.. but i couldnt find out wher the actual linuxdpp program was saved!!
Programs are usually in /usr, some will goto /opt
Core system programs  are in /sbin
several extra system programs are in /bin
Configuration files are in /etc
libraries are in /lib (these are .so files in linux, equivalent to .dll's in windows)

Here's a little overview of the Linux Filesystem Hierarchy [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

---

### Post by Metallion on 2009-02-18
If you really want to know where exactly files are installed you can open synaptic package manager, right click on any installed package en click properties. There should be a tab with installed files on there.

But indeed it's different from windows. Windows makes one directory for each program installed but linux groups all the executables together and keeps the data files somewhere else. The benefit is that you can easily launch programs by pressing alt+f2 and typing their name. Ubuntu will then just search that few directories where all the executables are and run it from there. Often it is so much faster to type firefox instead of opening a start menu, looking for the firefox folder and then clickin on the icon.

---

### Post by presence1960 on 2009-02-18
for #1. check this out : [http://linuxcommand.org/](http://linuxcommand.org/) and check out this attachment.Just unpack the file and you will get a pdf file. With a little willingness to learn you will become more comfortable with the command line. If all else fails you can copy & paste commands into the terminal. The community here is awesome and will help you through your difficulties. Welcome to Linux!!

---

### Post by redseventyseven on 2009-02-18
In response to question 1, you don't "need" to learn how to code things in order to use linux. But sometimes you may need to use the terminal to fix things. This is very similar to how Windows is - occasionally you need to open a DOS command window or root around through the Registry in order to fix a problem.

When you ask for help on these forums, frequently you will get responses in the form of terminal commands. There are a number of very good reasons for this:
[LIST=1]
[*]It is much more convenient to type out "go to a terminal and type {command}" than it is to type out "click on {menu x}, this will open up a dialog box, click on {tab y}, enter your password, etc. etc."
[*]Linux is a very customisable system (hence the hundreds of other "distributions" of Linux, not just Ubuntu), so it is very likely that the helper will have customised their system to suit their needs to such an extent that the menu items no longer resemble what they do when Ubuntu is first installed). The terminal commands, however, remain consistent.
[*]Terminal commands are the same regardless of what language the user speaks. For many of the people who offer help on these forums, English is a second language; all the menus will be set up in their own language. However, the terminal commands will still be the same.
[/LIST]

My rule of thumb (others may disagree) is that complicated terminal commands will generally be needed to fix problems, but once a particular problem has been fixed, you should be able simply to point and click to do your regular work (until you encounter another problem later on). Initially, of course, you'll encounter quite a few problems, so it may seem that you're using the terminal all the time, but you should find after a while that you're using the terminal less and less. Even further down the line, there may come a point that you start using the terminal more and more, not because you're forced to, but because you've actually started to get more comfortable with it that you *choose* to use it!

---

### Post by abhigyan91 on 2009-02-18
thank you every1 for your help.. the links here hav been extremly useful.. thx u all so much agn..

---

### Post by rburkartjo on 2009-02-18
ab.just hang in there i started using ubuntu about 2 years ago using the command line will come in time it is great. just dont give up and use this form as much as you need to. it is great/cheesemaker

---

