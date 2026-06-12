---
title: "Some launchers only work once"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by beew on 2011-09-05
I have installed webcamstudio from its website. I want to create a launcher in the Unity bar. I have tried 3 different methods 

1) Open the application and right click its icon in the Unity bar and check "keep" in launcher. It keeps the icon in the Unity bar but it doesn't work_ at all_, clicking it nothing happens. 
2) drag the applications' icon from the dash to the Unity bar, it works, but only once per session. If I close the app then I can't restart it with the launcher on the Unity bar. 
3) Copy the .desktop file from /usr/share/applications to 
~/.local/share/applications, change ownership from root to username and check the box allow to execute and then drag it to the Unity bar. Result was same as 2)

I can launch the program without problem from the dash though.

I open the .desktop file with gedit and it is how it looks like.
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=WebcamStudio
Type=Application
Categories=Application;AudioVideo;
Terminal=false
Icon=/usr/share/pixmaps/webcamstudio.png
Exec=/usr/bin/webcamstudio
Comment=WebcamStudio for GNU/Linux

```I can't see anything wrong with it.

Please help! Thanks.

---

### Post by beew on 2011-09-24
bump!

---

### Post by beew on 2011-09-28
I have installed LibreOffice manually and experienced the same phenomenon. The launcher on the Unity bar apparently only work once. Click the first time the application is launched, close it and click the second time nothing happens.

---

### Post by beew on 2011-09-29
Bump!

---

### Post by beew on 2011-09-29
Hello? Nobody experiences this problem??!!!

---

### Post by beew on 2011-09-30
Bump!

---

### Post by The Cog on 2011-09-30
Sometimes I have seen somethiong like this, only to discover that the application I'm trying to launch has a dialog window open somewhere, under another window or on a different desktop. For instance, firefox or LibreOffice which don't open a new copy of the application, but open a new window/tab in the currently open copy. If there's a password dialog already open but hidden somewhere, you can click the launcher until your arm falls off. 

Similarly, I have seen firefox fail to close properly, such that you can't see a firefox window, but you can't launch a new firefox because the old one isn't closed. In this case, the command "killall firefox-bin" helps.

---

### Post by beew on 2011-10-01
Hi, 

Thanks for the reply (finally someone!) Unfortunately it was not the problem, I have checked that the applications are closed properly. Somehow the launchers for some applications on the Unity bar just don't work the second time in the same session. I have the codes for one such in my first post.

---

### Post by beew on 2011-10-02
bump!

---

### Post by Krytarik on 2011-10-02
Although in your case the custom launchers already stop working within the running desktop session, not after closing it, the cause might be similar, so try this:

[http://www.tuxgarage.com/2011/07/unity-reset-after-restart-relogin.html](http://www.tuxgarage.com/2011/07/unity-reset-after-restart-relogin.html)

Btw., with its current behaviour, are the launchers still present after starting a new desktop session?

Hope that works!

---

### Post by beew on 2011-10-03
Hi,

the launchers are still in the Unity bar after restart, and they work too. They only stop working after being used once per session. This only happens for some programs and only for their launchers in the Unity bar (no problem with the dash), the other programs are working ok (so  it is not the same problem described in your link, but I tried the solution nevertheless, as expected it didn't work.)

The crazy thing is that I just tested these programs on another installation of Natty (same machine) and the launchers work perfectly! I am wondering where should I look to locate the problem.

---

### Post by beew on 2011-10-09
Here is what happened with LibreOffice, installing from synaptic Unity bar icons work, but install .deb manually they work only once per session, afterwards clicking has no effect (icons in dash work fine) Now if I install Libreoffice using synaptic BUT install an addon not in the repo the .desktop files work only once per sessin.

Can't find a general pattern, some applications are fine even though they are installed with .debs (like googleearth) and there seem to be at least one that is installed from the repo but icon works only once (jitsi)

Have tried chaging the command in the .desktop files to the absolute path but it makes no difference.

This problem seems to only affect one of my Natty installs. The other one is fine.  I think it may be some Unity or Compiz settings that have gotten screwed up. Is there a configuration file that I should look at?

---

### Post by Krytarik on 2011-10-09
> **beew said:**
> This problem seems to only affect one of my Natty installs. The other one is fine.  I think it may be some Unity or Compiz settings that have gotten screwed up. Is there a configuration file that I should look at?
Yeah, you should give resetting all Unity and Compiz settings a try, start with the first one:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

