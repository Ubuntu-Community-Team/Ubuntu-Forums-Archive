---
title: "Firefox Issues w/ Intrepid"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by MooseMagnet on 2009-01-20
Not sure how to describe these issues. They have happened after I evolved from Feisty to Intrepid.

In Firefox, I set View->Toolbars->Restore Defautlts, but... every time I open Firefox I must press F11 twice to be able to see the go-away box, minimize box, Time & Date, etc. The top two bars are hidden unless I press F11 twice every time I load Firefox.

Firefox is very slow loading pages, and when I scroll a page it is very jumpy. Many times, it seems to sleep before it loads a page. By sleep, I mean the screen dims for a few seconds.

When I wake the laptop up after it's been asleep, it is slow to display the screen, and the screen is scratchy and distorted during the wake-up.

Totem is very slow to load, and it seems to sleep before it loads. Same 'sleep' as when loading Web pages. And before Totem loads the video, the screen flickers and flashes.

I'd wonder if there is a problem with the video card? None of these things happened with Feisty. I suppose these are only nuisances, but I worry that an underlying problem should be fixed.

Anyone else have these problems, or know how to remedy them?

Thanks.

---

### Post by gettinoriginal on 2009-01-20
First problem, no title bar:  After you hit F11 twice, manually minimize the page, close firefox, reopen, then maximize with the max button, that should solve that problem.

All other problems depend on if you are running compiz or not.  If you are, into terminal type:
```
compiz --replace
```
If you are not running compiz:
```
metacity --replace
```       :p

---

### Post by kansasnoob on 2009-01-20
Wow! Feisty to Intrepid!

Did you keep the same /home!

Exactly how did you upgrade?

---

### Post by fooman on 2009-01-20
> **MooseMagnet said:**
> In Firefox, I set View->Toolbars->Restore Defautlts, but... every time I open Firefox I must press F11 twice to be able to see the go-away box, minimize box, Time & Date, etc. The top two bars are hidden unless I press F11 twice every time I load Firefox.


for the firefox fullscreen problem,  the solution is simple:

press f11 twice to get to a normal screen.

next click the unmaximize button.

close firefox.

reopen firefox.

maximize firefox.

that should fix it....for good. :D

---

### Post by gettinoriginal on 2009-01-20
As far as the speed of Firefox, see here:
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by kansasnoob on 2009-01-20
Actually, even before you answer, I wonder what version of Firefox Feisty was running?

I just did some testing for Nanotube at Ubuntuzilla and I'm thinking even Gutsy is stuck on Firefox 2.

It might be worth the time to try Ubuntuzilla. I'm not at all sure.

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

If you decide to try it just download it to your desktop, then double click the desktop icon to install it to the repos.

Then make sure Firefox is shutdown and in terminal run:

```
ubuntuzilla.py -a install -p firefox
```

I didn't test Feisty because it's reached "end of life".

---

### Post by MooseMagnet on 2009-01-21
Okay, hang on.

Gettinoriginal: How do I know which I'm running? Compiz or Metacity? I don't know which commands to run.

Kansasnoob: I saved my pics, music, etc. to my USB drive, and did a clean install with Intrepid. Am now working out the kinks.

To All: Firefox displays the full screen now. That was simple. Thank you all very much.

Gettinoriginal: I followed the steps in this ([http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)) but Firefox still loads weird. It doesn't display itself smoothly - it's hard to describe. Scratchy, puzzled, jumpy, jerky when it loads. I don't know anything about computers, but if I guessed, I'd say the video card isn't happy.

And Totem still loads really slowly, and flickers and flashes as it does. Weird.

Kansasnoob: I'll try Unbuntuzilla. But it's not just Firefox that is jerky and scratchy. Dang, I can't describe it with words very well at all.

How do I know? Compiz or Metacity?

Thanks

---

### Post by MooseMagnet on 2009-01-21
Something is very wrong with Firefox on Intrepid that was not a problem with Feisty.

It goes to sleep - the screen turns gray color - while it loads pages very slowly. Maybe I should report it as a bug?

