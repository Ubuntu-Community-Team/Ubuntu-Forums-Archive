---
title: "Terminal question sudo apt-get install gimp"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2010-10-11
Hi All,

I just upgraded to 10.10 and today wanted to install GIMP.
As per the instructions on the gimp.org website I tried sudo apt-get install gimp.

I then received a message in the terminal that I needed extra files and that would require 23 megabytes of space.  Did I wish to continue? Y/n

When I type Y then hit enter the process is aborted.  No matter what I type when I hit enter the process is aborted.

I was able to install GIMP via Synaptic but I wonder what the problem with the terminal is and how to resolve it?

---

### Post by slakkie on 2010-10-11
Could you copy/paste the input/output and place it here? Use [code]-tags when pasting :)

---

### Post by mr_luksom on 2010-10-11
Hmm... was synaptic open/installing something at the same time by any chance? You can't use two package installers at the same time.

---

### Post by Elaztic on 2010-10-11
Hi, have not yet given 10.10 a go but why don't you use the software center in the 'start' menu?

If you have any other package managers open you will normally get an error....check if you have other open programs.

Hope this helps

---

### Post by GrouchyGaijin on 2010-10-11
> **slakkie said:**
> Could you copy/paste the input/output and place it here? Use [code]-tags when pasting :)
Actually no because since I installed gimp via synaptic I get the message that the latest version of gimp is already installed if I try to run sudo apt-get install gimp in the terminal.

---

### Post by aeiah on 2010-10-11
yea you must remember that synaptic is just a graphical front end for apt, and you'll get a locking error if using both at the same time. if that isnt the issue, then the errors produced should give you some clues. could be that one of the repositories is down, your connection is flaky or you've manually compiled something in the past that's causing a dependency conflict

---

### Post by GrouchyGaijin on 2010-10-11
> **mr_luksom said:**
> Hmm... was synaptic open/installing something at the same time by any chance? You can't use two package installers at the same time.
Nope nothing else was open - just the terminal.

---

### Post by ankspo71 on 2010-10-11
Hi,
Have you tried restarting your computer and trying it again? Once in a while the update manager runs in the background to collect update information, and that can cause other package managers (or apt-get install) to give an error about having another package manager in use.
Hope this helps.

---

### Post by GrouchyGaijin on 2010-10-11
No I haven't.  The next time I need to install something I'll see if it happens again.  What is the command to upgrade or update a package?

Thank you!

---

### Post by GrouchyGaijin on 2010-10-11
I just checked the update manager and there were six updates totaling 23 megabytes.  The same number I saw in the terminal message.  I guess the update manager was or had been running at the same time.

Thank you for your help.

---

### Post by slakkie on 2010-10-11
> **GrouchyGaijin said:**
> Actually no because since I installed gimp via synaptic I get the message that the latest version of gimp is already installed if I try to run sudo apt-get install gimp in the terminal.

Well, uninstall it first (I placed it in my previous comment, thought it would be the logical thing to do, removed it. Appears my logic is flawed).

---

### Post by migs73 on 2010-10-11
I had the same thing trying to download XBMC. It turned out that it was not aborted at all but is in fact finished. Check your applications > graphics menu and see if Gimp is there. That would be why Synaptic/apt is telling you it is already installed.

---

### Post by ankspo71 on 2010-10-11
> **GrouchyGaijin said:**
> What is the command to upgrade or update a package?

Hi, you can use either of these commands to upgrade a package. But first it is best to use the **sudo apt-get update** command to refresh the repositories.

```
sudo apt-get install packagename
```
If there is an update available, it will tell you about it and allow you to upgrade it. 


```
sudo apt-get upgrade packagename
```
This will upgrade the package if there is an upgrade available. This one doesn't show as much detail though.


You can find more information about apt-get and apt-cache by typing these commands in the terminal:
```
apt-get --help
man apt-get
apt-cache --help
man apt-cache

```
Hope this helps.

---

