---
title: "skype"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by bogainey on 2009-01-11
In tying to find an answer to my recording problem, (That no one seems to have a clue), I keep running in to the term/word, "Skype". What is it, do I need it to record my voice,and where do I go to get it? I have looked it up under Synaptic, and I have looked it up under Add/Remove. I don't find it anywhere.
Thanks

---

### Post by TeoBigusGeekus on 2009-01-11
[http://www.skype.com/intl/en/]("http://www.skype.com/intl/en/")

However, Skype is not used for recording purposes but for Internet (video) calls.

---

### Post by moody_mark on 2009-01-11
Hi, are you after simply recording from an audio input? What are you using , ubuntu, xubuntu, kubuntu? Under the "Applications --> Muiltimedia" menu you should find a sound recorder there

---

### Post by minsf on 2009-01-11
Skype is probably not what you need (it's like the yahoo/msn messenger in windows- voice and video conversations). But you may want to know that the reason you don't see it in synaptics is that you need to enable the medibuntu repository. that is, first you need to go to System>Software Sources and put medibuntu in the Third-Party tag. only then use apt-get or synaptics. Detailed instructions can be found here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

However, like i said, skype is probably not what you want. If the existing sound recorded is not what you need, maybe try audacity or mplayer. i'm not so sure about those, just wanted to give you a little tip about repositories. 

to get more specific help, you may want to let us know what exactly you are trying to record. are you trying to record streaming?

---

### Post by bogainey on 2009-01-11
I would like to thank the three people who responded to my most recent thread: minsf, moodymark and TeoBigusGeekus.
I have spent and entire week trying to find an answer to my recording problem and you folks are giving me hope finally that someone cares.
I have had two other responses to two other threads but with no follow up.
Thanks for explaining Skype to me.
I am very new to the computer world and admitting that I am lost and trying to learn. If someone wants to call me an idiot, simple minded or whatever, I don't care. Call me what you want, just give me some answers!
I am on Ubuntu 8.04. At least thats what I believe. I went to applications but found no multimedia under Applications or any listing in Applications.
I am trying to record my voice from the microphone that I plugged in to the port to my computer. As I have stated in previous threads, everything seems to work. I get sound out of every test I run under sound preference except for mic. I have checked all levels at all areas that I know to go to. No mutes
I've tried downloading Audacity 1.3.5 to my desktop and when I go to open it it gives me this: Dependency is not satisfiable: libasound2. I checked and libasound2 is installed. Don't know what to do there! If I go to the sound/record under Applications>Sound, then I get: Subclass did not speciy output size and also: Internal Data Flow Error. So I'm lost there as well!!
I can't give up because there is a job possibility if I can get this worked out and start recording my voice and sending it off in e-mails .
If anyone out there can help I will greatly appreciate it .
Thanks,
Bo

---

### Post by spiderbatdad on 2009-01-11
Sound Recoder comes pre-installed with 8.04. Applications>>Sound & Video>>Sound Recorder.

---

### Post by llamakc on 2009-01-11
The Sound Recorder program is in the menu path:

Applications > Sound & Video > Sound Recorder

You can start it from the "run" dialog (press ALT+F2) and type gnome-sound-recorder

HTH

---

### Post by minsf on 2009-01-12
guys, please notice that he said that the default sound recorder does NOT work for him:
> 
If I go to the sound/record under Applications>Sound, then I get: Subclass did not speciy output size and also: Internal Data Flow Error. So I'm lost there as well!!

Bo,

1. dont give up! you'll find the solution. just be patient.

2. regarding the default sound recorder (that is, Application>Sound&Video>SoundRecorder). let's try to open it from the terminal. this way the errors are going to be sent to the terminal, so you can cut and paste them here, and we can help. here's how to do it:
a) open a terminal: go to Applications>Accessories>Terminal
by the way, the terminal is a very important tool, and you can learn more about it via the following beginer's link: [www.linuxcommand.org](www.linuxcommand.org))
b) in the terminal type
```
gnome-sound-recorder
```
and "enter"
c) the sound recorder will be opened, and if you get any error in the terminal, cut and paste it here

3) regarding audacity:
> 
I've tried downloading Audacity 1.3.5 to my desktop and when I go to open it it gives me this: Dependency is not satisfiable: libasound2. I checked and libasound2 is installed. 

