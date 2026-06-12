---
title: "Daily terminal commands?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by aceplayer97 on 2009-05-26
What are some commands that just a normal user could use in terminal to get things done quicker?

---

### Post by SuperSonic4 on 2009-05-26
**Daily/Near Daily Commands:** sudo, cd, cp, mv, ls, locate, rm, sudo apt-get update && sudo apt-get upgrade, ping, , nano, htop
[B]
Often but not daily[/B]: df -h, free, sudo fdisk -l, mkdir

reply to this post if you want to know what any of them mean :)

---

### Post by ugm6hr on 2009-05-26
Do you want to execute an identical command daily, or perform a similar action daily?

An  example might help.

---

### Post by SuperSonic4 on 2009-05-26
In some cases putting a script into ~/.Autostart (or wherever GNOME keeps them) if you want it at every boot. 

For example I set /usr/bin/numlockx to startup at when KDE does so whenever I log in num luck is turned on.


You may also set aliases to cut down on typing

---

### Post by aceplayer97 on 2009-05-26
> **SuperSonic4 said:**
> **Daily/Near Daily Commands:** sudo, cd, cp, mv, ls, locate, rm, sudo apt-get update && sudo apt-get upgrade, ping, , nano, htop
[B]
Often but not daily[/B]: df -h, free, sudo fdisk -l, mkdir

reply to this post if you want to know what any of them mean :)

Actually it would be nice if you could explain what all of them mean lol

---

### Post by bacardiandwatermelon on 2009-05-26
Here is a cheatsheet I found on the forum...

[http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/)

---

### Post by SuperSonic4 on 2009-05-26
> **aceplayer97 said:**
> Actually it would be nice if you could explain what all of them mean lol

EDIT: They're on that PDF the above poster linked to

**sudo** - run as root 
**cd** - change directory
**cp** - copy
**mv** - move
**locate**rm - remove
**ls** - list
**sudo apt-get update && sudo apt-get upgrade** - update your sources list and upgrade packages
**ping** - test your network connection
**nano** - cli text editor
**htop** - cli system monitor

**df -h** - shows a list of mounted filesystems- their size (in MiB/GiB
 etc) and how much is used
**free** - ram info
**sudo fdisk -l** - lists the disks on your system, their filetypes and their mountpoints
**mkdir** - create a directory

All of these have so-called man pages with more options so if you're unsure type ```
man <command>
``` where <command> is what you want to know

---

### Post by Idefix82 on 2009-05-26
The most important of them all is
```
man command
```
where command is any - well - command. It will open the manual page for this command.

Another one which I use a lot is tar.

Edit: SuperSonic4 beat me to it :)

---

### Post by _Purple_ on 2009-05-26
You might find this page helpful :)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by zerhacke on 2009-05-26
No matter what anyone tells you, do not run "sudo rm -rf /"

This will destroy your installation.

---

### Post by aceplayer97 on 2009-05-26
> **bacardiandwatermelon said:**
> Here is a cheatsheet I found on the forum...

[http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/)

Wow this sheet is amazing! Thanks for all the help everyone :)

---

### Post by aeiah on 2009-05-26
sudo shutdown -h now
sudo shutdown -h *time*

for shutting down

sudo reboot

sudo /etc/init.d/gdm restart (or start or stop for restarting your gui)

those are all useful for when you mess up your xorg.conf file like i tend to do whenever im starting to get my hdtv to play nicely :p

i dont run many commands on a daily basis besides the apt-get ones and perhaps vnstat and general file manipulation ones: ls, cd, mkdir etc.

id say a useful commandline program to get your head around early on is grep, and using it within a pipe. for example:

history | grep ssh
will show everything in your previous commands history that contains the word ssh, which is used for connecting to remote servers securely.

---

### Post by Celauran on 2009-05-26
> **aceplayer97 said:**
> What are some commands that just a normal user could use in terminal to get things done quicker?

I use the following every day and haven't seen them mentioned yet: cat, head, tail, less, grep, find, sed, ps

---

### Post by DBrocks on 2009-05-26
Got a runaway program? Use these to kill em. (Use with sudo)
          **ps -ef | grep {ProcessName}-** Find the PID of an unruly program.
          **Kill -9 {PID}-** Kill an unruly program
          **Killall {ProgramName}-** Also kill a program

---

### Post by Mornedhel on 2009-05-26
In addition to terminal commands, you might want to check out the bash keybindings when set to the (default) emacs style of keybindings :

Ctrl+R + some_string : case insensitive search in your history of typed commands, starting with the most recent ones -- cancel with Ctrl+G
Ctrl+A/E : go to the first/last character of what you've typed so far
Ctrl+K : erase all characters after cursor (aka Kill)
Ctrl+Y : re-paste killed characters (aka Yank)
Ctrl+W : erase previous word
Ctrl+C : interrupt/cancel, in most cases
Ctrl+D : insert "end of file" character, also exits terminal if typed on an empty line

Some all-time favorites that I have not yet seen mentioned :

watch [some command] -- displays output of [some command] every 2s
du -- display size of files, useful to know the total size of a directory
rename [perl script] 
[list_of_files] -- mass-rename a list of files executing the Perl script on each filename, for instance : rename 's/_/ /g' *.mp3 replaces all underscores by spaces for each MP3 file in the current directory

A previous poster mentioned find. It's incredibly powerful. You can do about everything with it if you know how to use it.

sed, awk, grep and cut, the text manipulation utilities, are also very useful.

Man pages, invoked with man [command], display its documentation in a convenient pager, complete with regular expression searching.

Last but not least : the omnipotent text editor emacs.

---

### Post by mprince on 2009-05-26
OK, try this one out. You could substitute another address if you like.  

```
w3m www.google.com
```

---

### Post by lisati on 2009-05-26
> **zerhacke said:**
> No matter what anyone tells you, do not run "sudo rm -rf /"

**This will destroy your installation.**

Emphasis added, just in case curiosity prevails. There are one or two others to avoid (or at least be extremely cautious about): see [here]("http://ubuntuforums.org/announcement.php?a=54")

---

### Post by raymondh on 2009-05-26
> **lisati said:**
> Emphasis added, just in case curiosity prevails. There are one or two others to avoid (or at least be extremely cautious about): see [here]("http://ubuntuforums.org/announcement.php?a=54")

On a test machine and out of curiosity, I did that once on purpose.  

The good thing that came out of that adventure was a sudden and continuous desire to learn the "how's" and the "why's" of Ubuntu and Linux.  

Still enjoying discovering and learning :)

Anyway, I digress .....  ditto on man command

---

### Post by Mornedhel on 2009-05-26
> **raymondhenson said:**
> On a test machine and out of curiosity, I did that once on purpose.

Yeah, I have the same morbid curiosity, but I don't have a test machine.

"How spectacularly would it fail ?"

---

### Post by mrbiggbrain on 2009-05-26
Ok so they arnt daily commands for everyone, but commands everyone should know. Linux differs from windows (and many other OS's) becuse they have many ways to install programs...

wget - gets files from a server

tar - untars files (.tar, .tar.bz, .tar.gz)
gzip - uncompress .gz files
bzip2 - uncompress .bz files

apt-get - manages installed packages (or installs new one)
dpkg -i - installs a .deb package

./configure - configures program for "make"
make - compiles programs, documentation reveals full requirements

g++ hello.C -o hello - compiles source code
g++ -c hello.C - compiles source code to object file
g++ hello.o -o hello - compiles object file(s) to executable

im probably missing a few, but for the most part, thats a quick list of what you need to know to install programs

---

### Post by Cowchip7 on 2009-05-26
> **DBrocks said:**
> Got a runaway program? Use these to kill em. (Use with sudo)
          **ps -ef | grep {ProcessName}-** Find the PID of an unruly program.
          **Kill -9 {PID}-** Kill an unruly program
          **Killall {ProgramName}-** Also kill a program

I find the runaway program using:

"top"                should tell you the PID number for the runaway program
"sudo kill (pid #)   and your good to go.

What does the -9 do?

---

### Post by Didius Falco on 2009-05-26
> kill -9 -1
              Kill all processes you can kill.

One of the first things I did was to go into **Terminal/Edit/Profile Preferences** and change the scrollback to 3000 lines temporarily. Then I cleared the screen and hit Tab 2x, pumped the Enter key until all the commands had scrolled by, Selected and Copied All and pasted it into an empty txt file to save.

Now, when I have a few minutes, I open the file, pick a command and read the Man page.

I'll never learn them all, but this way I at least know the names, which gives me a better chance of figuring out which command I need.

That was one of the more frustrating things at first - knowing what I needed or wanted to do, but not knowing the command that would let me do it.

I also learned than Man doesn't respond helpfully to commands like```
 man how do I copy a file! Answer me!!! 