---

### Post by gettinoriginal on 2009-01-21
Go to System, Preferences, Appearance, Visual Effects, is it set to Extra or Custom ?? If it is, then Compiz is enabled, if it is set to none, then metacity is.

---

### Post by MooseMagnet on 2009-01-21
LOL.

It's set to Normal.

Compiz or Metacity?

---

### Post by gettinoriginal on 2009-01-21
compiz  LOL, sorry about that.  But since you are not getting decent graphics, try setting it to Extra, that may help your problem.  It also will not hurt to copy/paste to terminal:
```
compiz --replace
```
If your graphics remain poor, try:
```
Metacity --replace
``` to see if things improve.

---

### Post by MooseMagnet on 2009-01-22
Well... It's still weird, but I'll do what I can to live with it. Frustrating that not all things work after upgrading. Oh well. Nothing is perfect.

metacity --replace does nothing but freak it out

Here's the results of compiz --replace.  Does all look right??

rich@rich-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by gettinoriginal on 2009-01-22
No, it is still not right.  Please run the following in terminal and post the results:
```
sudo gedit etc/X11/Xorg.conf
```

---

### Post by MooseMagnet on 2009-01-22
Nothing - xorg.conf is empty.

But isn't that information now in HTML format, in a different place? I looked for the post that has that info, but haven't been about to find it.

---

### Post by MooseMagnet on 2009-01-22
This:

