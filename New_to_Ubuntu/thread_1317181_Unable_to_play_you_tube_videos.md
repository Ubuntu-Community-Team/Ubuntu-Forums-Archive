---
title: "Unable to play you tube videos"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by abhilash1989 on 2009-11-06
Hi..At present im using an ubuntu ultimate 1.8 OS....My problem is im unable to play you tube videos..It has insisted me to upgrade to a new version of flash plugin so i downloaded the follwing file :
**install_flash_player_10_linux.tar.gz** archive file, which has 1 file i.e. **libflashplayer.so** file in it...
Now how to install the plugin..what should i do..Pls Help
THNX IN ADVANCE...

---

### Post by Old *ix Geek on 2009-11-06
HOW are you unable to add it?  That file just needs to be copied into the correct directory [which depends on your installation]. Please be more specific!

---

### Post by fuzzyllama on 2009-11-06
Search the forums for "FLASH".  There are literally hundreds of threads on this forums concerning Flash issues.  These MAY (or MAY NOT) work for you.  Check out the different solutions, then post again if you are still having issues... 

Best of Luck!

---

### Post by abhilash1989 on 2009-11-06
Sorry i was a bit wrong in expressing my problem...
Actually what i wanted is...Now what should i do for adding the plugin... i dont no how to install the plugin..
Please HELP

---

### Post by superharas on 2009-11-06
I think you should download the '.deb', that is much easier!
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) , choose the '.deb'.
When downloaded just double click, and follow the instruction.
Then, restart firefox/or whatever browser. Then it should work.

---

### Post by ajgreeny on 2009-11-06
I don't know Ubuntu Ultimate 1,8 OS, but in most Ubuntu versions you can do all this by using synaptic or apt-get.  If this is not possible for some reason, you can just use the flashplayer installer shell script which is also in the archive you downloaded from Adobe.  Just use the terminal to navigate to the folder where the two files are located and run the command ```
sudo ./flashplayer-installer
```Make sure the file is executable first, which I think it is when downloaded, or it will not work.  That script will put the plugin into the correct folders of your system.

EDIT:
Silly me!  I forgot there is a .deb file to do it all for you now.

---

### Post by Old *ix Geek on 2009-11-06
> **abhilash1989 said:**
> Now what should i do for adding the plugin... i dont no how to install the plugin..
Please HELP

It's really easy. :)

Have you extracted the libflashplayer.so file? If not, do that via whatever method you're used to (or ask for help if you don't know how).

Now all you have to do is copy it into the plugins directory for the browser you're using. Since you didn't mention your browser, and since most people around here--NOT including me!--use Firefox, I'm going to assume you are, too.  Do you use a GUI to copy files or the command line?  I'm command line, but I'll assume you're GUI. **Copy** libflashplayer.so and then navigate into this directory:

/home/YOURNAME/.mozilla/plugins

Now **paste** the file.

You're done.

If your browser was open when you did this you'll need to restart it.

Since I had to do so much assuming, this may or may not work!

---

### Post by chenxiaolong on 2009-11-06
The 32 bit driver can be downloaded from: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)

The 64 bit driver can be downloaded from: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

Hope this additional information helps :)

---

### Post by debayanm on 2009-11-06
hi all,

I have a dell inspiron 1525, quite new, 2 GB ram 160 GB HDD, core 2 due T 5750 processor, 2 MB Cache, etc etc

I downloaded ubuntu 9.10 desktop version and ubuntu 9.10 netbook version..They are in ISO version..but when i am running them using DAEMON tools lite, and restarting system, they UBUNTU is just showing a small logo and after that , system is going black..

Plz help..

---

### Post by chenxiaolong on 2009-11-06
I don't think Ubuntu is meant to be installed when the iso is mounted under Daemon Tools, You should try burning it to a CD or DVD and boot it from there.

---

### Post by abhilash1989 on 2009-11-07
Hii..ive navigated into my .mozilla folder..but there i didnt have a plugins folder.. so i created one n pasted the libflashplayer.so....but even now videos r not playing... it says upgrade to the new version...but i already have the latest version..
Pls Help

---

### Post by Old *ix Geek on 2009-11-07
> **abhilash1989 said:**
> Hii..ive navigated into my .mozilla folder..but there i didnt have a plugins folder.. so i created one n pasted the libflashplayer.so....but even now videos r not playing... it says upgrade to the new version...but i already have the latest version..
Pls HelpOkay, remember all the assuming I did? :)  We'll figure it out.

First of all, are you using Firefox?

Second, where is it installed? If you don't know, get to a command line and type this:
```
whereis firefox
```
and post the results. There should be a plugins directory under the installation directory.

If you find the latter on your own, paste the .so file there and you should be good to go.

---

### Post by chenxiaolong on 2009-11-07
There's no need for that. All you have to do is create a new "plugins" folder in your .mozilla folder. That's what I did.

---

### Post by abhilash1989 on 2009-11-08
Ya im using Firefox

```
whereis firefox
```

The result given after typing the follwing code is

abhi@abhi-desktop:~$ whereis firefox
firefox: /usr/bin/firefox /usr/lib/firefox /usr/lib64/firefox /usr/share/firefox
abhi@abhi-desktop:~$

---

### Post by sandyd on 2009-11-08
> **Old *ix Geek said:**
> It's really easy. :)

Have you extracted the libflashplayer.so file? If not, do that via whatever method you're used to (or ask for help if you don't know how).

Now all you have to do is copy it into the plugins directory for the browser you're using. Since you didn't mention your browser, and since most people around here--NOT including me!--use Firefox, I'm going to assume you are, too.  Do you use a GUI to copy files or the command line?  I'm command line, but I'll assume you're GUI. **Copy** libflashplayer.so and then navigate into this directory:

/home/YOURNAME/.mozilla/plugins

Now **paste** the file.

You're done.

If your browser was open when you did this you'll need to restart it.

Since I had to do so much assuming, this may or may not work!
or just run this in the terminal
```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree


