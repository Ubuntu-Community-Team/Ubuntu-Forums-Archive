---
title: "cannot make ANY sense out of it"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by nyuwa on 2009-05-03
Greetings from Japan
I have been using (but am NOT a computer specialist!) computers for 25 years, most of the time MS DOS, later Windows and in between also Mac. Since I do not like Microsoft (this sentiment grows stronger every day), I tried last year to "get friendly" with linux.
I tried Linguas OS, OpenSUSE, Ubuntu, Xubuntu and also have Devian disk somewhere. Right now, I am back to Ubuntu 8.10 (Japanese version), because I need the Japanese.

However - someone on another list suggested, that I am just too stupid - I cannot make it work. AT ALL!!
I did download the the "Pocket Guide" from Keir Thomas, 2-3 other 1000-page thick Linux manuals (not yet read), but the descriptions/instructions for some reason DO NOT work for me. Most probably I AM too stupid.

So, I would be really greatful, if someone could "take me by the hand and show me around". There are probaly a million problems I cannot figure out, but let's start with 2-3 of the immediate (urgent) problems.
1)  I am using some very old equipment for my experients. Monitor: 15 inches CRT, which definitely HAD a higher than 800x600 resolution, when I used it with a Windows system. Under Ubuntu it has a max resolution of 800x600, refresh rate can be chosen only among 60 and 54 Hz. With this setting most of the dialog boxes do NOT fit on the screen and I have to GUESS (literally blind touch) where to choose "Next" or "OK" or whatever. Is there any way of changing this?

2)  I cannot connect to the Internet (tried to follow all sorts of different instructions).&#12288;I am using a DSL with my computer and 2 PCs of my children connected to a HUB (could not make the router work). This is not perfect, but it works somehow. From the same hub I connected a cable to the Ubuntu computer. The network icon (which has somehow disappeared from the screen used to show me "connected", but nevertheless neither browser nor mailer work, because there is "no internet connection".

3)  Probaly related to (2). I need at least 2 (3) different keyboard layouts: Japanese, English + German. Currently I have set Japanese and German. The keyboard indicator on top of the screen shows me Jpn -> which gives me Japanese characters, but Deu does NOT give me German characters. I read somewhere, that Ubuntu needs to connect to the internet, to download something to make this work, but since I cannot get connected ....

The above mentioned Pocket Guide (and the other books) says: "Ubuntu simply works. Fussfree." 
As of now, that is not what I am experiencing. Since I cannot make ANYTHING work (same with all the other flavors of Linux), my attempts at getting friendly with Linux so far have been very frustrating. If there were at least 1-2 little success stories ....

So, ANY help would be great!
Thank you in advance           :confused:

---

### Post by Ptero-4 on 2009-05-03
Have you tried kubuntu 9.04?

---

### Post by pbpersson on 2009-05-03
To start, let us work with problems 1 and 2 - maybe when you get connected and you get all the updates problem 3 will work itself out.

1.  What graphics card are you using?  Does the machine tell you there are proprietary drivers for your card?  If so, that problem will most likely be solved when you get your network up and running.

2.  Post the output of the following command when typed at a terminal prompt.  I would imagine you would need to put the output on a flash drive and sneaker net them over to another machine to send to us.

```
ifconfig
```

---

### Post by SnaveDogg on 2009-05-03
your sentiment about it not being "fuss free" are true. It seems to be pretty fussy.

---

### Post by Ptero-4 on 2009-05-03
type:
```
lspci -v | grep "VGA"
```
in a terminal window. And post the results. This is for the videocard issue.

---

### Post by nyuwa on 2009-05-04
Thank you for the hint. I am currently downloading this file, but I am under the impression, that this, like most other versions, are ENGLISH version. Although I do not have any trouble with English, I NEED the computer to be able to handle Japanese. And this is also a feat that I NEVER achieved before with any of the English version - in spite of referring to lots of instruction. 
AND, I was just playing aroung with my "experimental computer", if I try to setup "language support" etc., I NEED to have internet access - which I still, literally after MONTHS or efforts and trying at least 5-6 different flavors could not achieve

