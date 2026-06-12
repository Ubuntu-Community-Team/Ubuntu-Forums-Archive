---
title: "WPA wireless took away my wireless adapter?"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by Mimsy on 2007-01-13
I think I broke my Ubuntu again... :oops: 

I followed the How-To on how to set up WPA wireless, since I want the laptop to be able to connect to my home network, and the thought of reconfiguring all the four other devices that connect to the network is not a pleasant one... I keep getting error messages, however, and worst of all, after following the guide in the sticky at the top of this forum, network-manager-gnome gives me the message "no network devices have been found" when I try to connect.

The laptop has issues going online, for obvious reasons, so I can't copy paste from it to the forum, but if you tell me what you want to know, I'll open the files and type all of it in manually. 

All help is greatly appreciated. :)

/Mimsy

---

### Post by Mimsy on 2007-01-13
After digging through laptop and router settings I've found some more information, that I thought I'd post here, in the hopes that it will help other forumites help me.

I am using the built-in W200 wlan of my compaqw notebook, with the orinoco_usb drivers found through the link in my signature below. I have a Motorola SURFboard SBG940 Wireless Cable Modem Gateway (according to the front page of the manual anyway), and my home network is on WPA with TKIP and dynamic addresses all around. 

I know I need to put all the relevant information into /etc/network/interfaces but I'm not sure which number, and what information is relevant and which is not. I'm hoping someone can help me out. :)

Thanks,
Mimsy

---

### Post by phossal on 2007-01-13
Mimsy, if your hardware is properly recognized, meaning it's using the correct drivers, you should be able to connect to a *protected* router in two commands. (This isn't *always* the case, but more often than not). I recommend avoiding the GUI tools and configuring */etc/net*/int** until your connection is up:


Where wlan0 is *your* wireless interface
```
sudo iwconfig wlan0 essid <essid> channel <channel> key <26-digit hex key>
sudo dhclient wlan0
```

That should get you connected. Then you can configure for persistence however you choose.
[SIZE="1"][COLOR="DimGray"]*No brackets when replacing <essid>, <channel> and <key> with *your* information. If you're using 40(64Bit) encryption, you have less than 26-digits. If you're using a password, the command is different.[/COLOR][/SIZE]

---

### Post by Mimsy on 2007-01-13
I'll try that next, thanks! :)

If I'm using a passphrase and not a hex key, how does that change the command?

/Mimsy

---

### Post by phossal on 2007-01-13
If you're using a passkey, iwconfig allows you to pass the parameter differently. See this html man page for [iwconfig]("http://www.linuxcommand.org/man_pages/iwconfig8.html").

The command would look more like this (note the preceding 's:' before the passkey):
```
sudo iwconfig wlan0 essid MYNET channel 7 key s:thisismykey
```

[edit] And, you're welcome! Anything for a self-declared *Geek's wet dream*.

---

### Post by Mimsy on 2007-01-13
> **phossal said:**
> [edit] And, you're welcome! Anything for a self-declared *Geek's wet dream*.

I have a diploma with that title, actually. Anniversary gift from The Fiance.

I'm very proud of it. :)

/Mimsy

---

### Post by phossal on 2007-01-13
> **Mimsy said:**
> I have a diploma with that title, actually. Anniversary gift from The Fiance.

I'm very proud of it. :)

/Mimsy

I'm not sure how I ended up in that thread, but it did make me laugh (and swear that I would never venture away from the java/wireless threads again).

Have you been able to connect yet? If so, what was the solution?

---

### Post by Mimsy on 2007-01-15
Error message:

> Error for wireless request "Set Frequency" (8B04) : 
     SET failed on device eth1 ; Device or resource busy

Device eth1 showed as diabled and inactive, and not configured, in the Networking GUI. I'm puzzled again...

/Mimsy

---

### Post by phossal on 2007-01-15
Are you using *sudo*?

```

bash 3.1:iwconfig wlan0 channel 3
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; *Operation not permitted.*
```

