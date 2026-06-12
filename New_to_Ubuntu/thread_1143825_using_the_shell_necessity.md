---
title: "using the shell: necessity?"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by ppb7 on 2009-04-30
i read recently that > even on the most user-friendly Linux distributions, the command line is still required.Now, if i decide to switch to Linux it will only be because I have been persuaded that ALL its features make it an OS superior to Windows.
So, what's the advantage of using the command line:?:? Why should I learn shell commands? I am not a newbie at programming as i have played with PHP, ASP and Visual Basic (don't ask me to teach you, though :!::smile:)

---

### Post by halitech on 2009-04-30
in day to day use, no you won't need to use the command line. If you have issues and come here to get help, you will probably get commands to type in as opposed to what programs to open as it is easier to give a command then explain what to open and what to click on.

---

### Post by Menschenfresser on 2009-04-30
The thing is that not all things can be configured through a GUI. However many of them would fall in the "advanced" category (starting/stopping your database, adding something to cron,etc.).

You can also argue it is faster (if you already know!) to type command A than to go to menu a > program b > option c

And another thing is that you can ssh into the machine and do/fix what you wanted to do (useful when troubleshooting another machine.

---

### Post by Simian Man on 2009-04-30
It's never necessary unless you have crap to fix.  Unfortunately because many hardware manufacturers and software developers don't support Linux, there often times *is* crap to fix.  And one reason Linux has small market share - and thus little commercial support - is because users must sometimes use the command line to fix crap.  It's a vicious cycle :(.  But in an ideal world where all your hardware works and you don't need to run non-native software, you would not need the command line.

That said the command line will always be more powerful for repetitive tasks and for power users - so it will never go away completely even in the ideal world.

Another benefit of the command line is that it is independent of desktop software and - for the most part - distribution.  If you say "Go to System->Preferences->Mouse" then you have tied your instructions to Gnome so users of KDE and Xfce won't be able to use them as is.  It will also confuse people on other Gnome distros, like Fedora, that lay out the menus a little differently.

---

### Post by JKyleOKC on 2009-04-30
> **ppb7 said:**
> i read recently that Now, if i decide to switch to Linux it will only be because I have been persuaded that ALL its features make it an OS superior to Windows.
So, what's the advantage of using the command line:?:? Why should I learn shell commands?
I'd quibble with that word "required" since with adequate patience, you can do most anything through a GUI that you can do from the command line.

However, doing so just might require you to first write a few scripts or programs, and learn a GUI framework such as GTK -- where the same task might need only a single command entered at the prompt.

Here's an example: I have one box configured as a print server for the other five on my home LAN. Sometimes when attempting to print a very large (500 MB of desktop publishing output) file, the printer itself will time out leaving the print driver stuck in a near-infinite loop. The cure is to kill the print driver program.

From the CLI, it takes only two commands to do so. First I use "ps ax |grep hp" to find the process ID of the stuck process, then "sudo kill xxxx" where the xxxx is actually the PID found by the first. That's all it takes.

From a GUI, I would first have to force the stuck process into a window on screen, which would mean writing a program to do so, then launch "xkill" from a menu, putting the xkill icon on the stuck process' window, and clicking. Much more complex! Actually most of us would simply reboot the print server, which could disrupt other printing jobs and would definitely take much longer...

So while I don't think using the CLI is "required" I do believe it's often much more efficient. In daily operation, most of my work is done through the GUI but the CLI is always there for use if needed...

---

### Post by DGortze380 on 2009-04-30
> **ppb7 said:**
> i read recently that Now, if i decide to switch to Linux it will only be because I have been persuaded that ALL its features make it an OS superior to Windows.
So, what's the advantage of using the command line:?:? Why should I learn shell commands? I am not a newbie at programming as i have played with PHP, ASP and Visual Basic (don't ask me to teach you, though :!::smile:)

This is a simplistic explanation, but it's the way that made most sense to me when I was starting.

In Windows, the GUI (Graphical User Interface) IS the operating system. They're permanently intertwined. The Command Line in Windows is really an emulator, it cause things to happen in the GUI, and has a limited command set.

In Linux, the CLI (Command Line Interface) IS the operating system. The GUI lays over the top, and things you do in the GUI cause changes in the CLI and config files. The command line is important because it literally gives you the ability to control and modify your entire system through a very complete command set.

