---
title: "How to answer dpkg-reconfigure questions?"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Mariane on 2010-06-04
Hi, 

I've just got a new screen and I am trying to follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

However I cannot run dpkg-reconfigure xserver-xorg. 
Every time I try it asks a few questions to which I answer by pressing return, and then it asks me which keyboard I have but gives me nowhere to answer. 

I thing I should type pc104 or pc105 but where??? There is no text field, the options cannot be selected with the mouse, and blindly typing pc104 and then return is ignored. 

How do I enter the answer to dpkg questions, please? 

Mariane

---

### Post by bodhi.zazen on 2010-06-04
xorg and dpkg-reconfigure xserver-xorg are depreciated, has been for some time now.

What hardware do you have and what problem is occurring ?

---

### Post by Mariane on 2010-06-04
I have an nVidia card and 2 screens. The one on my laptop, which works except I cannot set it to be brighter, and a new Dell screen. 

I have connected the new screen to the laptop and expectantly rebooted but the new screen is simply ignored. 

I don't really care if the new screen acts as an appendage of the laptop screen or duplicates the laptop screen or simply takes over when the laptop is booted with the new screen plugged in. All I want is to be able to see something on it. 

Mariane

---

### Post by Bachstelze on 2010-06-04
The nvidia control panel (under System > Administration) should let you configure that. No need for editing xorg.conf manually (or via debconf).

---

### Post by bodhi.zazen on 2010-06-04
Or from the command line user:

```
gksu nvidia-settings
```

---

### Post by Mariane on 2010-06-04
Thanks for the advice. 

