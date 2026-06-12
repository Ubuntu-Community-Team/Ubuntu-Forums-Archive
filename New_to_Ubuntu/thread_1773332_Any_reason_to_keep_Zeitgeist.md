---
title: "Any reason to keep Zeitgeist?"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by hreichgott on 2011-06-01
Hi, I don't know much about Zeitgeist, but from what I can find by searching online, it looks like one of those programs like Google Desktop Search that constantly runs, indexing your files and keeping track of your history.

I generally try to stay away from programs like this. I like to use "find" to find files and a Terminal to run programs and do most of my work. Once in a while I need to go into Firefox's history to find something, but firefox already handles that. After a couple weeks of honestly trying Unity, I disliked the crashes/unresponsive windows and went back to Ubuntu Classic, so I don't need Unity's "recent files" thing. Ubuntu One's web interface and Google Docs are the closest I ever come to cloud computing; I definitely don't like anything that takes resources to constantly update itself, other than the little weather applet.

I want the computer to do the things I am asking it to do, and as little extra as possible. After every Ubuntu upgrade I habitually delete everything I don't use (evolution, ubuntu one, bluetooth, and couchdb among others.) Should I add Zeitgeist to my delete list?

thanks, hreichgott

---

### Post by Mariane on 2011-06-02
Is this the thing that from time to time tells me it is "suspending desktop indexing to save resources"? I was puzzled by this one, as far as I could remember I had not told anything to index anything. 

If that's the one I'll delete it also, please tell me how when you do it. I'm not so worried about resources but I like a clear desktop, I hate having little uncalled messages popping up now and then, drawing my attention - I seem unable to stop myself from reading them - and distracting me from what I'm doing. 

Mariane

---

### Post by Paqman on 2011-06-02
> **hreichgott said:**
> 
I want the computer to do the things I am asking it to do, and as little extra as possible. After every Ubuntu upgrade I habitually delete everything I don't use (evolution, ubuntu one, bluetooth, and couchdb among others.) Should I add Zeitgeist to my delete list?


From the sounds of it, you wouldn't miss it much. 

You may want to consider coming at your system from the other direction. Start with a very minimal command line install and only add what you do want. There are very stripped-down versions of Gnome 2, XFCE, LXDE and even Unity available in the Ubuntu repos. The script in my sig will also help you build a system this way without a lot of prior knowledge of the packages required.

You could use the list of packages the script installed to write your own script to completely automate the install process. Wouldn't be complicated or hard at all, just one big apt-get line with heaps of packages in it.

---

### Post by Legendary_Bibo on 2011-06-02
```
sudo apt-get --purge remove zeitgeist
```

---

### Post by hreichgott on 2011-06-02
Thanks for the suggestions. I am going to delete zeitgeist and will post here again if deleting causes any problems.

Mariane, that would make sense, but I've never seen that message myself. It could be some other indexing program.

