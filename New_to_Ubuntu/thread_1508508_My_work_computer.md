---
title: "My work computer"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by brand-new on 2010-06-13
Hello everyone

I recently heard about Ubuntu(still can’t pronounce it), and just got through downloading it and tomorrow I will copy it to a disk, and am thinking about installing it on one of my computers.

Although I am brand new to Ubuntu, I have been using computers since 1995, and was a DOS man up until 2003(constantly staying about 5 to 10 years behind the times).

Moving from DOS to Win95, then 98, then XP, and am stopping their.
-------------------------------------------------- 
The question that I am asking here is a stupid one, because after all I am brand new....[COLOR=Red].
(If I install Ubuntu as my OS, does this mean that I will not be able to install and use any of my Windows programs??)[/COLOR]

I use my computer for work, 8 to 10 hours a day, and mainly use two programs:
(WordPerfect 12) & (Online Bible 2.10) & my Lexmark printer(driver).
-------------------------------------------------- 
Some people who use a computer for the internet and entertainment purposes only, may really like Ubuntu, but can those of us who NEED our old reliable programs, be able to use Ubuntu at all.
-------------------------------------------------- 


I am hoping that I am wrong, and that somehow Ubuntu can accommodate these programs, because I don’t like the way MS windows, seems to “gum-up” my computers.


Thanks for any help that can be given.

---

### Post by rukiaEnix on 2010-06-13
first of all ubuntu is also for work not someting for having fun.
and you can use openoffice instead of word

---

### Post by lisati on 2010-06-13
You won't be able to run Windows programs natively, but *some* can be run with the help of a program called "[Wine]("https://help.ubuntu.com/community/Wine")". 

There are equivalents for many Windows programs: for example, Open Office and Evolution (email) provide many of the same features as Microsoft Office.

---

### Post by spiky001 on 2010-06-13
hi you can use windows programs with something called Wine, also there are alternatives to window programs, the word program with Ubntu open office is compatable with window docs as well hope this helps

---

### Post by dtfinch on 2010-06-13
OpenOffice can read WordPerfect documents but not write them, so when editing your older documents you'd have to save to a different format.

---

### Post by garvinrick4 on 2010-06-13
Like any other OS Ubuntu has a learning curve, just like when you started using Windows.
If you make your living off of that one machine and do not have another one. Make your
living and learn Ubuntu in spare time before making the move.
 Start your machine with a dual boot until your learning curve is reached. I would say the
same thing to a person making his living running Ubuntu and wanting to try out Windows.
Gotta have them greenbacks to pay the rent. No what I mean.  [Main Page ]("http://ubuntuguide.org/wiki/Main_Page")
  I will tell you though I would never go back to Windows now, Linux is the way to go hands down.

[URL="http://ubuntuguide.org/wiki/Main_Page"]
[/URL]

---

### Post by mohamad123sh on 2010-06-13
> **dtfinch said:**
> OpenOffice can read WordPerfect documents but not write them, so when editing your older documents you'd have to save to a different format.

you can save your documents in older version of documents just by pressing control+shift+s and select type of file. U can choose on of wide range of ducument types.
for example:
word 95 document and....

brand-new
just install Ubuntu Inside Windows and learn first then switch to Ubuntu completely

one of my friends just install ubuntu(Fresh install) and completely remove his hard disk.

first research about Ubuntu and it's UI and other things , then install!!!

good luck):P):P:p:p

---

### Post by migs73 on 2010-06-13
Your Lexmark printer might be a problem though. They are notoriously poorly supported in Linux. Might be worthwhile finding out.
I have just had a quick look at the software centre as well and you could be spoilt for choice for bibles and bible based apps so no need to be online.

---

### Post by Matt__ on 2010-06-13
As for your bible question there are many bible packages in  Ubuntu...Bible time/Xiphos Bible guide/BibleMemoriser and even a whole  version of ubuntu for Christians...
[UbuntuCE]("http://ubuntuce.com/download.htm")

I cant see any native support for online bible but as mentioned previously it may run under wine and there is a MAC version too which you might be able to get going using... [MAConLinux]("http://sourceforge.net/projects/mac-on-linux/")


[COLOR=White].[/COLOR]

---

### Post by lkraemer on 2010-06-13
Since you are still sorta in the OLD DOS days have a look at DOSBOX.
Your DOS Software Programs can be run right in DOSBOX under Ubuntu.