The first option, clone the screen, only partially works. I see the Desktop icons but only  icons in the bottom bar (I'm using kde): The 'K' to start things, the home folder and the Konqueror folder. 

I launched vlc and it only displayed on my laptop screen. 

So I'll try another option now, see if it works better. 

Mariane

---

### Post by Mariane on 2010-06-04
Under Gnome I see no icons at all. 

I was at:
"Separate X screen"

I am now going to try:
"TwinView"

Mariane

---

### Post by Mariane on 2010-06-04
This works both under gnome and under kde. 
Only one problem: If I double-click on vlc to set it to full screen it jumps back to the laptop screen. 

One way round this: by clicking on the edge while holding "alt" it is possible to grab a window by its edge - any edge. So I can drag it around and resize it to be bigger than the screen. Thus I can adjust it to "full screen". 

If you know of a better way, I'll be back tomorrow to read you, now I am going to enjoy my new screen by watching a movie. 

Thanks to you all. 

Mariane

---

### Post by Mariane on 2010-06-04
One last word for tonight: 

We got far from my original question. Anyone knows the answer to that? 

Mariane

---

### Post by RTrev on 2010-06-04
Back when I had two monitors (one blew up) I recall that there was a way to tell VLC which monitor to use for full screen.  Dig through the vlcrc config file and you may find something that looks right.

Ah, here it is:

```

# Screen for fullscreen mode. (integer)
#x11-xineramascreen=-1

```

Not sure why mine is set to -1.  Perhaps because it's irrelevant when only one screen is present.  Uncomment the second line and play with values like 0 or 1 or 2 and I'll bet it will work.  Hopefully. <g>

---

### Post by Mariane on 2010-06-04
Thank you. My monitors are labelled 0 and 1. Where do I find this file, please? 

Mariane

---

### Post by RTrev on 2010-06-04
> **Mariane said:**
> Thank you. My monitors are labelled 0 and 1. Where do I find this file, please? 

Mariane

You're most welcome.  Look in your home directory for a hidden directory file called .config -- you'll have to enable viewing hidden files in your file manager (it's usually under the "View" menu.. I don't use KDE so am not sure.)

In the .config directory, there should be a vlc directory.

In the vlc directory should be the vlcrc file.

---

### Post by Mariane on 2010-06-04
This is where it should be according to: 
[http://www.videolan.org/support/faq.html](http://www.videolan.org/support/faq.html)

But there is no vlc folder in /home/tux/.config

I was looking for it with kwrite, a kde text editor. 
By default it doesn't show hidden directories. I do file>open and browse to the directory which contains the hidden directory. Then in the location text field I type a '.' and it shows all directories which have names starting with a '.' ie all hidden directories. 

Mariane

---

### Post by RTrev on 2010-06-04
> **Mariane said:**
> This is where it should be according to: 
[http://www.videolan.org/support/faq.html](http://www.videolan.org/support/faq.html)

But there is no vlc folder in /home/tux/.config

I was looking for it with kwrite, a kde text editor. 
By default it doesn't show hidden directories. I do file>open and browse to the directory which contains the hidden directory. Then in the location text field I type a '.' and it shows all directories which have names starting with a '.' ie all hidden directories. 

Mariane

Hmm.  Not sure what to tell you.  That's where it is under both Gnome and LXDE.

```

bob@lub32:~$ cd .config
bob@lub32:~/.config$ cd vlc
bob@lub32:~/.config/vlc$ ls
vlc-qt-interface.conf  vlcrc

```

You can try to locate the file:

```

locate -e vlcrc

```

Anybody out there using VLC under Kubuntu?

Sorry!
Bob

---

### Post by RTrev on 2010-06-04
Oh, I just noticed something in that link you sent:

> If you modify the available options in VLC and save the new configuration, then a configuration file will be created in your user directory.

Maybe the file is only there after you edit something in the preferences for VLC?  Why not try that?  Then you'll have the file, hopefully.  I just assumed it was created on first run, like most such files.. but not according to this quote.

---

### Post by EssexEagle on 2010-06-04
> **RTrev said:**
> Anybody out there using VLC under Kubuntu?

Yep, and I get exactly the same as you:
```
$ cd ~/.config/vlc/
$ ls
vlc-qt-interface.conf  vlcrc
```

And the file vlcrc contains the lines
```
# Screen for fullscreen mode. (integer)
#x11-xineramascreen=-1
```
as expected.

So KDE seems to be the same as other desktop environments.  Looks like you might have to edit some options in VLC first, as RTrev said.

---

### Post by RTrev on 2010-06-04
Roger that, EssexEagle, and thanks.  RTrev returning to base. :)

We'll find out if it works tomorrow after the movie. :popcorn:

---

### Post by RTrev on 2010-06-04
Just noticed one other thing that might be helpful.  There are at least three different lines to control which screen is used, depending on the type of video being used.  I'm a bit over my head with which is which, so maybe try each one until one of them works.  Remember to exit VLC, edit the file, then re-start VLC.  There ones I see are:

```

# Screen for fullscreen mode. (integer)
#x11-xineramascreen=-1

```

```

# Screen for fullscreen mode. (integer)
#xvideo-xineramascreen=-1

```

```

# Screen for fullscreen mode. (integer)
#glx-xineramascreen=-1

```

It's been so long, I'm afraid I don't remember which I used when I was using TwinView.

---

### Post by Mariane on 2010-06-07
Setting a preference has created the file. 
But the modifications I make to it don't stick. 

I set all 3 instances of "Screen for fullscreen mode" to 1 and saved. 

Double-clicking on vlc, open on the second monitor, sent it back to the first one and when I looked at my vlcrc fil again I got the message "The file has been modified by another program, what do you want to do? Overwrite, reload, ignore, cancel". 

I tried the same thing with -1 values instead of 1 and it was also reverted to 0.

The permissions for the file is:
-rw-r--r-- 1

Mariane

---

### Post by RTrev on 2010-06-07
> **Mariane said:**
> Setting a preference has created the file. 
But the modifications I make to it don't stick. 

I set all 3 instances of "Screen for fullscreen mode" to 1 and saved. 

Double-clicking on vlc, open on the second monitor, sent it back to the first one and when I looked at my vlcrc fil again I got the message "The file has been modified by another program, what do you want to do? Overwrite, reload, ignore, cancel". 

I tried the same thing with -1 values instead of 1 and it was also reverted to 0.

The permissions for the file is:
-rw-r--r-- 1

Mariane

That message about modification by another program might mean that you're trying to edit the file without first exiting completely from VLC.  Are you closing VLC, editing the file with your editor, saving the file, exiting from the editor, and then starting VLC?

From the sound of it, the editor is seeing that VLC has changed the file after the editor opened it, and asking what you want to do.  Possible?

I can tell you that once I got this set, it worked great.  No matter where VLC was on any screen, full-screen mode would make it instantly jump to the correct monitor.

---

### Post by Mariane on 2010-06-07
I set the owner to root, to no avail. I also renamed the "cache" directory to "cache.save" but vlc simply created a new cache directory. 

Now the vlcrc file is not modified any more but vlc still goes fullscreen to monitor 0. Whatever I write in this file. 

I wondered if maybe the new monitor cannot support vlc in fullscreen mode? It's a Dell, they are supposed to be quite good, but who knows? How could I test this? 

Mariane

---

### Post by RTrev on 2010-06-07
I think we're having two different conversations here.  Perhaps someone else can help.

---

### Post by Mariane on 2010-06-07
Yes, the thread got out of sync with the title. If you know the answer to the original question I'm still interested, even if I don't use it now i might come in handy sometimes to know that. 

Mariane

---

