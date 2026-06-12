---
title: "apt-get install??"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by raziiq on 2009-05-18
Hi there.
i m very new to Linux, basically a windows user.
I have just installed uBuntu 9.04. I have used some commands in Terminal like

**apt-get install xterm**

and

**apt-get install konsole**

So i got the idea that it is used to install the apps, alright. But how does the terminal know that it has to download this xterm and konsole from somewhere and is to install it on the local computer as we have not supplied any source for downloading these apps (like xterm.source.com etc.)??

Is it that Terminal is intelligent enough to get the sources on the web when we supply the app name ??

Please explain this concept

Thank you :)

---

### Post by juancarlospaco on 2009-05-18
Yeah, i think that Terminal and APT is intelligent enough to get the sources on the web.

*Welcome to APT magics...!*


Do you Know APT:/URL ...?

You can install programs with just a link to nowhere, 
like [Cheese]("apt:/cheese") for example.

---

### Post by gashcr on 2009-05-18
actually, you don't even need to do that. Ok, it's faster sometimes when you need to install a lot of things, but if you're quite new, I would suggest to use the Add/remove utility under the applications menu, or even synaptic, since they have descriptions of the apps you're going to install. There's also a tool under the administration menu (software sources) where you can set third party sources for your downloads (usually, a deb repository).

Have a nice time :D

---

### Post by raziiq on 2009-05-18
oh thats awesome, but how to know that a particular app is of what title. I mean i just saw in this forum, someone was looking for mPlayer, as i see the command for it should be

**apt-get install mplayer**

but it was like

**apt-get install mozilla-mplayer**

How to know the titles of the apps??

BTW what does apt-get stand for??

Also i dont know about APT:/URL, can you please explain?? :)

---

### Post by pulpinator on 2009-05-18
The quick answer is that there is a file named /etc/apt/sources.list that has the locations on the web from where apt-get will download the packages that you need. 

You can change that file in the terminal, or through the Synaptic Package Manager. At some point you will have to change it if you want to get certain packages.

Here's the longer answer:
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by raziiq on 2009-05-18
> **gashcr said:**
> actually, you don't even need to do that. Ok, it's faster sometimes when you need to install a lot of things, but if you're quite new, I would suggest to use the Add/remove utility under the applications menu, or even synaptic, since they have descriptions of the apps you're going to install. There's also a tool under the administration menu (software sources) where you can set third party sources for your downloads (usually, a deb repository).

Have a nice time :D

Thanks for the info :)

But i really dont wanna stick to the GUI, i really want to peep into the commands so i am trying to use SHELL commands as much as i can. BTW i have used Add/Remove and installed some apps from there as well, thats just too easy n simple :)

---

### Post by kukibird1 on 2009-05-18
Here is some info.

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by gashcr on 2009-05-18
By the way, just to give you a clear answer to your question, ubuntu has a package manager (apt) which have a list of places from where to download the software (repositories). These are precompiled for your distribution, so it's not good to mix repositories. By default, Ubuntu uses the universe repository, which is the main list that ubuntu developers mantain, even though you can enable extra repositories (multiverse, community, etc). When you execute those commands in the terminal, you're calling the package manager, it syncs with his repositories database and searches for that app inside the servers ir has defined. 

I hope this helps you answer your question

have a nice day :D

---

### Post by raziiq on 2009-05-18
> **pulpinator said:**
> The quick answer is that there is a file named /etc/apt/sources.list that has the locations on the web from where apt-get will download the packages that you need. 

You can change that file in the terminal, or through the Synaptic Package Manager. At some point you will have to change it if you want to get certain packages.

Here's the longer answer:
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Now thats some info, thanks.
Infact i am a iPhone user and normally adding/removing packages so i think its like Cydia;), where we have repositories in which sources of the apps are present, right?

---

### Post by pulpinator on 2009-05-18
> **raziiq said:**
> oh thats awesome, but how to know that a particular app is of what title. I mean i just saw in this forum, someone was looking for mPlayer, as i see the command for it should be

