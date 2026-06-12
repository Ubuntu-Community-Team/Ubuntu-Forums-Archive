---
title: "Connect Bluetooth Sound"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by TedinOz on 2011-01-03
Running Ubuntu 10.10. I am trying to connect the sound of Motorola Bluetooth Headset H350 with no success, both for system sound and VOIP (mainly skype) The headset itself makes a bluetooth connection and is listed in bluetooth preferences. I installed Blueman Manager and Pulse Audio and the connected headset is visible in both of these but is not displayed as an option in skype audio settings. Screen captures are attached here to show.

[ATTACH]179992[/ATTACH]

[ATTACH]179991[/ATTACH]

I made numerous attempts to configure Pulse Audio settings but with no result. I closed Pulse Audio application after settings adjustment and reopened but to no avail. 

I have searched this title and others here and found several similar problems but none appearing to be circumstance similar to mine that I could relate to any answers already given so I apologise if I have missed it somewhere. Also regret to advise that I am a true beginner with Ubuntu and especially the use of terminal commands. I am slightly hard of hearing but need to use Skype telephony frequently and the use of the headset makes it much more workable so if anyone can give me some clues to solve this it will be very much appreciated.

Thanks...Ted

---

### Post by TedinOz on 2011-01-05
So sorry to have to bump this. I feel such a goose in not being able to solve it but truly it is driving me nuts! There is no problem connecting the headset but when I do I have no sound at all and when I try to run a sound application like Rythmbox it just doesn't connect either. It seems to me that there is something missing in allowing the headset to run. PulseAudio has several options to nominate Default Server, Default Sink (whatever that means) and Default Source but I don't know which ones to choose or in what combination.
PulseAudio Configurations for Local Sound Server are as follows in attachments...

[Network Server Preferences.png]("http://ubuntuforums.org/attachment.php?attachmentid=180196&stc=1&d=1294234496")

[Network Access Preferences.png]("http://ubuntuforums.org/attachment.php?attachmentid=180197&stc=1&d=1294234496")

[Multicast RTP Preferences.png]("http://ubuntuforums.org/attachment.php?attachmentid=180198&stc=1&d=1294234496")

[Simultaneous Output Preferences.png]("http://ubuntuforums.org/attachment.php?attachmentid=180199&stc=1&d=1294234496")

With bluetooth off sound is normal without doing anything with these settings. It seems that I should change these to accommodate the bluetooth but I don't know which items should be checked or why or in what combination?

Maybe there is a Terminal command I can send to help identify the problem but I don't know what that is...Help please!

---

### Post by TedinOz on 2011-03-16
In the absence of any replies to this post and that the problem still remains (partially) unsolved, I am adding an update to it in the hope that someone here may identify with it and can offer some advice on how to proceed further. My headset is now partially working  in that I am able to use the headset microphone but I am as yet unable to hear through the headset speakers. I have tested the speakers in the headset using a phone connection so am happy that they work fine but with my bluetooth connection to my laptop, I still can't seem to connect the output to the headset. All the options for connection are there within Pulse Audio settings but when I activate the headset application in output, all sound not only ceases, it stalls completely...e.g. if I am playing Rythmbox player and activate the headset, it turns the off completely as if I have paused it and it does not progress.
Some screenshots attached to illustrate all of this. It can be seen in The Pulse Audio Volume Control that the headset is recognised in the output tab but greyed out in the control. This shot was taken when the headset was activated as shown here in the Sound Preferences.

[ATTACH]186331[/ATTACH]

[ATTACH]186332[/ATTACH]

[ATTACH]186333[/ATTACH]

If anyone can help me with a way to connect the headset speaker to Pulse Audio it will be So Much appreciated :).  I am loving Ubuntu and so glad I made the switch. In multiple cases applications I used on Windows work even better here but for this one...this one has got me beat.

Thanks if you can.

---

### Post by TedinOz on 2011-04-20
Solved!!

I stumbled across this thread which has already been been acknowledged and credited in these forums....

[http://forums.overclockers.com.au/showthread.php?t=780054](http://forums.overclockers.com.au/showthread.php?t=780054)

My problem was hardware not Ubuntu. HyRax1 lists in his prerequisites that a bluetooth adapter needs to be V1.2 or higher for a headset to be properly connected. I checked mine, found it to be V1.1, replaced it with an inexpensive V2.0 from Ebay for $5.95au and voila!...everything works perfectly. The adapter installed automatically, the headset plays music and videos, and I can talk and hear on Skype with beautiful sound! AND no configurations necessary!

I just thought everyone might like to know ;)

---

