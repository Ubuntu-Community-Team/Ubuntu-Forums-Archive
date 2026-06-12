---
title: "Installing Java via terminal, got to license agreement, stuck. No place to approve it"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by swarup on 2009-05-22
I downloaded the ubuntu-restricted-extras using a terminal window. It downloaded everything, and then during the install got to a window showing "Configuring sun-java6-jre". It is a license agreement screen, which looks look on my approval of which, it would go ahead and install java. But scrolling down to the bottom of the license agreement, there is no box to check or anywhere to indicate my approval. I tried hitting the "enter" key, but nothing happens. It just sits there. And if I try to close the terminal window, a message comes outside of terminal window which says "caution: there is a process running in terminal window. Stopping terminal window will kill it. Do you want to close it?" So I didn't close it. But I don't know what else to do. Is java installed yet? Or what more do I need to do?

---

### Post by taurus on 2009-05-22
You can highlight the <OK> by pressing the Tab key.  You need to accept the license agreement first before it can install java on your machine.

---

### Post by AndyCooll on 2009-05-22
Usually you do tab and return.

However you can also install all that using Synaptic (System > Administration > Synaptic Package Manager) if it gives you problems.

:cool:

---

### Post by swarup on 2009-05-22
> **taurus said:**
> You can highlight the <OK> by pressing the Tab key.  You need to accept the license agreement first before it can install java on your machine.

Wow, thank you. Sometimes the simplest things can create such a big problem. :p

---

### Post by swarup on 2009-05-22
> **AndyCooll said:**
> Usually you do tab and return.

However you can also install all that using Synaptic (System > Administration > Synaptic Package Manager) if it gives you problems.

:cool:

Thanks-- everything seems to have worked fine. :p

---

### Post by littlejay on 2009-06-17
Ok so I basically did the same thing as OP with the exception that I did not run the ubuntu-restricted-extras, instead I run a java package directly from Sun's homepage, but most importantly I DID NEVER HIT TAB AND ENTER, thus I never accepted the license agreement, AND I SHUT DOWN THE TERMINAL. Now I am stuck with a broken version of sun-java6-jre and I can neither get rid of it nor fix it! It makes me want to scream out loud.

The results were that first it locked my dpkg or something, I just got the errror message that the system was "unable to get an exclusive lock". I solved that by rebooting the computer.

Now I have tried a bunch of stuff to get rid of my broken java file(s?) but I can't get it to work! I have already tried the following:

**In Terminal: **
*sudo dpkg --configure -a*
[B]
Seems to work, I continue with:[/B]

*sudo apt-get update*
[B]
All seems fine:
[/B]
[I]Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Reading package lists... Done[/I]

**Then:**

*sudo apt-get install ubuntu-**restricted-**extras*

**Which results in:**

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-10-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-10-0ubuntu2) but it is not installable
                 Recommends: gsfonts-x11 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/I]

**Ok, so I try:**

*sudo apt-get -f install*
[B]
And it replies:[/B]

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  sun-java6-jre
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing sun-java6-jre (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 sun-java6-jre
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

**So I repeatedly try switching between:** 
[I]
sudo apt-get upgrade

 sudo apt-get -f install[/I]

**No luck.**

[B]In Syntaptic package Manager:
[/B]
I filtered out the broken file (sun-java6-jre) and tried to remove it (and get this error message: *E: sun-java6-jre: Package is in a very bad inconsistent state - you should try to reinstall it*) and tried to force another version (nothing happened).

Ok, so I simply try to re-install it by downloading the package ( sun-java6-jre_6-10-0ubuntu2_all.deb) and run it from the desktop. Package installer starts and I get this error message:

*Error: Can't install 'sun-java6-bin'*

Now there's something wrong with sun-java6-bin too? One last try, I go to Add/remove... and I select Sun Java 6 Runtime. It says I can't install sun-java6-bin and that I should consult Syntaptic Pacakge Manager, which I already have..

I'm out of ideas, please help me. And I'm also a total beginner on Ubuntu (thus the shutting down of the license agreement in the first place) so simple step-by-step instructions would be appreciated.

-::UPDATE 1::-

I managed to make the broken package disappear from Synaptic Package Manager by following these steps: [http://itechlog.com/linux/2008/12/18/fix-broken-package-ubuntu/](http://itechlog.com/linux/2008/12/18/fix-broken-package-ubuntu/)

It still doesn't work to install new packages though. Says I have had(!!) a broken package.

-::UPDATE 2::-

PROBLEM SOLVED!

After my manual deletion of the sun-java6-jre package (see update 1) I did this: [http://ubuntuforums.org/showpost.php?p=4848877&postcount=15](http://ubuntuforums.org/showpost.php?p=4848877&postcount=15)

Then I just run a 'sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin' and voila!

Tab, Enter, Ok, I win.

---

### Post by samthethe on 2012-05-07
I thought it was broken.

Man how dumb, why not just have some text somewhere saying "Press tab", or just highlight automatically.

I tried "y" then enter, "yes" then enter, enter x 100, space, etc.

---