The error is different, but it should actually force through.

[edit] Per usual, it might be helpful to see the output of both ifconfig and iwconfig.

---

### Post by phossal on 2007-01-15
I realize you would like to end up with the laptop connected to the network using WPA. Is there anything preventing you from disabling WPA short term to confirm that you're able to connect without it?

I don't know the details about your hardware. I've read reports that WPA is essentially a non-option for certain people, but I'm skeptical based on the voodoo I found regarding my own hardware. It would help put boundaries on the problem if we could confirm you were able to connect *without WEP/WPA*. 

Plus, I strongly believe setting up a network initially is best  done from the command line. Configuring the files and using the GUI tools sometimes tricks you into thinking you're making changes immediately, when in fact they're really not being recognized by the system until after some delay (the longest being a full reboot).

---

### Post by Mimsy on 2007-01-16
I have always been able to connect just fine without WPA or WEP; and I still can, if I bother to take the laptop someplace else for a while. My problem right now is, as far as I am concerned, that everything else on the network uses WPA, including, of course, the wireless router that now won't let me connect without having WPA enabled.

As for GUI or command line setup, I don't particularly care which one I use. I prefer GUI, because it is easier for me to remember what I did in a graphical environment than with the command line, but I'll happily use whatever works.

I'll see if I can find one of the USB-drives scattered around the house, and move the outputs from iwconfig and ifconfig over to this computer so I can post them.

Thanks!

/Mimsy

---

### Post by phossal on 2007-01-16
> **Mimsy said:**
> I have always been able to connect just fine without WPA or WEP; and I still can, if I bother to take the laptop someplace else for a while...

Have you ever connected to the router in question? Ever? Without wep/wpa?

---

### Post by Mimsy on 2007-01-18
I have. It worked in Windows. ](*,) 

Nothing else did, do I took it off and put Ubuntu back on... I don't want XP back on my beautiful portable machine ever again... :( 

/Mimsy

---

### Post by phossal on 2007-01-18
lol Mimsy. Work with me here. Have you connected to the router in question, without WEP/WPA, using the laptop in question, *while it was running Ubuntu?*

---

### Post by Mimsy on 2007-01-18
Sorry. I'll try.  :mrgreen: 

I'm reluctant to makes changes in the router configurations since we have a large number of other devices connected to it, and my fiancee, who works from home, would be in a lot of trouble if I messed up our internet connection. And then I would be in a lot of trouble as well. however, since I have tried every single form of settings on the laptop there's a good possibility I'll try changing the router around next, probably around tomorrow night when I have more time.

The thought of having to reconfigure the other four devices, including the company laptop with its very paranoid security software, makes me cringe though. The router gets temperamental from time to time, and has difficulty remembering that settings have been saved. It would be bad if it got stuck on the wrong ones.  ](*,) 

I'm almost positive that Ubuntu will let me connect to the router, but I'll try it without the WPA, and see what happens. tomorrow night, or this weekend, when I have two full days to work on whatever can go wrong :)

/Mimsy

---

### Post by Win2Mac2Linux on 2007-01-18
If it's okay I'd like to crash this thread.  In short I am a 3 day old linux/Ubuntu noob so...
I've been a Windows end user for many years, tried OSX for a year (VERY disappointed, believe it or not) and now trying to make the leap to linux.  My problem is this.  I used the sticky "how to" for my wireless card (BCM 4318).  After following the steps, the wireless option in my network settings (System>Admin>Networking) is no longer there.  Only the wired and modem connections are present.  People have been very helpful up to this point, but since the wireless connection disappeared from that spot, I haven't gotten much since.  ](*,)             I know it's there because it shows up in the device manager and when i ran a command  in terminal yesterday (I forget exactly what it was) it showed the card present.  Any help you can provide would be greatly appreciated.  I'm not the most technical oriented computer person (I'm in healthcare), but I've been VERY slowly making my way around this new OS, occaisonally knocking things over, but not breaking anything.  
;) 

