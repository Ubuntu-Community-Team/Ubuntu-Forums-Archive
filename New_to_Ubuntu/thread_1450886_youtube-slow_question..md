---
title: "youtube-slow question."
date: 2010-04-09
forum: New to Ubuntu
---

### Post by littlboz on 2010-04-09
I noticed that youtube and other video site seem to not be running as smoothly as they would be on another operating system. I read that this has something to do with flash player and the current mozilla firefox version. I also read that when mozilla firefox 3.6 is released this will possibly be fixed. 

What are my options for fixing this or should I wait for Mozilla firefox 3.6 to be released (if so, when will that be)?

~Is there a button to click on these forums to state that a problem is solved?

---

### Post by Raynman37 on 2010-04-09
Hey, I've had some problems with flash player as well, and I found one thing that seems to work here:

[http://blog.killtheradio.net/technology/slow-flash-in-ubuntu/]("http://blog.killtheradio.net/technology/slow-flash-in-ubuntu/")

I also found another site with a fix on it that I used on my laptop, but for the life of me I can't find it.  I'll be looking for it again though because it fixed all the flash problems I had.

Edit: Also if you are having problems with sites that have a lot of flash animations or ads on them, grab the firefox addon Flashblock.  You'll have to click an extra button to get your youtube videos to play, but it doesn't let any flash ads come up.

Edit 2: I'm also finding in some other posts that you need to remove the libswfdec* package if you have that installed.

Edit 3: This seems familiar: [http://www.linuxquestions.org/questions/ubuntu-63/flash-works-very-slow-748787/]("http://www.linuxquestions.org/questions/ubuntu-63/flash-works-very-slow-748787/")

---

### Post by adam22 on 2010-04-09
I'm running FF 3.6.3 with 64 bit flash....it works a lot better than 32 bit flash which is installed through the repo.

---

### Post by littlboz on 2010-04-09
> **adam22 said:**
> I'm running FF 3.6.3 with 64 bit flash....it works a lot better than 32 bit flash which is installed through the repo.

ooo, I have 64-bit ubuntu (Karmic Koala). Is the 32 bit flash installed by default?

 Raynman I will be checking out your links in a minute, thank you.[U]
[/U]

---

### Post by tom.swartz07 on 2010-04-09
> **littlboz said:**
> ooo, I have 64-bit ubuntu (Karmic Koala). Is the 32 bit flash installed by default?

 Raynman I will be checking out your links in a minute, thank you.[U]
[/U]

HAHA! Ive been eying this thread for a while just to see if this would pop up.

Follow the link in my sig to get the full 64 bit version of Flash. I have it and it works great!

---

### Post by adam22 on 2010-04-09
I would give 64 bit flash a go. I looked that the guide posted above, it'll work, but it can be done graphically without the terminal...

---

### Post by littlboz on 2010-04-09
What do you mean by graphically?

I also found a stumbling block on that tutorial

gksu nautilus /usr/lib/flashplugin-installer
when I type that in it states could not find "/usr/lib/flashplugin-installer"

wait, as I am writing this I remember I went to package manager to delete anything with the name flash in it. I deleted a file called "flashplugin-installer" 0.o.

...The reason I used package manager is because the script 
$ sudo ./flash_remove.sh 
was not working either.

---

### Post by QIII on 2010-04-09
Just don't go to Hulu with 64 bit Flash for Linux.

The bouncers show you to the door.

---

### Post by adam22 on 2010-04-09
I mean you don't need the command line. If you want to try 64 bit flash, remove the wrapper and installer for 32bit flash from synaptic.

Then, terminal, sudo nautilus.

Extract the 64 bit tar (downloads folder will be fine) and you should get a .so file. Copy this file, and then go to the root folder, /usr/lib/mozilla/plugins and copy it there. Open up firefox, and all should be well.

---

### Post by ssulaco on 2010-04-09
> **littlboz said:**
> 
~Is there a button to click on these forums to state that a problem is solved?
yes.....click thread tools at the top of this tread...

Take a look at this for fixing flash problems
[http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1)

---

### Post by ubiquitousblake on 2010-04-09
Though this does not directly address your problem, FireFox is notoriously slower on Linux than on other platform. And again- Flash settings aside, maybe you could try a WebKit browser like Chromium? They're a bit more heavy on processor cycles, but they're much faster. Also, if you really love your FireFox add-ons, try giving the Chrome add-on repositories a look through. They're getting more and more every day. I switched to Chromium when X-Marks was officially developed for Chrome and I've never looked back. I use Chromium because its open source, but Chrome is just as viable in my opinion. If you're looking for a smoother browsing experience on Linux, this might be worth looking into! 

I hope you end up with your problem fixed!

---

### Post by littlboz on 2010-04-09
> **tom.swartz07 said:**
> HAHA! Ive been eying this thread for a while just to see if this would pop up.

Follow the link in my sig to get the full 64 bit version of Flash. I have it and it works great!

When I went to type in the code: "gksu nautilus /usr/lib/flashplugin-installer

I got 

boswell@boswell-desktop:~$ sudo nautilus
[sudo] password for boswell: 

(nautilus:2729): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:2729): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Initializing nautilus-gdu extension

** (nautilus:2729): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2729): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2729): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.





