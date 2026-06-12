---
title: "Ubuntu, Kubuntu, Xubuntu, Which &quot;BUNTU&quot; is best for me????"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by Joe Ker1086 on 2009-11-06
I have been reading alot about all of the distros for Linux and I get a little confused when it comes to ubuntu. What exactly is the difference with all of the buntus? I know mythbuntu is centered around myth tv but what about the others? i noticed that ubuntu can be a little.....annoying when doing some things from terminal but i dont know if that is because im new to it. fedora will pretty much let you do what you want when you are super user but it was not quite as easy when using ubuntu. are any of the other buntu distros a little easier to use with terminal? or what is the main difference between them all?

---

### Post by Lateralis on 2009-11-06
The choice of Ubuntu distribution is largely due to personal preference. 

The nuts and bolts of the underlying operating system are the same across all of those editions of Ubuntu, except the desktop environment is different.  Ubuntu uses Gnome, Kubuntu uses KDE and Xubuntu uses the Xfce (essentially a stripped down version of Gnome for use on low power PCs and laptops).  

I personally use Gnome as I prefer the look and feel.  Others will tell you that KDE is better and more flashy but I find it irritating.  So it truly is a matter of personal taste as each operating system is basically identical.  Perhaps the best thing to do would be to burn LiveCDs of each flavour of Ubuntu and try each one out.  You might find you prefer Gnome to the others, or find Gnome ugly and plump for KDE.  Experiment and see what happens. =)  


As for the command line... doing things using the command line is just as easy as it is in Fedora, or any other Linux distro, so long as you are aware that you don't really initiate a root shell session in the same way as other distributions.  Debian based systems, such as Ubuntu, use the "sudo" command in order to give the shell temporary super user ('root') privileges.  This means you can make changes to the system, install updates and whatnot.  If you really want to, you can log yourself in as root in a terminal by typing the following into the command line 

```
sudo -i
```

followed by your password.  You can exit out of this root shell, returning to a default shell, by typing *exit*. However, doing this **is not recommended and is strongly discouraged** as a terminal with root privileges can change anything about your system. 

Instead, if you ever need to do anything using the command line that needs root privileges, preceed the command by typing sudo.  So for example if you wanted to edit a system file you should type 

```
sudo nano <file>
``` 

to open <file> using the command line editor nano with root privileges.  


The reason Ubuntu uses this system is a simple one: security.  


Hope this makes sense and is of some use. =)

---