If you can point me in the right direction great.  Of course, if you just want to show me the door, that's okay too.  I don't think I've been coming up with so many questions in such a short time in my life.  I'm just starting to read up (with what time I have) on a Ubuntu book.  Thanks again.

Aluminum Powerbook (v5.9) G4 17"
Broadcom Wireless BCM 4318 (Air Force One 54G)
Ubuntu 6.10 incl. all updates

---

### Post by Win2Mac2Linux on 2007-01-18
Just thought i would add the results from terminal:

ed@ed-laptop:~$ lspci | grep Broadcom\ Corporation
0001:10:11.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
ed@ed-laptop:~$ 

However, I also get this:

ed@ed-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ed@ed-laptop:~$ 

Not sure of the deeper meanings of these commands, but thought they might be helpful to those more knowledgeable.  Thanks for any help you can provide.




I

---

### Post by phossal on 2007-01-18
No clue what's plaguing you guys. I'm surprised more people haven't jumped in to help though. I figured if we kept bumping the thread, *someone* would be able to help you guys. 


Maybe write your own device driver?  :p

---

### Post by phossal on 2007-01-18
Did you install this using ndiswrapper? If so, what's the output to:
```
ndiswrapper -l
```

---

### Post by Win2Mac2Linux on 2007-01-18
> **phossal said:**
> Did you install this using ndiswrapper? If so, what's the output to:
```
ndiswrapper -l
```

I thought I did, but this is what I got on your command request:

ed@ed-laptop:~$ ndiswrapper 
bash: ndiswrapper: command not found
ed@ed-laptop:~$ 

Thoughts?  I'm not quite sure what the underlying technical meaning of all this is (I got a kick out of the "write your own driver" comment (LOL)), but if I remember correctly, I followed all the steps from the how-to and it appeared to go okay.  Of course, it was after that the wireless option under networking disappeared.  I'm guessing I'm going to have to do something to restore it and then start over?  Like you I'm also surprised more people haven 't jumped in.  I can't complain though.  I've gotten lots of feedback so far, but since the wireless "disappeared", you appear to be my only hope ("Help me Obi Wan...).
Thanks again for your help.    :-D

---

### Post by Mimsy on 2007-01-18
> **phossal said:**
> Maybe write your own device driver?  :p

Yeah, right... and after that I will right this beautiful poem in ancient Chinese calligraphy, that I mysteriously will be fluent in... :p 

Once again, come weekend, I will disable WPA for the router and see what happens.

/Mimsy

---

### Post by phossal on 2007-01-18
> **Win2Mac2Linux said:**
> I thought I did, but this is what I got on your command request:
ed@ed-laptop:~$ ndiswrapper 
bash: ndiswrapper: command not found
ed@ed-laptop:~$

Here is what ndiswrapper output looks like:
```
bash 3.1:ndiswrapper -l
Installed drivers:
**net111v2beta            driver installed, hardware present **
netwg111v1              driver installed 
bash 3.1:
```

I switch between versions of my hardware when I'm trying to help support the tutorial I wrote on them, but you can see that ndiswrapper -l is confirming a) that ndiswrapper is installed b) that my drivers are there and c) that my hardware is present.

The fact that it's not even recognized as a command for you is a very, very bad sign. lol

I'm not even sure your hardware *requires* ndiswrapper. How involved do you want me to get? Do I have to read the tutorial on it, or are we sure it needs it?  If it does, you should install it like so:
```
sudo apt-get install ndiswrapper-utils-1.8
```

---

### Post by phossal on 2007-01-18
> **Mimsy said:**
> Yeah, right... and after that I will right this beautiful poem in ancient Chinese calligraphy, that I mysteriously will be fluent in... :p 

I'm in the process of learning Chinese (or Mandarin, or Hanyu/Hanzi). I know a thousand words or so, but I can only write about 50 characters. I need an art class. I couldn't write any beautiful poems, but I could probably order the three of us some chicken. :D

