---
title: "Sound problems and?? Mathematica"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by harelb on 2010-10-01
My sound was working fine. I tried to install mathematica, I got a 650megabyte "Mathematica_7.0.1_LINUX_MachineSpecific.sh" file I double clicked...that failed.

About 24 or 48 hours later I tried to listen to some music and nothing. It might be a coincidence, due to something else that I did or which happened in those 48 hours. I did find [https://help.ubuntu.com/community/Mathematica](https://help.ubuntu.com/community/Mathematica) which says "sound does not work in mathematica" Now that is very different from saying "trying to run the .sh can ruin the sound" but does suggest that maybe, just maybe it was not a coincidence.

Also I tried the first few tips at 

[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

and those did not fix the problem. I also know it's not the monitor itself since I can still get sound out of it with other devices (other than my computer)  just fine.

Any ideas how to fix? I sure miss my music collection, my pc collection is more important than my stereo system etc.. Thanks,
Harel
(don't worry about helping me install Mathematica, I've given up for now and will just try the copy at the office on windows or use another software package..I just want my sounds back on my home ubuntu system..which is 9.10 karmic koala)

---

### Post by akoskm on 2010-10-02
What is the output of
```

aplay -L

```?

Right click to the mixer in the systray, select *Sound Preferences* and make sure that the sources are not muted under the Output tab.

---

### Post by harelb on 2010-10-02
Hello, the output of the aplay -L command is:

```

 aplay -L
front:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    Front speakers
surround40:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    4.0 Surround output to Front and Rear speakers
surround41:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server


```

Does that help? As for the rest, I'm really not sure what mixer you're referring to (I don't even think I have a 'systray' in this ubuntu version?) I looked under applications-->sound&video and none of the six items there has "mixer" in their names, so need more specific directions if you need me to try looking elsewhere as well. HB

> **akoskm said:**
> What is the output of
```

aplay -L

```?

Right click to the mixer in the systray, select *Sound Preferences* and make sure that the sources are not muted under the Output tab.

---

### Post by lidex on 2010-10-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by harelb on 2010-10-04
Lidex, here's what I got:


Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=8220218bd15ef2732167514763890cc5e7d968fb](http://www.alsa-project.org/db/?f=8220218bd15ef2732167514763890cc5e7d968fb)

Please inform the person helping you.


- -

---

### Post by lidex on 2010-10-05
> **harelb said:**
> Lidex, here's what I got:


Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=8220218bd15ef2732167514763890cc5e7d968fb](http://www.alsa-project.org/db/?f=8220218bd15ef2732167514763890cc5e7d968fb)

Please inform the person helping you.


- -

Did you check your mixer settings? Looks like they are muted.
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by harelb on 2010-10-05
Lidex,
thank you..I think you are on to something (which possibly happened during that failed running of that 650MB .sh file for mathematica which bombed..which apparently is what changed/reset one or more of my sound settings..) and I just want to make sure I'm doing this right. Since I have Gnome, I installed the gnome version, successfully, then I ran Gnome-alsamixer and got an error message but not a fatal one:

```

An error occurred while loading or saving configuration information
for GNOME ALSA Mixer. Some of your configuration settings may not work
properly.

```

when I clicked open for the details it said,

```

Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/":
Key/directory may not end with a slash '/'
Bad key or directory name: "/apps/gnome-alsamixer/display_names/":
Key/directory may not end with a slash '/'

```

As I said it wasn't fatal in that the gnome-alsa mixer still launched..but I'm sharing the above just in case it means I have to follow different directions. Assuming it's still ok to operate the gnome-alsa mixer, here's a screenshot of what I have (after making the screen wider to fill the whole screen (uploaded below as screen-sound.png)

it looks like I can just use mouse to change settings, which is good since (to be honest) I'm not sure what "select the right sound card" would be for me (in my years of using this computer I basically never have had to know the type/name of it..) so instead of the F6 and other F-keys, from the screenshot, should I simply uncheck ALL the "mute" buttons? some of them only (which)?

And leave the bottom portion (where "EIC958" and "External amplifier" are checked) alone?

I could try on my own but with so many variations and combinations to try I think I'll play it safe and wait for your reply :-) But hopefully it's as simple as something along those lines..Thx,
Harel

---

### Post by freacert on 2010-10-08
I would say, unmute everything, in both soundcards, and probably you will have sound

---

### Post by lidex on 2010-10-08
> **freacert said:**
> I would say, unmute everything, in both soundcards, and probably you will have sound

Sounds reasonable, you'll need to raise the levels also.
But for just the Realtek, the other looks like a modem.

---

### Post by harelb on 2010-10-08
Thank you freacert and lidex. Unfortunately nothing I try seems to work. Thanks lidex for the idea of "raise the levels also" But that didn't fix it either.

We have several obvious issues:

A. The error that comes up every time  I run it. See my previous post. Could this be a problem? See also the image "after-reboot-a.png" attached. Do we need to fix this error message, or else fixing the sound will be impossible, maybe..? Just wondering..

B. I was able to un-mute EVERYTHING. It used to have 12 things on mute (see screen-sound.png attached to my previous post) But when I re-boot, ONE of them, one of the two "master" is back to mute.

C. However, BEFORE I re-boot, I can have things so ALL the mutes are off..and even with all of them off (and the levels raised) I still don't get any sound.

See before-reboot1.png (and the second before-reboot2.png is the other tab, which you are right, does not seem to be a sound card) then see the two after-reboot files. So B. is a problem (mute comes back on in one place, after every reboot) but B. is not the only problem since AFTER I turn off the last mute (but BEFORE I re-boot again) the sound still doesn't work... 

I still have no proof that my trying to install mathematica did this, but if so, then I am never going to trust them again (see my original post re possible connection) I'm also attaching mathematica.png for an image of the possible culprit (huge) file.

D. One other possible problem..I'm a total newbie on much of the hardware on my system...I didn't even know the sound card..I guess "IEC958" is my sound card?? Could there be others?  Will "alsa-mixer" be able to "see everything"? 

Very much missing music/any sounds on my machine.. :(

I hope the above four bullets (A through D) help along with the attachments..any ideas how to fix these?
Thanks,
Harel

---

### Post by freacert on 2010-10-09
> **harelb said:**
> 

A. The error that comes up every time  I run it. See my previous post. Could this be a problem? See also the image "after-reboot-a.png" attached. Do we need to fix this error message, or else fixing the sound will be impossible, maybe..? Just wondering..



i as absolute beginner would say the clue lies here. Go to synaptic and reinstall alsa. Maybe that will work. 


> **harelb said:**
> 
D. One other possible problem..I'm a total newbie on much of the hardware on my system...I didn't even know the sound card..I guess "IEC958" is my sound card?? Could there be others?  Will "alsa-mixer" be able to "see everything"? 



 your soundcard is the realtek AL655. There are no other soundcards, the other one is a modem.

---

### Post by lidex on 2010-10-09
> **freacert said:**
> i as absolute beginner would say the clue lies here. Go to synaptic and reinstall alsa. Maybe that will work. 

 your soundcard is the realtek AL655. There are no other soundcards, the other one is a modem.

Once again, sounds reasonable, but first uninstall gnome-alsamixer:
```
sudo apt-get purge gnome-alsamixer
```
Now to re-install alsa. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Now re-install gnome-alsamixer and check your levels. Probably a good idea to provide updated 
output from alsa-info script also.

---

### Post by harelb on 2010-10-10
Lidex,
I hope I understood you correctly; I performed the following in exactly this order:
1) sudo apt-get purge gnome-alsamixer
2) sudo apt-get update
3) sudo apt-get upgrade
4)sudo apt-get purge linux-sound-base alsa-base alsa-utils
5) sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

