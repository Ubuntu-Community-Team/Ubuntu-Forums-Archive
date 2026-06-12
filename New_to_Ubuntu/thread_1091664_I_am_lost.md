---
title: "I am lost"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by winstont11 on 2009-03-09
I was attempting to upgrade ubuntu and I got advice saying I had to do this...
"you will have to do a fresh install of 8.10, if you don't have your /home on a separate partition then you will have to back-up your data then do the install. when you do the install you can make a separate partition for /home which means that in the future you can reinstall without having to touch any of your personal data."

And I'm trying to make a separate partition and was then advised to go here... [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I went there, but the first step is to go to System-Administration-Partition Editor.  However, when I try to find Partition Editor I am not finding it.  It's not under Preference or Administration.  My current system is Breezy Badger 5.10.  Any suggestions?

---

### Post by bailbath on 2009-03-09
Can you tell us your hardware?
Ian

---

### Post by LowSky on 2009-03-09
> **winstont11 said:**
> 
I went there, but the first step is to go to System-Administration-Partition Editor.  However, when I try to find Partition Editor I am not finding it.  It's not under Preference or Administration.  My current system is Breezy Badger 5.10.  Any suggestions?

it real name is gparted you can still install if you like here is the release that was originally in the repos form 5.10
[http://downloads.sourceforge.net/gparted/gparted-0.0.5.tar.bz2?use_mirror=internap](http://downloads.sourceforge.net/gparted/gparted-0.0.5.tar.bz2?use_mirror=internap)

Otherwise, just backup what data you still need, save it somewhere safe and use the partition editor on the newest Live CD, on the newest versions it will be under System-Administration-Partition Editor

---

### Post by bailbath on 2009-03-09
I have read the other threads you have started on this lets try to keep things in one place from now on it will help all who decide to help you. Nothing personal but it could get confusing!
You would be advised not to upgrade from breezy Badger.
You need to download a install cd.
Before you use the cd backup from breezy any files you want to keep like photo's or whatever to usb pen or external hard drive.
Then use the install cd.
Once we know your hardware we can recommend which version of ubuntu to download.
Thanks
Ian

---

### Post by hyper_ch on 2009-03-09
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by winstont11 on 2009-03-10
Hello, thank you for the advice, I will definitely use more specific titles in the future. 

I have a desktop Compaq computer. And to be honest thats about as much as I know about the hardware. 

I tried accessing the internet from that computer, but for whatever reason it wasn't detecting the network. I called the company that I have my internet service through and they told me that everything seemed to be connected correctly on their end. I went into networks and it said that the ethernet connection was enabled. Could you help with that as well?

---

### Post by snowpine on 2009-03-10
> **winstont11 said:**
> I was attempting to upgrade ubuntu and I got advice saying I had to do this...
"you will have to do a fresh install of 8.10, if you don't have your /home on a separate partition then you will have to back-up your data then do the install. when you do the install you can make a separate partition for /home which means that in the future you can reinstall without having to touch any of your personal data."

And I'm trying to make a separate partition and was then advised to go here... [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I went there, but the first step is to go to System-Administration-Partition Editor.  However, when I try to find Partition Editor I am not finding it.  It's not under Preference or Administration.  My current system is Breezy Badger 5.10.  Any suggestions?

My advice is: Back up any important documents (to a CD, flash drive, external hard drive, etc) and do a fresh install of Ubuntu 8.10. Breezy Badger is no longer supported, so the best advice is to simply replace it and all of its settings (including those in your /home folder) with a fresh install (and then restore important documents from the backup).

Since you aren't willing to research your hardware specs, you'll have to use trial and error to find whether or not 8.10 will run well on your computer. :)

---

### Post by winstont11 on 2009-03-10
> **snowpine said:**
> My advice is: Back up any important documents (to a CD, flash drive, external hard drive, etc) and do a fresh install of Ubuntu 8.10. Breezy Badger is no longer supported, so the best advice is to simply replace it and all of its settings (including those in your /home folder) with a fresh install (and then restore important documents from the backup).

Since you aren't willing to research your hardware specs, you'll have to use trial and error to find whether or not 8.10 will run well on your computer. :)

Ok, I will try that.  I wouldn't say that I am unwilling to do the research, I just don't know how to.  I've had the computer since 2003 or 2004 and no longer have the documents from when I originally purchased it.  Ha, my extent to my research however was looking at the tower and searching through google by typing in "Compaq computers."  I realize that wasn't the best approach, however, that's the only thing I could think of :)

---

### Post by mikechant on 2009-03-10
> I tried accessing the internet from that computer, but for whatever reason it wasn't detecting the network.