---

### Post by Rinzwind on 2009-04-30
> **ppb7 said:**
> i read recently that Now, if i decide to switch to Linux it will only be because I have been persuaded that ALL its features make it an OS superior to Windows.
So, what's the advantage of using the command line:?:? Why should I learn shell commands? I am not a newbie at programming as i have played with PHP, ASP and Visual Basic (don't ask me to teach you, though :!::smile:)

Not everyone has the same menu. And the command line instruction will still be the same. 

A command line instruction can be copied to the command line (duh ;) ) or even added to a script so you can repeat it. I have a script with mount points to connect to my other machine.

---

### Post by Celauran on 2009-04-30
> **ppb7 said:**
> i read recently that Now, if i decide to switch to Linux it will only be because I have been persuaded that ALL its features make it an OS superior to Windows.
So, what's the advantage of using the command line:?:? Why should I learn shell commands? I am not a newbie at programming as i have played with PHP, ASP and Visual Basic (don't ask me to teach you, though :!::smile:)

You phrase your question as though there is something inherently wrong with the command line. There isn't. Sometimes it's just the right tool for the job.

---

### Post by kpkeerthi on 2009-04-30
Its easier to copy paste a command from someone else's post offering you a help instead of clicking on GUI controls 100 times.

---

### Post by dawynn on 2009-04-30
It is not uncommon, when running a command from the menu, to see a blip of a splash screen (or maybe not even that much) and the program silently dies.  At least Windows usually prints out a GUI error message screen when something dies unexpectedly.

In those instances, the most helpful way to figure out what happened is... use the command line!  Running the same program from the command line will often provide the error messages that Linux failed to put into a nice viewable error screen.

Another advantage of the command line -- if something gets really hosed with the GUI, or some resource is just *really* clogging memory, you can usually get to a virtual terminal session (ctrl-alt-f1 through c-a-f6) and play around a bit.  I have saved myself a lot of reboot time just by going to a virtual terminal and typing 'sudo slay {myuserid}' (that is, kill my session and let me login again).

---

### Post by Niniel on 2009-04-30
> **Celauran said:**
> You phrase your question as though there is something inherently wrong with the command line. There isn't. Sometimes it's just the right tool for the job.
Even MS is making Windows more CLI-friendly - behold their newest offering, the power shell (I think that's what it's called). 
Of course you could always work with a command line in Windows, as well, many people just don't realize it. But you see that very nicely in many corporate networks where they have login scripts that display a non-interactive terminal/DOS-prompt window when you sign in.

---

### Post by cerz on 2009-04-30
I've got a friend who introduced me to Ubuntu.  He **won't** do tasks that require use of the command line, even though he knows more about Ubuntu than myself (I use the command line all the time...).
Most of the important command line tools have a GUI you can download through Synaptic.   Just search for the command line name, and a package containing "GUI utilies for <command>" or "Graphical wrapper for <command>" will often pop up.

Cheers

---

### Post by lykwydchykyn on 2009-04-30
Follow me on this a second:
Point 1:
 - Linux is primarily running FOSS software that is in "open development".  This means things are released publicly from the very earliest moments of development.
 - By contrast, commercial proprietary software is developed behind a curtain, and only unveiled to the public when it is deemed completely ready.

Point 2:
 - Functionality in the FOSS world is usually built "from the ground up".  It usually starts with a software library, then there is a command-line utility made, and then eventually a graphical front-end.  Often these three things are developed by different people or companies.

Conclusion:
 - There will always be functionality, features, and compatibility "on the horizon" that one can only get by digging down beneath the graphical surface of your Linux distro.  If you don't need this stuff, you don't have to dig.  

But the point is, when you "have to" use the command line, or compile software, or do something else "beneath the surface" to get something to work in Linux, you have to remind yourself that if Linux were a closed commercial product, you would just have to wait for the next version or two to get the functionality.  It's not what you "have to do", it's what you "can do" because you're working with free, open source software.

---

### Post by ByteJuggler on 2009-04-30
> **ppb7 said:**
> i read recently that Now, if i decide to switch to Linux it will only be because I have been persuaded that ALL its features make it an OS superior to Windows.
So, what's the advantage of using the command line:?:? Why should I learn shell commands? I am not a newbie at programming as i have played with PHP, ASP and Visual Basic (don't ask me to teach you, though :!::smile:)

