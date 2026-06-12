---
title: "lost sound after update"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Zundap on 2010-01-09
Could anyone please help, once again, after an update, i get a problem, this is about the 5th time its happened, on most of the occasions, i just reinstalled ubuntu  but this time i would like to sort it out, i am fed up with loosing my files and my stored favourites.

This time i have lost sound, could anyone help me with this, thanks very much.

And Can  any one tell me why this keeps happening?

---

### Post by spiderbatdad on 2010-01-09
Perhaps start by reinstalling alsa.
```
sudo apt-get install --reinstall alsa-base alsa-utils alsa-tools
```

---

### Post by Zundap on 2010-01-09
Thanks for the help spiderbatdad, i did as you advised and got this below printed out in shell, but i still do not have any sound at all, i would be most grateful for any further help.

Thanks.
  	 	 	 	 	  [SIZE=5]me@me-desktop:~$ sudo apt-get install --reinstall alsa-base alsa-utils alsa-tools [/SIZE]
 [SIZE=5][sudo] password for me:  [/SIZE]
 [SIZE=5]Reading package lists... Done [/SIZE]
 [SIZE=5]Building dependency tree        [/SIZE]
 [SIZE=5]Reading state information... Done [/SIZE]
 [SIZE=5]The following packages were automatically installed and are no longer required: [/SIZE]
   [SIZE=5]linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic [/SIZE]
 [SIZE=5]Use 'apt-get autoremove' to remove them. [/SIZE]
 [SIZE=5]The following NEW packages will be installed [/SIZE]
   [SIZE=5]alsa-tools [/SIZE]
 [SIZE=5]0 upgraded, 1 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded. [/SIZE]
 [SIZE=5]Need to get 1397kB of archives. [/SIZE]
 [SIZE=5]After this operation, 324kB of additional disk space will be used. [/SIZE]
 [SIZE=5]Do you want to continue [Y/n]?   I pressed y and got as below.[/SIZE]
 

 

 

 

 [SIZE=5]Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main alsa-base 1.0.18.dfsg-1ubuntu8 [232kB] [/SIZE]
 [SIZE=5]Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main alsa-utils 1.0.18-1ubuntu11 [1082kB] [/SIZE]
 [SIZE=5]Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe alsa-tools 1.0.18-1ubuntu2 [83.5kB] [/SIZE]
 [SIZE=5]Fetched 1397kB in 3s (406kB/s) [/SIZE]
 [SIZE=5](Reading database ... 121508 files and directories currently installed.) [/SIZE]
 [SIZE=5]Preparing to replace alsa-base 1.0.18.dfsg-1ubuntu8 (using .../alsa-base_1.0.18.dfsg-1ubuntu8_all.deb) ... [/SIZE]
 [SIZE=5]Unpacking replacement alsa-base ... [/SIZE]
 [SIZE=5]Preparing to replace alsa-utils 1.0.18-1ubuntu11 (using .../alsa-utils_1.0.18-1ubuntu11_i386.deb) ... [/SIZE]
 [SIZE=5]Unpacking replacement alsa-utils ... [/SIZE]
 [SIZE=5]Selecting previously deselected package alsa-tools. [/SIZE]
 [SIZE=5]Unpacking alsa-tools (from .../alsa-tools_1.0.18-1ubuntu2_i386.deb) ... [/SIZE]
 [SIZE=5]Processing triggers for man-db ... [/SIZE]
 [SIZE=5]Setting up alsa-base (1.0.18.dfsg-1ubuntu8) ... [/SIZE]
 [SIZE=5] [/SIZE]
 [SIZE=5]Setting up alsa-utils (1.0.18-1ubuntu11) ... [/SIZE]
 [SIZE=5] [/SIZE]
 [SIZE=5]Setting up alsa-tools (1.0.18-1ubuntu2) ... [/SIZE]

---

### Post by spiderbatdad on 2010-01-09
please use standard size text in replies.

---

### Post by Zundap on 2010-01-09
Sorry about that, but i just copied from shell and pasted it here and that is how it turned out. I will reduce it in future before i paste it here.

---

