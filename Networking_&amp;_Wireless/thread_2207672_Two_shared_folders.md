---
title: "Two shared folders"
date: 2014-02-24
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2014-02-24
12.04 LTS.

I am having a difficult time setting up sharing for a folder. The folder is meant to be accessed from our company's Windows network. 

I have created two folders and using Nautilus, right-clicked on them to set Sharing Options. 

_Folder1_ is shared, others are allowed to create and delete files in this folder, Guest access is not turned on.
_Folder2_ is also shared, same as above except that Guest access is turned on.

From a remote machine (Windows or Linux) I can see the shares. 

I can view the contents for Folder2 -- This is the one with Guest access turned on. 

When I go to view Folder1, I am asked for username and password (when trying to view from a Windows machine) or username, domain, and password (when viewing from another Ubuntu machine). 

On a Windows machine I enter the username that owns the folder (per the Properties of the folder), and that user's password. The login fails and the login box reappears. From my other Ubuntu machine, I enter the username, (don't even know what to enter for "Domain so I have the Workgroup name that all the machines belong to here) and password, and no luck -- the login window pops back up.

I do need access to this folder and its subfolders to be password protected. I'm a little stumped here.

---

