---
title: "help me please"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by Michalew818 on 2010-01-02
Although I am not new to computing and love the Ubuntu/Linux interface and philosophy, I am stumped every time I want to do something, (like make my wireless card work like an access point) all the tutorials start with writing code, and after hrs. of trying mostly because something in my computer configuration or release version is different I usually give up and turn off Ubuntu. 
Is there a way to change things in Ubuntu without having to type.
So would someone please direct me to tutorial lists that do not require typing.
Thank you 
Mike

---

### Post by cenzorrll on 2010-01-02
unfortunately many of the people who know ubuntu/linux best know it through the command line.  There are a lot of GUI (graphical user interface) ways to do things, but it's faster and more powerful to use the command line.  perhaps if you could make a list of what you want to do and someone may be able to point you in the right direction to find a GUI to do so?

with ubuntu becoming more popular and having more and more inexperienced users, GUI's will become more popular and available, just keep looking and asking.

---

### Post by donato roque on 2010-01-02
> **Michalew818 said:**
>  
Is there a way to change things in Ubuntu without having to type.
Mike

I went for about a year using Ubuntu without touching the terminal.  After I slowly learn the command lines, mostly by accessing the man pages, I realized how stupid I am for not using the power of the command lines.  There are GUI's but I can make things happen faster by invoking the command.  The power is there why not use it.

---

### Post by FreezWay on 2010-01-02
The command line isn't that bad. It's mostly copy and paste. some common thing's you'll see are:

cd - change directory (folder): you start out in your home folder and can cd to other folders ("cd .." takes you back a folder)

ls - list the stuff in the directory your in: go to your home folder and type ls. It will display the contents of your home folder.

man - manual: gives info about commands. try "man cd"

sudo - superuser do: do the commands after it with complete access to your computer. as a "superuser"

apt-get install - installs software from the repositories

apt-get remove - removes installed software but leaves its configuration

apt-get purge - removes installed software and configuration

apt-get moo - displays a text cow.
```
          (__) 
          (oo) 
   /------\/ 
  / |    ||   
 *  /\---/\ 
    ~~   ~~   
```

---

### Post by Anuovis on 2010-01-02
Could it be that most of the documentation and tutorials are outdated for 9.10? 

I also tried following several of them and always hit a wall because something was missing or different with the system I had. Might have been some specific things but when you realize you do not even have a file you are asked to edit in step 3 , this makes my wonder if this is not the case. 

Display settings via xorg.conf, Japanese input, changing boot screen... These are all good examples.

Maybe it is better to search forums for an answer? Usually people have more up-to-date solutions to things there.

---

### Post by DGortze380 on 2010-01-02
> **Michalew818 said:**
> all the tutorials start with writing code, and 

I assure you that the vast majority of tutorials do not require you to write a single line of code.

What you're referring to are terminal commands (not the same as 'writing code'), and they are used because they are the most powerful, efficient, and accurate method to preform most (if not all) tasks on *nix systems.

It is very different than the Widows GUI method, and takes some getting used to, but I assure you it's the best method for reasons stated above.

---

### Post by Michalew818 on 2010-01-03
I am sorry about using the word code to describe command line entry.
I have tried copy and paste method even using a remote terminal program (putty) because that is what one tutorial suggested.
I understand the power of typing or copying commands but after 2-3 hrs of trying everything, I found out things in my computer were called different than what the author had on his computer and that he was using 7.10 not 9.04, but no where did I find anything explaining what information I had to gather before I started copying and pasting.
When I try to type the commands half the time it will not accept my superuser  password if I add an extra space between commands or leave out the correct symbol.
Just for fun I tried commands for “man” this is what I got
michael@p3550ubuntu:~$ man

What manual page do you want?

OK then I typed.
michael@p3550ubuntu:~$ man cd

No manual entry for cd

I guess I was spoiled when I got my first computer in the early 90's using mac system 7.0.1 and everything worked as I expected it to. So I never learned to type commands like dos or unix users did.
And now computers are what I do to relax and play. So spending time typing or looking up information I have no idea most of the time what it means or if I  need it after I get it I give up. As I will do now it seems I am not smart enough to get this to do what I want so I  will remove this Ubuntu hard drive from my computer and leave my wireless access to the factory built wireless access points and routers. I will still keep checking on Ubuntu and the forums. Maybe in 20 years I will be able to do what I want with out being smarter than a computer.
Thanks for your time 
mike
by the way, to give an idea of time spent on this project this entry took almost 3 hrs to compose.

---

### Post by Methuselah on 2010-01-03
Hmmm....no manual entry for cd? Strange.
Anyway, if you explain what you want to do someone might be able to point you to a GUI.

---

### Post by Scunnered on 2010-01-03
Michalew818

As cenzorrll stated keep asking questions on the forum.  Like you I was steeped in Windows and initially ran for miles rather than use the terminal. Once I found that it was possible to copy and paste the instruction provided on the forum to the terminal it was all systems go.

