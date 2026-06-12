---
title: "I have no Idea wth I am doing"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Irishbmx on 2009-01-28
So I got a new MB ect and couldn't install my version on windows on it and I've had this Ubuntu 8.04 disk laying around I've always wanted to switch to but was to lazy.

Well now I'm stuck and banging my head against the wall I have the 64 bit edition I can't figure anything out. I tried fallowing the tutorial for Flash player with no luck, I can't find the driver for my motherboard which is an XFX Geforce 8200.

I wanna set it up for gaming ect so I know I'ma need wine and sound and graphix lol but for the life of me I can't understand anything.

So any help is appreciated and please not I am a complete noob to non windows OS so more detail the better :) what programs do I need what extras should I get and how do I do it all ect ect ect or just /wrist me.

---

### Post by Cypher on 2009-01-28
If you're primary use for the computer is gaming and that too the latest games, know that you will have a lot of trouble getting them to run under Wine.

If the games are older, then you might have a better chance of playing them.

For you GeForce graphics card, you can install the NVidia Restricted drivers to get full support.

Rather than play with Ubuntu 8.04, you should start with Ubuntu 8.10..

---

### Post by SunnyRabbiera on 2009-01-28
Well what is your processor type?
Your motherboard should work fine without drivers or anything, but is your issue a display issue or what?
You didnt specify what your issue exactly is

> **Cypher said:**
> If you're primary use for the computer is gaming and that too the latest games, know that you will have a lot of trouble getting them to run under Wine.

If the games are older, then you might have a better chance of playing them.

For you GeForce graphics card, you can install the NVidia Restricted drivers to get full support.

Rather than play with Ubuntu 8.04, you should start with Ubuntu 8.10..


I disagree, 8.04 might be older but a lot of people have had issues with 8.10.
8.10 is not much different underneith anyhow, not much of an improvement either as ibex has no easy to use tool for monitor settings...

---

### Post by jerome1232 on 2009-01-28
Flash is  actually very easy to install

```
sudo apt-get install flashplugin-nonfree
```

Actually if you want mp3 playback, java, and alot of other goodie codecs

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Rabindranath on 2009-01-28
Welcome to ubuntuforums. Try installing the flash player from the synaptic package manager. You can find it at System>Administration>Synaptic Package Manager.

I think you need to enable the "universe" and "multiverse" in the software sources. You can find it at System>Administration>Software Sources

Then search for "flash player" , "wine" in the synaptic package manager and click apply. You can also use the "Add or remove Programs" under the "Applications" tab to add or remove software.

And finally install the Graphics Driver through the "Restricted Drivers management".

---

### Post by Irishbmx on 2009-01-28
> **SunnyRabbiera said:**
> Well what is your processor type?
Your motherboard should work fine without drivers or anything, but is your issue a display issue or what?
You didnt specify what your issue exactly is

It's an amd 64 x2 dual core 4600+ I have no sound no graphics options I am on the computer right now but it only displays a small box and I can't change the size ect. I can't get flash player to work eather and I can't figure out how to install any addons and pluggins and get them to work.

---

### Post by Irishbmx on 2009-01-28
> **Cypher said:**
> If you're primary use for the computer is gaming and that too the latest games, know that you will have a lot of trouble getting them to run under Wine.

If the games are older, then you might have a better chance of playing them.

For you GeForce graphics card, you can install the NVidia Restricted drivers to get full support.

Rather than play with Ubuntu 8.04, you should start with Ubuntu 8.10..
not newer games Eve online which is supported ect crap like that. Can I download something to upgrade Ubuntu to 8.10 or do I have to dl it and burn it to a disk cause I don't have any CDR's

---

### Post by Irishbmx on 2009-01-28
> **jerome1232 said:**
> Flash is  actually very easy to install

```
sudo apt-get install flashplugin-nonfree
```

Actually if you want mp3 playback, java, and alot of other goodie codecs

```
sudo apt-get install ubuntu-restricted-extras
```
lol sorry if this is dumb but ... how do I use those?

---

### Post by Rabindranath on 2009-01-28
Applications>Accessories>Terminal

Copy and paste the code in the terminal.

---

