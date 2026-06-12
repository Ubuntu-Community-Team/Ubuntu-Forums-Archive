---
title: "Installing Games"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by jcmanley87 on 2010-06-04
So I'm new to Ubuntu and I already like it more than Windows. But I don't know how to install a game using Ubuntu. I have the game The Witcher and its not working for me. Any Help? And would same thing apply for Eve online?

---

### Post by c9-3Rr0r on 2010-06-04
To run windows games under linux u can use wine 
```

sudo apt-get install wine

```

when navigate to folder where game installer is and execute

```

wine installer_or_setup.exe

```

after installation is complited go to folder where u install game 
probably ~/.wine/drive_c and execute it

```

wine appname.exe

```

hope that it helps a little

---

### Post by TheMadMan on 2010-06-04
> **jcmanley87 said:**
> So I'm new to Ubuntu and I already like it more than Windows. But I don't know how to install a game using Ubuntu. I have the game The Witcher and its not working for me. Any Help? And would same thing apply for Eve online?
 
Is The Witcher a game for Windows or have you got a Linux version of it?  Just done a quick google of the game and I cannot find any reference to a Linux version being available, but I may be wrong.
 
Anyway, assuming that the game is a Windows game then you'll have to attempt to install the game using WINE.  You'll initially have to download and install WINE through the software centre.
 
Once WINE is installed you can give it a go installing The Witcher through WINE.  Based on my limited experience (see my post count, and I've only been using UBUNTU since Monday!) I think you will need to right click the executable file on the CD and click the install using WINE option (or words to that affect).  
 
There's probably a way of doing all this via the Command Line, but I'm currently inexperienced with the CLI and tend to use the GUI when needed.  
 
Hope this helps.

---

### Post by Bradtek on 2010-06-04
Try installing it with Play On Linux

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by jcmanley87 on 2010-06-06
ok so I installed wine and i intsatlled Eve....everything went well so far. the game start up is good. The problem now is no text in the EULA. i tried googling it put i can't seem to figure it out. I downloaded the arial font. but what do i do with it from there?

any help would me much appreciated.

---

### Post by Barrucadu on 2010-06-06
Just a warning before you get your hopes up too much: WINE is very good, but far from perfect. Many things work poorly or simply not at all in it.

---

### Post by jcmanley87 on 2010-06-06
ok so i have msttcorefonts in the windows font file for wine. but still no text. i'm so confused now.

---

### Post by TeoBigusGeekus on 2010-06-06
Why do you want text in the eula? Just agree with it and go on.

---

### Post by EssexEagle on 2010-06-06
> **jcmanley87 said:**
> ok so I installed wine and i intsatlled Eve....everything went well so far. the game start up is good. The problem now is no text in the EULA. i tried googling it put i can't seem to figure it out. I downloaded the arial font. but what do i do with it from there?

any help would me much appreciated.

The Eve Online EULA is [here]("http://www.eveonline.com/pnp/eula.asp") if you want to read it.

I have a friend who plays Eve Online in Ubuntu (I assume he uses Wine), so it's definitely possible to get it working.

---

### Post by jcmanley87 on 2010-06-06
that would be cool but without the text it won't scoll down.

---

### Post by ashwinhgtx on 2010-06-06
> **jcmanley87 said:**
> that would be cool but without the text it won't scoll down.

Shouldn't you get a scrollbar even if the text is missing? Post a screen shot if you don't mind.

---

### Post by jcmanley87 on 2010-06-06
ok i figured it out. It works now.

go to this link if you are having troubles too.

[http://www.eve-search.com/thread/1007680/page/1](http://www.eve-search.com/thread/1007680/page/1)

---

