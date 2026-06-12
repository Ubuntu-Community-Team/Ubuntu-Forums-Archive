---
title: "Firefox sound not working"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by lolzwut on 2010-04-30
To start off I'd like to say I tried this solution: [http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422) but it doesn't work. My firefoxrc file is blank.


So onto my main problem, my sound just stopped working earlier today on firefox. I didn't even do anything it just didn't work. The sound works on everything else though like media player. I've searched the site for threads about it but none of the solutions work. I've restarted firefox a ton of times so I don't know what could be wrong or how to fix it. Can someone help me? Thanks.

edit: btw my sound is turned up on firefox in the sound mixer

---

### Post by ratcheer on 2010-04-30
Sound for Flash in Firefox?

Tim

---

### Post by lolzwut on 2010-04-30
> **ratcheer said:**
> Sound for Flash in Firefox?

Tim


what? the sound doesn't work at all..

---

### Post by ratcheer on 2010-04-30
That's what I was asking. I know how to fix the Flash sound issue, but not if your problem is bigger.

Tim

---

### Post by Kafubie on 2010-04-30
For me, I went to
The Sound Icon -> sound preferences -> output -> connector -> analog speakers. (if you don't have the sound button on your panel,right click any panel ->  go to add to panel -> indicator applet) 
:-D

---

### Post by lolzwut on 2010-04-30
> **ratcheer said:**
> That's what I was asking. I know how to fix the Flash sound issue, but not if your problem is bigger.

Tim


Sorry, I didn't understand the question completely. The sound only doesn't work on streaming videos like youtube. I guess that's flash. Can you tell me how to fix it?

@Kafubie:

I don't have a connector tab

---

### Post by Kafubie on 2010-04-30
> **lolzwut said:**
> Sorry, I didn't understand the question completely. The sound only doesn't work on streaming videos like youtube. I guess that's flash. Can you tell me how to fix it?

@Kafubie:

I don't have a connector tab

I mean, go to the input tab on top, then go to connecter which is like half way down in the input tab.  If it's literally not there then I don't know If I could help.  You need expert powers!:lolflag:

---

### Post by ratcheer on 2010-04-30
Yes, YouTube videos are Flash.

So, next question: Does your system have more than one sound card? If yes, the problem is that Flash will ONLY use the first sound card that ALSA sees. If that is not the card connected to your speakers, you will get no sound from Flash.

Tim

---

### Post by lolzwut on 2010-04-30
That's weird it just started working again. I don't get it for absolutely no reason it just started working. Whatever at least it works, I'll post back here again if it stops working later on.



> **ratcheer said:**
> Yes, YouTube videos are Flash.

So, next question: Does your system have more than one sound card? If yes, the problem is that Flash will ONLY use the first sound card that ALSA sees. If that is not the card connected to your speakers, you will get no sound from Flash.

Tim

Um....I don't know how to check how many soundcards I have. I'm really a linux noob sorry. I would the guess the answer is one though because in sound preferences under hardware it has internal audio then my headphones... I don't know if that's what you're asking for though.

---

### Post by ratcheer on 2010-04-30
Ok, I'm glad you're working, again.

Tim

---

### Post by stinkypudding on 2010-04-30
May I ask what if anything you did?  I'm having the exact same issue.   Flash video works, but no audio.  Everything else works fine, and I just have a single sound card.   And it's not limited to firefox, same issue with Google Chrome.  I've uninstalled and reinstalled flash, to no avail.  Can anyone help?

---

### Post by Kafubie on 2010-04-30
Try the way I recently posted, it helped for me.
I did exactly what you did prior also. lol

---

### Post by lolzwut on 2010-04-30
> **stinkypudding said:**
> May I ask what if anything you did?  I'm having the exact same issue.   Flash video works, but no audio.  Everything else works fine, and I just have a single sound card.   And it's not limited to firefox, same issue with Google Chrome.  I've uninstalled and reinstalled flash, to no avail.  Can anyone help?

nope sorry. I didn't do anything it just worked for no reason. I didn't even restart firefox

---

### Post by smythie86 on 2010-05-01
> **ratcheer said:**
> Yes, YouTube videos are Flash.

So, next question: Does your system have more than one sound card? If yes, the problem is that Flash will ONLY use the first sound card that ALSA sees. If that is not the card connected to your speakers, you will get no sound from Flash.

Tim

I believe this is the exact problem I am having. sound works for amarok, but not for firefox. I have 2 sound cards on my system, one on the motherboard, and another one that I am actually plugged into. How can I fix this problem?

Thanks

---

### Post by ratcheer on 2010-05-01
> **smythie86 said:**
> I believe this is the exact problem I am having. sound works for amarok, but not for firefox. I have 2 sound cards on my system, one on the motherboard, and another one that I am actually plugged into. How can I fix this problem?

Thanks

1) cat /proc/asound/modules

If card 0 is the one you **don't** want, you have to force it to be card 1.

2) Edit file /etc/modprobe.d/alsa-base.conf. Find the line that says:

"# Prevent abnormal drivers from grabbing index 0" and, after it, insert a new line:

options xxxxxxx index=1

where xxxxxxx is the name of the sound module with index 0 from step 1 output

3) Save the file and reboot. Your Flash sound should be working. To double check, rerun "cat  /proc/asound/modules".

I hope this helps.

Tim

---

