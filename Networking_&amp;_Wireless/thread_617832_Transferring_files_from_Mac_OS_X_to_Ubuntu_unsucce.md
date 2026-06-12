---
title: "Transferring files from Mac OS X to Ubuntu unsuccessful?"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by baffled_person on 2007-11-19
Hello, I have an inquiry, after fiddling around with this for at least five hours with no success.

My quandary is as follows:  Yesterday, I finished transferring all my files from my MacBook (where I am storing my computer's files prior to the installation, because I wasn't doing a dual-boot because my computer, which was previously running Windows XP Professional, was ridden down with too many viruses and I thought it was time for a change, so that system is now completely wiped), and I installed ubuntu. Now, I am in the process of attempting to send these files back to the desktop (that is running ubuntu now) from the laptop. I transferred them fine, yesterday, but it seems the Mac to Ubuntu situation is not going as smoothly as I would like. I can't connect to the desktop using the Mac, because every time I try to connect, I am given a password prompt, and even though I either leave it blank or type in the same password I am using to log into ubuntu, I get the same error message:

"The alias could not be found, because the original item cannot be found". 

I don't understand getting this error message, because as far as I can tell, the permissions I set on the folder did not call for a password. I do not understand why I'm being asked for one and the one I'm putting in (which I've checked countless times for spelling errors) is not working. I turned file sharing and Windows file sharing on on the Mac, but none of the files on the Mac are showing up on the ubuntu system. 

What I would like to know is either:

- how to connect to the Ubuntu using the MacBook so I can transfer my files back
- how to connect to the MacBook using Ubuntu so I can transfer my files back (there seem to be no tutorials on how to do it the other way around). 

I did this wirelessly when I was on Windows, so I am not sure why it is not working out and I don't have access to an external hard drive or an ethernet cable, because if I did, I would have done it already. I set up Samba already. 

Thanks in advance.

---

### Post by vsiege on 2007-12-05
Hey, I would love to knwo the answer to this too... move the post to the mac forum here to see if you get a response. Maybe that will help.

---

### Post by zorkerz on 2007-12-10
Im looking into doing something similar to this. What do you know about mac filesharing? Are you using the default mac method or have you set it up for samba (the windows protocol i believe). I don't know enough about mac filesharing yet to be of much help im afraid.

---

### Post by vsiege on 2007-12-10
I installed the 7.10 server edition of Ubuntu, then put the xubuntu desktop on. I could get ubuntu to mount on my mac but not the other way around. So then I installed the Ubuntu desktop and everything changed for both desktops... i could get both to mount, on each system, and for each desktop environment (GNOME and Xfce).

Mac Settings>
System Preferences>Sharing>
Enable....
Personal File Sharing
Windows Sharing
Remote Login (probably dont need this... i just have it on)
FTP Access (probably dont need this... i just have it on)

I used the Root login to make my life easier.... most people will freak out and tell you all the possible things that can go wrong. Its your computer and your choice.

Make a directory on your Ubuntu machine shared... give it the privilages you want... in my case I gave it a group where it could read and write. Now when you go to log into this folder from the mac.... leave all the fields blank and it should mount. from the ubuntu machine: go to places>Network.... and you should see two versions of the mac drive you want... one with a SSH (if you allowed Remote Login) and one with FTP (if you allowed FTP Access). hyou can even find you mac drive under Places>Network>Windows Network>workgroup

Hope this helps... as I have more time i will put together my version of a HOWTO.... that will include how to use different accounts... b/c at the moment i dont have enough time to figure that out... if you find out or need more help get in touch

---