[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

---

### Post by gettinoriginal on 2009-01-22
This may be your problem if Xorg is totally empty.  Yes, they are trying to program away from it, but some is still left.
Reboot, and at the grub splash hit escape and enter recovery mode, after that finishes, choose "try to fix x", then resume normal boot.

---

### Post by MooseMagnet on 2009-01-23
No luck. Hit esc at Grubb. Recovery Mode. Try to Fix X Server. Then it displayed one sentence for a few seconds only. I couldn't read it quick enough to tell you what it said. Then it went back to the recovery mode screen and I selected normal boot. 

Same thing with xorg - nothing. Same graphics problem - no difference.

Maybe I should report it to launchpad as a bug??

---

### Post by MooseMagnet on 2009-01-24
Not good. Reported it to launchpad. Followed some advice. Caused the laptop to boot to a text screen only. Tried Recovery and other boots. No luck.

Had to start from scratch with clean install of Intrepid. Lost data and time.

Now I'm back to setting up the thing from start. Will be several days until I can have the luxury of dealing with the graphics issue.

---

### Post by MooseMagnet on 2009-01-27
How can I install Firefox 2 with Intrepid (and get rid of Firefox 3)?

Spoke with a friend last night, and he said Firefox 3 is real bad slow on windoze also. It's so terribly slow with Intrepid. Have to click the touchpad numerous times, but it's not the touchpad, it's Firefox 3 that's slow as molases in January.

How can I get Firefox 2 back - with Intrepid?

---

### Post by nanotube on 2009-01-27
well, fwiw, i find ff3 is faster that ff2... but here's what you can try:

0. first, try starting firefox with a fresh profile (back up your old one). a lot of firefox issues end up being due to messed up profiles.

1. you can try installing ff3 using ubuntuzilla, that will install the stock mozilla build - maybe it will be better for you.

2. if you want to get ff2, you could also use ubuntuzilla to get the stock mozilla build of the latest ff2 - you just have to tell it not to install the latest v3, and instead manually enter the latest ff2 release. if you do that, suggest to start with a fresh profile.

---

### Post by MooseMagnet on 2009-01-27
ff3 won't accept mouse (touchpad) clicks. I click and click and click and click, but nothing happens. Have adjusted the touchpad numerous times. Only thing I can do is wait for ff3 to finish whatever it's doing, and then try clicking again.

I don't understand anything about the profile. I looked in the pull-downs, but nothing about a profile. How do I start with a fresh one, change the current one?

---

### Post by MooseMagnet on 2009-01-27
I installed ubuntuzilla, but where is it? 

and, what will this do:
ubuntuzilla.py -a install -p firefox

I don't like issuing terminal commands unless I'm sure they won't kill the system to a point where I can't recover it.

I am a common computer user. I know NOTHING about the inner workings of a computer. I use Ubuntu as a way to support open source. 

I have entered recommended terminal commands more than a few times, and had to completely rebuild the computer because of them.

This click click click click is driving me nuts. It did NOT do this problem with Feisty. That's one of the reasons I held on to Feisty as long as I did. Intrepid is really quite awful on this laptop.

Is Canonical/Ubuntu moving away from supporting laptops?

---

### Post by nanotube on 2009-01-28
your profile lives in your home dir in .mozilla/firefox
just close firefox, and rename that directory (say, firefox.bak), and start firefox again, and that's it, firefox will start with a fresh profile.

ubuntuzilla:
you can read about what exactly ubuntuzilla does on the website for the project (see my sig)

in brief: it downloads the firefox build from mozilla.com, unzips it into /opt/firefox directory, and sticks a link to it from /usr/bin/firefox (which is where the system normally looks for firefox). so, once you do that, you will be running the mozilla build when you start firefox, rather than the build that comes from the ubuntu repos.

if you don't like it for whatever reason, you can undo whatever it did by running "ubuntuzilla.py -a remove -p firefox", and it will wipe the mozilla build from /opt, and restore the /usr/bin/firefox link to point to the repos version.

hope this helps...

---

### Post by k3lt01 on 2009-01-30
> **MooseMagnet said:**
> I installed ubuntuzilla, but where is it?  It's in your / directory somewhere. Try looking at the Ubuntuzilla site for information.

> **MooseMagnet said:**
> and, what will this do:
ubuntuzilla.py -a install -p firefox

I don't like issuing terminal commands unless I'm sure they won't kill the system to a point where I can't recover it.This bypasses Ubuntu's standard Firefox profile and allows sudo (root) to update Firefox. By doing this you are effectively updating firefox from Mozilla itself.  When you see .py in a name it means that it is a python script. Scripts automate tasks.

> **MooseMagnet said:**
> I am a common computer user. I know NOTHING about the inner workings of a computer. I use Ubuntu as a way to support open source. 

I have entered recommended terminal commands more than a few times, and had to completely rebuild the computer because of them. There are warnings all over the Ubuntu forums telling people NOT to do terminal commands UNLESS they know and understand what it does.

> **MooseMagnet said:**
> This click click click click is driving me nuts. It did NOT do this problem with Feisty. That's one of the reasons I held on to Feisty as long as I did. Intrepid is really quite awful on this laptop. You aren't criticizing are you? Also you are adding issues to a thread after you have started it. How are people supposed to keep up with you?

> **MooseMagnet said:**
> Gettinoriginal: How do I know which I'm running? Compiz or Metacity? I don't know which commands to run. Go to Synaptic click on a program then type Compiz, if it is installed you will see the square is green, now do the same thing for Metacity.

> **MooseMagnet said:**
> Something is very wrong with Firefox on Intrepid that was not a problem with Feisty.

It goes to sleep - the screen turns gray color - while it loads pages very slowly. Maybe I should report it as a bug?How much RAM do you have? The going grey isn't the laptop going to sleep or for that matter FireFox. If you dont have enough RAM many programs will do this. How much SWAP do you have?

Feisty was pretty lightweight compared to Hardy and Intrepid, the latter 2 really require more RAM or SWAP than Feisty did.

One last point for the time, I don't think three pages of replies shows that your problems are being ignored like you claimed they are.

---

### Post by MooseMagnet on 2009-01-30
Thank you for your help and explanations. I don't know computers as well as most of you.

I should start a thread of general frustration of not being experienced enough and smart enough to upgrade to Intrepid. I have done everything that everyone has suggested - except for the things that are beyond my ability.

And the touchpad still does not work properly, the graphics are very distorted, and Firefox and Totem load so slowly it goes to sleep. I guess that's because I need more memory to run Totem now. I need to purchase another laptop?

I'll take 100% responsibility for not having enough smarts. Feisty worked great. Intrepid is lots of problems for me. That is what's frustrating. I've been saddled with a cumbersome OS. A very disappointing thing, considering how well Feisty worked.

Sorry to be so ignorant about Linux, and sorry for needing so much help. And sorry I don't understand most of what you tell me. I am not a UNIX administrator. I am just a common Internet browser/home computer user.

How much RAM or SWAP do I need? How do I download that?

---

### Post by kansasnoob on 2009-01-30
I've been extremely pleased with the official Mozilla build of Firefox using Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by k3lt01 on 2009-01-30
You are very welcome, help is what this community is about. All you have to do is ask, be very clear and concise though.

Don't take this personally but your first mistake was taking such a big leap in the distribution. Seriously, Hardy (8.04) is an LTS (Long Term Support) and once things are sorted you wont have to worry about anything for at least 3 years. Feisty, Gutsy, and Intrepid are just regular releases and ar only supported for 18 months so in 18 months time you will have this same trouble again.

> **MooseMagnet said:**
> And the touchpad still does not work properly, the graphics are very distorted, and Firefox and Totem load so slowly it goes to sleep. I guess that's because I need more memory to run Totem now. I need to purchase another laptop? I can't help you with the touchpad unfortunately, that will have to be left to other Dell users and people with experience in that type of thing. However, I will say don't go and get another laptop unless you really, Really, REALLY, have to.


> **MooseMagnet said:**
> I'll take 100% responsibility for not having enough smarts. Feisty worked great. Intrepid is lots of problems for me. That is what's frustrating. I've been saddled with a cumbersome OS. A very disappointing thing, considering how well Feisty worked. It was the exact opposite for me, apart from a few issue with Gutsy that were my own fault, Ubuntu got better and better and easier to use.

> **MooseMagnet said:**
> Sorry to be so ignorant about Linux, and sorry for needing so much help. And sorry I don't understand most of what you tell me. I am not a UNIX administrator. I am just a common Internet browser/home computer user. Don't take this personally either, but please stop with the self pity. I'm not an admin either, I just learned by listening, reading and watching.

> **MooseMagnet said:**
> How much RAM or SWAP do I need? How do I download that?Ram is part of the laptop if your laptop is under a year old it will probably have 1 gb, mine has 256 mb which is 1/4 of 1gb. When you set Ubuntu up you can set the partitions up manually, depending on your hard drive size (my original hard drive was 40 gb so I will use it as an example) you would use 10gb for /, 2 gb for SWAP, and the rest which in my case was 28 gb for /home. 

Google Ubuntu Screencasts, on a pc that has a browser working ok if you can. It has video podcasts which show you how to do various things such as setting up partitions.

---

### Post by nanotube on 2009-01-31
> **MooseMagnet said:**
> Thank you for your help and explanations. I don't know computers as well as most of you.

I should start a thread of general frustration of not being experienced enough and smart enough to upgrade to Intrepid. I have done everything that everyone has suggested - except for the things that are beyond my ability.

And the touchpad still does not work properly, the graphics are very distorted, and Firefox and Totem load so slowly it goes to sleep. I guess that's because I need more memory to run Totem now. I need to purchase another laptop?

I'll take 100% responsibility for not having enough smarts. Feisty worked great. Intrepid is lots of problems for me. That is what's frustrating. I've been saddled with a cumbersome OS. A very disappointing thing, considering how well Feisty worked.

Sorry to be so ignorant about Linux, and sorry for needing so much help. And sorry I don't understand most of what you tell me. I am not a UNIX administrator. I am just a common Internet browser/home computer user.

How much RAM or SWAP do I need? How do I download that?

so, have you tried doing the fresh profile for firefox? have you tried ubuntuzilla? advice doesn't work if you don't try it. :)

