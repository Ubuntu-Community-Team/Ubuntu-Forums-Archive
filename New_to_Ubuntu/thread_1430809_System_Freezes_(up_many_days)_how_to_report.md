---
title: "System Freezes (up many days) how to report?"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by penguinv on 2010-03-15
**My computer:**
I have some AMD computer with 1.2 G of Ram AFAIK, an old one with AGP-PCI, with Ubuntu 9.10 upgraded from 9.04 and I have installed all the updates. I have a second hard drive just for data. I am using the on m-board video driver.
This computer uses up all the ram often so I keep system monitor running to observe. I might learn something. YouTube in chrome will often go silent, then I open Firefox and it plays fine.

**My problem:**
What was running.I had xchat, gedit, a couple of chrome browser windows (one with 5 tabs, one with 20 tabs). One tab had a finished TED-talk, otherwise it was mostly craigslist and Amazon shopping, for a pressure cooker. Some pictures. And the system monitor.

This is the third time it has frozen. The first time I just took it as weird, "Linux doesnt do that?" The next two times I was typing text, the second in a text box and the third in Yahoo compose. (Why do I use Yahoo instead of Gmail? If I had been n gmail I'd still have my draft."

**What should I do when it happens?:**
What I did do is turn off the power and then reboot.

This is what I got from the internet.
2, 3, or 4 here  [http://maketecheasier.com/4-ways-to-get-yourself-out-of-a-ubuntu-crash/2008/09/01](http://maketecheasier.com/4-ways-to-get-yourself-out-of-a-ubuntu-crash/2008/09/01)
   2 is  ‘Ctrl + Alt + Backspace‘.
   3 is MagicSysKey ‘Alt + SysRq + K’ (magic=Alt + SysRq/prtscr)
   4 is " (hold it) r then e then i then s then u then b 
       (Text shows caps it's likely they mean just hit the key)

I have seen 4 on other websites last week but I didnt write it down. A letter from 2007 [http://linux.derkeiler.com/Mailing-Lists/Debian/2007-05/msg03706.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2007-05/msg03706.html) gives a longer sequence. "Pressing Alt-SysRq on an i386, (HOLD I ADD) followed by one
of the keys r 0 k e i s u b, does the magic." and then explains why.

**How can I help with the bugfix?:**
Now I am going to print out the recover information I saw on a webpage. I suppose it works for Ubuntu. But which? My choices;

Now I just booted up after a hard reboot. What can I recover to tell The Bug Fixers what happened? I looked at the "How to report" page and it was very-much-way beyond me. It included lots of incomprehensible and unexplained terms or function names or perhaps swearwords. That's typical on help pages in Ubuntu. Someday perhaps I'll write a better one.

Now I know to look and see if the capskey light is flashing. I didnt look any of the times. 

**Why this is a new posting:**
The reason I made this a separate post is because my situation is different. On the other thread "Ubuntu froze, please help", all of the posters had immediate freeze problems, at least in the first 20 minutes after being booted up. 

My computer system is fine for days. My understanding is that linux can be left on and on and that it doesn't "get old" like Windows or Firefox on Windows and need to be rebooted to clear memory or registers or something else.




Thanks for reading all this.
And while you are waiting:     :popcorn:

---

### Post by sandyd on 2010-03-15
> **penguinv said:**
> **My computer:**
I have some AMD computer with 1.2 G of Ram AFAIK, an old one with AGP-PCI, with Ubuntu 9.10 upgraded from 9.04 and I have installed all the updates. I have a second hard drive just for data. I am using the on m-board video driver.
This computer uses up all the ram often so I keep system monitor running to observe. I might learn something. YouTube in chrome will often go silent, then I open Firefox and it plays fine.

**My problem:**
What was running.I had xchat, gedit, a couple of chrome browser windows (one with 5 tabs, one with 20 tabs). One tab had a finished TED-talk, otherwise it was mostly craigslist and Amazon shopping, for a pressure cooker. Some pictures. And the system monitor.

This is the third time it has frozen. The first time I just took it as weird, "Linux doesnt do that?" The next two times I was typing text, the second in a text box and the third in Yahoo compose. (Why do I use Yahoo instead of Gmail? If I had been n gmail I'd still have my draft."

**What should I do when it happens?:**
What I did do is turn off the power and then reboot.

This is what I got from the internet.
2, 3, or 4 here  [http://maketecheasier.com/4-ways-to-get-yourself-out-of-a-ubuntu-crash/2008/09/01](http://maketecheasier.com/4-ways-to-get-yourself-out-of-a-ubuntu-crash/2008/09/01)
   2 is  ‘Ctrl + Alt + Backspace‘.
   3 is MagicSysKey ‘Alt + SysRq + K’ (magic=Alt + SysRq/prtscr)
   4 is " (hold it) r then e then i then s then u then b 
       (Text shows caps it's likely they mean just hit the key)

I have seen 4 on other websites last week but I didnt write it down. A letter from 2007 [http://linux.derkeiler.com/Mailing-Lists/Debian/2007-05/msg03706.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2007-05/msg03706.html) gives a longer sequence. "Pressing Alt-SysRq on an i386, (HOLD I ADD) followed by one
of the keys r 0 k e i s u b, does the magic." and then explains why.

**How can I help with the bugfix?:**
Now I am going to print out the recover information I saw on a webpage. I suppose it works for Ubuntu. But which? My choices;

Now I just booted up after a hard reboot. What can I recover to tell The Bug Fixers what happened? I looked at the "How to report" page and it was very-much-way beyond me. It included lots of incomprehensible and unexplained terms or function names or perhaps swearwords. That's typical on help pages in Ubuntu. Someday perhaps I'll write a better one.

Now I know to look and see if the capskey light is flashing. I didnt look any of the times. 

**Why this is a new posting:**
The reason I made this a separate post is because my situation is different. On the other thread "Ubuntu froze, please help", all of the posters had immediate freeze problems, at least in the first 20 minutes after being booted up. 

My computer system is fine for days. My understanding is that linux can be left on and on and that it doesn't "get old" like Windows or Firefox on Windows and need to be rebooted to clear memory or registers or something else.




Thanks for reading all this.
And while you are waiting:     :popcorn:
You can post the bug on bugs.launchpad.net

Then wait for them to mark it for incomplete and theyll ask you for the stuff they need.

But then again, the less work they do the better... so you might as well attach the stuff they need in the start...

Youll want to attach these files to the buglog, and check back to it every once in a while

There are several versions of the logs im talking about. this is because the logs are archived once they reach a certain size. You will need to open each log (even the oens that end in "gz" if the crash took place between the start/end times of the log, that is the one to attach.

For example, if your computer locked up at 2:30 this morning, and you found a log with the first entry dated march 15th, 1:00:00, and the last entry march 15th, 9:00:00, you would upload that particular log. It is important that you upload the correct log, otherwise you are wasting the developer's time.

You will want to file the bug on the "Ubuntu" project btw.
 ```

/var/log/syslog
/var/log/dmesg
/var/log/Xorg.0.log #could be xorg that locked up

```
you will also want to post your hardware through```
lspci
```

---

### Post by penguinv on 2010-03-16
> **carlee said:**
> You can post the bug on bugs.launchpad.net
...
There are several versions of the logs im talking about. this is because the logs are archived once they reach a certain size. You will need to open each log (even the oens that end in "gz" if the crash took place between the start/end times of the log, that is the one to attach.


tinyogen@tinyogen-desktop:~$ ls -l /var/log/message* 
-rw-r----- 1 syslog adm   211471 2010-03-16 16:24 /var/log/messages
-rw-r----- 1 syslog adm 19873017 2010-03-14 07:42 /var/log/messages.1
-rw-r----- 1 syslog adm    32600 2010-03-07 07:56 /var/log/messages.2.gz
-rw-r----- 1 syslog adm    62353 2010-02-28 08:16 /var/log/messages.3.gz
-rw-r----- 1 syslog adm    68118 2010-02-21 21:09 /var/log/messages.4.gz

For instance my computer has crashed 3 times today 2010-03-16

so then I just need to send one file and skip the past crashes.
...

> You will want to file the bug on the "Ubuntu" project btw.
 ```

/var/log/syslog
/var/log/dmesg
/var/log/Xorg.0.log #could be xorg that locked up

```
you will also want to post your hardware through```
lspci
```

-rw-r----- 1 syslog adm 216754 2010-03-16 16:24 /var/log/syslog
-rw-r----- 1 root adm 32436 2010-03-16 09:24 /var/log/dmesg
-rw-r--r-- 1 root root 44690 2010-03-16 16:24 /var/log/Xorg.0.log


your last para was unclear to me. I infer this:
1. I should include these three logs.
(and messages also I presume plus a directory of /var/log)
2. And file it on the Ubuntu project, which I guess is a section of the bugs.launchpad.net
-- I found that ubuntu > "too many matches, please narrow"
-- ubuntu 9.10 was not found. I'm reading the Launchpadhelp
-- I capitalized it and got "There is no project named 'Ubuntu' registered in Launchpad"  *I'm doing my best.*
-- but I see this 
	
#539973 Konqueror fails to load web page correctly
in Ubuntu, reported 11 minutes ago by Luke

which sure looks like Ubuntu so I'm calling it Ubuntu anyway.
I looked up What is a project and it didnt say much except it marks who might be affected by it.

Your search query "how to report a bug" didn't return any results.

[B]I'm writing as I'm doing, making this a lab notebook.  :)
Hope it will help others.[/B]

[https://help.launchpad.net/](https://help.launchpad.net/)   This helps. I need to make an account.

It was not clear at all what to do.
-----------------------------------

So I went reading and read mention of #ubuntu, and thought that would be a good things to do.

I'm interested in fixing my system even more than reporting a bug. Maybe I was not clear.

Well that took a while and I'm only in the middle. I copied all of the conversation to a file and put it off to another day. 

Between mentions of fsck and pastebinit and memtest and make more freespace on my HD (that I did, now I have 2.1G free on a 10G drive) I am ready to take a break. 

I'm not letting anything be unsaved though so it's time to post this now.

Thanks for reading this and for any help.


I bet you a bean that flash is part of the problem!

And while you are waiting...   *[FONT="Comic Sans MS"](A cup of espresso)[/FONT]*
                                Where is the cup smilie?

---

