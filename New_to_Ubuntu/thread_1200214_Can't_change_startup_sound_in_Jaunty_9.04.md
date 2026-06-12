---
title: "Can't change startup sound in Jaunty 9.04"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by pseudo x nyn on 2009-06-29
ok. I have a quick one for you guys. 

I've been wrestling with Jaunty trying to change the login sound (the drums) to one I've downloaded. The file is in wav format and in \usr\share\sounds\feather. Its the name of the theme and I wanted to keep it separate. I used the Sound GUI found in System > Preferences to change the login sound. Not only does it not change the sound on restart, but it won't even preview my file. I know its a working file, because I can play it in Quod Libet and via preview in Nautilus.

Any suggestions? Should I just give up and replace the default file [wherever it is]?

---

### Post by ~sHyLoCk~ on 2009-06-29
I don't know for sure, but you can try changing the file permissions. If you don't know how to tell us the exact path to your sound files.

---

### Post by pseudo x nyn on 2009-06-29
wow, that was quick. ^_^

path to my sounds: \usr\share\sounds\feather\
filename: opening.wav

   I changed most of the other system sounds with files extracted from the same place and they worked on the first try. This is the only one that's giving me problems. I'll give your idea a go though. 

Thanks for helping me out!

---

### Post by ~sHyLoCk~ on 2009-06-29
Ok try,
```
sudo chmod +rx /usr/share/sounds/feather/opening.wav
```

---

### Post by pseudo x nyn on 2009-06-29
Worked like a charm. I'm all set!

Thank you so much for helping me out right away! :D 

Rock on.

---

### Post by ~sHyLoCk~ on 2009-06-29
> **pseudo x nyn said:**
> Worked like a charm. I'm all set!

Thank you so much for helping me out right away! :D 

Rock on.

Glad that worked :) Enjoy Ubuntu.

---

### Post by Cuco3 on 2009-08-15
Hello.

I've tried the same solution but it doesn't work for me.

Like Pseudo experienced, it continues to read the original Ubuntu startup sound when previewing

I've verified that the file has the read and execute permissions for "Other".

Anybody else having this problem?

---

### Post by Cuco3 on 2009-08-16
Anybody? Please?

---

### Post by CaptainMark on 2009-08-16
i once had this problem, i fixed it but never figured out how this worked. Opened the sound file using sound converter and resaved as .wav in a different location then move it back where you want it. Worked okay after that???

---

### Post by Cuco3 on 2009-08-16
^I'll try converting it to .wav, thanks.

Ubuntu/Linux is a nice experimental OS but it's clearly not ready to compete with Windows or OSX.

The nice thing about WIndows/OSX is, when you tell it to do something, it does it. That's why they can afford to charge for their OS.

---

### Post by Cuco3 on 2009-08-16
> **CaptainMark said:**
> i once had this problem, i fixed it but never figured out how this worked. Opened the sound file using sound converter and resaved as .wav in a different location then move it back where you want it. Worked okay after that???I tried converting it, saving to a diff location, then saving it back to the /usr/share/sounds/mytheme folder. That didn't work.

What a POS Ubuntu is. Sorry if that offends anyone but this is just the tip of the iceberg when it comes to the custom configurations I've had to do to get it to work. Not to mention the problems that there appears to be no solution for (Intel video card problems and Suspend issues).

GG Ubuntu.

---

### Post by Cuco3 on 2009-08-16
Here's something to laugh at: when you select "Disabled" for "Login" sound, it still continues to play the original Ubuntu sound. What a POS!!! LOL.

---

### Post by CaptainMark on 2009-08-17
Ubuntu isnt free because its rubbish, nor is it rubbish. Its free because not everyone likes worshipping corporate idols and some people think you should be able to express freedom of mind on a computer as well, just the same way you have the freedom of speech. Ubuntu was never made to be like windoze or mac os, you can customise absolutly anything in ubuntu something you cant do in windows or mac os. If you feel you want to use a more user friendly os, go ahead, no ones stopping you.

---

### Post by Cuco3 on 2009-08-17
> **CaptainMark said:**
> Ubuntu isnt free because its rubbish, nor is it rubbish. Its free because not everyone likes worshipping corporate idols and some people think you should be able to express freedom of mind on a computer as well, just the same way you have the freedom of speech. Ubuntu was never made to be like windoze or mac os, you can customise absolutly anything in ubuntu something you cant do in windows or mac os. If you feel you want to use a more user friendly os, go ahead, no ones stopping you.When you talk about Ubuntu, do you really mean Unix/Linux altogether?

