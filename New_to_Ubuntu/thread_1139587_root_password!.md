---
title: "root password!"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by smileyguy on 2009-04-27
**QUICK VERSION** 
What's the root password and how do I log on as root?

**EXTENDED VERSION**
This question is more about my understanding Linux rather than needing the root password.

Let's say I was a real super nerd (like you programmer guys) and wanted to use the root account to do whatever you geeks do (type code & program stuff). **How would I go about using the root account - or is it only the root passsword I need?** **Is the password I get asked for sometimes (for my user account) the root password? Can I log onto the root account like a regular user**(with all the GUI stuff)?

When I installed my version of ubuntu 9.04 it only asked me for a password for the first (assumed) user account, not the root account.

OK before you all go blasting me: 

[LIST]
[*]Yes I can only do stuff through GUIs
[*]Yes I will print out the free beginners guide at work tomorrow so I can read it during dinner instead of interacting with my children
[*]Yes I understand that the very fact that I am asking this questions means I shouldn't even be allowed to know what the root account is!
[*]Yes I promise not to use the root password if it is revealed!
[/LIST]

---

### Post by skymera on 2009-04-27
By default on Ubuntu, the root account is disabled without log in.

You can use Sudo to gain admin privs for a short period of time.
Im the Terminal, if you type "sudo su" you can become root with your password.
I tend to avoid being root as sometimes i cannot trust myself :)

---

### Post by abraxas334 on 2009-04-27
Well ubuntu is a bit different to other Linux distros as far as I understand. Most linux distros have options of using the command su which makes you a superuser, i.e. root. This is need to say install things edit certain config files etc.
In Ubuntu a user can have root privileges. So every time you type sudo something you are using the root admin privileges of your user account. So if you use GUI's like synaptic you change your system with root privileges. 
Programming on the other hand does not require any kind of sudo or root admin privileges because you can write and compile your own program with your normal user login.

your user accound password is also your root access password for sudo. Yeah and definitely avoid doing stuff as sudo su! Sudo alone will generally do the job you shouldn't login as root really.

---

### Post by Roadbloc on 2009-04-27
I think that the root or administraitor account is disabled unless your in the terminal.

```

su root

```

and then the root password which can be changed in users and groups in the admin menu.

---

### Post by bapoumba on 2009-04-27
Please remember our stance on login as root:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by spiderbatdad on 2009-04-27
> let's say i was a real super nerdroflmao

let's say i was superman...how would i actually go about flying?

---

### Post by t0p on 2009-04-27
If you want to do something "as root" (ie with admin privileges), prefix your command with **sudo**.  For instance, to edit the file at /etc/wvdial.conf, you could type into terminal

```
sudo nano /etc/wvdial.conf
```

If you want to do something as admin in gui, use **gksudo**.  To edit /etc/wvdial.conf with gedit (the gui editor), hit **Alt+F2** and in the box that pops up, type

```
gksudo gedit /etc/wvdial.conf
```

---

### Post by mcduck on 2009-04-27
> **smileyguy said:**
> **QUICK VERSION** 
What's the root password and how do I log on as root?

**EXTENDED VERSION**
This question is more about my understanding Linux rather than needing the root password.

Let's say I was a real super nerd (like you programmer guys) and wanted to use the root account to do whatever you geeks do (type code & program stuff). **How would I go about using the root account - or is it only the root passsword I need?** **Is the password I get asked for sometimes (for my user account) the root password? Can I log onto the root account like a regular user**(with all the GUI stuff)?

When I installed my version of ubuntu 9.04 it only asked me for a password for the first (assumed) user account, not the root account.

OK before you all go blasting me: 

[LIST]
[*]Yes I can only do stuff through GUIs
[*]Yes I will print out the free beginners guide at work tomorrow so I can read it during dinner instead of interacting with my children
[*]Yes I understand that the very fact that I am asking this questions means I shouldn't even be allowed to know what the root account is!
[*]Yes I promise not to use the root password if it is revealed!
[/LIST]

Short answer: There is no root password, and you just don't login as root. you don't ever need to, normal users who belong to admin group are able to do administrative tasks (and everything else that would require root permissions) using "sudo" and their own password.

Long answer: You don't need root account to do any of the "super nerdy stuff" you mentioned. Root is simply the administrator who has the ability to mess with all the system file, users and everything else in Linux systems. This has nothing to do with programming or anything people actually do when *using* the computer. Ubuntu just has easier way to handle system adminsitration which doesn't require you to log in as different user to maintain your system.

