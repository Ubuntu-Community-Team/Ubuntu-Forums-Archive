---
title: "wifi lost after upgrade to 7.04"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by cenitram on 2007-04-21
I have been running 6.01 for a while and really like it. I upgraded my old Dell laptop and all whent very well. However, when I upgraded one of my old desktops with a Dlink DWL-520 wifi card it was another story. It will not even see the card and on that machine it is the only network device installed. Do I need to just go back to 6.10 or is there an answer to little problem?
This is bumming me out. 7.04 solved a number of internet video issues without having to hunt the web on my own.:(

---

### Post by jjschmidt6 on 2007-04-21
Sigh... I have same problem. Go back a couple of threads and see this post by
 jrlander .  Strange that this card worked fine with previous versions.:( 

Join Date: Apr 2007
Beans: 6
Re: Wireless card not detected
OK, I figured it out (well, it works anyway, but probably isn't the best solution). After a little investigation, I discovered my wireless card was a Realtek RTL8180L. Apparently the driver for this card has been blacklisted in Feisty. The blacklist file lists the following reason: "# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)".

I modified /etc/modprobe.d/blacklist and commented out the following line:

blacklist r818x

There is also a ESSID workaround that needs to be completed too.

I found the information on the following post:

[http://ubuntuforums.org/showthread.php?t=407853&page=2](http://ubuntuforums.org/showthread.php?t=407853&page=2)

I realize that it is probably not a good idea to use a blacklisted driver, but it is working now until I get around to upgrading.

---

### Post by cenitram on 2007-04-22
Thanks. I saw that and tried it but my card still doesn't show up in the manager. I got it to list but iwconfig kicks back lo no wireless extensions. I'm going to bed and worry about this in the morning. I appreciate your response. If I get it I will let everyone know what I did to repair the issue.

---

### Post by thebinz on 2007-04-22
try installing GTKwfi. 

I had the same problem until i installed that bad boy. 

Give it a shot...

[http://gtkwifi.sourceforge.net/]("http://gtkwifi.sourceforge.net/")

---

### Post by jjschmidt6 on 2007-04-22
I also encountered a strange problem with the SSID.
My ssid (essid) is schmidt6 and that showed up in some
of the network config GUIs. But iwconfig showed it
as "schmidt". 

The command 
sudo iwconfig wlan0 essid "schmidt6" 
left essid as "schmidt" but the command
sudo iwconfig wlan0 essid "schmidt6 "
(NOTE the extra space after the 6)
changed the essid to "schmidt6" and then
everything magically worked.  Of course , I
tried so many things that perhaps something else
did the trick but I did find a mention of the above in
one of the threads.  Hope you have better luck
in the morning!

---

### Post by mcleaver on 2007-04-22
I just tried Feisty on my Fujitsu Lifebook P series... and see no wireless APs. wlan0 is present and apparently active, but for some reason in Network Manager it is called a "wired connection". I tried adding a network and used the SSID as network name (?) but no luck.
Not sure how to get this prism set (that worked fine with 6.06 but not with 6.10) working.
Martin

---

### Post by cenitram on 2007-04-22
I'm thinking that Feisty is a little too feisty for me at this time. Not ready for wifi prime time. I have spent hours working on and reading what others have done all for not at this point. I am going to download 7.04 and put it on another drive so I can deal with it at my leisure but for now I'm feeling Edgy. After all my laptop upgrade has been perfect so far so I know a solution is at hand and I am entirely too cheap to buy a new wifi card to replace a perfectly good one.:) 
Thanks for the ideas.

---

### Post by AloneOverSeas on 2007-04-22
sudo gedit /etc/network/interfaces
and comment out everything except the lines that have (lo) interface.
i dont know that might help, it works for me.

---