IMHO: 

You should not need to learn shell commands generally speaking.  However, doing so is highly recommended/advantageous.  Without wanting to ignite another GUI vs. command line flamewar, let me just observe that GUI's are designed with certain use cases in mind, and that's it.  They can't be combined in creative ways with other GUI's, they cannot exceed their original designer's intent (what he anticipated the GUI will be used for.)  Thy are what they are and that's it.  

The shell command line on the other hand is not like this.  Shell/text based commands are also designed with a certain usage/intent in mind by their creators, however by nature they are flexible/maleable by being combinable with other commands in creative ways which typically would not have been anticipated by their creators.  In this way, the command line is a superior environment for instructing and using your computer, for at least some tasks, due to the capacity of command line tools to exceed their original design intent, so to speak.  Evem so this power comes at a price, which is that it takes a bit more effort to get into and that they're perceived as less user friendly.  

In the end there's room for both GUI's and the command line.  GUI's are good for "happy path" scenarios and getting common tasks done (relatively) quickly.  The command line is good to fill in when GUI's run out of steam or when a GUI is not available for whatever reason.

---

### Post by Niniel on 2009-04-30
> **lykwydchykyn said:**
> But the point is, when you "have to" use the command line, or compile software, or do something else "beneath the surface" to get something to work in Linux, you have to remind yourself that if Linux were a closed commercial product, you would just have to wait for the next version or two to get the functionality.  It's not what you "have to do", it's what you "can do" because you're working with free, open source software.
That has nothing to do with Windows vs. Linux. There is plenty of free and open software available for Windows as well.

---

### Post by passonno on 2009-04-30
> **lykwydchykyn said:**
> 
But the point is, when you "have to" use the command line, or compile software, or do something else "beneath the surface" to get something to work in Linux, you have to remind yourself that if Linux were a closed commercial product, you would just have to wait for the next version or two to get the functionality.  It's not what you "have to do", ***it's what you "can do"*** because you're working with free, open source software.

Exactly the right answer!!

---

### Post by SunnyRabbiera on 2009-04-30
Using the shell these days is very optional, in fact I have not even touched the shell in months.
But using CLI commands is helpful when doing certain things, and actually some things are easier to do in a CLI.
The coolest thing about the linux terminal though is that you can copy and paste commands given to you by the members of the linux community.
so manually typing commands is not really needed, unless something seriously goes wrong.

---

### Post by steviefordi on 2009-04-30
ppb7, why do you think the command line makes Linux inferior to Windows? This is not the case at all. You need to learn to love the command line in order to see it's advantages.

You say you have some programming experience, it'll be worth you taking some time to follow the tutorials over at:

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

You can follow most of it using [cygwin]("http://www.cygwin.com/") (a *nix environment on a Windows machine).

You'll soon realise it's often the GUI that's clunky and restrictive, and the command line that's slick and powerful.

---

### Post by SunnyRabbiera on 2009-04-30
> **steviefordi said:**
> ppb7, why do you think the command line makes Linux inferior to Windows? This is not the case at all. You need to learn to love the command line in order to see it's advantages.

You say you have some programming experience, it'll be worth you taking some time to follow the tutorials over at:

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

You can follow most of it using [cygwin]("http://www.cygwin.com/") (a *nix environment on a Windows machine).

You'll soon realise it's often the GUI that's clunky and restrictive, and the command line that's slick and powerful.


But one does not have to be a command line guru to use linux.
For me I see why we do need more GUI's in linux, for beginners CLI is very intimidating and also very complex looking.
Of course there is the vast population of linux users that want us all to just shut up and use CLI only, I think both the GUI and CLI can be beneficial.

---

### Post by Celauran on 2009-04-30
> **SunnyRabbiera said:**
> But one does not have to be a command line guru to use linux.
For me I see why we do need more GUI's in linux, for beginners CLI is very intimidating and also very complex looking.
Of course there is the vast population of linux users that want us all to just shut up and use CLI only, I think both the GUI and CLI can be beneficial.

Of course they're both beneficial. CLI v. GUI is a silly argument; the two are not mutually exclusive.

---

### Post by SunnyRabbiera on 2009-04-30
> **Celauran said:**
> Of course they're both beneficial. CLI v. GUI is a silly argument; the two are not mutually exclusive.

