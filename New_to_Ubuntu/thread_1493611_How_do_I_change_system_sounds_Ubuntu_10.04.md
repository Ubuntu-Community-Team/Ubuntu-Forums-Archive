---
title: "How do I change system sounds? Ubuntu 10.04"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by erusso0001 on 2010-05-26
Hello,

Im trying to figure out how to change the sounds on ubuntu 10.04. For instance, when I click to run an application I have a certain sound I want it to play, when I turn on and shutdown the laptop i have another sound for that, etc...

Any help would be appreciated

Ed

---

### Post by drpjkurian on 2010-05-26
Hi
What I figured from your question is that you have to change system sounds.

Well Please navigate to System->Preference-> Sound.
In Sound please click sound tab. You may find several features like login sound etc.

If you have to change it, Double click on it and add the sound clip you prefer.

Hope it was helpful

---

### Post by abtinf on 2010-06-16
drpjkurian: your answer is wrong. That functionality no longer exists.

I would like to know the answer to this as well. The GNOME folks keep removing features and its never quite clear how to accomplish the same task again.

---

### Post by winterfire on 2010-07-02
Can you do it in KDE? (Kubuntu)?

---

### Post by gallifrey on 2010-07-03
A work around that I am using is to copy the Ubuntu sounds file from /usr/share/sounds, and substitute the files within with whatever I want (so long as they are in Ogg format). The I use gksu nautilus to replace the modified folder (making sure to backup the original, just rename to ubuntu-bak or something). 

I am currently enjoying a Doctor Who sound themed desktop!

---

### Post by milesnapue on 2010-07-11
Having trouble with this, used the Nautilus script found on gnome-look called Avconvert to change some sounds I picked up from .wav to .ogg, renamed to match what was in /usr/share/sound/ubuntu/stereo but they do not work. I'm not sure if it was how Avconvert converted the files or what. Any help is much appreciated.

---

### Post by daniel_w93 on 2010-07-11
> **gallifrey said:**
> A work around that I am using is to copy the Ubuntu sounds file from /usr/share/sounds, and substitute the files within with whatever I want (so long as they are in Ogg format). The I use gksu nautilus to replace the modified folder (making sure to backup the original, just rename to ubuntu-bak or something). 

I am currently enjoying a Doctor Who sound themed desktop!

Is that working for the start up/shutdown sounds as well? cause I can remember on Jaunty I had to work around that, changing something in a /bin/bash script that was used in the start up applications....took me hours just to work around that stupid start up sound

---

### Post by daniel_w93 on 2010-07-11
> **milesnapue said:**
> Having trouble with this, used the Nautilus script found on gnome-look called Avconvert to change some sounds I picked up from .wav to .ogg, renamed to match what was in /usr/share/sound/ubuntu/stereo but they do not work. I'm not sure if it was how Avconvert converted the files or what. Any help is much appreciated.

Some of the system notification sounds are in the /usr/share/sound/gnome directory so maybe you try putting them there as well.
And maybe give an example what custom sound you put where to substitute a system sound.

I just hate how there isn't a really easy way of doing all that, as if the ubuntu team is against customization

---

### Post by Nafetitive on 2010-09-13
Any idea if or when they're going to return the "Sounds" option in System>Preferences? 10.04 has been out for a while, so I would think they'd have figured it out by now. I'm getting tired of the default startup music! We shouldn't have to manually mess around with files just to change a particular sound. One of the (many) things that attracted me to Ubuntu was how customizable it was. 
I still love Ubuntu, I just wish it had some of the same options from previous releases.

---

### Post by mastablasta on 2010-09-13
> **Nafetitive said:**
>  We shouldn't have to manually mess around with files just to change a particular sound.
 
Maybe the devs really liked the way things were handled in Win 3.x :D
 
 
seriously changing sound by changing files liek that is the silliest thing ever. i have to check but unless i am wrong i should have the menu still there. maybe because i upgraded from 9.10.

