---
title: "Pidgin"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by Georgia boy on 2009-06-20
Hi guys and gals. Using Hardy. Since Pidgin isn't able to connect to Yahoo Messenger now what in the repos' is a good replacement? Also, will Pidgin update itself with our regular updates when it comes out with a version that will work with Yahoo or will we have to wait until we get the next LTS?
Just curious. Right now, having to go to Yahoo and sign in to do any instant messaging with them.
Thanks
Tom

---

### Post by treesurf on 2009-06-20
There is a Yahoo IM client for Linux called Gyachi.  I have not used it, but it supposedly supports webcam, voice, etc.  It can be downloaded from this PPA:

[https://launchpad.net/~loell/+archive/ppa](https://launchpad.net/~loell/+archive/ppa)

Change the drop down menu to Hardy, add those two lines into your Software Sources>Third Party Software, and then do a "sudo aptitude update" and "sudo aptitude install gyachi" in the terminal.  You can follow the instructions on that webpage for how to install the gpg key do that it doesn't give you annoying messages when you install the program.

---

### Post by starcraft.man on 2009-06-20
> **Georgia boy said:**
> Hi guys and gals. Using Hardy. Since Pidgin isn't able to connect to Yahoo Messenger now what in the repos' is a good replacement? Also, will Pidgin update itself with our regular updates when it comes out with a version that will work with Yahoo or will we have to wait until we get the next LTS?
Just curious. Right now, having to go to Yahoo and sign in to do any instant messaging with them.
Thanks
Tom

If you want to keep using pidgin, I think this is the fix you'll want. [Link]("http://ubuntuforums.org/showthread.php?t=1192417&highlight=yahoo"). Post by eagelton.

---

### Post by djheadley on 2009-06-20
What Ubuntu release are you using?  I've used Pidgin since it came out and I don't have any problems with it.

---

### Post by Sef on 2009-06-20
> Since Pidgin isn't able to connect to Yahoo Messenger now what in the repos' is a good replacement? 

Have had similar problems.  here is how I fixed it: 

Look at post 514 of [this thread]("http://ubuntuforums.org/showthread.php?t=773802&page=52&highlight=gyachi").  It's the [gyachi]("http://ubuntuforums.org/showthread.php?t=773802&highlight=gyachi") how to thread.

> Also, will Pidgin update itself with our regular updates when it comes out with a version that will work with Yahoo or will we have to wait until we get the next LTS?

You have to wait, unless you want to install a PPA, so it will update.

---

### Post by Georgia boy on 2009-06-20
I'm using Hardy 8.04. Just noticed tonight that it isn't working. Read a post that others are having same problem so just was wondering what could be used until Pidgin gets updated.
Tom

---

### Post by Georgia boy on 2009-06-20
Thanks everyone!!!! I wasn't able to get my buddy list to show. Then I went to that link and saw where it said to put in the IP address. Works great now!!!
Yea Team!!!
Have a wonderful weekend everyone!!!
Thanks
Tom

---

### Post by 3rdalbum on 2009-06-21
I recommend using Meebo.com as their web-based messenger keeps up with all protocol changes, and supports a large number of the same protocols as Pidgin. (plus, does Facebook Chat natively using the Facebook Connect API)

---

### Post by LewRockwell on 2009-06-21
[http://bigbrovar.wordpress.com/2009/06/21/how-to-fix-pidgin-and-yahoo-issues/](http://bigbrovar.wordpress.com/2009/06/21/how-to-fix-pidgin-and-yahoo-issues/)

---

### Post by Georgia boy on 2009-06-21
This is the link that I finally found last night when doing this. Tried it and it worked real well. I wish to thank everyone for their helpful solutions. There are so many to choose from. 

 [http://ubuntuforums.org/showthread.php?t=973284&highlight=pidgin+yahoo](http://ubuntuforums.org/showthread.php?t=973284&highlight=pidgin+yahoo)

By the way, I noticed on some of the links I was following that people were talking about Facebook. If you have friends that use Facebook and are using Windows that they might want to be careful. A friend of mine got about five virus's and she thinks that she got them while playing some game on Facebook. 
Just something that I thought some of you might be interested in.
Again everyone, thanks for your wonderful help. This is why I'm always checking the forums and ask questions here

---

### Post by Hund on 2009-06-21
Upgrade Pidgin to 2.5.7 using their PPA: [https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by LesterPalooza on 2009-06-21
Whew! It's good I'm not alone in this problem :D

---

### Post by BeBoBli on 2009-06-21
> **3rdalbum said:**
> I recommend using Meebo.com as their web-based messenger keeps up with all protocol changes, and supports a large number of the same protocols as Pidgin. (plus, does Facebook Chat natively using the Facebook Connect API)

I would never recommend Meebo for anything other than using on other computers you don't have permission to install on. It doesn't have a lot of features a taskbar program would have such as notifying you visually of instant messages and it uses a lot more resources (especially if you want to do something else with your computer other than use the browser). Other problems I'd only be nitpicking. It's excellent as a program itself, just it being programmed in flash, AJAX or whatever browser-based IDE really limits it's usability.

---