---

### Post by nyuwa on 2009-05-04
Thank you.
I entered that on the screen and got some output - which is, however, most in Japanese. Would it make any sense posting that here?
The same holds true, naturally, for the "VGA" output.
I also suspect, that both the monitor and the computer I am trying to use are (WAY!) too old, but an attempt at installing Linux on a free HDD on my work computer completely disabled the computer and almost put me out of business. I am afraid, that is something I cannot afford ...

Also, I did not try a flash memory yet, I made a file with that data in OpenOffice Word, but when I tried to save it on a FD (to transfer to my other computer), I could NOT find the FDD anywhere. Should the FDD as a drive not listed by default somewhere? Just saving something on a FD cannot really be asking too much, can it?

---

### Post by SunnyRabbiera on 2009-05-04
It depends on the flash drive really, some work better then others under linux.
Brand of flash drive?

---

### Post by antmenj on 2009-05-04
Do you mean flash drive aka usb stick or 3.5 inch floppy aka FDD.

You have to mount a floppy by putting in the disk then clicking the disk drive icon in places or maybe places -> computer.  At the end right click it and unmount / eject before removing it from the drive.

If you go to the terminal and type:

```
ping www.ubuntu.com
```

does it say unknown host?

---

### Post by freeman2000 on 2009-05-04
At least twice you've mentioned "old" as in equipment.  Maybe therein lies the problem.  Why don't you list what equipment you are using and maybe we can see if it will work.  For instance, if your computer is so old that it only has 16mb ram, then it will never happen.  Lets go from there.  Fortunately for me, Linux has been practically "fuss-free".  Good luck and don't give up.

---

### Post by BuffaloX on 2009-05-04
I don't know about the other problems, but if your windows don't fit on your monitor, you can move them by pressing <alt> + <left mouse button> and then move the mouse.

That way you can navigate any window not fitting your screen.

---

### Post by fenian on 2009-05-04
Have you tried getting help in the Japanese ubuntu forum?You can [find it here]("https://forums.ubuntulinux.jp/").

---

### Post by Didius Falco on 2009-05-04
I'd suggest you focus first on the internet access problem. After you have access to the net, the other problems will be much easier to solve.

For example, I just looked at my options for the Japanese language, and it offered to install the following:  The language file itself, Basic translations, Extra translations, Input methods, Extra fonts and Extra software.

For German I find: the language file itself, Basic translations, Extra translations, spell-checking and writing aids and Extra software.

That sounds like pretty robust support for your language requirements.

I'd suggest starting a new thread entitled something like "no Internet access" detailing the problem in as much detail as you can, along with the system specs of your pc.

Then once that gets straightened out, the rest will be easier to resolve.

The suggestion to use a Japanese forum is a good one, too.

Good luck!!

---

### Post by nyuwa on 2009-05-04
> **Ptero-4 said:**
> type:
```
lspci -v | grep "VGA"
```in a terminal window. And post the results. This is for the videocard issue.


I copy here, what the computer gave me, first section for the "ifconfig" and next for the video card command.
The computer gives me these Japanese messages, which do not make any sense to me. And although I do translations for a living, this is not my field, so I could translate probably only very few of the technical terms:

 ifconfig 
eth0      Link encap:&#12452;&#12540;&#12469;&#12493;&#12483;&#12488;  &#12495;&#12540;&#12489;&#12454;&#12455;&#12450;&#12450;&#12489;&#12524;&#12473; 00:c0:4f:cf:62:e2  
          UP BROADCAST MULTICAST  MTU:1500  &#12513;&#12488;&#12522;&#12483;&#12463;:1 
          RX&#12497;&#12465;&#12483;&#12488;:0 &#12456;&#12521;&#12540;:0 &#25613;&#22833;:0 &#12458;&#12540;&#12496;&#12521;&#12531;:0 &#12501;&#12524;&#12540;&#12512;:0 
          TX&#12497;&#12465;&#12483;&#12488;:0 &#12456;&#12521;&#12540;:0 &#25613;&#22833;:0 &#12458;&#12540;&#12496;&#12521;&#12531;:0 &#12461;&#12515;&#12522;&#12450;:0 
          &#34909;&#31361;(Collisions):0 TX&#12461;&#12517;&#12540;&#38263;:1000 
          RX&#12496;&#12452;&#12488;:0 (0.0 B)  TX&#12496;&#12452;&#12488;:0 (0.0 B) 
          &#21106;&#12426;&#36796;&#12415;:11 &#12505;&#12540;&#12473;&#12450;&#12489;&#12524;&#12473;:0xe000 