if nothing else works, you could always do a clean install of hardy, that's an LTS release, so should be "more stable"...

---

### Post by ugm6hr on 2009-01-31
> **k3lt01 said:**
> How much RAM do you have? The going grey isn't the laptop going to sleep or for that matter FireFox. If you dont have enough RAM many programs will do this. How much SWAP do you have?

I suspect this is the problem.  Feisty was slightly lighter, due to not running Compiz.  Compiz turns the winodw grey while it is "thinking" - generally because your hardware can't cope.

Also - you are meandering with this thread.  It makes it very difficult to help if you do this.  Read the "How to get help" link in my signature for more advice - but in simple terms:
1. Describe the problem in detail
2. Don't fill your response with irrelevant stories about how frustrated you are
3. Include details about your setup
4. Describe what you have already done
5. Limit yourself to 1 problem per thread
6. If you don't know how to do any of the above - ask.

With regard to Terminal commands - you can find out what they do with (example below):
```
man **command**
man free
```

Now - moving on to trying to solve the problem(s):

1. Remove Compiz:
```
sudo apt-get remove compiz-core
```

2. Tell us how much ram you have - post the output:
```
free -m
```

3. See what's taking all the processor:
```
top
```

---

### Post by MooseMagnet on 2009-01-31
Thank you. I do apologize for the ambivalent posts. I will refrain from that from now on. With that said - I have focused on getting the touchpad to work, and planned on coming back to this issue after I fixed that. It is now fixed. Hooray. Synaptics does not work anywhere near as well as gsynaptics - difference is like night and day. Sorry for the off post, but wanted to explain why I have not worked on the Firefox issue.
------------------------------------------------------------------
sudo apt-get remove compiz-core  --  seems to have worked okay.
------------------------------------------------------------------
rich@rich-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           494        467         26          0          3        102
-/+ buffers/cache:        362        132
Swap:         1451        146       1304
rich@rich-laptop:~$ 
------------------------------------------------------------------
rich@rich-laptop:~$ top