---

### Post by HayaL on 2010-09-20
I changed the default ubuntu sound theme, as follows:
[FONT=Verdana]
1. Install "Sound Conventer"
2. Convert your "desktop-login.wav" file to "desktop-login.ogg" (and others)
3. Create a directory under /usr/share/sounds/ (for example: Mac)
4. Create this /usr/share/sounds/Mac/index.theme file:[/FONT]

```

[Sound Theme]
Name=Mac
Directories=Leopard

[Mac]
OutputProfile=Leopard

```5. Create your /usr/share/sounds/Mac/Leopard directory
6. Copy your "desktop-login.ogg" file to "/usr/share/sounds/Mac/Leopard/"
7. Open "Sound Preferences" and click "Sound Effects" tab. Click Sound theme combo-box and select your "Mac" theme.
8. Logout, login and listen :)

---

### Post by Python Jedi on 2010-09-24
This works great, I'm going to look into making a script to do this given a series of files.  the only problem is having to do ```
sudo nautilus
``` and ```
sudo gedit
``` or similar to be able to read and write in /usr/share/sounds

Aside from that, it works fine, and I'm going to look up different names so that I can have even more sounds and figure out the text file's format.

---

### Post by HayaL on 2010-09-25
We don't need sudo.
We can do the same thing in our home directory.
The directory structure may be as follows:

```

$HOME/.local/share/sounds/Windows/index.theme
$HOME/.local/share/sounds/Windows/stereo/desktop-login.ogg
$HOME/.local/share/sounds/Windows/stereo/desktop-logout.ogg
$HOME/.local/share/sounds/Windows/stereo/dialog-question.ogg
$HOME/.local/share/sounds/Windows/stereo/dialog-warning.ogg
.....

```But this time, other users won't access the sound theme.

---

### Post by mjonyh on 2010-10-26
Why does ubuntu make tough to customize..?

---

### Post by bluntz on 2010-10-28
I absolutely refuse to make any directory named
Windows... I hate the changes that break things without
a way to return the old functionality.
I hate pulse audio with a passion!!!!

---

### Post by Ichido on 2010-12-07
Here is how I changed my "Drums" to a Cool Sound:


1.Open Nautilus-root (gksudo nautilus) and go to /usr/share/sounds/ubuntu/stereo/ .
2.Copy the  &#8220;desktop-login.ogg&#8221; file, Create a new folder  /Music/OGG Files/ and paste &#8220;desktop-login.ogg&#8221; into /Music/OGG/ directory and change it's name to UbuntuDrums.ogg, (so you will have it Backed-Up).
3.Find the WAV File you want to as your start-up sound and use Sound Converter to change MYSOUND.wav into MYSOUND.ogg and then put MYSOUND.ogg file into /Music/OGG/.
4.Change the name of the &#8220;MYSOUND.ogg&#8221; File to &#8220;desktop-login.ogg&#8221;
5.Change all of &#8220;desktop-login.ogg&#8221; File Permissions to root/read and write.
6.Copy/Overwrite the &#8220;desktop-login.ogg&#8221; to /usr/share/sounds/ubuntu/stereo/ &#8220;desktop-login.ogg&#8221;.

	Next boot will play your new sound!

	Remember to use Nautilus-root (gksudo nautilus) for all of the above file operations.

---

### Post by jonnan on 2011-06-15
This is frickin' insane - I just updated to Ubuntu 10.04 and just want to toggle off the one, huge, login noise that goes off with the volume at 100% when I login at 10:30 at night and the house is in bed.

It's utterly ridiculous that we've been reduced to changing files around to deal with this. 

This is basic functionality that regresses a 21st century OS back to the 1990's.

---

### Post by unc0nn3ct3d on 2011-09-07
Thsi issue is seriously still here? I can only guess that the previous setup was causing major problems somewhere because there's no rational reason at all for taking this out.

---

