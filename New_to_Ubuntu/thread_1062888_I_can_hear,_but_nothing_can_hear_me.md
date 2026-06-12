---
title: "I can hear, but nothing can hear me"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by canam101 on 2009-02-07
I'm running 2.6.24-22 and most things are fine - very pleased with ubuntu.

The only major thing that doesn't work is being able to speak into the microphone on my headset and have the computer 'hear' it.

For example, I can call the skype test number, and hear the voice, but when I speak a message, it does not get recorded.

It isn't the headset or the sound card, because I can boot into mepis and the microphone works.

I used a command (can't recall it) and set all the levels - linein, etc. to 100 percent, but it doesn't help.

I am using the Also sound system.

Any suggestions?

Thanks

---

### Post by beno1990 on 2009-02-07
One solution I've found works for most Skype users is this:

Open the options window and go to sound devices.

Change sound out and ringing to "Pulse" and sound in to "HDA Intel (hw:Intel,0), replacing "Intel" with whatever chipset manufacturer your computer has and shows up in the devices menu.

---

### Post by Dougie187 on 2009-02-07
If you right click on the sound manager and click on "Open Volume Control" what tabs do you see?

You should at least see a playback tab. What selections do you have (to change the volume) in this tab? Do you have a Recording tab, and if so what is listed under that. Finally do you have an options tab, if so what is the top Input Source set to?

If you don't have the Recording or Options tabs try click on the preferences and checking the boxes next to Capture and Input Source. Then under options change one of the input sources to be set to internal mic. Then go to the Recording tab and make the volume higher on the mic and make sure it isn't muted (the picture of a mic right below the volume bars).

---

### Post by superprash2003 on 2009-02-07
what all options do you see under sound capture in system->preferences->sound ??

---

### Post by jery27 on 2009-02-07
I have the same problem.  Have read until blue in the face.  Found that minimizing skype only will avoid the "another instance of skype window" and avoids rebooting, habit only.  I have played w/preferences, tried all the command line tricks for pulse audio and still no successful test call to skype.  This is my 4th day with UBUNTU and I really do not want to go back to windows XP just to use skype.  What do I do?????   Thanx in advance!!

---

### Post by canam101 on 2009-02-07
> **Dougie187 said:**
> If you right click on the sound manager and click on "Open Volume Control" what tabs do you see?

You should at least see a playback tab. What selections do you have (to change the volume) in this tab? Do you have a Recording tab, and if so what is listed under that. Finally do you have an options tab, if so what is the top Input Source set to?

If you don't have the Recording or Options tabs try click on the preferences and checking the boxes next to Capture and Input Source. Then under options change one of the input sources to be set to internal mic. Then go to the Recording tab and make the volume higher on the mic and make sure it isn't muted (the picture of a mic right below the volume bars).

Thank you very much, and thanks to the other gentlemen who replied.

I clicked on preferences, and pretty much enabled everything that said 'capture', and I also enabled 'mic select'.

It looks like 'mic select' was the key for me, because that added an additional microphone, giving 'mic1' and 'mic2'. By switching to mic1, I was able to use the microphone. That fixed the skype problem as well.

---

### Post by Dougie187 on 2009-02-07
Glad to hear that helped you.

---

### Post by jery27 on 2009-02-07
I do not seem to have any of the options that worked for you.  I am still micless.  Glad you got yours going, I will continue searching. TY

---

### Post by jery27 on 2009-02-07
Now I have it!!  Found this in my searching.  What I did:

    applications/accessories/terminal  and then enter this:


                 killall pulseaudio   
                 sudo apt-get remove pulseaudio                   
                 sudo apt-get install esound
                 sudo rm /etc/X11/Xsession.d/70pulseaudio

   Restarted the laptop,  open skype,  main menu/options/sound devices,
   Set sound in/out and ringing to default devices and presto!!!!!
   Test the sound and make a test call, all ok.

  This was a post by RP.    here is the link:

  [http://blog.rajatpandit.com/2008/11/15/skype-audio-playback-and-capture-problem-on-ubuntu-810/](http://blog.rajatpandit.com/2008/11/15/skype-audio-playback-and-capture-problem-on-ubuntu-810/)


  I have spent all day on this and finally...............jery27


  Found a solution for closing skype and then not seeing it running and getting error messages (another instance).  Again it is to someone else's credit:

       [http://lifehacker.com/software/featured-linux-download/dock-any-application-to-the-system-tray-with-alltray-263921.php](http://lifehacker.com/software/featured-linux-download/dock-any-application-to-the-system-tray-with-alltray-263921.php)


        In the terminal:   sudo apt-get install alltray 


      Now skype will show when running and you can see to access it.
        Just loving UBUNTU after only 4 days!!!!!!!!

---

