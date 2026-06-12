---
title: "running the Live CD"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by larrypg on 2011-04-14
Hello all,
I have a few questions about using the livecd.  When I boot to it and choose try without making any changes it then goes to a black screen with Xubuntu in the middle.  The cd is being used but nothing else happens.
If I then boot to the livecd and try without making any changes but hit the f6 key and choose nomodeset it then goes to a purple screen with Xubuntu with the dots underneath.  I did not give it more than a minute or so because I just wanted to make sure that by using the nomodeset it will not then turn it into an install instead of a try.  
I also would like to have a general idea of how long it will take with a low memory computer (256M) for the livecd to go to something other than that screen.  
Not sure if I asked what I mean but thanks for any responses.

---

### Post by sanderj on 2011-04-14
On my 4GB RAM Athlon 64 X2, the live-CD-boot can take 5-10 minutes.

So ... be patient.


You can also review "quiet splash" from the boot options (somewhere after the F6 command): you will then see the progress on your system.


BTW: running Ubuntu from a live-CD on a 256MB system won't be fun.

---

### Post by kn0w-b1nary on 2011-04-14
I would say look at youtube to take a peek, then install using the alternate install cd.

---

### Post by KegHead on 2011-04-14
Hi!

If possible add some ram..best to have at least 512 ram.

KegHead

---

### Post by K_45 on 2011-04-14
It can take a few minutes, at least unless you have a desktop speed burner. On my laptop it took 2 or 3 mins. Desktop slightly less. Upgrade the ram though, right now RAM is dirt cheap. What are your system specs?

---

### Post by larrypg on 2011-04-14
I tried it again but let it go a bit longer.  It got to the desktop fine.  By the way I have a 10 year old Dell Dimension 8200 with 256M RDRAM RIMM and they do not make the ram anymore.  I am hesitant on sending my money to somebody on Ebay or Craigslist and hope that it is the correct ram 
Not sure if I should start a new topic or not but ifconfig eth0 shows everything correct except for my ipaddress.  DNS servers etc are correct.  Because my ip is wrong I can not connect or ping anything.  I am guessing I need to search around for DHCP setup.

---

### Post by K_45 on 2011-04-14
Are you connected through an ADSL2 router or a separate modem?

---

### Post by larrypg on 2011-04-14
I connect through a modem ip is obtained from my isp's (I guess) dhcp server.

---

### Post by larrypg on 2011-04-15
Hello again,
I was playing with things a bit more and I am not sure if I am wasting my time or not.  I am running the live cd and I am not sure that changes can be made to my connection or not.  It seems that everything is correct in the network connection info.   
went to network connection..edit connection...wired...eth0.  It is checked.  MAC is correct...802.1 not selected...ip4 auto (dhcp) and ip6 ignore.  Without being able to write to the disc I am not sure I can make changes.

---

### Post by K_45 on 2011-04-15
If the internet is working, run ifconfig in a terminal (in the Accessories menu) and note down the pertinent information.

---

### Post by larrypg on 2011-04-15
Just a reminder that I am running from the LiveCD.  When I run ifconfig eth0 everything seems to be ok except my ip.  The ip of the dns servers are correct.  The gateway is correct.  The MAC of my ethernet card is correct etc.  I just can not connect to the internet or ping or anything.  As I am using the LiveCD I would have to write down everything onto a piece of paper and then type it in here because there is no cut and paste when you have to reboot back into XP.  
Thanks for any suggestions

---

### Post by K_45 on 2011-04-15
I'd contact your ISP, get all the required settings off them, then manually enter them.

---

### Post by Miljet on 2011-04-15
By the way, you can make any changes you want while running the Live CD -- even install programs. But all changes will be lost when you turn off the computer since all changes are saved to memory instead of hard drive.

---