**apt-get install mplayer**

but it was like

**apt-get install mozilla-mplayer**

How to know the titles of the apps??

BTW what does apt-get stand for??

Also i dont know about APT:/URL, can you please explain?? :)

The easiest way to see what packages are available is to use the Synaptic Package Manager GUI.

---

### Post by raziiq on 2009-05-18
> **gashcr said:**
> By the way, just to give you a clear answer to your question, ubuntu has a package manager (apt) which have a list of places from where to download the software (repositories). These are precompiled for your distribution, so it's not good to mix repositories. By default, Ubuntu uses the universe repository, which is the main list that ubuntu developers mantain, even though you can enable extra repositories (multiverse, community, etc). When you execute those commands in the terminal, you're calling the package manager, it syncs with his repositories database and searches for that app inside the servers ir has defined. 

I hope this helps you answer your question

have a nice day :D

Waoo, that was really helpful, thanks mate :)

---

### Post by Bradtek on 2009-05-18
apt-get, aptitude, synaptic package manager & Add Remove know where to get the programs because it  gets the information from your 
/etc/apt/sources.list 
(or GUI, System Menu/Administration/Software Sources)

When you reload synaptic or type sudo apt-get update
it fetches the latest listing from the addresses in  sources.list

---

### Post by pulpinator on 2009-05-18
> **raziiq said:**
> Now thats some info, thanks.
Infact i am a iPhone user and normally adding/removing packages so i think its like Cydia;), where we have repositories in which sources of the apps are present, right?

I don't have an iPhone, so no idea what Cydia is :).

---

### Post by juancarlospaco on 2009-05-18
Try:

sudo apt-cache search applicationnamehere

for example:

sudo apt-cache search mplayer

apt-get means *" Advanced Package Tool Get "* i think

APT:/URL is like apt-get install but designed for the World Wide Web

---

### Post by raziiq on 2009-05-18
Oh thats amazing :)

This Forum is just too good, people here are really friendly and informative.

Thanks Guys for all the Help, u all are beautiful :)

---

### Post by raziiq on 2009-05-18
ok one more question please.

if i want to open something in Nautilus from Terminal, what should be the command for that.

For example i want to open the /home/Desktop folder in Nautilus, what should be the command in Terminal??

---

### Post by waspbr on 2009-05-18
just do 

```
nautilus /location/you/want/to/open
```

To my desktop, for example, the code is

```
nautilus /home/waspbr/Desktop
```

---

### Post by raziiq on 2009-05-18
oh thanks for the reply, i ll try it.

I heard there is a command 'open' that will open a specified file in whatever default program it is attached to, for example

**open myTextFile.txt**

if i am not wrong the command will open myTextFile.txt in gedit??

---

### Post by Redache on 2009-05-18
> oh thanks for the reply, i ll try it.

I heard there is a command 'open' that will open a specified file in whatever default program it is attached to, for example

**open myTextFile.txt**

if i am not wrong the command will open myTextFile.txt in gedit??     This is going to be weird to explain:

In Linux the file types don't actually matter to the OS. It reads the header of the files to deduce the File Type. The file extensions are added for us Human Beings to understand, you could theoretically have a whole OS without any File Extensions whatsoever. This is called the Mime Type so for instance MyTextFile.txt has the Mime Type of the Text file.

Some programs do rely on File Types but that's down to the programmer rather than the OS itself.

a command like open won't work because it's telling the Terminal to open it rather than the terminal to open a graphical tool to work with the file.

You have to specify what application the Terminal will use.

For instance try the following:

```

gedit MyTextFile.txt
nano MyTextFile.txt
firefox www.google.com

```If you look at most of the applications properties (Second Click on the Application - Properties) it will give you the command used to start it. Use that command in the terminal to start the application.

Hope that's even close to what your looking for.

---

### Post by raziiq on 2009-05-18
that is a real explanation, thats exactly what i was asking.

So its recommended to use program names to open the files

---

