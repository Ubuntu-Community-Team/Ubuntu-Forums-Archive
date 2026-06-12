---
title: "Install Safari using VirtualBox"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by john olson on 2009-11-30
I am a beginner and have a requirement to use Safari. I have read information I should use VirtualBox to allow Safari to run in Ubuntu 9.10. I downloaded and installed VirtualBox OK. I download Safari for linux but I don't know what to do next.

---

### Post by Merk42 on 2009-11-30
Just curious, what is the requirement that you need Safari?

Anyway, back to your question.
VirtualBox is used for running entire operating systems. So you'd need a copy of Windows (Xp, Vista, or 7) and install that in Virtualbox, then install the Safari for Windows version like you normally would.

There is no Safari for Linux, I wonder where you go that.

Another thing would be WINE, but it looks like [that doesn't run Safari flawlessly](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16867)

---

### Post by john olson on 2009-11-30
I just purchased an iMac with tutorials called "one on one". When I sign in to the apple site for the tutorial I get the message that I need Safari to open it.

I am using moxilla/5.0 (X11;U;Linux i686;en-US;rv:1.9.16pre)Gecko/20091129 Ubuntu/9.10(karmic)Shiretoko/3.5.6pre. which maybe the problem. How do I go back before I install Siretoko and check my old version firefox version 3.5.5?

I got the "Safari on linux" from the following site: [http://alicious.com/2009/safari-4-on-linux-download-now/](http://alicious.com/2009/safari-4-on-linux-download-now/)

I have an XP CD and could try to install it on VirtualBox. Is there any guide some where to help me with that?

---

### Post by Merk42 on 2009-11-30
I'm going to guess the "One on One" tutorials are about OSX and its software, if so running it in Linux will be of no use anyway. 

Running shiretoko may be a problem. What is the link you're trying, I'll attempt it in Firefox 3.5.5.  How did you install 3.5.6 anyway?

Installing XP in Virtualbox is pretty straightforward.  Maybe just have to [read the manual](http://download.virtualbox.org/virtualbox/3.1.0/UserManual.pdf)

---

### Post by john olson on 2009-11-30
I called my son and had him try his firefox version 3.5.5 and it worked OK so how do I uninstall version 3.5.6 and reinstall 3.5.5?

---

### Post by Merk42 on 2009-11-30
How did you install 3.5.6 in the first place?

---

### Post by john olson on 2009-11-30
I have checked my notes and bookmarks but can't find any information on where i downloaded the version 3.5.6 pre. Sorry

---

### Post by Merk42 on 2009-12-01
Um you could try opening up synaptic package manager, clicking status (bottom left), filtering by installed and seeing if it's in there? It may be under firefox or shiretoko I don't know.

---

### Post by jrrader on 2009-12-01
I'm confused.  Did you remove OSX completely on your new Imac?  The one on one tutorials are to teach you how to use OSX.

---

### Post by Merk42 on 2009-12-01
> **jrrader said:**
> I'm confused.  Did you remove OSX completely on your new Imac?  The one on one tutorials are to teach you how to use OSX.
Ugh that's what I thought.
> **Merk42 said:**
> I'm going to guess the "One on One" tutorials are about OSX and its software, if so running it in Linux will be of no use anyway.
Well let's try to help with the problem anyway

---

### Post by jrrader on 2009-12-01
You can have firefox fool the website into thinking you're using safari.

In firefox go to tools > add-ons and then select "get new add-ons"  Search for "User Agent Switcher" and install it.  Browser will restart.  Then do tools > default user agent > edit user agents...

create a new agent:
[http://techpatterns.com/forums/about304.html](http://techpatterns.com/forums/about304.html)

---

### Post by john olson on 2009-12-01
As a newie I didn't gave you all the information I need to. I purchased the iMac but delivery isn't until December 21. I wanted to start learning what I could before it arrives. That's why I tried to get into Apple's site with the one on one program. I think I would like to go back to firefox 3.5.5 and stay with that until I have the iMac up and running. 
Thank you for your help.

---

### Post by Merk42 on 2009-12-02
Oh, that makes much more sense!
Well try what I said on the previous page about packages, or even what jrrader said about user agent.

---