lo        Link encap:&#12525;&#12540;&#12459;&#12523;&#12523;&#12540;&#12503;&#12496;&#12483;&#12463;  
          inet&#12450;&#12489;&#12524;&#12473;:127.0.0.1  &#12510;&#12473;&#12463;:255.0.0.0 
          inet6&#12450;&#12489;&#12524;&#12473;: ::1/128 &#31684;&#22258;:&#12507;&#12473;&#12488; 
          UP LOOPBACK RUNNING  MTU:16436  &#12513;&#12488;&#12522;&#12483;&#12463;:1 
          RX&#12497;&#12465;&#12483;&#12488;:214 &#12456;&#12521;&#12540;:0 &#25613;&#22833;:0 &#12458;&#12540;&#12496;&#12521;&#12531;:0 &#12501;&#12524;&#12540;&#12512;:0 
          TX&#12497;&#12465;&#12483;&#12488;:214 &#12456;&#12521;&#12540;:0 &#25613;&#22833;:0 &#12458;&#12540;&#12496;&#12521;&#12531;:0 &#12461;&#12515;&#12522;&#12450;:0 
          &#34909;&#31361;(Collisions):0 TX&#12461;&#12517;&#12540;&#38263;:0 
          RX&#12496;&#12452;&#12488;:15932 (15.9 KB)  TX&#12496;&#12452;&#12488;:15932 (15.9 KB) 

thomas@thomas-desktop:~$ 

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

