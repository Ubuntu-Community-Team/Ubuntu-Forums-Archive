---
title: "sound preferences"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by wstay on 2009-01-27
I would like to change the default sound under Sound Preferences but is unable to do so.
Is there a way to do it?
Can someone please help.

---

### Post by stoogiebuncho on 2009-02-01
What is preventing you from changing the sound?

What I do is go to System > Preferences > Sound and go to the "Sounds" Tab.  To change a sound, I click on the drop down box and select "Select Sound File".

If that's not working, maybe the sound you want to use is not the proper format.  What type of sound file is it?

---

### Post by wstay on 2009-02-01
> **stoogiebuncho said:**
> What is preventing you from changing the sound?

What I do is go to System > Preferences > Sound and go to the "Sounds" Tab.  To change a sound, I click on the drop down box and select "Select Sound File".

If that's not working, maybe the sound you want to use is not the proper format.  What type of sound file is it?

I go to System > Preferences > Sound and go to the "Sounds" Tab and the only drop down box I have is for the Sound Theme. And when I click on the down arrow there isn't anything for me to select. The only wording I can see in the Sound Theme box is Ubuntu. 
There isn't any drop down box for "Select Sound File" anywhere on the Sound Preferences page.

---

### Post by stoogiebuncho on 2009-02-01
What happens when you open the Sound Preferences from a terminal?  Do you get any error messages?

```
gnome-sound-properties
```

Also, if you could upload a screenshot of your sound settings, that might be helpful as well

---

### Post by wstay on 2009-02-03
> **stoogiebuncho said:**
> What happens when you open the Sound Preferences from a terminal?  Do you get any error messages?

```
gnome-sound-properties
```

Also, if you could upload a screenshot of your sound settings, that might be helpful as well

My Sound Preferences opens alright from a terminal.
Please see attachment and hope you can help.

---

### Post by wstay on 2009-02-08
> **stoogiebuncho said:**
> What is preventing you from changing the sound?

What I do is go to System > Preferences > Sound and go to the "Sounds" Tab.  To change a sound, I click on the drop down box and select "Select Sound File".

So you see that there isn't any drop down box for "Select Sound File".
Is there a way to install or to change the Sound Preferences properties to include this?

---

### Post by stoogiebuncho on 2009-02-08
I'm not able to open that screenshot.

Are you running 8.10?

---

### Post by wstay on 2009-02-08
> **stoogiebuncho said:**
> I'm not able to open that screenshot.

Are you running 8.10?

Yes I am running Ubuntu 8.10.
I save the attachment "gnome-sound-properties tar.gz" to my Desktop and it opens ok.
Can you please try again.

---

### Post by stoogiebuncho on 2009-02-08
Ok.  I'm still on 8.04, and I think the sound preferences thing is different between the two versions, which is probably why my advice isn't helping you.

