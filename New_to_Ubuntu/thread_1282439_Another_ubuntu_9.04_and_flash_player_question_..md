---
title: "Another ubuntu 9.04 and flash player question ."
date: 2009-10-04
forum: New to Ubuntu
---

### Post by burnnxs on 2009-10-04
HI it's my first post here.
I am ultra new to ubuntu I just installed i  int my laptop last night. I have tried to get the flash player plugin to work with mozilla, looking thru google and using instructions but I did not get anywhere.

I used to get the error i386 or i638 can't remever wich. And by reading around it said that I needed a 64bit flash player. 
  I used this instructions [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

The only thing I do notice (dunno if it matters ) is that the extracted file icon does not look like the one in the instructions. It looks like a sheet of paper in my desktop. 
As you can tell I am not anywhere near awesome with computers, but really want to learn, A step by step solution would be much much appreciated. 
Thanx in advance

---

### Post by Vaphell on 2009-10-04
it's quite brave to begin your linux experience with alpha/beta version of a release :)

maybe try classic way first: fire up synaptic, look for flashplugin-installer, mark it, apply

in url bar of firefox write **about: plugins** (but without space) and see if there is flash mentioned. if it is, that means it's installed

---

### Post by PatrickMoore on 2009-10-04
> **burnnxs said:**
> HI it's my first post here.
I am ultra new to ubuntu I just installed i  int my laptop last night. I have tried to get the flash player plugin to work with mozilla, looking thru google and using instructions but I did not get anywhere.

I used to get the error i386 or i638 can't remever wich. And by reading around it said that I needed a 64bit flash player. 
  I used this instructions [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

The only thing I do notice (dunno if it matters ) is that the extracted file icon does not look like the one in the instructions. It looks like a sheet of paper in my desktop. 
As you can tell I am not anywhere near awesome with computers, but really want to learn, A step by step solution would be much much appreciated. 
Thanx in advance

check to see if you have gdebi package installer, its in synaptec or even easier to find in add/remove software. that should help you.

---

### Post by dwasifar on 2009-10-04
If you are that new at this, it's probably not a good idea to be using 9.10.  The final version of 9.10 has not been released yet; what you have is an alpha or beta testing version, which still has bugs and will be harder to troubleshoot, especially for a new user.  

You'll do yourself a favor if you start over with Jaunty, version 9.04.  Get it [here.]("http://www.ubuntu.com/getubuntu/download")

Then, to get the extras like Flash working, follow the guides on this page: [http://www.johannes-eva.net]("http://www.johannes-eva.net").

---

### Post by burnnxs on 2009-10-04
I installed it using wubi and looking back at the site it says 9.04. So i'm guessing i'm on the right track ?

---

### Post by burnnxs on 2009-10-04
> **Vaphell said:**
> it's quite brave to begin your linux experience with alpha/beta version of a release :)

maybe try classic way first: fire up synaptic, look for flashplugin-installer, mark it, apply

in url bar of firefox write **about: plugins** (but without space) and see if there is flash mentioned. if it is, that means it's installed
I did as you said and I can see it in the list as installed. But I still can't see videos.

---

### Post by burnnxs on 2009-10-04
> **PatrickMoore said:**
> check to see if you have gdebi package installer, its in synaptec or even easier to find in add/remove software. that should help you.
 It shows that I do have  it .

---

### Post by burnnxs on 2009-10-04
Any other tips?

---

### Post by sandyd on 2009-10-04
```

wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xvfz libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/firefox/plugins
rm libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz libflashplayer.so

```

make sure you remove flashplugin-nonfree first

---

### Post by burnnxs on 2009-10-04
> **carlee said:**
> ```

wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xvfz libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/firefox/plugins
rm libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz libflashplayer.so

```make sure you remove flashplugin-nonfree first
I runned it thru terminal, It asked for my password and it stopped.
I runned about:plugins and it shows it active.
Tried youtube, now it wont even show the video rectangular box.

---

### Post by burnnxs on 2009-10-04
This means that I am running at 64bit right ?

 uname -a
Linux ubuntu 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

---

### Post by burnnxs on 2009-10-04
Bump!
I need a step by step check list to fix this player. :(

---

### Post by theozzlives on 2009-10-04
Go to Terminal and type:
```
sudo apt-get install ubuntu-restricted-extras
```
it'll install java, flash, MS fonts and some other stuff (codecs and things).

---

### Post by overdrank on 2009-10-04
[s]Moved to Karmic Koala Testing and Discussion[/s]:oops:

---

### Post by burnnxs on 2009-10-04
I went in thru synaptic and looked up  ubuntu- restricted extras, Installed them.
Tried it but nothing yet.

I tried it thru terminal with the code provided by theozzlive , Nothing.

---

### Post by scradock on 2009-10-04
> **overdrank said:**
> Moved to Karmic Koala Testing and Discussion
Why? It's becoming clear he/she's running Jaunty, with a 2.6.28 generic kernel. The title is incorrect - this belongs in Absolute Beginners.

---

### Post by burnnxs on 2009-10-04
> **overdrank said:**
> Moved to Karmic Koala Testing and Discussion
I installed wubi 9.04 version yesterday. What ubuntu version is that ?

---

### Post by miegiel on 2009-10-04
> **burnnxs said:**
> I installed wubi 9.04 version yesterday. What ubuntu version is that ?

That's jaunty.

If you want to install the 64bit flashplayer try [_this thread_]("http://ubuntuforums.org/showthread.php?t=1259102") (I think it should work for karmic too).

---

### Post by cariboo on 2009-10-04
Moved to ABT where it belongs.

---

### Post by 3rdalbum on 2009-10-04
The people advising you to install the "ubuntu-restricted-extras" package are not 64-bit users.

The URE package adds 32-bit Flash plugin which does not really work well in 64-bit Firefox.

You need to extract the 64-bit alpha Flash plugin archive (double-click on it and you'll be able to extract it to a location on your computer). Inside the archive is a file called "libflashplayer.so". Open up a file browser as root by using this terminal command:

```
gksudo nautilus
```

Navigate to /usr/lib/mozilla/plugins in the file browser you've just opened. Drag the libflashplayer.so file from where you've extracted it to, to the /usr/lib/mozilla/plugins folder.

Close Firefox completely and open it up again, and you should have Flash player. If you've installed Gnash or swfdec already, or the 32-bit flash plugin (flashplugin-nonfree) you need to remove those other Flash players.

---

### Post by burnnxs on 2009-10-05
I will try it in no time.Thanx 3rdalbum and everybody that is trying to help me!.
One lil thing I forgot to add... last night after reading around and attempting several fixes,I opted for a full uninstall of WUBI, As I kept reading it said that wubi is awesome but there is limitations with space and power saving setting not added on the "wubi version".

I am really happy with my brief experience with Ubuntu. and want to reinstall the real deal in my laptop as a partition, because I want all the features. Not worried about space with this laptop because it is new and has 500gb, 4gb of ram, T6500 and so on... 
 Question:
What do I need and how do I install the full ubuntu as a partition without wubi?

Im not lazy. I just keep finding old info from 2006/7.

---

### Post by miegiel on 2009-10-05
> **burnnxs said:**
> ... 
 Question:
What do I need and how do I install the full ubuntu as a partition without wubi?

Im not lazy. I just keep finding old info from 2006/7.


Try : [_Ubuntu Documentation > Community Documentation > Installation_]("https://help.ubuntu.com/community/Installation") (last edited 2009-09-06 20:34:38

---

### Post by burnnxs on 2009-10-09
ok I can see videos now but I have no audio, what do I do ?

---

### Post by miegiel on 2009-10-09
> **burnnxs said:**
> ok I can see videos now but I have no audio, what do I do ?If you have no sound at all [_Ubuntu Documentation > Community Documentation > Sound_]("https://help.ubuntu.com/community/Sound")
If you only have no sound playing flash vids: I'm not really sure. But at least tell us if you're using the 32 or 64 bit flash player (if you don't know tell us how you installed it). You're still using 64bit ubuntu, right?

---

### Post by HarrisonNapper on 2009-10-09
At the risk of redundancy,

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

If that doesn't work (it's a pre-release):

[Install/Uninstall flash in 64-bit]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html") 

The above link is a script that will wrap the 32-bit flash player so it will run in a 32-bit environment on your computer. I warn you, however, this should be your option only if the first does not work as npviewer.bin will use a lot of processor with this method.

---

### Post by burnnxs on 2009-10-09
> **miegiel said:**
> If you have no sound at all [_Ubuntu Documentation > Community Documentation > Sound_]("https://help.ubuntu.com/community/Sound")
If you only have no sound playing flash vids: I'm not really sure. But at least tell us if you're using the 32 or 64 bit flash player (if you don't know tell us how you installed it). You're still using 64bit ubuntu, right?
 I ended up reinstalling the WUBI version 9.04 ,all I changed was the install space, and went ahead and used the installation style that 3rdalbum told me in a previous post .

 Yeah I used the 64 bit flash and it worked great. I can play cd's or watch videos in youtube with no sound at all. so.....?

---

### Post by burnnxs on 2009-10-09
I am attemting the update of alsa but got one error notmentioned. it goes something like this....

checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking panel.h usability... no
checking panel.h presence... no
checking for panel.h... no
configure: error: required curses helper header not found
gus@ubuntu:/usr/src/alsa/alsa-utils-1.0.21$ sudo make
make: *** No targets specified and no makefile found.  Stop.
gus@ubuntu:/usr/src/alsa/alsa-utils-1.0.21$ sudo make install
make: *** No rule to make target `install'.  Stop.
gus@ubuntu:/usr/src/alsa/alsa-utils-1.0.21$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.
gus@ubuntu:/usr/src/alsa/alsa-utils-1.0.21$ Advanced Linux Sound Architecture Driver Version 1.0.21.
bash: Advanced: command not found
gus@ubuntu:/usr/src/alsa/alsa-utils-1.0.21$ Compiled on Aug 31 2009 for kernel 2.6.28-15-generic (SMP).

---What does it mean ?

---

### Post by HarrisonNapper on 2009-10-12
Looks like you're missing the library "panel.h"; maybe search for it in repos? Could be part of another package.

---

