---
title: "Neophyte who wants to install Adobe Flashplayer"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by fiatveritas on 2011-07-23
[FONT=Times New Roman;&quot; line-height=&quot;150%;font-size=&quot;10pt;&quot;]Greetings Comrades,

I am having trouble installing Adobe's Flashplayer on my system (Ubuntu 11.04 x64bit) and am following Adobe's installation instructions on their website with no success. 

Normally, I choose where Firefox will save my files--in this case in the Downloads folder--and am at moment wondering if I should save my files in the desktop? If Ubuntu's terminal is anything like the Window's Command Prompt then it irrelevant where a user saves a files as long as the user chooses where to install the  file. Also, is there any difference whether I install the Debian (*.deb), Tarball (*.tar.gz), or the Red Hat Package Manager (*.rpm) package? Here's another general question, 'Is unpackaging synonymous to unzipping a file?'

Here's what I've tried: I've saved the *.tar.gz file into the 'Downloads' folder, extracted the *.tar.gz file into the 'Downloads' file--which  yields a *.so file, and used sudo cp *.so /usr/lib/firefox-addons/plugins to move the *.so file (that Adobe instructs) into the plugins folder. However, I'm suspicious that a plugins' extension must be in the form *.xpi because that is how the other packages in the 'extensions' folder are. This is further proved by the fact that after placing the *.so file in the plugins folder and checking the addons installed on Firefox that Flashplayer is not installed.

Fiat Veritas[/FONT]

---