### Post by Darce on 2009-11-06
[http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29#Variants](http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29#Variants)

Differences are the different desktop environments (Gnome,KDE, etc ) and installed/standard applications

---

### Post by jbrown96 on 2009-11-06
In Linux, almost everything that can be divided into a smaller piece is. There's a Unix saying that software should do only one task and do it very well. This is really important to understanding the way linux works. 
As far as Kubuntu, Xubuntu, and Ubuntu:
They refer to the desktop environmnet that is the default. A desktop environment includes quite a bit. It's the way that widgets and title bars look, the default applications, how the desktop looks, and how the user sets system settings. Choosing one is a personal choice; there isn't one that's necessarily better unless you have a really slow system then try Xubuntu first. KDE (Kubuntu) is designed to be a complete solution (can't think of a better phrase). There are a million tweaks you can make to it (but don't need to), and it generally has more glitz to it. I really like and use it exclusively. Gnome (Ubunutu) is designed for stability and consistency. I would say that it is the most "corporate" of DEs. It doesn't radically change things often, and you will unlikely to have stability problems. It's the default for most Linux varieties (including Ubuntu). Xubuntu is pretty similar to Gnome (in fact it uses GTK, which is the basis for Gnome), but is designed for slow systems. I've used it a couple times, and it didn't really seem to offer anything over Ubuntu. I'd recommend Ubuntu to start; you will be able to get better support on the forums. Check out KDE at some point.
The terminal is going to be practically the same no matter what distribution you use. There are some differences, but they are not important if you have a guide or some experience. Getting to know the command line is part of Linux, and while there are some distributions that avoid the terminal, they tend to have other problems. You will find most help on the forums uses the terminal because it's faster to help people. All of the graphical settings are just front-ends for a terminal command. It's easy to get lost trying to navigate a complex window, but a command is never ambiguous. If you really want to stay away from the terminal, you could try a distribution that has more graphical configuration. I'd recommend Mandriva or OpenSUSE; they also have the best KDE implementations, so if you want to try KDE. 
Ubuntu is a really good distribution. I started using it three years ago, with zero experience. There were some things that were tough, but you learn quickly. There are so many resources on the net to get your problem solved. A huge percent of Linux users run Ubuntu, so it's the easiest to get support. Just a word of caution: make sure to check the date of any resources you find. Linux changes quickly, and help that was valid a year ago, may no longer be true. 

Man (manual) pages are a really good resource. When you are starting out, you'll probably get a lot of help that will include commands to run. You can find out what the command does by running ```
man COMMAND
``` use the arrow keys to scroll and q to quit. This will build your knowledge very quickly.

Best of luck.

---

### Post by Joe Ker1086 on 2009-11-06
Thanks Lateralis, that helped alot.

---

### Post by Joe Ker1086 on 2009-11-06
> **jbrown96 said:**
> In Linux, almost everything that can be divided into a smaller piece is. There's a Unix saying that software should do only one task and do it very well. This is really important to understanding the way linux works. 
As far as Kubuntu, Xubuntu, and Ubuntu:
They refer to the desktop environmnet that is the default. A desktop environment includes quite a bit. It's the way that widgets and title bars look, the default applications, how the desktop looks, and how the user sets system settings. Choosing one is a personal choice; there isn't one that's necessarily better unless you have a really slow system then try Xubuntu first. KDE (Kubuntu) is designed to be a complete solution (can't think of a better phrase). There are a million tweaks you can make to it (but don't need to), and it generally has more glitz to it. I really like and use it exclusively. Gnome (Ubunutu) is designed for stability and consistency. I would say that it is the most "corporate" of DEs. It doesn't radically change things often, and you will unlikely to have stability problems. It's the default for most Linux varieties (including Ubuntu). Xubuntu is pretty similar to Gnome (in fact it uses GTK, which is the basis for Gnome), but is designed for slow systems. I've used it a couple times, and it didn't really seem to offer anything over Ubuntu. I'd recommend Ubuntu to start; you will be able to get better support on the forums. Check out KDE at some point.
The terminal is going to be practically the same no matter what distribution you use. There are some differences, but they are not important if you have a guide or some experience. Getting to know the command line is part of Linux, and while there are some distributions that avoid the terminal, they tend to have other problems. You will find most help on the forums uses the terminal because it's faster to help people. All of the graphical settings are just front-ends for a terminal command. It's easy to get lost trying to navigate a complex window, but a command is never ambiguous. If you really want to stay away from the terminal, you could try a distribution that has more graphical configuration. I'd recommend Mandriva or OpenSUSE; they also have the best KDE implementations, so if you want to try KDE. 
Ubuntu is a really good distribution. I started using it three years ago, with zero experience. There were some things that were tough, but you learn quickly. There are so many resources on the net to get your problem solved. A huge percent of Linux users run Ubuntu, so it's the easiest to get support. Just a word of caution: make sure to check the date of any resources you find. Linux changes quickly, and help that was valid a year ago, may no longer be true. 

Man (manual) pages are a really good resource. When you are starting out, you'll probably get a lot of help that will include commands to run. You can find out what the command does by running ```
man COMMAND
``` use the arrow keys to scroll and q to quit. This will build your knowledge very quickly.

Best of luck.

Appriciate how in depth you got, you both gave me a couple things to think about. Thanks again.

---

### Post by kio_http on 2009-11-06
If your machine is capable of running XP then I'd say chose Kubuntu, if Xp runs but very slow then Ubuntu, if it can run win 98 or below Xubuntu. 

Not if you have less then 384 mb ram use the alternate iso 

However if the machine is extremely old you might consider puppy Linux.

---

### Post by Joe Ker1086 on 2009-11-06
Im sure it will have no problem running any of the linux distros. The only problem i have had with ubuntu is the graphics are a little glitchy....but i think that is cuz i am using an ati radeon card and it has specific drivers.

---

