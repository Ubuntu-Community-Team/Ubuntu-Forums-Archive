---
title: "Teathering Phone Internet Around Wireless Carrier Restrictions"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by Michael_Kolonay on 2013-10-24
I recently set about trying to connect my laptop to the internet using the 3g connection on my phone.  Sprint has denied me this possiblity out of the box, but I have found a work around using some developers options.  The walk-through I followed can be found **here**:[http://www.asgrim.com/2009/07/24/tethering-your-htc-magic-android-phone-in-ubuntu-9-04-jaunty-jackalope/](http://www.asgrim.com/2009/07/24/tethering-your-htc-magic-android-phone-in-ubuntu-9-04-jaunty-jackalope/)

For the most part, I understand everything the guide has me doing, and I have been able to successfully connect to the internet using only my phone's connection.  However, I feel that the guide stops short (the process it uses for subsequent connections is not nearly clean enough for my tastes), so I was hoping for some help with a few issues in particular:

1) **Security**: From what I can tell the connection is being established with no security at all.  It seems to me the internet connection is coming through a vpn connection with no encryption.  I am not sure if I need security for this kind of connection, but I do I would appreciate some insight on where to start.

2) **Make Commands Accessable**:  I was unable to figure out how to add the directories necessary to my path.  I searched elsewhere for more information, but it seems I was not able to find the lines I needed to add to my .bashrc file.  These are the lines I added (they are slightly different than the ones in the guide to reflect the difference in the actual pathname in my bundle download and system):

**export PATH=$PATH:/opt/android-sdk-linux/adt-bundle-linux-x86-20130917/sdk/tools**

[B]export PATH=$PATH:/opt/android-sdk-linux/adt-bundle-linux-x86-20130917/sdk/platform-tools
[/B]
I was able to use them anyway by using the full file path each time, but this was obviously cumbersome, so I would really like to know where I am going wrong as far as adding the path is concerned.  And perhaps a simple description of what this process is actually doing...

3)**Setup Nameserver**: Using the /etc/resolv.conf is not ideal for me since I use the network manager (I find the interface useful since this is a laptop and often has to connect to new connections), so my changes will never stay in resolv.conf.  Perhaps there is another file I can edit or a profile I can create and access via the network manager...

Please feel free to ask for clarifications on anything and thanks in advance,
Michael Kolonay

---

### Post by Michael_Kolonay on 2013-10-24
Update: I have solved my second issue on my own.  Seems it was an issue with file permissions.  I checked and found that the paths had been added using **echo $PATH**, but they could not be accessed because they were not executable.

This leaves issues number one and three.  I am not looking for anything earth-shattering as far as my security question goes: simply a yes or no to whether I should worry about it and a general direction.
 
As for question 3 I figure I would be happy with a bash to add the nameserver line to my /etc/resolv.conf.  I can look into that myself, but I have no prior experience with writing scripts and I figure there may be an easier, cleaner way via the network manager.

---

### Post by Michael_Kolonay on 2013-10-24
Update: I have solved issue 3 as well (nearly).  I found a simple script in the comments section of the original walk-through: 
    **   adb forward tcp:41927 tcp:41927**[B] 
      sudo openvpn /home/michael/azilink.ovpn[/B]
[B]       sudo cp resolv.conf /etc/
[/B]My only remaining issue as far as that is concerned is that I am unable to add the command to my launcher based on permissions issues. I have the file saved as 'connectphone' in my home folder, and I am able to launch it by using: **sudo ~/connectphone**.  I use gnome,so I attempted to add a launcher that employed the command, but I could not figure out how to give it the correct access.  I have also tried adding this line to the sudoers file: **michael  ALL=(ALL) NOPASSWD: /home/michael/connectphone**, but that did not work either.  For now I will live with entering a line via the command line, but I'd prefer to have a single click from the desktop, and I feel I must be close...

Question 1, which is still my top priority, has yet to be answered.  My gut reaction is that security is not actually too much of an issue since the unencrypted information is all being sent over usb, right?  However, if need be, I believe there is a way to add a password to the openvpn configuration file; nonetheless, I would prefer to tunnel through my existing ssh connection or use keys if that were possible...

---

