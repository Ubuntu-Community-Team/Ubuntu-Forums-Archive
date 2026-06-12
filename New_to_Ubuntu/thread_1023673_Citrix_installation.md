---
title: "Citrix installation"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by OllieGab on 2008-12-28
I'm trying to install the Citrix setup file: **setupwfc **but whether I choose just the RUN option or RUN FROM TERMINAL it just seems to stop; or rather nothing happens after that.

Any particular terminology I should use when installing a downloaded program (which has been unpacked) from the terminal?

Being new to Linux I "obviously" prefer the GUI method of doing things but I realise that I need to learn to use the command line as well.

Ollie

---

### Post by vanadium on 2008-12-28
I assume you managed to download and unpack the archive. The executable is unpacked in the same directory as the archive. Your current directory should be that of the executable (i.e. when you do "ls", "setupwfc" must be one of the files in the directory). Then you start the installer with the command

```

./setupwfc

```

---

### Post by linux_tech on 2008-12-28
open terminal (applications>accessories>terminal)
cd /home/user/download/citrix (folder where you downloaded setupwfc to)
in terminal type:
```

sudo ./setupwfc 
```

---

### Post by PilotJLR on 2008-12-28
After the setup is over... if you are using the citrix Web Interface, then firefox may ask you what app you want to use to open an .ica file. For ica files, tell it to open with the /usr/lib/ICAClient/wfica  program.

---

### Post by OllieGab on 2008-12-28
Well, I must be doing something wrong.
All I get is 'there is no file or directory with that name'...when there clearly is.
I tried to move the file around a bit, just i case I was in the wrong directory.

I also seem to have general problems with the **cd **command; ie just moving from one directory to another.

Is there a site with all the basic command a newbie would find useful?

Ollie

---

### Post by linux_tech on 2008-12-28
I found these, hope they are useful-
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Install_Citrix_ICAClient_10](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Install_Citrix_ICAClient_10)
[http://citrix.utipu.com/app/tip/id/2543/](http://citrix.utipu.com/app/tip/id/2543/)
[http://www.itgeeeks.com/how-to-install-use-citrix-ica-client-on-ubuntu-linux/](http://www.itgeeeks.com/how-to-install-use-citrix-ica-client-on-ubuntu-linux/)
[http://www.open-of-course.org/courses/mod/resource/view.php?r=367](http://www.open-of-course.org/courses/mod/resource/view.php?r=367)
[http://www.unixtutorial.org/commands/cd/](http://www.unixtutorial.org/commands/cd/)

---

### Post by PilotJLR on 2008-12-28
Ollie, are you using the dot-slash that the vandium and linux_tech showed?

If you type "setupwfc" in the terminal, then bash will try to find that program in your $PATH and execute it. But it's not in your path... the dot-slash prefix basically means to run the program in the current directory.

So if this file is on your desktop (for example), then:
```

cd ~/Desktop
sudo ./setupwfc

```

the tilde (~) means "home directory"

---

### Post by OllieGab on 2008-12-28
Yes, I did have some "problems" with the slashes and the dots in the right place. 
I did manage to install the program now (I think) but when I actually got as far as wanting to log into my work's server (which is why I needed the Citrix program) I was told I hadn't chosen to accept the server's security certificate. So I have obviously not succeeded completely!

---

### Post by OllieGab on 2008-12-29
Thanks everybody for advice and suggestions!
I finally managed to log onto where I wanted. As it turned out, what I needed in the end was a .crt file (contents copied from another forum which had to do with a similar problem with a Mac) made and placed in the 'cacert' folder i ICAClient main folder.
After re-starting Firefox it suddenly let me in!

I also did a few other changes and tweaks but was careful to do just one at the time but I'm pretty sure the added crt file is is what clinched it!

Ciao

Ollie:P

---

### Post by alek01 on 2011-06-20
Thanks a million PilotJLR! After many hours of trying installing Citrix on Natty 64Bits, I could see Citrix Receiver" in th eInternet menu but could NOT make it opne the .ICA file. I was close to throwing myself by the window (or having a drink to forget) when I discovered your directory link.
You've saved my day, or days... Thks!

---