You should never log into desktop as root, as this would mean that every program you use would also have full permissions over your system. Now if any of those programs would have a security hole, possible attacker would automatically gain full access to your computer. Also there simply is no reason to log in to desktop as root, like I said it's simply administrative account and doesn't give any benefits on normal use like tasks you'd do on desktop.

So, when people are telling you you shouldn't use root they don't do it because they are trying to hide some secret knowledge from you. Just because you really, really don't need to do that, and will most likely get a smoother Linux experience with less problems if you leave the root account locked and just use "sudo" instead when ever you need administrative privileges.

---

### Post by kerry_s on 2009-04-27
a lot of us use nautilus scripts for editing root files and opening folders as root.

i use this:

```
#!/bin/sh

if [ -d "$@" ]; then
	gksudo nautilus "$@"
else
	gksudo gedit "$@"
fi

```

some will use something like this:
```
#!/bin/sh
gksudo gnome-open "$@"

```

there's a xdg-open to.

i wanted to be able choose what programs to use.
still work in progress, only installed this mourning. :)

---

### Post by smileyguy on 2009-04-27
So to perform tasks which require root access you are given a password and get prompted for that password every time you do something with root access? Is that right?

Sounds like what MS does with Vista and its security thingy (although I am aware the admin in Vista is not locked). And yes I know LInux did it first!

So if you're not even using the "root" password, what would you ever need the root account for? Is there another password for the root or are there just "other ways" of going about getting root access which I'll probably never need? I assume it wuold be by console access only too (root access) I think that's the gist I got from bapuoma's links.

---

### Post by t0p on 2009-04-27
> **smileyguy said:**
> 
So if you're not even using the "root" password, what would you ever need the root account for? Is there another password for the root or are there just "other ways" of going about getting root access which I'll probably never need?

There *is* a root password.  But default ubuntu generates a random password for root, and you never get to know it.  You never *need* to know it, if you wanna play by ubuntu's rules.

There are ways to change it to something chosen by you.  But the guys who run this forum don't like us to talk about it here.  All you gotta do, though is read the manpage for the **passwd** command and think about it for a minute.  You can also do it through the gui if you want.  I'd tell you how,but then I'd have to kill you! ;)

---

### Post by smileyguy on 2009-04-27
I'd tell you how,but then I'd have to kill you! :wink:

LMAO

I was waiting for that reply!

Thanks:)

---

### Post by Abu_Dayya on 2009-04-27
The root password is the password of the user account 'root'. loool

You usualy log on to the system with a user account you define during installation (i.e. your name). Root is the user that can control/have permission on the whole operationg system (Administrator account in Windoes). In linux you can switch to another users, either through command line interface (the command su), or through the graphical user interface (the 'user swtcher' on the top panel). Because root can control the whole system - you might want to read about file and permissions - it is considered a security risk to log in as root if you don't need to.

Thats why in Ubuntu, the root user is locked. You can't log on it when you boot your system, and you can't switch to it. You can unlock the root account from System -> Admin -> Users and Groups, and give it a password of your choice. This way you can use the 'su' command to switch to root with no problems. But its not advisable due to the security risk of being root when you  don't need to. 

An alternative method to swtching to root, is a program/command called 'sudo'. When you prefix any command you want to type with sudo, that command will run as if it was run by the root user. Sudo will only ask you for your own user password, just to make sure the sudo command is not being run by an automated script of a malicious program. This enables you to run  root/administrative tasks without having to log in as root. The GUI equivalent to sudo is this window you see when running some programs (the 'Enter your password to run administrative task' window), like the Upgrade Manager program for example, you need root account to upgrade and install softwares. Every application that requires root privilages, will take care of this on its own and you'll see that 'enter your password window' as if the application is running sudo itself (accually GUI applications use a GUI alternative to sudo called gksu).

Hope that helps

---

### Post by mcduck on 2009-04-27
> **smileyguy said:**
> So to perform tasks which require root access you are given a password and get prompted for that password every time you do something with root access? Is that right?

Sounds like what MS does with Vista and its security thingy (although I am aware the admin in Vista is not locked). And yes I know LInux did it first!

So if you're not even using the "root" password, what would you ever need the root account for? Is there another password for the root or are there just "other ways" of going about getting root access which I'll probably never need? I assume it wuold be by console access only too (root access) I think that's the gist I got from bapuoma's links.

Not really. Not logging in directly as root doesn't mean that you would have to type your password for every single thing you want to do with rot privileges. First, "sudo" remembers the password for certain amount of time so you don't need to type it again. Secondly, you can still use "sudo -i" to start a root session in a terminal, or "gksudo nautilus" to open the file manager as root etc.

