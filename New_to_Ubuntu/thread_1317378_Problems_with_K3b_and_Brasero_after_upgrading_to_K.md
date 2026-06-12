---
title: "Problems with K3b and Brasero after upgrading to Karmic 9.10"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by SlimBiggins on 2009-11-06
[SIZE=2]Hello. I've been usuing Ubuntu for about three or so months now. I started running Jaunty Jackalope 9.04. I haven't had any major problems until now.

    That being said, I just put on the new distribution, Karmic Koala 9.10. I did a fresh install, not an upgrade. So far I like to new distribution except I have one problem. I re-installed all my apps and have had no problems except with burning software. k3b is the best burning software I've found so far for Ubuntu.

    In k3b, whenever I try to add a .MP3 file, I get an error message (whether I drag drop the file in, use the programs internal browser, or use the "Add Files" option from the "Project Menu"). The error detail reads as:
 
[/SIZE]**[SIZE=2]Unable to handle the following files due to an unsupported format:[/SIZE]**[SIZE=2][B]
*You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.*
[/B] 
    What I gather from this is that k3b will no longer convert the .MP3 files to .WAV before burning??? Or is this some bug in the program, or the new distribution.??? However I have no problem adding an .OGG file. Is this some type of legal issue???

    Since k3b wouldn't work, I figured I'd give the native burning software a shot (hoping I could at least [/SIZE] [SIZE=2]use that until the issue is resolved). [/SIZE][SIZE=2]Much to my disappointment, I received the same/similar error in [/SIZE][SIZE=2]Brasero. The error detail reads as:

[/SIZE] [SIZE=2]**"01-mos_def-excellence-mob.mp3" could not be opened.**
[/SIZE] [SIZE=2]***"01-mos_def-excellence-mob.mp3" is not suitable for audio or video media.***
[/SIZE] [SIZE=2]
At first I thought Brasero was insulting my taste in music by calling it "not suitable". [Pause for Snare-Snare-Highhat]. I even re-formatted and re-installed again, thinking I had a faulty installtion. Same problems. I know this thread is getting long, but there's one more thing I'd like to add. I got my grandfather to switch to Ubuntu just about a week ago. He got the exact same error with K3b, however was able to burn with Brasero. So I know atleast one other person has the same problem.

[/SIZE] [SIZE=2]Please help. I don't know whats going on here. Is it a bug in the distro? A bug in the new versions of Brasero and/or k3b? A legal issue about converting .MP3 files? I'm stumped.

[/SIZE] [SIZE=2]- SlimBiggins
[/SIZE]

---

### Post by madverb on 2009-11-06
Are you able to play the mp3s?

You might just want to try ```
sudo apt-get install ubuntu-restricted-extras
``` just in case.

I'm having the opposite effect with burning in 9.10. Brasero has been running the best I have ever had it running. I have previously had massive amounts of problems with Brasero but for me it is now running perfectly.
The new interface is fantastic.

---

### Post by SlimBiggins on 2009-11-06
madverb: You hit the nail right on the head. Thanks so much.

I can add .mp3 format, in both k3b and brasero, and convert/burn them with no problems whatsoever. Seems like a legal issue with the software/distribution.

And I must also agree that Brasero's new GUI is a HUGE improvement. Check out k3b. Its a KDE burning app, but runs just fine in GNOME. Infact I prefer k3b over Brasero.

As far as playback, are you getting an error? or just no sound? and are you getting system sounds?

---

### Post by Morpholinux on 2010-01-31
I have the same problem that SlimBiggins..
...
uhmmm I already had the restricted extras..
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>><
sudo apt-get install ubuntu-restricted-extras
[sudo] password for murphy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>><




If I try...
new project->audio cd...
->
I get...
"Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project."

But If I do...
new project->data cd
Then I can burn *.mp3 to a dvd.
...
I just burn it...and my dvd player can read it...so I am happy with that.









I think that w



thanks!

---

### Post by Emmtor on 2010-09-03
I've had the same problem with Morpholinux, but a little searching revealed the solution:

[CODE]$ sudo apt-get install libk3b6-extracodecs [CODE]

Please tell if that worked out after all.
Also, I would like to know what's going on with the codecs and the restricted formats, so someone posting a brief explanation would be nice.

---

### Post by ussndmac on 2010-09-03
I just got tired of fooling with Brasero since 8.04 and installed Gnome Baker.

It has never failed on any of 6 machines I have.

---

