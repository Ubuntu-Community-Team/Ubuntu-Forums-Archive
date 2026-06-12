---
title: "alas ! I will have to roll back to windows, i see some hope only there?"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by gs777 on 2008-11-28
This is my first post and i afraid may become the last .
     With great enthusiasm i installed Ubuntu 8.10. At first it gave a great impression- easy install, beautiful graphics at tthe time of istallation ,time taken for etc.Then came the harder part.I found the following
1) No 3d graphic driver was installed by default.
2)No media codecs not even of mp3.
4)bluetoth software just refuses to work! no reason.
     well. I want some software to install in ubuntu.what i see that every attempt to this requires internet connection.In our area no broadband, No dsl connections available, but the edge connection provided by my cellular operator is of decent speed 
about (135K practical speed).I have a pda running on windows mobile 5 and want to connect to internet through it.I read in the documentation that some packages need to be installed for this . The question is I don't have any other way to connect to internet except using my wm5 as a modem.Now, no net no program can be installed ,so no way to connect to internet .......ultimately ubuntu- useless.is it really useless or is there any way out ? 
my mission - connect to internet with my pocket pc as modem 
  pit falls -no net connection to install software from repository.
 looking here a way out ... or I will have to go back to windows
thanks in advance.:confused:

---

### Post by albandy on 2008-11-28
If your mobile phone act as an standard usb modem it should work.
No drivers needed.

I'm using a Sony Ericsson k610i and works perfect.

---

### Post by ashmew2 on 2008-11-28
> **gs777 said:**
> This is my first post and i afraid may become the last .
     With great enthusiasm i installed Ubuntu 8.10. At first it gave a great impression- easy install, beautiful graphics at tthe time of istallation ,time taken for etc.Then came the harder part.I found the following
1) No 3d graphic driver was installed by default.
2)No media codecs not even of mp3.
4)bluetoth software just refuses to work! no reason.
     well. I want some software to install in ubuntu.what i see that every attempt to this requires internet connection.In our area no broadband, No dsl connections available, but the edge connection provided by my cellular operator is of decent speed 
about (135K practical speed).I have a pda running on windows mobile 5 and want to connect to internet through it.I read in the documentation that some packages need to be installed for this . The question is I don't have any other way to connect to internet except using my wm5 as a modem.Now, no net no program can be installed ,so no way to connect to internet .......ultimately ubuntu- useless.is it really useless or is there any way out ? 
my mission - connect to internet with my pocket pc as modem 
  pit falls -no net connection to install software from repository.
 looking here a way out ... or I will have to go back to windows
thanks in advance.:confused:

"Dont stop those who want to leave"

But i'd say if you wanna stick with Ubuntu and have sucky internet (or no internet)..Its going to be hard , but you could (and IMO , SHOULD) try Linux Mint and Ubuntu Christmas Edition. They come with codec support by default. And as far as i remember , windows doesnt install the graphic driver on its own...Anyhow , you might have some luck with them and once you are connected to the internet , everything should make sense.

Another thing..Sometimes the things that dont work in 8.10 still work in 7.10 or 8.04...If you are willing to spend some time with Ubuntu , you can probably expect something out of it.

---

### Post by kevdog on 2008-11-28
threatening all of us that you are going to roll back to windows??? Go ahead!

---

### Post by madverb on 2008-11-28
Are 3D graphics card drivers installed by default in Windows? That must be new... because the last 50 times I've installed windows on computers I have had to install the drivers afterwards.
Windows doesn't play a lot of formats by default.
How do you install programs in windows? Oh that's right... you pay excessive amounts for a CD to install it. Or guess what? You download the software and install it.
It seems Ubuntu is useless for you. Why do people always have to post in forums with this ish? It's pointless, if you don't have the patience to sort out a few problems don't bother.

---

### Post by gs777 on 2008-11-28
sorry! I was in afrustated condition! 
  think of the situation 1) no dsl connection 2) only way to connect to internet is via pocket pc and to set up this as a modem i need internet. almost any useful work requires internet. hope u guys will help me 
.if in any awy i get connected to net i will surely kick out bill gates.but for now i see no hope.

