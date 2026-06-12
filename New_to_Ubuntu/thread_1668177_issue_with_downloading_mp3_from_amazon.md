---
title: "issue with downloading mp3 from amazon"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by newlinuxlady on 2011-01-16
Hi friends- this is my first post!  I have some questions- but I will start with this one.  I just purchased an mp3 from amazon and when I downloaded it- it is an .amz extension (cute- for amazon- short for).  It is only gobblygoock on a word doc- no mp3.  I then downloaded the amazon downloader software which does work with linux- but only 32 bit to my understanding.  When I downloaded it- it did not complete the download and it says the status message:

Error: Dependency is not satisfiable: libboost-filesystem1.34.1

Can anyone help with how I can download the amazon downloader or if it is possible and compatible with amazon and the mp3 or if I should be able to download the mp3 in another way?  I have contacted Amazon concerning the issue and they have already re-offered the mp3 for me to download- so I want to get it right the second time if I can.

They don't know it is a Linux system- only that the amazon downloader didn't work.

All I want is the have the mp3 work on linux so I can listen to it.

Thanks in advance for your help.  Best, Liane

---

### Post by Perfect Storm on 2011-01-16
libboost 1.34 is an old version which is not available in newer version of Ubuntu.

But you can download it manually here: [http://packages.ubuntu.com/search?keywords=libboost-filesystem1.34.1&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=libboost-filesystem1.34.1&searchon=names&suite=karmic&section=all)

It is possible to to use 32bit software in 64-bit but it sometimes require a little more work in rare occasion.

---

### Post by newlinuxlady on 2011-01-16
Thank you for the feedback- I did the download in your message and it went through- but when I tried to download the amazon mp3 downloader after it- now this error message comes up:


Error: Dependency is not satisfiable: libboost-regex1.34.1


How can I get the mp3?  What else do I have to download to get the downloader to work or another way to get the mp3 player?

---

### Post by Perfect Storm on 2011-01-16
There's properly a bunch of dependencies that needs to be sorted out. You can find all the libboost 1.34 here: [http://packages.ubuntu.com/source/karmic/boost](http://packages.ubuntu.com/source/karmic/boost)

---

### Post by kittkatt on 2011-01-16
Yikes, congrats for taking the dive into Linux. I don't use the amazon downloader but did some digging and [this link should solve your problem]("http://ubuntuforums.org/showthread.php?t=1478214").  If you ever get stuck again, keep posting in the forums, you're doing great!

To access the terminal, go to the menu button 
Application > Accessories > Terminal

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

^^ This is the website that I used when I was starting out.  Its awesome, hope you find it useful too.

---

### Post by newlinuxlady on 2011-01-16
Hi KittKatt- thank you for your feedback- I just ran the terminal with requested commands and now it shows this:

FINISHED --2011-01-16 00:14:59--
Downloaded: 7 files, 7.4M in 48s (158 KB/s)
goodwill@Multimedia1:~/old_boost$ sudo dpkg -i *.deb
[sudo] password for goodwill:

but the cursor is blinking very slowly and when I try and type the password- it does nothing and when I tried to close the terminal since I cant do anything- is says if I close it it will kill the actions just completed.

What to do now?

I am totally a fish out of water working in linux- but I am giving it a go.  It is hard for a complete newbie- so I will be posting questions for sure.

---

### Post by Perfect Storm on 2011-01-16
It's a security thing that you can't see the typing of the pass word. Just type the password and hit <enter> afterwards.

---

### Post by kittkatt on 2011-01-16
Yes, I know its tough at the start.  I felt like trying to write out an explanation of why your problem is happening but didn't want to overwhelm you with info.

Anyway, anytime it asks you for a sudo password, you type in the same password that you used when you installed Ubuntu (or try the one you log on with).  It will not spell out on the terminal b/c of safety reasons (other people perhaps looking at your screen) but after you press "enter" it will register.

---

### Post by newlinuxlady on 2011-01-16
thanks I was able to put in the password and it worked- but now it has this message in terminal:


Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
goodwill@Multimedia1:~/old_boost$ 

what do I enter in now?  is has the blinking cursor.

Please help.

---

### Post by Perfect Storm on 2011-01-16
Another option to download and hear music on Ubuntu is Ubuntu's build-in music-shop with Ubuntu One. 
If you open Ryhtmbox music Player in Ubuntu, you'll see something called Ubuntu One.

The music are DRM free.


More about Ubuntu One: [https://one.ubuntu.com/](https://one.ubuntu.com/)

> thanks I was able to put in the password and it worked- but now it has this message in terminal:


Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
goodwill@Multimedia1:~/old_boost$ 

what do I enter in now? is has the blinking cursor.


It means it's done. It have installed the libraries. Try now install Amazon.

---

### Post by newlinuxlady on 2011-01-16
I believe I HAVE to use the amazon downloader since I purchased the mp3 through amazon.

---

### Post by Perfect Storm on 2011-01-16
> **newlinuxlady said:**
> I believe I HAVE to use the amazon downloader since I purchased the mp3 through amazon.

Yes.

EDIT: check my previous post, as I have edited it.

---

### Post by kittkatt on 2011-01-16
> what do I enter in now? is has the blinking cursor.


Double click the amazon downloader program file that you were originally having problems with.  It might ask you for a sudo password, enter the same one that you used previously.  The amazon downloader program should then install and run and you should be home free!

---

### Post by newlinuxlady on 2011-01-16
THANK YOU- I was now finally about to download the amazon downloader successful after the terminal run/command.

You both have been VERY helpful.  Artifical- had I completed the other downloads from the Library- should have it worked then too?  

I have another media question- how can you stream instantly netflix movies on the linux?  What application/software download works/makes it compatible?  So far- it is not working since Netflix does not support.

Look forward to hearing from you.  Thank you, Liane

PS- now I have to see if I can get the mp3 to download!  Wish me luck!

---

### Post by Perfect Storm on 2011-01-16
> You both have been VERY helpful. Artifical- had I completed the other downloads from the Library- should have it worked then too?

The way I did it was simple point'n'click. The link that was given to you was through commands (+ the whole solution). But in the end the outcome will be the same.

---

### Post by Perfect Storm on 2011-01-16
There's a guide on how to install netflix on ubuntu - it requires windows running virtually in Ubuntu: [http://how-to.wikia.com/wiki/How_to_watch_Netflix_(Watch_Instantly)_in_Linux](http://how-to.wikia.com/wiki/How_to_watch_Netflix_(Watch_Instantly)_in_Linux)

---

### Post by kittkatt on 2011-01-16
They both work, its just that at this point, you don't have enough experience working with Ubuntu to understand the actions that you're taking so it all seems so difficult.  Congratulations of sticking it through though!

I did a quick look about the netflix thing and [while its possible]("http://how-to.wikia.com/wiki/How_to_watch_Netflix_%28Watch_Instantly%29_in_Linux"), the solution is really convoluted and way too much of a headache for a beginner to want to try.

The easiest solution is to use windows, or buy a "Media Center PC" like [boxee]("http://www.boxee.tv/") or Apple TV or Xbox360/Wii/PS3.  Ask your local bestbuy/futur***** person about it and they can explain it all to you.

The reason why netflix doesn't work is the same underlying reason why your Amazon downloader didn't work at first.  In fundamental terms, most businesses will spend most of their resources towards making sure the Windows version of their product works first b/c 95% of computers worldwide run Windows.  Often, companies do not even bother making a Linux version of their product b/c it doesn't make sense business-wise.  

The Amazon downloader used outdated software, the company didn't feel it was worth its time/effort to make sure that everything was up to date.  This is why it didn't work until you yourself downloaded/installed some outdated software that it needed to install/run properly.

This is the one big flaw with Linux and a problem you may find yourself encountering again and again.  It is also why linux programmers are so passionate about free and open source software, so that users like yourself don't have problems like this.  Good luck exploring Ubuntu!

---

### Post by newlinuxlady on 2011-01-16
Thank you again for feedback- I do have a virtualbox loaded on the computer- so I will look into the recommendation you offered AI.

Thank you both- if I have other questions- I will put up a new thread as this one is now completed concern amazon- oh and the mp3 did download just fine and I have already listened to it!  Thank you for making my night or shall I say morning!

Yes- it is difficult taking the road less traveled when in comes to computers- but I am willing to try!  Thanks to helpful people like yourselves- I can have some friendly support along with learning on my own.

THANK YOU!

---

### Post by newlinuxlady on 2011-01-16
KittKatt- AI offered a wiki link above and wanted to share that the following does NOT work:

Other methods that DON'T work (as of 10/13/2010)

Boxee
Wine, though a Netflix customer service rep said (on 11/7/2010) he had clients tell him they got it working in Wine, but they wouldn't support it
Mono/Moonlight

---

### Post by oldos2er on 2011-01-16
A couple better solutions, in my opinion, using an Amazon mp3 downloader on 64-bit Ubuntu are
[http://code.google.com/p/pymazon/](http://code.google.com/p/pymazon/) and [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

