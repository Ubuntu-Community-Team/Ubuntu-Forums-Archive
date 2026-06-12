---
title: "Unable to get Assembler for Ubuntu 9.04"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by diabolator2 on 2009-10-13
Hi, all! Could anybody tell me how to get a "Turbo Assembler"(or better) for my Ubuntu 9.04? If yes, direct me through the installation steps, please. Thanks! 

By the way, I got Eclipse, could it contain Assembler IDE?

---

### Post by lkraemer on 2009-10-13
Assuming that Turbo Assembler DOES NOT use an Install program.....

If it does use an install program try Crossover or Wine.

If you want to use Turbo Assembler, why don't you try installing
DosBox from Synaptics Package Manager and then just create a folder
in your home like this: /home/loginname/C:

Copy all your Turbo Assembler files into a folder TurboAssembler
under C:
Then in DosBox use:
Mount c C:

Then change to C: from Z: in DosBox

Then cd TurboAssembler and 

Off you go to Playing in Assembler.... Jusy like DOS!

To unmount use:
mount -u C:

Read the Intro & 
[http://www.classicdosgames.com/tutorials/dosbox.html](http://www.classicdosgames.com/tutorials/dosbox.html)


A86 and D86 might still be around.  Search with Google.

There are several for Linux.  Search with Google.
Nasm, Yasm are in Synaptic Package Manager.

lk

---

### Post by falconindy on 2009-10-13
The popular assemblers for Linux are GAS and Netwide. They have similar syntax, and are both available in the repositories in the packages 'as' and 'nasm'.

Geany (a text editor) integrates support for NASM, but not a linker. I'm sure there's a way to solve that, and I assume that integration for the GAS assembler is available as well.

---

### Post by Jerry N on 2009-10-13
If you are talking about the same Turbo Assembler that I used, that is one REALLY OLD piece of software.  I think I dumpstered my Turbo Assembler floppies and documentation a really long time ago, probably along with Wordstar.

Jerry

---

### Post by rCXer on 2009-10-14
Another open source assembler you could try is FASM. It was partially inspired by TASM's "ideal mode" but its not in Ubuntu's repositores yet.  You can download the linux version [here](http://flatassembler.net/download.php) and its forum is [here](http://board.flatassembler.net). Just copy the fasm executable to your "/usr/bin/" directory.  Very few tutorials are available for it though...

---

### Post by diabolator2 on 2009-10-15
EVERYBODY, thanks! I'm sure I would get through all this with your help above. Thanks again!!

---