Indeed, though I am on the party there needs to be more GUI tools for every aspect of the OS.
One thing I really with Ubuntu had was a master control center, to configure major monitor settings, set up repositories, manage wireless all under one GUI similar to Mandrake control center or YAST.

---

### Post by steviefordi on 2009-04-30
> CLI v. GUI is a silly argument; the two are not mutually exclusive.

I wasn't suggesting they were. I think an appreciation of the command line is a good thing and, if a choice exists, the user can decide which method of performing a task is preferable for them.

> for beginners CLI is very intimidating and also very complex looking
I suggested the tutorial to the OP as they say they have some programming experience. I agree with what you say and would no way advise it in the early days to a non-tech person.

---

### Post by benj1 on 2009-04-30
in my experience i don't need to use the terminal, but i choose to.

i think part of the problem is the fact that in nearly all linux forums people say you don't need to use the terminal, then give you instructions on how to use it. although it is for a very good reason

System-->administration-->synaptic package manager, enter password, click search, enter program to download, scroll down to program, click mark for installation, click apply.
(and thats just for 1 version of gnome)

versus

```
sudo apt-get install program
*password*
``` 

which is easier?

---

### Post by Niniel on 2009-04-30
Lol, Synaptic of course because there you can get some description of what the program does, at least in many cases. :P

---

### Post by wmcbrine on 2009-04-30
The command line is a beautiful thing. It's nothing to be feared. Especially for a programmer!

---

### Post by SunnyRabbiera on 2009-04-30
> **steviefordi said:**
> I wasn't suggesting they were. I think an appreciation of the command line is a good thing and, if a choice exists, the user can decide which method of performing a task is preferable for them.


I suggested the tutorial to the OP as they say they have some programming experience. I agree with what you say and would no way advise it in the early days to a non-tech person.

well even those with programming experience might find CLI unusual.

---

### Post by benj1 on 2009-04-30
> **Niniel said:**
> Lol, Synaptic of course because there you can get some description of what the program does, at least in many cases. :P

well my example was for a known program, you aren't likely in a forum to tell some one to install a program you don't know the name of

even so

```
apt-cache search *term*
apt-cache show *program*
apt-get install *program*
```

is a lot easier to type, and more portable than my synaptic example

---

### Post by halitech on 2009-04-30
> **benj1 said:**
> in my experience i don't need to use the terminal, but i choose to.

i think part of the problem is the fact that in nearly all linux forums people say you don't need to use the terminal, then give you instructions on how to use it. although it is for a very good reason

System-->administration-->synaptic package manager, enter password, click search, enter program to download, scroll down to program, click mark for installation, click apply.
(and thats just for 1 version of gnome)

versus

```
sudo apt-get install program
*password*
``` 

which is easier?

> **Niniel said:**
> Lol, Synaptic of course because there you can get some description of what the program does, at least in many cases. :P

both do the same thing but if you already know the name of the program you are installing then it would stand to reason that you know what it does, otherwise, why are you installing it? On the other hand, if you know you want a program to send email for example but don't know which one you want, synaptic would be better as you can search for "mail" and select the one you decide you want.

---

### Post by benj1 on 2009-04-30
sorry i think im being misunderstood.

i was just talking about advice given in the forums. my point is that we say that you dont need to use the command line, but if people ask for help, 90% of the time the solution is a command line, not gui solution, because from the helpers point of view it is easier to give the helpee a terminal command to copy + paste, and i was backing up this up with an example.

---

### Post by lykwydchykyn on 2009-04-30
> **Niniel said:**
> That has nothing to do with Windows vs. Linux. There is plenty of free and open software available for Windows as well.

Sure there is, but with Windows the system itself is not predominantly (or at all) composed of free software.  I guess I'm not really talking about the 'application level', but more on the level of things like desktop environment, utilities, hardware support, etc.

A good example is the firewall on Linux.  Netfilter/iptables is incredibly flexible and powerful, but not every graphical front-end for it exposes all the features, either because the aim is to make something simple, or because they just haven't been able to implement everything yet.  If you really need advanced firewall functionality, you can learn iptables and do just about anything you'd want to do with a firewall.  If you just need to block a few ports, then you can use a GUI.

Contrast with the Windows firewall:  Whatever is in the GUI is what you've got.  If it's not there, you can't do it.  Who knows what the Windows firewall engine is really capable of?