6) I re-booted my computer
then to re-install and run it, I did:
7) sudo apt-get install gnome-alsamixer
and then did
8 ) Alt-F2 and then " gnome-alsamixer" (I'm not sure how this differs from just typing " gnome-alsamixer" into a terminal shell but to be on the safe side did this vertabim)

(I hope the above is correct; I initially skipped from 5) to 7) and that didn't work, so I redid the entire process 1, 2, 3, 4, 5, 6, 7 and 8 in order)

unfortunately, got the same as last time; errors and one of the main mute buttons on, I'll attach 2010oct10.1.png and 2010oct10.2.png


9) Did the wget to be supplied with a url with public info on my settings (namely I ran from terminal, "wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh") got:

 [http://www.alsa-project.org/db/?f=9cebc059c2084b08eca63b801a0d81b6af46d8ce](http://www.alsa-project.org/db/?f=9cebc059c2084b08eca63b801a0d81b6af46d8ce)

Any clues there? If not, short of reinstalling the entire OS (you'd think that wouldn't be necessary..!) isn't there some "do everything sound-related from scratch" set of commands? The above string of commands for some reason didn't do it.. :confused: short of re-installnig OS, what's the 2nd strongest thing (sound-related only, don't want to risk messing up other components, especially being very non-techie)? Harel

