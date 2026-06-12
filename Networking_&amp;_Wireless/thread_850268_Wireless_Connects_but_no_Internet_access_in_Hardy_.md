---
title: "Wireless Connects but no Internet access in Hardy Heron 8.04"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by Hokani on 2008-07-05
Hello,

I have a Dell Inspiron 9400 with Intel wireless card that has been working great under Hardy since I installed it about a month ago.  I recently installed some updates and it still worked fine (yesterday).  But last night I was playing Battle for Wesnoth and after adding an add-on to it, I could no longer connect to the multiplayer server.  Ok so I openned up Firefox to try to see if there was a problem with the server.  No connection to my home page ([www.google.com](www.google.com)).  Checked the wireless connection and it shows connected with 77% signal in the network manager on the task pane at the top of the screen.  Disabled the connection and reconnected it, again, 70% signal now but still no internet.  Logged out of Ubuntu and went to my XP partition and wireless connects and internet works fine (how I am able to post here now).  What should I do or look at to see about fixing this?  I'm all for getting rid of Windows but I've never had these kinds of problems in the windows world either.  I would love to leave this side of my hard drive alone if only the internet worked.  Please help.  I'm new to Linux and Ubuntu, and can provide detailed posts of what I find if necessary to help resolve this issue.  I have no access to the wireless router either, I'm currently staying at a hotel, so its a free public wireless connection.  Thanks in advance.

---

### Post by Midwest-Linux on 2008-07-05
Updates are killing wireless for some users, maybe someone should put up a sticky warning people of this.

Several things, try to boot up to the previous kernel (in grub). 

Try to find the original script that you typed in the terminal window to enable wireless in the first place. The driver is still likely in the system yet and needs to be reconnected. So needing a internet connection to reinstall wireless may not be a requirement. 

I found a thread that might be helpful.

[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

---

### Post by superprash2003 on 2008-07-05
in the terminal type ping google.com and post output here.. also type ifconfig and post output here.

---

### Post by Hokani on 2008-07-05
Thanks, I will give those a shot.  I never typed in anything in the terminal to get wireless working it has worked since installing Hardy from the get go.  I will update to the iwl driver as that link you posted suggests if I can get internet back.  Again it is not that I cannont connect, it is that it gives me no internet access even though it shows connection in the network manager.  I'll post results here when I get them for the suggestions so far.  Thanks again.

---

### Post by Hokani on 2008-07-06
Strangely enough after not touching anything and coming back to ubuntu logging in to the 2.6.24-18 kernel then finding the internet working, then logging into the 2.6.24-19 kernel it was working again.  Not sure what happened, and before I logged into windows and had internet working, then back to ubuntu and it didn't work, then back to windows when I posted my original thread.  Strange... I guess its attributed to the crappy network here at the old Days Inn i'm staying at.  Thanks for all the help!

-Alik

---