---

### Post by Niniel on 2009-04-30
DE, utilities... free alternatives *are* available (I'm a user of Blackbox for Windows myself). 
As for firewalls, there are a number of free ones out there that can be configured to your liking. Some are very simple to use, and some are not. So what if they are not part of Windows. 
It's really funny, people complain when MS includes software with their OS, like a browser or a media player, and they also complain when they don't or only ship basic tools, like this firewall. 
Really, this was a very poor example. :)

---

### Post by lykwydchykyn on 2009-04-30
> **Niniel said:**
> DE, utilities... free alternatives *are* available (I'm a user of Blackbox for Windows myself). 
As for firewalls, there are a number of free ones out there that can be configured to your liking. Some are very simple to use, and some are not. So what if they are not part of Windows. 
It's really funny, people complain when MS includes software with their OS, like a browser or a media player, and they also complain when they don't or only ship basic tools, like this firewall. 
Really, this was a very poor example. :)

I'm not complaining about anything.  Why are you making this another Windows vs Linux thing?

I'm just pointing out that we have a system that is almost entirely FOSS.  With FOSS you have access to stuff from the alpha stages on, and it takes a little more skill to get the very newest stuff.

If you use FOSS software on Windows, then yes it holds true there as well for the FOSS software you use.  Sorry to generalize, but most people who are comparing how much you "have to" use the command line or other "expert user" things on Linux are not comparing it to installing FOSS on Windows.

If you were to use a lot of commercial, proprietary software on top of the Linux kernel, then what I said would not be true.  But that's beside the point, because most people don't do that.

---

### Post by nandemonai on 2009-04-30
> **ppb7 said:**
> i read recently that Now, if i decide to switch to Linux it will only be because I have been persuaded that ALL its features make it an OS superior to Windows.
So, what's the advantage of using the command line:?:? Why should I learn shell commands? I am not a newbie at programming as i have played with PHP, ASP and Visual Basic (don't ask me to teach you, though :!::smile:)

If those features include running propriety software, gaming, having 100% hardware support, expecting support as if you payed for it then no, Linux is not for you.

Then again, if you're after something more secure, flexible, open and free, more intuitive desktops etc etc etc then sure check Linux out.

This whole 'SWITCH' thing is pointless in my opinion. You're not restricted to running one Operating System in your life.

I use Linux, Windows, MacOS, Netware and a range of others for specific uses.

Why limit yourself to one Operating System in the first place? True, I prefer Linux to most anything else but that doesn't mean when I wanna do some gaming I won't boot into Windows or want to do some multimedia work that I'll hop on a mac.

Use whatever you like. This whole zealot 'I will use only one Operating System and be damned all the rest!' attitude only harms yourself in terms of being able to choose what you use and when.

---

### Post by camper365 on 2009-04-30
It was a very long time before I used the command-line.
I was able to do everything with the graphics, and a lot of time I still do.
However, a lot of times, it will be easier to use the command-line than the graphics.
For example:
You need to install a program.
Instead of going to System > Synaptic Package Manager
and waiting for it to load, then find the package, select it, and apply changes, why not go to a terminal and type:
```
sudo aptitude install package
```Much easier. Especially if you use a keyboard shortcut to start a terminal (I use Alt+Shift+F2 since the run dialog is Alt+F2).

I can probably give a very long demonstration of Ubuntu and show what it can do, and not show a terminal at all. Now, if you were to use Gentoo or Slackware, you will have to use a terminal.

Basically, everything can be done with the graphics

---

### Post by Niniel on 2009-04-30
> **lykwydchykyn said:**
> Why are you making this another Windows vs Linux thing?
Lol, you are the one who's arguing Windows (proprietary, gui, no obvious/true cli = bad) vs. Linux (free & open, cli = good), not me. I'm simply pointing out to you that the freeness of the OS as such has nothing to do with anything we're talking about here. 
Which was originally command line interfaces and why they might be good and useful even in an otherwise graphical world.

> **nandemonai said:**
> Then again, if you're after something more secure, flexible, open and free, more intuitive desktops etc etc etc then sure check Linux out.
This is the same junk. Apart from the inherent security issues, if you really want to, you can be (almost) as flexible, open and free with Windows as your OS. The applications and even the DEs are not the OS.

