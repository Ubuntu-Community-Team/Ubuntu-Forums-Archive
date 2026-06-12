---
title: "Plugin help (flashplugin-nonfree)...there's got to be a way"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by jburrell on 2009-01-14
Good morning all from snowy Germany!  

I have just installed 8.10 on my computer and its running great except for the fact that I need to install some plugins.  I've never had a problem with this on my netbook which is running 8.04, it gives me the messages, I tell it to find the appropriate packages, and it installs them.

Not so with 8.10 on this computer for some reason.  

Here's the notification I receive (forgive me if its not word for word):
"Additional plugins are required to display all the media on this page"  I then click on "install missing plugins" and the plugin finder service tells me "the following are available plugin downloads" and "choose a type of plugin for the type of media application/x-shockwave-flash:"
"Adobe Flash Player (Installer)"
"Swfdec Player for Adobe/Macromedia Flash"
"Gnash SWF Player"

I then click on "next" to install the packages and I get the following error message: "could not find package flashplugin-nonfree"

The plugin finder service then tells me it "finished installing the missing plugins: Adobe flash player (installer) installed"

I've been all over the web searching and found the "flashplugin-nonfree" and I tried to download and install it and I get another error message that says something about an error regarding something about "dependency" with some sort of code "libswfdec0.5-1." 

I've tried to solve this on my own before taking people's time here.  Can anyone help me with this one?

Thank you

---

### Post by nhasian on 2009-01-14
close firefox.  open up a terminal via Applications->Accessories->terminal and type:

```
sudo apt-get install flashplugin-nonfree
```

all done.  flash should be working now in firefox.

---

### Post by zvacet on 2009-01-14
```
gksudo gedit /etc/apt/sources.list
```

and add this line 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

save and close file.

```
sudo apt-get update
```

Go to the synaptic and in search box type **adobe-flashplugin** and when you find it just install.

---

### Post by stevoo on 2009-01-14
i am highly against that plugin 

i would reccomend method 2 here 
[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

that way you get the best from adobe

---

### Post by Paqman on 2009-01-14
> **stevoo said:**
> i am highly against that plugin 


Any particular reason? If you're going to make recommendations that aren't the defaults you should explain whether it's due to technical or philosophical reasons.

---

### Post by stevoo on 2009-01-14
No special reason. 
Mostly cause it downloads version 9 of adobe which a lot of times it doesnt act as it should. 

I had the same errors with that version until i switched into version 10 which was still in beta and has solved all of those problems. 

So until flash-plugin-non-free doesnt catch up, i reccomend switching to v10

---

### Post by jburrell on 2009-01-14
I followed the steps in 2 and 3 through the commands in the terminal and it worked like a charm.  Thank you to everyone who made comments, I really appreciate it,
Thanks once again!

---

### Post by gandaran on 2009-01-14
> **stevoo said:**
> No special reason. 
Mostly cause it downloads version 9 of adobe which a lot of times it doesnt act as it should. 

I had the same errors with that version until i switched into version 10 which was still in beta and has solved all of those problems. 

So until flash-plugin-non-free doesnt catch up, i reccomend switching to v10
this only happens with ubuntu hardy 8.04 (flash 9), on ubuntu 8.10 the flashplugin-nonfree installs the latest adobe flash 10 release directly from adobe.com site but you have to update apt-get or synaptic first or it wont install due to the new flash release
if you don't like the flashplugin-nonfree package you can install the adobe-flashplugin, just enable archive.canonical.com repository to get it or get it from the adobe site, it's just the same flash as the the flashplugin-nonfree.

---

### Post by jburrell on 2009-01-14
I want to mark this thread as "solved."  How do I do that?

---

### Post by zvacet on 2009-01-14
Look [here.]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by jburrell on 2009-01-14
That's what threw me off.  I go to the "Thread Tools" and it only gives me 4 options, the last of which being to add a poll, there is no selection for marking as solved.  

I don't have this problem with my netbook, could it be the display settings on this Compaq Presario 700?

---

