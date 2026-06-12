---
title: "New User Wireless Problem"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by frigate13 on 2009-11-27
Hello.

I know there is a thread with a similar name already, but it doesn't sound exactly like my problem.

I had a laptop that some kind of bug got in, and because I had lost my software, I couldn't wipe it and reload with the Windows XP operating system.

As a last shot before pitching the laptop and buying another, I took the advice of a tech guy at work and loaded Ubuntu on the machine.  The only way it would load properly was to wipe out the Windows system at the same time.

It loaded fine, and everything works but the internet connection.  I have wireless, and it would not connect automatically (as it had with Windows XP).

So I went to "Editing Wireless Connection" and got all of the information that the tabs requested (with the help of my wireless provider) but when I finished putting in all the information it would no let my hit the "Apply" button.

I am thisclose to just tossing the laptop and starting over.  It seems like this forum may be the best place to find help, since I have not been able to find a telephone tech support number.

Any ideas?

---

### Post by Bigadada_saba on 2009-11-27
first of all  we need to know if you what type of wireless card your using and if the drivers are installed
 and also what versions of ubuntu are you using

---

### Post by Bigadada_saba on 2009-11-27
click on the wireless icon and see if there are avaleble networks

---

### Post by frigate13 on 2009-11-27
> **Bigadada_saba said:**
> first of all  we need to know if you what type of wireless card your using and if the drivers are installed
 and also what versions of ubuntu are you using

Oh.  I forgot to add to my original post that I am in no way computer savvy.  The only thing I know is that my laptop connected to my wireless when I bought it.  How do I check for what kind of card it is using?

Oh yeah.  I loaded Ubuntu on two days ago, so I am assuming it is the most recent version.

---

### Post by frigate13 on 2009-11-27
> **Bigadada_saba said:**
> click on the wireless icon and see if there are avaleble networks

It says the wireless networks are disconnected.

---

### Post by Bigadada_saba on 2009-11-27
> **frigate13 said:**
> Oh.  I forgot to add to my original post that I am in no way computer savvy.  The only thing I know is that my laptop connected to my wireless when I bought it.  How do I check for what kind of card it is using?

Oh yeah.  I loaded Ubuntu on two days ago, so I am assuming it is the most recent version.

beside your speaker icon in the top right-hand corner is an icon for wireless simmilar to what you see on a cellphone click on that with you mouse and see if you get networks

---

### Post by crazy dave on 2009-11-27
Hey, 

Doesn't sound serious, I had a similar issue.  If you can connect to your router with a LAN cable and then choose from the drop down menu System>Administration>Hardware Drivers........then it will search for the driver for your WiFi card and you should activate it and reboot, then you should find your home network automatically, click on it then enter your passcode.

Hope this helps,

Regards

---

### Post by frigate13 on 2009-11-27
> **crazy dave said:**
> Hey, 

Doesn't sound serious, I had a similar issue.  If you can connect to your router with a LAN cable and then choose from the drop down menu System>Administration>Hardware Drivers........then it will search for the driver for your WiFi card and you should activate it and reboot, then you should find your home network automatically, click on it then enter your passcode.

Hope this helps,

Regards

OK.  This is going to sound completely computer impaired, but I'm used to it by now.  Is the LAN cable the one that goes from the router to my PC to give it wired DSL?  Once I have connected it by wire and activated the WiFi card, I will be able to go wireless, instead of staying attached by a LAN?

---

### Post by Bigadada_saba on 2009-11-27
yes once the drivers are installed and u reboot the laptop

---

### Post by crazy dave on 2009-11-27
yeah thats it, you just need to connect it and try what I've suggested, it should find the piece of software required to run your WiFI card.  Choose the one with Recommended in brackets beside it, press activate and reboot.

don't worry the jargon gets to me too sometimes.

---

### Post by Bigadada_saba on 2009-11-27
did you get it working???

dont get frustrated we were all newbees at one point in time.
the good thing is that in this forum you'll get help for practicaly any problemthat you have. but beleave me when i say you wont regret switching to ubuntu

---

### Post by frigate13 on 2009-11-27
> **Bigadada_saba said:**
> did you get it working???