### Post by vandorjw on 2009-01-28
You can download the updates to get to 8.10 but I don't recommend it.
if you want to install something, just post on this forum what you want.

people will generally tell you a command to enter in the terminal.

if you don't know what the terminal is,click Applications --> Accessories --> Terminal.

---

### Post by DGortze380 on 2009-01-28
> **Irishbmx said:**
> 
I wanna set it up for gaming

Then run Windows. If you want a gaming rig, you're simply not going to be happy with and Linux Distribution.

---

### Post by philinux on 2009-01-28
> **Irishbmx said:**
> It's an amd 64 x2 dual core 4600+ I have no sound no graphics options I am on the computer right now but it only displays a small box and I can't change the size ect. 

Can you take a screen print of this small box. alt printscreen and attach it to a your post.

---

### Post by Irishbmx on 2009-01-28
> **Rabindranath said:**
> Applications>Accessories>Terminal

Copy and paste the code in the terminal.
ok I entered both codes flash player still doesn't work do I need to restart or did I screw something up when I tryd to install it before?

I ran some file I downloaded from a tutorial called get64bitflash in terminal earlier.

---

### Post by Irishbmx on 2009-01-28
> **philinux said:**
> Can you take a screen print of this small box. alt printscreen and attach it to a your post.
It won't show it it's just about 2 inches of black on the right and left.
I have a wide screen monitor my resolution is 1280x1024 refresh rate is 76 Hz and I can't change the settings.

I mainly wanna set the computer up so I can lay eve online and watch videos online.

---

### Post by Irishbmx on 2009-01-28
> **DGortze380 said:**
> Then run Windows. If you want a gaming rig, you're simply not going to be happy with and Linux Distribution.

I hate windows and my disk won't install on my computer cause it's not sp2.
I'm really just wanting to set it up for Eve online maybe other MMO's not worryd about other games.

---

