---
title: "sound issue"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Sentoguy on 2010-03-27
Ok, so I've been trying to get my sound system to work (Ubuntu 9.10, Dell Zino HD) and have already updated Alsa using this tutorial and this tutorial:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

I got to the "pastbin" part, made an account and started to ask a question and I got what looks like a big red "-" sign up on the right of the tool bar (the synaptic manager) asking me to install sun-java6. Apparently I missed the "accept terms" box and now it won't let me install the package. Keeps telling me that it's broken, even after pasting the command prompt "sudo dpkg --configure -a" into into the terminal.

This is really getting to be a headache. Is there anyway that I can just go back, reboot the kernel from scratch and start over? Is that what the "recovery mode" option is at the start up?

Please help.

Thanks

---

### Post by NightwishFan on 2010-03-27
To fix packages, try:
```
sudo apt-get -f install
```

For sound, check volume using:
```
alsamixer -c0
```

---

### Post by Sentoguy on 2010-03-27
> **NightwishFan said:**
> To fix packages, try:
```
sudo apt-get -f install
```

For sound, check volume using:
```
alsamixer -c0
```

Ok, package fixed. Thanks.

Tried the second code and all volume levels seem to be maxed out (though there was a S/PDIF and S/PDIF DEF in the middle which didn't seem to have volume levels).

I've seen lots of other tutorial threads where people are having trouble with Karmic Koala's sound. But don't really know which one to follow and don't know enough to feel comfortable just shooting arrows into the dark if you know what I mean.

For reference, I'm using a Dell Inspiron Zino HD if that helps.

Thanks again.

---

### Post by Sentoguy on 2010-03-27
When I enter the command prompt "sudo lshw -C multimedia" I get:
*-multimedia            
       description: Audio device
       product: RS780 Azalia controller
       vendor: ATI Technologies Inc
       physical id: 5.1
       bus info: pci@0000:01:05.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:26 memory:feae8000-feaebfff
  *-multimedia
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:fe8f4000-fe8f7fff

If that helps

---

### Post by NightwishFan on 2010-03-27
I will try to get back to you if I find anything. Someone else can help you in the meantime. Good luck, when I am back I will remember to report.

---

### Post by Chris Edgell on 2010-03-29
I see you got your distro on your name tag.  LOL

I must say the same thing happened to me with Karmic and I just reinstalled.  Then I went to update manager before I opened the synaptic.  In the process, that lock went away and it all worked.  A couple of times it said I didn't need an update but I clicked around a little bit and went back --that time it began giving me 250 updates.

AFTER receiving the updates I went and installed XUbuntu (FOR YOU Ubuntu) Restricted extras.  It wasn't straightforward finding then...I had to click around; it wasn't listed alphabetically under ALL.  I left it in the search window while I clicked everywhere till it popped up.  Communication, multimedia, network...can't remember where I found it; multiverse, universe, ... you WILL see it pop up.  Then type in: Flashplugin, it may show up as "Adobe-Flashplugin".  

It seems like after I installed those two packages, I got sound.  If not, see if you find java-common; see if it is installed if not, it can't hurt to install it.

We'll be waiting to hear... (no pun intended). LOL

Chris

---

### Post by Sentoguy on 2010-03-29
> **Chris Edgell said:**
> I see you got your distro on your name tag.  LOL

I must say the same thing happened to me with Karmic and I just reinstalled.  Then I went to update manager before I opened the synaptic.  In the process, that lock went away and it all worked.  A couple of times it said I didn't need an update but I clicked around a little bit and went back --that time it began giving me 250 updates.

AFTER receiving the updates I went and installed XUbuntu (FOR YOU Ubuntu) Restricted extras.  It wasn't straightforward finding then...I had to click around; it wasn't listed alphabetically under ALL.  I left it in the search window while I clicked everywhere till it popped up.  Communication, multimedia, network...can't remember where I found it; multiverse, universe, ... you WILL see it pop up.  Then type in: Flashplugin, it may show up as "Adobe-Flashplugin".  

It seems like after I installed those two packages, I got sound.  If not, see if you find java-common; see if it is installed if not, it can't hurt to install it.

We'll be waiting to hear... (no pun intended). LOL

Chris

Thanks Chris.

When I first installed Ubuntu I did have around 250 updates that I installed, so maybe I just need to install the restricted extras.

When you say that "you left it in the search window while you clicked everywhere till it popped up", what do you mean by "it". And where are these folders "communication, multimedia, network, etc..." that you were looking through?

Sorry, as you can tell I'm a complete newb when it comes to this stuff.

Thanks again.

---

### Post by Chris Edgell on 2010-03-29
Happy you've come this far with following my thought pattern.. now I will try to be more explicit in my details.

Get to synaptic, in the top search box type "Ubuntu-restricted-extras" (I have 4 computers here and often with the same procedures they work a little differently).  

In this case, this computer with sound was set up by my mentor, and I see here that he installed Ubuntu extras v Xubuntu...and it works anyway...

On another computer I typed the words of what I was looking for -- and then there on the left you see on top ALL.  One would think that it would show all BUT sometimes you have to leave what you are looking for in that search box and go clicking around, in a rather organized fashion...going down each item on that list on the left and seeing if what you've got in the search box pops up in the applications box.

I've gone so far as to then having to move to the "filters" at the bottom half of the left side and go through them till I find the package or application that I'm looking for.

I'm going to go through my very long and disorganized thread, "I think I ruined my hard drive--and even more"  I'm quite sure someone told me the easy way to get to these extras...(although the easiest way would have been to have them listed under ALL, don't you think??!!  Although it may limit the humoungousness of the task by sometimes dividing the packages by filters)

It won't hurt for you to do a lot of clicking around there because you'll see a lot of interesting pieces and ways of structuring in this Linux/Ubuntu "world".

Lots of people recommend a really more straightforward method of get(ing)-app(lications) but I was so comfortable in the synaptic method because I could see so clearly what I was doing.  After awhile I may learn more about "Command line" in the terminal, (I think there's an acronym for that), but for now I stay with the slower and more visual method.

I'm cheering for you...I'm going to post 4 screenshots of how the synaptic looks on my machine.  Notice how in the first one, down at the bottom, that the adjustable factor is "Custom Filters"; in the second it is the first option in that bottom left section called, "Sections" -- think about that approach: Sections, Status, Origin, etc.  You'll begin to see how it works.

Watch how the bottom left choices change your options etc.

Bye for now
Chris

---

### Post by lidex on 2010-03-29
To help you, we'll need more information. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by Chris Edgell on 2010-03-30
> **Sentoguy said:**
> 

 maybe I just need to install the restricted extras.



I wouldn't have continued to try to solve this sound problem if Sentoguy had not said this.  But since he did, I HAVE tried to explain how to install these extras.  If anyone can state it more definitely, clearly, concisely...Please do so.  I know my way of explaining is not concise; it'll get you there Sentoguy, but the route could be more precise.

So anyone, jump in...no one will appreciate it more than me...well, except maybe sentoguy.  LOL

Best wishes
Chris

---

### Post by Sentoguy on 2010-03-30
> **Chris Edgell said:**
> I wouldn't have continued to try to solve this sound problem if Sentoguy had not said this.  But since he did, I HAVE tried to explain how to install these extras.  If anyone can state it more definitely, clearly, concisely...Please do so.  I know my way of explaining is not concise; it'll get you there Sentoguy, but the route could be more precise.

So anyone, jump in...no one will appreciate it more than me...well, except maybe sentoguy.  LOL

Best wishes
Chris

Hi Chris,

Ok, so I went into synaptic like you suggested and typed in "ubuntu-restricted-extras" and under All it listed 36 packages (the box was marked green, which I took to mean meant I had already installed it). How many restricted extras packages should there be?

I also searched for "flashplugin" and "adobe-flashplugin" was also maked installed. So I think that's already installed.

---

### Post by Sentoguy on 2010-03-30
> **lidex said:**
> To help you, we'll need more information. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

Hi Lidex,

It says "no such file or directory".

What now?

---

### Post by lidex on 2010-03-30
Make sure you downloaded the script to your home folder, ie /home/your-user-name/utils_alsa-info.sh The error msg means it's not there. Alternately, if you know the location of the script you can move to that directory using terminal cd command. 
Example:
```
cd ~/Downloads
```

puts you in the Downloads directory.

---

### Post by Chris Edgell on 2010-03-31
Hi Sentoguy,....

I looked at your profile and see that your last activity was 21 hours ago, so you may be checking in sometime soon.

I see that the ubuntu extras were already installed, as was the flash-plugin.  Most, or I should say, many of these are packages and the one you click on includes the rest of the package when you install it.  

When you "select" the line of the one you're considering, you see down in the bottom area that it describes what it is about.  When you click the "Install" button, it just show you what comes with it.  Even when you click "Apply" it gives you a window describing and listing all the additional apps, etc, that come with it -- the package.  It says, "This is your last chance before applying the changes", or words to that effect.  You may have noticed all this already.

Did you go to java-common?  It may show you sumjava-common, but the key words are "java-common".  Is that installed?  With my Karmic install, when I had these main things: extras, adobe, and java...then I got sound.

Did you have sound before you downloaded Karmic"  I muyself had been through the wringer trying to get any sound from my AMD; but I GOT sound before I downloaded the Karmic.  In case you're interested: my thread on the subject is very step-by-step...although in the end I needed a sound card.

[http://ubuntuforums.org/showthread.php?t=1404762&page=9](http://ubuntuforums.org/showthread.php?t=1404762&page=9)

That's why I ask: did you have sound before you downloaded Karmic?

But, as I said, I knew  by then that the sound would work; so it was just a matter of getting it to work in Karmic.  Again, as I said, with the first install I got the message there are no updates so I went on to synaptic.  (I should have known there would be updates...) Then when I tried to run the synaptic additions, I got the message like you described, a red warning and and error message something about something else already running and now something was locked up.  

At that point, I decided to simply Reinstall, to make sure I got the updates before opening synaptic (if only by waiting and checking again about updates, going back to the Update Manager area, etc) Then after those updates, then and only then to go to synaptic.  I installed the 3 main packages I've talked about and then I had sound!

I say all this because I plan to be out for quite a few hours -- they are jack-hammering 10 feet from me... LOL  (I say LOL but I am not laughing.)

I hope next time I hear from you, I will hear that you have sound.

Best wishes
Chris

---

### Post by Sentoguy on 2010-03-31
> **Chris Edgell said:**
> Hi Sentoguy,....

I looked at your profile and see that your last activity was 21 hours ago, so you may be checking in sometime soon.

I see that the ubuntu extras were already installed, as was the flash-plugin.  Most, or I should say, many of these are packages and the one you click on includes the rest of the package when you install it.  

When you "select" the line of the one you're considering, you see down in the bottom area that it describes what it is about.  When you click the "Install" button, it just show you what comes with it.  Even when you click "Apply" it gives you a window describing and listing all the additional apps, etc, that come with it -- the package.  It says, "This is your last chance before applying the changes", or words to that effect.  You may have noticed all this already.

Did you go to java-common?  It may show you sumjava-common, but the key words are "java-common".  Is that installed?  With my Karmic install, when I had these main things: extras, adobe, and java...then I got sound.

Did you have sound before you downloaded Karmic"  I muyself had been through the wringer trying to get any sound from my AMD; but I GOT sound before I downloaded the Karmic.  In case you're interested: my thread on the subject is very step-by-step...although in the end I needed a sound card.

[http://ubuntuforums.org/showthread.php?t=1404762&page=9](http://ubuntuforums.org/showthread.php?t=1404762&page=9)

That's why I ask: did you have sound before you downloaded Karmic?

But, as I said, I knew  by then that the sound would work; so it was just a matter of getting it to work in Karmic.  Again, as I said, with the first install I got the message there are no updates so I went on to synaptic.  (I should have known there would be updates...) Then when I tried to run the synaptic additions, I got the message like you described, a red warning and and error message something about something else already running and now something was locked up.  

At that point, I decided to simply Reinstall, to make sure I got the updates before opening synaptic (if only by waiting and checking again about updates, going back to the Update Manager area, etc) Then after those updates, then and only then to go to synaptic.  I installed the 3 main packages I've talked about and then I had sound!

I say all this because I plan to be out for quite a few hours -- they are jack-hammering 10 feet from me... LOL  (I say LOL but I am not laughing.)

I hope next time I hear from you, I will hear that you have sound.

Best wishes
Chris

Hi Chris,

As far as I know i've already got java as well.

The computer is basically brand new (it came with Windows 7 already installed, which does get sound) and I burned Karmic off the Ubuntu site onto a CD, then installed it onto my hard drive. I suppose that something could have gotten screwed up with the downloading of the Karmic kernel, but don't really know how I would check for that.

Thanks for the help. Maybe I'll try running Karmic off the disc and see if I get sound then, and if not, then maybe something went wrong with the original Karmic kernel download.

---

### Post by Sentoguy on 2010-03-31
> **lidex said:**
> Make sure you downloaded the script to your home folder, ie /home/your-user-name/utils_alsa-info.sh The error msg means it's not there. Alternately, if you know the location of the script you can move to that directory using terminal cd command. 
Example:
```
cd ~/Downloads
```

puts you in the Downloads directory.

Ummmm, not to sound annoying but I don't really understand what you're talking about. I'm totally, utterly new at this stuff and terms like "script" aren't yet part of my vocabulary.

How would I download a script to my home folder? Would I type that exact sequence "/home/my-user-name/utils_alsa-info.sh" into the terminal?

---

### Post by Chris Edgell on 2010-03-31
Go into synaptic and find "hardinfo", install.

Then press F2 and you'll see the run box.  Type "hardinfo" into that box and enter or "run".

You'll see so much info including kernels.

---

### Post by Sentoguy on 2010-04-01
> **Chris Edgell said:**
> Go into synaptic and find "hardinfo", install.

Then press F2 and you'll see the run box.  Type "hardinfo" into that box and enter or "run".

You'll see so much info including kernels.

Hi Chris,

Ok, so I went into synaptic and I installed "hardinfo". But pressing F2 doesn't bring up a run box. Is there another way that I can access the run box? Is there a command that I can type into the terminal to get it to run?

Thanks again for the help.

BTW, I tried running off the live CD on my mother's laptop and I got sound fine. But, when I tried running the live CD on my computer, no sound. Could it just be that my soundcard/speakers are too new and not yet recognized by Ubuntu?

---

### Post by NightwishFan on 2010-04-01
alt+f2 ;)

For your sound card, perhaps. It could be any number of issues though. Open a terminal and run this command, what is the output?
```
speaker-test
```

---

### Post by Sentoguy on 2010-04-01
> **NightwishFan said:**
> alt+f2 ;)

For your sound card, perhaps. It could be any number of issues though. Open a terminal and run this command, what is the output?
```
speaker-test
```

speaker-test 1.0.22

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 8192
Period size range from 1024 to 1024
Using max buffer size 8192
Periods = 4
was set period_size = 1024
was set buffer_size = 8192
 0 - Front Left
Time per period = 2.835288
 0 - Front Left
Time per period = 2.986623
 0 - Front Left
Time per period = 2.986634
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986642
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986633
 0 - Front Left
Time per period = 2.986645
 0 - Front Left
Time per period = 2.986632
 0 - Front Left
Time per period = 2.986615
 0 - Front Left
Time per period = 2.986640
 0 - Front Left
Time per period = 2.986625
 0 - Front Left
Time per period = 2.986634
 0 - Front Left
Time per period = 2.986643
 0 - Front Left
Time per period = 2.986626
 0 - Front Left
Time per period = 2.986632
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986634
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986639
 0 - Front Left
Time per period = 2.986629
 0 - Front Left
Time per period = 2.986625
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986684
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986580
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986636
 0 - Front Left
Time per period = 2.986619
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986645
 0 - Front Left
Time per period = 2.986624
 0 - Front Left
Time per period = 2.986634
 0 - Front Left
Time per period = 2.986649
 0 - Front Left
Time per period = 2.986619
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986642
 0 - Front Left
Time per period = 2.986631
 0 - Front Left
Time per period = 2.986629
 0 - Front Left
Time per period = 2.986647
 0 - Front Left
Time per period = 2.986619
 0 - Front Left
Time per period = 2.986641
 0 - Front Left
Time per period = 2.986643
 0 - Front Left
Time per period = 2.986628
 0 - Front Left
Time per period = 2.986629
 0 - Front Left
Time per period = 2.986653
 0 - Front Left
Time per period = 2.986615
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986633
 0 - Front Left
Time per period = 2.986639
 0 - Front Left
Time per period = 2.986636
 0 - Front Left
Time per period = 2.986631
 0 - Front Left
Time per period = 2.986638
 0 - Front Left
Time per period = 2.986640
 0 - Front Left
Time per period = 2.986627
 0 - Front Left
Time per period = 2.986627
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986634
 0 - Front Left
Time per period = 2.986636
 0 - Front Left
Time per period = 2.986638
 0 - Front Left
Time per period = 2.986643
 0 - Front Left
Time per period = 2.986677
 0 - Front Left
Time per period = 2.986582
 0 - Front Left
Time per period = 2.986633
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986643
 0 - Front Left
Time per period = 2.986621
 0 - Front Left
Time per period = 2.986631
 0 - Front Left
Time per period = 2.986629
 0 - Front Left
Time per period = 2.986636
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986636
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986636
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986633
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986639
 0 - Front Left
Time per period = 2.986631
 0 - Front Left
Time per period = 2.986639
 0 - Front Left
Time per period = 2.986632
 0 - Front Left
Time per period = 2.986632
 0 - Front Left
Time per period = 2.986632
 0 - Front Left
Time per period = 2.986641
 0 - Front Left
Time per period = 2.986644
 0 - Front Left
Time per period = 2.986629
 0 - Front Left
Time per period = 2.986622
 0 - Front Left
Time per period = 2.986640
 0 - Front Left
Time per period = 2.986631
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986650
 0 - Front Left
Time per period = 2.986623
 0 - Front Left
Time per period = 2.986611
 0 - Front Left
Time per period = 2.986633
 0 - Front Left
Time per period = 2.986638
 0 - Front Left
Time per period = 2.986630
 0 - Front Left
Time per period = 2.986656
 0 - Front Left
Time per period = 2.986612
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986641
 0 - Front Left
Time per period = 2.986679
 0 - Front Left
Time per period = 2.986580
 0 - Front Left
Time per period = 2.986630
 0 - Front Left
Time per period = 2.986636
 0 - Front Left
Time per period = 2.986636
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986629
 0 - Front Left
Time per period = 2.986636
 0 - Front Left
Time per period = 2.986651
 0 - Front Left
Time per period = 2.986621
 0 - Front Left
Time per period = 2.986632
 0 - Front Left
Time per period = 2.986641
 0 - Front Left
Time per period = 2.986630
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986642
 0 - Front Left
Time per period = 2.986626
 0 - Front Left
Time per period = 2.986633
 0 - Front Left
Time per period = 2.986820
 0 - Front Left
Time per period = 2.986508
 0 - Front Left
Time per period = 2.986582
 0 - Front Left
Time per period = 2.986631
 0 - Front Left
Time per period = 2.986651
 0 - Front Left
Time per period = 2.986606
 0 - Front Left
Time per period = 2.986647
 0 - Front Left
Time per period = 2.986618
 0 - Front Left
Time per period = 2.986636
 0 - Front Left
Time per period = 2.986634
 0 - Front Left
Time per period = 2.986695
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986573
 0 - Front Left
Time per period = 2.986651
 0 - Front Left
Time per period = 2.986633
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986674
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986636
 0 - Front Left
Time per period = 2.986573
 0 - Front Left
Time per period = 2.986637
 0 - Front Left
Time per period = 2.986693
 0 - Front Left
Time per period = 2.986632
 0 - Front Left
Time per period = 2.986570
 0 - Front Left
Time per period = 2.986643
 0 - Front Left
Time per period = 2.986693
 0 - Front Left
Time per period = 2.986630
 0 - Front Left
Time per period = 2.987360
 0 - Front Left
Time per period = 2.985898
 0 - Front Left
Time per period = 2.971696
 0 - Front Left
Time per period = 3.001880
 0 - Front Left
Time per period = 2.986330
 0 - Front Left
Time per period = 2.986567
 0 - Front Left
Time per period = 2.986635
 0 - Front Left
Time per period = 2.986696
 0 - Front Left
Time per period = 2.986579
 0 - Front Left
Time per period = 2.986646
 0 - Front Left

...and so on....

What do you think this means?

---

### Post by NightwishFan on 2010-04-01
It means that the card is not locked and sound is playing. Forgive me, you did not have to run it that long it loops forever. If you did not previously double check the volume.
```
alsamixer -c0
```

Also check to see if another device such as headphones works.

---

### Post by Chris Edgell on 2010-04-01
[Glad to see you here again, NightwishFan -- thanks for the Alt + F2  I went and put it in the edit just so it would be correct there also.]  

Guy, I want to go into something else, ...although, DID you go to my thread Post #150 and see about the:

System>Preferences>Sound>hardware   etc 

Have you looked there?  Go there: Sometimes it sticks and you can't open the hardware tab but close it and go back till that tab clicks open.  Then turn on Youtube, something that makes sound and see if you hear anything with any of the choices available on that drop down menu. It took me a while to realize that what YOU "select" in that drop down menus IS what shows up as the configuration for the sound card or whatever device you have showing as the hardware in the upper part of the window ...so what you are really trying to do here is trying all the various configurations on that menu to see if one works for the hardware you have installed that is showing there above.

I'll put screenshots of how mine looks.  But I don't imagine your configuration would be just like mine...although it could be.  I spent quite a bit of time going back and forth with this "tab" and the Input and Output tabs.  (Checking the mute, trying one thing, then going back and forth to the config of the hardware) ...but eventually ... I GOT SOUND...  I hope you will to.

Bye for now

---

### Post by Sentoguy on 2010-04-02
> **NightwishFan said:**
> It means that the card is not locked and sound is playing. Forgive me, you did not have to run it that long it loops forever. If you did not previously double check the volume.
```
alsamixer -c0
```

Also check to see if another device such as headphones works.

Haha, yeah I figured that might be the case after it basically just kept going for like 10 minutes and didn't seem to be showing anything different.

Yeah, I already checked 
alsamixer -cO

and the volumes are all up.

---

### Post by Sentoguy on 2010-04-02
> **Chris Edgell said:**
> [Glad to see you here again, NightwishFan -- thanks for the Alt + F2  I went and put it in the edit just so it would be correct there also.]  

Guy, I want to go into something else, ...although, DID you go to my thread Post #150 and see about the:

System>Preferences>Sound>hardware   etc 

Have you looked there?  Go there: Sometimes it sticks and you can't open the hardware tab but close it and go back till that tab clicks open.  Then turn on Youtube, something that makes sound and see if you hear anything with any of the choices available on that drop down menu. It took me a while to realize that what YOU "select" in that drop down menus IS what shows up as the configuration for the sound card or whatever device you have showing as the hardware in the upper part of the window ...so what you are really trying to do here is trying all the various configurations on that menu to see if one works for the hardware you have installed that is showing there above.

I'll put screenshots of how mine looks.  But I don't imagine your configuration would be just like mine...although it could be.  I spent quite a bit of time going back and forth with this "tab" and the Input and Output tabs.  (Checking the mute, trying one thing, then going back and forth to the config of the hardware) ...but eventually ... I GOT SOUND...  I hope you will to.

Bye for now

Thanks again Chris.

I'll give that a try and report back how it goes.

---

### Post by Sentoguy on 2010-04-02
Hi Chris.

Ok so I went into preferences>sound>hardware>etc and tried all of the different options (of which there weren't many to choose from), made sure that the volume was up on everything, and still no sound. 

I'm really starting to think that it might be a compatibility issue and I'll have to wait until Ubuntu's drivers catch up and become compatible with my sound card/speakers to get sound.

---

### Post by NightwishFan on 2010-04-02
Check this before you give up:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Sentoguy on 2010-04-02
> **NightwishFan said:**
> Check this before you give up:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

From what I can tell, my soundcard isn't supported by ALSA. So, looks like I'll have to contact them, or wait until they come out with new drivers that do support it.

---

### Post by NightwishFan on 2010-04-02
I am sorry if that is the only solution. Perhaps file a bug on launchpad and ask them to seek support for it.

---

### Post by Chris Edgell on 2010-04-02
You know how to take a screenshot?  (Pressing the Print Screen/Sys rq button there on your keyboard up over the cursor keys)  Do you know how to add a screenshot to your post?

Take the screenshot; wait for screenshot window; type in title if you like, as reference; press save.

Make your post; beneath this box press go advanced; scroll on down and click "manage attachments"; then you get an attachments window (see screenshot LOL)  at the top hit "Browse"; this takes you to files -- like I go there and see "Desktop", I click "open" and I see lists of files, etc, if you scroll down you see a file that is whatever you named your screenshot.pgn (see screenshot--see I didn't name it).. Click open and it takes you back to the original attachment window where you had clicked browse, there just to the right you click "Upload" and when the bottom left corner says done...you close that window and discover that where it says "Manage attachments" you see the little icon for your screenshot.  If you click "Preview Post" it shows you what your post is looking like with that screenshot.  You can do this up to five times...you can go back and remove there too, just look for remove button.

I would like to see the screenshot of your hardware page, also the input and output.  Will you do that for me?  I myself tried to get a shot of the list that is offered as ways to configure, but for some reason it would not take one.

If you knew all this "how-to" forgive me, I wrote it all for the person who might not know...and wonders.

Bye for now
Chris

---

### Post by lidex on 2010-04-02
Do this for me. 
Go to "System>Administration>Software Sources". On the updates tab, place a check in the box for "Unsupported Updates (Backports). Close that out. Open a terminal: "Applications>Accessories>Terminal"
Enter these commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-backports-modules-alsa-karmic-generic
sudo update-grub

```
One line at a time. Enter user password when prompted.
Now reboot. Check alsamixer settings as before. Still no sound?
Run this command and post output:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by NightwishFan on 2010-04-02
Wow lidex you seem like the 'sound man' around here. ;) I did not know about the alsa backports even though I used the wireless ones a lot. I will take a look at some of your links and get acquainted with some sound solutions to spread around.

---

### Post by DantePasquale on 2010-04-12
Hi All,

Seems I have a similar problem, but not totally similar. 

I have sound working with 9.10 AMD 64 with Amarok, but not via PulseAudio! It's using alsa (I think).

When I run PA Manager the default sink is <auto_null> and the default source is auto_null. When playing anything with audio, the sliders look fine and the application registers fine, but there's no sound.

alsamixer settings are fine.

Do I need to define a real sink instead of auto_null???

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by lidex on 2010-04-12
> **DantePasquale said:**
> Hi All,

Seems I have a similar problem, but not totally similar. 

I have sound working with 9.10 AMD 64 with Amarok, but not via PulseAudio! It's using alsa (I think).

When I run PA Manager the default sink is <auto_null> and the default source is auto_null. When playing anything with audio, the sliders look fine and the application registers fine, but there's no sound.

alsamixer settings are fine.

Do I need to define a real sink instead of auto_null???

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Try this:
[http://georgia.ubuntuforums.org/showpost.php?p=5918935&postcount=199]("http://georgia.ubuntuforums.org/showpost.php?p=5918935&postcount=199")

Also, what is the output of this command;
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by stevek123 on 2010-04-12
Maybe I'm just butting in ... but ... I just did an ubuntu install for the first time alone (I've been running Gutsy->Hardy for 2 yrs) and went to install Karmic on an amd64 from asus/nvidia. It took me a long time and some frustration to find/figure out that my onboard sound wont work and that a bug for it has been issued. I ended up getting sound by installing an old ESS card that alsa still supports and re-installing Karmic (Newest alsa STOPPED supporting my old Yamaha ymf724 card too!). 

On my old machine/Hardy I have to reconfigure my sound module and driver for the yamaha soundcard with every kernel update (GGRRRRR!) I found the best way was using the Comprehensive Sound Problem Guide here. 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Good step-by-step instructions and the worst that happens is nothing but wasted time (and some frustration). Good luck.

---

### Post by DantePasquale on 2010-04-12
Hi Lidex,

Good ideas. I updated /etc/pulse/default.pa with no better result.

lsof of those files show none in use!

Do you know if you need to reboot after editing /etc/pulse/default.pa if it's configured as 'per user session'? I didn't reboot because, well, I hate to reboot :)

---

### Post by lidex on 2010-04-12
> **DantePasquale said:**
> Hi Lidex,

Good ideas. I updated /etc/pulse/default.pa with no better result.

lsof of those files show none in use!

Do you know if you need to reboot after editing /etc/pulse/default.pa if it's configured as 'per user session'? I didn't reboot because, well, I hate to reboot :)
I would think so. Or try this:
```
killall pulseaudio
```

---

### Post by DantePasquale on 2010-04-12
Thanks, the suggestions did help, but still no sound out of pulse audio, but I do get sound from alsa (via amarok). The pavolume thingy does change the volume and does route the sound to the stereo analog output or the stereo headphone output.

However, now I don't see npviewer as an application on the tab for the volume control!

Not sure what info would help for debugging. Any suggestions?

Here's fuser now:

```
                    USER        PID ACCESS COMMAND
/dev/snd/controlC0:  gdm        2327 F.... pulseaudio
                     dante      6400 F.... amarok
                     dante      6428 F.... python
/dev/snd/pcmC0D0p:   dante      6400 F...m amarok
/dev/snd/timer:      dante      6400 f.... amarok
```

```
ps aux | grep pulse
gdm       2327  0.3  0.4 211428  9604 ?        Ssl  19:02   0:21 /usr/bin/pulseaudio --start --log-target=syslog
gdm       2366  0.0  0.1  94308  2644 ?        S    19:02   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
dante     5453  0.0  0.0  36060   704 ?        Ss   19:17   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute gnome-session
dante     5456  0.0  0.0  26156   784 ?        S    19:17   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute gnome-session
```

here's /etc/asound.conf

```
cat /etc/asound.conf 
pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}
```

/etc/pulse/default.pa is as installed (no mods to it).

pactl --list (output edited)

```
Sink #0
	State: SUSPENDED
	Name: alsa_output.pci-0000_00_06.1.analog-stereo
	Description: Internal Audio Analog Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 4
	Mute: no
	Volume: 0:  48% 1:  48%
	        0: -19.15 dB 1: -19.15 dB
	        balance 0.00
	Base Volume: 100%
	             0.00 dB
	Monitor Source: alsa_output.pci-0000_00_06.1.analog-stereo.monitor
	Latency: 0 usec, configured 0 usec
	Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
	Properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC262 Analog"
		alsa.id = "ALC262 Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xfbef0000 irq 31"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:06.1"
		sysfs.path = "/devices/pci0000:00/0000:00:06.1/sound/card0"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "nVidia Corporation"
		device.product.id = "0371"
		device.product.name = "MCP55 High Definition Audio"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Internal Audio Analog Stereo"
		alsa.mixer_name = "Realtek ALC262"
		alsa.components = "HDA:10ec0262,10f1c303,00100100"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	Ports:
		analog-output: Analog Output (priority. 10000)
		analog-output-headphones: Analog Headphones (priority. 9000)
	Active Port: analog-output

Source #0
	State: SUSPENDED
	Name: alsa_output.pci-0000_00_06.1.analog-stereo.monitor
	Description: Monitor of Internal Audio Analog Stereo
	Driver: module-alsa-card.c
	Sample Specification: s16le 2ch 44100Hz
	Channel Map: front-left,front-right
	Owner Module: 4
	Mute: no
	Volume: 0:  74% 1:  74%
	        0: -7.85 dB 1: -7.85 dB
	        balance 0.00
	Base Volume: 100%
	             0.00 dB
	Monitor of Sink: alsa_output.pci-0000_00_06.1.analog-stereo
	Latency: 0 usec, configured 0 usec
	Flags: DECIBEL_VOLUME LATENCY 
	Properties:
		device.description = "Monitor of Internal Audio Analog Stereo"
		device.class = "monitor"
		alsa.card = "0"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xfbef0000 irq 31"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:06.1"
		sysfs.path = "/devices/pci0000:00/0000:00:06.1/sound/card0"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "nVidia Corporation"
		device.product.id = "0371"
		device.product.name = "MCP55 High Definition Audio"
		device.form_factor = "internal"
		device.string = "0"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
```

One thing I see is that alsamixer -c0 shows the front at 0 and won't let me change it. Maybe that's the problem, but how to fix it ...

Attached jpg screenshot of alsamixer outoupt

---

### Post by lidex on 2010-04-13
Do this for me. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by DantePasquale on 2010-04-14
Hey, Thanks to everyone and everyone's suggestions -- sound is back working again!

Key thing for me was to go into synaptic, then search for 'pulseaudio' and select every already installed packages and set them for "Re-installation"! And let it do its thing!!! Didn't even need a reboot!!

---

### Post by pcarcel on 2010-04-21
I am having a problem updating the alsa driver to 1.0.23.  I upgraded alsa using this info:
 
[http://monespaceperso.org/blog-en/2010/04/17/upgrade-alsa-1-0-23-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2010/04/17/upgrade-alsa-1-0-23-on-ubuntu-karmic-koala-9-10/)

and then using lidex's script i got this output: 

```
!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      Gateway         
Product Name:      NV79            


!!Kernel Information
!!------------------

Kernel release:    2.6.31-21-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.22.1
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd4400000 irq 33


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 05)
    Subsystem: 1025:031c


!!Modprobe options (Sound related)
!!--------------------------------

snd-hda-intel: model=3stack
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: model=auto


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 1,1,1,1,1,1,1,1
    enable : Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1
    model : auto,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    patch : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    position_fix : 0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
    probe_only : N,N,N,N,N,N,N,N
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC272
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0272
Subsystem Id: 0x1025031d
Revision Id: 0x100001
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC272 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC272 Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x9f 0x9f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC272 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x1f 0x1f] [0x1f 0x1f] [0x80 0x80] [0x80 0x80] [0x1f 0x1f] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 8
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x80]
  Connection: 2
     0x02 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400700: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x0:
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x0:
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40050c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x03 0x03]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x03a19840: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x03 0x03]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x99a30930: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 3
     0x0c* 0x0d 0x0e
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 3
     0x0c* 0x0d 0x0e
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4006892d: [N/A] Line Out at Ext N/A
    Conn = Digital, Color = Purple
    DefAssociation = 0x2, Sequence = 0xd
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400780: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x03451120: [Jack] SPDIF Out at Ext Left
    Conn = Optical, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
  Processing Coefficient: 0x00
  Coefficient Index: 0x07
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0321101f: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 3
     0x0c 0x0d* 0x0e
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16 0x0b 0x13
Codec: Conexant ID 2c06
Address: 1
Function Id: 0x2
Vendor Id: 0x14f12c06
Subsystem Id: 0x1025031c
Revision Id: 0x100000
Modem Function Group: 0x2
Codec: Intel G45 DEVIBX
Address: 3
Function Id: 0x1
Vendor Id: 0x80862804
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Device: name="INTEL HDMI 0", type="HDMI", device=3
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Device: name="INTEL HDMI 1", type="HDMI", device=7
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3
  Power: setting=D0, actual=D0