---

### Post by markharding557 on 2009-04-30
i think it is very wise to gain a basic grasp of using cl,i,m glad i did when the video screwed up when installing drivers a while ago'if i didn't know how to use nano i would have been stuck

---

### Post by lykwydchykyn on 2009-04-30
> **Niniel said:**
> Lol, you are the one who's arguing Windows (proprietary, gui, no obvious/true cli = bad) vs. Linux (free & open, cli = good), not me. I'm simply pointing out to you that the freeness of the OS as such has nothing to do with anything we're talking about here. 
Which was originally command line interfaces and why they might be good and useful even in an otherwise graphical world.


I believe you missed the point of my post, because I had no intention of arguing about Windows.  But I am equally sure there will be no convincing you of this, because this is the internet.

I was only making the point that due to open development, things are always available to us that are not available with closed development.  That holds true for openly-developed software on any platform.

These things usually start out as "primitive" CLI components and only later become graphical.  So the idea that some people have ("Do you **still** have to use the command line on Linux?") that Linux will someday evolve out of using the CLI is misguided, because we will always have available features that can only be had via the console (or compiling, or fill-in-the-blank non-newbie-friendly process) because the GUI or the slick interface hasn't caught up yet.

The freeness (in the freedom sense) of the SOFTWARE (not necessarily the OS) involved does have something to do with it, because we only have access to those new features by way of open development.  Thus, if you use open software on Windows, you get the same thing.

But since we are generalizing all over this thread, I guess I took the liberty of generalizing that "linux" means a stack of predominantly FOSS, whereas "Windows" means a stack of predominantly commercial/proprietary software.  Maybe that's what you are taking such exception to.  I don't know, really.

---

### Post by Skrynesaver on 2009-04-30
While I agree with you unreservedly in that the more methods you know the easier it is to choose the appropriate solution for the problem at hand, I have to argue that a CLI allows greater productivity than any other approach, except perhaps Perl (personal bias).

You don't **need** to know the shell to use Linux, in fact the Ubuntu project has produced many GUI tools which allow simple configuration and administration of a Linux box, once you know your way around the shell however you never look back.  The efficiency it provides is unbeatable, you can do things in a shell that are impossible in any GUI.

While Ubuntu allows a new Linux user to learn Linux without trawling through the man pages, I would advise every user, particularily one with familiarity with progamming, to get with the shell as it will improve your efficiency in computer use.

---

### Post by VCoolio on 2009-04-30
Ok, I'm sure this already has been said in this thread, +1 for me then: the shell is not 'necessary' when you have your system up and running. It's just the easiest way to explain how to do things. And no, I'm not particularly geeky and still I like the shell because you command and it is done. No searching for the one little box to tick, just command. Nothing scary. Using interfaces does the same, only with the mouse instead of keyboard.

---

### Post by llamabr on 2009-04-30
I don't know how we got so far off track of the OP.

Anyway, something else that may not have been mentioned is that learning to bash script really unlocks the power of data and text manipulation, along with one of the main strengths, IMO, of piping the output of one program into another.

probably an excel macro could be written to take an array of data, remove the second field of every third entry, sort them alphabetically, and send them, via email, to my web server.  But I have no idea how it would work.  Bash does it in one line.  Perl and python, too.

it also makes any very tedious task, like adding a suffix to a million file names, which would take hours ina  gui like openoffice, and completes it in a second.

Most things you can do fine, but data and text manipulation, particularly for anything tedious and repetative, really makes it worth while.

---

### Post by steviefordi on 2009-05-01
> data and text manipulation, particularly for anything tedious and repetative, really makes it worth while

I couldn't agree more. I still class myself a bit of a newbie to the *nix world, but I'm becoming a CLJ. I installed Linux at home and learning how to use the CLI has lead me to do my job (in which I use Windows) much better.

I recently had to trawl gigs and gigs of log files for just 150 lines of data that was scattered sporadically throughout. I installed cygwin and used 'grep', it was the perfect tool. I don't think I'd have found what I was looking for by Christmas if I'd have been using a GUI text editors search facility.

'sed' and 'regexp' rule too. It seems a bit geeky and sad but I'm starting to wonder how I survived without this stuff!

The OP should at least try the command line before dismissing it as "**Inferior**". Sometimes it just has the right tools for the job!

---

