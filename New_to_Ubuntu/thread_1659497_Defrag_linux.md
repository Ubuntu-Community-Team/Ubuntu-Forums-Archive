---
title: "Defrag linux?"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Sirius B on 2011-01-04
Here is a quick question, in MS Windows such as XP and Vista there are tools that can clean up old and temp files and a disk defragmenter that defragments the hard drive or partition to help it run more smoothly.

My Question is does Linux or Linux distros such as *Buntu have tools to perfom these tasks? or is linux so wonderfull that it doesn't require being defraged?

Thanks

---

### Post by nomko on 2011-01-04
For Linux there's no need to use a defragmentation tool since Linux is handling files and filesystems on a different way then Windows (1 of the advantages of Linux).
 
But if you think there's a need for such a tool:
- [http://vleu.net/shake/](http://vleu.net/shake/)

---

### Post by Sirius B on 2011-01-04
> **nomko said:**
> For Linux there's no need to use a defragmentation tool since Linux is handling files and filesystems on a different way then Windows (1 of the advantages of Linux).
thats amazing, im yet to find anything wrong with linux.

im happy with linux so far, its miles better than any MS OS.

All i need to do is learn more about the linux language and commands, and i think my next thread for help will be about installing programes because if its not a self installing then  i have trouble understanding what to do manually.

thanks for your help

---

### Post by nomko on 2011-01-04
> **Sirius B said:**
> thats amazing, im yet to find anything wrong with linux.
 
im happy with linux so far, its miles better than any MS OS.
 
All i need to do is learn more about the linux language and commands, and i think my next thread for help will be about installing programes because if its not a self installing then i have trouble understanding what to do manually.
 
thanks for your help
 
Your welcome!

---

### Post by Yougo on 2011-01-04
there is an attempt at a 'cleaning' program called Computer Janitor, only it tends to be agressive and 'clean' programs and even vital pieces of your OS if you're not careful. i steer clear of it. other than that, i don't really know about a central cleaning program. many programs manage their own cache and temporary files, such as your browser and its history and cookies and so. 
at any rate, i find programs in linux to be both a lot less messy, and better at cleaning up after itself than on the other OS.

to clear old downloaded packages (when you installed a program through the repository, the downloaded install files remain stored on your computer) you could use ```
sudo apt-get clean
```

to remove packages the system no longer needs, you can use ```
sudo apt-get autoremove
```

if you have a pretty old ubuntu installation, chances are you have had a lot of kernel updates. older kernels remain available. while it may come in handy to boot with an older kernel, you might not need eight fo them hanging around. you an use the Synaptic Package manager (search for packages with the word "linux") to remove older ones.

also emptying your trash folder regularly is a space saver :)

as for defragmentation, the ext filesystems manage your files quite differently frm FAT or NTFS filesystems, and don't require (or benefit from) defragmentation

here's a good (simplified) read on how files are managed in different filesystems:
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by nomko on 2011-01-04
Never use Computer Janitor! It removes more files than you want! 
 
Only use the 2 given commands:
- sudo apt-get autoremove
- sudo apt-get autoclean
 
Normally the first command is sufficient to clean/remove.
 
And also remove Computer Janitor using synaptic.

---

### Post by Sirius B on 2011-01-04
> **Yougo said:**
> 

here's a good (simplified) read on how files are managed in different filesystems:
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

thanks for that link i will give that a read over with a cup of tea  :D

---

### Post by nomko on 2011-01-04
> **Sirius B said:**
> thanks for that link i will give that a read over with a cup of tea :D
 
Don't spill tea on your monitor! :lolflag:

---

### Post by paul_in_london on 2011-01-04
> **Yougo said:**
> there is an attempt at a 'cleaning' program called Computer Janitor, only it tends to be agressive and 'clean' programs and even vital pieces of your OS if you're not careful. i steer clear of it. other than that, [COLOR="Red"]i don't really know about a central cleaning program[/COLOR]. many programs manage their own cache and temporary files, such as your browser and its history and cookies and so. 
at any rate, i find programs in linux to be both a lot less messy, and better at cleaning up after itself than on the other OS.