Maybe someone can help you diagnose this, but you are running a very old release and the time spent getting the network working just so you can download a new release might be better spent getting an up to date install CD by other means, e.g. using another computer with a working internet connection (Linux, Windows, Mac, whatever) to download an install image (.iso file) and burning it to disk (using the 'burn image' command for whatever CD burner software you have available), or if you can only borrow another PC briefly, you can get a free install CD posted to you. Both options are available from the Ubuntu website.

---

### Post by winstont11 on 2009-03-10
How would I find out what kind of hardware I have?  I remember there using belarc when I had windows.. I tried utilizing that, but it is not system supported.

---

### Post by apolaustic on 2009-03-10
I'm not certain about this (I am quite new to Ubuntu), but I believe that you can discover what hardware you have by entering lspci in the terminal.

Good luck.

---

### Post by kansasnoob on 2009-03-10
The following commands will render the listed results:

```
lspci | grep VGA
```

BTW that's a lower case L. It'll display specific info regarding the graphics card.

```
lspci | grep Audio
```

Basically same as above only regarding sound card.

```
cat /proc/cpuinfo
```

As it says CPU info. Post the full output here if you don't know what you're looking for.

```
cat /proc/meminfo
```

Will tell us how much RAM you have.

---

### Post by winstont11 on 2009-03-10
Thank you!:D  I'm the type of person who needs a break down of the steps the way that you just did.  That was very helpful!  Thanks again :)

---

### Post by kansasnoob on 2009-03-10
Your welcome, but something funny cropped up in my nOObish brain:confused:

I'll probably get laughed at, but I have no idea how to type the separator bar in those first two commands. I've always just used copy-n-paste, but I thought to myself, "self, how do you type the separator bar in those commands if you can't connect to the internet and thus just use copy-n-paste".

So I've been looking and haven't figured it out yet. Guess I'll have to ask and get laughed at!

Also the command:

```
lshw

```

Should show all we'd need to know and much, much more.

---

### Post by parkinrg on 2009-03-10
Kansasnoob, I wont laugh at you  , it just took me 10 mins to find it
"|"   is typed by using the AltGr key and the ¬ key together
The Alt Gr key is on right hand side of the space bar , and ¬  is top left.
I have never had to use that one before either

---

### Post by winstont11 on 2009-03-10
Ok great!  Thanks a bunch.  When I log onto my computer this evening I'll try that and hopefully I will have a response as to what my hardware is.  Thanks again!

---

### Post by winstont11 on 2009-03-10
> **mikechant said:**
> Maybe someone can help you diagnose this, but you are running a very old release and the time spent getting the network working just so you can download a new release might be better spent getting an up to date install CD by other means, e.g. using another computer with a working internet connection (Linux, Windows, Mac, whatever) to download an install image (.iso file) and burning it to disk (using the 'burn image' command for whatever CD burner software you have available), or if you can only borrow another PC briefly, you can get a free install CD posted to you. Both options are available from the Ubuntu website.

I didn't realize until after I placed the order for the updated install CD that it would take a few weeks to receive it.  Unfortunately, the only time I can gain access to the internet is when I am at work.  I'm not able to burn a CD so that I can upgrade ubuntu that way.  I'm still having issues logging onto the internet at home.  Does anyone know what I can do to gain access?  Thanks

---

### Post by kansasnoob on 2009-03-10
What did you find out about the hardware?

If you're in the US I'd be glad to drop you a disc in the mail, but I want to know I'm sending you a disc that should work with your hardware.

You can also find a number of vendors at Distrowatch:

[http://distrowatch.com/](http://distrowatch.com/)

I like:

[http://www.linuxcdshop.com/](http://www.linuxcdshop.com/)

---

### Post by winstont11 on 2009-03-10
Hey I am in the US.  I haven't found out what my hardware is because I'm not home yet.  I kind of have to go back and forth because I only have internet access at work.  When I get home later tonight I'll be able to find out what my hardware is and then tomorrow I'll be able to let you know :) It just thought it would be less complicated if I could gain internet access through my home CP and report what I found later tonight.

---

### Post by winstont11 on 2009-03-10
Again, to everyone who has offered advice, I appreciate the help :D

---

### Post by avtolle on 2009-03-10
> **kansasnoob said:**
> Your welcome, but something funny cropped up in my nOObish brain:confused:

I'll probably get laughed at, but I have no idea how to type the separator bar in those first two commands. I've always just used copy-n-paste, but I thought to myself, "self, how do you type the separator bar in those commands if you can't connect to the internet and thus just use copy-n-paste".

So I've been looking and haven't figured it out yet. Guess I'll have to ask and get laughed at!

Also the command:

```
lshw

```Should show all we'd need to know and much, much more.
The "separator bar" is called a pipe. On a standard keyboard, it is typed by shifting the backslash key, located at the end of the row of keys located above the Enter key.

---