### Post by itisachilles on 2010-05-01
If limewire is installed on your computer and its running ***_[COLOR=Red]TURN IT OFF AND EXIT[/COLOR]_***[COLOR=Red][COLOR=Black] it will kill any sound coming from firefox but not chrome nor opera (as far as i can tell)
 p.s. only had this problem in 10.04
[/COLOR][/COLOR]

---

### Post by smythie86 on 2010-05-02
> **ratcheer said:**
> 1) cat /proc/asound/modules

If card 0 is the one you **don't** want, you have to force it to be card 1.

2) Edit file /etc/modprobe.d/alsa-base.conf. Find the line that says:

"# Prevent abnormal drivers from grabbing index 0" and, after it, insert a new line:

options xxxxxxx index=1

where xxxxxxx is the name of the sound module with index 0 from step 1 output

3) Save the file and reboot. Your Flash sound should be working. To double check, rerun "cat  /proc/asound/modules".

I hope this helps.

Tim

Yes this was exactly the problem, and this fixed it. Thank you!

---

### Post by ratcheer on 2010-05-02
> **smythie86 said:**
> Yes this was exactly the problem, and this fixed it. Thank you!

You're welcome. I'm glad I could help.

Tim

---

### Post by Kafubie on 2010-05-02
-Rat
=D>=D>=D>=D>=D>

---

### Post by eklypze on 2010-05-02
Thanks so much ratcheer ! It worked !

---

### Post by ratcheer on 2010-05-03
> **eklypze said:**
> Thanks so much ratcheer ! It worked !

You're welcome.

Tim

---

### Post by distilledwater on 2010-05-11
> **Kafubie said:**
> For me, I went to
The Sound Icon -> sound preferences -> output -> connector -> analog speakers. (if you don't have the sound button on your panel,right click any panel ->  go to add to panel -> indicator applet) 
:-D

Awesome! this worked for me except i had to change it to > analog output. 

Woo! this problem has been troubling me for the last two days.

I don't understand how that fixed it though.

---

### Post by distilledwater on 2010-05-14
Alright actually my audio is still not fixed.

Audio works fine through Amarok and VLC when i play different forms of media.

In firefox when i try to watch a video on youtube or try streaming music from grooveshark or myspace i get no audio. The visual aspect of the video on youtube works but not the audio.

Also when i close the tab after getting no audio firefox will just crash.

I have uninstalled flash completely and reinstalled it multiple times, then i tried fully reinstalling firefox, still to no avail.

This is driving me nuts cause everything else on lucid works perfectly.

---

### Post by mcalautt on 2010-11-26
I have the problem.    vidio/audio works fine in players but not in konqueror or firefox.


DISTRIB_ID=Ubuntu  
DISTRIB_RELEASE=10.04 <br>DISTRIB_CODENAME=lucid 

DISTRIB_DESCRIPTION=&quot;Ubuntu 10.04.1 LTS 
 Linux toshiba-carcass 2.6.32-26-generic #47-Ubuntu SMP Wed Nov 17 15:59:05 UTC 2010 i686 GNU/Linux  
firefox 3.6.12    flashplugin-installer                        10.1.102.65ubuntu0.10.04.1 
                  
     i tried downloading the libflashplayer.so from adoble directly and added it in 
/usr/share/ubufox/plugins/libflashplayer.so 
/usr/lib/flashplugin-installer/libflashplayer.so 
/usr/lib/firefox/plugins/libflashplayer.so

---

### Post by mcalautt on 2010-11-28
I found it.. it was the stupid PCM volume control. It was at 0. its on the mixer controls when you click on the speaker in the tool bar

---

### Post by GWild on 2010-12-26
> **ratcheer said:**
> 1) cat /proc/asound/modules

If card 0 is the one you **don't** want, you have to force it to be card 1.

2) Edit file /etc/modprobe.d/alsa-base.conf. Find the line that says:

"# Prevent abnormal drivers from grabbing index 0" and, after it, insert a new line:

options xxxxxxx index=1

where xxxxxxx is the name of the sound module with index 0 from step 1 output

3) Save the file and reboot. Your Flash sound should be working. To double check, rerun "cat  /proc/asound/modules".

I hope this helps.

Tim

ratcheer:

Thank you for posting this.

I'm running Kub 10.04 64 and lost Flash audio after installing the Flash blocker add-on for Firefox - but lost ALL Flash audio on the system (it worked prior to installing the Flash blocker).

I used your method (and a bit of trial and error) and was able to restore Flash audio on the system.

---

### Post by ratcheer on 2010-12-26
> **GWild said:**
> ratcheer:

Thank you for posting this.

I'm running Kub 10.04 64 and lost Flash audio after installing the Flash blocker add-on for Firefox - but lost ALL Flash audio on the system (it worked prior to installing the Flash blocker).

I used your method (and a bit of trial and error) and was able to restore Flash audio on the system.

You are welcome.

Tim

---

### Post by jornand on 2011-07-11
I had the same problem for ages until I accidentally stumbled upon a solution. It is important to have a flash video or flash app running. If no, the alsamixer won't show up. Then go to sound/preferences/applications and crank up the volume on the alsamixer. Problem solved! :)

---

### Post by cje on 2011-09-13
> **jornand said:**
> I had the same problem for ages until I accidentally stumbled upon a solution. It is important to have a flash video or flash app running. If no, the alsamixer won't show up. Then go to sound/preferences/applications and crank up the volume on the alsamixer. Problem solved! :)

That's it! Thanks! :-)

---

