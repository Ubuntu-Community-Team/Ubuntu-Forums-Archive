---
title: "help me think through my home network"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by Ndyanabo on 2007-09-20
Please help a noob think through a networking situation. I just want to confirm that what I have in mind is possible. 

Here's what I want to do: in addition to share files and a printer between a windoze laptop and ubuntu desktop, I want to control a linux music box remotely on my main linux desktop.

This also involves internet. My internet connection is a wireless network provided by my apartment complex. The service assigns a dynamic IP. There are no ethernet jacks. 

I have three computers:
**main desktop**: connects to internet through a wireless card, and hosts my music files.
**music box**: barebones desktop, headless, connected to my stereo. I want to connect this to the internet by sharing the main desktop's connection. I want to connect to my home network via ethernet cable.
**Windoze laptop**. connects directly to net through a wireless card. Want to share files and printer with the main desktop wirelessly.

I also have a wireless router.

FIRST QUESTIONS: Can I share the main desktop's internet connection with the music box? Can I do this through an ethernet connection via  the router? (ie, wire both desktops to the router) How do I do this? Will the music box be assigned a static IP?

On to the music issue. The music files are on the main desktop, the music will actually be played on the music box.  I need to be able to run the music program (quod libet, amarok, or other graphical program) remotely from the main desktop.

SECOND QUESTION: I need to serve the music files from the main desktop to the music box. Will I use samba for that? Mount the drives via SSF?

THIRD QUESTION: How will I run the music program on the music box from the main desktop remotely? Can I do it with Samba? SSF will work, but is that the best way?

So, at this stage, I have two desktops on a wired ethernet network. Finally, I want to network the windows laptop.

FOURTH QUESTION: Given the above, any reason why it'd be complicated to share files and a printer over a wireless network between the laptop and the main desktop? I assume that the main desktop would do this networking through the wireless router, not its wireless card.

In summary:
My main desktop would connect to the internet through its wireless card, and connect by cable to the home network via the wireless router. 

The router would link wirelessly to the windows laptop, and wired to the music box and main desktop. 

The music box would have a wired connection through the router. It would use this to receive music files, share an internet connection, and run programs controlled by the main desktop. 

Any reason why that wouldn't work? Anything considerations? Headaches with dynamic IP addresses? How-tos to look at?

Will I create one home network, making all files available on it (stuff on laptop, stuff on desktop, and music) to the different computers, or will I make separate connections (laptop/main desktop and windows box/main desktop)?

Thanks!

---

### Post by wirelessmonkey on 2007-09-20
I'll answer you more thoroughly tomorrow, if someone doesn't get to it before I do.

One question on the details... The Windowz laptop will connect to the home network via wireless router, so you will not have access to the internet from this machine, unless you have your wireless router attached to your desktop as a gateway, which will require that you set up a network bridge on your desktop machine, bridging your wired and wireless connections, or setting up your desktop as a NAT machine.  

What you want to do is entirely possible, and probably not too hard. (Now that I've written that, I've almost certainly doomed you/us to days of hassle, sorry ;)) 

Dynamic IP's won't be an issue, as all of your internet traffic is going to end up going through your desktop machine, and we'll have to set up static IPs on your wireless router.

I'll draw this out and write an explanation tomorrow sometime. Feel free to PM me.

---

### Post by Ndyanabo on 2007-09-20
thanks!

So, what you're saying is that I can't use the windoze laptop's wireless to connect to both the home wireless network and the apartment's wireless internet network. Unless I go to a lot of trouble. 

In that case, could I do just connect the windoze desktop to the router with a cable when I want to share files and the printer? I don't have that many needs for sharing between the windoze laptop and the main desktop.

---

### Post by Ndyanabo on 2007-09-28
bump... this shouldn't be too hard a question, just a little conceptual advice. Could someone help me out?

---

