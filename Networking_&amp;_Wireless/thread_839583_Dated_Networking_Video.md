---
title: "Dated Networking Video"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by Tom_ZeCat on 2008-06-24
Darn it.  This video is just what the doctor ordered, but it's out of date for Ubuntu 8.04.  The video is about Ubuntu 6.10.  

[http://youtube.com/watch?v=Ad17kma8rNM](http://youtube.com/watch?v=Ad17kma8rNM)

It says to go to: 
> System ===> Administration ===> Shared Folders.  

The closest I can find is 
> System ===> Administration ===> Services ===> Unlock ===> [scroll down] ===> Folder Sharing (samba)

However, when I try to double click on that, I don't get the same window as shown in the video.  What is the 8.04 equivalent to 6.10's "System ===> Administration ===> Shared Folders"?  Or is there an updated video about home networking for Ubuntu 8.04?

---

### Post by komputes on 2008-06-24
Yes, I've noticed this too, it seems that the "shares-admin" application you are referring to has been removed from the menus Hardy. I think it stopped working or they voluntarily took it out. I say this because it is still there, both on my Hardy and on my Gutsy computer.

If you go to a terminal and type the following command it will bring it back up, although I am not sure if it is still recommended to use this interface. 

shares-admin

I have tested it and I'm not satisfied because it does not seem integrated into samba and it does not post the correct paths. Very flaky, very weak. I'm not very impressed by the integration of samba into Hardy at the moment but apparently it's being worked on.

---

