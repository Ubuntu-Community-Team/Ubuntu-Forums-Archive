---
title: "Sound problems with audigy 9.04"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by tony.morse on 2009-07-10
I've been at this all day and I'm getting nowhere so all help appreciated.

I've installed ubuntu 9.04 and I'm not getting sound.  The test in Sound Preferences works fine on the Audigy 1...(alsa mixer), I can hear that, but I can't seem to get any programs to use that, they all play through pulse it seems.  So sounds register in pulse, I can see the sound meter move but I just cant hear the sounds.  I've gone through all the how to guides and so on but they all seem to focus on setting up pulse, which doesn't seem to work for me.  If I could just get my programs to use alsa instead then I think all would be fine.

Help please!!

---

### Post by tony.morse on 2009-07-11
bump

---

### Post by VCoolio on 2009-07-11
[Here]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") is what I used a couple of weeks ago when I was setting up 5.1 sound with a new audigy card. Not sure if that was all I did to disable pulseaudio, but sound is working well. I'm no expert though, so this is all I can give.

---

### Post by tony.morse on 2009-07-15
Well I tried that and the result was that my sound card was no longer listed at all, even lspci couldn't see it.  So I've re-installed and am still stuck???

I've tried uninstalling pulse audio with...
sudo apt-get purge pulseaudio

and then installing esound (which worked for a friend with a different sound card)
sudo apt-get install esound

This made ubuntu play a startup noise!! but after that no sound, and the only thing I can hear is from the sound preferences set to alsa and press test. nothing else makes sound.

I've really gone through loads of other guides too please please can someone help
Thanks

---

### Post by tony.morse on 2009-07-16
bump

---

### Post by t4thfavor on 2009-07-16
Hate to say it, but I have 2x audigy 2 ZS OMFG I cost 300USD when NEW CARDS, and both of them are in a box, unused, and rotting. I say this because I will never buy another Creative product again after finding out that they purposly crippled the driver under Vista in order to get more people to buy new cards. 

I know this because a programmer by the name DanielK modified the drivers for the Audugy4/XFi series to work with my audigy 2 under Vista. Without these slightly modified drivers I would have had a paperweight under Windows too, and had to buy another.

There is no reason to have to buy a brand new high end card every 2 years, so I will just not buy from them anymore.

Bottom line is:

None of my audigy's work with creatives drivers under Windows, and most of the advanced features don't work under Ubuntu/Linux, and it's all Creative's fault.

/rant over.

Good luck, hope you don't have a livedrive :)

---

### Post by tony.morse on 2009-07-19
well I've updated my work machine too and now I have the same problem there, also an audigy... CA0106

Please please someone help...
Does anyone have an audigy working with ubuntu 9.04???

---

### Post by ratcheer on 2009-07-19
Yes, my Audigy is working fine with 9.04. It did not work at first, but I followed the instructions in the big tutorial thread and got everything going.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

My biggest issue was the permissions to the pa* groups. But, that was solved after going through everything several times, so I am not sure what other problems were resolved along the way.

Tim

---

### Post by tony.morse on 2009-07-20
Wow, thanks I'm not sure which bit did it but I followed that thread and now have sound!!!

Problem is that Skype still doesn't produce sound.  Anyone have any ideas on this, I've tried all the possible sound settings within skype and no luck...

---

### Post by tony.morse on 2009-07-21
Ok so I followed both of these links [this]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") and [this]("http://ubuntuforums.org/showthread.php?t=766683")

And the result is that I now have sound working on my machine at home (audigy1 CA0060) I have yet to test skype and firefox but things are looking good there.

I did exactly the same at work and now I have no sound again!!

Both machines are free from pulseaudio though and default to alsa which is good news.

---

### Post by tony.morse on 2009-07-21
> **t4thfavor said:**
> Hate to say it, but I have 2x audigy 2 ZS OMFG I cost 300USD when NEW CARDS, and both of them are in a box, unused, and rotting. I say this because I will never buy another Creative product again after finding out that they purposly crippled the driver under Vista in order to get more people to buy new cards. 

I know this because a programmer by the name DanielK modified the drivers for the Audugy4/XFi series to work with my audigy 2 under Vista. Without these slightly modified drivers I would have had a paperweight under Windows too, and had to buy another.

There is no reason to have to buy a brand new high end card every 2 years, so I will just not buy from them anymore.

Bottom line is:

None of my audigy's work with creatives drivers under Windows, and most of the advanced features don't work under Ubuntu/Linux, and it's all Creative's fault.

/rant over.

Good luck, hope you don't have a livedrive :)

For windows and audigy you should NEVER use vreatives drives, instead look at the KX project [here]("http://kxproject.lugosoft.com/"), you will get far superior sound from that and it should all work nicely!!

---

### Post by tony.morse on 2009-07-22
just to update, all sound on my home machine is working!!!

My work machine (with CA1060 audigy) still has no sound... any more ideas?

---

