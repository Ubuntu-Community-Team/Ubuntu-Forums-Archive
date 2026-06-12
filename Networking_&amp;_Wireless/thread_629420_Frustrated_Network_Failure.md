---
title: "Frustrated Network Failure"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by Jumpmasterrt on 2007-12-02
Just like many others here, I've read through every thread and every post here and on google and in at least 3 books on Ubuntu and countless other blogs and video instructions. The only good thing about it is I've learned OTHER nifty tricks so it hasn't been a total waste of time.

I can NOT get my Ubuntu and Windows to talk to each other. I can ping Ubuntu from Vista but not the other way.

I have tried smb and nfs setups, I've tried manually configuring Samba and using SWAT. The only thing is, I don't know what's right or not.

I just need ONE SHARE and a printer between the two (Ubuntu server, Win Client).

They're both on the same subnet, in the same workgroup (no spelling errors) and as far as I can tell, have the sharing enabled correctly locally.

I'm willing to reload Ubuntu to make this work. (I haven't gotten far enough in the configurations that I can't redo it).

---

### Post by Jumpmasterrt on 2007-12-03
Bump

---

### Post by Jumpmasterrt on 2007-12-05
Ok, well, I guess I didn't come right out and say it, but I NEED HELP.

---

### Post by infinitezero on 2007-12-07
Follow this link and download the Samba Install on Kubuntu 7.04 - rev1.3.pdf.tar.gz .


[http://ubuntuforums.org/showthread.php?t=575214](http://ubuntuforums.org/showthread.php?t=575214)


I hope that helps you out,
iz

---

### Post by jonandrews on 2007-12-07
I've done a step-by-step illustrated guide showing how to network Ubuntu & Windows PC's, biased towards people more familiar with Windows.

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

Let me know if it works for you..

---

### Post by Jumpmasterrt on 2007-12-08
Jon, 

At least now I know where the problem is. You stated in your step one that right out of the box, Ubuntu should be able to see the windows network. In my case, it doesn't. Now, I know the obvious answer is, "Well then your windows machine isn't shared." That's not true as I can see my win net on any win machine.  Coincidently I don't see my Ubuntu machine when I click that either.

Does it matter that I'm using Win Vista and not XP?

After following your steps, shouldn't the shared folder have the shared icon? It's listed in the System -> Admin -> Shared folders directory and has the shared folders Icon there. I thought I remembered it being a shared icon in both places.

---

### Post by Jumpmasterrt on 2007-12-08
Ok, now I'm confused. The network all of a sudden appeared.
but
I don't have a workgroup called MSHOME, yet I see one listed in my windows network with my Ubuntu machine listed and accessible. The workgroup I WANT to be able to get into I can't (Folder contents could not be displayed).

This all takes place on my Ubuntu machine, I still don't see anything on my windows box

However, this is farther than I've gotten using any other method, so YAY!!! LOL

---

### Post by Jumpmasterrt on 2007-12-08
Oh good grief.

I guess it just takes forever for the things to connect? I'm beginning to see more stuff. I'll wait a couple of hours before continuing with questions.

---

### Post by Jumpmasterrt on 2007-12-08
Well, it all kind of shows up now, only problem is, I can't access the sub folders or files on the windows machine with Ubuntu.  I get "Nautilus cannot display 'smb://path'" and my local Ubuntu printer isn't showing in windows.

---

### Post by Jumpmasterrt on 2007-12-10
anyone have an answer for this?

---

### Post by Jumpmasterrt on 2007-12-12
No pressure, but I leave for Iraq VERY soon and I'd like this fixed so my wife can use the printer.

---

### Post by gilf on 2007-12-17
Just suggesting a possibility -- am unfamiliar with Vista.

Check that a firewall in the windows machine isn't interfering.

Check that folder and subfolder permissions in Ubuntu aren't also interfering.

I'm having the same error message in a Ubuntu to Ubuntu access via samba -- trying to find a solution. It even shows up when I try to access a shared folder via Places-Network on the SAME machine the folder is on.

---

### Post by buccaneere on 2007-12-18
> **Jumpmasterrt said:**
> anyone have an answer for this?

bump...

not ANY folders can be displayed!

...and by the way jmrt, I couldn't vista to see VISTA, and only XP sometimes.

Why can folders not be displayed???

---

### Post by gilf on 2007-12-18
Okay got my own samba network problem solved,
this set of instructions absolutely worked for me:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

