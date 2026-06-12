---
title: "Two simple questions I can't find the answers for."
date: 2009-02-14
forum: New to Ubuntu
---

### Post by drizzintahl on 2009-02-14
First off, I need to set:

> aoss wine /path-to-program/Ventrilo.exe

aoss wine /path-to-program/WoW.exe

but I can't figure out what the path would be, how many // I need, and where to start it from.  I tried

> aoss wine /home/drizzintahl/.wine/dosdevices/c:/Program Files/Ventrilo/ventrilo.exe

And some variations, but I know I'm doing it wrong.  

Next up, I have a USB headset, and double clicking the volume icon brings up a large list of different outputs, but when I select Logitech USB Headset, it doesn't let me set it as default, just turn it up and down but nothing comes through it.

thanks a ton and sorry for ze newbish questions, I'll learn this in no time.

---

### Post by mikewhatever on 2009-02-14
Type <locate ventrilo.exe> to get the path.

---

### Post by hyperyoda on 2009-02-14
> **drizzintahl said:**
> First off, I need to set:



but I can't figure out what the path would be, how many // I need, and where to start it from.  I tried



And some variations, but I know I'm doing it wrong.  

Next up, I have a USB headset, and double clicking the volume icon brings up a large list of different outputs, but when I select Logitech USB Headset, it doesn't let me set it as default, just turn it up and down but nothing comes through it.

thanks a ton and sorry for ze newbish questions, I'll learn this in no time.

Try:

$ aoss wine C:\Program Files\Ventrilo\ventrilo.exe

Zach

---

### Post by hyper_ch on 2009-02-14
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by drizzintahl on 2009-02-14
> drizzintahl@GPenguin:~$ $ aoss wine C:\Program Files\Ventrilo\ventrilo.exe
bash: $: command not found
drizzintahl@GPenguin:~$ aoss wine C:\Program Files\Ventrilo\ventrilo.exe
wine: cannot find 'C:Program'
drizzintahl@GPenguin:~$ 

> drizzintahl@GPenguin:~$ locate ventrilo.exe
drizzintahl@GPenguin:~$ <locate ventrilo.exe>
bash: syntax error near unexpected token `newline'
drizzintahl@GPenguin:~$ 


Thanks for the replies but this is what I have so far.

---

### Post by Old *ix Geek on 2009-02-14
One problem is that you're not quoting the pathname--because it has windoze-style naming, i.e., spaces!, you must quote it:

```
$ aoss wine "C:\Program Files\Ventrilo\ventrilo.exe"
```

---

### Post by mikewhatever on 2009-02-14
If you don't get any output from <locate ventrilo...> NO BRACKETS, then perhaps it should be <locate Ventrilo> or locate ventrillo, I don't know. The point it that spelling, including capitalization, does matter.

---

### Post by drizzintahl on 2009-02-14
Ah thank you for all the help, and sorry for the few mistakes with title and posting. 

Cheers = )

---

### Post by yther on 2009-02-14
If it was just installed, the "locate" database may not know where it is yet.  Try this:

```
sudo updatedb
locate -i ventrilo
```

The "updatedb" tells the system to scan your drives and update the database of files.  It has to run as root, thus the "sudo" bit.  The "-i" switch to **locate** says to ignore case, so it would find "VentriLO" or "ventrilo".

---

### Post by Bölvaður on 2009-02-14
for your usb problems I advice you to use pulse audio (System &#8594; Preferences &#8594; Sound and put everything on pulse audio)
then install a package called "padevchooser" aka pulse audio device chooser. get it form synaptic (System &#8594; Administrator &#8594; Synaptic Package Manager)

It may be a little confusing but you turn on the program from Applications &#8594; Sound&Video, and click on the  icon that will appear in your... open tasks area on your panel... or what ever it is called.. if you know what I mean. by default it is next to the clock.

Um there you pick Volume control and are able to redirect any program to any output device that pulse can sent to. So you can have a film playing in your 7.1 and playing a game in your headphone...

---

### Post by Tony Flury on 2009-02-14
Bölvaður ; I hope you are right that the OPs problems can be solved by using Pulse. I was a tad suprised though - because I had no-end of sound problems until I removed pulse from my system.

drizzintahl : if setting everything to Pulse does not work - it might be that doing the opposite, and then removing pulse completely might be better for you.

in my experience (and that of a few others I have seen post here) Pulse Audio can be a bit hit and miss when it comes to working correctly.

to remove Pulse - should you need to : 

```

sudo apt-get remove pulse-audio

```
but try Bölvaður suggestion first.

---

### Post by Bölvaður on 2009-02-14
Pulse was bad in 8.04. I helped a guy yesterday to switch to alsa, and then everything was fine.
But pulse in 8.10 seems to be quite good. Must because of some more basic package perhaps, Im not too bothered to find out why.

---

