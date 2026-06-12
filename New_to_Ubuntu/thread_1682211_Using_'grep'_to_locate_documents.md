---
title: "Using 'grep' to locate documents"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by JuliaHenson on 2011-02-05
[SIZE=5]Dear Sirs,
I am an end-user new to Linux and also have a slight brain injury.  I thought I had a simple question:
I need to locate the document in which I used a certain word.  I had been told that I should use the 'grep' command to do this, but all the places I looked up were all 'greek to me'.  I need to find this document. Can someone tell me how?
My system is Ubuntu 11.04 Natty Narwhal.
I'm sorry, but my brain simply cannot function well sometimes and I need to know exactly what to do to find my document. I have done several searches in a couple sites and all of the results are totally incomprehensible to me.
Can someone help me, please?
Thank you,
Julia Henson
[/SIZE]

---

### Post by cogier on 2011-02-05
[SIZE="5"]Can I suggest you look here for advice on finding files. [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfinding.html]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfinding.html"). If this is no good use Google or you favorite search engine to look for more help. I used **locate files in linux** and found the above.

**Grep** is used to find specific text in text returned by other commands and again if you are interested use a search engine to get yourself more details.[/SIZE]

---

### Post by TeoBigusGeekus on 2011-02-05
[SIZE="6"]```
grep -r "wordurlookingfor" /path/to/folder/to/look/
```[/SIZE]

---

### Post by bioterror on 2011-02-05
> **cogier said:**
> [SIZE="5"]Can I suggest you look here for advice on finding files. [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfinding.html]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfinding.html"). If this is no good use Google or you favorite search engine to look for more help. I used **locate files in linux** and found the above.

**Grep** is used to find specific text in text returned by other commands and again if you are interested use a search engine to get yourself more details.[/SIZE]

Seems like your advices didnt give much help in finding a certain document which contains a word.

Something that's close to this is [Beagle]("https://help.ubuntu.com/community/Beagle"), an indexing search.

---

### Post by JuliaHenson on 2011-02-05
Thank you for the responses.  I shall try what you suggest.  At the moment, my computer tech suggested a particular grep command, which I used and became unable to use my computer for anything, although I have 4 processors.  I lost the bottom menu line - well, he finally gave me a command to put in to restart the computer.
It appears to be a given that Linux is not for end-users, but I have no choice in this, since I cannot afford Windows any more.
Right now, I'm so confused in my brain that I can't do anything else at the moment.  I will try again when I might be able to understand what I am reading.
Another thing is, I gather, not to use the 'grep' command unless you are closing down everything else and going to bed so it can find the document.  This is not a good option for end-users like me.  I used to use Desktop Search engines with wonderful results - but Linux makes all that unavailable.  I will have to keep trying and hope that within a year or two, I will be able to do what were simple tasks to do in Windows.  I am not a programmer and it appears that Linux is only for programmers. 
However, I appreciate your response and when my brain can do it, I will follow through on your suggestions.
I do appreciate it - it's just so overwhelming right now!
Thank you,
Julia

---

### Post by DiSTORT3D on 2011-02-05
*OMG, where are my readingglasses*

---

### Post by BicyclerBoy on 2011-02-05
You could try the **search for files** option in the Gnome desktop menu...
(Ubuntu 10.04)

Top menu bar:
**Places**
**Search for files....**

Try not to point this command (& grep) at the top of the file system.
Try to look/search into one folder.

The windows desktop search tool works well because it is an indexed database search engine. This makes it very fast to respond but it still takes hours to run the first time it is used.
I think Beagle is a tool like this for Linux..

---

### Post by quadproc on 2011-02-05
> **JuliaHenson said:**
> 
It appears to be a given that Linux is not for end-users, but I have no choice in this, since I cannot afford Windows any more.

Linux is very similar to Unix, an operating system which was designed by programmers for programmers.  Unix requires a lot of knowledge.  However, Ubuntu has taken most of the work and most of the need to know out of the Linux environment.

Ubuntu is different than Windows; it wasn't intended to be a replacement for Windows.  You do need to learn some things to be able to use it effectively.  It may seem like a daunting task but after a short while you will become comfortable with it.
> 
Another thing is, I gather, not to use the 'grep' command unless you are closing down everything else and going to bed so it can find the document.  This is not a good option for end-users like me.It sounds like you used grep to try to search every file on the computer.  There are a couple of points to make about this:
 First, search the most likely locations first.  For example, if you think that your target file might be in a directory (i.e., a folder) named Documents then try code such as this:
```
cd ~/Documents
nice -n  10 grep "thedesiredword" *  | more

```Second, start this task in its own terminal.  That way, you can let it run without interfering with other things that you may wish to do.

Please note the use of the _nice_ command in the example. _ Nice_ changes the priority of the task to be run; a value of 10 decreases its priority by 10 points; this is halfway to as low as it can be set.  Using _nice_ will reduce the impact of the search on other tasks and processes.

quadproc

---

### Post by Old *ix Geek on 2011-02-06
Julia, I'd like to point out that we're not all 'sirs' around here. ):P

Some of your comments really seem odd to me. For example:
> my computer tech suggested a particular grep command, which I used and became unable to use my computer for anything, although I have 4 processors.  I lost the bottom menu line - well, he finally gave me a command to put in to restart the computer.Strange. I've been using grep for over 25 years and have never seen anything like that! Sounds much more like a 'computer tech' problem than a Linux problem.
> It appears to be a given that Linux is not for end-usersYou know, 20 years ago, or even 10, I could have agreed with you on this, but not now. (K)Ubuntu is extremely easy to use and user friendly. I say this all the time, but it's true--if my 80+ year old mother can use Kubuntu day in and day out, never touching--or NEEDING to touch--a command line, ANYONE can use it. Your assertion that it's not for end users really makes me wonder.
> Right now, I'm so confused in my brain that I can't do anything else at the moment.  I will try again when I might be able to understand what I am reading.I feel for you. I had a brain tumor removed via large craniotomy a year and a half ago and have had severe brain fog and confusion ever since. Not fun.
> Another thing is, I gather, not to use the 'grep' command unless you are closing down everything else and going to bed so it can find the document.  This is not a good option for end-users like me.  I used to use Desktop Search engines with wonderful results - but Linux makes all that unavailable.  I will have to keep trying and hope that within a year or two, I will be able to do what were simple tasks to do in Windows.I'm scratching my head. I use nothing but Linux--you couldn't PAY me to touch a windoze computer--and I simply don't have the issues you're talking about. I'm really wondering if you perhaps have a bad installation, or if you're not using the best desktop environment for you. Have you tried KDE/Kubuntu? It doesn't get any easier or more user friendly than that! My mother, who used windoze for years, made the transition to KDE effortlessly--and appreciates the much faster speed, the stability, never having to shutdown [for silly things like installing software], and all the other stuff that made using windoze such a miserable headache.

As for your actual question, do you store all your documents in the same location? If so, that will make searching easier. Regardless, finding the file should not be a big deal! Work with us and we'll get it found, okay?

---

