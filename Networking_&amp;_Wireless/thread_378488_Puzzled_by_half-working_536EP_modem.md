---
title: "Puzzled by half-working 536EP modem"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by Ethelbert2 on 2007-03-07
[SIZE="3"][FONT="Georgia"]I am puzzled by my modem.

I identified my modem as a Intel 536EP by seeing what drivers Win XP found for it in an alternative boot. It worked nicely in Win so I know the hardware is good. 

The Ubuntu wiki had good instructions on finding an Intel driver for Linux and installing it. I am using Xubuntu 6.10 on an old P3 450MHz with 192 RAM.  A wirelss link has finally got going and everything is updated.

Loading the driver seemed to go alright as per the instructions and the command line responses matched that on the read me instructions. But using Network Manager to configure and enable it got nowhere. 

I downloaded and tried gnome-ppp, and after filling in the details it just said said "could not make the modem work" and when I ran the test button "cannot find a modem"

A small clue was that the detailed instructions hinted that the modem ends up as /536ep0 in the dev folder rather than /modem  (I had entered /dev/modem for the port info.)

So I looked in the dev folder and there is a file 536ep0 but no "modem" file or folder

I tried putting dev/536ep0 in the gnomeppp configuration - no better.

Then I went to Network Manager and put in the same and ticked the enabling box etc box. (Plus putting in phone number info etc)

Nothing seemed to happen but when I went back to gnome ppp after this, it now responded when I clicked connect and the modem started making its noises.  Following the log I can see gnome ppp gets as far as "found a carrier". Then it waits a couple of seconds and says it has "lost the carrier", then it retries, fins the carrier and loses it again.

So I am not sure what is wrong here and why I seem to have a modem but various programmes tell me I don't have one.  

Two possibilities are that I have to set a country for the modem somewhere - don't know where or how - or that I have to set it to be "stupid mode" - again I am unsure how to do that or where.

Final information - the Network Manager still does not indicate anything about the modem to show it is configured even though I have filled in the boxed etc - is that true always for Network Manager?  My wirelss card is working but Network Manager does not seem to have any indicator to tell me that - I just know because Firefox comes up.

Incidentally when testing the modem I switch out the wireless. 

For the modem if I run the "test" button in gnomeppp it still says it cannot find a modem (which since it seems to be operating it, is weird). 

I also tried using wvdial but it gets as far as testing for a modem at various baud rates, says there is no modem and just stops.

Does anyone have a hint at what to do next? 
[/FONT][/SIZE]

---