Like you I have looked high and low only to discover that the manual that I bought has been superceeded by the current version of the OS.  In some instances the changes are not too bad and by following your book and comparing it to what you see on the screen you can get to a satisfactory conclusion.  In a lot of instances each new version improves the OS automating things that you had to do a bit of work to achieve with earlier versions.

Failing that then help is always at hand on the forum. Please be specific in your post heading as this will identify the problem and spark the interest of those who know what is what.  If you particularly detail which OS you are using and your system details this will assist others in getting to the root of the problem.

As is often quoted "Linux is not Windows" but don't dispare as the assistance given by others on the forum will have you up and running in jig time.  This happened to me and now I feel confident that,in some areas,I can contribute in the forum and at times to the documentation project.

---

### Post by 3rdalbum on 2010-01-03
> **Michalew818 said:**
> 
I guess I was spoiled when I got my first computer in the early 90's using mac system 7.0.1 and everything worked as I expected it to. So I never learned to type commands like dos or unix users did.

Yeah, I was a Mac user for more than 10 years. I ended off switching to Ubuntu straight from Mac OS 9. You really needed a terminal back in 2005 when I started with Ubuntu.

The terminal is mainly just copy and paste - it's not that difficult really, it's just different to what you're used to. But you do need to be using the correct commands for your version of Ubuntu - things move quickly here.

'cd' is (I think) a built-in command to Bash, which is why it doesn't have a man page. Most other commands are programs, which will have man pages.

As for getting your computer to act as an AP, I'm sure this doesn't require putting anything in the terminal. You can use Network Manager to bridge a wired connection to wireless. See: "Create New Wireless Network" in the Network Manager applet.

---

### Post by SteveNorman on 2010-01-03
[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)


learn it, live it, love it

---

### Post by Methuselah on 2010-01-03
I suppose Ubuntu does not package man pages for built in commands.
On the distribution I am using currently cd has a manpage.

Anyway, the OP really should not despair.
Copying an pasting is really, really easy in Ubuntu.

Here is a little trick:
Whenever you select text in Ubuntu it is automatically copied.
All you now have to do is hit your middle mouse button or press your mouse wheel and it will be pasted.

---

### Post by audiomick on 2010-01-03
> Here is a little trick:
Whenever you select text in Ubuntu it is automatically copied.
All you now have to do is hit your middle mouse button or press your mouse wheel and it will be pasted. 

I'll be jiggered. It works!:)

To see how "man" works, and find out a bit about the terminal
```
man bash
```

@scunnered: nice to see you here. ;)

---

### Post by Methuselah on 2010-01-03
> **audiomick said:**
> I'll be jiggered. It works!:)

To see how "man" works, and find out a bit about the terminal
```
man bash
```


What's more, the two buffers are different.
So if you select, then choose copy then select something else without choosing copy a subsequent paste will paste the first thing while a middle click will paste the second thing.
I thought it was pretty neat.

---

### Post by audiomick on 2010-01-03
Very neat. Thanks for the tip!

---

### Post by Alex De Duck on 2010-01-03
> **Methuselah said:**
> Hmmm....no manual entry for cd? Strange.
Anyway, if you explain what you want to do someone might be able to point you to a GUI.

It's the same for me. :/ No man entry.

---

### Post by Michaelw818 on 2010-01-03
Thank you for all the support so far.
I am sorry if I sounded harsh on giving up before, but like I said this is what I do to take my brain off work.
If this is the wrong forum let me know and I will move, I picked this one-even tough what I want to do is advanced my skill level in Ubuntu is beginner.
Ok lets start with what wish to do.
1: Wireless access point
2: File server acting as network attached device.
3; Secure ftp to access files in above server from the internet.
maybe
4: Web server.
5; Mail server.
I have at this time 2 wireless networks, one downstairs on a Linksys BEFW11S4 which is also my router. The other is a Linksys WRT54G acting as wireless access point to serve my upstairs. 
Every time I attempt to make changes in my networking controls something stops working. Following one tutorial I made changes to /etc/network/ interfaces and lost all network access, i was not able to regain access to the G access point, although it still shows in my network panel and I can connect but it will not get an ip address, but I can connect to the b router, which is ok for internet but is slow to access my network.
Lesson learned read tutorials very carefully before making changes and make copies of every thing I am changing if I need to return it to original form without having to reinstall Ubuntu.
Configuration at this time:
Dell OptiPlex GX 110 @1.0ghz
Original on board Intel 21140 nic eth5
3Com 3c920 pci nic eth6
Linksys WMP54GS Ver.1.1 wireless nic wlan0 (found in old computer that was being discarded) of course there are no native drivers for that card so I tried (windows wireless drivers) and attempted to install the linksys drivers, although it lists the card it thinks it is not there. Strange but at least it works somewhat.
I have installed wicd manager (read somewhere it had a better interface and it seems to work ok., but i have not found any way to add new networks with it.
Ubuntu 9,04
If it would be better I will install any other version or distro. I have disks for:
Ubuntu 7,10, 8.04, 8.10, 9.04, 9.04 server (another tutorial), and 9.10
Clark Connect 5.0 (another tutorial)
 I hope this gives more information as to what I want so I might be directed to the correct location for tutorials or forums.

thank you all
Mike

---