``` ;)

Regards,

Didius

---

### Post by Mornedhel on 2009-05-26
> **Didius Falco said:**
> I also learned than Man doesn't respond helpfully to commands like```
 man how do I copy a file! Answer me!!! 
``` ;)

Man, it's a good thing you posted that. The correct way to ask the terminal that sort of question is :

```
apropos copy
```

It helpfully prints a list of man pages related to the keywords you enter (among them cp in our case).

---

### Post by Didius Falco on 2009-05-26
Yep, I know that _now_, but when I first started out, all I knew was that I didn't know anything. These forums and search engines helped a lot, though.

Now I know just enough to know how much I still have to learn.

Regards,

Didius

---

### Post by EssexEagle on 2009-05-26
> **aceplayer97 said:**
> What are some commands that just a normal user could use in terminal to get things done quicker?

I'm amazed no-one has mentioned [LinuxCommand.org]("http://www.linuxcommand.org") yet - it's the best way to start learning the Linux command line IMHO.

---

### Post by andrew.46 on 2009-05-26
Hi,

What about commands that you file away because you think that one day you *might* find a use for such as this:

```
 echo 'dnammoc hcus eno si sihT' | **[COLOR="Purple"]rev[/COLOR]**
```

Andrew

---

### Post by oldos2er on 2009-05-26
**apropos** is the bee's knees.

---

### Post by raymondh on 2009-05-27
> **oldos2er said:**
> **apropos** is the bee's knees.

LOL at the expression

---

### Post by Junkieman on 2009-05-27
> **Mornedhel said:**
> ```
apropos copy
```

I just learned another great command, thanks!

---

### Post by Nythain on 2009-05-27
another alternative to finding the pid of a program
```

pidof <programname>

```
while not as thorough as a good 'ps aux | grep <whatever>', it is quicker and easier to read

other htan that, i dont have any nuggets of wisdom except,
<program> -h or <program> --help
is generally a lot easier to follow than an entire man page, and if you gotta man something, unless you really love the terminal, most people for some reason find the web more comfortable
google 'man <program>' usually returns a lot of rather bland web pages of the man pages :P

---

### Post by ecmatter on 2009-05-27
> **EssexEagle said:**
> I'm amazed no-one has mentioned [LinuxCommand.org]("http://www.linuxcommand.org") yet - it's the best way to start learning the Linux command line IMHO.

Thanks for the link.

---

