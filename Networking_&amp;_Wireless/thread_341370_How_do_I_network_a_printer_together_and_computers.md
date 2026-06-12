---
title: "How do I network a printer together? and computers?"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by thenetduck on 2007-01-18
Hi, 
  My family has 3 computers in the same room all running Ubuntu (I got em all to switch hehe). We have a printer that we would like all of the computers to use, but can seem to figure out two things. 
   1.) How can I network our computers together? What I mean is how can I share files from one computer to another computer. I have tried the "shared folder" but that hasen't seemed to work. I'm not sure if I should be using the Windows netwoking or the Unix networking and even if I did, I don't really know anything about host names etc. (I'm really bad at networking) Does anyone have a guide or could someone help me through the networking presses to get all of our computer sharing files? 
    2.) How can we all use the same printer from different computers? The installation process for the singer printer on a computer was really easy and I guess that the networking of the printer is easy, however I don't even know the basics to networking. 

 Any help will be usful for me because I don't know anything when it comes to networking. Thanks 

 The Net Duck

---

### Post by lhtown on 2007-01-18
Unfortunately, there is no easy way I am aware of to go about file sharing. You are probably looking at either Samba, which is a bear to configure, or nfs file sharing which isn't all that easy either. You will find tons on information on these forums, and most of it is about as clear as mud for the uninitiated.

As for printing, the easy thing is to get a router that supports printer sharing. That's what I have. Otherwise, I think that cups does sharing.

Disclaimer: I stink at networking.

---

### Post by ianmac on 2007-01-18
File sharing can be done using ssh...

You need to setup the ssh server...  check out:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server)

For printing, check out:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Print_Server_.28cupsd.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Print_Server_.28cupsd.29)

This should get you started...

Ian

---

