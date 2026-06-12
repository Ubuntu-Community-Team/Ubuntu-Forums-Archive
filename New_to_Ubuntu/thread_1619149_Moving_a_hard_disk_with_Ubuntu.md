---
title: "Moving a hard disk with Ubuntu"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by littleknowledge on 2010-11-11
Good day!

I have a computer set up with ubuntu and all the software and settings I require. I would like to "clone" this hard drive to put into several other computers of different hardware. Is there anything special I need to do for ubuntu to 're-query' the hardware?

thanks for any help

---

### Post by Temposs on 2010-11-11
I would not recommend cloning an Ubuntu install for another computer. Having different hardware will definitely make a difference, and the computer will probably not work well or at all.

What you want to do if you want to keep your same files and settings across different computers is to actually install Ubuntu the normal way on one of your other machines and then copy over your /home folder. This folder contains most settings for your applications, as well as personal files like documents and photos.

Of course, there are more sophisticated ways to do these things, but this would be the simplest way.

---

### Post by Verbeck on 2010-11-11
try remastersys to create a distributional copy of your installation

[http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb](http://www.geekconnection.org/remastersys/repository/karmic/remastersys_2.0.17-1_all.deb)

even though it says karmic, works for lucid and maverick too

---

### Post by oldfred on 2010-11-11
Most things just work. Video drivers are often the biggest issue.

One user did this:
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

Otherwise you could install a generic video driver.

---

### Post by littleknowledge on 2010-11-11
Thanks for the info! 

Although Oldfred's suggestion seems like it would do the trick, I think the individual installation + data as suggested by Temposs seems to be the most stable. I will give this one a shot.

Thanks again for your help, linux never seizes to amaze me!

---

