---
title: "Most Common Terminal Commands by usage"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by LinuxMaster9 on 2011-05-09
Hi there,

My purpose for posting this thread is to assist all those n00bs on Terminal usage.:D

I will take some of the most common Terminal commands and their usage and separate them by type. The commands will be in [COLOR="SeaGreen"]green[/COLOR], the modifiers will be in [COLOR="Blue"]blue[/COLOR], the variable will be [COLOR="Red"]red[/COLOR] and the directories will be [COLOR="Sienna"]brown[/COLOR].

Let us start off with simple things like:

List contents of Directory
user$ [COLOR="SeaGreen"]ls[/COLOR]

Next:
Change Directory:
user$ [COLOR="SeaGreen"]cd[/COLOR] [COLOR="#a0522d"]/blah[/COLOR]

This is used in this syntax: "user$" is the username of the current user and should not be entered with the command. This is displayed to let the user know whether or not they are in root or not. 

The first part of the command is "[COLOR="SeaGreen"]cd[/COLOR]" which stands for 'Change Directory'. This is the Primary command of the syntax string.

The second part of the command is "[COLOR="#a0522d"]/blah[/COLOR]" replace 'blah' with the name of the directory you wish to change to (Everything is Case-Sensitive). You can use '..' instead of '[COLOR="#a0522d"]/something[/COLOR]' to go back one directory.

For Example:
user$ [COLOR="SeaGreen"]ls[/COLOR]
Contents of [COLOR="#a0522d"]/home/user/[/COLOR]
blah blah blah blah [COLOR="#a0522d"]Downloads[/COLOR]

user$ [COLOR="SeaGreen"]cd[/COLOR] [COLOR="#a0522d"]/Downloads[/COLOR]
[COLOR="#a0522d"]user/Downloads[/COLOR]$ [COLOR="SeaGreen"]ls[/COLOR]
List Contents of [COLOR="#a0522d"]/home/user/Downloads/[/COLOR]
blah blah blah blah


That is all for now. Let me know what you would like to know about.:P

---

### Post by taseedorf on 2011-05-11
Hm.... not sure what the point of that post was consider it was so short, but........ go into depth about automation and scripts - commands to make your computer do something.

File systems checks...

adding users

configuring firewall...

---

### Post by blind2314 on 2011-05-11
> **LinuxMaster9 said:**
> Hi there,
 
My purpose for posting this thread is to assist all those n00bs on Terminal usage.:D
 
I will take some of the most common Terminal commands and their usage and separate them by type. The commands will be in [COLOR=seagreen]green[/COLOR], the modifiers will be in [COLOR=blue]blue[/COLOR], the variable will be [COLOR=red]red[/COLOR] and the directories will be [COLOR=sienna]brown[/COLOR].
 
Let us start off with simple things like:
 
List contents of Directory
user$ [COLOR=seagreen]ls[/COLOR]
 