Node 0x04 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x02* 0x03
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560020: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x02* 0x03
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560030: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=06, enabled=1
  Power states:  D0 D3
  Power: setting=D0, actual=D0
  Connection: 2
     0x02* 0x03
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  0 Apr 21 06:12 /dev/snd/controlC0
crw-rw----  1 root audio 116,  4 Apr 21 06:12 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  5 Apr 21 06:12 /dev/snd/hwC0D1
crw-rw----  1 root audio 116,  7 Apr 21 06:12 /dev/snd/hwC0D3
crw-rw----  1 root audio 116, 24 Apr 21 06:12 /dev/snd/pcmC0D0c
crw-rw----  1 root audio 116, 16 Apr 21 06:21 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116, 17 Apr 21 06:12 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116, 19 Apr 21 06:12 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116, 23 Apr 21 06:12 /dev/snd/pcmC0D7p
crw-rw----  1 root audio 116,  1 Apr 21 06:12 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Apr 21 06:12 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Apr 21 06:12 .
drwxr-xr-x 3 root root 280 Apr 21 06:12 ..
lrwxrwxrwx 1 root root  12 Apr 21 06:12 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xd4400000 irq 33'
  Mixer name    : 'Intel G45 DEVIBX'
  Components    : 'HDA:10ec0272,1025031d,00100001 HDA:14f12c06,1025031c,00100000 HDA:80862804,80860101,00100000'
  Controls      : 35
  Simple ctrls  : 18
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [off]
  Front Right: Capture 31 [100%] [30.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Front Mic'


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 64'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 64
        value.1 64
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 true
        value.1 true
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 64'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 64
        value.1 64
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value.0 31
        value.1 31
    }
    control.6 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Mic Playback Switch'
        value.0 true
        value.1 true
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Front Mic Playback Volume'
        value.0 31
        value.1 31
    }
    control.8 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Front Mic Playback Switch'
        value.0 true
        value.1 true
    }
    control.9 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3000
        iface MIXER
        name 'Mic Boost'
        value.0 3
        value.1 3
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3000
        iface MIXER
        name 'Front Mic Boost'
        value.0 3
        value.1 3
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 true
        value.1 true
    }
    control.12 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        index 1
        value.0 false
        value.1 false
    }
    control.13 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1650
        comment.dbmax 3000
        iface MIXER
        name 'Capture Volume'
        value.0 31
        value.1 31
    }
    control.14 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1650
        comment.dbmax 3000
        iface MIXER
        name 'Capture Volume'
        index 1
        value.0 31
        value.1 31
    }
    control.15 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Front Mic'
        iface MIXER
        name 'Input Source'
        value Mic
    }
    control.16 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic
        comment.item.1 'Front Mic'
        iface MIXER
        name 'Input Source'
        index 1
        value 'Front Mic'
    }
    control.17 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.18 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.19 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.20 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
    control.21 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Default PCM Playback Switch'
        value true
    }
    control.22 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Beep Playback Volume'
        value.0 31
        value.1 31
    }
    control.23 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Beep Playback Switch'
        value.0 true
        value.1 true
    }
    control.24 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 64'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value 64
    }
    control.25 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.26 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 1
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.27 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 1
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.28 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        index 1
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.29 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        index 1
        value true
    }
    control.30 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        index 2
        value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.31 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        index 2
        value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.32 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        index 2
        value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.33 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        index 2
        value true
    }
    control.34 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 255
        value.1 255
    }
    control.35 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 120'
        comment.tlv '0000000100000008fffff44800000032'
        comment.dbmin -3000
        comment.dbmax 3000
        iface MIXER
        name 'Digital Capture Volume'
        value.0 60
        value.1 60
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
isofs
udf
crc_itu_t
binfmt_misc
ppdev
joydev
arc4
ecb
snd_hda_codec_intelhdmi
snd_hda_codec_realtek
ath9k
mac80211
ath
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
uvcvideo
videodev
iptable_filter
v4l1_compat
snd_seq
psmouse
cfg80211
snd_timer
snd_seq_device
ip_tables
serio_raw
x_tables
snd
soundcore
snd_page_alloc
led_class
lp
parport
fbcon
tileblit
font
bitblit
softcursor
i915
drm
i2c_algo_bit
tg3
video
intel_agp
agpgart
output


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x411111f0
0x12 0x411111f0
0x13 0x411111f0
0x14 0x99130110
0x15 0x411111f0
0x16 0x411111f0
0x17 0x411111f0
0x18 0x03a19840
0x19 0x99a30930
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x4006892d
0x1e 0x03451120
0x21 0x0321101f

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D1/init_pin_configs:
0x73 0x016a10f0

