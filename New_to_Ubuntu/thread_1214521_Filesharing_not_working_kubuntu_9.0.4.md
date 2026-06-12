---
title: "Filesharing not working kubuntu 9.0.4"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by LinuxNooblet on 2009-07-16
So I'm not actually a Linux nooblet, I just feel like one right now and am sure there is some easy answer I am missing. I am trying to set this laptop up for my daughter and chose ubuntu because I kept hearing how easy it was and how nontechies could use it.

So I am trying to setup network sharing so that she can just right-click in dolphin choose properties and share the folder. So at first I didn't realize Samba was not installed so I was trying to share with Dolphin and nothing would happen. It just said "You need to be authorized to share folders" and when I clicked the "Configure File Sharing" button I got asked to sudo and then nothing happened. So I start poking around and realize Samba isn't even installed. This seemed wierd for a Live CD distro, but I can roll with it. I install Samba 4 and pickup the kdenetwork-filesharing module along the way.

I go to the Computer->System Settings->Advanced and there is now a "Samba" icon, which is good because the last time I touched a Samba Config file we hadn't even invaded Iraq. I go to launch the configuration and nothing happens. The Icon highlights on the first click but will not launch the application.

So, does anyone have any clue as to what I am doing wrong. I've verified that samba is in fact running and I could configure it manually, it would be a huge fricking pain but I could do it. But I really need to get it setup so my daughter can share files through Dolphin and I just can't figure out what is wrong.

---

### Post by AndThenWhat on 2009-07-16
Lol @ your name. Anyways, I think you need to add her user to the  'sambashare' group.  Also, I don't know about Kubuntu but Ubuntu comes with samba installed. And you're probably going to hate me for saying this but drawing from my experiences of introducing Windows users to Linux, they usually transition much smoother in a Ubuntu environment as opposed to Kubuntu.

Hope that helps.

---

### Post by LinuxNooblet on 2009-07-16
I chose Kubuntu because I "grew up" with Desktop Linux with Suse back when I was in college. I pretty much quit using Linux on the desktop for years due to useability issues. Sure I could always go to the command line and get things done, but it was a pain in the *** to have to always figure out how when I needed desktop feature X, such as DVD playback. To tell the truth this really feels the same way. 

There is a section in the System Settings called "Sharing" which was the first place I looked, but it has one tab that ask for a Defualt user and default password. Nothing about allowing users to share. The samba tool does nothing when I click on it. Do you have anyidea how frustrating it is to click on a program icon and have nothing happen? Try looking for a binary file, nope, it's a plugin so you can't run it standalone. I mean this should be simple ****. I'm using the Kubuntu default file browser (Konquerer also) and am trying to set up filesharing using the kdenetwork-filesharing tool, and it's not working. I try seeing if other people are having this problem, nope can't find anything online. I try looking for a guide, can't find any for 9.0.4 kubuntu. Its frustrating crap. 

Sure I could just apt-get install gnome-desktop but then I have all kinds of crap I don't need in both program menus, so I need to wipe kubuntu and install ubuntu. Thankfully I kept /home on a seperate partition. I don't want to even think about retransfering all her files. I wish that it "would just work" at least for the simple **** like filesharing. I can understand if I trying to get oracle installed and configured, but filesharing?

---

### Post by AndThenWhat on 2009-07-16
Yeah doing that separate home partition is a lifesaver. I know it will be a pain in the ***, but you would be much happier with the general usability on Ubuntu if you switched. I mean look at what comes default:

[http://img188.imageshack.us/img188/4451/screenshotzze.png](http://img188.imageshack.us/img188/4451/screenshotzze.png)

I'm telling you Samba will work out of the box.

Cheers.

---

