---
title: "Best way to learn the Terminal?"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Blackdragon1400 on 2008-12-02
Hey guys, I was just wondering what the best way to learn to navigate ubuntu's OS using mostly the terminal would be. I'm interested in getting used to using unix commands and such. i was just wonder how I should go about learning how to do this?????

---

### Post by binbash on 2008-12-02
for my experience best way to learn linux terminal is facing with problems = archlinux install or gentoo install.Also unpluggin mouse will do trick and i am serious about this.

PS : Also owning a server helps A LOT.

---

### Post by Blackdragon1400 on 2008-12-02
ok, im a noob what is "archlinux install or gentoo install"? just different versions of the OS?

---

### Post by carbm1 on 2008-12-02
As far as owning a server...  Linux can virtual turn any computer into a server.  I really started to learn the CLI after I installed Ubuntu Server edition.  I also read plenty online tutorials. I have also picked up a couple of those cheap small books from Amazon.

I just reached over and one I have is "Linux Pocket Guide".  It covers Fedora Linux but most of the commands are the same.  A quick flip through the book and it basically only covers command line.

---

### Post by poebae on 2008-12-02
This doesn't directly address your issue, but if you want to get more comfortable with using the terminal, install Yakuake and bind the shortcut key to F1.

I wouldn't bother using the terminal most of the time if I didn't have Yakuake to make it so easy :)

---

