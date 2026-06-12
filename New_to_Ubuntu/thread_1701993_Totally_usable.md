---
title: "Totally usable?"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by Polaf on 2011-03-07
So I just recently started using ubuntu for is education benefits and I was wondering if it was possible to get literally any program running on it. I ask this because im not totally sure whether or not I want to do a full install if theres some programs that I cant get to function.

---

### Post by Polaf on 2011-03-07
The length and complicated-ness of the process to get a difficult program running does not matter either. As long as I can eventually get it up and running no matter what.

---

### Post by TeoBigusGeekus on 2011-03-07
What program did you have in mind?

---

### Post by nothingspecial on 2011-03-07
You will only be able to get some windows programs to run in wine. Usually with only part functionality.

There are plenty of linux alternatives to most things but not all.

I suggest a dual boot

---

### Post by mick_86 on 2011-03-07
> **Polaf said:**
> So I just recently started using ubuntu for is education benefits and I was wondering if it was possible to get literally any program running on it. I ask this because im not totally sure whether or not I want to do a full install if theres some programs that I cant get to function.

i know that a lot of windows programs can be run through wine, but not all of them.

i'm new to ubuntu aswell so thats the best i can offer.

---

### Post by cchhrriiss121212 on 2011-03-07
> I was wondering if it was possible to get literally any program running on it
Ubuntu is a Linux OS, so it will run any program designed for Linux, I get the feeling you are wanting to run Windows programs. Is that right?

It would help if you mention what specific programs you want to run, and what problems you have had with them.

---

### Post by Frogs Hair on 2011-03-07
What kind of programs ? If you are thinking of Windows programs some work with the  wine  program and others do not . Perhaps a list of programs may help.

---

### Post by Anuovis on 2011-03-07
This depends only and only on your computing needs. No system can run every program, nor would you want to.

Ubuntu has a good selection of great software for basic and popular tasks, like office apps, web browsing, email, multimedia and such. 

If you need to run Windows apps, there is this program called Wine that helps with more widespread software but can be a bit tricky. Other than that, you can either run a virtual Windows OS inside of Ubuntu or dual-boot. Each way has pros and cons.

Unless you have something very specific in mind (one Windows application that you need to matter what for work, high-end professional software etc.) or play a lot of games, you shouldn't be too concerned about the software selection.

---

### Post by Polaf on 2011-03-07
I dont have any specifics as of now but im talking about im willing to get these programs up and running no matter the cost of time or space... just as long as I can get them running either way

---

### Post by IWantFroyo on 2011-03-07
Go to software center and get VirtualBox OSE. Install Windows and OS X, or whatever operating systems the programs were made for. Then you can run them :D

---

### Post by JBAlaska on 2011-03-07
If your going to use Virtualbox and you want USB 2.0 access, try the non-free version of Vbox 4.0 (Hint: you don't have to pay for it)
```
sudo -v
echo "deb http://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib" | sudo tee -a /etc/apt/sources.list
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-4.0
```

And the Extension pack [Here](http://download.virtualbox.org/virtualbox/4.0.0/Oracle_VM_VirtualBox_Extension_Pack-4.0.0-69151.vbox-extpack)

---

### Post by Anuovis on 2011-03-08
> **Polaf said:**
> I dont have any specifics as of now but im talking about im willing to get these programs up and running no matter the cost of time or space... just as long as I can get them running either way

Yes, you can get any software to run on Ubuntu because it is open source and you can modify or write new apps as you wish.

So, learn a couple of programming languages and start reverse-engineering whatever you want to run here, or maybe join the Wine dev team, or maybe create your own virtualization software, options are limitless :)

Seriously though, it does come down to your particular needs. So unless you have a list, nobody can help you. The general answer is - if it is used somewhat widely, you can run it with a bit of effort.

---

### Post by slooksterpsv on 2011-03-08
If I'm looking for a program that's like <XYZ> in Windows, I will look on:
[http://www.osalt.com/](http://www.osalt.com/)

Or just Google it.

Example:

Photoshop -> GIMP
Excel -> OpenOffice.org/LibreOffice Base
Outlook -> Evolution or Zimbra
Adobe Premier -> Kdenlive or Cinelarra
etc. -> etc.

---

### Post by theDaveTheRave on 2011-03-08
There are always work around to getting programs that are designed for windows (eg office, various adobe stuff, games... etc) to run within a linux system.

The best options are....

Wine - to enable you to run the system locally, proviso is you may find that the functionality isn't what you'd expect!

Virtualisation - if you have a windows install disk, a powerfull enough computer, you can install a virtual machine within your actual machine. This is normally very effective, and will give you access to all those nice 'windows' programs with full their functionality.  You could of course do the opposite too, run your prefered linux system as a VM on your windows pc

Remote desktop - Yes if you have a spare pc with all those nice windows programs running on it, why not just remote desktop / VNC into it whenever you need to use them. Downside is that you need to have it turned on, but then with a dual boot you need to reboot to get into it also!

personaly, I don't use anything windows anymore. There are some nice things that I would like to have access to (such as a better video editing system - but then I'm not into video, I prefer still photography).
[INDENT][INDENT]
On a side note, I observe that a lot of the film / animation studios use editing systems on a 'unix type' system (most often sun, or HPos). So these things are available, just not for the public ~ ie must be very expensive :P


Truth is that most software will now run on both windows and MAC so technically as MAC are based on the unix kernel (well BSD-Darwin to be more precise) they should work on a linux system - but for some strange reason they don't![/INDENT][/INDENT]

well that is my pennies worth.

David.

ps. please feel free to correct me if I'm wrong on the Mac OSX - BSD thing.

---

