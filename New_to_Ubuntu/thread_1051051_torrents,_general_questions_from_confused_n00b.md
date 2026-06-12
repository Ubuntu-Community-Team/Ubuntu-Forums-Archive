---
title: "torrents, general questions from confused n00b"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by beanco on 2009-01-26
hi all,

was having trouble wit ktorretn (see my thread from sunday, jan 27.) so started trying deluge.

in both clients i now have trouble getting the files i need.

in deluge, i currently have one torrent showing the status as:

0(15334)

there are others with less over all seeders but 0 current seeders.

is it actualy possible that this many seeders are not on line? i assume that is hat is happening in theory. ie. lots of folks are seeding these files, just not at the moment, and have not been seeding at all today or last night...sounmds strange to me.

and in deluge in the name colum, if the drop is green then it is down loading, right? and if it is blue, then I am seeding, right?

robi

---

### Post by taurus on 2009-01-26
Check your router if your computer connects to one.  Make sure you open a port, whichever deluge or ktorrent uses, for incoming signal.  Otherwise, you are not going to get any good downloading speed.

---

### Post by beanco on 2009-01-26
> **taurus said:**
> Check your router if your computer connects to one.  Make sure you open a port, whichever deluge or ktorrent uses, for incoming signal.  Otherwise, you are not going to get any good downloading speed.

well, i have several torrents going simulteneously and one or two are downloading, the rest are not.... the router has been in service a while aqnd worked fine.

no idea about the open port thing... how to figure thast out?

robi

---

### Post by cariboo on 2009-01-26
If you have Deluge running, click on the Preferences button, then click the Network Tab, next click the Test Active Port button. Firefox should open a page with your external ip address and a message saying Yay! :-)

Jim

---

### Post by beanco on 2009-01-26
> **cariboo907 said:**
> If you have Deluge running, click on the Preferences button, then click the Network Tab, next click the Test Active Port button. Firefox should open a page with your external ip address and a message saying Yay! :-)

Jim

well i may just try FF then.... I have epiphany as my default browser...

I tried the manual check and it came up with:

TCP port 5774 closed on 91.120.148.130


ok, so the port is closed... how do you open a port? 

Thanks 

Robi

---

### Post by stchman on 2009-01-26
> **beanco said:**
> hi all,

was having trouble wit ktorretn (see my thread from sunday, jan 27.) so started trying deluge.

in both clients i now have trouble getting the files i need.

in deluge, i currently have one torrent showing the status as:

0(15334)

there are others with less over all seeders but 0 current seeders.

is it actualy possible that this many seeders are not on line? i assume that is hat is happening in theory. ie. lots of folks are seeding these files, just not at the moment, and have not been seeding at all today or last night...sounmds strange to me.

and in deluge in the name colum, if the drop is green then it is down loading, right? and if it is blue, then I am seeding, right?

robi

IN order for your torrent client to function properly you will need to open up the proper ports in your router.

Your router assigns an IP to your PC, you need to tell the router to open up the torrent's port for that particular IP.

---

### Post by beanco on 2009-01-26
stchman,

ok, how do i open the ports?

and why  are they not open if they were working before...?

thanks

robi

---

### Post by stchman on 2009-01-26
> **beanco said:**
> stchman,

ok, how do i open the ports?

and why  are they not open if they were working before...?

thanks

robi

You need to go into your router's software.  Refer to your router's manual to open the proper ports.  What kind of router do you have?

The reason that the ports are not open is that the router's firewall has all ports either "stealthed" or "closed" to keep hackers from getting in.

---

### Post by xpod on 2009-01-26
[http://portforward.com/](http://portforward.com/)

That should help.

---

### Post by beanco on 2009-01-26
the router is a d link wireless router... i installed it a week ago and it worked fine until the weekend...

i will check out the links above and the manual.... but is it possible that the ports were open and then shut somehow?

robi

---

### Post by Tomatz on 2009-01-26
> **beanco said:**
> well, i have several torrents going simultaneous and one or two are downloading, the rest are not.... the router has been in service a while and worked fine.

no idea about the open port thing... how to figure that out?

robi

The other torrents are not going because they are queued. They will not start until the active torrents are finished...

:lolflag:

I have these days too ;)


