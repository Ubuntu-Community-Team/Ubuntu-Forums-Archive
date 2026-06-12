---
title: "does best buy sell wifi card that wks"
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by guest5 on 2006-08-31
Please excuse me for this question, but after several purchases, I cannot find a working wifi card for my desktop.  I have vmware installed, configured for NAT which works.  And now that I know I love this OS, and am ready to set aside ?icrosoft, I was hoping someone could just say hey, goto best buy and purchase ??? card.

Right now I have a 'Buffalo WL12-PCI-G545'.  Kubuntu doesnt see it.  I looked at the list of known working cards, but can't find any of those cards in my town anywhere.

---

### Post by x64Jimbo on 2006-08-31
You will have the best luck purchasing your card from the internet. I recommend searching ebay for Atheros chipset cards. They're quite powerful and are extremely well supported in Linux through the madwifi open source driver. And to top it all off, they're cheap compared to what you can find at b&m retailers.

---

### Post by guest5 on 2006-08-31
Thank you.  I will do it!!!

---

### Post by guest5 on 2006-08-31
I hate to be a crybaby here, but I am up to my eyeballs in webpages, and none of them have the simple statements that card 'x' is recommended.

Surely I am overlooking a simple list of Atheros chipset supported cards that are supported for Ubuntu's OS.

This can't be this hard.  My first assumption is that it is me, but after looking at all the postings on this subject I can take no comfort in the company I seem to be keeping re: this subject, which begs the question:

Am I really looking at a 'compilation of driver sources' 'to enable a wifi card (if possible)' before wifi is going to work under Ubuntu? (quotes from  Welcome to the Jungle (Redux))

---

### Post by alanmzifa on 2006-08-31
Guest5, I think we all seem to have been over-sold on Dapper's wireless capabilities and there's a dirth of answers out there.

Like you I'd love to just have an (up to date) list of what works with the current Ubuntu  version and what has to be done for each device to make it work.

I've suggested something [like this]("http://www.ubuntuforums.org/showthread.php?t=246403") via a thread or a sticky link to a properly updated wiki page).



[click here]("http://www.ubuntuforums.org/showthread.php?t=246403")

---

### Post by guest5 on 2006-08-31
I'd like to share my first thoughts on this.  Like any web site, there are no 'finished' web sites, only abandoned ones - similarly, my first thought on this issue was that the Ubuntu list is, after all, 2 months old, and way back then, I probably would have been able to walk into the store and find one on the list...

I just torrented O'reily Ubuntu hacks from torrentspy.com.  Although I am quite secure with my $icrosoft knowledge base - fully stealthed for years, I am new to Linux.  This ebook is very nice and I will first try to wrap this driver according to the book.  Looks straight forward enough.

I just thought someone might say something like, I use this card and it worked great, maybe someone will.  I don't want to wait too long, or drive across town too many times.  I want to dive right into this, have had it on my mind for a year or more, guess I was waiting for Ubuntu - although I didn't know it at the time, lol.

Hope that made some sense.  Thanks to everyone for being here.  I will look at those links.

---

### Post by srt4play on 2006-08-31
[http://shopper.cnet.com/4014-3380_9-20797458.html](http://shopper.cnet.com/4014-3380_9-20797458.html)

I used that card and it worked great. 

Ubuntu sees it with no effort and uses the driver "rt2500".

HTH

---

### Post by mabhatter on 2006-08-31
> **guest5 said:**
> Please excuse me for this question, but after several purchases, I cannot find a working wifi card for my desktop.  I have vmware installed, configured for NAT which works.  And now that I know I love this OS, and am ready to set aside ?icrosoft, I was hoping someone could just say hey, goto best buy and purchase ??? card.

Right now I have a 'Buffalo WL12-PCI-G545'.  Kubuntu doesnt see it.  I looked at the list of known working cards, but can't find any of those cards in my town anywhere.

Yes!  I've been waiting all week to post this, so here it goes.

Like you, I'm sick of f***ing around with wireless and was dying to find something that "just worked".  I ran to dinner the other day after work bonuses (yea!) and researched BB's website and the Linux compatible website listed on the wiki page. I only found 3 that looked compatible with all "greens" There were two netgear ones listed WG511T and WPN511 Both were labled on the box as Atheos chipsets.. score 1 point.  Anyway, I picked the more expensive one the WPN511 (the labeling looked more promising?).  It worked out of the box with the live CD of Kubuntu and Ubuntu 6.06 with the only setup being SSID and WEP key.  I was so happy I didn't bother looking at iwlist till just now and it says I'm getting almost the full 54 Mb.  

Seriously, I'm on this card right now.  The Only downside was that to get it working on my Dell Latitude C610, I had to reinstall Ubuntu but that could have been because I had an upgraded setup from breezy beta thru Dapper... but with the Live CD recognizing it, it was a sure bet to work with a install.  

Normally I don't hype products, particularly Best Buy, but in this case they happened to be the only retail with anything from the "green" list.. and it happened to be in stock.

---

### Post by guest5 on 2006-09-01
Many thanks for the input and experiences.  I live on a small island, so Idon't have too many choices, and it is a drag getting off and back on the key, but just so happens I gotta do it today anyways to troubleshoot someones problems, so I will package this Buffalo card up and make the stop.

Again, many thanks for many reasons.

---

### Post by pomfrey_ml on 2006-09-01
?????

---

### Post by guest5 on 2006-09-01
Of the 3 cards profered, BB only had the Linksys, so I grabbed it, and the card was recognized on the 2nd reboot, but the connection fails.  I then disabled the encryption on the router (linksys) and reset it to the default channel - but to no avail.

I have an error message upon boot, but do not know if this is related.  The message is:

'The process for the media protocol died unexpectedly.'

I am starting to get exicted.  I must be very close now.  Any clues?

---

### Post by NetworkGuy on 2006-09-01
Guest5,

Exactly what model Linksys card do you have.

I have a WPC54g v2 and a with a quick command, this card is able to connect to my router.

---

### Post by guest5 on 2006-09-02
I am IN, after trying with the live cd w/o success, I just rebooted and was able to connect.  I didn't really do any configuration adjustments, so I don't have any advice for anyone on this beyond the fact that this card did find the driver and connect:

model no. wmp54g

                                          
Thanks to everyone for their input.  I'll be back, and perhaps one day even I will be able to assist someone rather than asking for direction.

Now I can get some sleep, lol.

g5

slight sigh, so I need to secure the router, but lose the connection - had to go in through $icro$oft to remove the 128 bit wep, so it isn't the hardware.

Am very familiar with network settings and so forth.  Everything looks good.  Could it be that something didn't get installed when it couldn't connect during install?

Again, much appriciation for everyone being, and being here.
g5

---

### Post by msarullo on 2006-12-21
Get this card.  Only $20 and worked out of the box on Edgy:

[http://www.newegg.com/Product/Product.asp?Item=N82E16833147017](http://www.newegg.com/Product/Product.asp?Item=N82E16833147017)

:KS

---