[http://www.dosbox.com](http://www.dosbox.com)
[http://dosbox.sourceforge.net/wiki](http://dosbox.sourceforge.net/wiki)

You will need to install Dosbox in Ubuntu by using Synaptics or apt-get.
The folder/subdirectory that contains your older DOS program (EXE, COM,
or BAT) will need to be copied to your Ubuntu /home/loginname folder.

This folder will be mounted as C: Drive in Dosbox so the EXE, COM or BAT
file can be executed. To mount your C: drive, you will use the mount
command to mount the Linux folder as c and then change to Drive C:\> and
execute your old DOS Program.

As an example:
I had several recipes that were saved in C:\pw\2_LDK\Cookin on an
old Dos machine. I copied the complete C:\pw folder to /home/larry/C:/.
Then I executed Dosbox from the Ubuntu menu
APPLICATIONS &#8594; SYSTEM TOOLS &#8594; dosbox

When the dosbox window opened I typed the following:
Z:\> mount c ~/C: and the response was: Drive C is mounted as local Directory /home/larry/C:
Z:\>C: and the response was: C:\>
C:\>dir/p gave a paged directory listing of ~/C:>
C:\>cd pw and the pw window opened with the word processor running
C:\>pw and now I have access to my old recipes.


The following commands can be used in dosbox
intro
intro mount
intro cdrom
intro special
help
help /all

Along with a lot of special commands that are shown on their help screens.

Now, lets get Sourcer from V-Communications running in Dosbox. First we
need to copy the DOS subdirectory Sourcer_305 to the Linux folder C:.
This will copy all the files needed to run Sourcer version 3.05.
When the copy is complete, start Dosbox from the pulldown menu.
Then mount the folder as C: and do the following commands:
mount c ~/C:
C:
cd source~1
sr
(NOTE: Once mounted you don't need to repeat that command, just cd to the folder you need to access.)

To UNMOUNT C: use the following command:
mount -u c

**WORDPERFECT**
Wordperfect 12 most likely won't work, but be sure to go to 
[www.winehq.org](www.winehq.org) then click on APPDB and search for Wordperfect just so
see if someone has tested it.  (If it is a DOS Version it should work
fine in DOSBOX.)
Ref:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=530](http://appdb.winehq.org/objectManager.php?sClass=application&iId=530)

Looks as if it has some problems in WINE.  Another option is to use 
Crossover by Codeweavers to install Wordperfect in a Bottle in Crossover.
[www.codeweavers.com](www.codeweavers.com)
[http://www.codeweavers.com/compatibility/browse/company/?company_sort[company_name]=ASC;company_curPos=600;company_id=81](http://www.codeweavers.com/compatibility/browse/company/?company_sort[company_name]=ASC;company_curPos=600;company_id=81)

If Wordperfect doesn't use an Install/Setup program in Windows it might
be possible to just copy the subdiredctory from an installed version to
a Crossover Bottle and create a Link (Shortcut) to it and run it.
Otherwise, you can try to install it in a Bottle and see if it works.
  
**DUAL BOOT**
Since you are just starting with Ubuntu, I'd recommend using a Dual Boot
machine to make your transition as painless as possible.  With Dual Boot
you can make the transition as long or short as you need.  (I took two years,
and it was the correct thing to do for my case.)

**VIRTUALBOX**
Another option is to install VirtualBox, then install XP inside VirtualBox,
then install Wordperfect in XP and use it as normal.  But, you will need at least
2 Gig RAM, and need a machine fast enough so everything isn't real slow.
It could be used as an intermediate temporary fix until you make the transition.

**START HERE:**
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Send me Private Mail (PM) if you need specific help or have questions.

lk

---

### Post by brand-new on 2010-06-13
Thanks everyone, for your super quick input.
This is certainly a community.

Like most computer users, it is very hard moving from the things you know to something new, but sometimes it’s worth it.

I believe that I will install ubuntu on one of my old computers, and go from there.
By the way, will it work on a P1?
-------------------------------------------------- 
As for DOS, I do still have a DOS program that I use regularly(written in 1983), “Address Book Plus”, and it works great with XP, using shortcuts.

Does ubuntu have shortcuts?
Will I be able to get into my C drive with ubuntu? (Will I still have a C drive?)
-------------------------------------------------- 
As for Lexmark, that is a shame. (I have found Lexmark machines, to be the best hardware for printing, in existence.)


Thanks again for all your help.

---

### Post by migs73 on 2010-06-13
Your printer may still be able to work, it is just Lexmark is very protective of its drivers and does not release Linux ones. That has not stopped some clever individuals from 'reverse engineering' drivers that work in Linux. Do a google search (and search the forums) to see if yours is one of the few.

---

### Post by Don1500 on 2010-06-13
One thing not mentioned (they mentioned WINE and using a Virtual Machine) you can Dual Boot, i.e. have both operating systems on one computer. You can use one or the other to accomplish your task until you find a way of doing everything on Ubuntu. This will give you the opportunity to learn Ubuntu without hindering your work during that learning phase.

---

### Post by slash86 on 2010-06-13
Hi,

Your windows programs will not run in ubuntu. like others said, you can use Openoffice to get your job done or you can try to emulate them. I also found it funny what you said that ubuntu is just for internet and fun. I use it everyday at home and at work and got no problems. After some time you get so used to it that you'll have trouble using windows. believe me. Hope you install ubuntu, and sure you'll have fun ;)

---

### Post by slash86 on 2010-06-13
Hey man, you said your're going to install it on your old machine. Can you give us its configuration? Processor, memory, hard drive capacity, etc. If your old pc is equal or less than 256mb ram you may consider install an alternative version of ubuntu designed to low memory pc's.

---

### Post by -kg- on 2010-06-13
Greetings, brand-new

Like you, I started in DOS, but in 1984, before Windows was even an option.  I think that, considering you have DOS experience, the switch will be even easier for you than it would for those who have used Windows in all their computing.  You have the advantage of being comfortable with the CLI (Command Line Interface).

There will be a learning curve, but of course there is a learning curve with anything new.  I think the suggestion of dual booting until you get used to it and learn what replacement software there is is a very good one.  That way, if you absolutely need to get some work out and can't as yet figure out how to get it done in Linux, you can boot over to Windows and just get it done.

Another consideration for you is Virtual Box.  You can load and run a Linux OS in Virtual Box under Windows; you can also load Virtual Box under Linux in which to run Windows (and its software).

> I believe that I will install ubuntu on one of my old computers, and go from there.
By the way, will it work on a P1?

That would be another option. You can experiment with it until you get used to it and have your regular computer free to continue to take care of business.  Of course, I would take the dual boot option on my regular computer.  In that manner, you can make speed and efficiency comparisons on the same computer.  Of course, I have enough experience now that I can set up dual- (and multi-) boot installations in my sleep.

Whether it will work on a P1 is a matter of what resources you have on it.  As I remember, P1 technology (specifically, the ability to handle large hard drives) is somewhat limited, but I don't see why not.  You can make a "usable" installation on around an 8GB hard drive with no problem.  Larger would be better.  You will also need *at least* 256 MB of RAM to run it well.  And...expect it to be slow (I'm sure you already know this)!

> As for DOS, I do still have a DOS program that I use regularly(written in 1983), &#8220;Address Book Plus&#8221;, and it works great with XP, using shortcuts.

There are many Address Book type software out there, and many under Linux, including with Evolution (included by default in the installation) and many others.  While I understand holding on to software that you like, there are times that you finally just have to "let it go."  Try a few of the newer ones and you may find one that you like even better.

> Does ubuntu have shortcuts?
Will I be able to get into my C drive with ubuntu? (Will I still have a C drive?)

I'm sure Ubuntu has shortcuts (though I've never used them), and ***_absolutely_...***you will be able to retain and access your C: drive with/from Ubuntu.  The only way that you will lose your C: drive is if, during the installation, you choose the "Use Entire Disk" option in the partitioning section.

When performing the installation, choose "Install Side By Side" and the installer will shrink the C: partition and install in the free space created.

> As for Lexmark, that is a shame. (I have found Lexmark machines, to be the best hardware for printing, in existence.)

That certainly hasn't been ***my*** experience! :p

I have a Lexmark printer in the basement I bought a few years back that, after just a little operation started falling apart...***literally!***  Little screws and bolts started falling out of the carriage!  I may have gotten a lemon, but it certainly put me off!

I've always heard (and it has been my experience) that HP made the best printers.  I now have an HP Office Jet printer (bought just after the Lexmark fell apart) that I've had in operation for a number of years now that is just *excellent* and has performed perfectly, through use in several home businesses, printing out massive amounts of printouts.

And the thing is, HP printers are ***_very well supported_*** under Linux.  The basic drivers are included in the installation, and you can get the printer control GUI by installing "hplip" from the repositories.

Once you get used to it, I'm sure you'll find Ubuntu a very enjoyable and efficient OS.  I certainly do.  When I started, I kept Windows around and would boot into it to accomplish certain things.  As I learned, I found myself booting into Windows for less and less, until now.  Nowadays, I so rarely boot into Windows that I almost might as well not have it on my computers.

It's the same with several people I know.  They started out saying that Linux is nowhere near "ready for prime time," then morph into "well, this distribution is starting to get there," into "the next distribution just *might* be ready".  The next progression is obvious...they're using Linux and the "prime time" comment is never mentioned again.

:lolflag:

---

### Post by chandrav23 on 2010-06-13
Hi,New
Welcome to ubuntu......
 
Please ref ubuntu books to understand about ubuntu and its fetures.
 
Time being plese ref the below books:
 
1.Ubuntupocket guide
2.Ubuntu Kung fu
 
 
Thanks

---

