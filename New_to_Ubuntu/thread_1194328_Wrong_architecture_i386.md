---
title: "Wrong architecture i386"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by squishy121888 on 2009-06-22
Hello, I have recently installed Ubuntu and have had the same error with everything I have tried to install. After I open the file, it gives me "Wrong architecture i386"

I've searched aa bit, and read it was related to 64-bit/ 32 bit stuff. I remember getting the 64 bit Ubuntu, and definitely recall that my PC is 64 bit, so what is the problem?

---

### Post by Therion on 2009-06-22
The problem is you're trying to install a 32-bit .deb on a 64-bit system.

What is it, exactly, that you're having trouble installing?

---

### Post by wil08son on 2009-06-22
The packages and programs you're downloading and trying to install are made for 32-bit systems. You can either downgrade to a 32-bit version of Linux, or head over to the 64-bit forum for help with some of your problems.

---

### Post by halitech on 2009-06-22
what are you trying to install and where did you get it from?

If you have the 64bit version then you need to install the 64 bit version of apps and it looks like you are trying to install the 32bit versions.

---

### Post by squishy121888 on 2009-06-22
Weird. Is there anyway to find the 64 bit versions of them? I never had the problem with my previous OS.

---

### Post by anystupidname on 2009-06-22
What is the output of these?
cat /proc/cpuinfo
lshw -C cpu
uname -a

Give us a couple examples of the packages you're trying to install.

---

### Post by squishy121888 on 2009-06-22
> **halitech said:**
> what are you trying to install and where did you get it from?

If you have the 64bit version then you need to install the 64 bit version of apps and it looks like you are trying to install the 32bit versions.


Avast! and Adobe flash [I got the flash player by using the terminal]

Sorry if I seem retarded, but I am not well studied on anything but Windows.

---

### Post by halitech on 2009-06-22
why not look in synaptic? easier and safer then downloading things from online and should work with no flaws as they have been tested to work.

---

### Post by squishy121888 on 2009-06-22
> **halitech said:**
> why not look in synaptic? easier and safer then downloading things from online and should work with no flaws as they have been tested to work.

lol, thanks. Now I know what you meant.

---

### Post by Therion on 2009-06-22
> **squishy121888 said:**
> Sorry if I seem retarded, but I am not well studied on anything but Windows.
No problem... But Ubuntu is not like Windows in many respects, as you're not doubt figuring out.

Best to stick with Add/Remove for now.  You're golden with Add/Remove.  Next up from there would be using Synaptic.  

No real need for Avast! in the Ubuntu environment...  Let it go.

---

### Post by squishy121888 on 2009-06-22
> **Therion said:**
> No problem... But Ubuntu is not like Windows in many respects, as you're not doubt figuring out.

Best to stick with Add/Remove for now.  You're golden with Add/Remove.  Next up from there would be using Synaptic.  

No real need for Avast! in the Ubuntu environment...  Let it go.

lol, sorry, but I don't feel safe using the internet without being armed to the teeth in security software.

In this synaptic thing, where can I find a program to remove cookies and other things? Basically, I am looking for analouges of AVG, Adaware, and Spybot.

---

### Post by LowSky on 2009-06-22
> **Therion said:**
> No real need for Avast! in the Ubuntu environment...  Let it go.
Trying to open a can of worms Therion? LOL.. in all seriousness, unless you run a windows based shairng network with your linux machine, you wont need antivirus. Linux cant be infected like Microsoft, and Linux has no viruses in the wild to worry about. Linux is so different from Windows its cant be infected the same way, just like Apple computers.

If you need flash for 64bit, you can download it form this link
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

instructions are here
[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install)

---

### Post by jmszr on 2009-06-22
squishy121888,

You are obviously concerned about security. This link will explain a lot to you: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) . When I first switched to Ubuntu I had a hard time realizing that I wasn't facing a lot of the issues that are inherent with Windows - but it's true.

---

