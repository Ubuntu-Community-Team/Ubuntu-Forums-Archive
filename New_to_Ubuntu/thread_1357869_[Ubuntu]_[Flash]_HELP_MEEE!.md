---
title: "[Ubuntu] [Flash] HELP MEEE!"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by Razbuntu on 2009-12-17
WHAT IN NAME OF ERUSEA IS GOING ON??!?!?!!? I Am Having Issues With Ubuntu's Flash Plugin... i cant interact with the flash files! hold me... is there a work around???
please help!:confused:](*,)

---

### Post by llawwehttam on 2009-12-17
Please be more specific. What is it you can't do then maybe I can help.

---

### Post by Razbuntu on 2009-12-17
I Am Not Able To Interact With The Mouse, The Keyboard Or Anything. I Am Running Ubuntu 9.10, Karmic Koala, Flash 10.0. On A Dell Insperion 1525,  With Another OS, Windows Vista Home Premium. (Karmic Installed Via Wubi Installer

---

### Post by llawwehttam on 2009-12-17
By not able to interact with the mouse do you mean not at all or just in flash apps in general or just in a specific app. Also have you installed the flash-plugin?

---

### Post by llawwehttam on 2009-12-17
Just top add to that last have you tried installing adobeflash-nonfree . It might help a lot as flash 10.1 is still unstable.

---

### Post by Razbuntu on 2009-12-17
I Am Visiting Newgrounds.com And I See it happen All The Time. Other Websites Are Working Just Fine.
I Don't Know What is Up...

---

### Post by llawwehttam on 2009-12-17
Hmm the site works fine for me. Open synaptic and search for flash and tell me all the installed things with 'flash' in the name.

---

### Post by Razbuntu on 2009-12-17
:KS I'll Give it A Whirl.:KS

---

### Post by llawwehttam on 2009-12-17
Do post back if you have success. Its good to know how the problem was fixed exactly.

---

### Post by Razbuntu on 2009-12-17
Try A Flash On One Of it's Subpages, Hang On, I'll Get My Favorite Just To Find Out.

---

### Post by Razbuntu on 2009-12-17
Here: [http://www.newgrounds.com/portal/view/326847](http://www.newgrounds.com/portal/view/326847)

---

### Post by llawwehttam on 2009-12-17
Its all working fine for me.

---

### Post by MooPi on 2009-12-17
Have you installed flash plugin?

---

### Post by davec64 on 2009-12-17
I had an issue when running flash video's in web pages where the viseo stuttered and CPU went to 100%. I found that turning off desktop effects help for me.

---

### Post by llawwehttam on 2009-12-17
Dave- that problem is caused by older grapics cards with insufficient memory or by cards that havn't got drivers installed for them. It wouldn't be affected by flash. The adobeflash-nonfree package in synaptic should help.

---

### Post by Razbuntu on 2009-12-17
it doesn't work.

---

### Post by mikewhatever on 2009-12-17
A question for the OP, how exactly does one interact with flash files?](*,) I mean, the keyboard is for typing and mouse for clicking, so were do flash files come it here?](*,)
I am particularly interested in what the OP has to say.](*,)

---

### Post by Razbuntu on 2009-12-17
That's not the problem!!! I had installed the flash-nonfree package from synaptic! It still doesn't work!!! My video doesn't flicker at all!

---

### Post by MooPi on 2009-12-17
So you can get youtube to work but you can't interact with flash games ?

---

### Post by PH James on 2009-12-17
It seems to be a problem with the 64-bit version of Flash 10. It might be in the 32-bit version too, I'm not sure.

I had the problem, and this fixed it for me: [http://www.youtube.com/watch?v=VQnyJsP0z_U&feature=related](http://www.youtube.com/watch?v=VQnyJsP0z_U&feature=related)

Essentially, you edit this file (this is the command you use in the terminal):

```
sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

And then add this line before the last line in the file:

```
export GDK_NATIVE_WINDOWS=1
```

Then just restart your browser.

---

### Post by wolke on 2009-12-17
are you perchance using 64-bit ubuntu 9.10?
if not, nevermind this post.


on 64-bit systems, the 32-bit flash library reportedly works fine, but not for me.
i experience something very similar to you: the mouse and the keyboard often do nothing {but usually the space bar can pause videos}; no idea whats wrong. {maybe a 32-bit library thats missing, but w/e}


as you know, you can install the 32-bit version of Adobe Flash 10.0 by running:
```
sudo apt-get install flashplugin-nonfree

```


to install the alpha pre-release of native 64-bit flash from evil Adobe:

kill firefox dead
```
sudo apt-get purge flashplugin-nonfree flashplugin-installer
cd
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
tar -xvf libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins

```
start firefox

---

### Post by wolke on 2009-12-17
ooh, yea that fixes it for me. {thx PH James}

this makes the 32-bit Adobe Flash 10 (the one in the package: flashplugin-nonfree) work fine for me, on x86-64 ubuntu 9.10


the 64-bit alpha pre-release doesnt appear to have this problem.

---

### Post by Razbuntu on 2009-12-18
The Windows Export Did it For Me. Thanks.

---

### Post by fatum on 2009-12-18
> **PH James said:**
> It seems to be a problem with the 64-bit version of Flash 10. It might be in the 32-bit version too, I'm not sure.

I had the problem, and this fixed it for me: [http://www.youtube.com/watch?v=VQnyJsP0z_U&feature=related](http://www.youtube.com/watch?v=VQnyJsP0z_U&feature=related)

Essentially, you edit this file (this is the command you use in the terminal):

```
sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

And then add this line before the last line in the file:

```
export GDK_NATIVE_WINDOWS=1
```

Then just restart your browser.

This did it for me also. Had the issue of the player not accepting any input from mouse but the space bar would pause the video. Running 9.10 with 10.1 flash beta for 64bit with Chrome browser. Now I have no issues that I have tried so far. Thank you so much. It was very annoying for me.

---

