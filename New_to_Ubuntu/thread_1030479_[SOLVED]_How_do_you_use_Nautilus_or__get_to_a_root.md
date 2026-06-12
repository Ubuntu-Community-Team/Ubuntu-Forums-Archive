---
title: "[SOLVED] How do you use Nautilus or  get to a root folder?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by jalehtor on 2009-01-04
I have a Sansa Fuze that is not working with Ubuntu, and one possible solution listed elsewhere was to make sure that the computer recognized it as a music player rather than as a storage device:

In the root folder of your sansa create a text file( If you are using GNOME use the following in nautilus: right click-> Create a document-> empty file. Now, name your file as .is_audio_player

Anyhow...how do I get to the "root folder" of my Sansa?
How do I get to nautilus? I've never used it before.

---

### Post by fooman on 2009-01-04
not sure about that sansa...but for my sansa (e250) i had to change the usb setting to "MSC mode" before ubuntu would recognize it.

check in the sansa's settings.

nautilus is the default file manager of ubuntu...go to places in the top panel and click "home folder"

that is nautilus.

---

### Post by northern lights on 2009-01-04
While I would try fooman's approach first, rather than anything you've read on some unverified source - a few clarifications:

I'm certain you've used nautilus quite a bit - it's gnome's standard filemanager. Whenever you click on any folder symlink or anything in the "Places" menu, nautilus opens.

The root folder of your player would just be the lowest level of it's data structure, i.e. "/".

---

### Post by jalehtor on 2009-01-04
> **fooman said:**
> not sure about that sansa...but for my sansa (e250) i had to change the usb setting to "MSC mode" before ubuntu would recognize it.

check in the sansa's settings.

nautilus is the default file manager of ubuntu...go to places in the top panel and click "home folder"

that is nautilus.

Switching to msc was almost the first thing I did. 

This is my first mp3. I have rhythmbox (RB) and Amarok installed. I downloaded a song into my regular music folder, then tried to download it into RB and Amarok. It went into RB, but Amarok said the mp3 could not be played. So I gave up on Amarok.

When I plug Sansa in, I get a 4.1 GB media icon on my desktop. It has a bunch of folders in there, including a music folder. I can drag the music from RB to the Music folder, but the music does not then download into my player. When I unplug the player, there's a refresh notice, but nothing's added.

So I was reading up on this, and one solution was to make certain that the computer recognized the Sansa as a music player, rather than as a storage device, which is what it looks like right now. Btw, there are a number of icons on the sansa thing, for instance, /media/disk/SYS_CONF.SYS. When I click on these I get a "There is no application installed for this file type" message.

I would really appreciate some help; I'm on the verge of returning the device and giving up on the whole thing altogether.

---

### Post by mc4man on 2009-01-04
> When I plug Sansa in, I get a 4.1 GB media icon on my desktop. It has a bunch of folders in there

Go to that window, right click on an empty area, -> create document-> empty file. Then rename it what ever your guide said to. Then right click on the icon -> unmount, unplug the player, plug it back in and see if it works.

..............

When you d, click on the 4.1gb icon the window that opens is the 'root' of the drive, the file your creating has to go there, not inside of any folder

---

### Post by jalehtor on 2009-01-04
> **mc4man said:**
> Go to that window, right click on an empty area, -> create document-> empty file. Then rename it what ever your guide said to. Then right click on the icon -> unmount, unplug the player, plug it back in and see if it works.

..............

When you d, click on the 4.1gb icon the window that opens is the 'root' of the drive, the file your creating has to go there, not inside of any folder

Thank you! I followed your instructions, created a file in the 4.1 icon, renamed it, unmounted, unplugged the Fuze, plugged it back in (btw, the file can not be seen when you do that) but no luck. 

In the sansa instructions for windows, it says to click on the Sansa's "internal memory." I have no idea what that means, but the one song I'm experimenting with won't move from the 4.1 icon to the memory of my device.

---

### Post by fooman on 2009-01-04
> **jalehtor said:**
> Switching to msc was almost the first thing I did. 

...I downloaded a song into my regular music folder, then tried to download it into RB and Amarok. 

....I can drag the music from RB to the Music folder

instead of downloading the song first from the "regular music folder" into RB, then from RB into the sansa...have you tried dragging it directly from the "regular music folder" into the sansa's music folder?

---

### Post by jalehtor on 2009-01-04
> **fooman said:**
> instead of downloading the song first from the "regular music folder" into RB, then from RB into the sansa...have you tried dragging it directly from the "regular music folder" into the sansa's music folder?

Tried it, no luck. Is there a very simple step that I am missing? Please forgive this stupid question, but this is my first mp3. After you drag the song into the Sansa music folder, what do you need to do to get it unto the device? Do you just wait, or is there a button to click?

---

### Post by fooman on 2009-01-04
the only thing i have ever done with my sansa (in ubuntu) is drag files from the music folder of my /home folder,  into the music folder of my sansa.

when i plug in the device, a box pops up telling me that "you have just inserted a digital audio player.  choose what application to launch.  select how to open the sansa e250..."

i close that box and open my home folder.  in the left hand column,  i will now have an entry for "sansa e250",  i click on that and on the right side i open the music folder of the sansa.

  then i open another instance of nautilus, and i open *ubuntu's* "music" folder where i keep all of my tunes.  i then simply drag the songs, albums, or folders from ubuntu's music folder into the music folder of the sansa.
when i do that...the sansa's screen says "writing".  it will say "writing" for a really long time if i let it....but it should only take a few minutes to write a few songs into the player (obviously give it more time if dragging an entire album or folder),  so after awhile...i simply unmount it and unplug the device.

when i start up the sansa,  the new songs are there.  been doing this way for a couple of years now (battery life is still great btw)...occasionally deleting the entire contents of the sansa's music folder and starting from scratch.  ...has not failed me yet. :)

i have always used it in MSC mode,  since ubuntu will not even recognize it while in MTP mode.

---

### Post by jalehtor on 2009-01-04
> **fooman said:**
> the only thing i have ever done with my sansa (in ubuntu) is drag files from the music folder of my /home folder,  into the music folder of my sansa.

when i plug in the device, a box pops up telling me that "you have just inserted a digital audio player.  choose what application to launch.  select how to open the sansa e250..."

i close that box and open my home folder.  in the left hand column,  i will now have an entry for "sansa e250",  i click on that and on the right side i open the music folder of the sansa.

  then i open another instance of nautilus, and i open *ubuntu's* "music" folder where i keep all of my tunes.  i then simply drag the songs, albums, or folders from ubuntu's music folder into the music folder of the sansa.
when i do that...the sansa's screen says "writing".  it will say "writing" for a really long time if i let it....but it should only take a few minutes to write a few songs into the player (obviously give it more time if dragging an entire album or folder),  so after awhile...i simply unmount it and unplug the device.

when i start up the sansa,  the new songs are there.  been doing this way for a couple of years now (battery life is still great btw)...occasionally deleting the entire contents of the sansa's music folder and starting from scratch.  ...has not failed me yet. :)

i have always used it in MSC mode,  since ubuntu will not even recognize it while in MTP mode.

Oh dear. None of this is happening for me.

 When I plug in the device, I don't get the "you have just inserted a digital audio player.  choose what application to launch.  select how to open the sansa e250..." I do have Fuze, of course. I just get the 4.1 GB Media screen.

When I open my home folder, there's no Sansa. 

When I assume that the music folder in the 4.1 GB Media thing is my Sansa folder, and drag a piece of music onto it, it doesn't say that it's writing...no message at all. 

Btw, if I put the player in MTP mode, the 4.1 GB Media icon does not show up. It only shows up with MSC.

I am very, very, very confused.

---

### Post by theozzlives on 2009-01-04
> **jalehtor said:**
> I have a Sansa Fuze that is not working with Ubuntu, and one possible solution listed elsewhere was to make sure that the computer recognized it as a music player rather than as a storage device:

In the root folder of your sansa create a text file( If you are using GNOME use the following in nautilus: right click-> Create a document-> empty file. Now, name your file as .is_audio_player

Anyhow...how do I get to the "root folder" of my Sansa?
How do I get to nautilus? I've never used it before.

alt+F2, then type:```
gksudo nautilus
```

---

### Post by abn91c on 2009-01-04
you need this to play mp3's   libxine1-ffmpeg

---

### Post by efexD on 2009-01-04
```
sudo nautilus
```

---

### Post by karlr42 on 2009-01-04
Please actually read the original post before you start posting commands. Just creates confusion.

---

### Post by jalehtor on 2009-01-04
> **abn91c said:**
> you need this to play mp3's   libxine1-ffmpeg

I'm really new to this. What is libxine1-ffmpeg? Is this something I need to type into the terminal?

---

### Post by fooman on 2009-01-04
type or copy/paste the following to install the package libxine1-ffmpeg (they are codecs needed to play mp3s):

```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by jalehtor on 2009-01-04
> **fooman said:**
> type or copy/paste the following to install the package libxine1-ffmpeg (they are codecs needed to play mp3s):

```
sudo apt-get install libxine1-ffmpeg
```

I did that...no results. If this helps at all: the icon that appears when I plug in the player is an msdos inode/directory folder. Its properties are Sansa Fuze etc.

Also, here's what you see when you click on the folder [IMG]http://i142.photobucket.com/albums/r113/jaletoran/Screenshot-disk-FileBrowser-1.png[/IMG]

---

### Post by mc4man on 2009-01-04
I don't have a sansa (only an older ipod) so can't help from experience.
what ubuntu are you using? ( i'm assuming intrepid 8.10

What's the complete name, model of your player? (maybe some searching will prove fruitful

---

### Post by jalehtor on 2009-01-04
> **mc4man said:**
> I don't have a sansa (only an older ipod) so can't help from experience.
what ubuntu are you using? ( i'm assuming intrepid 8.10

What's the complete name, model of your player? (maybe some searching will prove fruitful

I'm using Intrepid. The player is a Sansa Fuze, 4gb, model Vo2.01.09A.

---

### Post by mc4man on 2009-01-05
Didn't see much more than what you may have found. Looking in the current music players .fdi in hal info I see several sanso models listed. As far as Clip/Fuze there are just 3 vendor id's (maybe based on firmware version..?

Running this with your sansa plugged in should give the id. (there's another way to develop more info, this should suffice, (if it doesn't show anything use sudo lsusb

```
lsusb
```

sometimes this will give an accurate firmware version, sometimes not.
```

sudo lshw -C disk
```

---

### Post by fooman on 2009-01-05
that screenshot looks like its fine.  that is exactly how my sansa shows up except mine says "sansa e250" where your's says "4.1 gb media"....ubuntu does recognize it,  so thats a good sign.

when the window is open as in your screenshot...open the music folder of the sansa.

then open your /home/jaleh/Music folder in another window.

*left*-click (and hold) on a song in your /Music folder, then *drag* it over to the music folder of the sansa and release.

when i do that,  the sansa says "writing" on its screen and the song(s) show up in the music folder of the sansa....after a minute or 2.  the song(s) are written onto the sansa.  i unmount it and its ready to play.

sorry,  i do not understand why that does not work for you.

---

### Post by jalehtor on 2009-01-05
I'm glad to hear that ubuntu recognizes it. However...I left click and drag and...nothing. The song does not make it onto the device. I have to go teach now, and when I get home I'm going to try another song. Thanks and have a great day.

---

### Post by jalehtor on 2009-01-05
Oh, and I just discovered something interesting (or maybe not)...when my kids plug their ipods in, I get a screen telling me that a device has been installed. I don't get anything like that with my player...I do get the icon. Also, my daughter's ipod is showing as a music player on the left side of rhythmbox. Sansa is not.

---

### Post by northern lights on 2009-01-06
> **efeXor said:**
> ```
sudo nautilus
```
Please _never_ use *sudo* with graphical applications (You may use it yourself of course, but please don't suggest it as an answer to a support request).

If you need to run graphical applications as root, use either *gksu* or *gksudo* under gnome and *kdesu* under KDE.

For further information, read [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by jalehtor on 2009-01-07
I got on the Sansa Fuze site, and a very nice poster found the solution to my problem. I'm posting it here with his leave in case it helps someone else: :D

OK - here's how to do it in RhythmBox...

 

First, the bit of magic that lets RB hook your Fuze. 

Plug the Fuze in. Click the '4.1GB Media' desktop icon so you have a filemanager on the top directory in the Fuze. Right click and 'Create Document->empty file'. Rename the file .is_audio_player (the leading . is important).

 

Next, how to rip CDs in RB

I'm going to tell you how to rip to Ogg Vorbis format, because (1) you don't have to install an MP3 encoder, and (2) the tagging is probably easier (RB rips MP3 files with ID3v2.4 tags which Fuze doesn't understand). Ogg is not recognised by some players, but if you are using your Fuze, it will be fine. If you want to use MP3 for compatibility with other players, we'll need to talk some more...

 

We need to tell RB to use the right file naming for the Fuze. You only need to do this once.

    * Start RB.
    * Go to  Edit->Preferences->Music, and set 'Preferred Format' to CD Quality, Lossy (.oga type).
    * Now click the Edit button.
    * Choose CD Quality, Lossy and click the Edit button.
    * In the window that opens, change 'File extension:' from oga to ogg.The Fuze doesn't understand .oga as a file type.
    * Click 'Close' on all the preference panels.
    * Go to  Edit->Preferences->Music
    * Fill in 'Music files are placed in:' with some sensible location like Music in your home directory.
    * Click 'Close'
    * Restart RB

Now we can rip stuff

    * Put a CD in the drive. It should show up under Devices in RB's left panel.
    * Right click the CD icon, and  choose 'Extract to Library'
    * A progress bar should appear on the bottom right of RB.
    * If you select Music under Library in RB's left panel, you should see tracks start to appear.
    * When the prgress bar goes, it's ripped...

Put it on the Fuze

    * With Music highlighted under Library, you can drag the album or artist or an individual track from the right panel to the Fuze '4.1 GB' icon in RB's left panel.
    * Once the copying is done, right click the Fuze icon and choose Eject.
    * Wait till its finished unmounting & unplug the Fuze.

---

