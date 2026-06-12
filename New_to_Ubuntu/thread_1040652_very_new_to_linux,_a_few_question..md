---
title: "very new to linux, a few question."
date: 2009-01-15
forum: New to Ubuntu
---

### Post by insanity99 on 2009-01-15
hey. i am currently running Ubuntu with Wubi. i am loving Ubuntu so far but still have a lot to learn.

i am a new to linux and would like to know a few things.

1. where are programs insatalled too? i am still used to the windows folder structure, C:\program files.

2. is there a task manager? like windows ctrl + alt + del.

3. is there an object dock type program?

4. should i get an anti virus? if so which one? i have Avast on windows 

5. can i change the way it always asks for a password? reminds me too much of the annoying UAC with vista.

6. when i installed ubuntu using Wubi i only choose 30GB and would like to increase the size. could this be done without uninstalling ubuntu and losing everything i have done so far?

thanks. sorry about all the questions :P

---

### Post by insanity99 on 2009-01-15
oh right i figured out question 2.

---

### Post by 2hot6ft2 on 2009-01-15
> **insanity99 said:**
> hey. i am currently running Ubuntu with Wubi. i am loving Ubuntu so far but still have a lot to learn.

i am a new to linux and would like to know a few things.

1. where are programs insatalled too? i am still used to the windows folder structure, C:\program files.

2. is there a talk manager? like windows ctrl + alt + del.

3. is there an object dock type program?

4. should i get an anti virus? if so which one? i have Avast on windows 

5. can i change the way it always asks for a password? reminds me too much of the annoying UAC with vista.

6. when i installed ubuntu using Wubi i only choose 30GB and would like to increase the size. could this be done without uninstalling ubuntu and losing everything i have done so far?

thanks. sorry about all the questions :P
1. Linux is not windows see link in my sig

2. You mean task manager no this is not windows
P.S. Ctrl+Alt+Del will reboot ubuntu

3. ? Explain what you mean.

4. You don't need one but you do have one installed called clamav if you 
want a gui for it you have to install it use
```
sudo apt-get install clamtk
``` in a terminal.
Applications>Accessories>Terminal
then it will be in 
Applications>System Tools>Virus Scanner
also see 
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

5. yes you can,
System>Administration>Login Window> Security tab first option
That's just for booting up as for it asking for your password to make system changes no not that I know of it's a security issue.

6. I don't use wubi so can't help you there.

---

### Post by 2hot6ft2 on 2009-01-15
For # 3 you may be talking about something like screenlets, desklets, system monitor docks, or cairo dock there are a bunch.

