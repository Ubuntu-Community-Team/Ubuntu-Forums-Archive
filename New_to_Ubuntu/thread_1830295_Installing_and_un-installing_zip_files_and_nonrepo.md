---
title: "Installing and un-installing zip files and nonrepository platform independent filesFi"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by PcMojo on 2011-08-21
[SIZE=3]First of all, I want to thank the thousands of contributors and the forum itself for the tons of knowledge you make available to us and the endless hours spent helping others. I've been using linux for about two years and have not made many posts - because I haven't had to. :) I've trashed my system at least a half dozen times and have been able to recover it just by reading others' posts.  Thank you all very much! (I'd give you all a "thumbs up" smilie, but I can't find one, so have some :popcorn: instead!)

On to my questions.  I come from an Ms world and  while I understand zip files and exe files, I don't understand platform independent applications. I usually install Linux applications through KpackageKit or Synaptics because it's easy, I feel safer, and I can uninstall without wasted cleanup efforts. I don't go out to the internet and randomly download and install programs. But recently, I came across a very large suite of platform independent applications that I really want to try. They are only available as a zip file. If I like them I will eventually install them on another computer, but I want to try them on this, my current Kubuntu:KS PC. Regardless of whether I like them or not, I will eventually un-install them from this pc. My questions are these:

1) How do I install platform independent zip files into Kubuntu? - I've seen tutorials showing how to unzip in linux, but in M$ I knew to look for an exe, usually setup.exe to run the install program. Since it is platform independent, do I run setup.exe or is there usually an equivalent  linux file I should be looking for?
2) Since I am **not** using a package manager to install this program, will I still be able to uninstall through a package manager? If there is an uninstall.exe, since it's platform independent, can I use that in linux to uninstall later or will that just work in M$? Is there an easy way to manually uninstall all the files in linux (perhaps save a log file to undo changes later)?

This package is big. It's called OrangeHrm. From what I understand the applications are web based, but not internet based. It installs apache to serve them up and uses MySql (or another db). I want to try it out but I don't want to get stuck with waiting for a web server and database at startup forever, I know I will uninstall them. I just want to know the best way to go about this ahead of time so I don't have to format and reinstall Kubuntu from scratch. :((Finally got in juuuuussst right!):cool:

Any advice would be greatly appreciated![/SIZE]

---

### Post by bkratz on 2011-08-21
Don't know what version you are using, but here is one about 10.04

[http://www.whiteleytech.ie/articles.php#Installing_OrangeHRM_on_Ubuntu_Server](http://www.whiteleytech.ie/articles.php#Installing_OrangeHRM_on_Ubuntu_Server)

---

### Post by gandaran on 2011-08-21
zip or tar files are just archives that can contain anything, they are not executable files, you just unpack the archive then see whats inside, they can in case of applications contain source code which need compiling or install scripts or even ready executable applications, usually inside the archive is a readme file with install instructions which you must read as there are many different ways to install things on Linux.
>  Since I am not using a package manager to install this program, will I still be able to uninstall through a package manager?
only if you use .deb packages (which are similar to .exe windows files) you can uninstall from package manager, any other install package type (there many for linux) have other uninstall methods.

---

### Post by PcMojo on 2011-08-21
Thanks a lot! The instructions are great! I'm excited to get under way, but I have learned to restrain my enthusiasm. Since working on Linux, I've found that although it is a very stable & secure system, it is very easy to trash if you don't know what you are doing. :o These days, when I get enthusiastic about a Linux project I force myself to stop, 
                                                           take 10 deep breaths, 
                                                                                                  and chant my new mantra -  I call them my 
[INDENT][SIZE=3][COLOR=Red]Linux Learnin' Lumps:[/COLOR][/SIZE]
[/INDENT][SIZE=2][COLOR=Red]1) I promise to back up, even if I think I know what I am doing.
2) I promise to read ALL the instructions **before** I touch my keyboard or mouse.[/COLOR][/SIZE][SIZE=2][COLOR=Red]
3) I promise to research commands before I type "sudo" and to have at least a[/COLOR][/SIZE][SIZE=2][COLOR=Red] basic understanding of what a command does before I hit enter.[/COLOR][/SIZE]

With that said, I'm going to get to work on this.
Thanks for all of your help!

---