So, you need to give the password every time you *start* doing administrative tasks. Not for every task you do.

And the root account is pretty integral part of the system itself, most of your systems services and stuff like that runs as root, and pretty much everything outside your home directory belongs to root. It's just that you don't need to log in as root yourself.

---

### Post by bapoumba on 2009-04-27
> **smileyguy said:**
> I assume it wuold be by console access only too (root access) I think that's the gist I got from bapuoma's links.
Others have already answered the rest of the post, so I'll stick to this :)

Ubuntu made choices, sudo, gksudo (or kdesu if using KDE). Other Linux distibutions still work with the root account to perform admin tasks and the user account for all the other stuff. It is all a matter of choice. If you come across a tutorial asking to be root to run a command, you can use sudo or gksudo. There are very limited instances where a true root account is required, and should not interfere with any regular use of the desktop (some situation over a network for a sysadmin for ex).

---

### Post by DGortze380 on 2009-04-27
> **bapoumba said:**
> There are very limited instances where a true root account is required, and should not interfere with any regular use of the desktop

Thanks, someone who knows what they're talking about instead of regurgitating 'what ubuntu told me to do'...

There are instances when you need to log-in as root, even the developers know this, because they put a root shell in the recovery kernel options. There is nothing wrong with logging in as root.

Disclaimer:

1) Ubuntu does not support this method of administering your system.
2) Good Luck if you screw up your system while running as root ... know what you're doing or don't use the account.

---

### Post by pastalavista on 2009-04-27
Use ```
gksu nautilus
``` and you can use the gui to do lots of different file operations. You can right-click on files and select 'properties' and change ownership and permissions without all the sudoing and texting but be very careful as you can bork your system quite easily.

---

### Post by 123456789123456789123456 on 2009-04-27
you can enable root, if you need to, you can only use root through terminal, I find it easy, to switch the user to root, so I can do multiple root functions, without typing sudo before each command.  GNU, or the graphical interface does not allow root login.

to enable root, you go to users, unlock
click on root
edit
create a password
and apply changes

root now has a password, and you can access the account.
It is all up to the person.
I find it useful as an technition to have root, so that if someone was unable to log into there account, I could change the runlevel through grub, and login as root from text mode terminal, to see what the problem is.

---

### Post by bapoumba on 2009-04-27
@ 123456789123456789123456: you can change the sudo timeout if you need to get it working for a longer period of time :)

---

