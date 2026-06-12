---
title: "Installing downloaded programs + a few other ?'s"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Cornphlake on 2009-05-19
I am a long time Windows user and have been on a big open-source kick recently with Thunderbird, Firefox, and Open Office.  I am still limited by the OS (Vista currently) so I chose Ubuntu to begin learning from.

My main concern is installing downloaded programs.  This is my first shot at Linux so I am running (and currently typing from) Ubuntu within Sun Virtualbox within Vista.

So what I have noticed thus far:

Windows = download file, double click, hit next a few times & you're done.

Ubuntu = Not so much, doesn't work that way.  I have search and searched for hours with results saying installations are easier in Ubuntu than Windows and keep seeing the same explanations about using Add/Remove or Synaptic Package Manager.  OK, someone prove it to me then.

I have a 1985 Corolla GTS with a tunable fuel management system that I need to be able to access/use, so the first thing I am trying to download and install is this:

[http://www.efianalytics.com/TunerStudio/](http://www.efianalytics.com/TunerStudio/)
from this page:
[http://www.efianalytics.com/TunerStudio/beta/](http://www.efianalytics.com/TunerStudio/beta/)

I downloaded the latest release [TunerStudioMS_v0.988.5.tar.gz]("http://www.efianalytics.com/TunerStudio/beta/TunerStudioMS_v0.988.5.tar.gz").  I am very particular about my folders and how I arrange things in Windows, so within my /home/russ/ folder I have created /home/russ/Download.  I have the tar.gz file sitting there, as well as a /home/russ/Download/TunerStudio folder with everything extracted sitting right next to it.  I have tried everything I know currently to get this damn thing to install.  Applications-> add/remove, System->admin->synaptic, and trying to run TunerStudio.sh as per the "readme" file.  I also read that downloaded files need to be in /usr/share, so I put both my unzipped TunerStudio folder as well as the tar.gz file in /usr/share but it still does not show up in add/remove or synaptic.

I have used the DOS prompt within windows many times and can navigate to any folder and run just about whatever program I wish... I try the terminal in Ubuntu for the longest time and then I stumble upon something after searching the internet saying if I want to run said file, I need to put a ./ before it.  Why is this?  **(I really am looking forward to an answer to this one also)**

Anyway, now that I found that out, within terminal, ~/Download/TunerStudio$ ./TunerStudio.sh again produces no results.

I am aware that Tuner Studio needs JRE to operate, so I downloaded "jre-6u13-linux-i586.bin".  After searching someone suggested to chmod and add executable capability to the .bin file.  I did, typed ./jre-6u13-linux-i586.bin in terminal and it appears to have installed correctly.

The few times I have used unix in the past, you were able to "su" to gain admin rights and it would remain until you were to exit.  With Ubuntu, do you have to type "sudo" every time you wish to gain admin rights or can you still "su"?

I was super frustrated when I first started with Vista for the sole reason it took me forever to find the TCP/IP properties to enter a static IP address.  Once I caught on and now that I've learned Vista I wouldn't turn back to XP and love it.  I'm sure the same will happen with Ubuntu, but it's just that initial lerning curve (which seems to me as extremely huge) where I get super frustrated and want to give up.

Sorry for the extremely long novel but I have too many questions.  Any advice is welcome and look forward to all responses.  So where am I going wrong and can someone point me in the right direction?

Thanks Everyone!!!
-Russ

---

### Post by barnex on 2009-05-19
Have you tried applications > add/remove software yet? You will notice that installing software in linux is actually very simple, you just check the programs you want, click "apply", and you're done.

For applications that are not in this repository, a usual procedure is either:

chmod u+x installer.sh
sudo ./installer.sh

or in other cases:

make
sudo make install


Hope this helps you!

---

### Post by qjmoss on 2009-05-19
I skimmed your thread.


I see that your trying to install tar.gz files.


I avoid this.


Look for .deb files, that will remind you more of a windows click and install.


I'll look for a tutorial on install tar.gz files, i've completely forgot how.



I think... if you right click them and let them run as executable, it will install.  But i'm not sure, it's been awhile ! :(

---

### Post by qjmoss on 2009-05-19
> The few times I have used unix in the past, you were able to "su" to gain admin rights and it would remain until you were to exit.  With Ubuntu, do you have to type "sudo" every time you wish to gain admin rights or can you still "su"?


Sudo is a security feature, I think that when you type sudo in front of a command that it enables it for 15 minutes or so.  There is a way to run in root, but it's something that everyone says to avoid.

---

### Post by Mornedhel on 2009-05-19
You are still operating under the Windows paradigm of "search for installer on the web, download installer, execute installer".

You need to understand that Ubuntu, being a derivative of Debian, has its own method for installing software.

There probably is a sticky somewhere on how to install/remove programs, but here is the gist of it :

First, check that the software you want to install is available in the standard repositories. To do this, open Synaptic, search for its name or something you think might be in the description. If it's there, just click the package and mark it for installation. Then, click Apply ; everything necessary (libraries, etc.) will be fetched from the Ubuntu repositories, installed, and in most cases a menu entry will appear somewhere in Applications. (There are other methods for installing from the repository, for instance through Add/Remove, or on the command line through apt-get or aptitude ; the end result is identical, but Synaptic offers greater control than Add/Remove and is more user-friendly than the command line.)

If not available in the repositories for whatever reason (proprietary software or no one bothered to package it for Ubuntu) you can revert to your Windows habits. Get the package (something.deb) from the website, install it with gdebi ; failing that, get the source and compile it (ask again here if you need help for that). Some people also set up their own repositories. You can then add the repository's URL to your list of repositories and everything on it will show up in Synaptic.

In the case of a JRE, you should have installed sun-java6-jre from Synaptic. It's no big deal if you installed it by hand, but the updates won't be handled by Ubuntu.

Su'ing is not possible anymore in Debian or Ubuntu, for security reasons (root accounts are easier to break in if you already know the username, among other reasons). You can use sudo -i to enter a root shell.

Adding ./ before something.sh is necessary because the shell tries to interpret something.sh as an alias to a command (the actual executable being somewhere in $PATH). If no such command exists (there is no executable something.sh nowhere in any folder in PATH, type echo $PATH to get the list of such folders) it returns with a command not found message. You need to specify "in this directory", which is what . means (same as DOS : . is "here", .. is "parent directory").

Hope it helps, ask again if more clarification is necessary.

---

### Post by lovinglinux on 2009-05-19
> **Cornphlake said:**
> I downloaded the latest release [TunerStudioMS_v0.988.5.tar.gz]("http://www.efianalytics.com/TunerStudio/beta/TunerStudioMS_v0.988.5.tar.gz").  I am very particular about my folders and how I arrange things in Windows, so within my /home/russ/ folder I have created /home/russ/Download.  I have the tar.gz file sitting there, as well as a /home/russ/Download/TunerStudio folder with everything extracted sitting right next to it.  I have tried everything I know currently to get this damn thing to install.  Applications-> add/remove, System->admin->synaptic, and trying to run TunerStudio.sh as per the "readme" file.  I also read that downloaded files need to be in /usr/share, so I put both my unzipped TunerStudio folder as well as the tar.gz file in /usr/share but it still does not show up in add/remove or synaptic.

It won't show up anywhere. The file you downloaded is the source code, which is used to compile the program yourself, which means you will actually build the program from the source code created by the programmer. I wouldn't bother to compile software, unless you really need it. Most of the time, you can get the software you want from the repositories (Add/Remove and Synaptic) or through deb files ([GetDeb](http://www.getdeb.net/), Launchpad), which are similar to Windows installation programs (exe). If you find a deb file, just double click it to install.

You might want to read this tutorials before proceeding:

[https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html)

If you need to compile, then you could read this:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)


> **Cornphlake said:**
> I have used the DOS prompt within windows many times and can navigate to any folder and run just about whatever program I wish... I try the terminal in Ubuntu for the longest time and then I stumble upon something after searching the internet saying if I want to run said file, I need to put a ./ before it.  Why is this?  **(I really am looking forward to an answer to this one also)**

You need the ./ to make sure the program is running from the current folder and not from the system folders. I think is a security feature, to make sure you don't run the wrong file.

> **Cornphlake said:**
> Anyway, now that I found that out, within terminal, ~/Download/TunerStudio$ ./TunerStudio.sh again produces no results.

First make sure the file is allowed to execute as program, by accessing it's properties, then you might need to start with the sudo command. Since you are installing stuff, you need root access.

> **Cornphlake said:**
> I am aware that Tuner Studio needs JRE to operate, so I downloaded "jre-6u13-linux-i586.bin".  After searching someone suggested to chmod and add executable capability to the .bin file.  I did, typed ./jre-6u13-linux-i586.bin in terminal and it appears to have installed correctly.

You can install java from the Medibuntu repositories. It's pretty easy.

> **Cornphlake said:**
> The few times I have used unix in the past, you were able to "su" to gain admin rights and it would remain until you were to exit.  With Ubuntu, do you have to type "sudo" every time you wish to gain admin rights or can you still "su"?

It's a security feature. Sudo will expire after a few minutes. You can increase the time for expiration, but I don't remember how and I don't recommend.

> **Cornphlake said:**
> I was super frustrated when I first started with Vista for the sole reason it took me forever to find the TCP/IP properties to enter a static IP address.  Once I caught on and now that I've learned Vista I wouldn't turn back to XP and love it.  I'm sure the same will happen with Ubuntu, but it's just that initial lerning curve (which seems to me as extremely huge) where I get super frustrated and want to give up.

Linux is a different OS, so the learning curve might be steep sometimes, but the good thing is that you have the support from this community. So don't give up so fast.

---

### Post by Cheesemill on 2009-05-19
Also check out this link

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Cheesemill

---

### Post by oldos2er on 2009-05-19
What the OP downloaded is a Java .jar file that comes with a shell script to start the program.

   To the OP: To install Java, run this command in a terminal:
```
sudo apt-get update && sudo apt-get install sun-java6-jre
```

 After this command is finished (hopefully it was successful), "cd" to the tunerstudio directory, and run
```
java -jar tunerstudioms.jar
```
 Let us know if it worked.

---

### Post by Cornphlake on 2009-05-19
> **oldos2er said:**
> What the OP downloaded is a Java .jar file that comes with a shell script to start the program.

   To the OP: To install Java, run this command in a terminal:
```
sudo apt-get update && sudo apt-get install sun-java6-jre
``` After this command is finished (hopefully it was successful), "cd" to the tunerstudio directory, and run
```
java -jar tunerstudioms.jar
``` Let us know if it worked.

I would say that would have worked but right before you replied I finally got it.  The java .bin I downloaded and attempted to install (before I knew of the repositories and installing that way) didn't go through.

I reinstalled JRE 6 through synaptic and after this, I am able to either lanch from the terminal or double-click TunerStudio.sh.

Thank you all for your prompt responses, it means alot to be welcomed here so quickly and warmly.  Automotive forums are exactly the opposite, where you need to prove yourself to a gaggle of a-holes, which is what I'm used to.

But wow... I guess you start seeing all that code...

*```
sudo apt-get update && sudo apt-get install sun-java6-jre
``````
java -jar tunerstudioms.jar
``` *

... like the guy in the first Matrix... "blonde, brunette, red-head"... but just starting out that does not look easy to remember every time something is downloaded and installed that can't be located in the repositories.

Again, thanks everyone!!!!  BTW I am not giving up this easy, just my first speed-bump of many I'm sure.

---

