---
title: "Making a new folder in usr?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Omegaham on 2009-09-02
I did a search and couldn't find anything, so my apologies if this has already been answered to death.

Here's what I'm trying to do - [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

It says that I should install Java inside /usr/java. I tried that with the terminal, and it said that no such directory exists. I then tried to create a folder inside usr, and it wouldn't let me. I also tried creating a folder on the desktop and dragging it into usr. Permission denied, cue annoyance.

My question is, how do I make a folder in the command line?

Here's what the terminal looks like now:

[IMG]http://img16.imageshack.us/img16/5735/commandline.png[/IMG]

Thanks in advance.

---

### Post by kwikshot on 2009-09-02
If you wanna make a new directory in /usr/ use:
```
$:cd /usr
$:mkdir Java
```

or

```
$:cd /usr
$:sudo mkdir Java
```

---

### Post by nhasian on 2009-09-02
the command to create a fold is mkdir.  for more info see

```
man mkdir
```

---

### Post by kwikshot on 2009-09-02
"man" is your best friend

---

### Post by Omegaham on 2009-09-02
I know I said thanks in advance, but thanks again. I knew it was something simple like that...

Is there a comprehensive list of commands for this sort of stuff? Edit: Looks like man works. Questions are answered before they're asked on this forum... Crazy.

---

### Post by OffAxis on 2009-09-02
there's also the one in the repos.

```
sudo apt-get install sun-java6-jre
```

---

### Post by nhasian on 2009-09-02
also i looked at the page you were following the instructions.  it doesnt list ubuntu as one of the OSes it applies to.  

you can easily install java with the terminal command:

```
sudo apt-get install sun-java6-jre
```

oops OffAxis beat me to it by seconds...

---

### Post by Omegaham on 2009-09-02
> **nhasian said:**
> also i looked at the page you were following the instructions.  it doesnt list ubuntu as one of the OSes it applies to.  

you can easily install java with the terminal command:

```
sudo apt-get install sun-java6-jre
```oops OffAxis beat me to it by seconds...
That worked as well. You guys are awesome.

Edit: Is there any reason other than humor why Ubuntu is linked with (possibly very caffinated) coffee?

---

### Post by kwikshot on 2009-09-02
Getting it from the repos is just so much easier than any other way

---

### Post by OffAxis on 2009-09-02
> **nhasian said:**
> 

oops OffAxis beat me to it by seconds...

I'm stealthy like that :)

---

### Post by QIII on 2009-09-02
To make the plugin available, also:

```
sudo apt-get install sun-java6-plugin
```Finally, to give preference to Sun over OpenJDK if that is installed, do the following:

```
sudo update-java-alternatives -s java-6-sun
```You can check your version

```
java -version
```

---

### Post by Omegaham on 2009-09-02
One last question - It's currently sitting at the software license agreement page, and I can't get out of it. At the top it's saying that it's "configuring sun-java6-jre," but it hasn't moved for a while. Is there some sort of command that I need to put in to get out of it, or can I just quit out of it?

Edit: Pressed Tab, and it highlighted the "OK" icon. I then pushed enter, and it started installing. I am an idiot.

---

### Post by Omegaham on 2009-09-02
Sorry, I have another question.

The version of Java I have now with Firefox is version 14. The Java website says that I should have version 16. How can I update to the newest one?

---

### Post by QIII on 2009-09-03
I'd hold off on getting the most recent from Java at the moment.  To install it from there, you have to follow a procedure that may be entirely foreign to you at this point.

You can download the file, follow the instructions and install it.  I'm not telling you not to.  But it might be a task you don't want to undertake until you are more familiar with the terminal CLI.

Update 14 has some bugs.  Update 15 came out shortly afterwards as an attempt to fix those, but bugs were reported in that too.

I like to install the most recent version because I do Java development, but Update 14 should be good for most of what you want to do.

Not sure, but last I checked Karmic came with Update 15 in the repositories.

I reluctantly gave my Karmic box back to Windows (hack, cough) for the time being so I could do some Windows (hack, cough) development on it, so I haven't watched to see if they updated to Update 16 yet.

Edit:  Just checked.  It looks like the Karmic repositories have Update 15.  You can add them to your sources list and update your install.  Again, if you are new this might not be something you want to tackle right now.

---

### Post by kansasnoob on 2009-09-03
Being the gui-guy that I am I'd simply install:

```
sudo apt-get install nautilus-gksu
```

Then if you right click, and choose to open as admin the folder preceding the one you want to edit you can do what you wish.

But, if you break it you own it!

EDIT: After seeing Karmic mentioned I should also add that a bug in brasero causes nautilus to crash, so you must remove or downgrade both brasero and libbrasero-media0.

---