### Post by me.translucent on 2009-04-27
i have one more question .. how can i set a blank    password for my account .it's possible in other distros but ubuntu just won't accept blanks :(

---

### Post by snowpine on 2009-04-27
In Ubuntu, the default root password is 'root', however, it is deactivated from the GDM login screen, so you can't actually log in as root. (Use sudo or gksudo instead.) However, you can select Recovery Mode from your Grub boot menu if you want full root access without a password. (Be careful! :))

---

### Post by DGortze380 on 2009-04-27
> **me.translucent said:**
> i have one more question .. how can i set a blank    password for my account .it's possible in other distros but ubuntu just won't accept blanks :(

must have a password

---

### Post by caravel on 2009-04-27
> **me.translucent said:**
> i have one more question .. how can i set a blank    password for my account .it's possible in other distros but ubuntu just won't accept blanks :(
This is probably because your account could then be easily compromised as it is on the sudoers list, this would be dangerous.

These discussions about su vs sudo have been going on since the beginning.  I use Ubuntu as it is with sudo, but Debian has a root login as do many other distributions so who is right/wrong?

I've seen many arguments for and against su and sudo.  Many admins dislike having any user accounts at all that can perform administrative tasks and this does makes sense.  The single root account as the sole administrative user with a regularly changed, complex password is harder to break than having multiple users that can use sudo as default.

I think it's really up to the user, though root is probably disabled on Ubuntu because it's dangerous for your average every day user.  Yes sudo can be configured per user so this makes it viable.  Sudo is also good in that you can set a time out, so that the root privileges are lost when the time is up.  This is an extra secure and beats accidentally leaving a root terminal open.  At the same time anyone that has migrated from another distribution, such as Debian should be able to enable the root account and use that in the terminal to do their administrative tasks - and there's no need for a "howto" as they should know how to do it anyway.

---

### Post by oldosc on 2009-04-27
> **smileyguy said:**
> So to perform tasks which require root access you are given a password and get prompted for that password every time you do something with root access? Is that right?

Sounds like what MS does with Vista and its security thingy (although I am aware the admin in Vista is not locked). And yes I know LInux did it first!

So if you're not even using the "root" password, what would you ever need the root account for? Is there another password for the root or are there just "other ways" of going about getting root access which I'll probably never need? I assume it wuold be by console access only too (root access) I think that's the gist I got from bapuoma's links.

hi
 am totally new to this..may I use a few lines to rant..I am a bit old, have played with computers since zx80..I run winxp, because it's best so far, back in 81 I could prog in basic on my acorn.since icons, I have not used command line prompts..I regularly read other rants..Mac/Win/linux, on many forums.
  I live in a small place (less than a 1000 people) but still know more than them (computer wise)UBUNTU sounds exciting, yet when a simple thing goes wrong, I cannot understand the posts from forums to start putting it right...is there any way to access LINUX with maybe a little less esotoric  knowledge. As an ex trawler captain, I have instructed total young persons how not to hit things at sea
Oldosc

---

### Post by Elfy on 2009-04-27
> **oldosc said:**
> hi
 am totally new to this..may I use a few lines to rant..I am a bit old, have played with computers since zx80..I run winxp, because it's best so far, back in 81 I could prog in basic on my acorn.since icons, I have not used command line prompts..I regularly read other rants..Mac/Win/linux, on many forums.
  I live in a small place (less than a 1000 people) but still know more than them (computer wise)UBUNTU sounds exciting, yet when a simple thing goes wrong, I cannot understand the posts from forums to start putting it right...is there any way to access LINUX with maybe a little less esotoric  knowledge. As an ex trawler captain, I have instructed total young persons how not to hit things at sea
Oldosc

Hi oldosc - if you need help and get confused by the non-nautical terms (I forget port from starboard all the time - annoys my boss no end :) ) then ask people to break it down a bit so you begin to learn it as you go - it's what I did.

People here will go slowly and answer it simply if you ask them too. If you need a bit more help then so be it - that is the way of this forum :D

---

### Post by t0p on 2009-04-27
> **oldosc said:**
> hi
 am totally new to this..may I use a few lines to rant..I am a bit old, have played with computers since zx80..I run winxp, because it's best so far, back in 81 I could prog in basic on my acorn.since icons, I have not used command line prompts..I regularly read other rants..Mac/Win/linux, on many forums.
  I live in a small place (less than a 1000 people) but still know more than them (computer wise)UBUNTU sounds exciting, yet when a simple thing goes wrong, I cannot understand the posts from forums to start putting it right...is there any way to access LINUX with maybe a little less esotoric  knowledge. As an ex trawler captain, I have instructed total young persons how not to hit things at sea
Oldosc

You should probably start a new thread. But anyway: you may be an old hand at computing, but you are a self-confessed newbie when it comes to linux. So study some newbie guides. You will soon pick it up.

---

### Post by snowpine on 2009-04-27
> **oldosc said:**
> hi
 am totally new to this..may I use a few lines to rant..I am a bit old, have played with computers since zx80..I run winxp, because it's best so far, back in 81 I could prog in basic on my acorn.since icons, I have not used command line prompts..I regularly read other rants..Mac/Win/linux, on many forums.
  I live in a small place (less than a 1000 people) but still know more than them (computer wise)UBUNTU sounds exciting, yet when a simple thing goes wrong, I cannot understand the posts from forums to start putting it right...is there any way to access LINUX with maybe a little less esotoric  knowledge. As an ex trawler captain, I have instructed total young persons how not to hit things at sea
Oldosc

Hi Oldosc, most tasks in Ubuntu can be accomplished using graphical tools (icons). However, we talk about the command line a lot on the forums because it can be a more accurate way to give help. 

Compare:

"Hey, I followed your advice and clicked the green button, then dragged the blue icon to the desktop, but when I did, an error message briefly flashed on the screen, and then the window did something weird, and now my panel looks funny."

with

"Hey, I copied the command you suggested and pasted it verbatim into the terminal, and it gave me the following output, which I am copying and pasting here so you can help help me troubleshoot."

See the difference? :)

---

### Post by Roadbloc on 2009-04-27
or you could always set yourself with the privileges of the root account....

---

### Post by winston-smith on 2009-06-26
as you've been told. not supported and don't cry when you shoot yourself in the foot

**$ sudo sh**

---

### Post by philcamlin on 2009-06-26
root account is locked by default :D:popcorn:

---

### Post by aysiu on 2009-06-26
This thread's issue has been addressed. No need to bring it up again.

---

