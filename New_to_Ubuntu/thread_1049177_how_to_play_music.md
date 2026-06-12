---
title: "how to play music"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by tushar88 on 2009-01-24
hello i am new to ubuntu ,

i use ubuntu 7.10

so how to play a media file in ubuntu including mp3 , .mov 

i tried to play .mov with default player but it gave error message below :

the playback of the movie requires the following decoders to be installed 
   MPEG -4 AAC decoder
   H.264 decoder

so i want a detail explanation about what r repositories & codecs required to play media file & is it possible to have a VLC player in ubuntu . 
 
   please reply me in brief

---

### Post by yeats on 2009-01-24
First of all, for multimedia playback, go here:

[http://www.medibuntu.org/]("http://www.medibuntu.org/")

which includes a Repository How To link.

To get VLC just open the synaptic package manager

System -> Administration -> Package Manager (or Synaptic) - I use Kubuntu now so I forget the labels :-)

and search for VLC.

---

### Post by Stalker72 on 2009-01-24
You should also install **ubuntu-restricted-extras**.

**In Terminal,  type:**

```
sudo apt-get install ubuntu-restricted-extras
```

Stalker72

---

### Post by Stalker72 on 2009-01-24
> **tushar88 said:**
> 
i use ubuntu 7.10

Why? There are 2 newer versions.

Welcome to Ubuntu! :D

Stalker72

---

### Post by tushar88 on 2009-01-24
> **Stalker72 said:**
> You should also install **ubuntu-restricted-extras**.

**In Terminal,  type:**

```
sudo apt-get install ubuntu-restricted-extras
```

Stalker72

what will this command do and after that will my media play .

---

### Post by Stalker72 on 2009-01-24
> **tushar88 said:**
> what will this command do and after that will my media play .
[http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)

Stalker72

---

### Post by linux_tech on 2009-01-24
Rythymbox can play the mp3's. Open synaptic and install all gstreamer & plugin pkgs.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_VLC_Media_Player](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_VLC_Media_Player)

FYI, there is a Multimedia & Video section in the forums that will help your post get more responses for Multimedia & Video questions

---

### Post by leonardo_neo on 2009-01-24
> sudo apt-get install ubuntu-restricted-extras

This will install most of the codecs to play different file formats like MP3. 

> sudo apt-get install vlc

This should install the vlc media player.

Best of luck.:D

---

### Post by carml on 2009-01-24
You can use whatever software you like to play music,but you have to install the gstreamer codecs,to do so you can look for them under Applications->Add/remove.:p

---

### Post by Stalker72 on 2009-01-24
**sudo** means superuser do. When you put it in front of a command, you let it run with administrator privileges.

**apt-get** : Turn the words around and you will get **get apt**. Think of it like **get application**.

**install** : It means that you want to install what you type next.

**ubuntu-restricted-extras** : It means that you want to install that package. As long as you know the name of the application you want to install, you can type it in this command. Replace **ubuntu-restricted-extras** with, for example, **firefox**, and you will install the web browser Firefox.

Press **enter** and then **y** when it asks for your permission.

To remove an application, type the same command only that you replace **install** with **remove**.

Good luck!

Stalker72

---

### Post by leonardo_neo on 2009-01-24
> **Stalker72 said:**
> **sudo** means superuser do. When you put it in front of a command, you let it run with administrator privileges.

**apt-get** : Turn the words around and you will get **get apt**. Think of it like **get application**.

**install** : It means that you want to install what you type next.

**ubuntu-restricted-extras** : It means that you want to install that package. As long as you know the name of the application you want to install, you can type it in this command. Replace **ubuntu-restricted-extras** with, for example, **firefox**, and you will install the web browser Firefox.

Press **enter** and then **y** when it asks for your permission.

To remove an application, type the same command only that you replace **install** with **remove**.

Good luck!

Stalker72

No one could explain the basics, better than you did! 

Good Job (Thumbs up);)

---

### Post by tushar88 on 2009-01-25
> **leonardo_neo said:**
> No one could explain the basics, better than you did! 

Good Job (Thumbs up);)

thanks bro.

but what if it ask for internet connection . i cannot connect to internet

---

### Post by -kg- on 2009-01-25
> **tushar88 said:**
> thanks bro.

but what if it ask for internet connection . i cannot connect to internet

Uh, it will.  You have to be connected to the internet to get the applications for Ubuntu.  Why can't you connect to the internet?

---

### Post by leonardo_neo on 2009-01-25
> **tushar88 said:**
> thanks bro.

but what if it ask for internet connection . i cannot connect to internet

Yes, to get softwares and updates, you must need internet. I wonder why you can't connect to internet? Creating a connection in Ubuntu is really very easy. For that I must know what kinda connection you have ADSL connection? Do you use router? 

Well, for basics, I recommend if you can access internet from your service provider in windows, then first check the TCP/IP setting configuration. If it is set in automatic, then you can get the TCP/IP setting from your internet service provider. You need to know

1. Gateway IP address
2. Subnet mask
3. Primary DNS
4. Secondary DNS

Fill this information to create a network, and you are done. But first try to connect to internet by using 'Auto' settings. That only should do the job.:D

---

