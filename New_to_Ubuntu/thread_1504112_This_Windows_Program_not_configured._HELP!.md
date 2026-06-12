---
title: "This Windows Program not configured. HELP!"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by denis153 on 2010-06-07
Okay So I have this one file and it is called PBsetup.run and everytime i click on it it says there is no windows program configured to open this file! Help! :confused:

---

### Post by Mariane on 2010-06-07
What is it supposed to do? 

Mariane

---

### Post by khelben1979 on 2010-06-07
Do you have [wine]("http://en.wikipedia.org/wiki/Wine_%28software%29") installed?

---

### Post by denis153 on 2010-06-07
Yes I have Wine installed..


It configured my punkbuster so i can play games.

---

### Post by SunnyRabbiera on 2010-06-07
Might be one of those things you may have to boot into windows for, wine is not perfect and does not offer 100% compatibility with windows apps.
Though wine is always getting better, so one day that windows boot might not be needed.

---

### Post by sandyd on 2010-06-07
you picked the wrong version of the installer.
just pick the one for windows instead of the one for linux, and ill be fine.

---

### Post by denis153 on 2010-06-07
> **carlee said:**
> you picked the wrong version of the installer.
just pick the one for windows instead of the one for linux, and ill be fine.

I downloaded the one for linux. But that's the one that doesn't work. THere is like 4 downloads for it. THe GUI and command line and 32 or 62 bit games. If you could get me the version that maybe you have but for linux that would be great. Thanks in advance.

---

### Post by Shhnap on 2010-06-07
It sounds like you have to chmod +x the file first and then run it. It is a common problem that new people find when they download executables for linux.

1. Open a terminal
2. Use the 'cd' command to get in the same directory as the file.
3. chmod +x theFileYouDownloaded.
4. ./theFileYouDownloaded

And you are done.

---

### Post by SlidingHorn on 2010-06-07
> **denis153 said:**
> I downloaded the one for linux. But that's the one that doesn't work. THere is like 4 downloads for it. THe GUI and command line and 32 or 62 bit games. If you could get me the version that maybe you have but for linux that would be great. Thanks in advance.

More than likely, you're going to want the 32-bit GUI Linux version.

---

### Post by denis153 on 2010-06-08
> **Shhnap said:**
> It sounds like you have to chmod +x the file first and then run it. It is a common problem that new people find when they download executables for linux.

1. Open a terminal
2. Use the 'cd' command to get in the same directory as the file.
3. chmod +x theFileYouDownloaded.
4. ./theFileYouDownloaded

And you are done.

Can you give me the "code" for that. The file name is pbsetup.zip because I don't really understand the cd command or whatever.:confused:

---

### Post by sandyd on 2010-06-08
> **denis153 said:**
> Can you give me the "code" for that. The file name is pbsetup.zip because I don't really understand the cd command or whatever.:confused:
ok, which game are you trying to play.

and the linux version does NOT interface with windows games, so if your trying to use it with a windows game, download the windows version of punkbuster, extract it, and double click the file that you just extracted

---

### Post by denis153 on 2010-06-08
I am Trying to play Americas Army 
And I downloaded it for linux.
But when I run it i get these such as pb user path3 not found and stuff.

---

### Post by sandyd on 2010-06-08
> **denis153 said:**
> I am Trying to play Americas Army 
And I downloaded it for linux.
so your running the linux version of America's Army on Linux right?

ok, so

go to
[http://websec.evenbalance.com/downloader/download.php?file=4](http://websec.evenbalance.com/downloader/download.php?file=4)

Download it to your desktop

run
```

cd ~/Desktop
unzip pbsetup.zip
chmod 667 pbsetup.run
 bash ./pbsetup.run
```

---

### Post by denis153 on 2010-06-08
> **carlee said:**
> so your running the linux version of America's Army on Linux right?

ok, so

go to
[http://websec.evenbalance.com/downloader/download.php?file=4](http://websec.evenbalance.com/downloader/download.php?file=4)

Download it to your desktop

run
```

cd ~/Desktop
unzip pbsetup.zip
chmod 667 pbsetup.run
sudo sh ./pbsetup.run
```

Sorry to keep bothering you but it says this:


```
denis@denis-desktop:~$ cd ~/Desktop
denis@denis-desktop:~/Desktop$ unzip pbsetup.zip
Archive:  pbsetup.zip
  inflating: pbsetup.run             
denis@denis-desktop:~/Desktop$ chmod 667 pbsetup.run
denis@denis-desktop:~/Desktop$ chmod 667 pbsetup.run
denis@denis-desktop:~/Desktop$ sudo sh ./pbsetup.run
[sudo] password for denis: 
./pbsetup.run: 1: Syntax error: "(" unexpected
denis@denis-desktop:~/Desktop$ 



```

---

### Post by sandyd on 2010-06-08
> **denis153 said:**
> Sorry to keep bothering you but it says this:


```
denis@denis-desktop:~$ cd ~/Desktop
denis@denis-desktop:~/Desktop$ unzip pbsetup.zip
Archive:  pbsetup.zip
  inflating: pbsetup.run             
denis@denis-desktop:~/Desktop$ chmod 667 pbsetup.run
denis@denis-desktop:~/Desktop$ chmod 667 pbsetup.run
denis@denis-desktop:~/Desktop$ sudo sh ./pbsetup.run
[sudo] password for denis: 
./pbsetup.run: 1: Syntax error: "(" unexpected
denis@denis-desktop:~/Desktop$ 



```
oops, my bad

try again.

---

### Post by jms1989 on 2010-06-09
wait wait, you're trying to run a .run file for linux?

Try this;

chmod +x pbsetup.run
./pbsetup.run

OR

right click on the run file, go to the priviliges tab and check all markers for excutable then close. double click on the file and click run

Only install programs from the ubuntu repos or debs files as root, never run third party apps as root. You run the chance of ruining your install.

---

### Post by denis153 on 2010-06-09
> **jms1989 said:**
> wait wait, you're trying to run a .run file for linux?

Try this;

chmod +x pbsetup.run
./pbsetup.run

OR

right click on the run file, go to the priviliges tab and check all markers for excutable then close. double click on the file and click run

Only install programs from the ubuntu repos or debs files as root, never run third party apps as root. You run the chance of ruining your install.
ZOMG! Thank you so much! I tried it and it worked!
> **carlee said:**
> oops, my bad

try again.
ZOMG AGAIN! I tried it and worked also! Now i know 2 Ways!
Thanks so much guys thank you so much!!!!!!!

---

### Post by Shhnap on 2010-06-12
Yeah, that's exactly what I told you to do. Friendly advice, next time use 'man <command_name>' to look up the manual to understand the commands if you do not understand them. That way you know what you are doing next time and will not come back with a similar problem. :)

---

