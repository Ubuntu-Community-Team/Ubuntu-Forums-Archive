---
title: "Yet another noobuntu wireless question"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by P4r4digm on 2008-07-31
Alright so I rarely ever post questions on te internet because cahnces are someone else has asked the same question first...well I've been scouring this damned internet all day and can never seem to find the question or answer I need.

I am running Ubuntu 8.04 LTS Desktop Edition on a Dell Latitude D600.  This lappy has had 0 hardware changes since coming out of the box.  I'm not sure what sort of network gadgets it has although I believe it is Truemobile or something to that effect.

Alot of people have the issue of getting drivers to work and allow ubuntu to connect to devices.  My issue is that Ubuntu can't find the damned wireless card.  When connected via a LAN cable, the internet connects fine and when I right-click the network icon, it only allows me to "Enable Networking" and doesn't give me the choice of "Enable Wireless" that everyone says must be checked.

Furthermore when I go to system->admin->network, it only has options for wired connection and point-to-point connection...There's no wireless there.  Also I tried doing ndiswrapper but trying to install the windows drivers with wine caused an error saying that the hardware is not present.

Now I know for a fact the hardware is present because i was able to connect to wireless netowrks jsut fine when i had windows xp on this machine.  So I went to the bios....the wirless was disabled...wtf....so I enabled it and made sure everything was turned on....then went back through all this above **** again and it still doesn't work.

I'm at a complete loss...what must I do to make the ubuntu system recognize my wireless?

---

### Post by tashmooclam on 2008-07-31
I don't know which wireless card it came with, but I had a Dell that came with a Broadcom card. I decided to replace the wireless card with an Intel one for $25 and my wireless problems magically disappeared.Intel Linux drivers are in Ubuntu already. There are other answers, but that is how I solved the problem. 

Someone will probably be able to come up with a less drastic solution shortly.

---

### Post by P4r4digm on 2008-07-31
that's starting to sound like a pretty good idea at this point....soo frustrating

---

### Post by tashmooclam on 2008-07-31
I just realized that I had the same laptop and the "truemobile" card=Broadcom. On this laptop, swapping the card is very easy. The access is a little door on the bottom of the laptop. What is *nice* about this laptop is it will be able to run Compiz and have some fun desktop effects. Check eBay for the Intel card for this laptop, I paid $25, maybe there are cheaper ones out there. My friend begged me to sell him this laptop, so I had to put XP back on, and it caught a virus in a week :)

---

### Post by P4r4digm on 2008-07-31
So I'm guessing an intel card would do the trick? found an ebay listing for an intel centrino wireless card for the d600....$30 i might just go for it if it'll work....this lappy cost me a whopping $50 anyway =P

---

### Post by tashmooclam on 2008-07-31
Is this what you have? 
[http://www.laptopbroker.com/reviews/Dell-Latitude-D600-Laptop-Notebook-Review/](http://www.laptopbroker.com/reviews/Dell-Latitude-D600-Laptop-Notebook-Review/)

You can go to the Dell website and see a nice bunch of instructions also for changing the wireless card. It was about the same as adding RAM, except you must attach the antennae leads to the card.

After installing the new Intel card, remember to *turn it on* using that key combination on the laptop. Just do that once of course. 

Have fun with it. Ubuntu runs well on this laptop. 

7.1 had a bug for startup using that screen resolution. Lucky if you haven't had that problem using 8.04

---

### Post by tashmooclam on 2008-07-31
An Intel card will do the trick, because Intel supports Linux.The Intel wireless card drivers are real linux drivers and they are on your Ubuntu CD already.
Are there any more $50 laptops like that around? I want one! :lolflag:

---

### Post by P4r4digm on 2008-07-31
heh I think they shouldve payed ME $50 for this piece o' ****....the seller originally sent me an ac adaptor that wasn't made for the system which sent me on a several-month wild goose chase inspecting the motherboard and drivers trying to figure out qwhy the battery wouldn't charge...and now, after looking up that new wirless card on ebay...i decided to crack open the wireless slot and take a look.....this thing was freaking gutted! lol....the card in there is some unlabeled thing that doesn't even fit the antennae lengths...not even the same card that came with the system.....so much pain and anguish

anyways i went ahead and nabbed that new card...should work like a charm and now my lappy will be a centrino lappy! =D

EDIT: Wow I was totally right....the wireless card I've been toting around is none other than the infamously crappy Inprocomm IPN2120...a card not among the standard options for the d600...how funny...
I guess this says it all:
[http://www.leenooks.com/page/show/Linksys%20WMP11%20(rev.%204)%20(InProcomm%20IPN2120](http://www.leenooks.com/page/show/Linksys%20WMP11%20(rev.%204)%20(InProcomm%20IPN2120))

That was definately the issue here....thanks alot tash for the advice tog et a new card...otherwise i never would have thought to open her up....

---

### Post by tashmooclam on 2008-07-31
You'll have a nice laptop for $75 after it is all over. If you have the higher screen resolution you are really stylin. Slap some Ubuntu stickers on it and download some Frostwire while slurping coffee somewhere. Your entire computer costs less than a copy of XP or Vista, or Office! :)

---

