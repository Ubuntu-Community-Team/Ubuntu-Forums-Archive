---
title: "VERY new - have questions about IP forwarding, static IP, proxy, and other - PLEASE?"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by NoOnee on 2010-08-22
Hi.  I'm very, VERY new, so please be gentle ;) 
 
 Hopefully, I'm posting this in the right spot, if not, please let me know where it should have gone and why.
 
 I've been a Windows user and decided to try a Linux based OS after hearing a lot of good things.  Usually, with new programs I'll learn best by just jumping in and playing around, and reading about stuff as I go along.  And yep, I've backed up everything just in case anything gets broke and the full system needs to be reinstalled.  :) 
 
 I've decided to try Backtrack 4 R1 and have installed it as a dual boot.  First I tried to use it in Virtual Box, but although it could be bridged to get some net access for browser use, I learned that VB  does not recognize the built-in wireless drivers and that's why I couldn't do a lot of things I had read about for BT4.  Since I can't get a wireless USB right now, I went and installed it as dual-boot. 
 
 I've played with it only a tiny, tiny bit and have not been able to find answers to a couple of questions, or have been confused by too many different answers, so I'm hoping to find simple, easy clarification here.  Please? 
 
 
 1) I haven't found any good manuals yet and wanted to ask, will the Ubuntu Pocket Guide help with BT4 commands?  (I was thinking they might basically have the same commands since they're both Linux?) 
 
 2)  After starting ip forwarding using this command "echo "1" > /proc/sys/net/ipv4/ip_forward",  and then I run the command "iptables -t nat (etc, etc)"... when i want to stop without rebooting, how do i reverse this and make it stop forwarding?  
 
 I'm wondering, does rebooting cancel the process automatically too?  If not, does the setting carry over when I boot into Windows? 
 
  3)...a)  How do I set up a static IP (for example, on Windows, I have it set that i'm always 192.168.2.123), and how to I make it keep that setting when I reboot?  I tried ifconfig and it SEEMED to change it for the session, even in the wcid window, but when I ran nmap, it still showed me as 192.168.2.2, so I must have done something wrong there...?? 
 
  .....b)  If I needed to UNDO the static IP and go back to (dynamic?), how do I undo the static IP settings so it would pick an address at random?  Are there two different ways if I wanted to set this per session vs. permanent? 
 
 4) I have a Firewall/Virus program in windows, TrendMicro, but I'm guessing it's not going to carry over into BT4.  Do you know if it comes pre-configured with anything?  Or is there a decent FREE program I'd have to download and install? 
 
 5)  I know I've seen this question on several forums and never really saw a good answer, but I also want to set up chain proxy.  I've found instructions on getting it to work with tor/privoxy, but have also heard that in Linux based systems, it tends to leak some info.  Can you offer any assistance here too please? 
 

 I know that's a LOT, but for me those are my getting started questions.  Yep, I have quite a few more, but these are the one's i'm anxious to take care of asap, and hopefully a good manual will answer a lot of others so if your manual will help, that'd be awesome - if not, can you recommend a good one please? 
 
 Thank you very much for taking the time to read my questions, and special thank you for anyone who can help. 
 
 Have a great day.  :)

---

### Post by howefield on 2010-08-22
Try breaking your questions into paragraphs, make it a little easier on the eye and therefore worth reading.  ;-)

---

### Post by NightwishFan on 2010-08-22
My friend, welcome to Ubuntu, and Ubuntu forums! I will give you some quick advice on how to get help. This is not criticism. :)

It is hard to read that paragraph and see what you actually need for help. You can edit the post at the bottom right of it and separate the points. Then I can take it point by point. Also, rather than a mega thread, you can ask a few basic questions here, and start a new thread for each individual question, if they require it. Something simple does not.

Other than that, welcome, and I hope you like Ubuntu, I certainly do.

---

### Post by uRock on 2010-08-22
> Hi.  I'm very, VERY new, so please be gentle :wink:   Hopefully, I'm posting this in the right spot, if not, please let me  know where it should have gone and why.  I've been a Windows user and  decided to try a Linux based OS after hearing a lot of good things.   Usually, with new programs I'll learn best by just jumping in and  playing around, and reading about stuff as I go along.  And yep, I've  backed up everything just in case anything gets broke and the full  system needs to be reinstalled.  :smile: 

I've decided to try Backtrack 4 R1 and have installed it as a dual  boot.  First I tried to use it in Virtual Box, but although it could be  bridged to get some net access for browser use, I learned that VB  does  not recognize the built-in wireless drivers and that's why I couldn't do  a lot of things I had read about for BT4.  Since I can't get a wireless  USB right now, I went and installed it as dual-boot.  

I've played with  it only a tiny, tiny bit and have not been able to find answers to a  couple of questions, or have been confused by too many different  answers, so I'm hoping to find simple, easy clarification here.  Please? 

1) I haven't found any good manuals yet and wanted to ask, will the  Ubuntu Pocket Guide help with BT4 commands?  (I was thinking they might  basically have the same commands since they're both Linux?)  

