---
title: "WPA driving me crazy"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by Rollotamasi on 2007-01-20
I have just about come to my wits end.  I finally managed to get my broadcom wireless set up so that now my light comes on but I can't get WPA set up to save my life.  I have read close to  guides and tried what they said but have yet to find a solution.  I downloaded a network manager suggested in one of the guides and I also downloaded wifi radar.  My system sees the network but when I click the tab for WPA it looks like its asking me for the location of a diver.  I am pretty much 100 percent new to linux and am getting frustrated so anyone help anyone can give me would be very much appericated.  Is there a log file or anything I can post that would help?

Thanks

---

### Post by jck3j on 2007-01-20
I'd stick with using the NetworkManager Applet 0.6.3. I have a Dell Latitude d820 ipw3945 with WPA encryption at home, and it worked really well. Just click to connect and when it prompts you, type in your WPA encryption code. I believe i disabled all of my network adapters under  System => Networking => Connections, but when I reconfigured, I had to enable them. So I'm not too sure about that, but the NetworkManager Applet definitely worked for me.

---

### Post by Rollotamasi on 2007-01-20
Can you explain how to download that please?

---

### Post by Rollotamasi on 2007-01-21
Can anyone tell me how to get the desktop applet 0.6.3?

---

### Post by spd106 on 2007-01-21
He's talking about the network manager applet in the notification area. It comes with the network-manager-gnome package.

Have you read through this wiki page [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)?

It might also be useful to try this page as well [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo).

---

### Post by Rollotamasi on 2007-01-21
I have followed the intructions in those wiki's but I think maybe im not explaining my self correctly.  I am using wireless assisant but it doesnt offer an option for WPA, just wep.  Does setting up wireless assistant to use WPA require a different set of steps?  Because having to edit a file and so fourth every time I want to connect to a new WPA network is pretty cumbersome for a linux newbie like myself.

---

### Post by Rollotamasi on 2007-01-21
I also think that part of the problem may be that I've tried so many things that I might have one thing conflicting with another.

---

### Post by frick on 2007-01-21
Greetings,
This is my first post on Ubuntu. I am Ubuntu newbe, but I started computing in the CPM days so command line computing is not huge fright.

I have an older DELL Latitude, Pentium 3, 512 of ram, and 20 gig hard drive. It started life with Windows 2000. A perfect machine to play with Ubuntu.

I purchased a Orinoco Gold WIFI (pcmi card) as it was on the "works out of the Box list.  With the install of 6.10. It did in fact work out of the box (as I had already disabled the WEP on the Dlink 524 router.

As soon as I applied WEP. The net work vanished.  The Network control window just never worked with WEP.  I have read a significant amount of the posts on this issue and tried several of the command land solutions... that resulted in my reinstalling Ubuntu...  The end result was that I did this three times.  A great many of the posts have been about driver problems, which is NOT an issue with the Orinoco Wifi Card.  I am having WEP issues.

I did download wifi radar, and this has been the only program that has allowed me to recover from my wep and wpa tries.  Right now I am on and open WIFI connect.

It is a good thing I am having fun learning about Ubuntu and a pile of new commands. If I had to rely on this intall for work I would buy and new windows laptop and get back to work. 

 My Ubuntu 6.10 WIFI experience is a very frustration process, and a significant path of learning  about Linux.  

Also there really seems to be a great many varied solutions, but non are very newbe friendly, and all are command line solutions, that may or may not work.  I know that one of my reinstalls occured because I made a command line mistake.

Still having fun and as Capt. Taggert said " Never give, never surender."

Frick

---

### Post by frick on 2007-01-21
This is post number two...

While watching the Colts wins a trip to the superbowl...

I uninstalled wifi-radar.
rebooted
Installed Networkmanager aplet
rebooted
it refused to work because it could connect to the internet.

hummmm

repeted...
rebooted

same problem... it refused to work.
removed networkmanager again..
rebooted
installed
wifi-radar
rebooted
connected right away

I still have not WIFI

I am now convinced that the Network Monitor that was installed with Edgy 6.10 just does not work with wifi.

I still can not run WEP... whihc was my main reason for for attempting to use Network manager as many others said that it was the one of use if you wanted WEP.

The only good thing tonight was that the game made playing around with Ubuntu worthwhile.

---