to clear old downloaded packages (when you installed a program through the repository, the downloaded install files remain stored on your computer) you could use ```
sudo apt-get clean
```

to remove packages the system no longer needs, you can use ```
sudo apt-get autoremove
```

if you have a pretty old ubuntu installation, chances are you have had a lot of kernel updates. older kernels remain available. while it may come in handy to boot with an older kernel, you might not need eight fo them hanging around. you an use the Synaptic Package manager (search for packages with the word "linux") to remove older ones.

also emptying your trash folder regularly is a space saver :)

as for defragmentation, the ext filesystems manage your files quite differently frm FAT or NTFS filesystems, and don't require (or benefit from) defragmentation

here's a good (simplified) read on how files are managed in different filesystems:
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

In terms of a cleaning program you could look at **bleachbit** (installable from the repos):

[http://www.uluga.ubuntuforums.org/showthread.php?t=1527018](http://www.uluga.ubuntuforums.org/showthread.php?t=1527018)

---

### Post by nomko on 2011-01-04
> **paul_in_london said:**
> In terms of a cleaning program you could look at **bleachbit** (installable from the repos):
 
[http://www.uluga.ubuntuforums.org/showthread.php?t=1527018](http://www.uluga.ubuntuforums.org/showthread.php?t=1527018)
 
 
Like Computer Janitor even Bleachbit removes more files then wanted or expected. Such cleaning tools are completely unnecessary. 
 
Just use the 2 commands:
- sudo apt-get autoremove
- sudo apt-get autoclean
 
There's no need for more than those 2 commands!

---

### Post by niteling on 2011-01-04
I remember asking the exact same question...

---

### Post by nomko on 2011-01-04
> **niteling said:**
> I remember asking the exact same question...
 
I hope this topic was usefull to you!

---

### Post by alaukikyo on 2011-01-04
You can try [bleachbit]("apt://bleachbit") (a cleaner).

---

### Post by nomko on 2011-01-04
> **alaukikyo said:**
> You can try [bleachbit]("apt://bleachbit") (a cleaner).
 
 
**_Never_** use Bleachbit. Or Computer Janitor.
Those 2 applications removes more files (and even worse: systemfiles) then you wanted or expected!! If you want to end up with a unstable system, you're free to use them. In any other case: never use them! 
 
Just use:
sudo apt-get autoremove
sudo apt-get autoclean

---

### Post by matt_symes on 2011-01-04
Hi

It's not strictly true that Ubuntu does not need defragmenting. It does try to keeps its inodes together but the data for a file can be spread over the hard disk. There are a number of processes that attempt to mitigate this though especially ureadahead at startup (part of the reason Ubuntu boots quickly).

This is not nearly as bad as some other operating systems though. To you check to see how badly a file is fragmented using the filefrag command.

[http://manpages.ubuntu.com/manpages/lucid/man8/filefrag.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/filefrag.8.html)

Have a read of this

[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

> But Linux filesystems don't need defragmenting!

Whoever told you that is deeply mistaken, this is one of the most common myths of Linux.

What is true is that Linux filesystems avoid, where possible, fragmenting their inode tables. This means that the index of how files are split up (fragmented) across the disk, and where those parts are, tends to be kept together as a whole.

That's a good thing; fragmentation of inode tables is a big problem for other filesystems (FATs in that filesystem, etc.) so by keeping them together, it wins a lot of performance.

But the data itself is still fragmented, and spread all over your disk in a random order. And unfortunately during boot, it's the data we need.

One of the future things we want to do is use the ureadahead analysis of what we need during boot to feed into a defragmenter, so everything we need is in one big block on the disk.


Kind regards

---

### Post by dasan on 2011-01-04
But i believe Our journaling file system keep track of all the changes and hence fragmentation chances are less.
also it will be more stable compared to non journaling file systems.In case of sudden power failure etc...

---

### Post by nomko on 2011-01-04
> **dasan said:**
> But i believe Our journaling file system keep track of all the changes and hence fragmentation chances are less.
also it will be more stable compared to non journaling file systems.In case of sudden power failure etc...
 
And that's why i said that defragmantation is not needed. There's a difference between needed and required. If something is not needed, it doesn't mean it's not required. 
 
If someone feels the need to defrag his/her disk, i'm the last person to stop them! But if someone ask me if defrag is needed, then my answer will be that defrag is not needed.

---

### Post by Jay Car on 2011-01-04
> **Sirius B said:**
> Here is a quick question, in MS Windows such as XP and Vista there are tools that can clean up old and temp files and a disk defragmenter that defragments the hard drive or partition to help it run more smoothly.

My Question is does Linux or Linux distros such as *Buntu have tools to perfom these tasks? or is linux so wonderfull that it doesn't require being defraged?

Thanks

Hi Sirius B,

For general clean-ups, this "How-to" might also be helpful to you. 
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Also, here's a free [Ubuntu manual]("http://ubuntu-manual.org/") that you might find helpful. 

:D

---

### Post by waynefoutz on 2011-01-04
> **nomko said:**
> Never use Computer Janitor! It removes more files than you want! 
 
Only use the 2 given commands:
- sudo apt-get autoremove
- sudo apt-get autoclean
 
Normally the first command is sufficient to clean/remove.
 
And also remove Computer Janitor using synaptic.

Bleachbit is much easier than using the command line for beginners. Ubuntu Tweak is another safe clean up tool. Much safer than the Computer Janitor.

---

### Post by A_M_S on 2011-01-04
[here is a nice link]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting") to understand why fragmentation is less problematic in linux than in windows

---

### Post by matt_symes on 2011-01-04
Hi

As all file systems suffer some fragmentation, the real question becomes "does the fragmentation under extX file systems unduly affect performance?" 

The consensus answer to that question is no. I don't believe there is even a defragger for extX file systems at the moment (although if i am wrong someone should and will correct me). I believe one is being developed though.

Kind regards

---

### Post by nick_goodfate on 2011-01-04
you can also remove old kernels. [Ubuntu tweak]("http://ubuntu-tweak.com/") can do it with one click.

---

### Post by nomko on 2011-01-04
> **nick_goodfate said:**
> you can also remove old kernels. [Ubuntu tweak]("http://ubuntu-tweak.com/") can do it with one click.
 
Ubuntu tweak is, like bleachbit and computer janitor, has to be considered a dangeroius tool for beginners. Mainly for the reason that you can remove more than you want too. 
 
In Ubuntu tweak you can perform operations which goes beyond the security of Ubuntu, like adding or removing applications wityhout the necessary authentication check. For this reason, ubuntu tweak is prone to make a system very unstable. And therefor unsuitable for beginners who doesn't have the knowledge of an expert or novice user.
 
If you want to remove old kernels, use synaptic and a terminal.
- open a terminal
- type in: **uname -r**
- write down the kernelversion which is shown in the terminal
 
Now open synaptic and search for linux-header (hint: use the search button).
Mark all kernels for removale that do not match the kernel which you wrote down.
Click apply.

---

### Post by Sirius B on 2011-01-04
Oh dear i have seemed to opened a can of worms with asking about Defragmenting Linux :lolflag:however i have just made a cup of tea so im going to sit down with a notebook and click on all the links you kind peole have posted up.


As regards Bleachbit, and Janator and the like i think i will pass on them as im only new to linux and my luck I would mess it all up.

[QUOTE="namko"]**_Never_** use Bleachbit. Or Computer Janitor.
Those 2 applications removes more files (and even worse: systemfiles)  then you wanted or expected!! If you want to end up with a unstable  system, you're free to use them. In any other case: never use them! 
 
Just use:
sudo apt-get autoremove
sudo apt-get autoclean     [/QUOTE]

Yes i will try them codes in the Konsole Terminal, and if its ok with you (nomko) i will post up what the reply is and you could tell me if everything is ok?

---

### Post by psusi on 2011-01-04
> **matt_symes said:**
> I don't believe there is even a defragger for extX file systems at the moment (although if i am wrong someone should and will correct me).

See launchpad.net/e2defrag.

It used to be packaged in Debian and Ubuntu and known simply as the defrag package, but it was abandoned many, many years ago by its original authors so it suffered bit rot and was eventually removed.  I decided to save it and update it to run on ext4.  It is inherently dangerous though, so you want to have a current backup before trying to use it.

---

### Post by Sirius B on 2011-01-04
[QUOTE=nomko]
If you want to remove old kernels, use synaptic and a terminal.
- open a terminal
- type in: **uname -r**
- write down the kernelversion which is shown in the terminal
 
Now open synaptic and search for linux-header (hint: use the search button).
Mark all kernels for removale that do not match the kernel which you wrote down.
Click apply.[/QUOTE]

What is Synaptic? and where do i find the program? im running Kubuntu which as you will know is KDE desktop

---

### Post by oldsoundguy on 2011-01-04
there is a third party cleanup program called Ubuntu Tweak.  Program is also very good for managing repositories and  has some very useful utilities.

HOWEVER ...... do not get too aggressive with the program until you have a handle on Linux in general.
I find it really simple to use and it will get the occasional package file left behind from updating.
Decent documentation with the program.
(I use it to remove old kernels, also .. always keep the latest 3 kernels but will clean anything over that out.)

As to the de-frag .. about every 30th time you re-boot, the Linux system itself will automatically run hard drive checks.

---

### Post by mark_E on 2011-01-04
> **Sirius B said:**
> What is Synaptic? and where do i find the program? im running Kubuntu which as you will know is KDE desktop
 
. . .  "Synaptic's sibling on the Kubuntu desktop is Adept" as quoted here
 
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by Sirius B on 2011-01-04
> **mark_E said:**
> . . .  "Synaptic's sibling on the Kubuntu desktop is Adept" as quoted here
 
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)


How do i find/open Adept? is KpackageKit a different program?

---

### Post by oldos2er on 2011-01-04
You can install Synaptic on Kubuntu by opening a konsole and running **sudo apt-get install synaptic**. Not sure if adept is installed in 10.10; I personally prefer Synaptic to Kpackagekit.

---

### Post by beringse on 2011-01-04
Thanks for the info, I was wondering about this myself. Great users on this forum!

---

### Post by Sirius B on 2011-01-04
> **Sirius B said:**
> Oh dear i have seemed to opened a can of worms with asking about Defragmenting Linux :lolflag:however i have just made a cup of tea so im going to sit down with a notebook and click on all the links you kind peole have posted up.


As regards Bleachbit, and Janator and the like i think i will pass on them as im only new to linux and my luck I would mess it all up.



Yes i will try them codes in the Konsole Terminal, and if its ok with you (nomko) i will post up what the reply is and you could tell me if everything is ok?

Ok I've done the codes in the Terminal and here are the results:

**sudo apt-get auto remove**

Reading package lists...Done
Building dependency tree
Reading state information...Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded
[B]
sudo apt-get autoclean[/B]

Reading package lists...Done
Building dependency tree
Reading state information...Done

have i done this right? are the results to be as expected?

---

### Post by Sirius B on 2011-01-04
> **oldos2er said:**
> You can install Synaptic on Kubuntu by opening a konsole and running **sudo apt-get install synaptic**. Not sure if adept is installed in 10.10; I personally prefer Synaptic to Kpackagekit.
hey i have just done that, and it install fine, thanks. I have opened Synaptic and it seems to find alot more things to install than KpackageKit finds.

so does Ubuntu normally come with Synaptic or do you have to install it?

as regards adept being installed 10.10 i couldn't find it anywhere

---

### Post by matt_symes on 2011-01-04
Hi

Synaptic comes installed with Ubuntu.

System->Administration->Synaptic package manager.

BTW: No can of worms with defragging. Just debate ;)

> See launchpad.net/e2defrag

Psusi. Cheers. I'm having a look through the code now.

Kind regards

---

### Post by Sirius B on 2011-01-04
why hasn't Kubuntu come with adept? strange

anyway i now have synaptic thanks to you guys

---

### Post by nick_goodfate on 2011-01-04
> **Sirius B said:**
> **sudo apt-get auto remove**

Reading package lists...Done
Building dependency tree
Reading state information...Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded

what's the results of this command(copy-paste it in terminal):
> sudo apt-get upgrade

I'm asking because of the **1 not upgraded** part of "sudo apt-get autoremove" output ...

---

### Post by Sirius B on 2011-01-04
> **nick_goodfate said:**
> what's the results of this command(copy-paste it in terminal):


I'm asking because of the **1 not upgraded** part of "sudo apt-get autoremove" output ...

I got this:

Reading Package lists...Done
Building Dependency Tree
Reading State information...Done
the following packages have been kept back:
  devede
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded

---

### Post by puzzler995 on 2011-01-04
> **Sirius B said:**
> I got this:

Reading Package lists...Done
Building Dependency Tree
Reading State information...Done
the following packages have been kept back:
  devede
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded

```
sudo apt-get upgrade
``` will do the trick... apperently devede needs to be upgraded.

---

### Post by Sirius B on 2011-01-04
> **puzzler995 said:**
> ```
sudo apt-get upgrade
``` will do the trick... apperently devede needs to be upgraded.

did that and got this

Reading Package lists...Done
Building Dependency Tree
Reading State information...Done
the following packages have been kept back:
  devede
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded

---

### Post by nick_goodfate on 2011-01-04
> **Sirius B said:**
> did that and got this

Reading Package lists...Done
Building Dependency Tree
Reading State information...Done
the following packages have been kept back:
  devede
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded

for some reason the devede package can't be upgraded... 
try this in terminal
> sudo apt-get dist-upgrade
**but** when it ask you "Do you want to continue [Y/n]?", just choose n(press "n" and then Enter) and paste here want you see in terminal. Just to make sure that you don't make something wrong...

---

### Post by Sirius B on 2011-01-04
> **nick_goodfate said:**
> for some reason the devede package can't be upgraded... 
try this in terminal

**but** when it ask you "Do you want to continue [Y/n]?", just choose n(press "n" and then Enter) and paste here want you see in terminal. Just to make sure that you don't make something wrong...
lol
i didn't read your post correctly and i chose yes and i did loads of unpacking, well too much for me to write.

what shall i do now?

---

### Post by psusi on 2011-01-04
> **oldsoundguy said:**
> 
As to the de-frag .. about every 30th time you re-boot, the Linux system itself will automatically run hard drive checks.

Check != defrag.

---

### Post by nick_goodfate on 2011-01-04
> **Sirius B said:**
> lol
i didn't read your post correctly and i chose yes and i did loads of unpacking, well too much for me to write.

what shall i do now?

Did it upgraded devede thing? You can run sudo apt-get upgrade again and if it doesn't show any package which need upgrade means that it did upgraded.

note: you don't have to write by hand the output of commands, you can select-copy-paste from terminal...

---

### Post by Sirius B on 2011-01-04
> **nick_goodfate said:**
> Did it upgraded devede thing? You can run sudo apt-get upgrade again and if it doesn't show any package which need upgrade means that it did upgraded.

note: you don't have to write by hand the output of commands, you can select-copy-paste from terminal...

no its seems as it hasn't upgraded

I got:

Reading Package lists...Done
Building Dependency Tree
Reading State information...Done
the following packages have been kept back:
  devede
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded

---

### Post by nick_goodfate on 2011-01-04
> **Sirius B said:**
> no its seems as it hasn't upgraded

I got:

Reading Package lists...Done
Building Dependency Tree
Reading State information...Done
the following packages have been kept back:
  devede
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded

ok, it's not something to worry about, it's just one package that is not updated. You may have to start a new thread in order to find help for that. I can't help you any more, i'm sorry...

---

### Post by Sirius B on 2011-01-04
> **nick_goodfate said:**
> ok, it's not something to worry about, it's just one package that is not updated. You may have to start a new thread in order to find help for that. I can't help you any more, i'm sorry...
thanks for your help, your right im not really that worried about it for now

---