2)  After  starting ip forwarding using this command "echo "1" >  /proc/sys/net/ipv4/ip_forward",  and then I run the command "iptables -t  nat (etc, etc)"... when i want to stop without rebooting, how do i  reverse this and make it stop forwarding?   I'm wondering, does  rebooting cancel the process automatically too?  If not, does the  setting carry over when I boot into Windows? 

3)     a)  How do I set up a  static IP (for example, on Windows, I have it set that i'm always  192.168.2.123), and how to I make it keep that setting when I reboot?  I  tried ifconfig and it SEEMED to change it for the session, even in the  wcid window, but when I ran nmap, it still showed me as 192.168.2.2, so I  must have done something wrong there...?? 
       b)  If I needed to UNDO  the static IP and go back to (dynamic?), how do I undo the static IP  settings so it would pick an address at random?  Are there two different  ways if I wanted to set this per session vs. permanent? 

4) I have a  Firewall/Virus program in windows, TrendMicro, but I'm guessing it's not  going to carry over into BT4.  Do you know if it comes pre-configured  with anything?  Or is there a decent FREE program I'd have to download  and install? 

5)  I know I've seen this question on several forums and  never really saw a good answer, but I also want to set up chain proxy.   I've found instructions on getting it to work with tor/privoxy, but have  also heard that in Linux based systems, it tends to leak some info.   

Can you offer any assistance here too please?   I know that's a LOT, but  for me those are my getting started questions. Yep, I have quite a few  more, but these are the one's i'm anxious to take care of asap, and  hopefully a good manual will answer a lot of others so if your manual  will help, that'd be awesome - if not, can you recommend a good one  please?  Thank you very much for taking the time to read my questions,  and special thank you for anyone who can help.  Have a great day.  :smile:Welcome to ubuntuforums.org Hopefully someone with experience in Back|Track will be able to help you here.

---

### Post by corrytonapple on 2010-08-22
Try the Back|Track forums.
[backtrack-linux.com]("http://ubuntuforums.org/backtrack-linux.com")
Also, why did you choose Back|Track? Ubuntu is better for a beginner.
> **NightwishFan said:**
> My friend, welcome to Ubuntu, and Ubuntu  forums! I will give you some quick advice on how to get help. This is  not criticism. :)

It is hard to read that paragraph and see what you actually need for  help. You can edit the post at the bottom right of it and separate the  points. Then I can take it point by point. Also, rather than a mega  thread, you can ask a few basic questions here, and start a new thread  for each individual question, if they require it. Something simple does  not.

Other than that, welcome, and I hope you like Ubuntu, I certainly do.
Right on, Nightwishfan

---

### Post by NoOnee on 2010-08-22
Sorry about that big paragraph... I made the mistake of posting WITHOUT previewing... a good lesson for other newbies, PREVIEW before you post, it didn't take any of my paragraph marks... But it's fixed now... Thank you kindly  :D

---

### Post by NoOnee on 2010-08-22
> **corrytonapple said:**
> Try the Back|Track forums.
[backtrack-linux.com]("http://ubuntuforums.org/backtrack-linux.com")
Also, why did you choose Back|Track? Ubuntu is better for a beginner.

   
I've already checked their forums and couldn't find these particular answers either.  As for choice of program, it was the one that came up most often in searches and a few conversations.  Are they THAT different to work with, or is it more a matter of available commands?

---

### Post by corrytonapple on 2010-08-22
It is quite different. Burn a Ubuntu live CD and try it out. If you like it, erase Back|Track, and put on Ubuntu.
First, you get the community. Second, you get a stable, customizable, user friendly OS.

---

### Post by NoOnee on 2010-08-23
> **corrytonapple said:**
> It is quite different. Burn a Ubuntu live CD and try it out. If you like it, erase Back|Track, and put on Ubuntu.
First, you get the community. Second, you get a stable, customizable, user friendly OS.


