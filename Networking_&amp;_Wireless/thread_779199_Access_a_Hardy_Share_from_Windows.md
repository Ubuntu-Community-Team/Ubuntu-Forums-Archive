---
title: "Access a Hardy Share from Windows"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by enstardavid on 2008-05-02
Hi,

I am struggling to access a folder set to be shared in Hardy (8.04) from a Windows box.

I can easily see Windows shares FROM the Hardy box and access the files in them, but I cannot do it the other way.

When I search my Network Neighborhood from Windows I can see the Hardy box.
I have confirmed that the Samba service has started.

In Hardy I have created a desktop folder and set it to be shared, by right-clicking and selecting 'Sharing Options' - and set [x] Share this folder and [x] Allow other people.

I have gone to Firestarter and set Policy to allow Inbound Events from the LAN address (and I have also tried turning Firestarter off).

BUT - when I try to browse from the Windows box the connection is rejected.

AND - if I try to Map a Network Drive from the Windows box I get asked for a Username and Password. If I respond with the Admin Username and Password for the Ubuntu box the password dialog refreshes with the Network Share name, and a request for the password again - and then I am stuck in a loop, and can't progress.

Very frustrating.

I have scanned through lots of How-to's in the wiki - but it seems that there has been quite a change in this area with Hardy as none of the dialogs seem to match up for Sharing.

Can one actually do this? Or is it not ready yet or broken? It simply can't be this hard - I must be missing something really simple.

BTW - I really don't want to have to open a Terminal and start typing mumbo-jumbo: I think that equals broken.

TIA

D

---

