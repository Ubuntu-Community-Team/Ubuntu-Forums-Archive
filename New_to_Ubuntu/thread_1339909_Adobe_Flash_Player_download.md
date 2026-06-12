---
title: "Adobe Flash Player download"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Spiffjiggins on 2009-11-28
How is it done? I'm used to clicking on a link and selecting download file and being done. Is this possible with this OS?

---

### Post by 3rdalbum on 2009-11-28
It's possible to create a 'binary installer' (what you mention) for Linux, but it's not an elegant solution. 

If you are on 32-bit, just install the 'adobe-flashplugin' package in Synaptic Package Manager. If you are on 64kbit, get the alpha version of the 64-bit player from Adobe and copy the included .so file into /usr/lib/mozilla/plugins.

---

### Post by mbzn on 2009-11-28
Try this...

[http://ubuntuforums.org/showthread.php?t=1338358&highlight=flash+player+install](http://ubuntuforums.org/showthread.php?t=1338358&highlight=flash+player+install)

---

### Post by Spiffjiggins on 2009-11-28
> **3rdalbum said:**
> It's possible to create a 'binary installer' (what you mention) for Linux, but it's not an elegant solution. 
 
If you are on 32-bit, just install the 'adobe-flashplugin' package in Synaptic Package Manager. If you are on 64kbit, get the alpha version of the 64-bit player from Adobe and copy the included .so file into /usr/lib/mozilla/plugins.
 
I have zero...ZERO programming knowledge. What you said was as foreign to me as a Russian teaching Alegrebra to a 7 year old Texan. What is a synaptic package manager? Where do I download it from? Equally, 32 bit? 64 bit? Binary insallter?!!

---

### Post by aysiu on 2009-11-28
It's possible, but it's not the recommended way.

More details here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by user1397 on 2009-11-28
It is actually just as easy, if not easier in ubuntu.  just go to youtube or some other site with flash content, and then when it asks you to install flash just accept it.

if that doesn't work, try what aysiu suggested.

---

### Post by Spiffjiggins on 2009-11-28
> **mbzn said:**
> Try this...
 
[http://ubuntuforums.org/showthread.php?t=1338358&highlight=flash+player+install](http://ubuntuforums.org/showthread.php?t=1338358&highlight=flash+player+install)
 
I'm sorry. That stuff is soooo far over my head it wasn't worth reading very far. I do NOT know any programming terminology other than press enter if that exists in that world.
Thanks though.

---

### Post by Spiffjiggins on 2009-11-28
> **aysiu said:**
> It's possible, but it's not the recommended way.
 
More details here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)
 
There is no "Ubuntu Software Center" Icon on my computer.

---

### Post by Spiffjiggins on 2009-11-28
> **ubuntuman001 said:**
> It is actually just as easy, if not easier in ubuntu. just go to youtube or some other site with flash content, and then when it asks you to install flash just accept it.
 
if that doesn't work, try what aysiu suggested.
 
this is what happens when I tried it the Windows way.
 
I click on the link and it offers 4-5 different selections for Linux. So I click to download them all. This window pops up for everyone saying they have been downloaded and after each download the window fills with each. Now I'm done downloading so I click on the link on how to install. I says I should've been prompted to designate where I wanted to send it to and suggests I apply them to the desktop. Houston we have a problem! It never game me that option. They (all four Deb., and some others I can no longer remember) all appeared in that download box. What do I do? Every time I click on them, they perform some action I can't recognize. 
 
Is there as way to just download the player and just be done with it without dancing through hoops?
 
Also as post script, how do I shut off my screen saver?

---

### Post by aysiu on 2009-11-28
> **Spiffjiggins said:**
> There is no "Ubuntu Software Center" Icon on my computer. Maybe you missed the first sentence on the page that said if you're using an older version of Ubuntu, you should refer to this page:
[http://www.psychocats.net/ubuntu/flashjaunty](http://www.psychocats.net/ubuntu/flashjaunty)

Read the link. Don't just glance quickly at it.

Reading **will** help you understand things better. If you have specific questions, ask, and people will gladly explain anything you want to know more about.

Flatly dismissing things you haven't taken the time to read won't help you learn.

---

### Post by Elfy on 2009-11-28
Screensaver is in Admin > Preferences

If you don't have Software Centre then look for Add/Remove.

This is the older flas install page from psychocats - [http://www.psychocats.net/ubuntu/flashjaunty](http://www.psychocats.net/ubuntu/flashjaunty) it should be as simple as following it. They certainly helped me a great deal whn I started here a couple of years ago.

You need to get away from thinking that using the terminal is programming - it is not - I have no idea how to program either - you don't need to to use Ubuntu.

If you are randomly downloading files and trying to install them you are likely to get tied up in knots fairly quickly - there is a lot of information out there that is older.

---

### Post by aysiu on 2009-11-28
Sorry for being curt with you before. I just realized you're using Xubuntu and not Ubuntu.

The principle is the same but the screenshots would look slightly different. If the word *Synaptic* sounds like gobbledygook, then you should read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Once again, the screenshots will be slightly different for Xubuntu but the idea is the same. It's like the iTunes App Store or Android Market. You don't go to a website to install software. You go through a software manager to get software installed and updated.

I believe in Xubuntu you click on the menu button (top-left) and select System > Synaptic Package Manager to get to it.

Once again, if you have **specific** questions, post back here. I know this can seem overwhelming at first, but if you can open your mind that there are simpler ways to do things than in Windows, the experience is very likely to be rewarding. We'll help if you ask for it.

---

### Post by Spiffjiggins on 2009-11-28
> **aysiu said:**
> Maybe you missed the first sentence on the page that said if you're using an older version of Ubuntu, you should refer to this page:
[http://www.psychocats.net/ubuntu/flashjaunty](http://www.psychocats.net/ubuntu/flashjaunty)
 
Read the link. Don't just glance quickly at it.
 
Reading **will** help you understand things better. If you have specific questions, ask, and people will gladly explain anything you want to know more about.
 
Flatly dismissing things you haven't taken the time to read won't help you learn.
 
This is the first sentence of the link you provided.
 
"In Ubuntu 8.04, there was integration between Firefox and the system's software manager so that you'd get a nifty pop-up asking you to install the missing plugins when you visited a page requiring the Adobe Flash plugin."
 
(1) I have a newer version. I down loaded it less than 12 hours ago. It said 9 point something.
(2) no pop up. Just a very strange looking rendition of a page on a web site that I frequent telling me I need adobe flash player. This "integration between Firefox and the system's software manager" is seriously a foreign language to me.
 
You don't need to be so condoscending. I'm extremely ignorant in tech terminology. Don't play video games. Not a programmer. Other than watching Justin TV, sending emails, Fark, Reddit and Youtube I do not use the computer. 
 
I guess today would be an exception.

---

### Post by aysiu on 2009-11-28
I also don't play video games. I also am not a programmer.

Here you go. In Xubuntu, it's Applications > System > Synaptic Package Manager.

For more on Synaptic, read [http://www.psychocats.net/ubuntu/installingsoftware#synaptic](http://www.psychocats.net/ubuntu/installingsoftware#synaptic)

And stop insisting others are programmers. Many of us are not. I definitely am not.

---

### Post by Spiffjiggins on 2009-11-28
> **aysiu said:**
> Sorry for being curt with you before. I just realized you're using Xubuntu and not Ubuntu.
 
The principle is the same but the screenshots would look slightly different. If the word *Synaptic* sounds like gobbledygook, then you should read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
 
Once again, the screenshots will be slightly different for Xubuntu but the idea is the same. It's like the iTunes App Store or Android Market. You don't go to a website to install software. You go through a software manager to get software installed and updated.
 
I believe in Xubuntu you click on the menu button (top-left) and select System > Synaptic Package Manager to get to it.
 
Once again, if you have **specific** questions, post back here. I know this can seem overwhelming at first, but if you can open your mind that there are simpler ways to do things than in Windows, the experience is very likely to be rewarding. We'll help if you ask for it.
 
Thank you. THIs was more helpfull, however I that "Synaptic Package Manager " there is no Adobe. What do I do now?

---

### Post by Elfy on 2009-11-28
Sorry - I missed xubuntu too :(

In synaptic look for flash not adobe.

---

### Post by Spiffjiggins on 2009-11-28
> **forestpiskie said:**
> Sorry - I missed xubuntu too :(
 
In synaptic look for flash not adobe.
 
Thank you. I downloaded Flashplayer 10 pl_linux and install flash_player_10_linux.tar.gz Do I have to reboot my computer for them to work because when I downloaded them I was still unable to view Youtube and JustingTV.com?

---

### Post by Spiffjiggins on 2009-11-28
> **forestpiskie said:**
> Screensaver is in Admin > Preferences
 
If you don't have Software Centre then look for Add/Remove.
 
This is the older flas install page from psychocats - [http://www.psychocats.net/ubuntu/flashjaunty](http://www.psychocats.net/ubuntu/flashjaunty) it should be as simple as following it. They certainly helped me a great deal whn I started here a couple of years ago.
 
You need to get away from thinking that using the terminal is programming - it is not - I have no idea how to program either - you don't need to to use Ubuntu.
 
If you are randomly downloading files and trying to install them you are likely to get tied up in knots fairly quickly - there is a lot of information out there that is older.
 
Just saw this. Thanks. It was set at 5 min

---

### Post by 3rdalbum on 2009-11-28
Install the "flashplugin-installer" package:

Go to the Applications menu, then down to System, then Synaptic Package Manager.

Go to the Edit menu and Search, and type "flashplugin". Press Search.

The first result should be flashplugin-installer. Right-click it and choose "Mark for Installation". It will probably say that it will install some other packages; just click Ok.

Now click the big Apply button near the top of the window. It will ask you to confirm your selection. Click OK. The Flash Player plugin will be downloaded and installed for you. Close Firefox and open it again, and you'll be able to use Flash websites.

Synaptic Package Manager contains lots and lots of software that you can search through and install with a couple of simple mouse clicks. Always check it first before trawling the web for software. It will be easier.

You don't need to be a programmer to use Ubuntu, just be willing to learn and explore. And use Google. But really this is the same with any operating system and any software that you're not already familiar with.

---

### Post by kmacphail on 2009-11-28
Since you have already downloaded the *flash_player_10_linux.tar.gz* it may be better doing this manually.

A tar file (which you have downloaded) is similar to a zip file in windows.  It is a file that has more files inside it.  People do this to make a large smile a bit smaller or to email, for example, pictures (it will be one attachment instead of ten)

**Double click** on the **flash_player_10_linux.tar.gz** and this should open up a window.   

You should see that the tar contains a file called **libflashplayer.so**.

At the top the window there should be a button called **Extract** click on this. 

A new window will pop up, asking where you want to place the file. Click on the folder with **your username** on the left of this window (this is called the home folder)

At this point you will see a few folders (Documents, Pictures, Videos, Music) in the middle of the window.

**Right click** here and make sure that **Show hidden files** is ticked.

**Double click** on the folder **.mozilla**

**Double click** on the folder **plugins**

**click** on **Extract**

Restart Firefox and your flash should work.

---