Next:
Change Directory:
user$ [COLOR=seagreen]cd[/COLOR] [COLOR=#a0522d]/blah[/COLOR]
 
This is used in this syntax: "user$" is the username of the current user and should not be entered with the command. This is displayed to let the user know whether or not they are in root or not. 
 
The first part of the command is "[COLOR=seagreen]cd[/COLOR]" which stands for 'Change Directory'. This is the Primary command of the syntax string.
 
The second part of the command is "[COLOR=#a0522d]/blah[/COLOR]" replace 'blah' with the name of the directory you wish to change to (Everything is Case-Sensitive). You can use '..' instead of '[COLOR=#a0522d]/something[/COLOR]' to go back one directory.
 
For Example:
user$ [COLOR=seagreen]ls[/COLOR]
Contents of [COLOR=#a0522d]/home/user/[/COLOR]
blah blah blah blah [COLOR=#a0522d]Downloads[/COLOR]
 
user$ [COLOR=seagreen]cd[/COLOR] [COLOR=#a0522d]/Downloads[/COLOR]
[COLOR=#a0522d]user/Downloads[/COLOR]$ [COLOR=seagreen]ls[/COLOR]
List Contents of [COLOR=#a0522d]/home/user/Downloads/[/COLOR]
blah blah blah blah
 
 
That is all for now. Let me know what you would like to know about.:P
 
All of this information is available via a simple Google search and is more concise and more detailed than in the post above. The "New to Ubuntu? Start here..." sticky also contains links to several guides written by users of the forums or ones that were found to be particularly useful through searches. This wasn't intended to bash you or your idea to help, that's great; it's just that it already exists in a better format. So, instead of making your own post, why not contribute to the ones that already exist? :)

---

### Post by jtarin on 2011-05-11
OK...here's my contribution.....

---

### Post by nidzo732 on 2011-05-11
> **jtarin said:**
> OK...here's my contribution.....

This is for redhat

---

### Post by jtarin on 2011-05-11
> **nidzo732 said:**
> This is for redhat
Take what you need....Linux....it's not all about Ubuntu.

---

### Post by jerrrys on 2011-05-11
**APT and Dpkg Quick Reference Sheet**

[ATTACH]191851[/ATTACH]

---

### Post by widda on 2011-05-11
> **LinuxMaster9 said:**
> Hi there,
Y
My purpose for posting this thread is to assist all those n00bs on Terminal usage.:D

I will take some of the most common Terminal commands and their usage and separate them by type. The commands will be in [COLOR=SeaGreen]green[/COLOR], the modifiers will be in [COLOR=Blue]blue[/COLOR], the variable will be [COLOR=Red]red[/COLOR] and the directories will be [COLOR=Sienna]brown[/COLOR].

Let us start off with simple things like:

List contents of Directory
user$ [COLOR=SeaGreen]ls[/COLOR]

Next:
Change Directory:
user$ [COLOR=SeaGreen]cd[/COLOR] [COLOR=#a0522d]/blah[/COLOR]

This is used in this syntax: "user$" is the username of the current user and should not be entered with the command. This is displayed to let the user know whether or not they are in root or not. 

The first part of the command is "[COLOR=SeaGreen]cd[/COLOR]" which stands for 'Change Directory'. This is the Primary command of the syntax string.

The second part of the command is "[COLOR=#a0522d]/blah[/COLOR]" replace 'blah' with the name of the directory you wish to change to (Everything is Case-Sensitive). You can use '..' instead of '[COLOR=#a0522d]/something[/COLOR]' to go back one directory.

For Example:
user$ [COLOR=SeaGreen]ls[/COLOR]
Contents of [COLOR=#a0522d]/home/user/[/COLOR]
blah blah blah blah [COLOR=#a0522d]Downloads[/COLOR]

user$ [COLOR=SeaGreen]cd[/COLOR] [COLOR=#a0522d]/Downloads[/COLOR]
[COLOR=#a0522d]user/Downloads[/COLOR]$ [COLOR=SeaGreen]ls[/COLOR]
List Contents of [COLOR=#a0522d]/home/user/Downloads/[/COLOR]
blah blah blah blah


That is all for now. Let me know what you would like to know about.:P
Yeah, I like the colour-coding. Could go somewhere. Sometimes a  solution's offered and I know I need to adapt it for my own case, but  sometimes have trouble understanding what bit in a command refers to  what, or what it's actually doing even. I mean any command can be  translated into say, full  English in a short guide, I'd like it anyway!  A few of those translations seen would stick in my linguist brain! like  I know 'sudo apt-get install gnome' means 'Allow me maximum access to  system while using terminal, then from the repositories install Gnome  and whatever else it needs to function, and then resume 'ready for more  commands' prompt. Each little word of the command says a lot!  Yes, I  think this thread has potential. I know there are very good sources on commandline use, but that's just it, theres more than one.

---