---

### Post by lidex on 2010-10-10
It's a bug - apparently an old one:
[https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/184768](https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/184768)

What version of this program do you have? Use this command:
```
dpkg -l | grep "gnome-alsamixer"
```

Go ahead and upgrade your alsa install via the link in my sig.

---

### Post by harelb on 2010-10-11
Lidex,
The response I got to "dpkg -l | grep "gnome-alsamixer" " is:

```

ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                  ALSA sound mixer for GNOME

```

I very much appreciate your sticking with me to get this %$^$%^ sound thing fixed! Things are a bit hectic now but tomorrow night  I'll try the upgrade in your sig and will let you know how things look..thx,
Harel

---

### Post by harelb on 2010-10-12
Lidex, as I said last night I really appreciate your sticking with me but I'm afraid I need another path...this can't be the fix for "Absolute beginners"...can you or can anyone else help just get the sound settings back?

After looking at at your link Lidex, I'm very concerned. This being an "absolute beginning" forum, this is what I hoped to avoid:

> 
Disclaimer: I won't take any responsibility for mess-ups caused by using the script! -- Of course - I do my best to avoid these and support you as much as I can.

As usual - Make a backup first! - A restore will just take 5 minutes with rsync. That might save you hours of troubleshooting and frustration .


And then detailed script-using instructions. I don't even know how to "make a backup first" (and it doesn't even say of what...of the previous ALSA or of one's files or of the entire system OS?) Either way, I can see how this could take up hours..even if says above "save you hours of..." This is a forum for beginners, right? Wrong, it's a forum for ABSOLUTE beginners! Someone have some mercy on beginners who just want plain and simple their sound back...without getting fancy, just using synaptic or other tools for beginngers..I can run a few shell commands, sure, but getting into "I'm not responsible for any messups" and "save you hours" and "make backups (of what? and how?) first" and so on, and running multiple scripts, just to fix alsa (which still might not fix the problem, even if alsa is fixed), is not what I have in mind..

If this is the fix for the "Absolute beginners" forum, I shudder to think what the fix is for other forums. I know one (very inefficient, crazy-but-it-works) way to fix this: re-install the entire linux. I have less than 1% the linux knowledge of others here, for those who have 100 times my knowledge, surely they know of some other way to fix this other than one extreme (re-install linux) and the other extreme (lots of "don't blame me if this messed up your system" scripts to update ALSA which might not work and even if ALSA is updated, might not fix the problem) Help!?? Please? :confused:
Harel

> **lidex said:**
> It's a bug - apparently an old one:
[https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/184768](https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/184768)

What version of this program do you have? Use this command:
```
dpkg -l | grep "gnome-alsamixer"
```

Go ahead and upgrade your alsa install via the link in my sig.

---

### Post by harelb on 2010-10-12
Maybe the reply above in post #15, the reply I got to ""dpkg -l | grep "gnome-alsamixer"" allows the ALSA route to continue without the need to upgrade? If so, there is some hope left for the ALSA route. If not, maybe someone can suggest enough root to fix the sound so it's not automatically in "mute" mode (per above what ALSA did say despite errors) or else failing that, how to re-install all the OS's sound from Step one , in automated synaptec type fashion for Beginners, but short of re-installing the entire OS? Also my schedule is kicking my a** these days and my time if limited...I can see putting in another hour at most...failing that, I'm better off taking one hour (or less, or time needed actively at the computer) to backup all files on thumb-drive and (pretty depressing but will resort to it if I have to) reinstall linux entirely..thanks in advance! :-)
Harel

---

### Post by lidex on 2010-10-14
I have not seen many issues with the alsa upgrade script, in fact I had to use it as a beginner, with my laptop, to get sound. If you just follow the instructions posted there you should be OK. The problem is that releases of ubuntu are frozen as far as alsa is concerned and for good reason. Newer hardware, however, may not be fully supported with the version of a specific release and the alsa upgrade is a good fix for that as it allows you to get the support for it. If you are leery of compiling alsa for your install, I and others are here to support you. 

Having said that, you may wish to take an alternate route. You could try the alsa-backport-modules:
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
You may also upgrade to maverick, which includes alsa v. 10.23 as default.

---

