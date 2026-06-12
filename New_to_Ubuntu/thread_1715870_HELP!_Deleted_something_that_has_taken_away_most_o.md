---
title: "HELP! Deleted something that has taken away most of my GUI"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by Ghostlove on 2011-03-27
I installed Unity to see what it was all about. Then I decided to uninstall it, so I went into Synaptic Package Manager (do you see where this is going?) and removed four (I think) packages that said they were to do with Unity.

Then most of my GUI disappeared. I can only access Firefox because Tweetdeck opens at startup, and I can click links from there for Firefox to open. My desktop background has disappeared, as have my top and bottom menu bar thingies, and the bar at the top of the Firefox window that has the minimise and close buttons.

I don't know if this is relevant but some of my settings have changed too - for example my mouse is now behaving right-handedly when I had it set left-handedly.

I can't do ANYTHING right now except use Firefox. I can't even get back to Tweetdeck because the bar at the bottom with the buttons for each window is gone.

Please, PLEASE will someone help me get it all back? I'd really appreciate any help you can give.

---

### Post by TeoBigusGeekus on 2011-03-27
Alt+F2 and give
```
sudo apt-get install --reinstall gnome-desktop
```

---

### Post by Ghostlove on 2011-03-27
I just got "Unable to locate package gnome-desktop" :/

---

### Post by Paqman on 2011-03-27
> **TeoBigusGeekus said:**
> Alt+F2 and give
```
sudo apt-get install --reinstall gnome-desktop
```

Right idea, but not quite the right packages. Try:
```
sudo apt-get install --reinstall ubuntu-desktop gdm xorg
```

---

### Post by JamezQ on 2011-03-27
sudo apt-get install --reinstall gnome-desktop

try that but do ubuntu-desktop and not gnome.

---

### Post by Ghostlove on 2011-03-27
> **Paqman said:**
> Right idea, but not quite the right packages. Try:
```
sudo apt-get install ubuntu-desktop gdm xorg
```

All three of those say they are already the latest version. Sorry! Any other ideas?

---

### Post by Paqman on 2011-03-27
> **Ghostlove said:**
> All three of those say they are already the latest version. Sorry! Any other ideas?

I updated that to force a reinstall. What you want is to make the package manager check that all their dependencies are installed.

---

### Post by TeoBigusGeekus on 2011-03-27
> **Paqman said:**
> Right idea, but not quite the right packages. Try:
```
sudo apt-get install --reinstall ubuntu-desktop gdm xorg
```

Did I miss something?

---

### Post by JamezQ on 2011-03-27
Have you tried logging out and at the login screen selecting "Gnome" for the window manager, it should be at the bottom.

There should be safe-mode too.

---

### Post by goldaryn on 2011-03-27
> **TeoBigusGeekus said:**
> Did I miss something?

gnome-desktop is not a default package. check in debfoster

---

### Post by TheNessus on 2011-03-27
nm

---

### Post by Ghostlove on 2011-03-27
> **Paqman said:**
> I updated that to force a reinstall. What you want is to make the package manager check that all their dependencies are installed.

Forgive me if there are errors here, I had to write it down on a piece of paper and type it out!

```
Preconfiguring packages ...
dpkg: failed to open package info file '/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by Ghostlove on 2011-03-27
> **JamezQ said:**
> Have you tried logging out and at the login screen selecting "Gnome" for the window manager, it should be at the bottom.

There should be safe-mode too.

I don't appear to be able to log out...

---

### Post by JamezQ on 2011-03-27
Can you still open synaptic?

If you can try this.

Open History from the File menu.

Maybe we can see what you removed.

---

### Post by Wesnprogamat on 2011-03-27
Please delete this as it seems this won't let me post what I wanted to...

---

### Post by JamezQ on 2011-03-27
> **Ghostlove said:**
> I don't appear to be able to log out...


You can logout via terminal (or alt-f2) using

```
sudo pkill -kill -u username
```

---

### Post by StormNinja3 on 2011-03-27
Perhaps this may help>...If you have a Ubuntu LiveCD(any version)...Place in the CD/DVD Drive...Shut Down the computer and Restart...

Allow the LiveCD version to Run(without installing).  Then In GoTo> Synaptic  Update.  Once inside Synaptic....Scroll through the list of Gnome( just type Gnome in the serch bar) available Installations.  When you find the appropriate Desktop files....write on a piece of paper the exact name..

Now exit the LiveCD....Remove from the Computer and Restart. If you can get  Terminal to Open..type

 Sudo apt-get install   /whateverGnomefilenamesyoufound/

Press enter

Give Password(invisible no dots or asterisks) 

If it does not work..it will not kill your computer.  It will say" Bash command not found"...You will not have solved the problem but it will not be any worse.

Or you may have your GUI back.  Good Luck

---

### Post by Ghostlove on 2011-03-27
> **JamezQ said:**
> Can you still open synaptic?

If you can try this.

Open History from the File menu.

Maybe we can see what you removed.

I can't open Synaptic because I have no menus at the top. If I could, I could just search Unity and probably remember then which packages I removed. Is there a way of opening it from the terminal?

---

### Post by TeoBigusGeekus on 2011-03-27
Try 
```
gksu synaptic-manager
```

---

### Post by JamezQ on 2011-03-27
> **TeoBigusGeekus said:**
> Try 
```
gksu synaptic-manager
```

If this doesn't work, you can view the actual log files like this

```

sudo su **(to become root, so you can see the files)**
cd /root/.synaptic/log/

```

Then you can paste the most recent log or the relevant one here.

---

### Post by Ghostlove on 2011-03-27
(From inside my much-hated Windows partition)

The 10.10 Live CD I have just stops doing anything after I click 'try Ubuntu' unfortunately.

Anyway, now my Ubuntu partition is hanging at the purple screen telling me there are problems with my disk and that they need to be fixed. If and when it does let me in, it lets me in to the text interface only. I don't appear to be able to open the GUI at all.

So I've downloaded a program for Windows which will access my Ubuntu partition and *allegedly* let me save files from it to my external hard drive (important because there are about 70GB of photos documenting the last 5.5 years of my son's life which I haven't had a backup of for about a week).

I am going to backup all of my files, if this works, then make another Live CD and start afresh. Cross your fingers for me that this magic program actually works.

---

### Post by Ghostlove on 2011-03-28
Thanks for all your help everyone, I have one more question:

I've downloaded Maverick's 64-bit Live CD and it's not doing anything. It gets to the purple screen with the 'loading' dots and just hangs there after a while. How do I check if the Live CD is okay and if it's not, should I make a new one?

---

### Post by JamezQ on 2011-03-28
> **Ghostlove said:**
> Thanks for all your help everyone, I have one more question:

I've downloaded Maverick's 64-bit Live CD and it's not doing anything. It gets to the purple screen with the 'loading' dots and just hangs there after a while. How do I check if the Live CD is okay and if it's not, should I make a new one?

Well to check that you should run a checksum test.

You can usually get the checksum to check against at the site you downloaded the cd at. Do you know how to do this?

---

