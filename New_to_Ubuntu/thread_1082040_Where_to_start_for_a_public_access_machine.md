---
title: "Where to start for a public access machine?"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by Dobbick on 2009-02-27
I have a query, I have a small shop with broadband installed.  I would like to setup a machine or 2 to allow internet access for the public.  I have no intention of using windows for this as I don't want customers messing with settings or installing their own programs, and lets face it, security is not exactly a Windows strong point.

I'd like to use Ubuntu or maybe Kubuntu, (the latter only because I've heard of Admin Kiosk which seems like something I would need, if there is an alternative for Ubuntu, that would do me fine)  I would suspect I will need VNC for remote access to the machine as I will be accessing the it remotely from a Windows PC, and I have no idea how to use SSH.  The machine will also have Openoffice, Firefox, and a IM client like Pidgin along with CD/DVD burning software and network access to a printer.  

I'd like to have a multiple partition setup, a boot/system partition and a seperate data partition.  Is it possible to disable write access to the system partition and force all flies in use by the customers to write to the data partition?

I will be restricting physical access to the machine via a padlock and chain to a mounting bracket on the wall, and have a BIOS password.  I will also be disabling booting from CD and USB.  

Has anyone any advice for me on setting this sort of thing up, or anything else I would need?  Have I forgotten anything that I should have; for example, if a customer with Linux experience uses the machine will they be able to mess with the machines and make them non functional?  Is there any Internet Café software available that would help me restrict customers access and manage the time they have been online?

What is the best way of having the system partition backed up so it is easily restorable to a working state in case someone does manage to mess it up?   Is there a way of taking a snapshot of the drive ala Ghost?

Sorry for so many questions, I'm getting excited at the prospect of setting this up but I'm not sure of where to start...

I've already looked at this thread [http://ubuntuforums.org/showthread.php?t=758030](http://ubuntuforums.org/showthread.php?t=758030) but it doesn't really tell me everything I need..

Thanks in advance

---

### Post by blazemore on 2009-02-27
I don't think anyone will mess it up.
Add massive desktop icons
Use one Gnome-panel and lock it
Take a snapshot every night with something like remastersys
**Have Firefox set to clear all private data on exit**

---

### Post by mkvnmtr on 2009-02-27
I have heard of some internet cafe software but I can't name it. From my use of Ubuntu I think if you set up a guest account your customers can't change any thing with the system outside of that account. I think if I was going to allow people to use the machines I would set up several guest accounts and then if in the middle of the day something went wrong with one the next person could just log into another. Then when you have time fix or delete the problem. I think it will be easy to do. Remember it only takes about an hour to reinstall. If you make a dvd install disk of your system you can reinstall in almost no time and be back with the same system with out downloading all the apps again. I can't imagine what would be required to get a windows system to work and be secure but a Ubuntu system I think you can have ready in just one day. I am sure somebody with real experience will post some better help than mine.

---

### Post by superprash2003 on 2009-02-27
is the windows machine and the ubuntu machine on a LAN?? if so you could simply enable remote desktop (system->preferences->remote desktop ) and then use vnc viewer in windows!! 

for reference : [http://www.prash-babu.com/2008/05/how-to-remote-control-ubuntu-machine.html](http://www.prash-babu.com/2008/05/how-to-remote-control-ubuntu-machine.html)

---

### Post by Dobbick on 2009-02-28
Thanks for the suggestions, so if i make multiple guest accounts, can i grant them access to a cd burning tools etc?  also whats the situaution with using a second data partition for downloaded files and stopping write access to the boot partion?

Thanks

---

### Post by mkvnmtr on 2009-02-28
The user should have access to any apps that are installed in any account that is not the administrative user. I don't know how to allow downloads to only one partition but I would assume it can be done and not overridden by the user. As for changing the system the user has no access to any thing but his home. He can't alter the system. Try it on a system. Just open another account. give it the permissions you want it to have and use it. You should see what I mean. There is a thread in the testimonials forum now about a guy that just opened a internet cafe using Ubuntu and it is very informative. You might look at that for ideas.

---

### Post by 68omalley on 2009-03-04
This thread may be helpful, someone has set up Ubuntu machines in a public library and his howto is pretty good:

[http://ubuntuforums.org/showthread.php?t=707688](http://ubuntuforums.org/showthread.php?t=707688)

---

### Post by Dobbick on 2009-03-16
[FONT="Arial"]An Update

Well, I took my machine, installed 8.04lts and everything worked. It was so nice for an OS to work so easily. Except for one thing,  I couldn't get a resolution on the onboard graphics to go higher than 800*600.  I had a spare AGP card around so I installed it, an nv5500.  to my amazement Linux happily told me about the card and the driver, downloaded it, and I rebooted.  

I now could get more resolutions, but still none higher than 800*600...I reckoned I could come here and ask for help, so that wasn't a worry, installed things like flash so my daughter could play on he favourie website, she was delighted.  

and then someone pulled the plug...literally.  Someone was cleaning and unplugged the pc by accident.  it got stuck in a boot loop with the screen flashing slowly and would not go any further.  Oh well I thought, it was so easy I can just reinstall it all, and this time i'll leave the nvid card in during the install and maybe it will be happier. It was late so I gave up for the night, decided to continue next weekend.  

And thats as far as my story goes, the next week we folded the business due to a few reasons and my ubuntu linux machine lies in my shed untouched since. but I just want to say thanks to those of you who answered with help, believe me that this won't be the last time I'll install Ubuntu, I've read through most of the pocket guide, and intend to build a machine for my daughters bedroom, and can't think of a better OS, so none of this has gone to waste.

Thanks again.[/FONT]

---

