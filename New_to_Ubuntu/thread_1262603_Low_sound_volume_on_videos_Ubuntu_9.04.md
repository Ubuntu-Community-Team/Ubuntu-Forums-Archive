---
title: "Low sound volume on videos Ubuntu 9.04"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by GiantSpider on 2009-09-10
I thought I had no sound but as of recently I downloaded a flash player. It wasn't adobe it was something new. I was given 3 choices for missing plugin in firefox. One of which I picked another was adobe. Anyways I watched a video and I got low sound, loud enough for me to hear the sound not enough to hear any of the words. 

  So what's up? I got a gigabyte mobo with on board sound. Here's my mobo [http://www.gigabyte.us/Products/Motherboard/Products_Spec.aspx?ProductID=2847](http://www.gigabyte.us/Products/Motherboard/Products_Spec.aspx?ProductID=2847)

The important info is: Realtek ALC888 code

---

### Post by mapes12 on 2009-09-10
Have you installed all the none free codecs?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by anaconda on 2009-09-10
have you checked that the sound volume is set to high?

sometimes it is NOT enough to set the volume high from the palyer you use.. (eg. totem or vlc)

But you also need to set the volume high from
gnome-volume-control

(type gnome-volume-control in terminal to start it.)



alsamixer is another program for adjusting sound settings.....

---

### Post by GiantSpider on 2009-09-10
I have done neither. 

"Have you installed all the none free codecs?"

I assume you mean the not free codecs, or proprietary. I'll check out the gnome. Ok I checked out the gnome and it worked like a charm. Had a pc speaker option and it was set to zero. I was clicking on the volume controls in the upper right. How do you remeber these commands anyways, the commands seem very useful everyone. I'll experiment more with the sound should Ubuntu make sounds be default?

---

### Post by mapes12 on 2009-09-10
> How do you remeber these commands anyways, the commands seem very useful everyone.If you were using another OS e.g. MS windows it would be sensible to keep track of what tweaks and applications you made to your PC as you went along just in case the HDD failed or something like that and you had to install from scratch.

It's the same with Ubuntu. I keep a small text file in my Google Documents account and keep a little list of anything that I need to reinstall and system tweaks so that if I ever have to reinstall from scratch I can very quickly have it how it was before. To help this process I also bookmark any websites I need such as the one I suggested to you in my previous thread. I use the FF addon Xmarks which automatically keeps track of my bookmarks on the Xmarks server which means that even if my PC gets trashed I simply add Xmarks back to FF in a new machine and my bookmarks are instantly there for me.

The above is in addition to making regular backups and cloning the drive (belt & braces) but those are different subjects.

As you get used to Ubu and the fantastic tools you can deploy you will see that you have to try very hard to lose stuff.

---

### Post by GiantSpider on 2009-09-10
Hmmm, it seems tempting to look at the firefox add-on you described and the Google Documents. I keep most of my system changes/tweaks in a notepad in my documents (windows user). I don't back up often, I haven't found a good plan for doing so. My plan for backing up is to network two computers together and put a back up copy of all my data on each computer from both computers, including the tweaks. The more important data I then copy to an external hard drive. 

    I'm a little overprotective when it comes to privacy. I hate tracking cookies, I view them as worse than viruses. One wipe of your hard drive and a reinstall will take care of any virus. With tracking cookies that information is already collected and stored safely. So I'm not so sure of the idea of giving a website my favorites and .txt documents. 


     Backing up my data doesn't help much with Windows if I get a hard drive crash because of microsoft's anti-piracy measures. I mean I could find the orginial os cd and then call microsoft and request that they reactivate my Vista account that I am re-installing on the same computer. Part of the reason I switched to Linux was because of Microsoft treating paying customers unfairly. The main reason I switched to Linux is I'm still pissed about windows Me. I spent good money and microsoft refused to remburse me after I got an unrecoverable error.

---

### Post by RabbitWho on 2009-09-10
This happened to me when I first started using ubuntu. . . I assume you've already tried this, but just in case.. 

click on the speaker icon on your taskbar/panel, click on volume control and make sure everything's up and nothing is muted. 

If you've a microphone you'll need to play with the recording/capture parts as well. 

Don't be annoyed at me if that seemed too obvious, sometimes it's hard to find things on a new system! Especially when the "volume control" option isn't always obvious for some reason, especially with Kubuntu.

---

