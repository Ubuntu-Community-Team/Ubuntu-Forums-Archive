---
title: "How do you configure Wine?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by gshockxc on 2009-04-13
I downloaded Wine from the Repos but I'm not really sure what to do with it or how to use it.  I've done a few searches, but I haven't come up with much.  There are lots of question involving Wine, but nothing that I've found on how to configure it.  I don't have any help or Read Me files with t either.  
I'm running Kubuntu 8.10, KDE4, fresh install, and loving it so far.


Thanks.  Any help is much appreciated.

---

### Post by skymera on 2009-04-13
Applications > Wine > Configure

or terminal:

```
 winecfg 
```

To run a .exe using WINE

```
 wine /location/to/program.exe 
```

---

### Post by gshockxc on 2009-04-13
I don't have Wine listed in my Applications menu.  It's in the Lost & Found.  I clicked on Configure Wine, but I don't know what to do next.  I'm trying to figure out what's supposed to go where.  I copied all the files from the CD with the program I want to use.  It's just a 'Setup.exe' file, and several .CAB files, with some installation instructions for Windows.  Those I can read in OOo, but they aren't much use.  I navigated to the folder with the .exe file in the Configure Wine dashboard.  But then what?  How do I install the program?

When I run 'winecfg' in terminal, I get this: 
```

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disablingmixer

```

Thanks for the help.

---

### Post by skymera on 2009-04-13
What are you trying to install exactly?
To run the .exe open the terminal and type:

```
 wine filename.exe 
```
That will make Wine run the .exe program.

Sorry im being a bit waffly, it's 2:30 am :(

---

### Post by SunnyRabbiera on 2009-04-13
> **skymera said:**
> What are you trying to install exactly?
To run the .exe open the terminal and type:

```
 wine filename.exe 
```
That will make Wine run the .exe program.

Sorry im being a bit waffly, it's 2:30 am :(

you dont need the terminal with newer versions of wine, it installs just fine without the terminal.

---

### Post by skymera on 2009-04-13
I haven't used Wine since 0.9.46 back in late 2007, so I'm guessing it's changed a lot.

---

### Post by gshockxc on 2009-04-13
> **SunnyRabbiera said:**
> you dont need the terminal with newer versions of wine, it installs just fine without the terminal.

So how do you get it to install?  I'm sure it's a simple thing that I'm overlooking.  I navigated to the folder and added the setup.exe file to the Applications tab in wine.  But once that's done, what do I do with it.  It doesn't install anything.  When I close wine and bring it back up, that file is gone, and I have to add it again.

Also, installing from the terminal didn't work either.  

```

gshockxc@jarvis:~$ wine setup.exe
wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found

```

Thanks to both of you for your help.

This is software from NIST for thermal-fluid properties.

---

### Post by SunnyRabbiera on 2009-04-13
> **gshockxc said:**
> So how do you get it to install?  I'm sure it's a simple thing that I'm overlooking.  I navigated to the folder and added the setup.exe file to the Applications tab in wine.  But once that's done, what do I do with it.  It doesn't install anything.  When I close wine and bring it back up, that file is gone, and I have to add it again.

Also, installing from the terminal didn't work either.  

```

gshockxc@jarvis:~$ wine setup.exe
wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found

```

Thanks to both of you for your help.

This is software from NIST for thermal-fluid properties.

you dont need to do either, you can just go to where you downloaded your .exe and install it like you do in windows.
There should be no need for terminals or extra setup.
But be warned, Wine is not a universal solution and not all windows apps will work.
what is this application called?

---

### Post by gshockxc on 2009-04-13
It's just called NIST 12, ver 5.2.

It seems to work the way you suggested, but I didn't follow it through.  I couldn't quite make out the text so I quite before it went too far.
We'll see what happens.

---

### Post by gshockxc on 2009-04-13
> **SunnyRabbiera said:**
> you dont need to do either, you can just go to where you downloaded your .exe and install it like you do in windows.
There should be no need for terminals or extra setup.
But be warned, Wine is not a universal solution and not all windows apps will work.
what is this application called?

OK, now I understand the whole deal.  They make Kubuntu/Ubuntu too user friendly and you think it's going to be a lot harder than it really is.  Don't let me get lazy, now.  

That worked great.  The install icons were a bit hard to make out, but once it was done, the program worked great.  It's just a simple calculation tool for fluid properties.  It's really nothing more than a table of data with an interpolation routine.

Thanks again.

---

