---
title: "JetDirect HP LJ4 issue"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by ManTracker on 2009-04-23
As the forum says "NEWBIE"

A quick description of the frustration.

The PC has a 2nd nic card and set to it's own IP. The LJ4 has a JetDirect card and set to it's own IP. Just so you know both IP's are xxx.xxx.2.1xx & same.2.2xx & not the same as the network IP.
Telnet works to the Jetdrect but does not give me a port# 
So, the system sees the printer but it wont talk to it to print. Something in the setup is not correct and I am not really sure what it is.


Samba & Swat is installed.

Thanks

Steve

---

### Post by Iowan on 2009-04-23
Mine is a LJ5M.  I remember installing HPLIP on a previous version.  Currently, I think it's via CUPS - using port 9100.

---

### Post by cariboo on 2009-04-23
WHy did you x out the ip address private network addresses are none routable so there is no harm in posting for instance 192.168.2.200 and 192.168.2.200

---

### Post by ManTracker on 2009-04-23
> **Iowan said:**
> Mine is a LJ5M.  I remember installing HPLIP on a previous version.  Currently, I think it's via CUPS - using port 9100.

I don't know what CUPS or HPLIP is.


> **cariboo907 said:**
> WHy did you x out the ip address private network addresses are none routable so there is no harm in posting for instance 192.168.2.200 and 192.168.2.200


I was told to never give the IP out.


I am a complete Newbie, I really don't know much about this stuff.

---

### Post by ManTracker on 2009-04-24
You know what makes this a pain is that someone like me is used to friendly people who enjoy helping others no matter what it is.
I have learned to master skills and able to translate the lingo or methods to others who know nothing about it.

So far I am not having a good experience with Linux. :(


[SIZE=3][B]The Fix:
 I found on my own was to use Footmatic to finish the install to make the LJ4 work.  Also, I needed a 568A Crossover cable.
[/B][/SIZE]
What a Pain it has been to try and find a solution!

When I said Newbie, I meant right off that boat dazed and confused & Bassakwards newbie. :lolflag:

I am really frustrated with trying to get that printer to work.

---

### Post by Mortus Pryde on 2009-04-24
Well ummm... Have to say I have never heard of a network printer hooked up that way before. I am still a newbie myself so I would not have been able to help, but I think I can understand why others were unable to help.

Question, what made you decide to connect your network printer like that instead of through a router?

---

### Post by ManTracker on 2009-04-24
Hi Mortus Pryde,

So maybe I did something kind of advanced? :confused:

The Print/file server is 2 feet from the printer and the router is 25' away.  I did not want to run a 2nd cat cable from the router to printer.

Besides I have all 4 ports filled and I did not want to buy a hub, I already have nic cards.
I new it could be done, I just did not know how to do it.

Ill tell you what though.  It prints without waiting.  Over the network it always took time to print and images were very long.  Now no time at all.  Much nicer.

Thank for asking.

I do hope this might help others. \\:D/

---

### Post by Mortus Pryde on 2009-04-24
Well direct connect like that used to be a nightmare, not sure about Windows XP+ or Linux. It certainly is and unusual and uncommon way to do it though.

Though have to say by comparison connecting my OfficeJet Pro K5400dn was breasy, just picked up a few steps later I was printing, though I connect through a switch for much the same reason and I have 2 towers and a printer to connect and having a spare line for my lappy is always nice. ;)

---

### Post by Mortus Pryde on 2009-04-24
Oh and I would not blame you for not wanting to move the printer closer to the router... HP4s are tanks!

---

### Post by ManTracker on 2009-04-24
I did not think doing it this way or rather a direct connection as you call it such an odd way. But, being the newbie oh well.

This LJ4 is a workhorse and almost indestructible.  However I do think it needs a bit of a rest.  Now and again it has a Hiccup 

Like now, all this moving around and jarring I think I upset it.  It's giving me Grey spots on the paper and dark enough to cover the fonts or image.  I have no idea what is causing it.  It looks like it's coming from a roller.

Yes, tank it is.  Luckily I am a big guy and it's not that heavy to me.

---

### Post by Iowan on 2009-04-24
> **ManTracker said:**
> You know what makes this a pain is that someone like me is used to friendly people who enjoy helping others no matter what it is.
I have learned to master skills and able to translate the lingo or methods to others who know nothing about it.

So far I am not having a good experience with Linux. :(

 Hope I'm not responsible for you not having a good experience with Linux :oops:
(I DO enjoy helping folks)
CUPS is [Common Unix Printing System]("http://en.wikipedia.org/wiki/Common_Unix_Printing_System").
HPLIP is [HP Linux Imaging and Printing]("http://hplipopensource.com/hplip-web/index.html").

---

### Post by ManTracker on 2009-04-24
HI,

No not you or the other guy.

I should edit that out I think.  I am just so frustrated with this and other things I cant get right with the machine.  Like, I create folders and share them but only some PCs have access and others don't.  Some cant see the files in the folder & even when I am user with admin privileges I still cant change the shares on folders.

Anyway,  All that is not for this topic.

thanks for asking.

---

