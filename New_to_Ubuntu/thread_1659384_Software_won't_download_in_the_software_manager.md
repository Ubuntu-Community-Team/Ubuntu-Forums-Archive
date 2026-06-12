---
title: "Software won't download in the software manager?"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by bennoculus on 2011-01-03
I'm a pretty new Linux user here, but not computer illiterate at all.

Everytime I try and download a program from the software manager in Ubuntu, I'm getting an error message. Whether it be virtualbox, Vuze, or anything else. Nothing will download. It will go into an error message.

I have Ubunutu 10.10, it's a fresh install. I didn't install all of the updates when the window first popped up, simply because I was being an idiot. Could this be contributing to this problem?

My internet connect is valid, I'm wired via ethernet. I have a dual install of Linux mint 10 on another disk in the computer, and that OS's software manager works just fine at install applications.

I did try and search and couldnt find anything.

I even googled for command lines to manually install the programs, but none of them seemed to work. Any ideas for a command line to use?

Thanks in advance!

---

### Post by plucky on 2011-01-04
> **bennoculus said:**
> I'm a pretty new Linux user here, but not computer illiterate at all.

Everytime I try and download a program from the software manager in Ubuntu, I'm getting an error message. Whether it be virtualbox, Vuze, or anything else. Nothing will download. It will go into an error message.

I have Ubunutu 10.10, it's a fresh install. I didn't install all of the updates when the window first popped up, simply because I was being an idiot. Could this be contributing to this problem?

My internet connect is valid, I'm wired via ethernet. I have a dual install of Linux mint 10 on another disk in the computer, and that OS's software manager works just fine at install applications.

I did try and search and couldnt find anything.

I even googled for command lines to manually install the programs, but none of them seemed to work. Any ideas for a command line to use?

Thanks in advance!

Open a terminal **(Applications > Accessories > Terminal)** and post output of ```
sudo apt-get update
cat /etc/apt/sources.list
```

Good Luck

---

### Post by jonesyp on 2011-01-04
Are you able to access the internet via Firefox?

Kind regards

Peter Jones
[www.simplysowseeds.co.uk](www.simplysowseeds.co.uk)

---

### Post by oldos2er on 2011-01-04
> **bennoculus said:**
> Everytime I try and download a program from the software manager in Ubuntu, I'm getting an error message. 

Can you please post the error message?

---

### Post by bennoculus on 2011-01-04
> **jonesyp said:**
> Are you able to access the internet via Firefox?

Kind regards

Peter Jones
[www.simplysowseeds.co.uk](www.simplysowseeds.co.uk)

Yes I am. I posted from my Ubuntu machine.

I will post the error message in just a few minutes. I'll just take a screenshot and provide a Photobucket link.

Thanks for the replies!

---

### Post by bennoculus on 2011-01-04
Here's the error message inside of Ubuntu.

[IMG]http://i134.photobucket.com/albums/q84/bennypost/Screenshot.jpg[/IMG]

And a direct link incase [IMG] doesn't work
([http://i134.photobucket.com/albums/q84/bennypost/Screenshot.jpg](http://i134.photobucket.com/albums/q84/bennypost/Screenshot.jpg))

Edit: Also, I've visited GetDeb.com and downloaded Vuze in .deb format and I try and install and the software manager opens and tries to install. I get the same error message picture above if I try this method.

And, I'm installing my updates now.

---

### Post by oldos2er on 2011-01-04
Maybe you could resize the window so the entire msg appears? Anyway, it looks like there's a problem with tzdata, so I'd try these commands one at a time: ```
sudo apt-get clean
sudo apt-get purge tzdata
sudo dpkg --configure -a
```

---

### Post by bennoculus on 2011-01-04
> **oldos2er said:**
> Maybe you could resize the window so the entire msg appears? Anyway, it looks like there's a problem with tzdata, so I'd try these commands one at a time: ```
sudo apt-get clean
sudo apt-get purge tzdata
sudo dpkg --configure -a
```

I'm going to try these terminal lines now. Thank you

And, unfortunately, I could not resize that window. Otherwise I would have.

I also: Powered off my modem and routers for a few minutes to let them reset and then rebooted the computer. I'm about to try and see if I can download now from the Software Manager.

Is there a way to install a program (.deb file format) via the Terminal using code?

---

### Post by bennoculus on 2011-01-04
I tried all of the command lines listed above.

Then I tried reinstalling vuze and a few other programs and got the exact same error message.

Am I doomed out of Ubuntu?

How do I pull up the update manager? There's still files to be updated and maybe they could fix the issue?

Would I possibly need to wipe this partition and give a fresh install of Ubuntu? I really like the interface more than others I've tried it's just not going to be very useful without being able to install programs.

Any further suggestions would be great. Thanks!

---

### Post by ppv on 2011-01-04
When you say that you did not install all of the updates do you mean that you installed some of them completely and left out a few. Or the installation was stopped midway when it was going on.

---

### Post by bennoculus on 2011-01-04
> **ppv said:**
> When you say that you did not install all of the updates do you mean that you installed some of them completely and left out a few. Or the installation was stopped midway when it was going on.
The installation of Ubuntu went perfectly fine with no errors at all. I did not check the box to install updates automatically, due to the fact that I wasn't connected to the internet.

How do I get to the update manager (n00b here)? Will this help my case at all?

---

### Post by Rex Bouwense on 2011-01-04
I'm not using Maverick but in Lucid the update manager is under System->Administration->Update Manager.  You can also access from the terminal:
sudo apt-get update
sudo apt-get upgrade

---

### Post by bennoculus on 2011-01-04
Even when I try and update Ubuntu it gets to the end where it's trying to install the tzdata and it fails as well.

Should I try another install or just forget Ubuntu all together? I'd really like to use Ubuntu because I really like it, other than I can't install anything onto it.

---

### Post by plucky on 2011-01-04
> **bennoculus said:**
> Even when I try and update Ubuntu it gets to the end where it's trying to install the tzdata and it fails as well.

Should I try another install or just forget Ubuntu all together? I'd really like to use Ubuntu because I really like it, other than I can't install anything onto it.

Try from a terminal ```
sudo apt-get install -f
``` and post the complete resulting output to the forum.
You can put them between [noparse]```

```[/noparse] blocks if it is extensive.Or select the text and hit the # button at the top of the page will do the same job.

Good luck

---

### Post by bennoculus on 2011-01-04
> **plucky said:**
> Try from a terminal ```
sudo apt-get install -f
``` and post the complete resulting output to the forum.
You can put them between [noparse]```

```[/noparse] blocks if it is extensive.Or select the text and hit the # button at the top of the page will do the same job.

Good luck

I actually did some hardcore searching on the net and found this code not five minutes ago and used it. Worked like a charm. Took me about an hour of searching the web, however.

I got programs installing with no problem!

Thanks for the help!

---

### Post by cgroza on 2011-01-04
> **bennoculus said:**
> 
Is there a way to install a program (.deb file format) via the Terminal using code?

You can do it with dpkg -i or gdebi. In 10.10 the Uubntu Software Centre can do it too.

---

### Post by lolpenguin on 2011-11-14
Since you are new, install software from the Ubuntu Software Center (software-center), and refrain from using sudo unless you uctually understand what you are doing.

And next time post a new thread instead of adding on to the current one if you require help that is not covered in THIS thread. (Moderator may be required to rephrase the last paragraph)

---