adam22, when I typed in "sudo nautilus" i got the following:

boswell@boswell-desktop:~$ sudo nautilus

(nautilus:2950): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:2950): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Initializing nautilus-gdu extension

** (nautilus:2950): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2950): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2950): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.



Ssulaco, I installed the "automated installer created by carlee"
I then installed the flashplugin-nonfree

When I went to youtube the video embedding was blank







(Did I delete to much flash stuff :-P)

---

### Post by adam22 on 2010-04-09
Just open the file manager and see if you can access the root directory.

---

### Post by littlboz on 2010-04-09
> **adam22 said:**
> Just open the file manager and see if you can access the root directory.



sorry, you'll have to give me baby steps on where the file manager is.

---

### Post by adam22 on 2010-04-09
Nautilus is the file manager. It's like "My Computer" in windows. I am using Kubuntu though and the file manager is called Dolphin...

---

### Post by littlboz on 2010-04-09
> **adam22 said:**
> Nautilus is the file manager. It's like "My Computer" in windows. I am using Kubuntu though and the file manager is called Dolphin...

			 		 	 	  
 Alright, I found it but now it states "the folder contents could not be  displayed. 'You do not have the permissions necessary to view the  contents of "'root.'"" which is rather odd because I am using the only  account ever made on my ubuntu so why would it be restricted?

---

### Post by adam22 on 2010-04-09
That's what I thought...gksu nautilus or sudo nautilus should open the file manager in a window, then you will have access to the root directory.

With Linux, you do not run as a super user. You may be the admin, but you have to request super user power in order to run tasks that require elevated privelages. It's similar to the UAC in Windows 7, in theory.

---

### Post by tad1073 on 2010-04-10
this should do the trick:
[http://ubuntuforums.org/showpost.php?p=8522076&postcount=1](http://ubuntuforums.org/showpost.php?p=8522076&postcount=1)

---

### Post by littlboz on 2010-04-10
> **tad1073 said:**
> this should do the trick:
[http://ubuntuforums.org/showpost.php?p=8522076&postcount=1](http://ubuntuforums.org/showpost.php?p=8522076&postcount=1)


That looks excellent but I get this error on the first step:

boswell@boswell-desktop:~$ sudo add-apt-repository ppa:user/ppa-name
HTTP Error 404: Not Found

---

### Post by mellort on 2010-04-10
Hey littlboz,

Installing the 64-bit Flash version might solve your problems, but in general, many Linux users have performance issues with Flash. If you use the [Chromium]("http://digitizor.com/2009/11/06/how-to-install-chromium-browser-in-ubuntu-9-10-karmic-koala/") browser, you could tryout the [YouTube HTML5 demo]("http://www.youtube.com/html5"), which modifies your YouTube preferences so that videos are played without using Flash.

Cheers

---

