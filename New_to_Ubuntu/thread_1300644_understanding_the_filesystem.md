---
title: "understanding the filesystem"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by ni ni on 2009-10-25
Hello all!

I have linux on my laptop, i struggle away with not many computer skills....

i don't really understand the file hierarchies. where can i find this?

~/.local/share/vlc/skins2

thank you very much in advance!!!:KS:KS:KS

---

### Post by Vaphell on 2009-10-25
~ = your home directory, it is a substitute for /home/yourname/
.local is hidden because it starts with a dot, you need to ctrl+h (show hidden files in nautilus)

so full path would be /home/yourname/.local/share/vlc/skins2

---

### Post by vinutux on 2009-10-25
> **Vaphell said:**
> ~ = your home directory, it is a substitute for /home/yourname/
.local is hidden because it starts with a dot, you need to ctrl+h (show hidden files in nautilus)

so full path would be [COLOR="Red"]/home/[COLOR="Sienna"]yourname[/COLOR]/.local/share/vlc/skins2[/COLOR]

+1 

Also check this link for know more about file system in linux [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/")

---

### Post by ni ni on 2009-10-25
wow!


thanks Vaphell

just for answering that so quickly i understand a lot more now!

---

### Post by ni ni on 2009-10-25
Thanks vinutux!

i've been using only linux since December with no windows.  i can't believe how much i don't know!

---

### Post by Pioneer5000 on 2009-10-25
That should be in your home folder.

If you are wanting to get there without using terminal. Just go into your home folder, so eg. "/home/bob". The "." in front of local means its hidden. So push ctl + h to show all hidden files, then just look for
local ->share -> vlc ->skins2

---

### Post by ni ni on 2009-10-25
thanks Pioneer5000 x x x

---

### Post by halitech on 2009-10-25
> **ni ni said:**
> Thanks vinutux!

i've been using only linux since December with no windows.  i can't believe how much i don't know!

getting into linux is a very humbling experience :neutral: I used to think I was a power user when I was using windows and converting over made me realize just how little I actually knew about computers and how they worked. Things will come to you over time and you'll need to come here less and less for help and you'll be helping others more and more with their issues :D

---

### Post by ni ni on 2009-10-25
LOL I know!

halitech, that name is familiar - i think you've helped me before!

---

### Post by Rifester on 2009-10-25
Thanks for posting this link, I have been looking for something like this.    I also am a new Linux user.   Could you also suggest a sight to learn basic commands in terminal.    I have been gaining knowledge in this area but would like to learn more.

Thanks,

Mark

---

### Post by halitech on 2009-10-25
> **ni ni said:**
> LOL I know!

halitech, that name is familiar - i think you've helped me before!

quite possible, I've hopefully helped alot of people during my time here

---

### Post by vinutux on 2009-10-25
> **halitech said:**
> getting into linux is a very humbling experience :neutral: I used to think I was a power user when I was using windows and converting over made me realize just how little I actually knew about computers and how they worked. Things will come to you over time and you'll need to come here less and less for help and you'll be helping others more and more with their issues :D

100% agreed.... i learned more about computers... after switched to Linux.... before that  i am clicking on someone else commands That he not willing to share..........

---

### Post by ni ni on 2009-10-25
> **MRife said:**
> Could you also suggest a site to learn basic commands in terminal.    I have been gaining knowledge in this area but would like to learn more.



+1 i need this toooooo

---

### Post by ni ni on 2009-10-25
> **vinutux said:**
> clicking on someone else commands That he not willing to share..........

hate that! open source forever!

---

### Post by halitech on 2009-10-25
> **vinutux said:**
> 100% agreed.... i learned more about computers... after switched to Linux.... before that  i am clicking on someone else commands That he not willing to share..........

same here and I'm willing to admit that I still don't know it all or consider myself anything above newbie and thats after almost 3 years of using linux

---

### Post by vinutux on 2009-10-25
> **MRife said:**
> Thanks for posting this link, I have been looking for something like this.    I also am a new Linux user.   Could you also suggest a sight to learn basic commands in terminal.    I have been gaining knowledge in this area but would like to learn more.

Thanks,

Mark

Just googling for linux Cheat sheat there are alot of pdf too

here is a basic commands [URL="http://www.tuxfiles.org/linuxhelp/linuxcommands.html"]http://www.tuxfiles.org/linuxhelp/linuxcommands.html
[/URL]

---

### Post by loomsen on 2009-10-25
> **ni ni said:**
> +1 i need this toooooo

Here's a wallpaper with the most common commands. ask google for cheatsheets to find more.

[http://omploader.org/vMm05Nw](http://omploader.org/vMm05Nw)

---

### Post by vinutux on 2009-10-25
> **loomsen said:**
> Here's a wallpaper with the most common commands. ask google for cheatsheets to find more.

[http://omploader.org/vMm05Nw](http://omploader.org/vMm05Nw)

Wow that WP is rocking....

And check this one **[[COLOR="Red"]25+ linux Cheat sheets PDFs[/COLOR]]("http://www.techieblogger.com/2009/10/linux-unix-ubuntu-solaris-cheat-sheets.html")** **[http://www.techieblogger.com/2009/10/linux-unix-ubuntu-solaris-cheat-sheets.html]("http://www.techieblogger.com/2009/10/linux-unix-ubuntu-solaris-cheat-sheets.html")**

---

### Post by ni ni on 2009-10-25
Thanks soooo much!

for example, do you always have to do lsusb to make a digital cmera appear in the system? (i do anyway)

---

### Post by ni ni on 2009-10-25
oh that wallpaper is beyond me :-/

I can't understand a bit of it


i love the design tho!!!!!!

---

### Post by loomsen on 2009-10-25
> **ni ni said:**
> Thanks soooo much!

for example, do you always have to do lsusb to make a digital cmera appear in the system? (i do anyway)

lsusb= list usb devices

So, if it appears in lsusb, it did already appear in your system

*edit*
CLI = Command Line Interface

so, typing any of the commands into a terminal will do what the explanation says :)

---

### Post by ni ni on 2009-10-25
i mean if i connect it and leave it half an hour the system wont pick it up - until i run lsusb a few times.  is that normal?

---

### Post by loomsen on 2009-10-25
Actually not no.

But I haven't been running ubuntu for some time now, guess I can't help you there.

---

### Post by ni ni on 2009-10-25
okay kein sorge

---

### Post by ajgreeny on 2009-10-25
Another terrific command index here; click on any of them to go to the details of what it does.
[http://ss64.com/bash/](http://ss64.com/bash/)

---

### Post by hal10000 on 2009-10-25
More detailed info about bash and scripting you can get here:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
A lot of scripts can be found here:
[http://www.intuitive.com/wicked/wicked-cool-shell-script-library.shtml](http://www.intuitive.com/wicked/wicked-cool-shell-script-library.shtml)
[http://www.shelldorado.com/](http://www.shelldorado.com/)

---

### Post by ni ni on 2009-10-25
thanks everyone!!!!!!!!

---

### Post by noelvh on 2009-10-25
I have been using Ubuntu for a few years now, and still think of my self as a novice! One tool I have found is Ubernote, this is a firefox addon the I use to take notes as I go, and I can access them from any computer on the internet. 

When I troll through the forums and find some thing I copy it and put it into a note. I am all ways forgetting commands and the like as I do not use them all the time. So I open Ubernote and find what I need.

I also poke the forum's new posts a few times a day to see what I can learn.

Noel

---

### Post by vinutux on 2009-10-25
> **noelvh said:**
> I have been using Ubuntu for a few years now, and still think of my self as a novice! One tool I have found is Ubernote, this is a firefox addon the I use to take notes as I go, and I can access them from any computer on the internet. 

When I troll through the forums and find some thing I copy it and put it into a note. I am all ways forgetting commands and the like as I do not use them all the time. So I open Ubernote and find what I need.

I also poke the forum's new posts a few times a day to see what I can learn.

Noel

in karmic (9.10) you can use Tomboy notes with **ubuntu one** and it accessible from any computers..........

---