### Post by Girya on 2008-12-02
Check out linux from scratch. [//http://www.linuxfromscratch.org/lfs/]("http://http://www.linuxfromscratch.org/lfs/") Probably not the best way to learn the terminal though. 

Maybe this would be a better place to start:[http://linuxcommand.org/learning_the_shell.php]("http://linuxcommand.org/learning_the_shell.php")

---

### Post by nkri on 2008-12-02
As binbash said, learning from experience is the best way to go.

I would start with learning how to change directories with the
```
cd
```
command; for example, you always start in the Terminal in your /home directory.  To change directories to, say, your Documents folder, go into a Terminal and type
```
cd Documents
```

Then learn how to install/remove packages with
```
apt-get
```
apt-get is a command line package management system...the non-GUI form of Synaptic Package Manager.
For example, if you want to install pacman, type
```
sudo apt-get install pacman
```
It will ask for your password, and when you type it in, it won't show up...this is normal.  Just type it and press enter.  You now have pacman!

Also, be sure to learn the importance, power, and general use of
```
sudo
```
sudo (***s***uper***u***ser ***do***) is a command which allows you to run something as root (or all powerful administrator); it is a common command (apt-get requires it so that only you can install software on your system since you are the only one with your password, etc), but is very dangerous if used improperly (you can literally erase your entire system with one command).  

After that, you learn by running into problems and fixing them with new commands (we are always around to help if you have trouble:))

Also, [_this_]("http://ubuntuforums.org/showthread.php?p=475482#post475482") thread helps a lot if you aren't sure where to start.

Good luck!
-nkri

---

### Post by theozzlives on 2008-12-02
Basicly, just do it (that's how I learned DOS) at least Linux has the manpages

---

### Post by Sorivenul on 2008-12-02
> **Girya said:**
> Maybe this would be a better place to start:[http://linuxcommand.org/learning_the_shell.php]("http://linuxcommand.org/learning_the_shell.php")

This is always one of my suggestions.  
The other best place is directly from our own [Help]("https://help.ubuntu.com/community/UsingTheTerminal").

---

### Post by jeromey on 2008-12-02
best way to learn the terminal is to use it


just open the terminal and start using it

its really easy to use the terminal once you know a few basic commands


you could learn by setting yourself some goals and trying to  accomplish them

for instance you can say i want to be able to move this file from this directory to that one using only the command line

then you search the internet for the command to move files from one point to another in linux (the command is mv by the way)

then you try moving the file using your newly discovered command

you fail

but you read some more and learn some more and try again this time correcting your previous mistakes

and each time you mess something up you learn what not to do the next time

eventually your a pro


also the most important command youl ever know is the man command

you use the man command to read the manual pages for other commands

for instance if i wanted to learn about the mv command i would type this
```
man mv

```

this is especially important with certain commands where you need to know the options to use

for instance if you want to remove a file you can use the rm command like this
```
rm /home/tj/123.mp3
``` (this would delete the file 123.mp3 located in my users home folder (/home/tj/)

but if you wanted to remove an entire directory you would need to add the -r option to the command (r stands for recursively)
```
rm -r /home/tj/Music
```  (that command would delete my entire Music directory if it is executed with the proper privileges)


another thing you will need to know about is privileges

to make any kind of system wide changes you will need to have administrator (root) privileges

to get root privileges in ubuntu you will use the sudo command before the others  (i think sudo means something like superuser do)

```
sudo rm -r /home/tj/Music
```  (i would then be prompted for my password and after typing it in this would delete my Music directory)


EDIT: damn it looks like i took too long typing this, somebody already beat me to it

---

### Post by crwmike on 2008-12-02
Pick up a book on system administration, or a Linux+ study guide, it doesn't have to be new. Sit in front of your computer, read through the book and try the commands in the terminal.

---

### Post by xjcannonx on 2008-12-02
Instead of downloading .deb files, download the .tar file, maybe even try to build apps from source, that is how i am learning

---

### Post by nkri on 2008-12-03
> **xjcannonx said:**
> Instead of downloading .deb files, download the .tar file, maybe even try to build apps from source, that is how i am learning

This is a good way of learning, but I recommend against it since compiling from source does not integrate the software into GNOME (or KDE, XFCE, whatever you use) in the same way as .deb's.  It is, of course, personal preference, but if you compile something from source and later want to remove it, you have to find all the files and delete them manually, unless the package came with an uninstaller script; if you want to remove a .deb, you just go into Synaptic or use apt-get and don't have to worry about fragmented files and the like.

Good luck!
-nkri

---

### Post by WinterMadness on 2008-12-03
if youre new to linux, im gonna say gentoo and arch linux is a no go. you can learn the terminal on ubuntu without the headaches.

---

### Post by scorp123 on 2008-12-03
> **Blackdragon1400 said:**
> i was just wonder how I should go about learning how to do this????? There are just two commands you have to remember: [LIST]
[*]**apropos**
[*]**man**
[/LIST]

That's it. I mean it :D

Everything else will come from there.

Let's assume you want to reconfigure your network card for some reason ... Sure, you could use the "network-manager" icon to do this for you but you said you want to use the command line? Fine, so let's open a terminal and ask the terminal what it knows about networking: ```
> apropos network

**[COLOR="Red"]/etc/network/interfaces (5) [interfaces] - network interface configuration for ifup and ifdown[/COLOR]**
aseqnet (1)          - ALSA sequencer connectors over network
avahi-autoipd (8)    - IPv4LL network address configuration daemon
ctstat (8)           - unified linux network statistics
dhclient-script (8)  - DHCP client network configuration script
display-tele (7)     - Forwards the display over a network
**[COLOR="Red"]ifconfig (8)         - configure a network interface[/COLOR]**
[B]ifdown (8)           - take a network interface down
ifup (8)             - bring a network interface up[/B]
interfaces (5)       - network interface configuration for ifup and ifdown
iwconfig (8)         - configure a wireless network interface
iwgetid (8)          - Report ESSID, NWID or AP/Cell Address of wireless network
iwpriv (8)           - configure optionals (private) parameters of a wireless...
lanmap (8)           - A program that passively listens for any activity on y...
lnstat (8)           - unified linux network statistics
monkey-srv (1)       - monkey-bubble network server
mtr (8)              - a network diagnostic tool
nameif (8)           - name network interfaces based on MAC addresses
netdevice (7)        - Low level access to Linux network devices
netstat (8)          - Print network connections, routing tables, interface s...
network-admin (1)    - Network Administration Tool
NetworkManager (8)   - network management daemon
networks (5)         - network name information
nm-ppp-starter (1)   - PPP connection helper for NetworkManager
nm-tool (1)          - utility to report NetworkManager state
nm-vpn-properties (1) - Network management framework
nmap (1)             - Network exploration tool and security / port scanner
nstat (8)            - network statistics tools.
pabrowse (1)         - List PulseAudio sound servers on the network
ping (8)             - send ICMP ECHO_REQUEST to network hosts
ping6 (8)            - send ICMP ECHO_REQUEST to network hosts
pngtopnm (1)         - convert a Portable Network Graphics file into portable...
pnmtopng (1)         - convert a portable anymap into a Portable Network Grap...
rtacct (8)           - network statistics tools.
rtstat (8)           - unified linux network statistics
sane-net (5)         - SANE network backend
saned (8)            - SANE network daemon
services (5)         - Internet network services list
slattach (8)         - attach a network interface to a serial line
smbtree (1)          - A text based smb network browser
tcpdump (8)          - dump traffic on a network
tracepath (8)        - traces path to a network host discovering MTU along th...
tracepath6 (8)       - traces path to a network host discovering MTU along th...
traceroute6 (8)      - traces path to a network host
traceroute6.iputils (8) - traces path to a network host
wget (1)             - The non-interactive network downloader.
```
Do you see the stuff I highlighted? As you can see the shell is far from being cryptic ... as a matter of fact it will easily tell you the commands you'd need to type in if you ask nicely.

So now that we know which commands we would likely need to change a network configuration ... how precisely do we use those commands? Enter the **"man"** command, short for "**man**ual".

Chances are that each of the above commands that "apropos" spit out has a manual page attached to it. All you need to do is to ask "man" to show you the manual of the stuff you're interested in.

BTW, see those numbers in the brackets in above output? That's the chapter in the manual. Sometimes there are C procedures (yes, Linux includes programming manuals too!) and/or system variables that have the same name as a system command and the result might be ambiguous. Example - the "halt" command: ```
> apropos halt
halt (5)             - variables that affect the behavior of the shutdown scripts
halt (8)             - reboot or stop the system
``` Same name - two different things.

So in that case I'd add the number to what I need to know:
```
man 8 halt
``` .. that would give me the correct manual about the "halt" command which can be used to shutdown a system (in fact there are many ways).

Back to topic: Armed with "apropos" and "man" you can pretty much find anything you want and do anything you want via the shell.

Just keep using it and you will notice how all of a sudden you will know some commands by heart ... sooner or later using the shell becomes natural.

But as you can see ... **_The shell is friendly._** It tells you all you need or want to know if you ask nicely. It's not that "cryptic" or "hard to learn" at all. There is no reason to fear it.

---

### Post by Dr Small on 2008-12-03
The best way to learn? Practice.
Of course, the suggestions the other guys made are good too, but practice is the key. If you type (or even copy) one command into the terminal and say "ooohh. that was neat" and move on to the next command, what did you learn?

The best way to learn is to sit down, take a command, find out what the command does (by reading the manual), looking at the options (-x -y -z), understanding what they do, and practice using the command.

Compiling programs can teach you about compiling and learning how the programs work, but if you are just beginning at this with no patience for it, you will quickly become discouraged, even as I was.


Another way to learn, is to force yourself use the terminal for most daily tasks (no, I don't mean living in the CLI, like some of us challenge others to do). Just learning how to open Firefox, pidgin, and being able to kill them from the terminal is building your knowledge.

---

### Post by m_l17 on 2008-12-03
Using it for everything possible until you get comfortable with it. Once you do, you will notice it faster than using the gui for most tasks.

Take a look at this:

[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by treepolitik on 2008-12-21
So I have the "man" manual up.  As an example suppose I do exactly what I *think* it says to do for a particular option:

Under synopsis, it says:
```
mv [OPTION]... [-T] SOURCE DEST
mv [OPTION]... SOURCE... DIRECTORY
mv [OPTION]... -t DIRECTORY SOURCE...
```

So I would try the first, using arbitrary locations
```
mv --backup...[-T] /home /home/alpha
```

the second
```
mv --backup.../home... /home/alpha
```

the third
```
mv --backup...-t /home /home/alpha...
```

My point is that the instructions are not always clear for the command, despite that the syntax could be learned if a program was to be *written*.  For some reason, even though I am following the instructions, my submission does not seem correct.  If I were to try this, how would it be correctly coded(if you recognize what I would be trying to do)?  Also, is Bash space-sensitive?

---

### Post by handydan918 on 2008-12-21
> **treepolitik said:**
> 

My point is that the instructions are not always clear for the command, despite that the syntax could be learned if a program was to be *written*.  For some reason, even though I am following the instructions, my submission does not seem correct.  If I were to try this, how would it be correctly coded(if you recognize what I would be trying to do)?  Also, is Bash space-sensitive?

You are absolutely right. The man pages are less than perfectly understandable. They are also a helluvalot better than the DOS equivalent...
And yes, bash is space sensitive. a space is interpreted kinda like a \ is in a DOS shell. It matters.
Syntax is the toughest part of the shell, IMO. Just use it, and it will come.

---

### Post by Perkins on 2009-01-28
#-o

hint:  try 'man man'  ;)

---