So that sounds like if I don't get Ubuntu, then I won't be getting any help here...??  And it sounded like such a friendly and helpful community when I was reading through the threads...  :(

---

### Post by QLee on 2010-08-23
> **NoOnee said:**
> So that sounds like if I don't get Ubuntu, then I won't be getting any help here...??  And it sounded like such a friendly and helpful community when I was reading through the threads...  :(

Well, the quality of the help you get on a forum from people who aren't familiar with the operating system that you are using may not as useful as on that operating system's forum, that's probably why the BT forum was suggested.

However, BT is a distro specifically aimed at forensics with a toolbox of useful tools for that, overkill for someone who is inexperienced. Probably the reason Ubuntu was suggested was the users here are familiar with it and can be more likely to be able to help with issues on Ubuntu.

But you have the choice to run what you like and people here will still try to help, just make sure to mention what you are running when you ask a question, in order to prevent confusion.

---

### Post by uRock on 2010-08-23
> **NoOnee said:**
> So that sounds like if I don't get Ubuntu, then I won't be getting any help here...??  And it sounded like such a friendly and helpful community when I was reading through the threads...  :(

Back|Track is not for beginners. Many of the common tolls that are used can be installed on Ubuntu pretty easily, such as Zenmap- a port scanner, Wireshark- a packet catcher and reader, TCPDump. You already have nmap, which is a command line port scanner and in the menus you have the Network Tools application that allows you to do a few network troubleshooting tasks.

The reason you find this community less helpful is because the people who maintain Back|Track ripped most of the ubuntu out of the OS to make it lighter and to create room on their LiveCD for their tools, which are plenty when you look at the menus.

The best bet would be to install Ubuntu and learn the OS, then install Back|Track and learn their tools.

---

### Post by corrytonapple on 2010-08-23
> **NoOnee said:**
> So that sounds like if I don't get Ubuntu, then I won't be getting any help here...??  And it sounded like such a friendly and helpful community when I was reading through the threads...  :(
No. Ubuntu and Back|Track are very different. Look at Debian and Ubuntu. You can see how they are alike, but they still are very different. Back|Track has different menus, tools, and Grahpics User Interface. Thats like asking a question about Windows XP in a Windows 7 forum. See what I mean? Just try Ubuntu and give us your thoughts.

---

### Post by NoOnee on 2010-08-23
I've seen other topics in your forum assisting with other OS's, so it's really more of an animosity towards BT4 specifically, due to that reason?? 

That's kind of a shame really because it's hard to find any program that hasn't been influenced or modified from another anymore, ie: all those messenger programs out there - and though I wouldn't know myself, I'm sure some other people would say Ubuntu was ripped/influenced/modified from some other OS.  I know it's been said often "There is no such thing as an original idea". 
  
 I really do appreciate the info, and I do hope y'all will consider assisting and chatting with me in spite of that dislike for BT4 because I am listening.  And if someone is familiar with both programs, it would be the "best case scenario", in other words SUPER HELPFUL, to be able to hear the differences on how things are done.  For example, I know Wireshark comes with BT4 R1, and I have it in Windows (though just getting started with that one too), but I didn't know it could be used with Ubuntu - the downloads only say for Windows and OS X 10.5 (Leopard); another example, if setting the static ip command works one way for BT, and another way for Ubuntu, that would also be great information, and so on. 
 
 I just wish VirtualBox would directly use the wireless - then I could put both BT & Ubuntu there and do a side by side comparison :)  It's just a shame they don't have well-detailed New-even-for-a-Newbie manuals for these, like Ubuntu/BT4r1/wireshark ".. for Dummies "  :D

---

### Post by uRock on 2010-08-23
This thread is going with the wrong vibe. Very few people here have used BT and this is why you are having a hard time getting help. It has nothing to do with people discriminating against Back|Track.

---

### Post by QLee on 2010-08-24
[QUOTE=NoOnee]...  It's just a shame they don't have well-detailed New-even-for-a-Newbie manuals for these, like Ubuntu/BT4r1/wireshark ".. for Dummies "  :D[/QUOTE]
Well, it's extremely hard to write "for Dummies" documentation for an operating system that is specifically crafted for forensic and security experts because they don't start out using BT and its tools as "dummies", they are already familiar with operating systems and how they work, that's why they are able to do computer forensics and pen testing. As people have stated, BT isn't a good choice for an inexperienced user, however, the choice is yours and I wish you good luck.

---

### Post by eriktheblu on 2010-08-24
I'll try to help a little
> **NoOnee said:**
> 
 2)  After starting ip forwarding using this command "echo "1" > /proc/sys/net/ipv4/ip_forward",  and then I run the command "iptables -t nat (etc, etc)"... when i want to stop without rebooting, how do i reverse this and make it stop forwarding?Not certain what this means but```
echo "1" > /proc/sys/net/ipv4/ip_forward
```would create a file with a single line (that line displaying "1")
Stands to reason if the presence of that 1 stars ip forwarding, it's absence (or modification) would stop it.

Really just a shot in the dark but```
echo "0" > /proc/sys/net/ipv4/ip_forward
``` or ```
rm /proc/sys/net/ipv4/ip_forward
```

>   3)...a)  How do I set up a static IP (for example, on Windows, I have it set that i'm always 192.168.2.123), and how to I make it keep that setting when I reboot?  I tried ifconfig and it SEEMED to change it for the session, even in the wcid window, but when I ran nmap, it still showed me as 192.168.2.2, so I must have done something wrong there...?? 
Everything I've seen for this involves editing /etc/network/interfaces.
[http://codesnippets.joyent.com/posts/show/319]("http://codesnippets.joyent.com/posts/show/319")
 
>   .....b)  If I needed to UNDO the static IP and go back to (dynamic?), how do I undo the static IP settings so it would pick an address at random?  Are there two different ways if I wanted to set this per session vs. permanent? Before editing /etc/network/interfaces, make a backup with ```
sudo cp /etc/network/interfaces /etc/network/interfaces.old
```
to restore ```
sudo cp /etc/network/interfaces.old /etc/network/interfaces
```

---

