---
title: "DansGuardian trouble in Gutsy"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by arfink on 2007-11-02
Hello, I have been using Ubuntu for about a year now, and I recently upgraded to Gutsy. Back when I used Windoze I liked a program called Naomi, which filtered content by keywords and phrases and not by blacklists. It was also very unobtrusive and fast. I am looking at DansGuadian and I can see that it is the closest thing to Naomi I'm going to find for Linux. I know about the Ubuntu CE script to make it run in Feisty, but I tried to force the script to run in Gutsy and it won't work. 

Here is what I did: I modified the script so that it wouldn't check what distribution I was running, and then let it run free after that. It installed all the files I needed from the old Ubuntu Feisty repositories and it also successfully installed the GUI configuration program. I rebooted like the instructions said to do, and then I ran an update to make sure that all the packages I just installed from the Fiesty database got updated to the new Gutsy versions. After I did all this, I messed with the configuration files through the Ubuntu CE "parental controls" GUI and made sure everything was good. 

Then I tried to start it, and that is where thing stopped working. My browser would not function (Firefox) even though I thought the install script had updated the proxy info in Firefox to make it work. So, I opened up my Network Tools and looked at my computer to see what ports were open. I found port 8080 open on IP address 0.0.0.0, and I assumed that was the Tinyproxy that was connected to DansGuardian and so I redirected my Firefox to connect to it, and it seemed to work. Bad sites got blocked just fine, and I was browsing like I wanted to. So, I turned my computer off, happy it had worked. I came back the next day, only to find that nothing worked again. I checked my Network Tools, and that 8080 port I had used the day before was no longer open. I tried just about everything from the Parental Controls GUI, and it's not working. Anybody have any ideas?

EDIT: I am not using Ubuntu CE- I am running a stock Gutsy 7.10 install. The script I used was offered on the Ubuntu CE website as a separate package for people who want filtering but don't want all the extra Christian Edition stuff.

---

### Post by timcredible on 2007-11-02
dansguardian is available via synaptic.  i would suggest re-install gutsy and then installing dansguarding via synaptic - it'll install all the dependencies you need.  always try to install packages with synaptic first. 

btw, i've added several repos since i installed gutsy, so if you don't find dansguardian when you do a search in synaptic, do a search here and find out what repos you need to add.

lastly, i used dansguardian about 2 years ago, and it used squid for it's proxy, not tinyproxy, not sure if there's really any difference between the 2 proxy programs or not.

---

### Post by arfink on 2007-11-02
Yes, the script I have installs from the repositories via APT. My dependencies are all satisfied. The reason I have the script is because you need to have a local proxy running in order to use DansGuardian on a local machine. I am not trying to filter a whole network, just my own machine. The script I have from Ubuntu CE is supposed to set up the proxy for me (tinyproxy) as well as a mini-firewall (fireHol) and as I said, it all worked in Feisty. So, in other words, just installing from Synaptic won't cut if for me. I need to have a GUI control, because the end user I'm working this for won't be experienced enough  to work with the config files, but still needs to have access to the settings. That is why I have to use the script.

---

### Post by ajmoncrief on 2007-11-11
I could use this as well....I've got ubuntu on a family members pc and made the mistake of putting gutsy on it without checking for an update.  I'm not the very best at network stuff, so a script would be VERY ideal for me.

---

### Post by Yagad on 2007-11-13
I'm also using Gutsy now for 4 months and was looking for a web filtering software. I did install dansguardiian from the repos and followed the how tos that I found on the forums.
All went wel as soon as I tried to use it.

At first it doesnt want to let me brows get e-mail or skype. and then after just looking at the various config files of firehol, tinyproxy and dansgaurdian to make somthing of it, it starts to work after a few restarts of the three services.

After t restart it is back to the beginning, I'm still new to Linux but I'm a fast learner. I must say a script with a GUI at the end that is working will be nice.

What I did find when it was working is that my internet was allot slower than without, with it I have to count to twenty and without to 5. I know that it must go through the whole process of checking.

---

### Post by pete.dawgg on 2007-11-14
i suggest you use junkbuster or privoxy or sth like that. the squid/dansguardian-combo is intended for a very different scenario, i think.

---

### Post by coffen on 2007-12-25
You might wanna take a look at this --> [http://ubuntuforums.org/showthread.php?t=619146&highlight=dansguardian+gui+gutsy](http://ubuntuforums.org/showthread.php?t=619146&highlight=dansguardian+gui+gutsy)

There is a new dansguardian install script for gutsy.

---

