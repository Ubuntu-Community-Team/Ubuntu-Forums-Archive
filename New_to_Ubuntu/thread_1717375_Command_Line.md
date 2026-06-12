---
title: "Command Line"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Ditchdoc7893 on 2011-03-29
I'm trying to learn command line.  Do you guys have any tips, tricks, or tools that will help someone with very little experience in any form of a command line?

---

### Post by termin on 2011-03-29
first, it is not called a 'cammand line' but it's called a 'console' or 'terminal'. Whatever you want to call it, it comes with a app called a 'shell'.  the shell can interpret the cammand that your typing in and execute it, the default shell for most distros (including ubuntu) is bash. I use ZSH because i'm a power user, but thats your choice. Second the places where i learned cammands are 
[http://www.linuxconfig.org/linux-commands](http://www.linuxconfig.org/linux-commands)
[http://ss64.com/bash/](http://ss64.com/bash/)
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugbasics.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugbasics.html)

---

### Post by termin on 2011-03-29
Also, if you want JUST a terminal/console and want to get rid of all the desktop apps, just press ctrl+alt+f1 to go back just press control alt f7 or f8 (depends on your linux kernal version) and to exit it all together just type in clear_console && exit inside of the terminal

---

### Post by steveneddy on 2011-03-29
command I believe is the correct word here.

I can be called command line or the other options listed in the previous post.

Here are some advanced commands:

[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

Here is a beginner tutorial:

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

---

### Post by aaaaalex on 2011-03-29
1st: Keep a Terminal window open
2nd: Use it
3rd: I said use it :-D 

A good point of reference on how to construct your fist scripts can be found [here.]("http://tldp.org/LDP/abs/html/")

It just takes time to learn about all the tools available on the CLI - and you will never be able to master them all. Some programs are highly idiosyncratic. 

Use a editor like nano or vi to edit your scripts. 

When yo encounter a program you dont know try the man page to see what it does, e.g.

```
man ls
```

Don't be affraid to ask. 

Search engines are you friends. 

Oh yes - use it. :-D Even if you feel that a certain task can be achieved faster by doing multiple clicks. Very often this is an illusion.

---

### Post by Nutria on 2011-03-29
> **termin said:**
> first, it is not called a 'cammand line' but it's called a 'console' or 'terminal'.

Don't be a jerk.

The command line is *on* the console or terminal or terminal window...

---

### Post by Nutria on 2011-03-29
> **Ditchdoc7893 said:**
> I'm trying to learn command line.  Do you guys have any tips, tricks, or tools that will help someone with very little experience in any form of a command line?

In addition to steveneddy & aaaaalex's great tips, remember that Google Is Your Friend.

I've found that these aliases are extremely useful by reducing the amount of typing you must do.  Add them to the end of your .bashrc file.
```
alias da='date +"%F %T, %a"'
alias df='df -x unknown'
alias dir='ls -aFl --time-style=+"%F %T"'
alias mkdir='mkdir -p'
alias mv='mv -v'
alias ra='history | sort -rn | less'
alias rm='rm -v'

```

You'll have to start with the nano text editor, but use vim as much as possible.  There's got to be some Beginners Guide out there...

---

### Post by Ditchdoc7893 on 2011-03-29
> **termin said:**
> first, it is not called a 'cammand line' but it's called a 'console' or 'terminal'. Whatever you want to call it, it comes with a app called a 'shell'.  the shell can interpret the cammand that your typing in and execute it, the default shell for most distros (including ubuntu) is bash. I use ZSH because i'm a power user, but thats your choice. Second the places where i learned cammands are [l]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugbasics.html")

First off, thank you nutria, aaaaalex, and steveneddy for your comments.  They are appreciated and useful.  Second of all, termin, don't be a jackass.  When someone genuinely asks for help, you don't assist by insulting them.  Third, I do believe it was you that introduced the term "cammand line", not myself.  I do believe I have a little more intelligence and can spell a little better than that.  Fourth, termin, if you have something else to say, take it elsewhere.  I have no use for your smartass remarks.  

Fifth, guys, I apologize for that interruption in this thread.  Thank you others for your links and feedback.  Again, my apologies for this interruption.  Your comments and help are welcome and appreciated.  :D

---

### Post by aaaaalex on 2011-03-29
Very important! 

Once you start diving into it your personality will undergo certain changes. You will start to look down on everybody who uses a mouse, you will suddenly begin to like checkered shirts and start growing a beard that in time might develop into what is commonly known as the full Stallman.

Are you sure you want to do down that road, my friend?

---

### Post by Ditchdoc7893 on 2011-03-29
aaaaalex, that's hilarious!  I can definitely appreciate the humor.  Just looking to try to stretch my brain and learn something new (to me) that I've not yet even begun to understand.  :D

---

### Post by aaaaalex on 2011-03-29
Once you know how to navigate you could take a look [here.]("http://floppix.ccai.com/scripts1.html") The page gives you two exercises at the bottom - just in case you are wondering what great scripting project you want to tackle first.

Has the beard started growing already?

---

### Post by Ditchdoc7893 on 2011-03-29
> **steveneddy said:**
> 
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

Here is a beginner tutorial:

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

steveneddy, I have taken a look through this particular beginner tutorial.  This is a little embarrassing for me, but in going through it, when he started talking about writing scripts.  The example he used, he utilized an HTML page I believe as an example.  What's embarrassing to me is that I really have no experience and don't know much about HTML, so I have quite a difficult time following this section.  I guess I really do have a long way to go, huh?

---

### Post by Ditchdoc7893 on 2011-03-29
Also, just to throw it out there, while Google is an infinite and endless plethora of information, are there any books or other literature out there for purchase that you would recommend? (yes, I'm just a little old school sometimes and like the reference ;))

---

### Post by oldos2er on 2011-03-29
Look for books on bash; O'Reilly has some good ones: [http://www.amazon.com/s/ref=nb_sb_ss_c_1_4?url=search-alias%3Dstripbooks&field-keywords=bash&sprefix=bash](http://www.amazon.com/s/ref=nb_sb_ss_c_1_4?url=search-alias%3Dstripbooks&field-keywords=bash&sprefix=bash)

---

### Post by Ditchdoc7893 on 2011-03-29
Thanks oldos2er!  Appreciate the info!  I like to have a reference text to utilize.

---

### Post by collisionystm on 2011-03-29
You may want to get this book. i have it and find it very useful. It is called Unix in a nutshell. Its on google books

[Here]("http://books.google.com/books?id=YkNiiLupct4C&printsec=frontcover&dq=unix&hl=en&ei=X5iSTeSkN4GN0QGBupTNBw&sa=X&oi=book_result&ct=result&resnum=5&ved=0CEkQ6AEwBA#v=onepage&q&f=false")

---

### Post by Nutria on 2011-03-29
> **aaaaalex said:**
> Very important! 

Once you start diving into it your personality will undergo certain changes. You will start to look down on everybody who uses a mouse,

As amusing as that is, I must say that I find the mouse invaluable in terminal windows (and even at the console).

> you will suddenly begin to like checkered shirts and start growing a beard that in time might develop into what is commonly known as the full Stallman

[Stallman's too young.]("http://farm1.static.flickr.com/87/240803829_9212773615_o.png")

---

### Post by Ditchdoc7893 on 2011-03-29
collisionystm, thanks for the reference.  Gonna check that one out as well.  Hell, I may spend some $ on reference texts since its not like I have to pay for the OS!  I love it!!!!

---

### Post by Ditchdoc7893 on 2011-03-29
> **Nutria said:**
> As amusing as that is, I must say that I find the mouse invaluable in terminal windows (and even at the console).



[Stallman's too young.]("http://farm1.static.flickr.com/87/240803829_9212773615_o.png")

I have to say, to this point my ventures in terminal at the command line have been minimal (when compared to more experienced users ventures in terminal), but you're right, I have used the mouse quite a bit and feel like it is an invaluable tool.  

Love the toon!!!!  Great!!!!:D

---

### Post by steveneddy on 2011-04-01
> **Ditchdoc7893 said:**
> steveneddy, I have taken a look through this particular beginner tutorial.  This is a little embarrassing for me, but in going through it, when he started talking about writing scripts.  The example he used, he utilized an HTML page I believe as an example.  What's embarrassing to me is that I really have no experience and don't know much about HTML, so I have quite a difficult time following this section.  I guess I really do have a long way to go, huh?

Well - it is hard to judge on an online forum exactly how "experienced" any one person is from a simple post.

Use the examples you find on all of these sites to pick up what you can and get familiar with the "lingo" of terminal usage.

In time you will start to understand more and more.

And most importantly - take your time and learn at YOUR speed - take the time to absorb what you are learning - then in time you will be a command line guru.

Let's go through a simply exercise:

Open a terminal - Applications --> Accessories --> Terminal

The "prompt" will have 

**username@machinename:~$**

followed by a blinking cursor.

type this in to the terminal

```
sudo apt-get install cowsay
```

then hit the "enter" key

OK - sudo means **[COLOR="Red"]su[/COLOR]per user [COLOR="red"]do[/COLOR]**

apt-get means use the **apt** service to **get** an application

cowsay is a toy

It will now ask for you password in the terminal - type your password, but you won't see it and the cursor will not move.

There will be things happen in the terminal - it if asks if you would like to install cowsay, just type a "y" and hit enter.

When you get back to the command prompt, simply type into the terminal

```
cowsay Terminal is cool
```

and hit "enter"

There - you just did something in the terminal

---

### Post by cyb3r_sn4k3 on 2011-04-02
Books help you a lot. Then try to do (almost)everything on the terminal instead of relying on GUI :D

---

### Post by nahallac on 2011-04-02
I'd like to ask what you're wanting to learn? Is it using the command line to perform admin tasks and generally navigate? Or do you want to delve into scripting?
 
I'm fairly new to Linux myself, so I'm happy to share some of my limited experience thus far!

---

### Post by Ditchdoc7893 on 2011-04-02
steveneddy, thanks for the encouragement.  Its nice to try to take some baby steps, because Lord knows that´s the size of my steps so far.  :D

> **nahallac said:**
> I'd like to ask what you're wanting to learn? Is it using the command line to perform admin tasks and generally navigate? Or do you want to delve into scripting?

nahallac, I guess I have a broad wish list of things to learn.  In a general sense, I would like to become proficient with navigating the system from terminal as well as performing admin tasks.  The more I read, the more I want to learn about scripting, but as it is with anything complex, you have to master the basics first to even be able to make more complex tasks do-able.  So right now, I´m in to learning the basics and being able to navigate proficiently.  I think the concept I may be having trouble with is that having grown up (I guess you could say) on GUIs (from the enemy that´s name starts with a W), I have grown accustomed to having things right there in front of me in a very visual format.  So coming up with commands off the top of my head feels quite challenging.

---

### Post by nothingspecial on 2011-04-02
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by Ditchdoc7893 on 2011-04-02
nothingspecial, thank you for the link!  Looks like a lot of info, but that´s definitely the kind of things I´m looking for.  Thanks so much!  :D

---

### Post by nothingspecial on 2011-04-02
No problem, in that case here's a few more

[http://wiki.bash-hackers.org/start](http://wiki.bash-hackers.org/start)
[http://sunsite.ualberta.ca/Documenta...creen_toc.html](http://sunsite.ualberta.ca/Documenta...creen_toc.html)
[http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)
[http://regexlib.com/CheatSheet.aspx](http://regexlib.com/CheatSheet.aspx)
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

### Post by Ditchdoc7893 on 2011-04-02
Wow!  I´ve got some reading to do!  Thanks!!!  :D

---

### Post by wizard10000 on 2011-04-02
> **termin said:**
> I use ZSH because i'm a power user, but thats your choice.

After almost 20 years of providing enterprise-level desktop support it's been my experience that people who call themselves power users are generally anything but.

:D

---

### Post by el_koraco on 2011-04-02
> **wizard10000 said:**
> After almost 20 years of providing enterprise-level desktop support it's my experience that people who call themselves power users are generally anything but.



you just beat me to it. 
they're also often in the 15 to 17 year demographic.

---

### Post by Ditchdoc7893 on 2011-04-02
> **wizard10000 said:**
> After almost 20 years of providing enterprise-level desktop support it's been my experience that people who call themselves power users are generally anything but.

:D

That was my take on that line as well.

---

### Post by Ditchdoc7893 on 2011-04-02
> **el_koraco said:**
> you just beat me to it. 
they're also often in the 15 to 17 year demographic.

Without a doubt.

---

### Post by nothingspecial on 2011-04-02
> **Ditchdoc7893 said:**
> The more I read, the more I want to learn about scripting, but as it is with anything complex, you have to master the basics first to even be able to make more complex tasks do-able. 

IMO the best way to learn is to find something you would like to automate then try to script it. I mean learning bash is quite daunting and can be quite boring if you simply try to learn it. If you have a goal, then you have an incentive and solving the problem you set yourself can be very rewarding.


> **Ditchdoc7893 said:**
> coming up with commands off the top of my head feels quite challenging.

Don't try and remember all the commands at first, rather try to understand how to construct a script. The commands are all available through your preffered search engine.

For scripting, I would say, the most important concepts are variables and arrays, parameter expansion, loops and conditionals. (see the links I posted).

What I'm trying to say is that (for example)

```
[COLOR="Red"]if [/COLOR]

blah blah blah

[COLOR="Red"]then[/COLOR]

blah blah blah

[COLOR="Red"]else[/COLOR]

blah blah blah

[COLOR="Red"]fi [/COLOR]
```

It's the bits in red, the construct of the script and understanding how they work that is more important than knowing every single option of the find command......


.......if you see what I mean.......


..... I don't think I'm explaining myself very well.

---

### Post by wizard10000 on 2011-04-02
> **nothingspecial said:**
> IMO the best way to learn is to find something you would like to automate then try to script it. I mean learning bash is quite daunting and can be quite boring if you simply try to learn it. If you have a goal, then you have an incentive and solving the problem you set yourself can be very rewarding.

I think this is excellent advice.  I'd add that just about anything anybody's ever wanted to do so far has already been done by somebody else (or something awfully close to it has) so I tend to leech other people's scripts, adapt them for my needs and learn how they work at the same time.

---

### Post by cmcanulty on 2011-04-02
I am also trying to learn. I find it easy to learn various commands but have trouble figuring out where to put spaces or not, and the order of commands, options, etc which doesn't seem clearly explained

---