You might check out this thread, as it seems it might apply to you:
[http://ubuntuforums.org/showthread.php?p=6573353]("http://ubuntuforums.org/showthread.php?p=6573353")

As for your screenshot, it still doesn't work for me.  It's a file with no extention and when I try to open it in various image viewers it says the format is not recognized.

---

### Post by wstay on 2009-02-09
> **stoogiebuncho said:**
> Ok.  I'm still on 8.04, and I think the sound preferences thing is different between the two versions, which is probably why my advice isn't helping you.

You might check out this thread, as it seems it might apply to you:
[http://ubuntuforums.org/showthread.php?p=6573353]("http://ubuntuforums.org/showthread.php?p=6573353")

As for your screenshot, it still doesn't work for me.  It's a file with no extention and when I try to open it in various image viewers it says the format is not recognized.

I found this file 'gnome-sound-properties' in /usr/bin and is an executable (application/x-executable) file which I find that it cannot be send to you in this format. So I created an archive file from it and send to you as an attachment as a gnome-sound-properties.tar.gz file. So the extension should be .tar.gz. And when I saved it to my Desktop and double click on it, it opened alright. I don't know how to create a screenshot with other extension. May be you can show me how?

---

### Post by stoogiebuncho on 2009-02-09
Actually, to take a screenshot, all you need to do is press the Print Screen button.  It will take a picture of whatever is on your screen at that second (so be sure to have the sound preferences window open), and save it as a .png file on your desktop.

Did you find any helpful information in that other thread I linked to?

---

### Post by wstay on 2009-02-09
> **stoogiebuncho said:**
> Actually, to take a screenshot, all you need to do is press the Print Screen button.  It will take a picture of whatever is on your screen at that second (so be sure to have the sound preferences window open), and save it as a .png file on your desktop.

Did you find any helpful information in that other thread I linked to?

Thanks.
I found the answer in the thread you gave me.
And attach here is a screenshot of my sound properties file.

---

### Post by wstay on 2009-02-14
> **stoogiebuncho said:**
> Actually, to take a screenshot, all you need to do is press the Print Screen button.  It will take a picture of whatever is on your screen at that second (so be sure to have the sound preferences window open), and save it as a .png file on your desktop.

Did you find any helpful information in that other thread I linked to?

Hello again.
Though the link you gave me is useful, I find that setting the sound files (from my other partition where I store my sound files) with the custom setting is one thing.
To get the computer to play my custom sound file when I restart my computer with the startup.wav sound file is another thing. I mean, on restart, my computer doesn't play my custom startup.wav sound file.

Hope you can please tell me where I should place or put my custom sound file on my installed Linux partition?

---

### Post by stoogiebuncho on 2009-02-15
It seems like you should be able to specify any sound you want as the startup sound, though it would probably help to have it on the same partition as your Ubuntu install.

I'd try just moving it to your home folder and see if you can use the sound preferences to point to it there.

If that doesn't work, you can find where the rest of the system sounds are stored.  Open a terminal, and enter:
```
locate startup.wav
```

It will tell you where it finds that file, and that's probably where the system sounds are.  On my machine it's /usr/share/sounds/

---

### Post by wstay on 2009-02-15
> **stoogiebuncho said:**
> It seems like you should be able to specify any sound you want as the startup sound, though it would probably help to have it on the same partition as your Ubuntu install.

I'd try just moving it to your home folder and see if you can use the sound preferences to point to it there.

If that doesn't work, you can find where the rest of the system sounds are stored.  Open a terminal, and enter:
```
locate startup.wav
```

It will tell you where it finds that file, and that's probably where the system sounds are.  On my machine it's /usr/share/sounds/

I had tried to copy my sound file to my Desktop and also using the termimal as a SU (root) copy it to /usr/share/sounds/. And I still could not get my custom sound file to play. I think we have to create a link from the Sound Preferences to my custom sound file to where-ever we put it. But how do we create a link?

---

### Post by wstay on 2009-02-21
> **stoogiebuncho said:**
> It seems like you should be able to specify any sound you want as the startup sound, though it would probably help to have it on the same partition as your Ubuntu install.

I'd try just moving it to your home folder and see if you can use the sound preferences to point to it there.

If that doesn't work, you can find where the rest of the system sounds are stored.  Open a terminal, and enter:
```
locate startup.wav
```

It will tell you where it finds that file, and that's probably where the system sounds are.  On my machine it's /usr/share/sounds/

The sound files in /usr/share/sounds are all with .ogg extension.
My custom sound file startup.wav does not play when I restart my computer.
Is there away to change the startup.wav to startup.ogg?

---

### Post by stoogiebuncho on 2009-02-21
Open the file in Audacity, and then go to File > Export.  It should have the option to export as an ogg.

---

### Post by wstay on 2009-02-23
> **stoogiebuncho said:**
> Open the file in Audacity, and then go to File > Export.  It should have the option to export as an ogg.

I open the file in Audacity, and then go to File > Export.
The 'Save in folder:' option is grey-out.
That means I cannot fill in anything there.
And I do not know how to continue from there to save the .wav sound file to .ogg Can you please advice on how to continue from there?

---

