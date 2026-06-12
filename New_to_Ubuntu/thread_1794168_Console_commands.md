---
title: "Console commands"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by vagelism on 2011-06-30
Hello to all!
Is there out there any good free tutorial for Console commands?
Thank you!

---

### Post by dFlyer on 2011-06-30
From a terminal enter man then whatever command you want to use. man stands for maunal ie:

man cp                (copy)
man rm                (remove)
man mv                (move)

just to name a few.

---

### Post by FormatSeize on 2011-06-30
> **vagelism said:**
> Hello to all!
Is there out there any good free tutorial for Console commands?
Thank you!
[There are many]("http://www.google.com/#hl=en&xhr=t&q=bash+tutorial&cp=8&pf=p&sclient=psy&site=&source=hp&aq=0&aqi=&aql=&oq=bash+tut&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=c924775ad1dac27b&biw=1243&bih=636"). They are called "bash" tutorials since you are using the Bourne Again SHell.

---

### Post by dFlyer on 2011-06-30
I should have also said there are several tutorial references in the archives here. Just do a search of console commands.

---

### Post by spiky001 on 2011-06-30
See if [this]("http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html") helps

---

### Post by sisco311 on 2011-06-30
Start with the community documentation: [uhelp]community/UsingTheTerminal[/uhelp]

If you want to learn bash scripting, then check out the BashGuide at [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

Read the BashFAQ and BashPitfalls sections as well.

If you are new to Bash, then google is NOT your friend. The Internet is full of outdated tutorials and scripts full of bugs. If you have a question, ask it on freenode's #bash channel or here on the forum.

---

### Post by SniperWolf13 on 2011-06-30
Vagelism,

That's a really good question, but it does beg another in turn: what do you want to do in Konsole? 

The command lines for simple updates are themselves easy:

sudo apt-get updates, install -y 
sudo apt-get upgrade, install -y 
(the "install -y" part makes these  automatic, and is optional)

But if you're trying to do something more complex like mount a drive, create a shared drive or link servers, these are a LOT more complex. Beginner to beginner, I can honestly say I've learned most commands for things as complex as entire network builds on virtual machines by using Google to find how to point gateway server traffic to an authentication server. Just now, I pulled this:

[]("http://https://help.ubuntu.com/community/InternetAndNetworking")[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)

And this is where I go to do most network builds as it gives the command lines I need...

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

The command lines in these can be trusted since they are posted by Cannonical and the Ubuntu community. As for the lines I've posted at the beginning, they may be worth testing since I'm cursed with 10 thumbs. 


I do have to come back to the main question of what are you trying to do, if it's no secret? I may know the command lines for it or where to find it on Google.

--SniperWolf13

---

### Post by nothingspecial on 2011-06-30
> **sisco311 said:**
> Start with the community documentation: [uhelp]community/UsingTheTerminal[/uhelp]

If you want to learn bash scripting, then check out the BashGuide at [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

Read the BashFAQ and BashPitfalls sections as well.

If you are new to Bash, then google is NOT your friend. The Internet is full of outdated tutorials and scripts full of bugs. If you have a question, ask it on freenode's #bash channel or here on the forum.

This is good advice.

I had loads of bash bad habits (I still do). The BashGuide is the best tutorial I know of.

---

### Post by jtarin on 2011-06-30
[Bookmark]("http://www.linuxguide.it/commands")
[Searchbar]("http://www.linuxguide.it/command_line/en/linux_commands_line.php?MenuShow=Tools&ToolsOperation=m1#")

---

### Post by Frogs Hair on 2011-06-30
[http://linuxcommand.org/](http://linuxcommand.org/)

[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

[http://www.flickr.com/photos/caseytech/2988985863/](http://www.flickr.com/photos/caseytech/2988985863/)

---

### Post by dcsoldschool53 on 2011-06-30
We, all, had to start from some place, and these are some good places to start.

 [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

[http://ubuntuforums.org/showthread.php?t=171507](http://ubuntuforums.org/showthread.php?t=171507)

---

### Post by FormatSeize on 2011-06-30
> **sisco311 said:**
> If you are new to Bash, then google is NOT your friend. 
... oh. Perhaps this is why I'm not as good at shell scripting as I would like to be.

---

### Post by sisco311 on 2011-06-30
> **nothingspecial said:**
> 
I had loads of bash bad habits (I still do). 

Me too. Today, for example, I wrote a script in which I used the cd command without checking for error (BashPitffals #19). Guess what happens if you run the following script from your home:
```

cd /path/to/non-existent-directory
<insert the remove command here> -rf ./*

```

](*,)

Don't worry, I didn't run it. :)

> **FormatSeize said:**
> ... oh. Perhaps this is why I'm not as good at shell scripting as I would like to be.

It's newer too late to improve your skills and learn some good practice. Greg's Wiki is an excellent resource.

---

### Post by SniperWolf13 on 2011-06-30
> **nothingspecial said:**
> 

I had loads of bash bad habits (I still do). The BashGuide is the best tutorial I know of.

Hmm, that *is* good to know! I didn't know about that either. Thanks!

---

### Post by dash10 on 2011-06-30
I use [this bad boy]("https://launchpad.net/clicompanion"), works like a charm.

---

### Post by vagelism on 2011-06-30
> **sisco311 said:**
> Start with the community documentation: [uhelp]community/UsingTheTerminal[/uhelp]

If you want to learn bash scripting, then check out the BashGuide at [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

Read the BashFAQ and BashPitfalls sections as well.

If you are new to Bash, then google is NOT your friend. The Internet is full of outdated tutorials and scripts full of bugs. If you have a question, ask it on freenode's #bash channel or here on the forum.
Thank you!!!

---

### Post by vagelism on 2011-06-30
> **dcsoldschool53 said:**
> We, all, have to start from some place, and these are some good places to start.

 [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

[http://ubuntuforums.org/showthread.php?t=171507](http://ubuntuforums.org/showthread.php?t=171507)
Thank youi!

---

### Post by nothingspecial on 2011-07-01
> **sisco311 said:**
> Me too. Today, for example, I wrote a script in which I used the cd command without checking for error (BashPitffals #19). Guess what happens if you run the following script from your home:
```

cd /path/to/non-existent-directory
<insert the remove command here> -rf ./*

```

](*,)

Don't worry, I didn't run it. :)



It's newer too late to improve your skills and learn some good practice. Greg's Wiki is an excellent resource.

My worst one was using find to move all the files in all the subdirectories of the working directory to the working directory....

..... trouble is I didn't do it from ~/Videos :shock:#-o

hence my sig (lolcat speak or not)

---

