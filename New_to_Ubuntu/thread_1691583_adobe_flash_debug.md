---
title: "adobe flash debug"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by opiumpoetry on 2011-02-20
I am trying to install the Adobe Flashplayer Debugger. I downloaded it but don't know how to install it on my system. Your help will be greatly appreciated.

---

### Post by gandaran on 2011-02-20
did you download the stand alone flashplayer debugger package, I don't know of any other adobe linux flash debugger so if it was the stand alone player you just extract the tar package and put the player wherever you want then click the flashplayer file to start or create a launcher with the full path to the player and play your shockwave flash apps.

---

### Post by opiumpoetry on 2011-02-20
> **gandaran said:**
> did you download the stand alone flashplayer debugger package, I don't know of any other adobe linux flash debugger so if it was the stand alone player you just extract the tar package and put the player wherever you want then click the flashplayer file to start or create a launcher with the full path to the player and play your shockwave flash apps.

didn't fix it. i already have the plugin content debugger, i just need to learn how to install it. maybe sudo apt-get install?

---

### Post by opiumpoetry on 2011-02-21
this website [http://www.chesscube.com/](http://www.chesscube.com/) tells me i need to install the debug flash player. i already downloaded it, now how do i install it? i had no problem installing it on my other computer that uses Windows.

---

### Post by gandaran on 2011-02-21
> **opiumpoetry said:**
> didn't fix it. i already have the plugin content debugger, i just need to learn how to install it. maybe sudo apt-get install?
what exactly did you download or whats inside the tar package?
only with more information can we help, maybe post here the download link.

---

### Post by gandaran on 2011-02-21
> **opiumpoetry said:**
> this website [http://www.chesscube.com/](http://www.chesscube.com/) tells me i need to install the debug flash player. i already downloaded it, now how do i install it? i had no problem installing it on my other computer that uses Windows.
these downloads are only for windows machines.

---

### Post by opiumpoetry on 2011-02-21
[http://www.adobe.com/support/flashplayer/downloads.html](http://www.adobe.com/support/flashplayer/downloads.html)

---

### Post by opiumpoetry on 2011-02-21
> **gandaran said:**
> these downloads are only for windows machines.

except for the 3 at the bottom under the heading "linux" they are all tarball files

---

### Post by gandaran on 2011-02-21
> **opiumpoetry said:**
> [http://www.adobe.com/support/flashplayer/downloads.html](http://www.adobe.com/support/flashplayer/downloads.html)
was [this the package]("http://download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_plugin_debug.tar.gz") or one of the other three
I have a slow internet connection so I cant download the package, if it was this one then just extract the package, I believe there should be a libflashplayer.so file inside if correct post back and I will help you installing the file.

---

### Post by opiumpoetry on 2011-02-21
> **gandaran said:**
> was [this the package]("http://download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_plugin_debug.tar.gz") or one of the other three
I have a slow internet connection so I cant download the package, if it was this one then just extract the package, I believe there should be a libflashplayer.so file inside if correct post back and I will help you installing the file.

yes, libflashplayer.so is exactly the file i have, so how do i install it? thanx for your help so far.

---

### Post by gandaran on 2011-02-21
> **opiumpoetry said:**
> yes, libflashplayer.so is exactly the file i have, so how do i install it? thanx for your help so far.
you just have to put the libflashplayer.so in the right place but you will have to remove the installed flash first or you will have conflicting flash plugins, remove flash then check with firefox in any flash web page that flash isn't installed then just drop that libflashplayer.so in either /usr/lib/firefox/plugins (for all users) or /home/'user'/.mozilla/plugins/ (user only and make the plugins folder), flash should be working on flash sites now.
other browser probably will pick up the flash plugin from the firefox plugins folder if they don't then you can do the same on every browser plugins folder.
remember where you installed the libflashplayer.so so if you reinstall the system flash again you have to remove the libflashplayer.so

---

### Post by opiumpoetry on 2011-02-21
To any and all, I personally recommend swfdec flash player over adobe flash. Swfdec seems to be much more stable than adobe flash. You can find it in the software center.

---

### Post by opiumpoetry on 2011-02-22
I uninstalled Adobe Flash and installed Swfdec from the software center instead. Swfdec fixed the issue, it doesn't crash.

---

### Post by howefield on 2011-02-22
Threads merged.

---

### Post by randomcode on 2011-03-02
I tried uninstalling and copying the .so file into the plugins directory but the browser wanted to install Flash...

---

### Post by DoomNglooM on 2011-07-10
Hello,

Im trying to get the FlashFirebug 3.0.1 working on Firefox, but i got stucked when it comes to install the flash debug player plugin.I already followed the instructions from thread #11 but now im getting the error in Firebug:
Your Current Flash player version is "0.0 debugger". This Extension requires Flash player **Debugger** version 10.2.0 or higher **(for Netscape-compatible browsers)**

Looks like i missed the step when it comes to reinstall the flashplayer again.

So please³ give me a failsafe instruction for dummys :)

Thanks
Nik

---

### Post by gandaran on 2011-07-11
> **DoomNglooM said:**
> Hello,

Im trying to get the FlashFirebug 3.0.1 working on Firefox, but i got stucked when it comes to install the flash debug player plugin.I already followed the instructions from thread #11 but now im getting the error in Firebug:
Your Current Flash player version is "0.0 debugger". This Extension requires Flash player **Debugger** version 10.2.0 or higher **(for Netscape-compatible browsers)**

Looks like i missed the step when it comes to reinstall the flashplayer again.

So please³ give me a failsafe instruction for dummys :)

Thanks
Nik
hi
I will try to help if I can, so you have the debugger flash libflashplayer.so file, right? where did you install the file? and did you remove any other flash plugin first? 
please post any details of what you have done so far.

---

### Post by DoomNglooM on 2011-07-11
Hey,

Thanks for the reply!

> **gandaran said:**
> hi
I will try to help if I can, so you have the debugger flash libflashplayer.so file, right? where did you install the file? and did you remove any other flash plugin first? 
please post any details of what you have done so far.

1. uninstalled all flash plugins from my firefox.
2. uninstalled flash plugin v10 in the ubuntu software center.
3. Tested on youtube if flash might still be working. -> nope.
4. downloaded the flash debugger plugin from [here]("http://download.macromedia.com/pub/flashplayer/updaters/10/flashplayer_10_plugin_debug.tar.gz").
5. extracted the tar.gz and copied the "libflashplayer.so" to "/usr/lib/firefox-5.0/plugins" as you sayed in this [thread]("http://ubuntuforums.org/showpost.php?p=10479077&postcount=11").
6. Tested on youtube with the following errors:
    Flashplayer itself: "You need to upgrade your Adobe Flash Player to watch this video. 
 [Download it from Adobe.]("http://get.adobe.com/flashplayer/")"
    FlashFirebug: "Your Current Flash player version is "0.0 debugger". This Extension requires Flash player **Debugger** version 10.2.0 or higher [B](for Netscape-compatible browsers)"

[/B]I guess i am just making some embarrassing newbe mistake. :confused:

---

### Post by gandaran on 2011-07-11
okay, just to check what flash is installed, type in terminal first
```
sudo updatedb
```
to update data, then
```
locate libflash
```
post the output.
and also type in firefox url bar
```
about:plugins
```
post the output.
and a question about ubuntu? 32-bits or 64-bits? the 32-bits flash doesn't work on 64-bits systems.

---