top - 18:15:32 up  7:26,  2 users,  load average: 0.23, 0.62, 0.39
Tasks: 109 total,   2 running, 107 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.9%us,  1.7%sy,  0.0%ni, 68.8%id,  8.3%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    505992k total,   491208k used,    14784k free,     4272k buffers
Swap:  1485972k total,   150376k used,  1335596k free,   110972k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5259 rich      20   0  7736 4684 2188 S  9.3  0.9   0:06.20 gconfd-2           
 4907 root      20   0  398m  27m 6320 R  5.3  5.5   8:34.69 Xorg               
24651 rich      20   0 98.1m  17m  11m S  1.3  3.5   0:01.58 gnome-terminal     
 5353 rich      20   0 24480  13m 6684 S  0.7  2.7   0:43.52 compiz.real        
 5603 rich      20   0  377m 150m  21m S  0.7 30.5  25:00.76 firefox            
24865 rich      20   0  2416 1144  884 R  0.7  0.2   0:00.34 top                
    1 root      20   0  3056  912  492 S  0.0  0.2   0:01.44 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.90 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:02.24 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.30 kblockd/0          
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       

I will install and work with ubuntuzilla tomorrow when more rested, and then report the results here.

---

### Post by MooseMagnet on 2009-01-31
Here are the command results after restarting.
----------------------------------------------------------------
rich@rich-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           494        484          9          0         11        152
-/+ buffers/cache:        321        172
Swap:         1451          1       1449
rich@rich-laptop:~$ 
----------------------------------------------------------------
Strange... I can't copy/paste the results of the 'top' command. I highlight the text, release the mouse button, and the highlight goes away. But by observing the results, I see no mention of Compiz. Otherwise, it looks the same to me.

---

### Post by ugm6hr on 2009-01-31
How does FireFox behave now that you have removed Compiz?

---

### Post by MooseMagnet on 2009-02-01
Yes, Firefox works like it should now. Fast as usual, and the graphics are nice and crisp. Thank you for solving that. Totem behaves better also. Thank you very much.

---

### Post by ugm6hr on 2009-02-01
> **MooseMagnet said:**
> Yes, Firefox works like it should now. Fast as usual, and the graphics are nice and crisp. Thank you for solving that. Totem behaves better also. Thank you very much.

Happy to help.

---

