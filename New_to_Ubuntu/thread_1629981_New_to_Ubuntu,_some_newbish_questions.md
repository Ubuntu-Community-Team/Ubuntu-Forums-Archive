---
title: "New to Ubuntu, some newbish questions"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by rbs9009 on 2010-11-24
I suppose I should introduce myself. My name is Ryan, I'm 27 years old from the Hudson Valley region of NY. I have been computer literate since I was 10 years old (Windows 3.1 was my first OS) but only recently have I been interested in learning beyond the Windows OS. I currently own two laptops, one being a 1st gen Macbook Pro, the other a Toshiba Satellite A505, which I am running Windows Vista alongside Ubuntu. I consider myself computer literate, but I am looking to expand my knowledge and learn more about the Linux kernel.

I am looking for any pointers you guys could throw at me. Also, I have a few questions that I couldn't find the answer to with search. Here what I got:

1. I am already enjoying the Ubuntu OS much more than Windows. Granted, I have been running it for less than 24 hours, but I can already tell it works much better with my laptop than Vista; lag is pretty much nonexistent, things load quickly, no error messages. My question is whether or not keeping Windows on this computer is worth it? I use this computer for basic stuff: internet, music, word processing, minor photo editing, spreadsheets, and thats about it. Pros? Cons? Also, if I decide to remove Vista, how would I go about doing it?

2. I have approximately 50 gigs of music on the Mac that is formatted for itunes. Could I bring it over to my Ubuntu laptop without reformatting, or would it have to reformatted? 

Thanks for reading, definitely hope I can make a contribution some day.

---

### Post by Rubi1200 on 2010-11-24
Hi and welcome to the forums :)

I can't help you with the second question, but regarding the first I would say this. Keep Windows for the moment and run a dual-boot system. As you say, you have only been using Ubuntu for a very short period of time.

First get used to it, use it, ask questions, and get comfortable with what you are doing.

I recommend keeping Windows for at least 6 months; then make a decision as to whether or not you want/need it.

After all, there is a learning curve with anything new. Ubuntu is fantastic, but you may find some things won't work, especially games or other Windows-specific software.

Welcome to the community and, above all, have fun.

---

### Post by matt_symes on 2010-11-24
Hi

> I have approximately 50 gigs of music on the Mac that is formatted for  itunes. Could I bring it over to my Ubuntu laptop without reformatting,  or would it have to reformatted? What format are the tunes in?

You will have to install Ubuntu restricted extras package to play mp3 etc. (from a terminal)

sudo apt-get install ubuntu-restricted-extras

Have you tried to play the music through the live CD using Rhythm Box after installing the restricted extras?

Also +1 Rubi's suggestion.

Kind regards

---

### Post by cariboo on 2010-11-24
> **rbs9009 said:**
> I suppose I should introduce myself. My name is Ryan, I'm 27 years old from the Hudson Valley region of NY. I have been computer literate since I was 10 years old (Windows 3.1 was my first OS) but only recently have I been interested in learning beyond the Windows OS. I currently own two laptops, one being a 1st gen Macbook Pro, the other a Toshiba Satellite A505, which I am running Windows Vista alongside Ubuntu. I consider myself computer literate, but I am looking to expand my knowledge and learn more about the Linux kernel.

I am looking for any pointers you guys could throw at me. Also, I have a few questions that I couldn't find the answer to with search. Here what I got:

> 1. I am already enjoying the Ubuntu OS much more than Windows. Granted, I have been running it for less than 24 hours, but I can already tell it works much better with my laptop than Vista; lag is pretty much nonexistent, things load quickly, no error messages. My question is whether or not keeping Windows on this computer is worth it? I use this computer for basic stuff: internet, music, word processing, minor photo editing, spreadsheets, and thats about it. Pros? Cons? Also, if I decide to remove Vista, how would I go about doing it?

If you still need any Windows programs, I would suggest you keep your Vista partition. If not you can use [Gparted]("http://gparted.sourceforge.net/"), it's in the repositories, to remove your Windows partition, and expand your Ubuntu partition.

> 2. I have approximately 50 gigs of music on the Mac that is formatted for itunes. Could I bring it over to my Ubuntu laptop without reformatting, or would it have to reformatted?

If you can play your music using something other than Itunes, you shouldn't have any problems playing them on Ubuntu. I would suggest you go to the Software Center and install ubuntu-restricted-extras, this meta package installs most of the codecs you need to play most types of audio/video media, it also installs java plugins, flash and mscorefonts. 

> Thanks for reading, definitely hope I can make a contribution some day.

I would suggest you create an account on [https://launchpad.net]("https://launchpad.net"), and report any bugs you run into, that goes a long ways in helping make Ubuntu better. Reporting bugs is pretty simple, if you run into a bug, just press Alt-F2 and type:

```
ubuntu-bug <packagename>
```

where <packagename> = the program you found the bug in.

Good luck and enjoy.

---

### Post by Sef on 2010-11-24
> 2. I have approximately 50 gigs of music on the Mac that is formatted for itunes. Could I bring it over to my Ubuntu laptop without reformatting, or would it have to reformatted? 

If your music is formatted as .mp3, then it will play on Ubuntu. However, because mp3 is a restricted format, you have to [download software]("https://help.ubuntu.com/community/RestrictedFormats") from the Ubuntu repository to play mp3 files.

---

### Post by -schizoid on 2010-11-24
You should keep windows and just dualboot, as some things are made specifically for windows and are near impossible to get running on ubuntu. For example: Netflix, some newer games, some software...

---