My beef is with Ubuntu (9.04) and not Linux.

I'll probably end up installing an older version of Ubuntu to see if it works any better, if not, try another distro. CentOS was very rock solid but I wanted more of a home/office desktop distro.

But don't get too defensive when someone calls out Ubuntu for it's problems. There's plenty of Pro-Linux people that use every opportunity to knock on Windows or Mac OS for their problems knowing very well that some of these Linux distros have their fair share of problems. Like I said in another thread, all you need to do is look at the number of threads in the "Absolute Beginner Talk" forum to see that Ubuntu doesn't work great out of the box.

---

### Post by xaoxoa on 2009-08-18
I'm having the same problem too. I tried every "solution" on here. Please help. :(

---

### Post by philinux on 2009-08-18
In system prefs sound double click default and choose custom. Ir should then let you change it.

At least thats what I do with no probs.

---

### Post by xaoxoa on 2009-08-18
> **philinux said:**
> In system prefs sound double click default and choose custom. Ir should then let you change it.

At least thats what I do with no probs.
this is what I have:

---

### Post by Cuco3 on 2009-08-18
> **xaoxoa said:**
> I'm having the same problem too. I tried every "solution" on here. Please help. :(I'm glad I'm not the only one. Does yours also continue to play the default Ubuntu startup sound even though you've changed or disabled it?

Maybe if enough people speak up about this problem we can get someone who is generous enough to help us out with it.

---

### Post by Cuco3 on 2009-08-18
> **philinux said:**
> In system prefs sound double click default and choose custom. Ir should then let you change it.

At least thats what I do with no probs.Doesn't work but thanks anyways.

---

### Post by philinux on 2009-08-18
What changes have you done to your initial install?

---

### Post by JOHNNYG713 on 2009-08-18
Try placing your new sounds in a new folder in your home folder,and pull your sounds from there,you might have to seperate them into dfferent folders for each sound, This worked for me!

---

### Post by Cuco3 on 2009-08-20
> **philinux said:**
> What changes have you done to your initial install?Nothing drastic that I can think of ...

> **JOHNNYG713 said:**
> Try placing your new sounds in a new folder in your home folder,and pull your sounds from there,you might have to seperate them into dfferent folders for each sound, This worked for me!We have our winner!:guitar:

Thank you JohnnyG!

Although the "Logout" sound doesn't play when you logout (note: it does play when you preview it), the Logon sound does work perfectly.

This should be added to the Ubuntu documentation until the dev team can fix the real problem.

---

### Post by JOHNNYG713 on 2009-08-24
Glad to hear you got your sounds running , Now I maybe can help you with logout sound ! This is one of my posts at GNOME-LOOK, It has a "how to" enable logout sounds, Plus my complete sound scheme :)  Enjoy!

[http://www.gnome-look.org/content/show.php/new_remix-5-sounds?content=108674](http://www.gnome-look.org/content/show.php/new_remix-5-sounds?content=108674) 

:guitar:

---

### Post by Birch Bark on 2009-10-31
I had this same problem and thought I'd post my solution for anyone else who is searching.

I downloaded a theme called "Rainy Soundscape" from GNOME-Look and extracted it to /usr/share/sounds, and though it was in the right place it wouldn't display in the list at System --> Preferences --> Sounds.  After some head-scratching what I ended up doing was playing with the files a bit to make it uniform with the other sound themes.  I modeled it on what I found in the "Ubuntu" sound theme folder, like this:

In /usr/share/sounds: a folder called "rainy_soundscape."
In that folder: a folder called "stereo" to contain the sound files
and 
an executable text file called "index.theme", which says:
```
[Sound Theme]
Name=Rainy Soundscape
Directories=stereo

[stereo]
OutputProfile=stereo
```
NOTE: once you save this file with the ".theme" extension, it may not let you view it anymore in the GUI, so make sure you typed it correctly the first time unless you want to open it with the terminal.

Now, in the "stereo" folder, make sure your sound files have uniform names (I modeled mine on the "Ubuntu" theme, again): e.g. "desktop-login.wav," "dialog-warning.wav," etc.

After doing this I got the theme to work fine, with one glitch: the system still played the "Ubuntu" startup sound until I fooled it by munging that that particular sound filename to "desk3top-login.ogg" : )

---

### Post by amanetta on 2010-01-11
I've the same problem in karmik...can u help me?

---

