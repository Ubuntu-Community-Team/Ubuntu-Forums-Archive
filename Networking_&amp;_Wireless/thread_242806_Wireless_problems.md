---
title: "Wireless problems"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by agentsmith270288 on 2006-08-24
Hello, I am completely new to Linux. I booted form a Live CD and tried to connect to the internet using my Mac's Airport wireless card but I was unsuccessful. I am using Netgear WGR614v6. thank you

---

### Post by ironyCurtain on 2006-08-24
It helps to give us something to work with.  What happens when you try to connect?  Is your wireless card detected properly? Post the output of iwconfig.

Does dmesg contain any error messages regarding your wireless card?

Are you using encryption? WEP or WPA?

---

### Post by agentsmith270288 on 2006-08-26
thank you for replying. When i said that i am new to linux, i literally meant it (never used it before, got live cd 2 days ago and now am intrigued). I would be more than happy to post the output of iwconfig if i knew how to launch it or dmesg for that matter. here is all the important info:
i used a live cd on my mac mini with an airport card. i used system>networking to enable eth1 connection, but no network appeared on the list. I then istalled an x86 version into my hp laptop with intel centrino. I followed the same process, however, this time my network name appeared in the drop down list. since my network has a numbers-only password(it is WPA-PSK), i got confused by what plain (ASCII) and hexadecimal meant and how each should be input. when i click on the monitor icon on the right side of the top bar, it says that i am connected to "lo" and displays the number of packets sent and received and yet i cannot connect. well i think i covered all of it. thank you for any help you can provide and if you can't please point me in the right direction. i'd hate to give up on what looks like an amazing system simply because i can't wirelessly connect it](*,)

---

### Post by ironyCurtain on 2006-08-28
Alright, sorry, I assume too much.  You should first open up a terminal window and then type those commands I mentioned and post the result here.  Do this by clicking on the Applications menu at the top of the screen, go to Accessories, and launch an app called 'Terminal'--this is the Gnome terminal emulator, and you'll probably find yourself using it fairly frequently in the future, as it is actually quite handy.

Hexadecimal is a base-16 numbering system, and is often used in WEP keys, although has many other applications (for example, HTML colorcodes are hexadecimal codes).
[http://en.wikipedia.org/wiki/Hexadecimal]("http://en.wikipedia.org/wiki/Hexadecimal")

As to the problem at hand, if you're using WPA then you are going to have to install WPA supplicant.  There are tutorials out there.  This one for Airport Express cards looks promising: [http://www.revis.co.uk/site/?q=node/25]("http://www.revis.co.uk/site/?q=node/25")

Of course I don't know what hardware you have in your Mac exactly, so it would be wise to post the output of the commands I mentioned just to be sure we're dealing with similar hardware as the computer in the tutorial (a PPC laptop).  Assuming your wireless card is detected it should be listed in the output.

While you're at it post the output of **lspci -v**

Give following that tutorial a shot and see if it works.  Check back if you have problems.  Hope this helped.  Good luck!

---

### Post by ironyCurtain on 2006-08-28
> **agentsmith270288 said:**
> 
i used a live cd on my mac mini with an airport card.

Upon further investigation that tutorial should work for your Airport Extreme card that is somehow crammed into your Mac Mini (By the way, how do you like it?).  Anyways, bear in mind that I am not certain you can do all of that on the livecd--plus you'd have to do it again every time you booted it up, and who wants to do that.  Perhaps you should consider actually installing to part of your hard drive.

If you just want to see if wireless works at all beforehand then disable the encryption on your wireless router and try connecting from the livecd.

Hmm... Another option that crossed my mind just now is installing a program through the synaptic installer called wifi-radar.  It supports WPA, as I recall, but you will also have to install the wpasupplicant package.

One great thing about Linux is that there are a lot of different ways of accomplishing something.

---

