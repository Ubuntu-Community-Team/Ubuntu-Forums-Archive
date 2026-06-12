---
title: "Help needed sharing FROM Windows TO hardy [Nudge]"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by enstardavid on 2008-05-04
Hello,

I am really in a bind with this. I have upgraded our Ubuntu desktop box from GG to HH and I now can't access the file stores from our Windows network.

I am struggling to access a folder set to be shared in Hardy (8.04) from a Windows box.

I can easily see Windows shares FROM the Hardy box and access the files in them, but I cannot do it the other way.

When I search my Network Neighborhood from Windows I can see the Hardy box.
I have confirmed that the Samba service has started.

In Hardy I have created a desktop folder and set it to be shared, by right-clicking and selecting 'Sharing Options' - and set [x] Share this folder and [x] Allow other people.

I have gone to Firestarter and set Policy to allow Inbound Events from the LAN address (and I have also tried turning Firestarter off).

BUT - when I try to browse from the Windows box the connection is rejected.

AND - if I try to Map a Network Drive from the Windows box I get asked for a Username and Password. If I respond with the Admin Username and Password for the Ubuntu box the password dialog refreshes with the Network Share name, and a request for the password again - and then I am stuck in a loop, and can't progress.

[IMG]http://neatcomponents.com/sites/5722/69/text/83/files/ubuntu.gif[/IMG]

Very frustrating.

I have scanned through lots of How-to's in the wikis - but it seems that there has been quite a change in this area with Hardy as none of the dialogs seem to match up for Sharing.

Can one actually do this? Or is it not ready yet or broken? It simply can't be this hard - I must be missing something really simple.

I'll now even poke at Samba from a terminal window if someone will hold my hand.

TIA

D

---

### Post by questant on 2008-05-04
See the comment: 	
[ubuntu] Can no longer connect to network server after Hardy upgrade (Multi-page thread 1 2 3 ... Last Page)
Talegater posted must after yours.  The solution is on page 4

---

### Post by questant on 2008-05-04
See the comment: 	
 Can no longer connect to network server after Hardy upgrade (Multi-page thread 1 2 3 ... Last Page)
Talegater posted uust after your post.  The solution is on page 4.  To go from win to lin you must have a user name and password set with sudo smbpasswd -a username.  If the user name exists on lin just type sudo smbpasswd.

---

### Post by enstardavid on 2008-05-04
Thanks - I'll try this in the morning

---

### Post by enstardavid on 2008-05-08
Hi,

Turns out this was only half the answer.

You also have to do this:

[http://ubuntuforums.org/showpost.php?p=4904711&postcount=4]("http://ubuntuforums.org/showpost.php?p=4904711&postcount=4")

Peasy - when you know !

Good luck.

D

---