wget -c http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xvfz libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so
rm libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

```

---

### Post by abhilash1989 on 2009-11-08
```
sudo apt-get remove flashplugin-installer flashplugin-nonfree gnash swfdec

```

Result :

```
abhi@abhi-desktop:~$ sudo apt-get remove flashplugin-installer flashplugin-nonfree gnash swfdec
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-installer
abhi@abhi-desktop:~$ 

```

What is the problem i cant understand...even though i pasted the libflashplayer.so file in .mozilla folder.. the videos r not playing...

---

### Post by ajgreeny on 2009-11-08
> **abhilash1989 said:**
> Ya im using Firefox

```
whereis firefox
```The result given after typing the follwing code is

abhi@abhi-desktop:~$ whereis firefox
firefox: /usr/bin/firefox /usr/lib/firefox /usr/lib64/firefox /usr/share/firefox
abhi@abhi-desktop:~$
It looks from this as though you may have a 64 bit machine and OS.  If that is so, have you got the 64 bit version of flashplayer, or did you download the 32 bit version?

Just checking, and I don't want to assume too much, but it is worth asking the question.

---

### Post by sandyd on 2009-11-08
fixed typos
try copy and pasting the commands again

---

### Post by lucem auspicio on 2009-11-08
hi I had the same problem that you have, I download the last version of flash player in a tar.gz file, when I extract it I got a iso file, then I go to places (commant near sytem Up left) then click on computer Go to your home directory under the Places menu. Then press control + H to show hidden files. Then copy the .so file to .mozilla/plugins. You may need to create the plugins folder under .mozilla.

After that you have to turn off and restart the computer open firefox and see the videos

good luck

---

### Post by chenxiaolong on 2009-11-09
Well, you don't need to restart the computer, just firefox. :)

Also, you have to remove flashplugin-installer for it to work.

---

