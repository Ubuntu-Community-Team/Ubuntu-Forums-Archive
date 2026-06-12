---
title: "Hardware Driver GUI Stupidness"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by SupLox on 2009-01-18
I'm super new to Ubuntu but not a stranger to mac or PC "os's." I installed ubu yesterday and it seems pretty cool but one thing is really bothering me. I'm stuck in 800x600 display mode. I go to the resolution settings panel and there is no option for anything higher. So, I figure it must be the Display driver. I hit the Hardware driver panel and it says " No Proprietary drivers are in use on this system" I see three options tn the box and I go for the recommended one, NVIDIA accelerated graphics driver (version 117). I hit the activate button and it asks for my password, then I get the downloading and installing box. But it stays on the 0% for about 5 minutes and then it goes back to the hardware drivers box with no change except for when I press activate again i get 2 minutes of nothing. not even a dialog box. just an indented activate button.

I havent given up yet, so I go to the NVIDIA site and download a Linux driver compatible with my on-board card. The file has an exension of  ".run" Double click, and gedit opens and it says it cant read the character encoding. now i'm lost and i need to be found. any ideas?:confused:

---

### Post by mjheagle8 on 2009-01-18
are you connected to the internet? it sounds like it is not able to download the driver you need to use.

---

### Post by SupLox on 2009-01-18
of course that is how I got the ".run" package from the NVIDIA site. I wish it was that simple. :P

---

### Post by mjheagle8 on 2009-01-18
try the envyng utility. its good for handling nvidia drivers.

---

### Post by SupLox on 2009-01-18
sounds like a bet. but where would I find that?

---

### Post by mjheagle8 on 2009-01-18
i think it is in the repositories. try ```
sudo apt-get install envyng
```

---

### Post by oldos2er on 2009-01-18
You might want to try changing servers to get the driver through Hardware Drivers. Go to the menus System, Administration, Software Sources, click the tab next to 'Download from', 'Other,' Select Best Server.'

---

### Post by SupLox on 2009-01-18
so hit <ctrl> <alt> <f1> and type that in?

---

### Post by abyssius on 2009-01-18
SupLox

To install the NVIDIA .run file. You'll have to put your computer into a command line only mode (e.g. make sure you're not running x-server). Then at the command prompt, you have to issue the command: 
sh <the_name_of_your_nvidia.run_file>. If you try this, you could run into some further complications that require you to perform additional command line techniques.

I have a feeling this is not something you want to tackle just yet. It sounds like when you tried to install the restricted driver, your computer failed to access the Ubuntu repository on the Internet. As you pointed out you must have Internet access if you downloaded the nvidia driver.

I would recommend that you install a program called Envy. This will provide a way for you to easily install the driver you need.

The fastest way to install Envy is to open a terminal and type the following command:

```

sudo apt-get install envyng-core

```

After it's finished installing, you can run Envy from the terminal by typing:
```

envyng -qt

```

This will run a simple GUI program that will guide you through the install. I hope this helps.

---

### Post by SupLox on 2009-01-18
ok im in the command line and i was using the textual interface for envyng I selected the 177 update and it started dowloading the packages. I got an error in the function pulse and some other things that are too long to type verbatim.:confused:

---

### Post by mjheagle8 on 2009-01-18
can you copy and paste the error message(s)?

---

### Post by jimmy the saint on 2009-01-18
I know you already started, but it sounds to me like all you needed to do was change the download server.  This has happened to me every time I update ubuntu for some reason.  Just change it is synaptic.

System>administration>synaptic package manager

Then Settings>repositories
where it says "download from" select other in the dropdown
press the "select best server" button and let it use the one it selects

In addition to fixing your driver download, it will probably make updates go faster.  It is a hell of a lot easier than installing an nvidia driver manually, especially if you haev little experience.

---

### Post by SupLox on 2009-01-19
ok now that i'm using a windowed terminal I get a different error: 
   Error:                                                              |
 |                                                                        |
 |    EnvyNG has detected that one of the following                       |
 |    applications is running: dpkg, apt-get,synaptic,update-manager,     |
 |    adept, adept-notifier. Make sure that they                          |
 |    are not running and launch EnvyNG again.                            |
 |    If this is not the case, make sure that                             |
 |    your Internet connectionis working properly                         |
 |                                               

I has to be working because i'm using the forums

When i press crtl alt f1 and do the same I get  a different error. and I cant copy it from that screen

---

### Post by therevEJW on 2009-04-08
i'm having this same issue... i had to re-install Ubuntu (8.10) this morning due to stupidity on my part with partitions and for some reason the Hardware Driver will not download or install the drivers.  It worked just fine the last time I did it.

I've tried the envyng approach also, but i get an even stranger set of problems that way... i really REALLY need help

---