### Post by jerome1232 on 2009-01-28
It just so happens Eve has a linux version so Linux will work for that [http://ccp.vo.llnwd.net/o2/linux/eve_000066_all.deb](http://ccp.vo.llnwd.net/o2/linux/eve_000066_all.deb)

But before you get into that there's some issues here. 

Where did you get that script can you link to it?  

Where the any errors from running those install commands I posted (sorry I forget to tell you how to open a terminal up, while the terminal may seem less friendly at first, it so much easier than telling people click here, there, then look for this halfway down the screen etc...)

What does firefox show if you goto "about:plugins", just type that in the url bar where you would normally type a web pages address.

---

### Post by Irishbmx on 2009-01-28
> **jerome1232 said:**
> It just so happens Eve has a linux version so Linux will work for that [http://ccp.vo.llnwd.net/o2/linux/eve_000066_all.deb](http://ccp.vo.llnwd.net/o2/linux/eve_000066_all.deb)

But before you get into that there's some issues here. 

Where did you get that script can you link to it?  

Where the any errors from running those install commands I posted (sorry I forget to tell you how to open a terminal up, while the terminal may seem less friendly at first, it so much easier than telling people click here, there, then look for this halfway down the screen etc...)

What does firefox show if you goto "about:plugins", just type that in the url bar where you would normally type a web pages address.

Yea I know eve has a version but whanted to get everything else etched out first.
when I enterd the commands it said done and as for firefox I don't see anything on there about flash player do you whant me to copy and link everything on that page?

[http://ubuntuforums.org/showthread.php?t=772490&highlight=flash+install](http://ubuntuforums.org/showthread.php?t=772490&highlight=flash+install)
is the thread I looked at I downloaded [http://home.comcast.net/~ubuntume/Get64bitFlash-0.1.tar.gz](http://home.comcast.net/~ubuntume/Get64bitFlash-0.1.tar.gz) and fallowd instructions
2. Right click on the tar.gz and select "Extract Here"
3. Close all browsers.
4. Inside the folder that extracts is a "Get64bitFlash" or "Get64bitJave" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done. 

Any idea what drivers I am suposed to download for my MB btw it's the integrated graphix on the xfx geforce 8200 I didn't know what drivers to choose.

---

### Post by crimesaucer on 2009-01-28
> **Irishbmx said:**
> So I got a new MB ect and couldn't install my version on windows on it and I've had this Ubuntu 8.04 disk laying around I've always wanted to switch to but was to lazy.

Well now I'm stuck and banging my head against the wall I have the 64 bit edition I can't figure anything out. I tried fallowing the tutorial for Flash player with no luck, I can't find the driver for my motherboard which is an XFX Geforce 8200.

I wanna set it up for gaming ect so I know I'ma need wine and sound and graphix lol but for the life of me I can't understand anything.

So any help is appreciated and please not I am a complete noob to non windows OS so more detail the better :) what programs do I need what extras should I get and how do I do it all ect ect ect or just /wrist me.



The new 64bit Flashplugin works perfectly for me. (same with the 64bit java)

---

### Post by jerome1232 on 2009-01-28
> **Irishbmx said:**
> Yea I know eve has a version but whanted to get everything else etched out first.
when I enterd the commands it said done and as for firefox I don't see anything on there about flash player do you whant me to copy and link everything on that page?

[http://ubuntuforums.org/showthread.php?t=772490&highlight=flash+install](http://ubuntuforums.org/showthread.php?t=772490&highlight=flash+install)
is the thread I looked at I downloaded [http://home.comcast.net/~ubuntume/Get64bitFlash-0.1.tar.gz](http://home.comcast.net/~ubuntume/Get64bitFlash-0.1.tar.gz) and fallowd instructions
2. Right click on the tar.gz and select "Extract Here"
3. Close all browsers.
4. Inside the folder that extracts is a "Get64bitFlash" or "Get64bitJave" file, double click on it.
5. Select "Run in Terminal"
6. When the terminal closes, restart your browser.
7. Your done. 

Any idea what drivers I am suposed to download for my MB btw it's the integrated graphix on the xfx geforce 8200 I didn't know what drivers to choose.

From what I see the script that you run and the packages nspluginwrapper and flashplugin-nonfree can conflict with each other.

did the libraries make it there?

Can you post the output of these commands? (ctrl+shift+c to copy out of a terminal)

```
ls -al /usr/lib/mozilla/plugins/
ls -al /usr/lib/firefox-addons/plugins
```


Wrap the output in code tags by typeing [noparse]```
 at the begining of the output and 
``` at the end of the output [/noparse]

---

### Post by Irishbmx on 2009-01-28
> **jerome1232 said:**
> From what I see the script that you run and the packages nspluginwrapper and flashplugin-nonfree can conflict with each other.

did the libraries make it there?

Can you post the output of these commands? (ctrl+shift+c to copy out of a terminal)

```
ls -al /usr/lib/mozilla/plugins/
ls -al /usr/lib/firefox-addons/plugins
```


Wrap the output in code tags by typeing [noparse]```
 at the begining of the output and 
``` at the end of the output [/noparse]

I got everything working now I reformatted cause I screwd up my video drivers ><

The only problem I have now is finding the proper video driver for my integrated video it's an amd xfx 8200 I've already screwd it up twice to were I just got random splatter of colors on the screen I figured out how to reset it but can't find the right ones, and the drivers from the nvidia site are .run wich doesn't seem to work for me.

I switched to ubuntu 32 bit 8.04 btw instead of the 64 bit.

---

### Post by jerome1232 on 2009-01-28
Just so you know to recover from that type of stuff (video messing up)

Hit ctrl+alt+f1 and you will land at a text based login.

you would run this to reconfigure xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo service gdm restart
```

Since using the restriced driver manager wasn't working for you I would try envy. Alot of people have had success with this. Note I'm giving you terminal commands but pretty much everything can be done via gui (I just never use the gui's for the most part and commands are easier to remember than 50 menu's)

```
sudo apt-get install envyng-gtk
sudo envyng -t
```

select the appropriate nvidia driver (177 or 173) and envy should take care of it for you. If when you reboot you are having horrible video issues then there's an easy to bring the gui back. Bring up a virtual console (ctrl+alt+f1)
login, then remove everything envy did
```
sudo envyng --uninstall-all
sudo service gdm restart
```
If that doesn't bring you back a login window
```
sudo reboot
```

The next step would be to try nvidia installer but it's a true pain :) So let's see if envy get's you going first.

---

### Post by Irishbmx on 2009-01-28
> **jerome1232 said:**
> Just so you know to recover from that type of stuff (video messing up)

Hit ctrl+alt+f1 and you will land at a text based login.

you would run this to reconfigure xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo service gdm restart
```

Since using the restriced driver manager wasn't working for you I would try envy. Alot of people have had success with this. Note I'm giving you terminal commands but pretty much everything can be done via gui (I just never use the gui's for the most part and commands are easier to remember than 50 menu's)

```
sudo apt-get install envyng-gtk
sudo envyng -t
```

select the appropriate nvidia driver (177 or 173) and envy should take care of it for you. If when you reboot you are having horrible video issues then there's an easy to bring the gui back. Bring up a virtual console (ctrl+alt+f1)
login, then remove everything envy did
```
sudo envyng --uninstall-all
sudo service gdm restart
```
If that doesn't bring you back a login window
```
sudo reboot
```

The next step would be to try nvidia installer but it's a true pain :) So let's see if envy get's you going first.

Your a life saver man <3 thanx a bunch about to restart and see if it worked.

---

### Post by Irishbmx on 2009-01-28
> **jerome1232 said:**
> Just so you know to recover from that type of stuff (video messing up)

Hit ctrl+alt+f1 and you will land at a text based login.

you would run this to reconfigure xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo service gdm restart
```

Since using the restriced driver manager wasn't working for you I would try envy. Alot of people have had success with this. Note I'm giving you terminal commands but pretty much everything can be done via gui (I just never use the gui's for the most part and commands are easier to remember than 50 menu's)

```
sudo apt-get install envyng-gtk
sudo envyng -t
```

select the appropriate nvidia driver (177 or 173) and envy should take care of it for you. If when you reboot you are having horrible video issues then there's an easy to bring the gui back. Bring up a virtual console (ctrl+alt+f1)
login, then remove everything envy did
```
sudo envyng --uninstall-all
sudo service gdm restart
```
If that doesn't bring you back a login window
```
sudo reboot
```

The next step would be to try nvidia installer but it's a true pain :) So let's see if envy get's you going first.

well the drivers work the screen now fills my whole monitor I had envy update the driver it detected my stuff all correctly  the problem I am having now is in firefox everything is really sketchy now like the letter overlap ect or cut off untell I highlight them I tryd to print screen to show you but when I hit print screen everything goes back to normal.

 that and eve online isn't working still it just goes to a black screen and flickers I am not using wine or any other program just the linux version for ubuntu.

---

### Post by jerome1232 on 2009-01-29
Can't say I can help with either of those, I'm not sure what your talking about with firefox and I've never played Eve Online.

Maybe try adjusting your font settings? (System-Prefrences-Appearence-Fonts make sure subpixel smoothing is selected and play with some settings)

I'd suggest hitting up Eve Online's knowledge base and their forums.
[http://myeve.eve-online.com/ingameboard.asp?a=channel&channelID=630463](http://myeve.eve-online.com/ingameboard.asp?a=channel&channelID=630463)

The only things I can suggest would be to ensure compiz is off (System-Preferences-Appearance-Visual Effects, click none. Also try launching it from a terminal and see if there's any helpful error messages.

---

### Post by Irishbmx on 2009-01-29
> **jerome1232 said:**
> Can't say I can help with either of those, I'm not sure what your talking about with firefox and I've never played Eve Online.

Maybe try adjusting your font settings? (System-Prefrences-Appearence-Fonts make sure subpixel smoothing is selected and play with some settings)

I'd suggest hitting up Eve Online's knowledge base and their forums.
[http://myeve.eve-online.com/ingameboard.asp?a=channel&channelID=630463](http://myeve.eve-online.com/ingameboard.asp?a=channel&channelID=630463)

The only things I can suggest would be to ensure compiz is off (System-Preferences-Appearance-Visual Effects, click none. Also try launching it from a terminal and see if there's any helpful error messages.

I got eve working I just dicked around with some of the settings I'll try the font thing now I just need to get a better sound driver and I'm golden sound works it's just really scratchy and when I play eve it cuts in and out.
think I'm starting to get the hang of it thanx a ton man.

Edit font and visual effects thing fixt it right up thanx man now just gotta do the sound but I'll mess with it tomarow.

---