/sys/class/sound/hwC0D1/driver_pin_configs:

/sys/class/sound/hwC0D1/user_pin_configs:

/sys/class/sound/hwC0D1/init_verbs:

/sys/class/sound/hwC0D3/init_pin_configs:
0x04 0x18560010
0x05 0x58560020
0x06 0x58560030

/sys/class/sound/hwC0D3/driver_pin_configs:

/sys/class/sound/hwC0D3/user_pin_configs:

/sys/class/sound/hwC0D3/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[    6.116308] i2c-adapter i2c-2: unable to read EDID block.
[    6.116311] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    6.131826] [drm] fb0: inteldrmfb frame buffer device
--
[   19.622991]   alloc kstat_irqs on node -1
[   19.623000] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.623411]   alloc irq_desc for 33 on node -1
[   19.623414]   alloc kstat_irqs on node -1
[   19.623429] HDA Intel 0000:00:1b.0: irq 33 for MSI/MSI-X
[   19.623465] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.640963] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
--
[   19.675200]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.771793] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   20.073591] ath: EEPROM regdomain: 0x65
--
[   21.203549] i2c-adapter i2c-2: unable to read EDID block.
[   21.203553] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   21.208155] i2c-adapter i2c-2: unable to read EDID block.
[   21.208157] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   21.342061] i2c-adapter i2c-2: unable to read EDID block.
[   21.342065] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   21.346669] i2c-adapter i2c-2: unable to read EDID block.
[   21.346680] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   21.348312] CPU0 attaching NULL sched-domain.
--
[   22.541302] i2c-adapter i2c-2: unable to read EDID block.
[   22.541307] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   22.546002] i2c-adapter i2c-2: unable to read EDID block.
[   22.546005] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.170884] i2c-adapter i2c-2: unable to read EDID block.
[   23.170889] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.175556] i2c-adapter i2c-2: unable to read EDID block.
[   23.175559] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.310841] i2c-adapter i2c-2: unable to read EDID block.
[   23.310844] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.315496] i2c-adapter i2c-2: unable to read EDID block.
[   23.315499] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   33.439389] i2c-adapter i2c-2: unable to read EDID block.
[   33.439394] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   33.444309] i2c-adapter i2c-2: unable to read EDID block.
[   33.444313] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   33.581390] i2c-adapter i2c-2: unable to read EDID block.
[   33.581395] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   33.586086] i2c-adapter i2c-2: unable to read EDID block.
[   33.586088] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   33.723253] i2c-adapter i2c-2: unable to read EDID block.
[   33.723258] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   33.727896] i2c-adapter i2c-2: unable to read EDID block.
[   33.727899] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   34.626360] i2c-adapter i2c-2: unable to read EDID block.
[   34.626364] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   34.631303] i2c-adapter i2c-2: unable to read EDID block.
[   34.631305] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   36.376066] wlan0: deauthenticating from 00:22:75:95:47:0d by local choice (reason=3)
```

[FONT=monospace]
Alsamixer is showing all the volume maxed and unmuted, but still no sound.  I am pretty sure it is due to the unupdated driver but for some reason the install is not working.  Any help would be appreciated
lspci | grep Audio gives

[/FONT]```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
```[FONT=monospace]

and aplay -l gives
[/FONT]```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```[FONT=monospace]


[/FONT]

---

### Post by lidex on 2010-04-21
> **pcarcel said:**
> I am having a problem updating the alsa driver to 1.0.23. 

Have a look here:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")

---

### Post by pcarcel on 2010-04-21
Thanks for the quick reply.  I did what was described in that post but the driver is still 1.0.22.1.  I have gone through the update for the alsa driver 3 or 4 times now but it just stays at 1.0.22.1.

---

### Post by lidex on 2010-04-21
Did you open the script before running and edit the info as described in that post by *Temüjin*?

---

### Post by pcarcel on 2010-04-21
Yea changed everything to 1.0.23 except the last line which I think was 1.0.17, but anyway yea I changed the numbers based on that post.

---

### Post by lidex on 2010-04-21
pcarcel,
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack-dig 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
(2)Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by pcarcel on 2010-04-21
Thank you so much that got it working.  On that line I originally had model=auto but after changing it and rebooting the sound is working.  Thank you again

---

### Post by pcarcel on 2010-04-21
Ok I hate bothering you with all these problems but I got sound working in everything except my built in mic does not work in skype.  I don't know if you would know what to do but any help in pointing me in the right direction would be appreciated. 
never mind rookie mistake in sound preferences I had the wrong input to the mic its working now thanks again for all the help.

---

### Post by lidex on 2010-04-21
Terrific. Would you mark the thread as solved please? Use "Thread Tools" near the top. Thanks!

---

### Post by cuberts on 2010-04-21
> **Sentoguy said:**
> Ok, so I've been trying to get my sound system to work (Ubuntu 9.10, Dell Zino HD) and have already updated Alsa using this tutorial and this tutorial:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

I got to the "pastbin" part, made an account and started to ask a question and I got what looks like a big red "-" sign up on the right of the tool bar (the synaptic manager) asking me to install sun-java6. Apparently I missed the "accept terms" box and now it won't let me install the package. Keeps telling me that it's broken, even after pasting the command prompt "sudo dpkg --configure -a" into into the terminal.

This is really getting to be a headache. Is there anyway that I can just go back, reboot the kernel from scratch and start over? Is that what the "recovery mode" option is at the start up?

Please help.

Thanks
I am having the same problem, it is just a different model

---

### Post by pcarcel on 2010-04-21
> **lidex said:**
> Terrific. Would you mark the thread as solved please? Use "Thread Tools" near the top. Thanks!

I would be happy to but thread tools is only letting me view a printable version, email the page or subscribe to the thread.

---

### Post by lidex on 2010-04-21
> **pcarcel said:**
> I would be happy to but thread tools is only letting me view a printable version, email the page or subscribe to the thread.

That's only because I'm an idiot - you're not the OP. Got my threads mixed up. As Emily Litella would say, never mind.

---

### Post by pcarcel on 2010-04-21
I figured thats why I couldn't do it.  No worries.  Thanks for the help again.

---