You can change the number of "simultaneous downloads" in your torrent clients options.

---

### Post by beanco on 2009-01-26
> **xpod said:**
> [http://portforward.com/](http://portforward.com/)

That should help.

tried the first link but did not understand it... no time to concentrate on this now.... the second link is a video on burning cds and dvds,

robi

---

### Post by beanco on 2009-01-26
> **Tomatz said:**
> The other torrents are not going because they are queued. They will not start until the active torrents are finished...

:lolflag:

I have these days too ;)


You can change the number of "simultaneous downloads" the your torrent clients options.

so then why do  3 torretns go now?

how do i change the number of sim tors?

have to go look that up, i guess.

thanks.

robi

---

### Post by stchman on 2009-01-27
> **beanco said:**
> tried the first link but did not understand it... no time to concentrate on this now.... the second link is a video on burning cds and dvds,

robi

If you would have read deeper you would have found this page.

[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

Select your router and open the port for your torrent client as per the IP address of the machine you want to download torrents onto.

---

### Post by beanco on 2009-02-01
thanks for thar link..... i hope to have time today to get to the bottom of this...

btw, just how safe is port fowarding?

wouldn't i be opening up my router/compter to outsiders?

robi

---

### Post by beanco on 2009-02-13
found the manual and it is time to take care of this whole port problem but i really did not understand it..... Argh, I hate not understanding stuff!!!

robi

---

### Post by Big Luke on 2009-02-15
I hate to be the bearer of bad news but it may not have anything to do with your programs or connections but with the torrent, or site that you got it from.  

Sorry, but from what i understand, people can cushion the number of seeds, whether it is because they are just like that and need a helmet \\:D/ , or because they want to trick people into downloading the file/files either because they are from the SPA, BSA, DMCA or all those other nasty acronyms or because they want to infect your system.  The reason for this is either to give you a virus because they are like that and need a helmet \\:D/ or to get you to buy software to fix it...yada yada yada...you most likely know this.  The reason the SPA, BSA, DMCA, etc. wants to do this is to get a hold of your IP address and send your ISP a nasty email that will in turn make them send u a nasty email which may also include the disconnection of your internet in accordance with U.S. Federal Law. 
 
Anyway I DO have a point, first of all is, if its at all being used for piracy or anything of that sort, do not do it UNLESS you know what you are doing... a.k.a. using a proxy.  Second, check the file's location, if there are no comments on the validity of the torrent, do not download it!  A number of seeds like 15,334 seems a little unrealistic, it all depends on the file (do not respond with the file's info) and how popular/important it is.  But a torrent with 15,334 individual people connected to it WOULD NOT go unnoticed by an anti-piracy organization...so as i mentioned before, be smart.  

As a rule of thumb, if a torrent yields ANY unwanted/odd behavior, stop downloading/seeding it and get rid of it.  My advice for this particular situation is, search for the file/files on another website and try there and if the same problem arises then I am sorry, I have no clue.

Good luck, I hope this helped.

---

### Post by Xiong Chiamiov on 2009-02-15
> **Big Luke said:**
> But a torrent with 15,334 individual people connected to it WOULD NOT go unnoticed by an anti-piracy organization...
Depends on what it is.  All of my torrenting is Linux/BSD/Solaris distros and anime fansubs, so nobody bothers me.

---

### Post by Big Luke on 2009-02-15
> **Xiong Chiamiov said:**
> Depends on what it is.  All of my torrenting is Linux/BSD/Solaris distros and anime fansubs, so nobody bothers me.

Yes, but I have no clue (and don't need to know) what type of file/files beanco is trying to download.  In your particular case Xiong Chiamiov a anti-piracy organization would not bother you because you are not breaking or infringing any copyright laws as far as I know.  But if beanco is trying to get a hold of a movie, game, cd or any other stuff that is copyrighted, he may be "bothered" because that. technically is breaking/infringing on copyright laws.  So beanco, if the files you are trying to get are perfectly legal to be downloading...completely ignore everything I am saying :lolflag:

---