### Post by wojox on 2011-07-23
Easiest way [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

---

### Post by garvinrick4 on 2011-07-23
"Stopping any Firefox that might be running"
```
sudo killall -9 firefox
``` "Removing any other flash plugin previously installed:"
copy and paste one at a time.
```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

``` "Installing Flash Player"
Download flashplayer to Downloads, Desktop where ever you want.
cd (path to flash tarbal)
tar zxvf (flash player you downloaded in tarbal)
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/

```
Or you can use the Script that lovinglinux has written and is an addon in firefox as in post 2.
If you want it simple use lovinglinux's flashaid. If you want to maintain your own through Adobe do it this way.
lovinglinux does use the latest 64 bit beta in flashaid.

---

### Post by garvinrick4 on 2011-07-23
> Is unpackaging synonymous to unzipping a file?'Yes it is called extracting in a tarbal.

Ubuntu is Debian based we use .deb packages which can be installed.
Download package
cd to directory where package is located
sudo dpkg -i (name of package)
Getting package that is already in .deb is easiest. (for your architecture 32 or 64 bit)
In .deb you can also double click on and will install through Ubuntu software center nowadays.
How is that for easy.

Most tarbals you have to ./configure,make,make install and such.
Always read the READ Me file will give you instructions.

## Redhat ands its many cousins use RPM's and use yum instead of apt-get.

---

### Post by 3rdalbum on 2011-07-23
Not entirely sure why you're installing from the Adobe website. Flash Plugin is in the Ubuntu repositories.

```
sudo apt-get install flashplugin-nonfree
```

should do it, or find it in the Software Center.

---

### Post by garvinrick4 on 2011-07-23
> Not entirely sure why you're installing from the Adobe website. Flash Plugin is in the Ubuntu repositories.I believe OP was trying to install 64-bit beta from Adobe, if he isn't we wasted some keystrokes didn't we. I just assumed that is what OP was doing. You know what happens
when we assume don't we. I think with your post we got him covered any which way. Have a nice day.

---

### Post by fiatveritas on 2011-07-26
I tried using the quoted code and received a message that reads,"Unable to locate flashplugin-nonfree." As far as open source software is concerned the nonfree part of the terminal command makes me worry since we are using Ubuntu, open-source, because the word nonfree implies we pay a premium and as a result are not allowed to view the code (nonfree=negative connotation).

> **3rdalbum said:**
> Not entirely sure why you're installing from the Adobe website. Flash Plugin is in the Ubuntu repositories.

```
sudo apt-get install flashplugin-nonfree
```should do it, or find it in the Software Center.

---

### Post by uRock on 2011-07-26
> **wojox said:**
> Easiest way [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

+1 to this. It has worked in every system for me.

---

### Post by fiatveritas on 2011-07-26
At the moment I'm running a vanilla version of Firefox 4.0 so is it  advisable to skip the first half of your terminal input. I've checked  and made sure that there are not any previous plugins. I'm going to give the  second half a go.

> **garvinrick4 said:**
> "Stopping any Firefox that might be running"
```
sudo killall -9 firefox
``` "Removing any other flash plugin previously installed:"
copy and paste one at a time.
```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

``` "Installing Flash Player"
Download flashplayer to Downloads, Desktop where ever you want.
cd (path to flash tarbal)
tar zxvf (flash player you downloaded in tarbal)
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/

```Or you can use the Script that lovinglinux has written and is an addon in firefox as in post 2.
If you want it simple use lovinglinux's flashaid. If you want to maintain your own through Adobe do it this way.
lovinglinux does use the latest 64 bit beta in flashaid.

---

### Post by fiatveritas on 2011-07-26
I understand what you're having me do: After placing the *.so file in  /usr/lib/mozilla/plugins directory and then having me link the directory  with ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/firefox-addons/plugins I have a link between directories that  share the same file. After following the aforementioned instructions I'm  still having trouble after everything is copied and linked. In fact;  when I manually check whether the plugin is installed, the flashplugin  is not installed under the Firefox browser. Perhaps I'm not untarring  the *.tar.gz file correctly. What I did was save the Flashplayer  (tar.gz) from Adobe into my downloads folder and then I extracted the  contents to the downloads file from where I used the cp command.
> **garvinrick4 said:**
> "Stopping any Firefox that might be running"
```
sudo killall -9 firefox
``` "Removing any other flash plugin previously installed:"
copy and paste one at a time.
```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

``` "Installing Flash Player"
Download flashplayer to Downloads, Desktop where ever you want.
cd (path to flash tarbal)
tar zxvf (flash player you downloaded in tarbal)
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/

```Or you can use the Script that lovinglinux has written and is an addon in firefox as in post 2.
If you want it simple use lovinglinux's flashaid. If you want to maintain your own through Adobe do it this way.
lovinglinux does use the latest 64 bit beta in flashaid.

---

### Post by uRock on 2011-07-26
The flashaid add on does all of that for you and it does install the 64bit Flash.

---

### Post by fiatveritas on 2011-07-26
I'm trying to install Adobe's Flashplayer without using a GUI because  it's more enlightening--otherwise I would use closedsource software like  MacOS and Windows to meet my ends. In short, I do this because I want  to blog how to install flash in concise steps for other beginners who  will have the same problem. Is helping others not the philosophy  motivating Ubuntu?
> **garvinrick4 said:**
> I believe OP was trying to install 64-bit beta from Adobe, if he isn't we wasted some keystrokes didn't we. I just assumed that is what OP was doing. You know what happens
when we assume don't we. I think with your post we got him covered any which way. Have a nice day.

---

### Post by uRock on 2011-07-26
> **fiatveritas said:**
> Is helping others not the philosophy  motivating Ubuntu?

That is why one of our great [Ubuntu Members]("http://ubuntuforums.org/member.php?u=649167") created the [FlashAid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") add-on for Firefox. To make things really simple for everyone.

I admire your wanting to do what you are doing the way you are doing it. :)

---

### Post by fiatveritas on 2011-07-26
I'm going to try flashaid and reverse engineer the process--that is, see what files and what directories flashaids puts the files in.

---

### Post by uRock on 2011-07-26
> **fiatveritas said:**
> I'm going to try flashaid and reverse engineer the process--that is, see what files and what directories flashaids puts the files in.

Kool:) Once installed, it will run a script in a terminal requiring your input before it closes, so you will be able to copy and paste it for deeper review.

---

### Post by fiatveritas on 2011-07-26
> **uRock said:**
> Kool:) Once installed, it will run a script in a terminal requiring your input before it closes, so you will be able to copy and paste it for deeper review.
Flashaid works really well. I looked through some of the directories where Adobe's online documentation had me put files and to my surprise the Flashaid script did the same. I'm curious what I did differently, though. Now I need to read the code for Flashaid and be able to do the same for Java--but that shouldn't be as difficult, especially, if there are extensions like Flashaid. Thanks!

---

### Post by lovinglinux on 2011-07-26
> **uRock said:**
> That is why one of our great [Ubuntu Members]("http://ubuntuforums.org/member.php?u=649167") created the [FlashAid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") add-on for Firefox. To make things really simple for everyone.

I admire your wanting to do what you are doing the way you are doing it. :)

I am flattered :-)

> **fiatveritas said:**
> I'm going to try flashaid and reverse engineer the process--that is, see what files and what directories flashaids puts the files in.

> **uRock said:**
> Kool:) Once installed, it will run a script in a terminal requiring your input before it closes, so you will be able to copy and paste it for deeper review.

Don't need to reverse engineer the process. As uRock mentioned, you can see part of the script running when you finish the Wizard. However, if you use the Advanced Mode, you can preview the entire script.

> **fiatveritas said:**
> Flashaid works really well. I looked through some of the directories where Adobe's online documentation had me put files and to my surprise the Flashaid script did the same. I'm curious what I did differently, though. Now I need to read the code for Flashaid and be able to do the same for Java--but that shouldn't be as difficult, especially, if there are extensions like Flashaid. Thanks!

Flash-Aid also removes conflicting plugins installed manually.

---