---

### Post by mvalviar on 2008-11-28
I know its frustrating. I'm new to ubuntu too. Although I used GNU/Linux boxes in school this is the first time I ever had a GNU/Linux box of my own. If you really want to stay in ubuntu and sort out this problem state the situation clearly. I don't know how to solve your problem but what if someone browsing the forums does and sees your thread? Then he'll say, "Oh, he's given up why bother?" Put a little faith in the community.

---

### Post by madverb on 2008-11-28
What application do you need to install?

---

### Post by gs777 on 2008-11-28
synce-serial and librra0-tools

---

### Post by madverb on 2008-11-29
Ahh, that Windows device is a problem hey... If only they supplied software that was compatible with Linux.

---

### Post by alwayshere on 2008-11-29
see ya

---

### Post by mantasjn on 2008-11-29
Hey everybody - newbie to forum and linux.

I seem to run into that "compatible with linux" issue allot!!! Finding devices on the market that can run with LINUX natively, or with some drivers, is extremely hard, if not futile. That's just my take on the compability issue. I absolutely love UBUNTU LINUX and find that it, above all other distributions, is smooth, clean and very easy to install and work with. Each day that passes, I am more convinced that I won't be going back to Windows ever again...and here's the real kicker...I spent nearly 20 years in the IT field working with (cutting my teeth on) Microsoft Windows technology. - Jerry/Toronto.

---

### Post by J172 on 2008-11-29
gs777, I private messaged you regarding the matter.

Mantasjn, I'm a windows Fanboy -- I no longer run windows. :-) Ubuntu is contagoious and highly infectious.

---

### Post by J172 on 2008-11-29
Alright gs777, I just emailed you the files and dependencies it needed and everything. Just follow the instructions in the email and it should work fine.

---

### Post by gs777 on 2008-11-30
thanks j172, now I m connected to the internet with full power of linux.also i would like to point any one who falls in similar problems to this [link]("https://help.ubuntu.com/community/PortableDevices/WindowsMobile").

---

### Post by J172 on 2008-11-30
No problem. Glad I could help! I was worried it wouldn't work. I'd have been sad.

For the record
I went to the SynCE website, (synce was a package he had mentioned in a previous post to this thread). I downloaded all the files it said to download for Debian (again, Debian is the base of Ubuntu). To only download the files I entered sudo apt-get -d [files here]. It then said I needed dependencies and extra files and what not, so I copied all the package names and pasted it all into one giant sudo apt-get -d command, and downloaded them. However, I cleared the cache before so I wouldn't send him unnecessary files. (sudo apt-get clean, THEN download). I copied the contents of /var/cache/apt to my desktop using sudo cp * /home/jeffrey/Desktop/archives. I then CHMODd the files on my desktop so that I could work with them. (sudo chmod -R 777 /home/jeffrey/Desktop/archives). I then zipped everything up with a file simply containing the install command (sudo apt-get install (all of those packages). And emailed it to him. 


To install EVERYTHING needed (includes dependencies)

sudo apt-get install  libgnet2.0-0 libmimedir0 libopensync0 librapi2 librra-tools librra0  librtfcomp0 libsynce0 opensync-module-python python-dateutil python-libxslt1 python-opensync python-rapi2 python-rra python-rtfcomp python-tz python2.4   python2.4-minimal synce-sync-engine python-libxslt1-dbg python2.4-doc python-profiler libgnet2.0-0 libmimedir0 libopensync0 librapi2 librapi2-tools librra-tools librra0 librtfcomp0 libsynce0 multisync-tools odccm opensync-module-python opensync-plugin-evolution opensync-plugin-synce python-dateutil python-libxslt1 python-opensync python-rapi2 python-rra python-rtfcomp  python-tz python2.4 python2.4-minimal synce-serial synce-sync-engine

Oh, gs777 if you click thread tools at the top, click Mark as Solved if you're satisfied.

---

### Post by ByteJuggler on 2008-11-30
What did he have to do with the zip/where did he have to put the deb files for apt to pick them up?  In the /var/cache/apt folder?

---

