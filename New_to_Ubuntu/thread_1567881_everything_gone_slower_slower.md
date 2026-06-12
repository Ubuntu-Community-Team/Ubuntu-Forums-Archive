---
title: "everything gone slower slower"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by asal.mostafa on 2010-09-04
i don't know what happend?
but after installing ubuntu for a month 
everything comes slower 
every ten mints every thing stops for a mint
then comes back to normal status
 if there is a system restore  like windows?
just tell me what is the way to do this

---

### Post by asal.mostafa on 2010-09-04
plz help .. they didn't answer me in [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326")
i don't know what happend?
but after installing ubuntu for a month 
everything comes slower 
every ten mints every thing stops for a mint
then comes back to normal status
 if there is a system restore  like windows?
just tell me what is the way to do this

---

### Post by Naiki Muliaina on 2010-09-04
Patience lad you only asked an hour ago...

In your original post in Absolute Begginers post up as much information as you can. Such as your hardware etc. If theres something you have installed or changed before it got slow.

---

### Post by cariboo on 2010-09-04
Keep in mind that we are all volunteers her, and it may take the person that can answer your question some time to see it.

That being said, with out more information, it is pretty hard to answer your question. You should at least provide what version of Ubuntu you are using, your hardware specs, what the problem is eg:

[list]
[*] high cpu usage
[*] high swap usage
[/list]

What have you done yourself to try and troubleshoot the problem.

---

### Post by roy913 on 2010-09-04
please specify your hardware specs, the program that you are using like firefox, thunderbird etc, and your ubuntu distro like 8.04 or 9.10 etc.

my ubuntu works fine at work for more than a year time even with a celeron 2.x and 768Mb of ram and i installed a big bunch of programs on it and use them very frequently.

system restore in windows is irksome. 

as your last resort, in ubuntu or like many linux system, users personal files are normally stored in a different partition apart from the system files. so if the problem that you have is annoying enough, you can just reinstall your ubuntu.

---

### Post by Jazzy_Jeff on 2010-09-04
If your system is freezing up every ten minutes or so, something is using the resources. I would recommend opening up a terminal and type top. Keep an eye on it and when it freezes you should see what process is at the top of the list causing the problems. Let us know if this works.

---

### Post by asal.mostafa on 2010-09-04
> **Naiki Muliaina said:**
> Patience lad you only asked an hour ago...

In your original post in Absolute Begginers post up as much information as you can. Such as your hardware etc. If theres something you have installed or changed before it got slow.
i didn't install any thing new 
my pc is quitly good performance

---

### Post by asal.mostafa on 2010-09-04
> **cariboo907 said:**
> Keep in mind that we are all volunteers her, and it may take the person that can answer your question some time to see it.

That being said, with out more information, it is pretty hard to answer your question. You should at least provide what version of Ubuntu you are using, your hardware specs, what the problem is eg:

[LIST]
[*] high cpu usage
[*] high swap usage
[/LIST]

What have you done yourself to try and troubleshoot the problem.
thanx for answering me 
i'm using ubuntu 10.4
no there is no high cpu or swap usage and also there's no new packages installed
i wanna just something like (system restore) in windows is it ??

my pc specs 
mb asus 945 gla 
ram 512 ddr2
cpu 3.06 celeron

---

### Post by Dustin2128 on 2010-09-04
> **asal.mostafa said:**
> 
my pc is quitly good performance

hm, we need details though. E.g. how much RAM do you have? Have you done a memory test? How old is your hard drive? What type of CPU do you have? I'm thinking there's a terminal command you can run that will give us the required information... lspci?

---

### Post by Elfy on 2010-09-04
The place to be adding the information is in your thread in the support forum not here.

---

### Post by asal.mostafa on 2010-09-04
> **Jazzy_Jeff said:**
> If your system is freezing up every ten minutes or so, something is using the resources. I would recommend opening up a terminal and type top. Keep an eye on it and when it freezes you should see what process is at the top of the list causing the problems. Let us know if this works.
ya that's what i have done almost when browsing firefox
 but cpu performance  doesn't change so high ....still quite down  
