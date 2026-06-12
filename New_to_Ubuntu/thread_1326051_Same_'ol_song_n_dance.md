---
title: "Same 'ol song n dance"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by solomon316 on 2009-11-14
Ok, I've seen this problem posted so many times and yet i still can't get it to work.  Problem is, I can figure things all over the place in windows.  But linux I am complete virgin.  Ignorant

Running ubuntu 8.04.1
Atheros ar5007eg

Tried the ndiswrapper, couldn't figure it out
Madwifi have it on desktop tried instal through terminal, it wouldn't find it....  you heard it all
Is there anyone who has a SIMPLE letter by letter CAVEMAN explanation to help me get it working?

Thank you

---

### Post by garvinrick4 on 2009-11-14
All I can say is load the ndiswrapper through the Ubuntu desktop means.

If you want to through Terminal.

"sudo apt-get install ndiswrapper"

Type that in Terminal without quotes hit enter.
That should help you with Windows wireless drivers. 


You can open terminal from Applications to Accessories to Terminal.

Will look like       your login name@ubuntu : ~$ sudo apt-get install ndiswrapper

next in Terminal      sudo apt-get update && sudo apt-get upgrade

---

### Post by solomon316 on 2009-11-14
I moved the ndiswrapper to the desktop.....terminal wouldn't find it with the commands given.....  I am so used to windows, how do you install ndiswrapper from the desktop?  is there some form of install file?  I am totally lost

---

### Post by pasti on 2009-11-14
This article may help you:-

[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

although you may need to upgrade ubuntu to at least 8.10

just copy & paste the code in the boxes into a terminal

---

### Post by solomon316 on 2009-11-14
Ok, i'm downloading this compat wireless thru windows and will put it on the linux desktop because i have no internet through linux....  we will see

---

### Post by solomon316 on 2009-11-14
Ok, can a reason that terminal won't find the files on at all be because they're in a folder on the desktop?  do they have to be out in the open on the desktop?

---

### Post by pootan on 2009-11-14
The easiest way is to put things in your Home folder as that's where the terminal defaults to. You can change directories in your terminal but I think you will find it easier this way.

---

### Post by pasti on 2009-11-14
Solomon316

my advice wont work I thought you had a wired connection to the internet with ubuntu 8.04, those commands will download from the internet, but you haven't got a connection with ubuntu, I take it your windows computer is different to your linux one, i.e you're not dual booting

---

### Post by Old *ix Geek on 2009-11-14
> **solomon316 said:**
> Running ubuntu 8.04.1Is there a compelling reason you're sticking with such an old version of Ubuntu?  In my experience, each new version gets better at detecting/configuring hardware, including wireless.  For me, that change happened when I switched from 7.04--where I had to go the ndiswrapper route to get my Broadcomm 4311 working--to 8.04--where wireless worked on its own immediately after installation.  For you, it might be going from 8.04 to 9.04 (or 9.10 if you're up for some potential problems--I'm sticking with 9.04 for the time being).

---

### Post by solomon316 on 2009-11-14
Lol, Geek, yea, I keep sticking with this version because it's the only one I have....  I'm deployed to afghanistan right now, internet sucks hog balls anyways, so downloading a new distro won't work.  Although, I did order a new unbuntu disk bout 2 months ago, waiting for it in a package from my wife now.  I'll reboot into unbuntu and move everything to the home folder, like I said, I am linux illiterate and I hate windows.  I use an imac at home.  Dual boot, winXP on primary partition Unbuntu on secondary, rebooting....

---

### Post by pasti on 2009-11-14
Try This

download the madwifi driver from your xp install, then transfer it to the ubuntu install,use a usb drive or a cd, right click it to install it, anyway get it here:-

[http://madwifi-project.org/wiki](http://madwifi-project.org/wiki)

you can check in this link, it does support your wireless chipset, just scroll down a bit:-

[http://madwifi-project.org/wiki/Compatibility/Atheros](http://madwifi-project.org/wiki/Compatibility/Atheros)

---

### Post by solomon316 on 2009-11-14
Thanks guys.  I've already got the madwifi.  I did not know about right clicking to install.  Is there a specific file in the folder to install or just right click on the folder.  If it's a file, i have no clue.  I have double left clicked on several hit install and nothing

---

### Post by Old *ix Geek on 2009-11-14
Oh, I see, solomon. Hopefully you can get it working, but if not the newer version should take care of it.

By the way, thank you for serving our country. Come home safely.

---

### Post by solomon316 on 2009-11-18
Ok guys, thank you for all your help.  I finally got my 9.04 disk in, installed beautifully.  Internet works great.  I just have a few questions.  A.) Will my built in webcam work in pidgin?  If so what options do i need to run?  If not, do I have have to download the actuall yahell, aim and msn messengers for linux?  I am also (like I said, absolutely new to linux and ubuntu) having trouble to get the evolution mail client set up.  What should the receiving email setting be?  I f anyone uses comcast.net for email, is it pop or imap?  the sendmail setting should be on sendmail or SMTP?  and anything i change in these setting, the OK tab never lights up, only stays on CANCEL.....  really hoping to get this taken care of tonight.  Again, thanks for all your advice guys....

---

### Post by Chris Edgell on 2009-11-18
Hi Solomon,

I just wanted to say that I have found it works better if you ask one question at a time (start a new thread for a new topic)...then you will get a quicker answer to the question that some ONE knows the answer to.
 
I could be wrong with this answer--I don't mean necessarily one question at a time, if the questions are related...although I do know it is considered better to open a new topic with a new thread. 

Yes, God be with you there and bring you home safely.

---

### Post by rustutzman on 2009-11-18
> **solomon316 said:**
> Ok guys, thank you for all your help.  I finally got my 9.04 disk in, installed beautifully.  Internet works great.  I just have a few questions.  A.) Will my built in webcam work in pidgin?  If so what options do i need to run?  If not, do I have have to download the actuall yahell, aim and msn messengers for linux?  I am also (like I said, absolutely new to linux and ubuntu) having trouble to get the evolution mail client set up.  What should the receiving email setting be?  I f anyone uses comcast.net for email, is it pop or imap?  the sendmail setting should be on sendmail or SMTP?  and anything i change in these setting, the OK tab never lights up, only stays on CANCEL.....  really hoping to get this taken care of tonight.  Again, thanks for all your advice guys....

Hi, and thank you for your service. To check your webcam try cheese from the synaptic package manager. It's a small download. For your Comcast use POP and SMTP. For server names try mail.comcast.net for both. HTH

Russ

edit: here's what I found for comcast.
Comcast POP3 SMTP Mail News Servers

	 


Below are the POP3 incoming and SMTP outgoing mail servers and the News server for Comcast, a popular Internet Service Provider.

POP3 SMTP Mail News Servers for Comcast Internet Service Provider

Comcast incoming mail server: mail.comcast.net
Comcast outgoing mail server: smtp.comcast.net

Comcast news server: newsgroups.comcast.net

---

