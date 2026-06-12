---
title: "installing flash player on ubuntu 9.04 x64"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by djyoung4 on 2009-09-01
ok i found this:
[HTML]http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html[/HTML]
the problem is i dont know how to go about installing this.  i tried searching for it on google and here but didn't even know what to search for.  sorry if this is a repeat of some easily searchable post.  any advice would be helpful

---

### Post by chandru155 on 2009-09-01
Use Synaptic Package to Install Flash. I am also NewBie. After several searches and tries, i found that for Software Installation, Synaptic Manager is best and easy for Newbies. OR Download the Deb file from Adobe.com and download click to install it(it may download some extra files if needed)

---

### Post by SunnyRabbiera on 2009-09-01
> **chandru155 said:**
> Use Synaptic Package to Install Flash. I am also NewBie. After several searches and tries, i found that for Software Installation, Synaptic Manager is best and easy for Newbies. OR Download the Deb file from Adobe.com and download click to install it(it may download some extra files if needed)

The .deb from adobe might not suit a 64bit system though, in any case ubuntu restricted extras can help.

---

### Post by anujpathania on 2009-09-01
Easiest way to find & download application is using Synaptic Package Manager. Make sure you have added third party repository, and updated the package list.

Caution: Packages in synaptic may not be of the latest version of the app since it takes time for them to get update in the list.

---

### Post by Cheezespread on 2009-09-01
> **djyoung4 said:**
> ok i found this:
[HTML]http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html[/HTML]
the problem is i dont know how to go about installing this.  i tried searching for it on google and here but didn't even know what to search for.  sorry if this is a repeat of some easily searchable post.  any advice would be helpful


The steps mentioned can broken down into these.
1.  Get the script from [here]("http://www.myscienceisbetter.info/flash-player/native-64bit-flash-installer.sh").

2. Save the script where you want it.
3. Cd to the directory from terminal.
4. IN terminal type in this :

```
chmod a+x native-64bit-flash-installer.sh
```

This will make the script executable. 
5. If you are already in the directory where you saved it 

type in 
```
./native-64bit-flash-installer.sh
```

That should take care of it.

Or If you want to keep away from terminal.
1.u can also rightclick on the file > properties > permissions and enable the top execute box, and then doubleclick the .sh file . 

Hope I din make any mistake anywhere ;)

---

### Post by theozzlives on 2009-09-01
I just installed ubuntu-restricted-extras, my Flash and JAVA work fine.
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by djyoung4 on 2009-09-01
adobe wont let me.  it says it is the wrong architecture.  the url up there leads to i think a script of how to install it but i dont know how to make it work

---

### Post by djyoung4 on 2009-09-01
cheezespread you are awesome that is exactly what i was looking for.  thank you

---

### Post by SunnyRabbiera on 2009-09-01
> **djyoung4 said:**
> adobe wont let me.  it says it is the wrong architecture.  the url up there leads to i think a script of how to install it but i dont know how to make it work

Yeh like i said dont bother with the adobe site.

---

### Post by Perfect Storm on 2009-09-01
Check: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by humphreybc on 2009-09-01
I did the following in terminal:

```


sudo apt-get install flashplugin-installer


```

This should install flashplugin-nonfree as well and it should automatically get the 64 bit flash plugin from adobe.

---

### Post by nhasian on 2009-09-01
[COLOR="Red"]STOP[/COLOR]

dont use the flash from the repo if you want the 64 bit one.  the one in the repo is 32 bit.

also dont use the ndiswrapper because that will simply make the 32bit flash run in your 64 bit OS.

Here is the latest version of adobe flash 10 64-bit released July 30th:

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

unzip the archive and put the file libflashplayer.so in /usr/lib/mozilla/plugins/

almost forgot to mention you should uninstall any flash you installed before.

---