and swap area is about 2 giga i don't think it may be high swap usage

---

### Post by asal.mostafa on 2010-09-04
> **Dustin2128 said:**
> hm, we need details though. E.g. how much RAM do you have? Have you done a memory test? How old is your hard drive? What type of CPU do you have? I'm thinking there's a terminal command you can run that will give us the required information... lspci?

my pc specs 
mb asus 945 gla 
ram 512 ddr2
cpu 3.06 celeron

---

### Post by asal.mostafa on 2010-09-04
> **roy913 said:**
> 

as your last resort, in ubuntu or like many linux system, users personal files are normally stored in a different partition apart from the system files. so if the problem that you have is annoying enough, you can just reinstall your ubuntu.
ya but i didn't partition my disk 
it would erase everything
i installed it on the disk at all 
so what?????

---

### Post by Elfy on 2010-09-04
Ok - thread closed.

You have a duplicate thread in a support forum - go there please.

[http://ubuntuforums.org/showthread.php?t=1567881](http://ubuntuforums.org/showthread.php?t=1567881)

---

### Post by David Andersson on 2010-09-04
> **asal.mostafa said:**
> 
every ten mints every thing stops for a mint
then comes back to normal status


What CPU, and how much RAM?

A few ideas:

When firefox has a lot of tabs opened with a lot of active content, the system can occasionally freeze, but only for about a second on a modern computer.

Another reason for long freezes can be a faulty hard disk. In ubuntu there is a tool under System > Administration to check the health of the hard drives.

---

### Post by Brunellus on 2010-09-04
threads merged and moved to appropriate support forum.  

These forums are where users support each other;  they are NOT paid support.  Be prepared to be a bit patient.  

For more immediate (that is, while you're sitting at the keyboard) help, try the main support IRC channel, #ubuntu on irc.freenode.net

---

### Post by Glenn nl on 2010-09-04
Try removing kernels (easiest with Ubuntu Tweak installed) or cleaning the system (Also easies with Ubuntu tweak)

For downloading ubuntu tweak, typ in the terminal (or copy and paste):

```
sudo add-apt-repository ppa:tualatrix/ppa
```

when that is finished, type or copy paste this:

```
sudo apt-get update && sudo apt-get install ubuntu-tweak
```

--------

If you are not so keen on using ppa´s type this in the terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

     updates your repo´s and installs new updates

```
sudo apt-get autoremove
```

     removes removable packages

```
sudo apt-get clean
```

     cleans up the cache the system left behind

-----------

Also try using lighter programs like Exaile instead of Rhythmbox, Shotwell instead of f-spot, leafpad instead of gedit, etc etc.

Personally I think your prob is swap.

Open the terminal and type:

```
gksudo gedit /etc/sysctl.conf
```

add at the end of the file:

```
#
# Reduce swap
vm.swappiness=10
```

It should look pretty much the same as this:

[IMG]http://easy-upload.nl/f/IjZzzlMi[/IMG]

Last:

Add the cpu-freq applet to your gnome panel and make sure it is set to ondemand.

---

### Post by utnubuuser on 2010-09-04
There are also log files you can peruse to get an idea about what might be causing the problem.
System>>Administration>>Log File Viewer

They're kinda difficult to decipher at first, but if your machine is bogging down for a minute at a time, note the time in the clock when it happens, (you might want to add seconds to your clock display, 'cause lots happens in a few seconds on a computer), then check the corresponding time-slots in the log files.  
You could also go to System>>Administration>>Synaptic Package Manager and use the filters to check for broken packages.
There are also Startup Services - you might have something running in the background that's causing resource usage.
I've read that Anakondi causes problems at times, but the specifics are beyond me.

Also, I've had similar problems and they either fixed themselves during an upgrade, or I ended up re-installing.
It's fairly easy to add a seperate /home partition, (to make upgrading/reinstalling easier), even though you installed without it.
Here is a link to a forum How-To on adding a separate partition "after-the-fact"> [http://ubuntuforums.org/showthread.php?t=1457542]("http://ubuntuforums.org/showthread.php?t=1457542")

---

