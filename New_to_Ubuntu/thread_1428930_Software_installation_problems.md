---
title: "Software installation problems"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by cherryp on 2010-03-13
Hello, 
I'm an absolute beginner to Linux and need a lot of hand holding. I have successfully downloaded Ubuntu 9.10 and installed it. At present, I need help with installing Flash. Although there are many threads here that address this issue, I have not found one which has worked for the user. 

I listen to a jazz station which streams its music. I am able to listen to the station under Windows but under Ubuntu, it doesn't work. When I invoke the url "jazz.fm' directly, I get a message about a missing Flash plugin. If I invoke the url under Rythmbox, I get a message about a missing plugin and the search fails with the message 'no packages with the requested plugin found. Requested plugins are text/html decoder.. 

Is there something definitive with specific instructions for installing Flash?
 
Is there one way in which software products can be installed successfully with step by step instructions directed toward a beginner like myself? ? 

Being Open Source, understandably there are many ways to install software but there must be one tried and tested way which works for everyone?

Any help or direction will be very much appreciated.

Thanks

---

### Post by dmillard10 on 2010-03-13
Has this been tried?

1. Open a terminal window (Applications -> Accessories -> Terminal)
2. Type "sudo aptitude install flashplugin-nonfree"
3. Press enter
4. Enter your password (it won't echo to the screen, this is normal)
5. Respond "y" to any prompts
6. Try and load the stream through a web browser

Sorry if this is **too** basic or detailed, when I first started I needed this type of instruction.

Hope this helps.

---

### Post by cherryp on 2010-03-13
Thanks for the response dmillard10. I attempted that command you gave me and received a message "could not get lock /var/lib/dpkg/lock resource temporarily unavailable"
"unable to lock the administration directory. is another process using it?"

I will get out and start again in case something I did previously is holding on to the resource.

---

### Post by dmillard10 on 2010-03-13
That error pops up when more than one package manager is open.  If you haven't logged out already, try closing any of the following: synaptic, aptitude or Ubuntu Software Center.

---

### Post by cherryp on 2010-03-13
I tried it again and this time the message was it couldn't find 'flashplugin-nonfree'.

---

### Post by shabs on 2010-03-13
Are you sure the package manager is not running and also if you did type in 'sudo' before the apt-get?

Bah.. ignore this message :)

---

### Post by cherryp on 2010-03-13
Yes, I only had the terminal session open and I did prefix the command with 'sudo'.

---

### Post by dmillard10 on 2010-03-13
> **cherryp said:**
> I tried it again and this time the message was it couldn't find 'flashplugin-nonfree'.

Try going to System -> Administration -> Software Sources.

In the tab "Ubuntu Software", check the box labeled "(multiverse)".

---

### Post by cherryp on 2010-03-13
that box was already checked. the only one not checked is 'source code'.

---

### Post by sandyd on 2010-03-13
```

sudo apt-get install flashplugin-installer

```
flashplugin-nonfree is depreciated IMO.

---

### Post by sandyd on 2010-03-13
oops.
double posted.

---

### Post by cherryp on 2010-03-13
Thank You Very Much Carlee!!It worked and I am able to listen to the station by just clicking on the station! 
Appreciate everyone's help here. 
Is this how ALL products are installed? 
When I invoked the url from Rythmbox, I received a message "your Gstreamer installation is missing a plugin" would I install the missing plugin the same way?

---

### Post by sandyd on 2010-03-13
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

sudo apt-get install libdvdcss2 libdvdread4 libavcodec-unstripped-52 libavdevice-unstripped-52 libavfilter-unstripped-0 libavformat-unstripped-52 libswscale-unstripped-0 libpostproc-unstripped-51 ffmpeg lame libxine1-ffmpeg libamrwb3 libamrnb3 faac faad libquicktime1[FONT=Verdana] [/FONT]gstreamer0.10-ffmpeg gstreamer0.10-nice gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ubuntu-restricted-extras


```
32 bit
```

sudo apt-get install w32codecs
```

64-bit
```

sudo apt-get install w64codecs
```

---

### Post by cherryp on 2010-03-13
Thanks a lot for the help Carlee! Just what I needed.

What do these commands do, where are they documented? Curious.

Thanks again

---

### Post by sandyd on 2010-03-16
> **cherryp said:**
> Thanks a lot for the help Carlee! Just what I needed.

What do these commands do, where are they documented? Curious.

Thanks again

Hmm... their documented somewhere... in my brain...

but then again, my brain wouldn't store EVERYTHING right?

so...
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

the rest are just codecs I pulled out of my brain.

---

### Post by andrewthomas on 2010-03-16
> **cherryp said:**
> Thanks a lot for the help Carlee! Just what I needed.

What do these commands do, where are they documented? Curious.

Thanks again

The multimedia how-to could also be of use if you have any other problems.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by gordintoronto on 2010-03-16
> **cherryp said:**
> 
Is this how ALL products are installed? 


No!  I usually use Administration/Synaptic Package Manager. It has a nice search function to sort through the 27,000 available packages.

When giving help, it is easier to tell a person to copy/paste something into a terminal command line, than to say, "start this program, click here, enter this, click there..."  It's also a lot more foolproof.

But the normal way to install software is through the Synaptic.

Did you install the "restricted extras"?

---

### Post by cherryp on 2010-03-17
Thank you very much all. You have given me lots to read and understand. I am up and running and can now sit back, read and digest all this info. There's a lot of new terminology and applications to get to know and the whole architecture is very new too.

Thanks again for the help.

cherry

---

### Post by 3rdalbum on 2010-03-18
If the radio station website needs Flash, then that means you can only listen to it in your web browser, not in Rhythmbox. Unless it has a link to another stream so you can listen in a music player.

---

### Post by cherryp on 2010-03-21
Thanks! Using the browser is good for now. Lots of learning and catching up to do on other stuff.

---

