---
title: "Upgrading Ubuntu on a partitioned system"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by stisoulreaper on 2011-03-27
I am currently running Jaunty on a laptop that I have divided into 3 physical partitions; one for Jaunty and the other two for other OS's. The Ubuntu partiton has been further subdivided into 4 virtual partitions, one each for root, swap, boot and home.

I would like to upgrade to a newer version of Ubuntu, but I have several questions.

First, How would I go about updating the system, while retaining the information on the computer? Would I simply select the preexisting partitions as the new partitions on the partition editor screen?

Second; If I did upgrade, would I have to reinstall all of my drivers, or are they stored in the home partition?

Third, would it be worth it to upgrade from Jaunty? The distro is no longer supported, and I still have occasional issues with flash playing properly, but I don't really have any complaints besides that...

I'm sorry if this is posted elsewhere, but I haven't seen any answers that really satisfy me... If that's the case, I would more than appreciate a link to such a thread!

---

### Post by johntaylor1887 on 2011-03-27
I don't believe you can upgrade from an unsupported ubuntu. If you could, you would probably have to do it one version at a time, which would take a long time and probably not work right. But personally, I would go for a fresh install after backing up all your files.

---

### Post by aaaaalex on 2011-03-27
First: Exactly! You have to double check of course not to format your /home :-D. When done check again. Since you will not delete anything on your /home it will still be there. Most user specific configuration is stored in directories and files beginning with a . in your home dir. If you made some modifications to your system by editing files in /etc you may want to safe those as well. I forget doing that all the time. 

Second: What you mean by 'your drivers'? Did you have to set up a wireless driver with ndiswrapper? You will find that this has improved a lot. Just make sure you have the option to temporarily cable connect your machine. Ubuntu should then pop up a dialogue offering to install additional drivers. 

Third: In my opinion absolutely. The UI has undergone some big improvements - everything looks much slicker. Many pieces of SW that run in the background have been uped and for some stuff there are new default applications - not to mention the improvement in security. 

Just a question? Are you planning to do this by actually upgrading your Ubuntu? From what you are saying it sounds more like a fresh install of a current version. If you are really adventurous you could wait another month and jump straight into Natty Narwhal... There will be some major UI changes as Natty will be using Unity as a default. A classic GNOME Desktop will also be available to choose as a default alternative if i am not mistaken.

---

### Post by stisoulreaper on 2011-04-01
Thanks for the advice!

By drivers, I had meant the printer, wireless drivers, etc. It took me awhile to get them all running properly in the first place (and was a total pain to try and get the media control buttons on the laptop to work!), and my laptop isn't very portable anymore, but I could get it to a cable if need be.

Yea, I guess I intended to say fresh install- I planned to download the iso's and install the new version on top of the old. I had read somewhere that it was advisable to install each new version in succession and not just jump to the newest, or there might be problems with the install.

---

### Post by aaaaalex on 2011-04-01
I dont dist-upgrade from one Ubuntu to the next because it takes much longer as opposed to running a fresh install. Yes you could argue that you have to install all the programmes you that are used again, e.g. Gimp. That only takes a few seconds and runs in the background for each programme. Another argument to do that is because over the course of half a year i tend to install a lot of programs to check them out ending up not using them after a while. Because i also have my /home on a seperate partition the settings for most programs remain intact.

Good luck with your migration ;-)

---

### Post by grahammechanical on 2011-04-01
There are two ways to upgrade.

1) A fresh install using an iso image burned to CD. You can tell the installer to use the same partitions by giving them the same mount points. But do take the advice given earlier not to mark the /home partition for format.

2) Using Update Manager. This utility will tell you that an upgrade is available. It will provide a button to click. In fact you should be seeing it now. The utility will not let you go from Jaunty to Maverick. It will upgrade you to move you from 09.04 to 09.10. Then you click the button again and it will move you to 09.10 to 10.04. Then you click the button again and it will move you from 10.04 to 10.10. I know because I tried this when I had hardware problems and I installed 08.04 and then worked my way up to 10.10.

Regards.

---

### Post by Hedgehog1 on 2011-04-02
> **stisoulreaper said:**
> By drivers, I had meant the printer, wireless drivers, etc. It took me awhile to get them all running properly in the first place (and was a total pain to try and get the media control buttons on the laptop to work!), and my laptop isn't very portable anymore, but I could get it to a cable if need be.

As a test, if you boot off of a 10.04 or 10.10 LiveCD, and select 'TRY' does the LiveCD work with your wireless card out-of-the-box?  A test of this will give you feel of how much pain the install of the newer version will really cause.  You ***might*** find better support of your hardware and less driver setup.  Happy accidents do happen from time to time!

***The Hedge***

:KS

---

