---
title: "dialup modem setup?"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by TCMGO on 2011-04-12
[COLOR=black][FONT=Verdana]I finally succeeded in installing Ubuntu for dual booting (Windows XP) and it works well, so far as I can tell. Now I hit my next major wall: setting up my dialup modem, as I have discovered that the process is far more complicated and confusing than I thought. I confess that I have been dumb-downed using Windows for all these years. I live in the boonies of Missouri where High Speed Internet is hit & miss, so I still use a turtle dial up provider via a **US Robotics, Courier v.everything v90 external modem. **Anybody have success in using one of these with Ubuntu? Recommendations for setup?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thank you[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Missouri Mule[/FONT][/COLOR]

---

### Post by Rex Bouwense on 2011-04-12
Check this thread [http://ubuntuforums.org/showthread.php?t=1634580&highlight=dial+modem+setup](http://ubuntuforums.org/showthread.php?t=1634580&highlight=dial+modem+setup)

Rex

Post # 3 is very detailed.

---

### Post by lkraemer on 2011-04-12
TCMGO,
That should help you.  Post if you run into trouble.

Look at [www.Copper.Net](www.Copper.Net) for your Dialup Provider.  Works good!


lk  - ShowMe State TOO!  Southeast MISERY!

---

### Post by wep940 on 2011-04-12
And yes, some of us have used that same exact modem.  You are lucky you have an external modem - no need to worry about finding drivers in Ubuntu.  It should be very simple to set up.  It's been a while since I did it, but it didn't take more than a couple of minutes to do the entire thing, and it worked great.
 
Good luck, and glad you went dual-boot with Ubuntu!

---

### Post by TCMGO on 2011-04-14
Wep940, thank you for the encouraging news.  What do you mean by not needing drivers . . . can you give me basic instructions on how to do it.  Thank you all for replying.

---

### Post by mastablasta on 2011-04-14
he means that drivers are part of Linux kernel (as it goes for many devices). You probably  need to get the PPP or what is it called (a dial up agent) as it's not there on the cd anymore. see the link 
Rex Bouwense  provided.

---

### Post by wep940 on 2011-04-14
When you have an external hardware based modem like this, there are no drivers needed.  instead it's a matter of setting up things to access the port it is on.  I'll go looking to see what it was I did a few years ago with that modem.

---

### Post by TCMGO on 2011-04-14
Thank you for looking into it for me.  I am having all kinds of fun trying to figure this one out.  Talk about getting the old brain stretched after the years of Windows atrophy!

---

### Post by TCMGO on 2011-04-15
From the good help of the forum and a little research I believe that my serial hardware modem (US Robotics courier 56K v.everything) does not require drivers, but the correct "PPP Dialer."  What is a PPP dialer and how do I go about setting it up?

---

### Post by wep940 on 2011-04-17
This came from this thread [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)
 
You may want to try this first as it doesn't require installing any additional software.
 
**For Ubuntu, without installing additional software, using NetworkAdmin**


[NetworkAdmin]("https://help.ubuntu.com/community/NetworkAdmin") that you can find in **System => Administration => Networking**, will let you set up the ppp connection in a graphical interface. You have to know your device name, ISP phone number, username and password to set it up. [LIST=1]
[*]Open Network Manager (System => Administration => Network) 
[*]Select the Connections tab. 
[*]Select Modem Connection 
[*]Choose Properties and fill out the fields. 
[*]Click OK 
[*]Select the DNS tab. 
[*]Click add, enter your DNS address. 
[*]Click Close. 
[/LIST]
You can also use the *Gnome Modem Monitor* and *Network Monitor panel* applets if you want to stop, start and monitor modem connections without opening the *Networking* GUI every time. Some people have had a problem with the modem dialing during bootup. This may be related to setting the modem as default route to the internet on the *Options* tab of *Interface properties*. **Note:** It has been reported, that connections started with this interface might be very slow, if they work. You can try it, but if this is the case for you, just try one of the other options.

---

### Post by Bartender on 2011-04-17
My old [thread]("http://ubuntuforums.org/showthread.php?t=1377619") specifically talks about USR modems. 

The thread is probably way too wordy, but take your time and you should be good to go.  

I don't understand why people are trying to push new users into monkeying around with Network Manager and etc.  If you're out in the boonies with a fresh install of Ubuntu and a modem, pppconfig is by far the most direct route to getting online.

I'm a little bummed out that they're going to shut down the archives...

---

### Post by wep940 on 2011-04-17
+1 on the not using network manager on the dialup - I guess I didn't read what I copied very well. I always took the cheap way out and just used PPP and did pon and poff.  I think all I used to set things up was the command line pppconfig.
 
About the archives - I'm half and half on it. There are getting to be a lot of outdated posts out there that don't provide the correct answers for todays Ubuntu. That another resource for people to search for ideas will be gone is perhaps not so good. I don't know what's going to happen to all the links in the search engines that point to the archive - are people going to think Ubuntu doesn't exist anymore, or is there just going to be a single page there with a link to the current forums?

---

### Post by Bartender on 2011-04-18
wep, thanks for writing.  

I thought maybe things had changed and people were using Network Manager again?  I considered it unlikely, but wasn't sure.  Appreciate your feedback.

---