thomas@thomas-desktop:~$ code spci -v| grep "VGA" 
bash: code: command not found 
thomas@thomas-desktop:~$ 
thomas@thomas-desktop:~$ | ifconfig 
bash: syntax error near unexpected token `|' 
thomas@thomas-desktop:~$ eth0      Link encap:&#12452;&#12540;&#12469;&#12493;&#12483;&#12488;  &#12495;&#12540;&#12489;&#12454;&#12455;&#12450;&#12450;&#12489;&#12524;&#12473; 00:c0:4f:cf:62:e2  
bash: eth0: command not found 
thomas@thomas-desktop:~$           UP BROADCAST MULTICAST  MTU:1500  &#12513;&#12488;&#12522;&#12483;&#12463;:1 
bash: UP: command not found 
thomas@thomas-desktop:~$           RX&#12497;&#12465;&#12483;&#12488;:0 &#12456;&#12521;&#12540;:0 &#25613;&#22833;:0 &#12458;&#12540;&#12496;&#12521;&#12531;:0 &#12501; &#12524;&#12540;&#12512;:0 
bash: RX&#12497;&#12465;&#12483;&#12488;:0: command not found 
thomas@thomas-desktop:~$           TX&#12497;&#12465;&#12483;&#12488;:0 &#12456;&#12521;&#12540;:0 &#25613;&#22833;:0 &#12458;&#12540;&#12496;&#12521;&#12531;:0 &#12461; &#12515;&#12522;&#12450;:0 
bash: TX&#12497;&#12465;&#12483;&#12488;:0: command not found 
thomas@thomas-desktop:~$           &#34909;&#31361;(Collisions):0 TX&#12461;&#12517;&#12540;&#38263;:1000 
bash: syntax error near unexpected token `Collisions' 
thomas@thomas-desktop:~$           RX&#12496;&#12452;&#12488;:0 (0.0 B)  TX&#12496;&#12452;&#12488;:0 (0.0 B) 
bash: syntax error near unexpected token `0.0' 
thomas@thomas-desktop:~$           &#21106;&#12426;&#36796;&#12415;:11 &#12505;&#12540;&#12473;&#12450;&#12489;&#12524;&#12473;:0xe000 
bash: &#21106;&#12426;&#36796;&#12415;:11: command not found 
thomas@thomas-desktop:~$ 
thomas@thomas-desktop:~$ lo        Link encap:&#12525;&#12540;&#12459;&#12523;&#12523;&#12540;&#12503;&#12496;&#12483;&#12463;  
bash: lo: command not found 
thomas@thomas-desktop:~$           inet&#12450;&#12489;&#12524;&#12473;:127.0.0.1  &#12510;&#12473;&#12463;:255.0.0.0 
bash: inet&#12450;&#12489;&#12524;&#12473;:127.0.0.1: command not found 
thomas@thomas-desktop:~$           inet6&#12450;&#12489;&#12524;&#12473;: ::1/128 &#31684;&#22258;:&#12507;&#12473;&#12488; 
bash: inet6&#12450;&#12489;&#12524;&#12473;:: command not found 
thomas@thomas-desktop:~$           UP LOOPBACK RUNNING  MTU:16436  &#12513;&#12488;&#12522;&#12483;&#12463;:1 
bash: UP: command not found 
thomas@thomas-desktop:~$           RX&#12497;&#12465;&#12483;&#12488;:214 &#12456;&#12521;&#12540;:0 &#25613;&#22833;:0 &#12458;&#12540;&#12496;&#12521;&#12531;:0  &#12501;&#12524;&#12540;&#12512;:0 
bash: RX&#12497;&#12465;&#12483;&#12488;:214: command not found 
thomas@thomas-desktop:~$           TX&#12497;&#12465;&#12483;&#12488;:214 &#12456;&#12521;&#12540;:0 &#25613;&#22833;:0 &#12458;&#12540;&#12496;&#12521;&#12531;:0  &#12461;&#12515;&#12522;&#12450;:0 
bash: TX&#12497;&#12465;&#12483;&#12488;:214: command not found 
thomas@thomas-desktop:~$           &#34909;&#31361;(Collisions):0 TX&#12461;&#12517;&#12540;&#38263;:0 
bash: syntax error near unexpected token `Collisions' 
thomas@thomas-desktop:~$           RX&#12496;&#12452;&#12488;:15932 (15.9 KB)  TX&#12496;&#12452;&#12488;:15932 (15.9 KB) 
bash: syntax error near unexpected token `15.9' 
thomas@thomas-desktop:~$ 
thomas@thomas-desktop:~$ thomas@thomas-desktop:~$ 
bash: thomas@thomas-desktop:~$: command not found 
thomas@thomas-desktop:~$

---

### Post by nyuwa on 2009-05-04
Thank you. I just registered there. Maybe people "at home" are closer to the source of the trouble ...

---

### Post by Ptero-4 on 2009-05-04
Looks like it at least detects your network card.
Also the other command was.
lspci -v
(I ommited the "VGA" part so that we can see both the videocard and ethernet card make/model).

---

### Post by nyuwa on 2009-05-04
Thank you. 
I will try that next too. Yet - I do not want to complain - fiddling with two computers (the one with Linux and the one with which I am sending you these messages) for hours on end (literally!) without making much visible progress is starting to interfer with my work ...

---

### Post by nyuwa on 2009-05-04
I am using a Dell GX 1 PIII 450 MHz, 256 MB RAM, currently a 20 GB HDD just for the purpose of trying it out.
Monitor: 15 inch CRT, Japanese maker used to be called "Nanao" but company name has changed to "EIZO". Model: Nanao Flexscan 33F

I found somewhere a note, saying, that Ubuntu 8.04 needs at least CPU: 700 MHz, RAM: 384 MB. So it seems, I am quite behing the minimal requirements. But that is the equipment I do have and unfortunately I cannot afford to buy me something new.

---

### Post by nyuwa on 2009-05-04
Well, I just tried that. Regardless of whether I use the <alt> key or not, the window, here I tried "network configuration", move to the left, right and downwards. But NOT upwards to show me what is at the bottom: namely the "OK", "Next", "changee" or whatever buttons. 
So, I am still driving blind.

---

### Post by nyuwa on 2009-05-04
Yes, it says "unknown host".

FDD: I did put in a FD, went to "Places",&#12288;but cannot find neither "FD", nor "mount" nor anything like that there.
Inserting a FD into a computer and read its context ... is that not something that has been done before the dawn of time and should not require any technical expertise?
Following the instructions in the "Pocket Guide" I finally found the folder "media" somewhere in the file system, but this does not show the FD either.
As it is, I still cannot figure out read/write a FD.

---

### Post by Ptero-4 on 2009-05-05
From the Dell specs sheet it says that you got and "3Com PCI 3C905B-TX" network card and an "ATI Rage Pro (AGP 2X) 4MB VRAM" videocard. The videocard should work with the "ati" driver (which comes included in xorg).

---

### Post by antmenj on 2009-05-06
> **nyuwa said:**
> I am using a Dell GX 1 PIII 450 MHz, 256 MB RAM, currently a 20 GB HDD just for the purpose of trying it out.
Monitor: 15 inch CRT, Japanese maker used to be called "Nanao" but company name has changed to "EIZO". Model: Nanao Flexscan 33F

I found somewhere a note, saying, that Ubuntu 8.04 needs at least CPU: 700 MHz, RAM: 384 MB. So it seems, I am quite behing the minimal requirements. But that is the equipment I do have and unfortunately I cannot afford to buy me something new.

You can install 8.04 on a P3 500 with 256mb ram and 800X600 15inch CRT screen.  It is slow but I have used one for basic web browsing, playing music, openoffice and even editing photos in gimp.

You will need that network icon back.  Try right clicking on the top bar and see if you can re add it.

---

### Post by nyuwa on 2009-05-14
Yes, I tried that in the meantime. Did not work at all!
It took the computer 40 minutes to display the "Install" icon, but clicking on that icon or hitting the enter key did NOT lead on to the installation.
What the computer showed me up to that point is horrible too: you have pull down menus with black characters on black background = you cannot read anything inside those menu boxes unless you "highlight" the text, which turns the characters white. If that is the intended design, the person who designed it, must not be from this planet ...

---

### Post by Didius Falco on 2009-05-14
Hi,

This is an useful command I just found out about a couple of days ago. If you enter ```
export LANG=  
``` into the Terminal, all output will be in English for that session.

That would help with the output translation problem.
If you run that command and then ```
xrandr
``` and post the output, we should be able to fashion a command that will temporarily make your screen readable. As a stopgap measure, you could even add that command to your Startup Programs until you can get the resolution problem resolved.

Adding it to the Startup Programs means it won't run until after the log in screen, and you will probably initially see the same resolution you do now, followed by the change in resolution - it will probably make your display "jump" a bit, but that is normal behavior for it.

Regards,

Didius

---

### Post by Niniel on 2009-05-14
Ubuntu should run on your box - I managed to boot the 8.10 live CD on a P2 333MHz with 192 MB of RAM - but it will be slow. 9.04 may require less power, but I would recommend you try another distribution. Zenwalk should work nicely on your computer, but a minimal distribution such as Puppy Linux or Damn Small Linux will be even better. But I don't know how good their Japanese language support is. 
However:
> International support has always been of utmost concern for Zenwalk Live and in keeping with this tradition, input support for some Asian languages through Uim has now been added as well as a new dedicated booting option for Japanese users.
[source]("http://support.zenwalk.org/viewtopic.php?f=2&t=23162")

Some people may recommend Xubuntu, but in my mind, Zenwalk is better (I liked the default desktop better and it runs better on my really old computer).

But if you want to continue with Ubuntu, it may not be a bad idea to start from scratch since you've been trying to fix things for a while.

---

### Post by spillin_dylan on 2009-05-15
Would it be possible to start with the Ubuntu Server Edition, and add everything else from there (GUI & Languages & apps)?  I'm thinking on hardware that's older, this might be the simpler way to go, to reduce unnecessary overhead.

---

