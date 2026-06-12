---
title: "Not enough hardware for Natty-Unity"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by sewbiz on 2011-06-03
Do I need to uninstall Natty-Unity? I found out too late I don't have enough hardware.  Is this why my computer is soooooooo s   l    o    w? Do I need to go back to 10.10 Jaunty?

I have been working on this for weeks. Please any advice appreciated.:(

---

### Post by wojox on 2011-06-03
Have you booted into Classic in Sessions so it doesn't use Compiz?

---

### Post by sewbiz on 2011-06-03
yes

---

### Post by sewbiz on 2011-06-03
> **wojox said:**
> Have you booted into Classic in Sessions so it doesn't use Compiz?


Are there updates I should install? And how do I do that? I don't have my panels /menues or launchers on my desktop anymore. I have to go to a terminal for everything. I am a noob. This isn't easy to know what command to type.

Help is much appreciated.

---

### Post by JohnBonne on 2011-06-03
> **sewbiz said:**
> Do I need to uninstall Natty-Unity? I found out too late I don't have enough hardware.  Is this why my computer is soooooooo s   l    o    w? Do I need to go back to 10.10 Jaunty?

I have been working on this for weeks. Please any advice appreciated.:(

Why do you think you haven't enough equipment?  

Is you computer old?

How well did it run 10.10?

---

### Post by wojox on 2011-06-03
I don't know if there are updates. Try this:

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by sewbiz on 2011-06-03
> **JohnBonne said:**
> Why do you think you haven't enough equipment?  

Is you computer old?

How well did it run 10.10?


It ran alright with 10.10. My recollection of how I found out that I didn't have enough hardware is because of something to do with the Unity thing. (I have been working on this for weeks but not consistently because of other obligations.)

I think  during the process of of maybe  updating..... perhaps the things that were installed (using Synaptic package manager) I got a pop up or something that told me I didn't have enough hardware for Unity. I should have taken notes. Hmmm....sorry!

I have a Compaque Presario 2100...about 7 years old  but I installed more memory. (Not a geek...but could tell you more.)

---

### Post by sewbiz on 2011-06-03
> **wojox said:**
> I don't know if there are updates. Try this:

```
sudo apt-get update; sudo apt-get upgrade
```


thanks wojox. There were 14 things upgraded.  chromium browser/codecs...gnome nettool....blah...blah.

Is that what I do than each time to check and install updates?  Terminal and those commands?

---

### Post by sewbiz on 2011-06-03
> **sewbiz said:**
> It ran alright with 10.10. My recollection of how I found out that I didn't have enough hardware is because of something to do with the Unity thing. (I have been working on this for weeks but not consistently because of other obligations.)

I think  during the process of of maybe  updating..... perhaps the things that were installed (using Synaptic package manager) I got a pop up or something that told me I didn't have enough hardware for Unity. I should have taken notes. Hmmm....sorry!

I have a Compaque Presario 2100...about 7 years old  but I installed more memory. (Not a geek...but could tell you more.)



Does this sound like I have enough hardware?  If anyone can answer, very appreciative!  ;)

---

### Post by JohnBonne on 2011-06-03
> **sewbiz said:**
> Does this sound like I have enough hardware?  If anyone can answer, very appreciative!  ;)

Do you have a couple of gigs of RAM? The RAM and FSB you use is pretty rusty technology but I have a Desktop from about the same era I am thinking could I use Ubuntu on. Are you running Vista in a dual boot, or something else? Was the original O/S Vista or XP? 

10.10 sounds more stable. I first really got into repairing computers in early 2000's. Building computers / Set-ups / Installs were a bit tricky then is why i ask the questions. You are doing good.

---

### Post by I2k4 on 2011-06-04
My simple experience as a new user running Live off a 4GB PenDrive on a netbook (i.e. has twice the specs of my still running Dell Inspiron 8100 laptop) is that 11.04 was noticeably, I'll say unacceptably, slower than any of the 10.10 versions I've tried.  

I had been looking forward to trying it, but a couple of days of diminished performance and the intrusive Unity sent me scuttling back to Lubuntu 10.10.  I even tried Lubuntu's new 11.04 and dumped it because the performance hit is still there.

---

### Post by sewbiz on 2011-06-07
> **JohnBonne said:**
> Do you have a couple of gigs of RAM? The RAM and FSB you use is pretty rusty technology but I have a Desktop from about the same era I am thinking could I use Ubuntu on. Are you running Vista in a dual boot, or something else? Was the original O/S Vista or XP? 

10.10 sounds more stable. I first really got into repairing computers in early 2000's. Building computers / Set-ups / Installs were a bit tricky then is why i ask the questions. You are doing good.

I had Windows XP.  I am not running it side by side.

I don't know how much RAM or gigs I have. I will have to check. I think a lot of gigs though.

---

### Post by jramshu on 2011-06-07
Run this in terminal to check for Unity compatibility.

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by walt.smith1960 on 2011-06-07
If you're running 11.04 in classic mode, you can get the Applications-Places-System menu back.  Right click on the top bar, click "add" and there should be two menu choices.  Select the second choice.  In Unity, I press the "windows" key on the keyboard and type "upd" and update manager should appear.  If your hardware is pretty weak, you might try downloading Lubuntu and run it as a live session to see how your hardware behaves.  I'm running Lubuntu on an IBM Thinkpad that will celebrate its 10th birthday next year-P3 and 512 Mb. RAM.  It runs pretty well.  I  did find it better to start initially with "nomodeset" enabled but otherwise very straightforward.