And I may have to use it during a call to tech support to figure out why your hardware doesn't work.

---

### Post by phossal on 2007-01-18
If I become a 5-Shot Grande Mocha Cappuccino Latte by posting a few thousand times in *just this thread*, you two will officially be a geek's nightmares. :D While one of you is installing ndiswrapper, and the other is counting down the days to the weekend, I'll read the tutorial on your hardware.

---

### Post by Win2Mac2Linux on 2007-01-18
> **phossal said:**
> Here is what ndiswrapper output looks like:
```
bash 3.1:ndiswrapper -l
Installed drivers:
**net111v2beta            driver installed, hardware present **
netwg111v1              driver installed 
bash 3.1:
```

I switch between versions of my hardware when I'm trying to help support the tutorial I wrote on them, but you can see that ndiswrapper -l is confirming a) that ndiswrapper is installed b) that my drivers are there and c) that my hardware is present.

The fact that it's not even recognized as a command for you is a very, very bad sign. lol

I'm not even sure your hardware *requires* ndiswrapper. How involved do you want me to get? Do I have to read the tutorial on it, or are we sure it needs it?  If it does, you should install it like so:
```
sudo apt-get install ndiswrapper-utils-1.8
```

When I ran the command in terminal I got:

ed@ed-laptop:~$ sudo apt-get install ndiswrapper-utils-1.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.8
ed@ed-laptop:~$ 

I went to the Synaptic Package Manager and looked up ndiswrapper.  Of the 4 options it only allowed me to choose/install two of them (ndiswrapper-common and ndiswrapper-source).  The others couldn't be installed because they depended on the last choice (ndiswrapper-utils) which in the description in the bottom pane the last part stated "This is a dummy package for transitional purposes.  It will go away at some point soon."   I was reading on another website that supposedly this chipset has been supported in the kernel for awhile now (I don't really have an idea what I just said, but I get the general idea).  I just want my wireless going and I'll tough it out through the rest after that.  BTW, at home I am using a D-Link DGL-4300 wireless with SSID turned off and WPA-AES.  
Don't know how much of a difference that makes.  When the wireless option was originally there under System>Admin>Networking I entered the ESSID (I'm assuming that was the same as SSID) and the key I was using, but still nothing at that time.  My brain is pretty fried on this right now and it's late for me (actually it's now 5 am, boy how time flies when you're having fun with Linux)  ;) 

After doing what I could with Synaptic Package Manager now I still get:

ed@ed-laptop:~$ sudo apt-get install ndiswrapper-utils-1.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.8
ed@ed-laptop:~$ 

I'll hopefully be back to try and continue to sort this out.  Thanks again for your help.

---

### Post by Mimsy on 2007-01-18
> **phossal said:**
> If I become a 5-Shot Grande Mocha Cappuccino Latte by posting a few thousand times in *just this thread*, you two will officially be a geek's nightmares. :D While one of you is installing ndiswrapper, and the other is counting down the days to the weekend, I'll read the tutorial on your hardware.

I have that title too. ;)

Weekend, WPA disabled. Meanwhile, I am learning as much as I can about my router, by reading everything I can find about it. Every little bit helps, after all.

/Mimsy

---

### Post by Mimsy on 2007-01-20
According to what I found out about the wireless router, if I disable all security on it, I will need to set up the network from scratch all over again. That includes the other laptop, the two desktop PCs and the Xbox 360. The 360 is a royal pain, and the other laptop is a work-issued one, with very limited user rights and privileges. I contacted the manufacturer's customer support, and they confirmed this. ](*,) 

I have decided not to disable WPA on our wireless network now, since reconfiguring a 360 and a laptop that won't let you touch the system settings is time-consuming and painful. Sorry.

If this means I can't connect with my own Ubuntu laptop I will try to live with that, I am not without internet capable systems after all. It would just have been nice... :( 

/Mimsy

---

