---
title: "Linux-Like Terminal in Windows"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-11-23
I know about Cygwin, but I was wondering if it is possible to install a Linux-like environment based solely on terminal use; basically to be able to run Linux commands in Windows. Does anyone know of a way to do this? I would really appreciate this as I am fluent in *nix commands then Windows.

---

### Post by UnknownFear on 2010-11-23
Or, better yet, how can I setup Cygwin so it starts in the default Windows path (ie. C:\Documents\Users\<user-name>) so I can actually use Cygwin instead of CMD to make files, delete, etc. Thanks!!

---

### Post by ModelM on 2010-11-23
Ages ago (like back in the last century) there was a "unix toolkit" for ms-dos which could be found for download on many of the old bulletin boards. It contained some of the most commonly used unix commands like ls, grep, more - and more that I can't remember - compiled to run under ms-dos. They worked pretty well & even included some command-line switches for some of the commands.

I don't know if these would even work on a windows system today - this was back in the old dos 3-5 era. But if you want to try to track it down & try it there is probably a copy of the zip file out there somewhere in the interweb.

---

### Post by UnknownFear on 2010-11-23
@ModelM that sounds rather confusing, sorry. However, would you know how I could set up Cygwin to access Windows files and directories?

---

### Post by DaithiF on 2010-11-23
Hi, 
cygwin gives you (amongst other things) a bash shell.  You access your c:\ etc drives as /cygdrive/c 

what else do you need, or am I misunderstanding what you want to do?

---

### Post by UnknownFear on 2010-11-23
I've used Cygwin before, but when I used it, I was not sure how to actually navigate it into Windows. For example, it started in the cygwin folder, but how could I default it to the Windows cmd default folder, such as my documents? I would use Cygwin if I knew how to do this.

---

### Post by Joe of loath on 2010-11-23
[http://gnuwin32.sourceforge.net/](http://gnuwin32.sourceforge.net/)

---

### Post by dtfinch on 2010-11-23
You could add a cd to the end of .bash_profile in your cygwin home directory. On mine adding "cd /cygdrive/c/Documents\ and\ Settings/davidf/" works. But "~" still points to the cygwin home unfortunately.

edit: You can change your cygwin home directory by editing /etc/passwd, but the cygwin FAQ recommends against using paths that contain spaces.

To make it more linux-like, I use puttycyg instead of the built-in cygwin terminal (which uses the fixed-width Windows terminal).
[http://code.google.com/p/puttycyg/](http://code.google.com/p/puttycyg/)

---

### Post by UnknownFear on 2010-11-23
@dtfinch Thanks for the info, I'll try both of those when I get home from school.

---

### Post by beew on 2010-11-23
-1 to cygwin

I have had a much easier time actually installing Linux (Ubuntu and a few other distros) than to make cygwin to work. I tried that before I went all the way with Ubuntu and I found that it was kind of broken and buggy. There were always something missing. The manual is total gibberish to me. Maybe I was just inept. And oh, I could never make the drop down menu in X windows to stay, the moment I moved the cursor it disappeared.

To my mind cygwin is like the evil twin of WINE from the parallel universe except it is much bigger.

---

### Post by UnknownFear on 2010-11-23
@beew If it makes you feel better, I also run Linux virtually inside Windows, but I would like to give Windows a Linux-like environment to be able to use *nix commands inside Windows, as opposed to the Windows commands, which I don't like in the least.

---

### Post by anewguy on 2010-11-23
Just get MinGW and Msys - they're free and provide the environment you are looking for.  I use them for cross-platform application development - I delevop the program in ubuntu with gtk, then move it to windows and use MinGW and Msys to compile them there with unix-like scripts.

[http://www.mingw.org/]("http://www.mingw.org/")

Dave ;)

---

### Post by DaithiF on 2010-11-23
cygwin is fine for bash & the common gnu command line tools.  I've been using it for years on work machines where i'm stuck with windows.  The bash experience is equivalent to a linux machine.

---

### Post by Joeb454 on 2010-11-23
Cygwin (mentioned above) was recommended to students running Windows in our first year at university, as it provided the familiar bash experience to that at the university, and included gcc (if selected).

I usually opt for cygwin if I need a bash shell on windows. I don't have much experience with the other suggestions though, so I couldn't comment on those.

---

### Post by beew on 2010-11-23
Well now that I am stuck with a Windows partition in my dual boot that I cannot removed with gparted  I may put it to use by giving cgywin another chance. Hopefully it works better this time.

---

### Post by UnknownFear on 2010-11-23
> **Joeb454 said:**
> Cygwin (mentioned above) was recommended to students running Windows in our first year at university, as it provided the familiar bash experience to that at the university, and included gcc (if selected).

I'm currently installing Cygwin. Didn't know what all I needed, so I just selected to install everything lol. Hopefully this will work the way I want it.

Do you know if it is possible to access all Windows folders and files inside Cygwin, instead of just the Cygwin folder?

---

### Post by anewguy on 2010-11-23
MinGW and Msys, as I understand them, are the portions of Cygwin that provide what you are asking about.  MinGW provides the tools, including the compilers, etc., while Msys provides the bash command line tools.  That's why I recommended them.


Dave ;)

---

### Post by andrew.46 on 2010-11-24
Hi Dave,

> **anewguy said:**
> MinGW and Msys, as I understand them, are the portions of Cygwin that provide what you are asking about.

I have used MinGW32 and MSYS for some time now and I would definitely join with you in recommending them :). Mind you they are actually not part of Cygwin... Screenshot shows the native windows terminal rather than MSYS, I prefer it to MSYS for the most part.

Andrew

---

### Post by DaithiF on 2010-11-24
> **UnknownFear said:**
> Do you know if it is possible to access all Windows folders and files inside Cygwin, instead of just the Cygwin folder?

of course, there wouldn't be much point to it otherwise :)

---

### Post by HermanAB on 2010-11-24
```
$ cd /cygdrive/c
$ ls
```

---

### Post by SecretCode on 2010-11-24
> **Joe of loath said:**
> [http://gnuwin32.sourceforge.net/](http://gnuwin32.sourceforge.net/)

This is the way to go.

90% of the commands you use in Linux shells are actually GNU commands. gnuwin32 provides a good chunk of GNU on windows.

---