---

### Post by jramshu on 2011-06-07
Don't listen to me I was thinking Ubuntu 11.04 w/Unity. 

My bad. I see the OP was asking about Lubuntu.

---

### Post by DevilSolution on 2011-06-07
What are your system specifications? i doubt its lack of hardware unless your running like 512ddr ram and some legacy processor because unity runs smoothly on my pc with a p4 3.0ghz, 1GB ram...if your specs are similar to mine or better then the issue is to do with compatibility not power, there may be a work around for this i.e. adding something to a config file but im rather new to ubuntu so i wouldnt know where to start, i do seriously doubt that its because your pc isnt powerful enough tho. Write down your specs and ill read into it for you....irc is always useful.

---

### Post by sewbiz on 2011-06-07
> **DevilSolution said:**
> What are your system specifications? i doubt its lack of hardware unless your running like 512ddr ram and some legacy processor because unity runs smoothly on my pc with a p4 3.0ghz, 1GB ram...if your specs are similar to mine or better then the issue is to do with compatibility not power, there may be a work around for this i.e. adding something to a config file but im rather new to ubuntu so i wouldnt know where to start, i do seriously doubt that its because your pc isnt powerful enough tho. Write down your specs and ill read into it for you....irc is always useful.

Please help me find this info without a menue bar on my desktop (since installing Natty) and all my launchers are gone. I don't have this info in my head and don't know where I ever wrote it down.
  I used to just be able to look this up by clicking on my icon....My Computer.

How do I type something in a terminal to find this info you are asking about?   Any help is appreciated.

---

### Post by sewbiz on 2011-06-07
> **walt.smith1960 said:**
> If you're running 11.04 in classic mode, you can get the Applications-Places-System menu back.  Right click on the top bar, click "add" and there should be two menu choices.  Select the second choice.  In Unity, I press the "windows" key on the keyboard and type "upd" and update manager should appear.  If your hardware is pretty weak, you might try downloading Lubuntu and run it as a live session to see how your hardware behaves.  I'm running Lubuntu on an IBM Thinkpad that will celebrate its 10th birthday next year-P3 and 512 Mb. RAM.  It runs pretty well.  I  did find it better to start initially with "nomodeset" enabled but otherwise very straightforward.

Where is the top bar?  I just have a blank desktop with my screensaver and my folder icons and such. No launchers, no menu bar where I had the  applications thing before I upgraded. :guitar:

---

### Post by walt.smith1960 on 2011-06-08
> **sewbiz said:**
> Where is the top bar?  I just have a blank desktop with my screensaver and my folder icons and such. No launchers, no menu bar where I had the  applications thing before I upgraded. :guitar:
Here are a couple screen shots.  

[ATTACH]194574[/ATTACH]

[ATTACH]194575[/ATTACH]

I've always had the global menu and right top stuff so I've always had the top bar.  I didn't have the Applications-Places-System menu. I was able to get that menu by right-clicking the top bar then "Add to Panel -> Menu Bar.  If you don't have a top bar at all, there is a way to bring that back in older distros.  I don't know if those procedures will work in Natty or not.

Bear in mind this is the Ubuntu **Classic** desktop, selected at user logon.   The Ubuntu (Unity) desktop does not have the top bar by design.  I hope this is of some help to you.

---

### Post by grahammechanical on 2011-06-08
May I make a couple of points?

1) When you log in click on your user name and then look at the bottom panel. You will see three little boxes with menus. The right hand box will give you the option to use Ubuntu Classic. Click on that and you will load into the standard Ubuntu desktop with Applications, Places and System in the top panel. Is this what you are looking for?

2) When you click on the shutdown icon you get a menu. Is this correct. Do you see the line System Settings? Click on that and you will get all the options under the menus of System>Preferences and System>Administration.

3) When I upgraded to 11.04 I got a message that I did not have the hardware to run Unity. But I do have the right hardware. May be you do too. Go to Additional Drivers and activate the recommended driver. Then when you reboot and log in, that menu that I mentioned in point 1 will show Ubuntu as an option. That will give you the Unity User Interface.

4) If you do not have hardware powerful enough to run Unity you can install Unity 2D from the Ubuntu Software Centre and that will give you the look of Unity on less powerful hardware.

5) What have you been doing to fix things? Perhaps some of your problems (including slowness) are due your attempts to fix things. Some people have tried to un-install Unity and ended up with problems like the ones that you have. All they needed to do was boot into Ubuntu Classic.

That is more than a couple of points. I am sorry.

Regards.

---

### Post by sewbiz on 2011-06-09
TMI....thank you for your help graham (for short). If you read the beginning threads you will see that I did click on Ubuntu Classic, and all I get is a desktop that looks the same but without the menu bar.

My son helped me last night with this via skype messaging. 

Open terminal: type    'gnome-panel'    unless it was   'sudo gnome-panel'     enter.
I got it back.    However, when I closed the terminal...I lost it again. 
Then he suggested     'gnome-panel &'      that worked if I wanted IT to run and something else.   Putting the '&' after it allowed it to keep running.      I don't know, for awhile, when I started my computer up, the panels once again were missing. I knew what to do. Today however, was different.  I started the computer and the panels were there just like before. Weird. Ubuntu is a funny thing but I love it even with all the frustrations because it is FREE.  

I hope this has helped someone out there who is having the same problem. I do have enough hardware so don't always believe the messages you get. Go to the Ubuntu community and together we can work it out.

---