### Post by nandemonai on 2009-05-01
> **Niniel said:**
> This is the same junk. Apart from the inherent security issues, if you really want to, you can be (almost) as flexible, open and free with Windows as your OS. The applications and even the DEs are not the OS.

So I'm free to modify the source and re-release it to my liking in a closed OS like Win/OSX? Recompile an application to my liking?

I can perform advanced functions in the Windows CLI such as equivalents to grep / sed?

The list goes on. My point remains valid. I was referring to the OPs original statement:

> Now, if i decide to switch to Linux it will only be because I have been persuaded that ALL its features make it an OS superior to Windows.

To which my reply was, why need to 'switch' in the first place? You can use as many operating systems as you like, for whatever tasks you need to achieve.

I'm not here to convince anyone of anything. Do what you like and use what you like.

I was merely stating my opinion as to why the OP might want to try out Linux.

---

### Post by ppb7 on 2009-05-04
> **steviefordi said:**
> ppb7, why do you think the command line makes Linux inferior to Windows?.
You are misinterpreting me. My computer is a fairly old (about 7 years old) XP machine, but i am stuck with it so I want to switch to Linux because, from what I've seen it's very fast (at the moment I only need 15' for my computer to be fully functional:!::!:). I am only trying to convince other family members (and myself sometimes) that this is the right move. i guess i have to be able to answer all the "but,..." that could be levelled at me. I therefore need to be aware of all the functionality offered by Linux.
For one thing, I will never be able to convince them that Open Office is as good as, if not better than, MS Office (laziness, fear of the unknown (on their part), etc...)

---

### Post by ppb7 on 2009-05-04
> **wmcbrine said:**
> The command line is a beautiful thing. It's nothing to be feared. Especially for a programmer!
I am not a programmer, but a language teacher and programming languages are...well...languages.
Anyway, i am extremely glad to have started such an interesting thread. I hope that this will have convinced newbies of the usefulness of the CLI as an essential part of a user-friendly GUI operating system.
As for all that remains is that, when i do need to use the terminal, I will easily find the commands i need...:!: I am sure i can get that from this forum.:grin::wink:

---

### Post by blueridgedog on 2009-05-04
> **ppb7 said:**
>  i am extremely glad to have started such an interesting thread

Well...some feed on CLI vs GUI sort of debates.  In short, the command line is there when you want it and it will enable you to do things faster and more efficiently, but should not be required unless you are getting assistance with a problem.  

I wish you luck with Ubuntu and in working out the transition with your family.

---

### Post by steviefordi on 2009-05-05
> **ppb7 said:**
> i guess i have to be able to answer all the "but,..." that could be levelled at me.

I think you are worrying too much. You need to try Ubuntu (or another distro if you choose) and set up a dual boot with Windows on your machine. You then have your 'safety net' to return to if you wish, and you can speak from experience when 'selling' an alternative OS to your family.

The Windows vs Linux debate comes down to a couple of things for me. (And I stress my opinion will probably differ from the next man)

Choose Windows if...
1) You're a hardcore gamer.
2) You use an ipod touch or any other hardware not supported out of the box by Linux.

Choose Linux if...
1) You want the security of knowing you have no virus or spyware on your system watching what you're doing.
2) You want to avoid performance degredation, ie) your 15 mins start-up time before your PC is functional.

And remember nandemonai what said...

> You can use as many operating systems as you like, for whatever tasks you need to achieve.

On a side note, if you want a humurous yet intelligent look at the OS debate, check out:
[http://artlung.com/smorgasborg/C_R_Y_P_T_O_N_O_M_I_C_O_N.shtml](http://artlung.com/smorgasborg/C_R_Y_P_T_O_N_O_M_I_C_O_N.shtml)
and pay particular attention to the section headed - MGBs, TANKS, AND BATMOBILES. It says more about which OS to choose than I ever could!

---

### Post by Niniel on 2009-05-05
Holy cow, that is a looong read!
Quite interesting though; thanks for posting the link.

---

### Post by Insanity01 on 2009-05-05
one thing first, linux ain't superiour to windows if it comes to gaming, for other things? yeah

And the shell is more for advanced users to do everything in a faster way
a pc was made to do things easy, as in using a keyboard and not having to look things up with your mouse...
It's harder but if you get better with it, you'll notice it's handy, but necessity? not really

---