### Post by spiderbatdad on 2010-01-09
have you checked all volume setting in alsamixer? You can launch alsamixer as a command it your terminal. Make sure your volume isn't muted. If you can't resolve through alsamixer, please post back
```
cat /proc/asound/cards
lspci | grep Audio
```

---

### Post by Zundap on 2010-01-09
> **spiderbatdad said:**
> have you checked all volume setting in alsamixer? You can launch alsamixer as a command it your terminal. Make sure your volume isn't muted. If you can't resolve through alsamixer, please post back
```
cat /proc/asound/cards
lspci | grep Audio
```


I do not know how to check alsamixer, or even where it is, but ile paste the code you posted  in to shell and see what happens, thanks again.

---

### Post by Zundap on 2010-01-09
Sorry, i should of course said, post it in terminal.

---

### Post by spiderbatdad on 2010-01-09
launch alsa mixer as a command in your terminal
```
alsamixer
```
use arrows and tab to navigate. esc to close. Check the master and PCM levels.

---

### Post by Zundap on 2010-01-09
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.18 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
Here is what i got below, does that tell us anything????&#9474;


 Card: SiS SI7012                                                             &#9474;
&#9474; Chip: Analog Devices AD1888                                                  &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-45.00, -45.00]                                        &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;              &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;              &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;              &#9474;  &#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;              &#9474;  &#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;    Shared    &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;              &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;MM&#9474;     &#9474;OO&#9474;      &#9474;OO&#9474;     &#9474;MM&#9474;     &#9474;OO&#9474;      &#9474;MM&#9474;              &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;    3<>3      81       0<>0             81<>81     0<>0               100     &#9474;
&#9474; < Master >Master M  Master S Headphon   PCM     Surround Surround  Center

---

### Post by spiderbatdad on 2010-01-09
sure. turn the pcm up.

---

### Post by Zundap on 2010-01-09
Ahh i get it now, The Master and PCM levels both have 4 white marks - 3 green marks and the top mark in each case is red. Does tell us anything?

---

### Post by Zundap on 2010-01-09
How do i turn it up?  I have never used this before. Thanks

---

### Post by Zundap on 2010-01-09
ok i did it i used tab as you said, but PCM it is now at max, 100 but i stil have no sound at all. Sorry about this bit i am totally new to ubuntu virtually.

---

### Post by buntunub on 2010-01-09
In alsamixer, make sure nothing is muted. You can tell its muted if there is a MM at the bottom of the channel. Use the left, right, up, and down keys to navigate. Crank all channels to max and go from there. If you still dont have sound after that, search for the sound guide on these forums and follow directions carefully. Sound issues are one major nightmare to fix sometimes in Linux especially if you have cutting edge hardware and the devs havent gotten around to reverse engineering a driver for your card yet. PulseAudio might also be causing some issues for you but the audio guides tend to cover that aspect as well. With some time and a healthy dose of patience, you will get it sorted out and in the process, you will have learned a great deal that will make solving future issues like this a breeze.

---

### Post by Zundap on 2010-01-09
Thanks for the reply, i have done that and still no sound, i think i will just reinstall and refuse any updates, its the updating thats caued the trouble every time, its either that or go back to Windows, yuk.
 
Its such a shame, all the hard work thousands of people have put in to this for it not to work every time it updates.

Thanks again for trying though buntunub, cheers mate.

---

### Post by Zundap on 2010-01-09
Hey, i cracked it guys, i double clicked on the sound icon in the top right hand corner, as i read in another thread,  and an interface opened entitled, **Volume control SiS S17021 (Alsa mixer)**. There are five sections to it, all with slides to adjust them, they are named Master, PCM, Line in, CD, and microphone.

The slider named **"Line in"** Had a little red circle with a white diagonal line across it, just like a British No Entry road sign at the bottom of it and the sliders were right at the bottom of its scale, i just moved the slider up to the top and hey presto, the little red sign disapeared and i got my sound back.

I Hope this helps someone else in the future and thanks again to everyone that offered advice. 

Just one other thing, i just rememberd that i have had a Fire fox update after the ubuntu update, so it could have been that, that altered the sound setting. 

And i am running ubuntu 9.04.

---

