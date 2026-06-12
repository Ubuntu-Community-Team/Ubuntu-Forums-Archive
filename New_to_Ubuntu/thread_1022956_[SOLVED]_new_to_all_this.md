---
title: "[SOLVED] new to all this"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by dirtyharry on 2008-12-27
i have just recently changed os to ubuntu from windows xp.i was fed up with lining bill gates pocket.as i am new to ubuntu can anyone give me some advice about whether or not i need to install a firewall and an anti virus program.if so can you recommend which ones.also any websites where you can play good online games.any other good advice about do's and dont's would be greatly appreciated.i am still getting used to ubuntu but i am very happy i have made the switch.also i would like to transfer music to my mobile phone.it is a nokia 6300.any info would be greatly received and any websites which would help me would be great too!

---

### Post by gettinoriginal on 2008-12-27
Welcome to Ubuntu :popcorn:  The below sites are a great help when just starting off.  This site also has a search option for finding if a problem has been addressed before (use advanced search and tag "titles only).  

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[http://gnome-look.org/](http://gnome-look.org/)
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

Have fun, and good luck :P

---

### Post by jamesrfla on 2008-12-27
Inside Ubuntu kernel is a firewall so you don't need to worry about a fire wall. For anti-virus just keep Ubuntu updated and you should be fine. Nexuiz is a cool game. To get it do ```
sudo apt-get install nexuiz
``` into the terminal. Applications>Terminal. Enjoy Ubuntu!! :)

---

### Post by OldTimeTech on 2008-12-27
Welcome....remember this is not windows and you must remind yourself of this at all times...anti-virus is not a necessary here and neither is a firewall since it is pre-built into the kernel, but also programs don't load the same way and zip files are tar.gz files...so as a newbie to Ubuntu, learn all you can, don't be afraid of the terminal it is your friend, even if you only copy and paste into it...But best of all Ubuntu is FUN!!!  So enjoy!!!

---

### Post by HotShotDJ on 2008-12-27
> **dirtyharry said:**
> i have just recently changed os to ubuntu from windows xp.i was fed up with lining bill gates pocket.as i am new to ubuntu can anyone give me some advice about whether or not i need to install a firewall and an anti virus program.if so can you recommend which ones.also any websites where you can play good online games.any other good advice about do's and dont's would be greatly appreciated.i am still getting used to ubuntu but i am very happy i have made the switch.also i would like to transfer music to my mobile phone.it is a nokia 6300.any info would be greatly received and any websites which would help me would be great too!
**_Anivirus_**: Not needed.  Some people like to use their own system resources to help protect irresponsible Windows users.  I am not one of those people.

**_Firewall_**: Again, this is probably not necessary unless you are running services that are open to the internet.  If you are NOT behind a hardware firewall (such as most modern routers) it probably isn't a bad idea to configure the firewall that come with all Linux systems called IPTables.  To do that, you'll want to install a GUI front-end .  Using System --> Administration --> Synaptic Package Manager, install one of the several firewall front-ends -- firestarter, guarddog, shorewall, etc.  They all do basically the same thing -- help end users configure IPTables.

**_Nokia 6300_**: I have a Nokia 6085 and am able to push files to my phone (such as music files and contacts) via bluetooth.  If I had a USB cable for the phone, I'm sure that would work as well.  Just plug your phone in and see what happens.  You might have to futz with it a bit to get it to work.

**_Dos and Don'ts_**:If you remember nothing else, remember this -- Linux is NOT Windows... read the following web site: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)  -- commit it to memory.  Recite 10 times per day just before going to sleep: "Linux is NOT Windows!"  :)
But perhaps even more importantly -- HAVE FUN!

---

### Post by 2hot6ft2 on 2008-12-27
Welcome. Ubuntu comes with clamav anti virus already installed and firestarter firewall you just have to activate it System>Administration>Firestarter it's a simple setup. If you want a gui for the clamav go to a terminal Applications>Accessories>Terminal and put this in.
```
sudo apt-get install clamtk
```
Then it will be in Applications>System Tools>Virus Scanner

You will get false positives if you scan the system so it's best to only scan your home folder since that's where most everything goes it contains wine and the desktop too.

Applications are installed thru the terminal
Applications>Accessories>Terminal
Add/Remove
Applications>Add/Remove
and synaptic Package manager
System>Administration>Synaptic Package Manager

More helpful things to bookmark for future reference.

Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linux.org/apps/](http://www.linux.org/apps/)
[http://www.gimpshop.com/](http://www.gimpshop.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)

Everyone asks coming from windows
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

Customizing and apps
[http://ubuntuforums.org/showthread.php?t=856190](http://ubuntuforums.org/showthread.php?t=856190)
[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

Learning Linux
[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)
[http://ubuntuforums.org/showthread.php?t=655207](http://ubuntuforums.org/showthread.php?t=655207)

Troubleshooting, multimedia and misc help
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
[http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html](http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html)

---

### Post by metalf8801 on 2008-12-27
there are very few virus that can infect a computer running Ubuntu but anti-virus software can be helpful if you are sending files to windows computers so that you don't send an infected file 

the easiest anti virus program to get is Clamav because you can get it using add/remove and its open source 

you can also get for free 
Avast [http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

AVG [http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

there are some others that I can't find right now I know Kaspersky makes an anti virus program but its not free in anyway 



I just use the fire wall that is on my router but that's just me 


I don't play games on my computer much so I can't really help you with that but just look at the games you can get from add/remove 
there a lot of sites with information on games heres one of them 
[http://www.playubuntu.com/](http://www.playubuntu.com/)

A lot of people use Wine to play windows games but Wine does have limitations

---

### Post by ugm6hr on 2008-12-27
> **HotShotDJ said:**
> **_Nokia 6300_**: I have a Nokia 6085 and am able to push files to my phone (such as music files and contacts) via bluetooth.  If I had a USB cable for the phone, I'm sure that would work as well.  Just plug your phone in and see what happens.  You might have to futz with it a bit to get it to work.

USB cable will do this very easily.

Just plug it in.

---

### Post by hyper_ch on 2008-12-27
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Michael.Godawski on 2008-12-27
Welcome dirtyharry :P
good choice.

Here are some pages which might be helpful if you are crying for first aid help.

[LIST]
[*][https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[*][http://godawski.oxyhost.com/](http://godawski.oxyhost.com/)
[*][http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[/LIST]

---