dont get frustrated we were all newbees at one point in time.
the good thing is that in this forum you'll get help for practicaly any problemthat you have. but beleave me when i say you wont regret switching to ubuntu

I'm looking for an extra LAN wire.  I'll report back when I have met with success. [Optimism]

---

### Post by frigate13 on 2009-11-27
> **crazy dave said:**
> Hey, 

Doesn't sound serious, I had a similar issue.  If you can connect to your router with a LAN cable and then choose from the drop down menu System>Administration>Hardware Drivers........then it will search for the driver for your WiFi card and you should activate it and reboot, then you should find your home network automatically, click on it then enter your passcode.

Hope this helps,

Regards

OK.  Found a LAN wire and connected it to the router and the laptop.  I then did the Hardware Driver thing, and it came back with "No proprietary drivers are in use on this system."  However, I was able to connect to the internet with the wire in.

So I restarted, and ran the Hardware Driver again, and got the same message.  

Any ideas?

---

### Post by frigate13 on 2009-11-27
Bump.

---

### Post by bkratz on 2009-11-27
Go to applications--accessories--terminal at the top of the screen on the left.  It should bring up a small window that says your computer name and a~$ then a flashing cursor.     Type in     lspci
(That is lowercase LSPCI)

Look for the wireless card.  If you don't understand what you see-- copy and paste it here so someone can decode it for you.

Close the window when done!

---

### Post by frigate13 on 2009-11-27
> **bkratz said:**
> Go to applications--accessories--terminal at the top of the screen on the left.  It should bring up a small window that says your computer name and a~$ then a flashing cursor.     Type in     lspci
(That is lowercase LSPCI)

Look for the wireless card.  If you don't understand what you see-- copy and paste it here so someone can decode it for you.

Close the window when done!

It's all Greek to me:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


 By the way, the laptop is an "e-machine" if that helps.  I think it a plain label Gateway.

---

### Post by bkratz on 2009-11-27
You have the infamous 

00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Note REV 3 (there are a lot of different chipsets internally)

There are a lot of threads about each version in the Networking and Wireless Forum, I am searching for the best answer to help, but here is the search page for you to look also (two eyes are better...)

