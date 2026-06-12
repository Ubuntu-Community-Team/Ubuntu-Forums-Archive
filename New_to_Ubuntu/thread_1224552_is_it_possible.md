---
title: "is it possible???"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by snitchard on 2009-07-27
Hello,

I started using Ubuntu about 4 days ago, broke it and then fixed it by chance.  I'd love to switch to Ubuntu because the idea of not having to worry about paying hundreds or thousands of dollars for software is a nice one.  I'm a computer technician that works with and fixes Windows computers so moving over to Ubntu is a litle scary because not everything is done in a GUI.

Currently I have a few issues to work through.  I'm conflicted as to whether I want to use Evolution or Thunderbird as my e-mail client. Thunderbird is closer to M.S. Outlook Express but there are some annoyances I'll have to work around and live with.

I have been doing some research and the only thing that is going to be a pain is my video editing and Light scribe label making.  I'm not a professional video editor I just edit family home movies into DVDs but I need a piece of software similar to Roxio's Easy Media Creator that will allow me to:

Transfer the movie using fire wire from a mini DV camcorder
Cut and paste sections of the movie
create transitions
Create a title screen
create credits
Add voice and/or music to the background
Create picture slide shows
Create a DVD menu
output in ISO format to burn onto a DVD

I looked into Lacie 4L but following the directions from a website I found doesn't work. Everything in the software is grayed out and the software is not usable. I wish Linux could just be point and click but I guess that is why it is free. Even though I'm very experienced in Windows and fixing computers Linux is a whole new scary world. Will I ever feel comfortable and confident???

Any suggestions or opinions are greatly appreciated.

Thanks

---

### Post by nhasian on 2009-07-27
hello snitchard,

if you have enough hard disk space, perhaps you can dual boot between windows and ubuntu until you are more comfortable with linux.  At first I was reluctant to use the terminal as well, but I've found that some things are easier to do in a terminal, while some things are easier to do in a GUI.

I've been using ubuntu Since April 2008 and I've never even opened Evolution.  I use Thunderbird because its cross platform, and it is the same emails and interface weather i'm on my ubuntu computer or my windows computer.

for the video editing software, try [Open Movie Editor]("http://www.openmovieeditor.org/").

---

### Post by vinutux on 2009-07-27
Try kino movie editor ```
sudo apt-get install kino
```

or 

Pitivi video editor fro here**[ www.getdeb.net/app/PiTiVi ]("www.getdeb.net/app/PiTiVi")**

---

### Post by Ratscallion on 2009-07-27
> **vinutux said:**
> 
Pitivi video editor fro here**[ www.getdeb.net/app/PiTiVi ]("http://www.getdeb.net/app/PiTiVi")**

Pitivi is quite good yes.. Or, if you don't mind buggyness (or don't mind using it in KDE ```
 sudo apt-get install kubuntu-desktop
```) you could try kdenlive ```
sudo apt-get install kdenlive
```

---

### Post by juancarlospaco on 2009-07-27
Im sucessfully Light scribing on Ubuntu, there's a Software avaliable to do that, 
its maintained by LACIE, but is simple, not for complex graphics.

---

### Post by bailbath on 2009-07-27
I think there are plenty of Dvd authoring apps try as many as you like until you find one that suits you. Even if it does not quite fit what you want become a part of that community and tell them what you would like and they/you may enhance the product. Dual booting is only really needed if there really is no viable alternative or you could try a virtual machine if you feel there is no app for you.

---

### Post by j.bell730 on 2009-07-27
Also on the topic of video editing, I really like [Kaltura]("http://corp.kaltura.com/").

---

### Post by vinutux on 2009-07-27
> **Ratscallion said:**
> Pitivi is quite good yes.. Or, if you don't mind buggyness (or don't mind using it in KDE ```
 [COLOR="Red"]sudo apt-get install kubuntu-desktop[/COLOR]
```) you could try kdenlive ```
sudo apt-get install kdenlive
```

Th whole KDE aka kubuntu-desktop is not needed for kdenlive

---

### Post by AClark on 2009-07-27
I started out with Ubuntu on a non critical home computer and over a couple of years have now converted all of my business and home computers to Ubuntu.  

I use Virtualbox for the very few business applications that I can't duplicate in Linux.

I have found that many of the simple Windows programs I thought I would have to live without run perfectly in WINE.

I have two native Linux LightScribe applications running on my boxes without problems.

VirtualBox in seamless mode is awesome - it's as if you have left Windows completely.

In short I haven't booted up to Windows in months and to answer your question - YES it is possible.

---

### Post by MelDJ on 2009-07-28
Why not try Ubuntu Studio?

---

### Post by earthpigg on 2009-07-28
*_**no!**_*

> **Ratscallion said:**
> Pitivi is quite good yes.. Or, if you don't mind buggyness (or don't mind using it in KDE ```
_*** sudo apt-get install kubuntu-desktop***_
```) you could try kdenlive ```
sudo apt-get install kdenlive
```

there is no need to install kubuntu-desktop to run KDE/kubuntu applications in ubuntu.

you will need parts of KDE, which will automatically be installed (as "*dependencies*") with *no need* for you to do *anything* special.

---

### Post by Ratscallion on 2009-07-28
I know.. I was talking about Kdenlive being buggy in GNOME, so, if you don't want it to be buggy, go ahead and run it in KDE. I am well aware that you can install KDE apps in GNOME.

---

### Post by rannable on 2009-07-28
If you have a MS Exchange mail server Evolution is the way to go, if you need a hand setting up your client to talk to Exchange give me a shout as i can talk you through it...
Rob

---

### Post by 3rdalbum on 2009-07-28
> **snitchard said:**
> I looked into Lacie 4L but following the directions from a website I found doesn't work. Everything in the software is grayed out and the software is not usable.

Please post these instructions, and what exactly is greyed out?

Lightscribe burning in Linux does work from what I've been told, but it's not in an advanced stage of development. This is due to two factors:

1. The companies behind Lightscribe haven't put much effort into Lightscribe on Linux
2. Lightscribe discs seem to be difficult to find, at least in my part of the world, so a lot of community people who want to contribute can't, because they can't find the discs.

Nothing to do with being a free operating system. Linux is free because it's open-source, and it's open-source because it works better that way.

Some things in Windows aren't point-and-click either, but I digress.

General knowledge: Some Linux programs are distributed only as source code, that must be compiled first. Compiling is usually quite easy. On Windows, you always get precompiled programs - this is because Windows only really runs on one processor architecture (x86) so a precompiled binary is alright.

Linux, on the other hand, runs on a tremendous number of processor architectures, and as such a precompiled binary won't run on more than one architecture. Rather than distribute one binary for people with x86, another for people with 64-bit x86, another for people with PowerPC, another for embedded ARM users etc, they distribute source code that can be compiled to run on anything.

When Windows started making the transition to 64-bit x86, there were a massive number of problems because all these precompiled programs were compiled for 32-bit x86 only! As a result a lot of them didn't work properly on the 64-bit processor. Linux users, however, didn't have any such pain because most of their programs were just recompiled for 64-bit.

Also, Microsoft ported Windows to the ia64 (Itanium) architecture. Itanium is incompatible with x86, and so although Windows could run, there were no working programs because they were all compiled for the incompatible x86 architecture. Most Itanium-based computers run Linux now, because Linux programs can just be compiled for Itanium and they will work.

---

