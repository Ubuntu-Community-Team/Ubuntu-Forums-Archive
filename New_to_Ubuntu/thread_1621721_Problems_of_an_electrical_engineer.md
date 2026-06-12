---
title: "Problems of an electrical engineer"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by mustafa.alberta on 2010-11-14
Hi friends,
I'm glad to be a member of this open source community. I'm from Iran and using Ubuntu 10.04 lucid lynx on acer aspire 5251-1513 laptop. There is no problem of detecting hardware, but I encounter lots of software circumstances.If you'd mind helping me to solve these false?
1.I couldn't find any software for electronic! such as " mat lab,spice,Verilog HDL and so on.
2.It can connect to the wireless network and of course I can surf on the net, but I couldn't download any package from Ubuntu software center. Also I use CD form of Ubuntu.what could be the matter?
3.When I want to compile a .tar ball file,after typing
" ./configure " it says:" ./configure : no such file or directory"
Also I extract it and I go to the directory of path file with " CD command ".
4.How can I install .jar file on it?
5.If the answer is " wine ", I prefer to use " fedora FEL "
than it.And I don't have any internet access. I use university VPN wireless network with limit of M byte size of downloading?
Thank you:(

---

### Post by J V on 2010-11-14
> I couldn't find any software for electronic! such as " mat lab,spice,Verilog HDL and so on.
2.It can connect to the wireless network and of course I can surf on the  net, but I couldn't download any package from Ubuntu software center.  **Also I use CD form of Ubuntu**.what could be the matter?
3.When I want to compile a .tar ball file,after typing
" ./configure " it says:" ./configure : no such file or directory"
Also I extract it and I go to the directory of path file with " CD command ".
4.How can I install .jar file on it?
5.If the answer is " wine ", I prefer to use " fedora FEL Until you install ubuntu none of what you ask here can be done...

---

### Post by arvevans on 2010-11-14
As long as you are running from the Live CD, you will have some limitations of what can be downloaded and installed because you are running on a virtual-RAM based file system.  Also, any software that you do get downloaded and installed will probably go away when you reboot.

As the prior poster suggested, you really need to install Ubuntu to your hard disk.  You could try doing this with a larger (8 GB or so) pen-drive, but response times might be slower than expected.

There are many electronics related programs available in the Ubuntu repositories, and many more available for download from the Internet.  
I (also an EE) use these:
[LIST]
[*]**Eagle CAD** (schematic & pcb editor)
[*]**gEda programs** (several are available)
[*]**Gerbv** (Gerber file viewer to see CNC input files)
[*]**Arduino IDE** (for Atmel AVR chip programming)
[*]**electric** (simple minded electronics cad program)
[*]**kicad** (electronics CAD program)
[*]**Oregano** (simple schematic capture and simulation)
[*]**PCB Designer** (for PCB layouts)
[*]**piklab**  (for programming PIC microcontrollers)
[*]**qucs** (Universal Circuit Simulator)
[*]**tkgate**  (digital circuit simulator)
[*]**xoxcope**  (sound card based oscilloscope)
[*]**GTK Smith Chart Calculator** (RF impedance calculator)
[*]**LTSpice**  ((runs in WINE, this is spice optimized for electronics)
[*]**PCB123**  (runs in wine.  Integrated schematic & PCB editor)
[*]**Wavestar**  (Tectronics instrument control software)
[*]**Windaq**  (runs in WINE.  data collection & controller from DAQ)
[/LIST]

And there are many more available both via the Ubuntu repository and that can be downloaded and run either in Linux or as windows software using WINE.

I have also written many shell-script programs as quick solutions for specific problems.  If you go the Linux route you really need to know a scripting language so you can build little tools for solving simple and frequently recurring problems.

Linux and an EE is a fun combination.

---

### Post by mustafa.alberta on 2010-11-15
hi friends,
Thank you for your regards on me.
About problems I should say that I installed Ubuntu on my laptop and I always boot it from hard drive.I never use live CD.
Thanks

---

### Post by anewguy on 2010-11-15
The "standard" procedure for tar (compressed) files is to create a new folder and untar (extract) the files into the folder, then cd to the folder before trying any of the ./configure, make, etc..  This is similar to a "zip" file in that there can be many files, including subfolders, within this single tar file that all need to be extracted before you can do anything with them.

As far as your other problems go, perhaps your software repositories aren't correct.  Do they limit them somehow in your country?  

Dave ;)

---

### Post by matt_symes on 2010-11-15
Hi

> The "standard" procedure for tar (compressed) files is to create a new  folder and untar (extract) the files into the folder, then cd to the  folder before trying any of the ./configure, make, etc..That is good, however to expand on it there should be a file called README in the directory of the extracted tar that will contain instructions of how to build the software. There are a number of different ways.

> 
Until you install ubuntu none of what you ask here can be done...This is also correct. If you are using a liveCD all the time then you will need to install Ubuntu either as a dual boot or exclusively on your laptop

You can also use matlab on ubuntu. An alternative is Octave

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)
[http://www.gnu.org/software/octave/](http://www.gnu.org/software/octave/)

for .jar files read

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=541055](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=541055)


