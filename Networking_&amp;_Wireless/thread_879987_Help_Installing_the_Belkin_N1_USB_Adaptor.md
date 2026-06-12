---
title: "Help Installing the Belkin N1 USB Adaptor"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by MakingHeadway on 2008-08-04
Okay, before we begin let me just say that I'm almost entirely new to Linux. I say almost as I've dabbled here and there over the years, but never considered moving to a Linux OS permanently. After dealing with Vista's inherent issues, and refusing to go back to the dated and altogether lackluster XP user experience, I decided to make the switch.

So, I've just done an install of Kubuntu (latest release), hoping to try out KDE 4.1, which I seem to be hearing about quite a bit, and was interested in giving the OS a solid week of my time. Unfortunately I cannot for the life of me figure out how to install my network adapter (the Belkin N1 USB Adapter) and so far it's been my only hiccup (well, besides trying to figure out Grub).

I've done some searching and found articles on the ndiswrapper, but am totally lost and have no clue where to begin or which driver I should be trying to use.

This is the adapter in question: [http://www.technudgelive.com/reviews/?p=233](http://www.technudgelive.com/reviews/?p=233)

Any help, pointing me in the right direction, or maybe a simple set of instructions on how to get this installed would be greatly appreciated. Remember, as I said above, I'm a Linux newcomer, so please keep that in mind when replying. Thanks!

---

### Post by james_vanb on 2008-08-04
The basic process of installing wireless driver using ndiswrapper is as follows (The commands are for ubuntu and xubuntu - Replace with appropriate commands for kubuntu - i.e. gedit is the default editor for ubuntu, mousepad is default for kubuntu - Don't know what kubuntu uses):

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files (An .inf, .sys and maybe a .cat -if there are only 2 don't worry - copy whatever is in the folder). Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (My driver was the rt73 - replace as appropriate for your driver):

> sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

> sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (Replace text editor as appropriate - gedit for ubuntu and mousepad for xubuntu):

> sudo gedit /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

> sudo ndiswrapper -m

Reboot

The problem is that there may be some drivers included in the kernel that conflict.  If you reboot and still can't connect, You can either Google to see if any are listed or run:

> ndiswrapper -l

If the output lists and alternate, blacklist the alternate - reboot - and try again.  To blacklist:

> sudo gedit /etc/modprobe.d/blacklist

Add "blacklist (driver)" to end of list - In my case, blacklisted rt73usb as well as rt2500.

Sorry input is a little vague - difficult to be more specific without knowing what driver you are trying to install.  To ID driver, insert the wireless card install cd - navigate to drivers and specifically xp drivers and post the driver ending in .inf.

---

### Post by MakingHeadway on 2008-08-04
Half the problem here is I'm a fish out of water. I can't seem to find out where ndiswrapper is, or how to install it. The only guide I found was very out of date.

---

### Post by james_vanb on 2008-08-04
Keep in mind that I haven't used kubuntu and therefor don't know it's commands or application setup.  However, under System, you should find Synaptic Package Manager.  Open and search for ndiswrapper.  There are 2 applications that need to be installed.  One is ndiswrapper utils and I think the other is ndiswrapper common.  When you click one to install, it should tell you that the other needs to be installed as well.  Mark for install and click apply.  To open a terminal, go to Applications > Terminal.

kate (I think) is the default text editor in kubuntu - gedit (in ubuntu) - mousepad (in xubuntu).  Otherwise, commands should be pretty much the same.  Google commands for kubuntu to figure out any differences in what I have provided above.  To determine text editor available, look through Applications to see what is listed.

Let us know progress.

---

### Post by MakingHeadway on 2008-08-09
Thanks for the help, James. The out-of-date gate I mentioned above wasn't as out-of-date as I thought, as the suggestion you made mirrors it, and the numerous other guides I've found since posting this. Problem is, using the search function, and looking manually, I'm still not finding ndiswrapper. 

I'm the kind of guy that doesn't like wasting peoples' time, and as I'm now assuming I'm simply doing something wrong, I'm going to find out what that is and try fixing the problem. I think part of my frustration here is the fact that the wireless adapter is the only thing holding me back from moving to Linux as my permanant platform, a move I want to make sooner rather than later. 

I will be back when I figure out what it is I'm doing wrong here.

---

### Post by james_vanb on 2008-08-09
Sorry you're still having problems.  Comes with the territory and learning curve.  Took me 3 weeks to get wireless going my first attempt.  Stick with it, you'll find it's worth it.

This may be a statement of the obvious - But, have you enabled extra repositories under Software Sources?  I don't think ndiswrapper comes on the install cd.  If you have a wired connection, enable extra repositories and see if Synaptic updates and ndiswrapper becomes available.  Here is a guide that might help:

[http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

---

### Post by MakingHeadway on 2008-08-10
The unfortunate issue here is that it's very inconvenient for me to connect my PC's directly to the router. I may have to bite the bullet and move the PC in the bedroom, if that's what it's going to take. 

Again, James, thanks so much for the help. I will return after I've worked this out, hopefully posting from my Kubuntu machine. :)

---

### Post by james_vanb on 2008-08-10
Just came across an old thread that indicated that you can not install ndiswrapper in kubuntu without an internet connection.  Once you get your computer wired and confirm a connection, make sure that you have enabled all available sources (except cd) under "Software Sources" - My tab is labeled "Third Party Software".  Then in Terminal, execute following command:

```
sudo apt-get install ndiswrapper-utils-1.9
```

This should download and install it from the repository.  (At some point during the process you should be prompted that you also need ndiswrapper-common and asking if you want to install - indicate yes).

Good luck!

---

### Post by MakingHeadway on 2008-08-10
Awesome James, you've been a huge help. Now that I know for 100% certainty that there's a solution I'll be moving the PC in the room so I can cleanse myself of this Vista experience.

---

### Post by james_vanb on 2008-08-10
I neglected to include a link to the post in my last reply.

[http://kubuntuforums.net/forums/index.php?topic=3081934.0](http://kubuntuforums.net/forums/index.php?topic=3081934.0)

---

### Post by MakingHeadway on 2008-08-28
Thanks so much for your help James. I got everything working (to an extent, check my new thread for the sequel to my networking issues) and so far (barring the few problems) I'm much happier. Even my marriage has improved; my wife has stopped inviting her lovers over for chese and wine and we have pot-pie three days a week now, up from the usual two. They're just so tasty.

---

### Post by james_vanb on 2008-08-28
Good news - Enjoy the wireless and the pot-pie.

---

### Post by QwUo173Hy on 2010-09-06
> **james_vanb said:**
> The basic process of installing wireless driver using ndiswrapper is as follows ...
James VanB, you are one cool dude. After hours of fiddling around, your instructions got my card up and running in two minutes - thank you so very vey much.

Jarlath

---

### Post by james_vanb on 2010-09-07
Jarlath - Glad to hear your wireless is up and running.

---