[http://ubuntuforums.org/search.php?searchid=67495712](http://ubuntuforums.org/search.php?searchid=67495712)

---

### Post by bkratz on 2009-11-27
See post #6, at least we know the driver now. Still looking

[http://ubuntuforums.org/showthread.php?t=1298779&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1298779&highlight=BCM4306)

---

### Post by frigate13 on 2009-11-27
> **bkratz said:**
> You have the infamous 

00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Note REV 3 (there are a lot of different chipsets internally)

There are a lot of threads about each version in the Networking and Wireless Forum, I am searching for the best answer to help, but here is the search page for you to look also (two eyes are better...)

[http://ubuntuforums.org/search.php?searchid=67495712](http://ubuntuforums.org/search.php?searchid=67495712)

I'll look.  I don't know if I'm sure what I'm looking for.  Thanks for the help so far.

---

### Post by bkratz on 2009-11-27
> **frigate13 said:**
> I'll look.  I don't know if I'm sure what I'm looking for.  Thanks for the help so far.

Check out posts 5 and 6 (esp 6) of

[http://ubuntuforums.org/showthread.php?t=1298779&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1298779&highlight=BCM4306)

no wonder it sounded familiar!  (I just noticed same 1)

---

### Post by bkratz on 2009-11-27
This is what I really wanted to send!

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by bkratz on 2009-11-27
Look at post #7, I think it has the information you need

[http://ubuntuforums.org/showthread.php?t=1251901&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1251901&highlight=BCM4306)

Good Luck

---

### Post by frigate13 on 2009-11-27
> **bkratz said:**
> This is what I really wanted to send!

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

OK.......[trying to hide ignorance]......so does this mean I have to download something?  Remember, I'm reeeeally computer ignorant.  I sort of need a step 1...step 2...step 3...kind of direction.  

I DO appreciate the help.

---

### Post by bkratz on 2009-11-27
> **frigate13 said:**
> OK.......[trying to hide ignorance]......so does this mean I have to download something?  Remember, I'm reeeeally computer ignorant.  I sort of need a step 1...step 2...step 3...kind of direction.  

I DO appreciate the help.



Ignore that one and look at the final one   start with step two  Download and install the latest updates...

---

### Post by frigate13 on 2009-11-27
> **bkratz said:**
> This is what I really wanted to send!

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)


Sorry to be anal-retentive, but I just want to make sure I am doing the right things.  I am going to the above link, and going to the part titled "Installing Drivers for the bcm43xx cards," or am I going to the last part titled "Alternative Solutions" and doing the ndiswrapper thing?

You sort of lost me there.

---

### Post by bkratz on 2009-11-27
> **frigate13 said:**
> Sorry to be anal-retentive, but I just want to make sure I am doing the right things.  I am going to the above link, and going to the part titled "Installing Drivers for the bcm43xx cards," or am I going to the last part titled "Alternative Solutions" and doing the ndiswrapper thing?

You sort of lost me there.




No, that whole thing is really complicated.  Try the solution mentioned in post #7 or this link,

[http://ubuntuforums.org/showthread.php?t=1251901&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1251901&highlight=BCM4306)

 but starting with the second step (not counting plugging in the wired connection) , but you will need to have a wired internet connection to do this.  Start at download and install updates...

Here is the link to the single post

[http://ubuntuforums.org/showpost.php?p=7926460&postcount=7](http://ubuntuforums.org/showpost.php?p=7926460&postcount=7)

---

### Post by lexfati on 2009-11-27
frigate13 - I know digging through the forum posts can be confusing when you're just starting.  Don't give up yet.  

This might be more simple than you think, though.  Links in the previous posts from bkratz pointed to [[COLOR="Blue"]b43[/COLOR]]("http://linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy").

Depending on your chip id, it might be as simple as installing b43-fwcutter.

First, open a terminal window (Applications > Accessories > Terminal) and check your chipset by typing:
```
lspci -vnn | grep 14e4
```

If it comes back mentioning 14e4:4320 you're in luck according to the b43 website.  Just install b43-fwcutter and reboot.

```
sudo apt-get install b43-fwcutter
```

If your chipset comes back with a different number, installing b43-fwcutter is still worth a shot.  This might be all you need to do to get your driver.

---

### Post by frigate13 on 2009-11-27
> **bkratz said:**
> No, that whole thing is really complicated.  Try the solution mentioned in post #7 or this link,

[http://ubuntuforums.org/showthread.php?t=1251901&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1251901&highlight=BCM4306)

 but starting with the second step (not counting plugging in the wired connection) , but you will need to have a wired internet connection to do this.  Start at download and install updates...

Here is the link to the single post

[http://ubuntuforums.org/showpost.php?p=7926460&postcount=7](http://ubuntuforums.org/showpost.php?p=7926460&postcount=7)

OK...already ran into a problem.  I went into Applications to go to Add/Remove, but there is no Add/Remove under Applications.  What now?  (I did look elsewhere under Applications, but didn't find anything.)

There is an "Ubuntu Software Center" where you can add new software, but I'm not sure what I'm supposed to be adding.  Everything?

---

### Post by lexfati on 2009-11-27
Under applications, look for a terminal (not Add/Remove), so that you can access the command line.  It should be under the Applications > Accessories menu.

When you have opened the terminal, you can check your chipset and install b43-fwcutter.

---

### Post by frigate13 on 2009-11-27
> **lexfati said:**
> Under applications, look for a terminal (not Add/Remove), so that you can access the command line.  It should be under the Applications > Accessories menu.

When you have opened the terminal, you can check your chipset and install b43-fwcutter.

Are you talking about the same thing as bkratz is?

Once I access the command line, what do I do?

Pretend like you're talking to your great-grandmother...

---

### Post by bkratz on 2009-11-27
> **lexfati said:**
> Under applications, look for a terminal (not Add/Remove), so that you can access the command line.  It should be under the Applications > Accessories menu.

When you have opened the terminal, you can check your chipset and install b43-fwcutter.



Easiest way to do would be to go to system---administration--synaptic package manager- press reload wait till it does it

do a quick search for b43

it should come back 


saying b43-fwcutter

put a check mark next to it to mark for installation and install

You may have to restart maybe not.

look under system---administration--hardware drivers and see it it offers you B43 if so, select it

---

### Post by lexfati on 2009-11-27
I apologize if I'm confusing you, I know this is new to you and I'm trying to be careful to.  This is actually the same process from the post bkratz referenced, I'm just trying to cut out some of the technical stuff.

Once you have the terminal open, type the commands I previously listed  in post #27.

The first line checks to see the ID of your wireless card.  After reading the thread bkratz sent you, I'm guessing your output from the command should have 14e4:4320 in it.  If it does, you're set.  If it doesn't, the next step is still worth a shot.

The second step,
```
sudo apt-get install b43-fwcutter
``` 

will install special software your wireless card needs to work.  Its called firmware, but what is important is that your driver can access it.  When you enter that command, as long as you're plugged into the Internet, it should do what it has to do.  Just reboot afterwards.

---

### Post by bkratz on 2009-11-27
Both of these will install b43-fwcutter---I was just trying to stay away from the terminal for you. Actually the terminal is easier to use, you should learn about it.  I will find a link that I have that will be helpful for terminal work.

---

### Post by bkratz on 2009-11-27
Here is the link I mentioned (not for now--save some for later)!

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by frigate13 on 2009-11-27
Gentlemen (or gentlewomen; don't want to make assumptions), thank you SO much for your help.  This post was made via wireless.

I appreciate all of your efforts this afternoon and this evening, and appreciate that you did not make fun of the computorially-challenged newbie.

Thank you again.

---

### Post by Fast Iron on 2009-11-27
Big thanks to the people that visit this site!  I just started using Ubuntu 9.10 two days ago.  I really like it, but my wireless conn wouldn't work.  But after reading some of the posts it helped me out greatly.  
Just an other user that is willing to put the screws to windows!!!

---

### Post by lexfati on 2009-11-28
Glad your up and running!! (and I apologize if I scared you with the command line earlier - thanks to bkratz for knowing with the GUI.

---

### Post by bkratz on 2009-11-28
> **frigate13 said:**
> Gentlemen (or gentlewomen; don't want to make assumptions), thank you SO much for your help.  This post was made via wireless.

I appreciate all of your efforts this afternoon and this evening, and appreciate that you did not make fun of the computorially-challenged newbie.

Thank you again.



There is one more thing to do,  please go to the thread tools at the top of the page and mark the thread [Solved}.  This will help others find help should they have the same problems.

---

### Post by frigate13 on 2009-11-28
> **bkratz said:**
> There is one more thing to do,  please go to the thread tools at the top of the page and mark the thread [Solved}.  This will help others find help should they have the same problems.

Done and done.  Also, I think I will start another thread with a new name regarding things newbies should do after they first install Ubuntu.

---

### Post by Hoonakwa on 2009-11-30
Guys and or Girls,
 Thanks so much for your willingness to help. This work for me also. You linux people are the greatest. MANY MANY MANY thanks for your help.:P

---

### Post by benjamonk on 2009-12-02
> **bkratz said:**
> Easiest way to do would be to go to system---administration--synaptic package manager- press reload wait till it does it

do a quick search for b43

it should come back 


saying b43-fwcutter

put a check mark next to it to mark for installation and install

You may have to restart maybe not.

look under system---administration--hardware drivers and see it it offers you B43 if so, select it

When I look under hardware drivers, the window is empty - 'No proprietary drivers on in use on this system.'

---

### Post by bkratz on 2009-12-02
> **benjamonk said:**
> When I look under hardware drivers, the window is empty - 'No proprietary drivers on in use on this system.'




Do you have the same card these other people had?  Go to Applications--Accessories--terminal     a small screen will pop up

type in lspci  (LSPCI) in lowercase and copy and paste the results here (then close the window) or look carefully and see if you can see the wireless card mentioned.

---

### Post by lexfati on 2009-12-02
The command bkratz gave you will list all of your installed hardware.  To find just your wireless card you can type:
```
lspci | grep Wireless
```(The capital "W" in Wireless is important)

However, if you are using a USB wireless adapter, you need must replace 'lspci' with lsusb:
```
lsusb | grep Wireless
```

---

