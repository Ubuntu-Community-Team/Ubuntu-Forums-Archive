---
title: "installed programs not showing up"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by badboyheathy on 2010-04-24
ive installed several programs from the synaptics package manager,but i cant see where it installed such as the ham radio programs, and commodore 64 emulator the commodore 64 emulator wont even load,

is there something i have to do to make them show up in the applications menu?

---

### Post by ed-koala on 2010-04-24
Here's a link on how to add programs to the menu - 

[http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html]("http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html")

Most times all you need to do is type the application name in the command area and it'll work.

---

### Post by mike555 on 2010-04-24
they usually go into USR/Bin  , look there and find their icon , if it works make a launcher in your menu by going to System/Preferences/main menu , click "new item" put the name in or browse to the icon , then pick a icon for that menu launcher.........

---

### Post by cuberts on 2010-04-24
> **badboyheathy said:**
> ive installed several programs from the synaptics package manager,but i cant see where it installed such as the ham radio programs, and commodore 64 emulator the commodore 64 emulator wont even load,

is there something i have to do to make them show up in the applications menu?It should be showing up in the start menu. Maybe this link will help : [http://www.tomshardware.com/forum/21528-45-newly-installed-program-shown-start-programs]("http://www.tomshardware.com/forum/21528-45-newly-installed-program-shown-start-programs")

---

### Post by badboyheathy on 2010-04-24
wow, lot of icons to use, first help didnt work, second one, yea i found some in the bin directory,

why dont these install into menu themself? or is there a shortcut?
maybe il stick with windows xp... i think its easier,
yea theres heaps of free software for this, i run some, acess denied... windows doesnt do it,
thanks for the help il see how it goes

---

### Post by badboyheathy on 2010-04-25
too many to shortcut too, some have an acess dienied to i/o port. why is that?
i remember, installing one, cant remember, i had to  umm sudo?  and a heap of commands after it to make it work, and that made the  shortcus come up in the applications folder, do i have to do that sudo thing to all of them?

sorry, im a real n00b to ubuntu. looks good, but hard to use.

---

### Post by 3rdalbum on 2010-04-25
> **badboyheathy said:**
> too many to shortcut too, some have an acess dienied to i/o port. why is that?
i remember, installing one, cant remember, i had to  umm sudo?  and a heap of commands after it to make it work, and that made the  shortcus come up in the applications folder, do i have to do that sudo thing to all of them?

sorry, im a real n00b to ubuntu. looks good, but hard to use.

No harder than any current version of Windows.

Permissions is something you'll have to wrap your head around... because you can't stick with Windows XP forever, and anything later than XP will require you to know this concept.

Basically, your normal user account on the computer is not all-powerful. It can't do anything that might interfere with other people using the system at the same time as you. If you need to do something that the ordinary user account can't do, you can elevate to "root" (administrator) using the 'sudo' command. But be careful - you can screw up your system if you're not careful.

So, if you have a command-line command that you want to run as root, just put the word 'sudo' before it. For GUI programs, you put 'gksudo' and then the name of the program. Some programs, like most in the Administration menu, add themselves to that menu with 'gksudo' already in place.

The Commodore 64 emulator I'm not familiar with, but if you're getting permissions problems you may need to run it with 'sudo'.

Permissions is a safety and security feature; Windows XP actually has it too, but it's not mandatory in XP (the first user account you create is all-powerful, so you basically have permission for everything). A recent study showed that, when you use permissions correctly on Windows XP and run your computer as an ordinary user, you're 75% less likely to get viruses.

For your other question: Some programs don't add themselves to the menu because they are command-line programs. A shrinking number of packages contain GUI programs but not the method for adding themselves to the menu; I haven't come across one for years, but if you see one it's easy to just add a menu item for them.

---

### Post by quadproc on 2010-04-25
> **badboyheathy said:**
> ive installed several programs from the synaptics package manager,but i cant see where it installed such as the ham radio programs, and commodore 64 emulator the commodore 64 emulator wont even load,

Other posters have answered your question, but here is a tip: to find out where a program resides type the following into a terminal:
```
which <programname>
```
For example, to find out where the "cat" program lives, type "which cat".  If the system doesn't show anything then the program is not in your search path but may still be on your system.  In that case, you can try the Search For Files command in the Places menu at the top left of your screen.

Regarding the emulator, is it intended for Linux?  Is is 32 bit or 64 bit?

quadproc

---

### Post by badboyheathy on 2010-04-25
alll the programs  i added ,including emulator, came from the synaptics manager thing so, assuming its from there, and not downloaded, it should be for the linux/ubuntu.

and to do with the permissions thing, this is the only user, ans will only ever be the user,
several ham radio  programs like acfax, get permission problems when loading trying to use the  serial or paralel port, (for use of PTT relay board)can i remove that problem?. i found that program in the  bin directory, but a lot of others i cant find, but the synaptics pacage manager says there installed.

last thing, can i remove the password everytime i install or load some games? loading games shouldnt need permissions should it?

thanks..

---

### Post by 3rdalbum on 2010-04-25
> **badboyheathy said:**
> 

and to do with the permissions thing, this is the only user, ans will only ever be the user...

last thing, can i remove the password everytime i install or load some games? loading games shouldnt need permissions should it?

Seperation between users, and seperation between user and administrator is what keeps malware and crackers from being able to do damage to your machine. Most of us here have only one human user on their computers, but we still run with the normal security policy simply because it's safer. Also, Linux expects its security system to be intact, and many programs just don't work properly without that system in place.

If you try and subvert the security system you can easily end off breaking your operating system, because everything's designed to work with it in place. So much so, that Ubuntu Forums actually doesn't let us tell you how to do this - too dangerous.

In short: Get used to it.

---

### Post by badboyheathy on 2010-04-25
well, goodbye ubuntu.. hello windows..thanks for help guys..

this pc not even going to be connected to the net once it was up and running,but so many  issues,

have a pc below an amature radio keyboard hidden out of the way, only useing mouse,.
run a program,need to type password.... so, have to dig out keyboard... bit too much trouble,

i give up......
thanks people, all too hard..one day il try again...if those issues can be easily fixed.

have a good time with your perfect machines...

---

### Post by Serpher on 2010-04-25
> **badboyheathy said:**
> well, goodbye ubuntu.. hello windows..thanks for help guys..

this pc not even going to be connected to the net once it was up and running,but so many  issues,

have a pc below an amature radio keyboard hidden out of the way, only useing mouse,.
run a program,need to type password.... so, have to dig out keyboard... bit too much trouble,

i give up......
thanks people, all too hard..one day il try again...if those issues can be easily fixed.

have a good time with your perfect machines...

If that's the case, in a terminal type in 'sudo passwd' then from then on just log in as root (Account name 'root'). Do NOT do this with internet access as this is what gives Linux it's almost impenetrable security, and is one of the reasons that makes Windows so bad. I don't think the problem is the OS rather than you getting used to changes, and why things are the way they are. You also can add these applications to the menu, even though they're suppost to really be run in terminal. Personally I make a file only containing something like

'firefox'

To start up firefox. Of course this icon is already there, like all programs that use a GUI, but if a program uses a TUI, it'll open up a terminal for that program which will close when the program is.

---

### Post by badboyheathy on 2010-04-25
thanks, il do that when/if i get things rite,
il explain all the things what i hate about it,that may be able to be fixed easily, some sofar as in the forum here cant be,for me, il start,

installing free software from the synaptics package,doesnt automaticaly show up...the #1

access denied with the software wanting to use the com and paralel port

the password, but h havent tryed that yet, because its on the internet

a lot more but there not so much of a issue,

even with the wine, windows software wont work, but thats expected,

---

### Post by 3rdalbum on 2010-04-26
> **badboyheathy said:**
> installing free software from the synaptics package,doesnt automaticaly show up...the #1

Most should, unless they are command-line programs; exactly which ones are not doing it?

> access denied with the software wanting to use the com and paralel port

That's not a problem, that's a part of the security design.

---

### Post by badboyheathy on 2010-05-02
pretty much every  amature radio program that i have installed if i could take a screen shot and paste here, i could show all ticked ones, only some psk31 ones have poped up in the menu

some others i have found manualy un the usr/bin folder, but too many to manualy add shortcut

as an examply im trying on now, is hamfax, its there it runs from in there, but why doesnt it automaticaly make a start button?

never mind il manualy open them, some sofare dont even work

---

