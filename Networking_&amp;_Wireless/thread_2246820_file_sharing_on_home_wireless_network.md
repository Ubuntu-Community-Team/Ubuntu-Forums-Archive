---
title: "file sharing on home wireless network"
date: 2014-10-03
forum: Networking &amp; Wireless
---

### Post by spencer2 on 2014-10-03
Hi; i am curious about a few things concerning doing file sharing over my wireless network. 
I have 3 laptops all running ubuntu. My network is already set up and i've set up a couple folders on my desktops for the sharing. I've also already gone into the permissions section and set to share the folders to share. 
I've read multiple samba installation guides and have seen a couple slightly different variations of the terminal code for installation and setting shares. I am competent enough that i can go into the terminal and type code, find the info that commands kick out but am not good enough at code to I really know what i'm looking at or typing in  and what all that means.So not novice, i'd not comfortably call myself intermediate either.  
When I initially set up the sharing folders i did get asked for a password during the set up but i didn't really know what i was doing at the time so I didn't set anything and now I also don't know how to get back to it to set a password. From some of what i've read, it seems as though for sharing multiple files across multiple laptops on my network, samba file sharing would be a better option to begin with, so I'm cool with doing samba as oppossed to the generic sharing service --- but I would like to know which set of terminal codes would be best and which tutorial would be the most appropriate for my ubuntu only network. 
Any help with this stuff would be greatly appreciated: thank you.

---

### Post by spencer2 on 2014-10-03
I'm sort of thinking this is the best of the guides that i've looked at:

[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

---

### Post by Michael_McKenney on 2014-10-03
I set Samba up for only my users and set others to no access.

---

### Post by weatherman2 on 2014-10-03
I am not a novice - I have setup Samba numerous times over the years with all of the command-line stuff.  But these days, when doing simple sharing of folders on Ubuntu over a home network, I simply use the built-in Nautilus sharing - right-click on the folder and say "Share."  I did that recently on a new Ubuntu 14.04 install and it worked fine.  I was prompted to install some sharing packages the first time I shared a folder, but none of that required terminal commands; I simply followed the instructions and installed the packages via the mouse and windows.  It was painless.

FYI, the built-in Nautilus sharing - what you seem to have started to use - *is* Samba.  It's simply doing it in the background for you, without requiring a manual setup.

How to get back and set a password?  Easy: go back to the original folder you shared, right-click on the folder again and choose "Sharing" again.  Now you can change the sharing options.  The password option would be for an account on the Ubuntu computer which has the folder you are sharing.  If this is just you or trusted friends sharing these folders, you could simply use the user you already created for Ubuntu - so if you called the username "joe" and the password is "abc123," use that username/password.  If you want to protect that login account (because you have other home users whom you don't trust as much or something), instead of using "joe" create another user in Ubuntu called say "jane" and limit the access of that account - then give people on your home network the "jane" login and password.  Or, create Ubuntu users (accounts) on that machine for each individual user.

If you do have multiple users/accounts, you may need to set the folder permissions in the shared folders to belong to a single group that all users belong to - so the folders/files all belong to the group "homeusers" (or whatever group you create), then make sure all users/accounts belong to the "homeusers" group you have created.

---

