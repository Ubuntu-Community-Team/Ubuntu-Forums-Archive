---
title: "Microphone, External monitor, Wireless connection, etc.  problems"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by pinkpinkpinkpanther on 2009-08-22
Hi to all,

I have several problems with my newly installed kubuntu 9.04 on hp Elitebook 6930p laptop. Could you please give this absolute beginner advice on any of them? Thanks in advance!

1- My speakers work after creating file /etc/modprobe.d/options.conf 
    containing this line:
    options snd-hda-intel model=mobile   
I did this through ubuntu bugs pages.
But I cant use my skype even for a test call, it says problem with audio playback.
In setting of multimedia I can see Audio input for which I have one options: HDA Intel(AD 198x Analog); when I select this, test button is not active! How can I fix this?

2- When I want to use an external monitor, I dont see anything on the new monitor!

3- Function key+ other switch keys doesnt work! especially i need to connect this to a projecor.

4-I cannot detect any wireless network!

5- kopete do not connect to my yahoo messenger ID!

6- When I shut down I see this message before turning off:
unable to iterate IDE device
and then it turns off safely. Is this a serious problem?

---

### Post by kaitwospirit on 2009-08-23
I don't know the answers to all of these off the top of my head, but here's a small start.

#6: Other people who have that error seem to be okay. If you're not having any problems with shutdown, I wouldn't worry about it.

For #1: How did you install Skype? Did you download it from their website?

---

### Post by pinkpinkpinkpanther on 2009-08-23
Yes I downloaded .deb file then installed just by clicking; I did this because running 
sudo apt-get install skype 
didnt work.
But I think the problem is not within skype, I guess I shoul ddo somthing with that alsa to make it default for this capture devices. Actually I find out that KMix is not working! I even cannot open it to test my microphone! I even coudnt reinstall it!

---

