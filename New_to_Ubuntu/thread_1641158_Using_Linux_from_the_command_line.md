---
title: "Using Linux from the command line"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by nahallac on 2010-12-08
Hello all,
 
I have been flirting with the idea of learning Linux for a while now, and keep having a vague crack at it then moving off to learn other things. However, I am now determined to dedicate some proper time to it! 
 
With that in mind, I've dispensed with a desktop and have got myself an Ubuntu server. I figure that if I am forced to use the CLI I'm going to pick it up quicker. 
 
I have a purpose in mind (I want to run Postfix as an SMTP transport gateway for my Exchange 2010 mailbox server), but for now I just want to start learning the CLI basics. For one, I have been trying to find out how to scroll back through the results of a command. I have just run ifconfig --help, and can only see the last part of the output. Stupid question I know, but I'm happy to ask really daft stuff... As long as I learn I'll take looking a wally!

---

### Post by bananas4370 on 2010-12-08
> **nahallac said:**
> Hello all,
 
I have been flirting with the idea of learning Linux for a while now, and keep having a vague crack at it then moving off to learn other things. However, I am now determined to dedicate some proper time to it! 

That's great to hear.
 
> With that in mind, I've dispensed with a desktop and have got myself an Ubuntu server. I figure that if I am forced to use the CLI I'm going to pick it up quicker. 

I suggest installing a GUI. You can still access the command line through a terminal program. 
 
> I have a purpose in mind (I want to run Postfix as an SMTP transport gateway for my Exchange 2010 mailbox server), but for now I just want to start learning the CLI basics. For one, I have been trying to find out how to scroll back through the results of a command. I have just run ifconfig --help, and can only see the last part of the output. Stupid question I know, but I'm happy to ask really daft stuff... As long as I learn I'll take looking a wally!

Shift-Page Up/Page Down will let you scroll through the output of a command. Have you had a look at the [Command Line Howto]("https://help.ubuntu.com/community/CommandlineHowto")? I found it a good starting point.

Cheers
Patrick

---

### Post by bodhi.zazen on 2010-12-08
1. Learn to read the man pages.

2. Try this site:

[http://linuxcommand.org/](http://linuxcommand.org/)

At least the first few sections.

---

### Post by oracle2b on 2010-12-08
[This app]("https://launchpad.net/clicompanion") could be of some assistance.

---

### Post by SeijiSensei on 2010-12-08
> **nahallac said:**
> I have a purpose in mind (I want to run Postfix as an SMTP transport gateway for my Exchange 2010 mailbox server)

I suggest considering [**MailScanner**]("http://www.mailscanner.info/") if you want to put a box between incoming mail and your Exchange server.  I've been running it for years now to scan incoming and outgoing mail at my own and clients' sites. In combination with [ClamAV]("http://www.clamav.net/") and [spamassassin]("http://spamassassin.apache.org/") you'll get a very effective virus and spam scanner for free.

I've only installed this on RedHat/CentOS sites; for that platform, the developer, Julian Field, provides an automated script to install everything you need.  However there's also this [**detailed set of instructions**]("http://www.mailscanner.info/ubuntu.html") that should probably guide your efforts on the Ubuntu platform.

---

### Post by nahallac on 2010-12-13
Hello,
 
Sorry for the tardy reply! Anyway...
 
First of all, I went for the GUI-less server option as I figured having the GUI there as a crutch was against the idea of learning Linux properly! I work in Infrastructure and am pretty experienced with MS products, as well as Cisco, so I hope I have the mentality to suss it.
 
The site recommendations are excellent, so thank you. I just had particular problems finding how to move through the output of a command, so the shift pgup/down shortcut is handy. I have installed the openssh server package now, so I'm using Putty to emulate the terminal (which make it a bit easier).
 
I am slowly going through the Postfix config, so will get the hang of that soon. I like to know what every line does, so it's always a slow process. I will look in to spam filtering and general nastiness detection next, thank you again for the recommendations.
 
The next thing I should ask is if anyone can think of something interesting I can do with my server? I was thinking of having a go at getting Snort working away somewhere, any more ideas?! Is there anything I could do with the OS itself to configure and personalise it? ANything that would get me round the filesystem and understand where things live?

---

### Post by rburkartjo on 2010-12-16
ora tks for that cli companion link. a lot easier that using  history and then ! from the terminal

---

### Post by Hippytaff on 2010-12-16
This link might be of some interest - [http://kmandla.wordpress.com/software/](http://kmandla.wordpress.com/software/)

---

### Post by nahallac on 2010-12-16
Hippytaff - that article is brilliant! I am going to have a proper trawl through it tonight, but already it appeals to me. I think the fact that I am a grumpy sod like the blogger has something to do with it.
 
And is that Transport Tycoon I see?!
 
Anyway, does anyone have anything else to recommend? I was thinking of getting squirrelmail to replace OWA at some point, and as I said I do fancy taking on Snort.

---

### Post by nothingspecial on 2010-12-16
> **nahallac said:**
>  I think the fact that I am a grumpy sod like the blogger has something to do with it.
 


:shock:  :-$

That "grumpy sod" is an admin on this forum.........

.....I don`t think he`ll mind though, depends how grumpy he`s feeling I suppose.

---

### Post by nahallac on 2010-12-16
I use the phrase as a compliment, believe me! Being cynical is a wonderful thing!

---

### Post by mickwombat on 2010-12-16
For a pure server you shouldn't need to install a gui.  A great application that I use is Webmin.

It's not in the repositories so you'll have to install it by hand and maybe a few other dependencies.  It's a nice way to manage a server by means of a webpage.  I still find applying config by hand the best way, but webmin is a good way to see 'how' it is applied.

Putty is the best way to log in and you can change the amount of line of scrollback as well.

If a command has particularly lengthy output, then put ```
| more
``` after the command.

Good luck

;)

---

### Post by nahallac on 2010-12-16
Yes, thank you for that - piping to more is great. I am also going to try using grep in a sensible way as I can see it being very useful.
 
I will give webmin a go if it gives insight into how config hangs together. Thanks again.

---

### Post by nahallac on 2010-12-16
Would I be right that anything with the prefix ./ is a type of executable?

---

### Post by nothingspecial on 2010-12-16
No, ./ means here, as in where you are in the file system.

So if you are in your $HOME then ./ means /home/youruser

You run an executable by prefixing it your self with ./

---

### Post by JKyleOKC on 2010-12-16
> **nahallac said:**
> Would I be right that anything with the prefix ./ is a type of executable?You may already be aware of this, but every directory in a Linux file system contains two normally-hidden entries: . and ..

The first of them is a pointer (or link, if you prefer) to the current directory itself, and the second is to the parent directory. They simplify browsing from the command line, allowing you to move up the directory tree without having to remember the full path spec of the parent directory.

What makes these entries "hidden" is the convention that any file or directory name that starts with a period is hidden. You can view them with the command "ls -a" and you may be amazed at the number of such files and directories within your home directory.

The reason that "./" is used so often when running executable files is that unlike Microsoft's offerings, Linux distributions normally do NOT search the current directory first when parsing a potential command. They follow the paths listed in the environment variable "PATH" (you can "echo $PATH" to view it), only. By prefixing the file name with "./" you tell the parser to "look here for the file" instead of using PATH.

Hope this helps! You'll find that the CLI is much faster for many tasks, but like some others have said, having a GUI is also convenient and you can use the terminal emulator there to do CLI actions thus having the best of both worlds...

---

### Post by nahallac on 2010-12-17
Thank you JKyleOKC and nothingspecial for the explanation. I guess coming from a Windows background I am used to CDing to a directory and having it as a 'working' directory in the sense that I can run stuff from it. I wasn't aware that . acted as a pointer much as .. does, although I probably should have sussed it!
 
Thanks all for your help here so far, I am determined that I will have a significant Linux presence at home very soon. The Postfix config is done, so I think next I am going to attack squirrelmail. I might start looking at some Perl basics, anyone know of any good tutorials (considering I am very naive when it even comes to how to write scripts in general)?

---

### Post by napoleon3665 on 2010-12-17
so...u wanna learn command line linux? 

here u go   [http://www.archlinux.org/](http://www.archlinux.org/)

install that distro....and ur done.

---

### Post by nahallac on 2010-12-17
Ok... why so? Anyway, I'm not looking to hop from distro to distro at first. I'll get the basics in place and feel comfortable getting around using the CLI, then after that I'm sure I can experiment a bit.

---

### Post by napoleon3665 on 2010-12-17
lol im just saying, you are eventually going to end up with either arch or gentoo...u might as well start to get familiar now with it...

---

### Post by nahallac on 2010-12-17
Ok, I'll see if I can get an Arch VM chucked in somewhere and have a play! Why is it inevitable I'll end up with Arch or Gentoo, do they do things that other distros can't? How do they differ from using Ubuntu CLI wise?

---

### Post by napoleon3665 on 2010-12-17
well the reason i say that u will end up with that is because arch and gentoo you can build from the ground up, for example, you have to install sudo...i think arch or gentoo will give you an idea of what cli is really like.

---

### Post by nothingspecial on 2010-12-17
You can do all that from ubuntu minimal.

However, I participated in a similar thread recently. Rather than repost, here`s the link

[http://ubuntuforums.org/showthread.php?t=1635564](http://ubuntuforums.org/showthread.php?t=1635564)

---

### Post by nahallac on 2010-12-17
> **nothingspecial said:**
>  
However, I participated in a similar thread recently. Rather than repost, here`s the link
 
[http://ubuntuforums.org/showthread.php?t=1635564](http://ubuntuforums.org/showthread.php?t=1635564)
 
Ah! That's just the type of thread I was after. Thank you...

---

### Post by Baked- on 2010-12-17
+1 for using gentoo.

Just going through the install successfully will help you learn the inner-workings of the system much better.

---

### Post by bodhi.zazen on 2010-12-17
> **napoleon3665 said:**
> well the reason i say that u will end up with that is because arch and gentoo you can build from the ground up, for example, you have to install sudo...i think arch or gentoo will give you an idea of what cli is really like.

Arch and gentoo are for whimps, [LFS](http://www.linuxfromscratch.org/)

---

### Post by nahallac on 2010-12-17
Linux from scratch looks scary. I will bear it in mind though, I'll have a go at taking it on somewhere in the future. I like it!

---

### Post by nothingspecial on 2010-12-17
I wouldn`t bother if I were you.
Do what you will though, this is linux after all.:D

---

### Post by bodhi.zazen on 2010-12-17
> **nahallac said:**
> Linux from scratch looks scary. I will bear it in mind though, I'll have a go at taking it on somewhere in the future. I like it!

My point is that there is nothing "special" or "advanced" about Arch or Gentoo. As you gain experience you may prefer one distro over another, and they all have advantages and disadvantages.

You can make most distros into what you want, with Ubuntu / Debian do a minimal install and build up.

If you want to compile everything, you can, some distros are easier (Gentoo, Slackware, Arch) then others, but compiling from source can get old as well (as is resolving dependencies).

IMO, under the hood, these distros have more similarities then differences and if you can read man pages you can run most any distro.

---

### Post by Hippytaff on 2010-12-17
> 
Arch and gentoo are for whimps

really...I just downloaded Arch netinst on the back of the advice in this thread ;-)

I really did :-)

---

### Post by nothingspecial on 2010-12-17
> **bodhi.zazen said:**
> My point is that there is nothing "special" or "advanced"

:-k

---

### Post by nahallac on 2010-12-17
> **nothingspecial said:**
> I wouldn`t bother if I were you.
Do what you will though, this is linux after all.:D
 
I just like challenging myself. I can't see it being something I have a go at in the near future, but it will be one of those projects that feels rewarding at the end of it. I am only at the very beginning of my Linux use, I know it's going to take a while to suss it.

---

### Post by Hippytaff on 2010-12-17
> **nahallac said:**
> I just like challenging myself. I can't see it being something I have a go at in the near future, but it will be one of those projects that feels rewarding at the end of it. I am only at the very beginning of my Linux use, I know it's going to take a while to suss it.

Explore and enjoy the freedome to explore...lots of people think there are only 2 operating systems ;-)

---

### Post by bodhi.zazen on 2010-12-17
> **Hippytaff said:**
> really...I just downloaded Arch netinst on the back of the advice in this thread ;-)

I really did :-)

It was a joke, sheeesh =)

---

### Post by albert s on 2010-12-17
> **Hippytaff said:**
> Explore and enjoy the freedome to explore...lots of people think there are only 2 operating systems ;-)


there are,
mine,
and the one everyone else uses that never seems to use the same commands that mine needs to work properly.  ;)

---

### Post by JKyleOKC on 2010-12-17
> **nahallac said:**
> I just like challenging myself. I can't see it being something I have a go at in the near future, but it will be one of those projects that feels rewarding at the end of it. I am only at the very beginning of my Linux use, I know it's going to take a while to suss it.You'll have lots of fun along the way.

I've considered myself a toolmaker ever since getting started on mainframes many years ago. Today's open source movement makes it possible for anyone who's willing to invest the time learning to be able to modify existing tools or create new ones to meet one's own needs.

I'd recommend, though, that you start learning the art/craft of making tools by learning how to do "bash scripts." Much of any modern distribution consists of such scripts, written in the bash language -- which is the native tongue of the Ubuntu CLI, so you're already becoming familiar with it. You can browse through the files in the /etc directory and examine any of them that show an "x" in the listing you get from "ls -l /etc | less" (which indicates that they are executeable). That command is to get a "long" listing that shows the permissions, owner, and group for each file, and piping it to the "less" command allows you to browse through the list one screen at a time since it will be far too long to all fit into a single screen. To examine a file, use "nano xxx" where xxx is replaced by the full file name; if it shows up as ordinary text it's probably a bash script.

O'Reilly has some excellent books on learning the bash language that will keep you busy for a few weeks reading the details. You don't need to try to memorize them, but knowing the most common usages will definitely make your other learning easier. For example, "echo PATH" will simply display the word "PATH" and then return to the prompt, but "echo $PATH" will display the content of the PATH environment variable. The leading "$" is actually a bash operator meaning "evaluate the rest of this argument and display the result."

And above all, don't be shy about asking questions here. All of us have been down this road to some extent along the way and the only "dumb questions" are those that aren't asked at all...

---

### Post by Hippytaff on 2010-12-17
> **bodhi.zazen said:**
> It was a joke, sheeesh =)

I know...my god...you guys ;-)

I also downloaded Slitaz

---

### Post by tfultz33 on 2010-12-18
> **bodhi.zazen said:**
> 1. Learn to read the man pages.

2. Try this site:

[http://linuxcommand.org/](http://linuxcommand.org/)

At least the first few sections.

Yes! You will thank yourself over and over for learning to read the man pages.

---

### Post by nahallac on 2010-12-18
> **JKyleOKC said:**
>  
I'd recommend, though, that you start learning the art/craft of making tools by learning how to do "bash scripts." Much of any modern distribution consists of such scripts, written in the bash language -- which is the native tongue of the Ubuntu CLI, so you're already becoming familiar with it. You can browse through the files in the /etc directory and examine any of them that show an "x" in the listing you get from "ls -l /etc | less" (which indicates that they are executeable). That command is to get a "long" listing that shows the permissions, owner, and group for each file, and piping it to the "less" command allows you to browse through the list one screen at a time since it will be far too long to all fit into a single screen. To examine a file, use "nano xxx" where xxx is replaced by the full file name; if it shows up as ordinary text it's probably a bash script.
 
Yes, I absolutely plan to start scripting. It's something I have never set time aside to learn, but I'm getting to the stage now (even with MS products) where I feel very limited by my inability to string anything together!
 
> **JKyleOKC said:**
>  
And above all, don't be shy about asking questions here. All of us have been down this road to some extent along the way and the only "dumb questions" are those that aren't asked at all...
 
Thank you very much for your posts so far, they have been very much appreciated. Not just yours, but everyone's. I have a lot to work on now thanks to the help I've had here!

---