And for # 2 you can put ```
top
``` in a terminal for something similar.

---

### Post by user11 on 2009-01-15
#2. On the top of your screen, go to System, Administration, System Monitor.
This should be pretty close to what you are looking for. Ignore the wise arses, you're gonna hear a lot of "this isn't windows", comes with the turf.

---

### Post by earthpigg on 2009-01-15
> 3. is there an object dock type program?

AWN is the most popular dock.

if you mean sexy 3d desktop stuff, that would be compiz.

system->admin->synaptic. look for 'awn' and 'compiz' for that stuff.

the password stuff is not nearly as annoying as UAC, and exists for a reason... tools you ahve in linux are much more powerful than in windows. it is much easier to jack your system up - hence, it asks you for your password. if it really bugs you and you dont care about security., make your password 2 letters.

edit: compiz-config-blabla is the package you are looking for in synaptic for sexy desktop effects.

---

### Post by earthpigg on 2009-01-15
> 4. should i get an anti virus? if so which one? i have Avast on windows 

no, dont bother unless your computer is a server that has client windows machines to worry about.

a linux computer without an antivirus is far safer from viruses/malware than any windows box **with** an antivirus.

---

### Post by Bölvaður on 2009-01-15
2hot6ft2 answered well and pointed out the obvious fact that Ubuntu is not Windy.
You really should hang on this forum for a month to see other peoples problems, as they are often asking about stuff you might want to know but didn't think of asking about, that way you may learn A LOT.

But I would like to give the list a try:

> **insanity99 said:**
> 
1. where are programs insatalled too? i am still used to the windows folder structure, C:\program files.
To be honest, you do not really need to know as your package manager will take care of all programs it has installed so you will not really need to know where they are. Look at Applications &#8594; Add/Remove and System &#8594; Administrator &#8594; Synaptic Package Manager.
But if you insist of knowing... /usr/share, and for what you might think of as shortcuts you link other shortcuts (lunchers) at /usr/bin
When you install programs without super user rights you should install it to something like /home/you/programs

> **insanity99 said:**
> 
2. is there a task manager? like windows ctrl + alt + del.

I guess you can change ctrl+alt+del to show system monitor but you really shouldnt need to use system monitor that often that it needs a keyboard shortcut.

> **insanity99 said:**
> 
3. is there an object dock type program?

Are you talking about something like... try installing awn like 2hot6ft2 suggested.. but Im going to suggest doing it differently. Applications &#8594; Add/Remove look for AWN or avant window navigator like it is called

> **insanity99 said:**
> 
4. should i get an anti virus? if so which one? i have Avast on windows 

Umm... no. You may need to stop sending infected programs onto Windy's partition but it is highly unlikely you will need antivirus anytime soon.. you will see reports in all news media when it happens (promise)

> **insanity99 said:**
> 
5. can i change the way it always asks for a password? reminds me too much of the annoying UAC with vista.

This isnt really about taking password off. It can make sense taking it off the login (System &#8594; Administration &#8594; Login Window) but when you run on Ubuntu you have limited access to parts of the file system, so you will not be able to destroy the computer. Most programs have the same limited access to your computer, but if you would disable that user account and only use the SUPER USER, which can do anything. Then your computer will be considered under great security risk.. any program can delete or change any file on your system.... you probably do not want that.
But yes... you can run only as super user and never be asked for passwords.. but it is a reason why MS is trying to implement it.

> **insanity99 said:**
> 
6. when i installed ubuntu using Wubi i only choose 30GB and would like to increase the size. could this be done without uninstalling ubuntu and losing everything i have done so far?

I have no idea about Wubi but I cannot imagine a reason why it wouldnt work. But I would suggest defragging your windows disk few times and shrink your windy partition from windy it self. Then fire up ubuntu and install "gparted" (type in terminal "sudo apt-get install gparted" (sorry but it is a lot quicker to write commands than where to click, but you can do it also from synaptic of course))
It is very easy to use, but I would think that making the parition bigger would take about 1-2 hours as when you make it bigger all the data on the disk has to be moved accordingly.



sorry for the long answers.. but it is not even close to being detailed.
btw the reason why we use the terminal for tech support is because not everyone has the same desktop environment, but most things in the terminal is the exact same and only takes copy and paste skills from your behalf ;)

---

### Post by Facetious Falcon on 2009-01-15
> **insanity99 said:**
> hey. i am currently running Ubuntu with Wubi. i am loving Ubuntu so far but still have a lot to learn.

i am a new to linux and would like to know a few things.

1. where are programs insatalled too? i am still used to the windows folder structure, C:\program files.

2. is there a task manager? like windows ctrl + alt + del.

3. is there an object dock type program?

4. should i get an anti virus? if so which one? i have Avast on windows 

5. can i change the way it always asks for a password? reminds me too much of the annoying UAC with vista.

6. when i installed ubuntu using Wubi i only choose 30GB and would like to increase the size. could this be done without uninstalling ubuntu and losing everything i have done so far?

thanks. sorry about all the questions :P

1. Programs are usually installed in several different places for example you'll find all the executable files in the /usr/bin directory. Their library files will be /usr/lib64/ or /usr/lib32/ and config files will often be in /etc/ but this is irrelevant when it comes to day to day use. 

2. Looks like you've found an answer but if I ever want to find a task manager I just go into the terminal and type 'top' this lists all processes running and updates it in real-time. To quit it press 'q' and then to kill a process just type 'kill %' and then the process id after the '%'.

3. Don't know what you're on about.

4. Linux is much more secure than Windows because all important system files can only be edited using the root user. As the root user is not the day-to-day user a potential virus will have limited access to your system and hence an anti-virus isn't really needed.

5. I think you can get it to remember a session using keyrings (Administration->Authorizations). Again, what happens here when you type your password is that your temporarily becoming the root user so that you can do administrative tasks which is mainly to do with the security.

6. I'm not sure about the question but I think you mean to say you've partitioned 30 gb for Ubuntu and want more. This is possible using the live CD. The good thing about linux is that you can install it on many different partitions and/or hard disks using fstab.

---

### Post by Bölvaður on 2009-01-15
> **earthpigg said:**
> no, dont bother unless your computer is a server that has client windows machines to worry about.

a linux computer without an antivirus is far safer from viruses/malware than any windows box **with** an antivirus.

In all fairness.. you could run a virus on linux without damaging your system and without the virus spreading... unless if you really like the sudo and su command... ooh and gksu and gksudo

---

### Post by Vantrax on 2009-01-15
It may help to know there are two ways to 'draw' your desktop in Gnome.

The first is the default called metacity, its simple, plain, and it works with everything (its used by default). The second is called compiz, its more advanced, has pretty effects, and requires 3d processing, in some cases it will not work without better drivers for your linux box.

As far as docks go there are again two types. The first one is called Cairo and works under metacity and compiz, its a lightweight but simple. The second is AWN, its pretty, flashy, and can look like the OSX dock. It requires compiz.

Dont worry about viruses, keep patched, and unless you start running server software dont worry about firewalls either (ubuntu is locked down by default)

You might want to take a peak at the security discussions forum for a sticky explaining apparmor if your worried about being vulnerable, but honestly compared to windows you could do almost anything and you will still be better off.

---

### Post by fabounet on 2009-01-16
I don't call AWN flashy, **that**'s flashy :
[http://fr.youtube.com/watch?v=yWwXaQMdhiQ]("http://fr.youtube.com/watch?v=yWwXaQMdhiQ")

but you're right, Cairo-Dock can also be very lightweight, depending on how you configure it ^_^

---

### Post by hyper_ch on 2009-01-16
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by 3rdalbum on 2009-01-16
Don't fiddle with Ubuntu's security system. Don't enable automatic logins and don't try to bypass the password prompt. The phrase "Don't run as root" has been recommended practice for forty years, and there are forty years worth of stories of people who have ignored the recommendation and lived to regret it.

Get used to typing your password to elevate to root. All major operating systems have this now, and none of them are going to get rid of it.

---

### Post by stevoo on 2009-01-16
> **insanity99 said:**
> hey. i am currently running Ubuntu with Wubi. i am loving Ubuntu so far but still have a lot to learn.

i am a new to linux and would like to know a few things.

Dont we all ... there isnt a day that we dont learn a new thing. 



> **insanity99 said:**
> 1. where are programs insatalled too? i am still used to the windows folder structure, C:\program files.
They are all stored somewhere in your root directory. I an folder somwhere in there. All your setting are stored in your /home/username/ directory in hidden folders. 


> **insanity99 said:**
> 2. is there a task manager? like windows ctrl + alt + del.

using $top in the terminal will display all the running programs. 

> **insanity99 said:**
> 3. is there an object dock type program?
Avant navigator is very nice and easily configurable. You may wanna have a look

> **insanity99 said:**
> 4. should i get an anti virus? if so which one? i have Avast on windows  AV is not really needed in Linux. I have been running 3 different machines with out the use of an AV. The need of one is low for various reasons.

> **insanity99 said:**
> 5. can i change the way it always asks for a password? reminds me too much of the annoying UAC with vista. Well i am not sure if you can. Some key elements in your system that require unlocking is there for extra production.

> **insanity99 said:**
> 6. when i installed ubuntu using Wubi i only choose 30GB and would like to increase the size. could this be done without uninstalling ubuntu and losing everything i have done so far? There is a way that this can be done but it is not easy and a bit risky as well as time consuming. You dont need more. Anything you want to store you have a different partition and store everything there ! 


Enjoy Ubuntu !

---

### Post by insanity99 on 2009-01-16
thank you for all the help guys. i had no idea the security in ubuntu was so much greater than windows! and sorry about the stupid title, so i should but a [resolved] on the title?

the terminal seems very powerful, i can use DOS command line at an intermediate level and use it a lot, is terminal easier or harder in your opinions?

EDIT: and sorry about question 3, i should have said the Mac OS 'dock' functionality rather than the little known objectdock

---

### Post by 3rdalbum on 2009-01-17
> **insanity99 said:**
> the terminal seems very powerful, i can use DOS command line at an intermediate level and use it a lot, is terminal easier or harder in your opinions?

If you have a grip of how to invoke programs with special parameters in MS-DOS, then you'll quickly understand how it works with Linux programs. The difference is that there are some very powerful terminal programs for Linux; many of them actually do all the backend processing for GUI programs. For instance, when you burn a CD or DVD, you're actually indirectly using a command-line program that has a whole heap more options than the GUIs expose :-)

There are some things that I don't know if you can do in MS-DOS, like redirecting the output of one command to the input of another, temporarily pause programs, schedule a command to be run when the system is idle, and do pattern searching and replacing on files; but all but the last one are easy and very useful.

In short, if you've used a command-line before in MS-DOS, then you can learn things quickly.

---