it seems that the libasound2 package that is installed on your system is broken, and since the audacity depends on it, you get an error. so let's try to reinstall libasound2, and see what happens. in the terminal type
```
sudo apt-get install --reinstall libasound2
```
it'll ask you for your password, and then
it will remove the package and install the newest version of libasound2. in the process, it asks for your confirmation, so enter "y". 
please post the output that you get (so that we know if it was successful or if libasound2 had any broken dependency (libc6?)

---

### Post by moody_mark on 2009-01-12
> **bogainey said:**
> I am on Ubuntu 8.04. At least thats what I believe. I went to applications but found no multimedia under Applications or any listing in Applications.


Sorry, that was my fault for misleading you there, in Ubuntu as the others have said its "Applications --> Sound and Video --> Sound recorder"

> 
If I go to the sound/record under Applications>Sound, then I get: Subclass did not speciy output size and also: Internal Data Flow Error. 


Looks like a bug has been filed under this

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/229168]("http://https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/229168")

I would try what the others have said above first and try to run it from the command line. If your not familiar with command line, dont be too scared of it, many people are unfamiliar. In Linux you can run an application from the desktop or just from the command line. A lot of time if you run from the command line you can get extra debugging and lots of useful info which you can post into the forums for help.

Its a bit of a long shot but have you installed the ubuntu-restricted-extras packages? I always have and never used my sound until after so perhaps theres some drivers included in there.

Also heres a couple of good posts I noticed on the forums here;
[URL="http:// http://ubuntuforums.org/showthread.php?t=655207"]
http://ubuntuforums.org/showthread.php?t=655207[/URL] - tutorial of the week (good to bookmark)
[URL="http://ubuntuforums.org/showthread.php?t=766683"]
http://ubuntuforums.org/showthread.php?t=766683[/URL] - comprehensive multimedia (might have your answer here)

Hope this helps :-)

---

### Post by Captain_tux on 2009-01-12
> **bogainey said:**
> In tying to find an answer to my recording problem, (That no one seems to have a clue), I keep running in to the term/word, "Skype". What is it, do I need it to record my voice,and where do I go to get it? I have looked it up under Synaptic, and I have looked it up under Add/Remove. I don't find it anywhere.
Thanks

Have you tried Googling for this mysterious "Skype?"

---

### Post by bogainey on 2009-01-12
Thanks again to: "minsf" and to "moody_mark" for your input. 
This is embarrassing to say but I don't know how to cut and paste from one file or site to another. I need to learn how to do that to! Can you give me directions, step by step. It's like I just learned how to crawl. Hopefully with the help from you folks, soon I might be walking.
Thanks to all!
Bo

---

### Post by minsf on 2009-01-12
bo, 
A) when you see a text that you want to copy, like an error message in the terminal, point your mouse to the beginning of the text, right click and hold that click. then grab your mouse to the end of the text that you like (while still holding the right click). this should mark the text.
B) now press CTRL+C to copy the text to the memory (to the clipboard)
C) go to the internet browser and click the place where you want to paste it.
D) use CTRL+V to output the text from the memory to the new place (=paste the text).

By the way, in most situations, you can skip step B, and instead of step D press the right and the left buttons of your mouse simultanously (or your middle button, if you have 3 button mouse, or your weel if you have one)

Also, please have a look at the help files that come with your ubuntu: simply right click the question-mark on the top panel. in particular, check "new to ubuntu?" and in it check "bsic computer skills"

cheers:)

---

### Post by bogainey on 2009-01-15
To: "minsf" and "moody_mark": 
I went to the terminal and typed in: gnome-sound-record and here is what it said: " error: unexpected identifier 'colorize_ scrollbar', expected character '}'

I don't know what that means but I'm guessing that means I've got a booger in there somewhere, right?
Now where ?
Sorry if I'm bugging you folks but you've been a big help and I've regained confidence that I can someday start recording my voice.
Thanks,
Bo

---

### Post by minsf on 2009-01-15
Bo, I have a few question so that we can help you more:

1. have you already tried to reinstall libasound2 as i suggested in post #8 part (3)?
2. how do you plug in the mic? through a USB port?
3. do you know what kind of microphone it is? (name of vendor, model, etc.)
4. please go to the terminal (applications>accessories>terminal) and enter the following: ```
sudo lshw -short | less 
```
you will be asked for your password and then you'll get some output. please post here the output (that is, cut and paste what you get from the terminal in here). 
if the output is too long to fit into the terminal, you will need to scroll down with the arrow keys to get the rest of the output.

---

