---
title: "icon shortcut for running terminal command"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by i2yu on 2009-07-25
Hello,

I made a shortcut to Terminal on my Desktop. I have already edited its command from

```
gnome-terminal
```

to

```
gnome-terminal --full-screen
```

Now I would also like to immediately run a few terminal commands everytime it opens. For example, the "date" and the "cal" command. To clarify: I don't want a Terminal alias that will execute date and cal. I want an icon on my desktop that opens the Terminal in Fullscreen mode and automatically runs one or more commands.

When I  google or forum-search for this, I ALWAYS get threads about how to make shortcuts in the terminal itself (--> alias command), so please forgive me, if this question somewhere is answered already.

TIA and have a nice weekend,
Ryu

---

### Post by drs305 on 2009-07-25
Here is one way to do it.

On my setup, newly opened gnome-terminals using the "-x" switch run but then immediately close the terminal window. So first we must create a terminal profile which keeps the terminal window open upon completion of the command(s).

Open a terminal, then:
Edit > Profiles > New, Profile Name: "StayOpen".
In the *Title & Command* tab, at the bottom, "When command exits": Select "Hold the terminal open".
Close

Now the command to run in your shortcut is:

> gnome-terminal --window-with-profile=StayOpen -x bash -l -c "date;cal;bash"


---

### Post by i2yu on 2009-07-25
Yes, I can confirm that this works on ubuntu 9.04. I added --full-screen to the command, and that's fine, too.

Thank you very much for the quick answer! :)

I'm just curious:
by entering "man bash" in the console I found that -c is for the quotes, which are necessary because it's two command, but what is -l for? By entering "man bash" in the terminal, I found this:
> 
 -l        Make bash act as if it  had  been  invoked  as  a
                 login shell (see INVOCATION below).


but I don't understand it (what's a login shell?).
and also... where do you find information like this? I know I'm still quite new to Ubuntu, but I find that I never guess right, I always must ask in the forums (for example, I tried "-run date -run cal" oder "-run date & cal", but I'd never have found the actual solution).
Do you simply read the huge bash manual (that thing has several thousand lines)?

anyway, it works and I'm happy - thanks again, drs305! :)

---

### Post by drs305 on 2009-07-25
The "--fullscreen" isn't necessary. I just included it because you said you changed it to that in the first post. You can also set the size and location of the terminal by adding another switch, if you want to get fancy:
> --geometry=150x45+30+50
This would open a terminal 150 characters wide and 45 lines deep, offset 30 pixels from the top and 50 from the left.

From reading the man page for "bash", I added the login shell switch to include any variables you may have in your configuration files (.bashrc, paths, etc). It may have defaulted to that anyway even without the switch but I wanted to cover the possibility that it wouldn't.

As you saw from the sequence of PMs I sent you, I 'solved' this by trying various options, and then reading up on the particular commands and switches. I usually refer to the man pages, then do searches for clarification and examples.

Although your question was a bit different and I didn't find anything similar in the Ubuntu forums, most of the questions asked here have been asked before. The Search button at the top of the page is very helpful, especially the Advanced Search option, which you can use to narrow the search (for instance, when troubleshooting a system problem, I usually start with posts from the past month since these have the best chance of matching a current problem).

I keep an 'advanced search' shortcut for searching the Ubuntu forums in my panel:
[http://www.google.com/advanced_search?q=site:ubuntuforums.org&hl=en&lr=&tbo=1&num=30&tbs=qdr:m](http://www.google.com/advanced_search?q=site:ubuntuforums.org&hl=en&lr=&tbo=1&num=30&tbs=qdr:m)

Here is a good search result (not from the Ubuntu forums) for the Login Shell:
[http://learnlinux.tsf.org.za/courses/build/shell-scripting/ch02s02.html]("http://learnlinux.tsf.org.za/courses/build/shell-scripting/ch02s02.html")

---

### Post by dberg on 2010-01-08
I know I'm kind of digging up an old thread here, but I have a question that is basically a slight modification of what is happening here.

I would like to take this:
> gnome-terminal --window-with-profile=StayOpen -x bash -l -c "date;cal;bash" 

and use it to execute the command:
```
date "+%j"
```

I can't seem to figure out what combination of characters is required to achieve this.

Thanks in advance.

---

### Post by drs305 on 2010-01-08
> **dberg said:**
> I would like to take this:
and use it to execute the command:
```
date "+%j"
```
I can't seem to figure out what combination of characters is required to achieve this.
Thanks in advance.

I think this is what you want. It opens a new terminal, and for today produces a result of "008".
```

gnome-terminal --window-with-profile=StayOpen -x bash -l -c "date +%j;bash"

```

---

### Post by bodhi.zazen on 2010-01-08
You can put those commands in .bashrc =)

[img]http://bodhizazen.net/img/Terminal2.png[/img]

link to that bashrc

[http://bodhizazen.net/adblock/bashrc](http://bodhizazen.net/adblock/bashrc)

Or for those with attention to detail, the zshrc

[http://bodhizazen.net/adblock/zshrc](http://bodhizazen.net/adblock/zshrc)

(if you use those bashrc or zshrc, take teh time to read the (brief) comments at the top or modify them as I use a few apps such as most (color to the man pages) and display-dhammapada).

---

### Post by Sir Jasper on 2010-01-08
Hi,

Opening a Terminal and typing
cal 2010
will show all the current year.

Alt + F6 will expand vertically.

My regards

---

### Post by dberg on 2010-01-08
> **drs305 said:**
> I think this is what you want. It opens a new terminal, and for today produces a result of "008".
```

gnome-terminal --window-with-profile=StayOpen -x bash -l -c "date +%j;bash"

```
For some reason this isn't working. It just returns a blank line followed by the command entry prompt.

---

### Post by drs305 on 2010-01-08
> **dberg said:**
> For some reason this isn't working. It just returns a blank line followed by the command entry prompt.

Edit: I thought maybe it was because you didn't have a "Stay.Open" profile but it seems to work for me regardless. You aren't using the "curvy" quotes are you?

How about if you just type:  date +%j

---

### Post by dberg on 2010-01-08
I copied exactly what you typed and pasted it into the Launcher. Typing the command in the terminal produces the expected result.

Another thing I noticed is when closing the terminal produced by the Launcher I get the following message:
> There is still a process running in this terminal. Closing the terminal will kill it.

---

### Post by kenlyle on 2010-11-10
> **drs305 said:**
> Here is one way to do it.


Superb!  As the OP said, this tip was hard to find, but worth the search.

Thanks!

---

