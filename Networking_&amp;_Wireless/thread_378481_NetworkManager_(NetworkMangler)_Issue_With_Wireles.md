---
title: "NetworkManager (NetworkMangler) Issue With Wireless"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by dlbolton on 2007-03-07
First the details:
My computer is a Compaq Presario 5200; the wireless card is a Netgear wg311v2.  So far I have been unable to get this card to work with NetworkManager.  I have tried the suggestions in the Network manager guide in the community section.  I also have a wired ethernet card in my computer although I do not have it connected to anything.

So what this means is that I have one internet connection through a wireless card that is not managed by NetworkManager.  Firefox runs fine.  I have found that this works pretty well; however, sometimes I lose my connection and then I have to remove and reload the module for the wireless card.

Two applications that seem to have a prolem are Banshee and KMail.  They appear to look at NetworkManager when they start and of course NetworkManager responds "there are no working connections available ..." 

KMail refuses to get mail from my pop server. But rather than telling me that there are no connections available, it reports "Transfer Complete".  As in immediately, before it even asks for my password!

Banshee acts more weird than KMail.  I can download podcasts using the manually configured wireless card, but if I put an audio cd in the drive, it shows the cd as "Unknown".  If I rip (import) the cd, then the folder and filenames do not reflect the artist name, alblum name, track names.

Now for my experiment ..
Basically I killed the NetworkManager related processes.  I opened the System monitor and made a note of the process id's that were being used by NetworkManager.  For Gnome, I had to kill two processes.  For kde I only had to kill one.

Then I restarted these two applications.  I actually did this one at a time although I am sure I could have done them at the same time.  Both work fine now.

What have I learned here?  I am not really sure other than NetworkManager seems to confuse some apps if you have a manually configured card.  And of course I have found a workaround.

Am I the only one seeing this kind of problem?  So far I have not seen any messages on this forum about this issue with NetworkManager

---

