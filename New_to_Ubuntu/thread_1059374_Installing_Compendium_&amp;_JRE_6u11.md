---
title: "Installing Compendium &amp; JRE 6u11"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Dr Mac 24 on 2009-02-03
Hi,

I'm using Compendium on windows XP without problems and it loaded easily. It's a neat progrm. I've built a new computer that runs OK with Ubuntu as the main operation system. How on earth do I load Compendium on this OS?
I have both compendium-openlearn-1.5.2.tar.gz and Java Runtime Environment - jre-6u11-linux-i586.bin as well as the RPM version.
Can anyone please tell me how to load these. Note I'm a new user of linux.

Cheers,

Daniel.

---

### Post by petervk on 2009-02-04
For java, you don't need to download it off the internet, just run:
```
sudo apt-get install sun-java6-bin
```
in a terminal. That will install the latest sun java packages for ubuntu. (not 6u11, but a recent version)

For Compendium, I can't help. If your just interested in mind mapping and not that program specifically you could try freemind.

FreeMind Website: [http://freemind.sourceforge.net/wiki/index.php/Main_Page](http://freemind.sourceforge.net/wiki/index.php/Main_Page)

FreeMind Download: [http://sourceforge.net/project/showfiles.php?group_id=7118&package_id=161831&release_id=574421](http://sourceforge.net/project/showfiles.php?group_id=7118&package_id=161831&release_id=574421)

Download the freemind_0.8.1-2_all.deb file and "run" it.

---

### Post by Dr Mac 24 on 2009-02-06
Peter,

Yor suggestion sort of works. My computer isn't online yet. So I'm using a copy on a stick. Your suggestion sort of works in that I can run JRE6 in my personal area, the wrong place I know. When trying to load it to /opt my password is asked for, but it nothing happens when trying to enter it.

Any suggestions?

See [http://openlearn.open.ac.uk/](http://openlearn.open.ac.uk/) for the compendium program.

Cheers,

Daniel.

---

### Post by taurus on 2009-02-06
When you enter your password, the cursor doesn't move or display *** on the screen.  Just make sure you enter the same password that you log in with (assuming you are allowed to use sudo) and hit the Return.

---

### Post by terran2cv on 2009-02-06
> **petervk said:**
> For java, you don't need to download it off the internet, just run:
```
sudo apt-get install sun-java6-bin
```
in a terminal. That will install the latest sun java packages for ubuntu. (not 6u11, but a recent version)

For Compendium, I can't help. If your just interested in mind mapping and not that program specifically you could try freemind.

FreeMind Website: [http://freemind.sourceforge.net/wiki/index.php/Main_Page](http://freemind.sourceforge.net/wiki/index.php/Main_Page)

FreeMind Download: [http://sourceforge.net/project/showfiles.php?group_id=7118&package_id=161831&release_id=574421](http://sourceforge.net/project/showfiles.php?group_id=7118&package_id=161831&release_id=574421)

Download the freemind_0.8.1-2_all.deb file and "run" it.
I have a problem using this command:

Code:

sudo apt-get install sun-java6-bin


when I type it in the Terminal, it says:

cesar@cesar-laptop:~$ sudo apt-get install sun-java6.bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6.bin

And never installs it. Can anyone help?

---

### Post by taurus on 2009-02-06
> **terran2cv said:**
> I have a problem using this command:

Code:

sudo apt-get install sun-java6-bin


when I type it in the Terminal, it says:

cesar@cesar-laptop:~$ sudo apt-get install sun-java6.bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6.bin

And never installs it. Can anyone help?

Which release are you using? 
```
lsb_release -a
```

Are you running x86 or x86_64?  
```
uname -m
```

Post your /etc/apt/sources.list
```
cat /etc/apt/sources.list
```

---

### Post by rarsa on 2010-07-21
> **terran2cv said:**
> I have a problem using this command:

Code:

sudo apt-get install sun-java6-bin


when I type it in the Terminal, it says:

cesar@cesar-laptop:~$ sudo apt-get install **sun-java6.bin**

Although the original poster didn't follow up with the people that were trying to help (That's always rude) he should have noticed that he is typing a dot instead of a dash on sun-java6-bin.

Why can't people just cut and paste the commands? That would save a lot of back and forth.

---

### Post by Dr Mac 24 on 2010-07-25
Noted, I'll now remember my dot from my dash. Yes I do now tend to copy & paste commands. Sorry for not replying to those that have helped. Thanks all.
I eventually loaded JRE 6 following info from the SUN site

---

