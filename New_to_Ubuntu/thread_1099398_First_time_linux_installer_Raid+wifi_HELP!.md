---
title: "First time linux installer Raid+wifi HELP!"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Haitoyou on 2009-03-18
Hi this is my first time installing anything linux. I have tried to install Ubuntu but since I do not have a second computer to access the internet, I would need to at least be able to resolve my wifi problem before I actually go through with it. So far during dry runs, I have been unable to detect my wifi card nor get it to work. These are my problems:

1. My wifi receiver is a Hawking USB 300N dish. I may be missing the menu where it lists it as a device but I don't know much about the desktop environment. I am connected to a router that requires a WEP key, but I do have that information.

2. So far, I have been unable to get Ubuntu to recognize my two sata drives as a raid 0 setup. I have an on-board VIA sata raid controller and I currently have it set to establish the two drives in a raid 0 array. However, when I get to the Ubuntu partition part of the installation, it gives me an option to install either on one drive or the other but not as a raid 0 setup. Am I missing a program that helps recognize raid 0 setups, or is there something that establishes the two drives as such?

I wasn't sure about posting this in the beginner talk since I am very knowledgeable about computers, but then again, I've been accustomed to the spoiled windows XP lifestyle, and I am tired of my computer running slowly. OH HELP ME WISE ONES, I HAVE SEEN THE LIGHT!!!

---

### Post by iamkrazee on 2009-03-18
Take it easy, you're talking ubuntu so you mostly likely have "GNOME" Desktop Environment. Go to System Admin > Hardware Drivers from the menu. You should be able to see your wireless network card listed over there. You just have to activate the driver, get started with your internet while sata/raid help comes.

---

### Post by Haitoyou on 2009-03-18
Ok I tried that and the only thing that showed up was a proprietary driver for my ATI radeon card. I know I'm in for some trouble since it seems that linux is still iffy with USB wifi cards, but I'll still try to get it working.

I need help trying to use ndiswrapper, since the only thing I know about it is that it can be used to convert windows drivers into linux equivalents. I have downloaded it already. I am fairly knowledgeable about the terminal shell in linux. I would just need the commands to run, or how to set it up.

If anyone has knowledge on how to set up a raid 0 installation please let me know, I really don't want to run my two hard drives separately.

---