I do believe you will need an internet connection though (more MB than University). It is vital in this day and age. Internet Cafe? Friends place?

Kind regards

---

### Post by mustafa.alberta on 2010-11-15
hi,
Lots of files with . tar ball don't have read-me file or install.
instead i use :
"./configure
  make
  sudo make install"
on the other hand i use dual boot 7 with Ubuntu.
maybe i need to install a DVD of Ubuntu.but i don't have link.
if you'd mind giving me the direct link of Ubuntu DVD?
i should go to the internet cafe...    
:(:confused:

---

### Post by AngusH on 2010-11-15
> **arvevans said:**
> I have also written many shell-script programs as quick solutions for specific problems.  If you go the Linux route you really need to know a scripting language so you can build little tools for solving simple and frequently recurring problems.

I have to disagree with this. Knowing how to script is useful (knowing how to program in a fuller language is even more useful) and as it happens I am able to do both to a limited level, but I've never ever had to. Linux has come on a long way and has long since passed the point where the average user will never have to go near a terminal or some obscure config file if they don't want to. Nearly everything you need to do is already possible.
Just my 2 cents.
Angus

---

### Post by anewguy on 2010-11-16
> **mustafa.alberta said:**
> hi,
Lots of files with . tar ball don't have read-me file or install.
instead i use :
"./configure
  make
  sudo make install"
on the other hand i use dual boot 7 with Ubuntu.
maybe i need to install a DVD of Ubuntu.but i don't have link.
if you'd mind giving me the direct link of Ubuntu DVD?
i should go to the internet cafe...    
:(:confused:

When the file has come as a .tar, the normal procedure IS to configure, make and make install.  However, you do need to untar each to a seperate folder - don't untar all of your tars to the same folder or you'll REALLY have a mess.

After having untar'ing the file, change working directory to the folder you untar'd into (e.g, if the folder is "mytemp", then "cd mytemp", THEN do the configure, make, make install.

That's the normal procedure for this.

If you continue to have problems, copy the screen output from when you try to untar and then when you try to configure and post it back here so we can see what it is.

Dave

---

### Post by mc4man on 2010-11-16
> Until you install ubuntu none of what you ask here can be done..
A moot point to the Op, but still, as a statement, is pure nonsense.

---

### Post by anewguy on 2010-11-16
> **mc4man said:**
> A moot point to the Op, but still, as a statement, is pure nonsense.

+1    

Of course, moot rhymes with coot, and I'm an old one, so perhaps I'm getting senile ;)

---

### Post by Blutkoete on 2010-11-16
> **mustafa.alberta said:**
> 
1.I couldn't find any software for electronic! such as " **mat lab**,spice,Verilog HDL and so on.


There's a native version of *MATLAB* for Linux, but you won't find it in the repositories as it's non-free software which you'll have to get from the vendor's homepage. *Octave* is kind of a open-source alternative to *MATLAB* though (if you don't require special toolboxes).

---