Paqman, that is an interesting idea about a minimal install. I will need to do some learning about which packages I do need. Is there anything non-obvious required to run a minimal installation that can still handle 3D OpenGL graphics (on a Radeon 6310 card using ATI's Catalyst driver), heavy-duty audio processing, and video editing, not at the same time? I use my laptop for these things (part of why I like to have control over what resources are being used for).

---

### Post by iansane on 2011-06-02
please do post if you've already removed it and let us know. I looked it up in synaptic and found that it keeps a journal for use with unity on 11.04 but I have my system set to use classic ubuntu. Still when I click on remove completely it says also to be removed Ubuntu-Desktop.

I remember doing this before with other packages that said they would remove ubuntu desktop and sometimes they don't really remove it but once it did remove it and I had nothing but a terminal login and had to reinstall ubuntu-desktop. Can't remember what it was because it was over a year ago.

Also there are many other packages for zeitgeist than just the zeitgeist package.

---

### Post by Mariane on 2011-06-03
I have had a problem like this with another package. The problem is automated tools will not let you break dependencies. So if ubuntu-desktop is listed as being dependent upon zeitgeist you cannot use them to remove zeitgeist without removing ubuntu-desktop. 

The solution is to use the manual tool dpkg. Now be careful with it, right? It could really mess things up. But my guess would be (not necessarily in this order): 

```

sudo dpkg -r zeitgeist-datahub
sudo dpkg -r zeitgeist
sudo dpkg -r zeitgeist-core

```

Mariane

---

### Post by Elfy on 2011-06-03
> without removing ubuntu-desktop. Shouldn't cause a problem, though if you wish to later upgrade it's probably best to reinstall it. It's a meta package so as soon as something that is part of ubuntu-desktop is removed then so is ubuntu-desktop.

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)
[https://help.ubuntu.com/community/CommonQuestions#Meta-packages:%20ubuntu-desktop](https://help.ubuntu.com/community/CommonQuestions#Meta-packages:%20ubuntu-desktop)

---

### Post by wildmanne39 on 2011-06-03
> **Mariane said:**
> Is this the thing that from time to time tells me it is "suspending desktop indexing to save resources"? I was puzzled by this one, as far as I could remember I had not told anything to index anything. 

If that's the one I'll delete it also, please tell me how when you do it. I'm not so worried about resources but I like a clear desktop, I hate having little uncalled messages popping up now and then, drawing my attention - I seem unable to stop myself from reading them - and distracting me from what I'm doing. 

Mariane
Hi, the indexing it is probably referring to is the one that indexes files so you can search them quicker, but that is just a guess.

---

### Post by hreichgott on 2011-06-03
Zeitgeist removed. Had to do both 

```
sudo apt-get --purge remove zeitgeist
```

and

```
sudo apt-get autoremove
```

and reboot, to get all the Zeitgeist processes to go away and stop running. Everything is fine. Desktop (ubuntu classic) is the same. Things even seem faster but it could be just my imagination.

---

### Post by Paqman on 2011-06-04
> **hreichgott said:**
> 
Paqman, that is an interesting idea about a minimal install. I will need to do some learning about which packages I do need. Is there anything non-obvious required to run a minimal installation that can still handle 3D OpenGL graphics (on a Radeon 6310 card using ATI's Catalyst driver), heavy-duty audio processing, and video editing, not at the same time? I use my laptop for these things (part of why I like to have control over what resources are being used for).

Generally the way to go is that you install the package you want, and let the dependencies cascade down and install everything it needs to run. There are some bits and pieces that can make things easier though. To get the proprietary video drivers easily you'd want to install the Additional Drivers tool, which goes by the unlikely name of jockey-gtk.  You'd also want dkms so that it doesn't break when you update your kernel. Perhaps the simplest thing to do would be install the basics plus some package management, such as:
```

sudo apt-get install xorg gdm gnome-core network-manager-gnome gnome-themes indicator-session jockey-gtk dkms software-properties-gtk update-manager

```

That will give you a basic system that you can easily add your productivity applications to. That would install the generic kernel and Pulseaudio obviously, but that's easily fixed if you want.

---

### Post by slauper on 2011-08-22
> **hreichgott said:**
> Zeitgeist removed. Had to do both 

```
sudo apt-get --purge remove zeitgeist
```and

```
sudo apt-get autoremove
```and reboot, to get all the Zeitgeist processes to go away and stop running. Everything is fine. Desktop (ubuntu classic) is the same. Things even seem faster but it could be just my imagination.
Hi 
Thanx a lot !
it took me a lot of system ressources and finally never asked for it.
thanx helping me get it out my box :)

---

### Post by Duncan Williams on 2011-09-07
hi, after I read this I followed your advice:

sudo apt-get --purge remove zeitgeist

sudo apt-get autoremove

Which got rid of my `**zeitgeist Datah**' that was showing in my system manager as a **zombie process**.
which occured after installing **awn**.
thank you.

---

### Post by stallinux on 2011-10-12
> **hreichgott said:**
> Zeitgeist removed. Had to do both 

```
sudo apt-get --purge remove zeitgeist
```and

```
sudo apt-get autoremove
```and reboot, to get all the Zeitgeist processes to go away and stop running. Everything is fine. Desktop (ubuntu classic) is the same. Things even seem faster but it could be just my imagination.

Excellent. It worked. Thanks.

Just like you guys here, I don't like such programs. I am worried. Note the creepy 'mission statement' of Zeitgeist: "Our current goal is to index as much information from as many different sources as fast as we can." I have a very bad feeling about this. Well, as they say "The fact that you are paranoid doesn't mean that they *aren't* after you", but this has a lot of Big-Brother-is-watching-you structure.

Apart from that, those so-called 'indexing' services are resources-consuming and malfunctioning. (In W**os, the thing cannot find my files, even when standing smack on top of them!). Useless applications made by programmers that think in the way of Hey-guys-look-what-I-can-do-with-my-computer instead of making things for endusers. Zeitgeist does not fit in the philosophy of Ubuntu (?)(which is turning hardware into productivity centrals, where W**os is turning expensive hardware into colourful and cute icon displays).

Let me thank here all the people contributing to the good cause.

Conclusion: 
Any reason to keep Zeitgeist? No
How to remove it? See post of hreichgott quoted above. It works!

---

### Post by t.h.w. on 2011-11-01
Thanks a lot.
I went from Windows to Ubuntu just to get rid of this kind of nonsense.

I am scared now that this will be no incident. I am going to keep a lookout for other distributions....

@developers: PLEASE keep it simple and visible and stop with any tracking without asking your user every single time. Thank you!

---

### Post by Gnusboy on 2013-01-20
Hi
I was going to run updates and saw the Zeitgeist add-on. This is the description I get for it:

"Zeitgeist is a service which logs the user's activities and events (files opened, websites visited, conversations held with other people, etc.) and makes the relevant information available to other applications.
It serves as a comprehensive activity log and also makes it possible to determine relationships between items based on usage patterns.
This package contains the assets for either activity-log-manager or activity-log-manager-control-center."

Now I may be a little paranoid, but why would I want a program that saves everything I do?
I'm not into anything classified, but I just don't like the idea of this.
Can I just not install it with updates, or will it break something?
Thanks

---

### Post by Paqman on 2013-01-20
> **Gnusboy said:**
> 
Now I may be a little paranoid, but why would I want a program that saves everything I do?

Applications can use the data Zeitgeist provides to present useful options to you. For example, Zeitgeist could tell a word processor what the most recently opened text files were.

> 
Can I just not install it with updates, or will it break something?


You can remove it completely if you want, but you'll lose a lot of the Dash's functionality. You can adjust its settings in the Privacy section of the System Settings.

---

### Post by Gnusboy on 2013-01-20
> **Paqman said:**
> Applications can use the data Zeitgeist provides to present useful options to you. For example, Zeitgeist could tell a word processor what the most recently opened text files were.



You can remove it completely if you want, but you'll lose a lot of the Dash's functionality. You can adjust its settings in the Privacy section of the System Settings.

Ok. I guess I can live with that. I appreciate your help.

---

