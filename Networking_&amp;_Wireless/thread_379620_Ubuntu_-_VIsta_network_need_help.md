---
title: "Ubuntu - VIsta network? need help"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by 9.daemon on 2007-03-08
EDIT>>>>>>>>>>>>>>>> I solved it!  all I had to do was learn to use samba :P    

HI, I am a total newbie who recently switched from windows vista (been a windows user all my life) to ubuntu linux and I am loving it!  

I have 1 desktop PC and 1 laptop, this is the desktop PC, im using Ubuntu on it.

The laptop uses windows vista and it connects to the internet through my wireless router, however, the desktop pc is connect to the same router through an ethernet cable. 

I have no problems getting to the internet (i didnt even have to configure anything, it automaticly connected) but when I try to access the Laptop running vista, I go to Places > Network servers and I see  "windows network"  then  "jafher"  (it is the name of the laptop's workgroup)  then I see the laptop I double click it and it asks me for a username and a password.

I tried the username / password that the laptop uses and it didnt work, i tried making a guest account in vista and used that username /password and it didnt work, and I have this feeling I have no clue what I am doing.

I am slowly learning to use the shell and I have managed to get my ubuntu up and working quite nicely but im still a newbie, specially on this network subject, how can I access the vista laptop from ubuntu?

Thanks :)

---

### Post by noslenj123 on 2007-03-13
Bump!

I'm having the exact same problem.  Seems no matter what account name I try to use, it won't connect to the Vista computer.  The firewall is turned off on the Vista machine.  When I try to connect to the Vista pc from an XP pc, I have no problems.......

Anyone have a clue what we can try?

---

### Post by 9.daemon on 2007-03-14
bump..

samba only lets me access my ubuntu pc from vista but not the other way around :(

how can i acess my vista pc from ubuntu?  it says the contents cannot be displayed

---

### Post by NautArch on 2007-03-16
I'm having the same issue.  I see my computer under Network, but when I try and open it and enter my username/password, it doesn't seem to accept it.  If I cancel out, I get the error "couldn't display all the contents". If I don't it just keeps asking for my authentication.

---

### Post by lukew on 2007-03-16
> **NautArch said:**
> I'm having the same issue.  I see my computer under Network, but when I try and open it and enter my username/password, it doesn't seem to accept it.  If I cancel out, I get the error "couldn't display all the contents". If I don't it just keeps asking for my authentication.

Hi

you dont use a user name and password. You should use a samba username and password which maps onto a user account.

The Customization Guide has a very good guide to getting samba set up and running.

Luke

---

### Post by Sellout on 2007-03-16
you probably can't see the contents because by default ubuntu wont let you view NTFS formatted drives, which vista uses by default.  

see [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009) for an ntfs ubuntu solution that will at least let you read your vista computer.

---

### Post by Nergar on 2007-03-21
> **9.daemon said:**
> EDIT>>>>>>>>>>>>>>>> I solved it!  all I had to do was learn to use samba :P    

HI, I am a total newbie who recently switched from windows vista (been a windows user all my life) to ubuntu linux and I am loving it!  

I have 1 desktop PC and 1 laptop, this is the desktop PC, im using Ubuntu on it.

The laptop uses windows vista and it connects to the internet through my wireless router, however, the desktop pc is connect to the same router through an ethernet cable. 

I have no problems getting to the internet (i didnt even have to configure anything, it automaticly connected) but when I try to access the Laptop running vista, I go to Places > Network servers and I see  "windows network"  then  "jafher"  (it is the name of the laptop's workgroup)  then I see the laptop I double click it and it asks me for a username and a password.

I tried the username / password that the laptop uses and it didnt work, i tried making a guest account in vista and used that username /password and it didnt work, and I have this feeling I have no clue what I am doing.

I am slowly learning to use the shell and I have managed to get my ubuntu up and working quite nicely but im still a newbie, specially on this network subject, how can I access the vista laptop from ubuntu?

Thanks :)


Can u post how u solved it??? Don't you think is much nicer of you to help other ppl with the same problem rather than say you solve it?

---

### Post by postalservice14 on 2007-03-23
Please post how you solved it....

Thanks,

John

---

### Post by jeffreypop on 2007-11-01
To create a login using Samba:

sudo smbpasswd -a username

...where *username* was the same login as the administrative account which owns the folders you wish to share.  You will need to supply a password and verify it when prompted.

---

### Post by froy02 on 2007-11-02
See this link for a possible solution:
[http://ubuntuforums.org/showthread.php?t=598887](http://ubuntuforums.org/showthread.php?t=598887)

---

