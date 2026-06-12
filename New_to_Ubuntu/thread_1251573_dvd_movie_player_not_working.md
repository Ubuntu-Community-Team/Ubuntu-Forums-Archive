---
title: "dvd movie player not working"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by ceece on 2009-08-27
I went to medibuntu, cut and paste the scripts to run as suggested.
Tons of printing...no errors.  seemed to run okay:)

zjust tried to run dvd and it says I need plug in. Search does not come up with a pug in.

any help or suggestions would be appreciated

I have another thread that has this problem included.

ubuntu is stressing me out,  time to hop on the treadmill for a run!!:(

---

### Post by SoftwareExplorer on 2009-08-27
You can download the packages from one of these direct links and then open it.
If you are on jaunty:
[32 bit]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb") (if you don't know, it's probably 32 bit)  [64bit]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb")

If you are on hardy
[32 bit]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb") (if you don't know, it's probably 32 bit)  [64bit]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb")

Open it and install it and it should solve your problem.

---

### Post by ceece on 2009-08-28
:KSThanks,
I tried what you said last night, but it still would not play the dvds. It says I need a plug in.
I went to the automatic installs that you can search for different programs to download, and now I am getting errors with that.
 
I wonder if all the script writing I cut and paste (as suggested to do in the other thread) might have messed that up.
 
Right now I can at least get online, email, surf the web and got the adobe flash to work!! I don't want to lose those functions in the process of fixing things.
 
I need my 
dvd player 
built in web cam
sound recorder 
to start working.
 
Good thing this netbook is not my main computer.  I will try redoing what you said.
 
But with all said and done, I still think ubuntu is pretty awesome. I'm just as green as you can get with the Linux OS.:P

---

### Post by MrWES on 2009-08-28
> **ceece said:**
> I went to medibuntu, cut and paste the scripts to run as suggested.
Tons of printing...no errors.  seemed to run okay:)

zjust tried to run dvd and it says I need plug in. Search does not come up with a pug in.

any help or suggestions would be appreciated

I have another thread that has this problem included.

ubuntu is stressing me out,  time to hop on the treadmill for a run!!:(


This should cover it;
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by coldReactive on 2009-08-28
> **ceece said:**
> Good thing this netbook is not my main computer.  I will try redoing what you said.

What model and manufacturer is your netbook?

---

### Post by fanglinyong on 2009-08-28
have you installed smplayer or mplayer ?maybe your problem will be solved!

---

### Post by Bartender on 2009-08-28
If you're not sure you did medibuntu right, you can go back and do it over.  Watch the text messages - it'll say whether it already has the latest versions of packages.

In other words, you can't hurt anything by trying again.

---

### Post by mapes12 on 2009-08-28
Go to Synaptic and install ubuntu-restricted-extras

That solved it for me together with the Medibuntu stuff..........

---

### Post by win_soft2005 on 2009-08-28
Not a great suggestion but do you tried VLC media player?

---

### Post by ceece on 2009-08-28
> **mapes12 said:**
> Go to Synaptic and install ubuntu-restricted-extras
 
That solved it for me together with the Medibuntu stuff..........
 
 Synaptic is coming up with errror now. It didn't before. Not sure what happened or why. I am going to play around with that tonight:confused:

---

### Post by ceece on 2009-08-28
> **Bartender said:**
> If you're not sure you did medibuntu right, you can go back and do it over. Watch the text messages - it'll say whether it already has the latest versions of packages.
 
In other words, you can't hurt anything by trying again.
 
 
I am going to try running it again to see what happens. :confused:

---

### Post by ceece on 2009-08-28
> **MrWES said:**
> This should cover it;
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
 
 
Thanks, I will check it out tonight  :P

---

### Post by ceece on 2009-08-28
> **coldReactive said:**
> What model and manufacturer is your netbook?
 
I have a Eee PC 900 ASUS with a built in web cam.

---

### Post by SunnyRabbiera on 2009-08-28
did you try libdvdcss?
Also make sure to install totem-xine and replace totem-gstreamer.
The difference is huge trust me.

---

### Post by zkriesse on 2009-08-28
To get the movies to work follow the instructions given here. [HelpUbuntu.com/Movies]("https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html")

---

### Post by SoftwareExplorer on 2009-08-29
Let me make sure I understand correctly:Your computer now gives you an error if you try to install anything. If so, could you paste the error here?

---

### Post by mapes12 on 2009-08-29
Terminal is another option ```
sudo apt-get install ubuntu-restricted-extras
```If Synaptic is throwing up errors that suggests problems with your system. But what they are I don't know.

---

### Post by RabbitWho on 2009-08-29
I'm having the same problem and I've already installed everything it told me to in the instructions. I've used the default movie player as well as vlc player. 

Also my web cam and mic aren't working, but i haven't started working on that problem yet.
I've a dell inspiron 1545

---

### Post by mapes12 on 2009-08-29
If this doesn't help then I give up:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by oboedad55 on 2009-08-29
> **mapes12 said:**
> If this doesn't help then I give up:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I have everything installed that has ever been suggested and I can get DVDs playing in VLC, but not in the movie player. So, I use VLC and there's nothing wrong with doing that. In movie player I get an error: "The folder contents could not be displayed; Operation not supported." If anyone can figure out what that means and effect a solution I'd like to hear.

--Jon

---

### Post by ceece on 2009-08-29
> **SoftwareExplorer said:**
> Let me make sure I understand correctly:Your computer now gives you an error if you try to install anything. If so, could you paste the error here?

when I go to synamtic package manager< it says "error" then:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by SoftwareExplorer on 2009-08-29
> **ceece said:**
> when I go to synamtic package manager< it says "error" then:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Ok, we can fix that. Go to Applications->Accessories-Terminal. Paste the following in and press enter:```
sudo dpkg --configure -a
```
That should fix the software installation problem.

---

### Post by ceece on 2009-09-01
> **SoftwareExplorer said:**
> Ok, we can fix that. Go to Applications->Accessories-Terminal. Paste the following in and press enter:```
sudo dpkg --configure -a
```That should fix the software installation problem.


Thanks, that worked 
ceece:KS

---

### Post by SoftwareExplorer on 2009-09-01
> **ceece said:**
> Thanks, that worked 
ceece:KS

Your welcome. :)  What happens if you try what I suggested in the second post of this thread?

---

### Post by ceece on 2009-09-02
> **SoftwareExplorer said:**
> Your welcome. :) What happens if you try what I suggested in the second post of this thread?
 
It ran quite a bit of script with no errors, but the dvd player still did not work with two different movies. I will try it again. 
Ceece

---

