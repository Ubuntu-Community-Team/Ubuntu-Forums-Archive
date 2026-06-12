---
title: "downloaded Firefox HOW TO INSTALL IN UBUNTU"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by linux_nood on 2009-06-01
hey u guy i downloaded firefox from there website now i need to install in the comp....

---

### Post by Didius Falco on 2009-06-01
What is the complete file name of the file(s) you downloaded?

Regards,

Didius

---

### Post by linux_nood on 2009-06-01
firefox-3.0.10.tar.brz...and i extract from the archive manager and put in desktop...

---

### Post by Elfy on 2009-06-01
what version of ubuntu are you using?

---

### Post by Didius Falco on 2009-06-01
Here are instructions on how to build and install from source file:

[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

I'm curious as to why you just didn't use the repository, though - I'm running FF 3.0.10 and I got it through Updates....What version of Ubuntu are you using?

Regards,

Didius

---

### Post by linux_nood on 2009-06-01
im running ubuntu 9.04 Jaunty Jackalope

---

### Post by Didius Falco on 2009-06-01
Open **System/Administration/Synaptic Package Manager** and search for Firefox - 3.0.10 is available there.

No need to go through the hassle of compiling your own copy, and it is always better to use the repositories when possible - less hassle with updates, etc.

Regards,

Didius

---

### Post by linux_nood on 2009-06-01
i reinstall firefox and when i open it this comes up.....
 error 
 could not launch application
 failed to execute child process "firefox" (no such file or directory)

---

### Post by samden on 2009-06-01
It is unclear what you mean when you say you "reinstalled" firefox. Please explain exactly what you have done. 

In the meantime, forget about the file you downloaded. Just:

Go to the Applications menu, select "Add / Remove".

Find Firefox.

Select it and click "Apply changes"

That will download and install it to your computer. This is always the best way to install software and should do it perfectly (usually!). Only on very rare occasions would you need to download a file from a website to install. Ubuntu is far simpler to install software on than Windows - just use the "add/remove" application!

---

### Post by linux_nood on 2009-06-01
i try that and firefox is all ready install in the system but is just dont wanna run....
so i when to mozilla and download another but i just cant install that other firefox...

---

### Post by Didius Falco on 2009-06-01
Did you use the "reinstall" option in Synaptic? If not, try that first.

Regards,

Didius

---

### Post by linux_nood on 2009-06-01
no it just dont wanna work i am using the computer with the problem.....
but because i downloaded firefox  i cant istill search the web..
i dont really know what is going on with firefox

---

### Post by Didius Falco on 2009-06-01
> **linux_nood said:**
> no it just dont wanna work i am using the computer with the problem.....
but because i downloaded firefox  i cant istill search the web..
i dont really know what is going on with firefox


That's what we are trying to fix. Go to Synaptic, search for Firefox and and "mark for reinstallation". After it reinstalls, try it.

If it doesn't work, open a Terminal and try ti run it by typing ```
firefox
```

If that doesn't work, try it with ```
sudo firefox
```

Then let us know the results and we can work from there. Sorry for the delay in answering - I'm testing the Karmic Alpha and had to file a bug report myself. :tongue: 

Regards,

Didius

---

### Post by samden on 2009-06-01
You aren't being very clear sorry, if you are "using the computer with the problem" how are you on Ubuntu Forums if Firefox isn't working???

By "no it just dont wanna work" do you mean 
- no you have not tried reinstalling from synaptic? If so, TRY THIS.
- you have done that but it still doesn't work?

Have you tried rebooting? This should be unnecessary but computers are fickle things sometimes, it often pays to try...

Please be clearer. We "dont really know what is going on with firefox" either yet and can't help unless we know exactly what you are doing! :)

---

### Post by linux_nood on 2009-06-01
this is how im able to connect to the web...
i when to add/remove and added seamonkey web browser...
after that i when in seamonkey and when to mozilla.com and downloaded firefox 3.0 
check the website...[http://www.mozilla.com/en-US/firefox/personal.html](http://www.mozilla.com/en-US/firefox/personal.html) on the botton is the download now icon..

after that i when to extract and put it in the desktop and open the folder and click on firefox.....and firefox only works with  that folder

here is what came up in the terminal look at the screenshot
and the other screen is what comes up when i use the firefox icon in [B]application/internet/firefox web browser
[/B]

---

### Post by Didius Falco on 2009-06-01
In the Terminal type ```
sudo apt-get install --reinstall firefox-3.0
```

This will force a re-install of Firefox. After it re-installs, try it again.

Regards,

Didius

---

### Post by linux_nood on 2009-06-01
i really thank u Didius Falco for all ur help..
the code 
sudo apt-get install --reinstall firefox-3.0i was able to reinstall firefox but dont get online with the icon...

but firefox just dont work with the icon i istill get the error window from the screenshot...
i even restarted the computer but no firefox with the icon only in that folder.....
look at the screenshot that is the folder i downloded from firefox the icon that says "firefox" is the one that get me connected to the web....

---

### Post by Didius Falco on 2009-06-01
It seems that the folder on your desktop has "hijacked" your Firefox installation. Are all your bookmarks and extensions showing up when you start it from that folder on your desktop?

Smart thinking to grab that other browser to use until you can get Firefox straightened out. <G>

Regards,

Didius

---

### Post by linux_nood on 2009-06-01
i really dont know but u know im going to reinstall the os .....
ill let u know what happend

---

### Post by Didius Falco on 2009-06-01
Okay...Good luck!!

Regards,

Didius

---

### Post by linux_nood on 2009-06-01
hey i try the live session cd and firefox work with the icon...
what could u tell me about that

---

### Post by adit on 2009-06-01
See post #8
> failed to execute child process "firefox" (no such file or directory)

You have installed firefox in the Desktop in a local folder.  The launch script is inside the local folder.  I think you tried to launch firefox by clicking the shortcut in the main menu.  The shortcut in the main menu is actually pointing to /usr/bin/firefox.  Edit the shortcut to point to the launch script located in your local installation directory.

---

### Post by neo.patrix on 2009-06-01
I don't understand this. Firefox is there by default with your Ubuntu OS , when you install it, what is the need to download it from Internet, unless you want to do some private development on it.

---

### Post by linux_nood on 2009-06-01
i know that it was there from  default but it did not work from default so i try fixing it but it just stop working....
and now am in another computer

---

### Post by neo.patrix on 2009-06-01
Can you go back to your original system on which you are trying to get firefox working , try out following commands and post the output

```

aptitude show firefox

```

```

ps -e | grep 'firefox'

```

---

### Post by bacardiandwatermelon on 2009-06-01
> **adit said:**
> See post #8


You have installed firefox in the Desktop in a local folder.  The launch script is inside the local folder.  I think you tried to launch firefox by clicking the shortcut in the main menu.  The shortcut in the main menu is actually pointing to /usr/bin/firefox.  Edit the shortcut to point to the launch script located in your local installation directory.

I agree, if you have compiled firefox from source rather than using the repos then you will have to create your own shortcut

---

### Post by linux_nood on 2009-06-01
ok u guys i found the problem....it was the HDD it had some errors on it...
so i put a new HDD in computer and firefox works now.......<<<<<OH YES>>>>
thanks for all yalls help GUYS

---

### Post by adit on 2009-06-01
Please give the full details on how the problem was solved.  It will help anybody reading your thread.
> i put a new HDD in computer and firefox works now.......
Did you install firefox in the new HDD?  Or did you install entire operating system in the new HDD?

---

### Post by madverb on 2009-06-01
This really just seems like someone f---ing with you all.

---

### Post by linux_nood on 2009-06-01
well am running ubuntu 9.04 Jaunty Jackalope as a full operating system on the HDD....
i was able to run it on that bad HDD intill i open firefox and i would not work....
so i run TERMINAL and type FIREFOX and a BUS ERROR message would come up in TERMINAL..

so after that i when to ADD/REMOVE and added SEAMONKEY WEB BROWSER and i was able to search the web..so i when to MOZILLA.COM and download FIREFOX 3.0 and then i extract the file to my desktop and open firefox icon and there it was..... i was able to search the web but only with that folder,,, but not able to open firefox with the ICON NEXT TO THE SYSTEM BAR.....

so i try uploading a new UBUNTU 9.04 Januty i the Bad HDD and it got stop at 78% and then a message come up saying that maybe the HDD had some bad sector on it...

so i just when a put a new HDD and everything when well with the OS and now it runs really good better than before.....

i hope it help someone out there...

---