### Post by Therion on 2009-06-22
> **squishy121888 said:**
> lol, sorry, but I don't feel safe using the internet without being armed to the teeth in security software.
We understand this...

> **squishy121888 said:**
> In this synaptic thing, where can I find a program to remove cookies and other things? Basically, I am looking for analouges of AVG, Adaware, and Spybot.
You won't be needing those here.  If you want/need to... uh... flush your cookies *cough* ... Firefox has options for that.

As for Ad-Aware, SpyBot etc.  No...  I know it's hard, but you won't be needing those anymore.  You've decided to install an OS that is inherently safer and more secure.  Defragmenting is something else you'll need to get over.  It's okay, we're here to help you...

> **LowSky said:**
> Trying to open a can of worms Therion? LOL.. 
And I've been trying *so hard* to be good lately...

<sigh>

---

### Post by squishy121888 on 2009-06-22
> **Therion said:**
> We understand this...


You won't be needing those here.  If you want/need to... uh... flush your cookies *cough* ... Firefox has options for that.

As for Ad-Aware, SpyBot etc.  No...  I know it's hard, but you won't be needing those anymore.  You've decided to install an OS that is inherently safer and more secure.  Defragmenting is something else you'll need to get over.  It's okay, we're here to help you...


And I've been trying *so hard* to be good lately...

<sigh>


lol. Okay, so for reassurance, I should be fine against Spyware? If not, how do I get something useful, or am I still, even at this point, thinking too much like a Windows user?


lol, I feel like a junkie forced onto methadone.



Er, as an aside, how do I get a better font than Sans, I prefer Times New Roman.


Also, what system maintnence do I need to run now that I needn't defrag?

---

### Post by LowSky on 2009-06-22
open add/remove

search for  msttcorefonts

if not open a terminal, applications>accessories>terminal type 

```
sudo apt-get install msttcorefonts 
```
type password (you wont see it, just hit enter when done, it will install)

then on the blank desktop, right-click and open of the options is for Fonts

dont worry about "system matenience"
Ubuntu takes care of it's self

---

### Post by squishy121888 on 2009-06-22
> **LowSky said:**
> open add/remove

search for  msttcorefonts

if not open a terminal, applications>accessories>terminal type 

```
sudo apt-get install msttcorefonts 
```type password (you wont see it, just hit enter when done, it will install)

then on the blank desktop, right-click and open of the options is for Fonts

dont worry about "system matenience"
Ubuntu takes care of it's self


Thanks. Where can I find lists of this add/remove stuff I understand? People seem to know all these things that I don't. Basically, where do I learn this stuff without trial and error?

---

### Post by Therion on 2009-06-22
> **squishy121888 said:**
> Thanks. Where can I find lists of this add/remove stuff I understand? People seem to know all these things that I don't. Basically, where do I learn this stuff without trial and error?
Well we seem to know this stuff because we started where you are now at some point and asked a lot of questions, did some reading and slowly gained experience.

There are some very basic differences in how Ubuntu does things vs how Windows does them and one of them is how you go about installing software.  Huge differences here.  

What might do you some good would be looking into some of the community documentation.  There's a lot of stuff online that will help get you up to speed.  

Here's a good starting point for you: [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by jmszr on 2009-06-22
squishy121888,

In addition to the above link I would suggest this sticky by umg6hr: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) . The links to Psychocats Ubuntu Guide and Free Ubuntu Pocket Guide by Keir Thomas are of particular note but the entire sticky is full of a lot of good information.

---

### Post by 73ckn797 on 2009-06-22
Last time I checked, Avast does not have a 64bit Linux version.

Most of the programs you will find in System/Administration/Synaptic Package Manager.

I recommend adding Medibuntu repositories for extra stuff: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Read the page a follow applicable instructions. I recommend the codecs and stuff for audio & video.

Also, go to System/Administration/Software Sources and make sure to check the universe, multiverse and restricted repositories if not checked off and under System/Administration/Software Sources/Third-Party Sources check off the choices there.

---

