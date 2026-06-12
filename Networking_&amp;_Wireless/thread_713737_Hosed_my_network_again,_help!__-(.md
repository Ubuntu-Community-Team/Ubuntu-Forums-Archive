---
title: "Hosed my network again, help!  :-("
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by oldsmobile_mike on 2008-03-03
I should've known better than to mess with it.  It seems like every time I get it running well, something comes along and screws it up.  Well, here I was, smooth-sailing on a perfect network, the Linux machine could see the PC's, the PC's could see the Linux machine, they could all copy files into each other's shared directories, the world was at peace.

So, stupid me, thought that by following the instructions <a href="http://ubuntuforums.org/archive/index.php/t-298149.html">here</a> that I googled up, I could get Amarok to be able to play the 5,000 mp3's I have in a shared folder on one of the PC's.  Haha, yeah, right.  Instead what wound up happening was that I lost all network connectivity on the Linux machine, down to the point where I had to uninstall and reinstall WICD to get it to even connect to the network again.

Somehow, during this process, Samba also got totally screwed up.  Now the PC's can see the Linux machine, and copy files into it's shared directory, but the Linux machine won't see any of the PC's on the workgroup.  Interestingly enough, it usually sees itself when I click on the Network icon (smb://workgroup), but it won't see the PC's.  Whereas before, it would see everything on the PC's, even the administrative shares, haha (till I ran the patch to stop administrative share creation ;-)

So...  help?  It's 3:00am and I'm gosh-darn tired, and pretty frustrated!  How do I get my Linux machine to see the PC's?  I've even done a sudo apt-get remove and reinstall of samba, and there was no change.  Argh!!

---

### Post by oldsmobile_mike on 2008-03-03
Oh, dammit, this system is so unpredictable.  After messing with it for three hours, I left it alone for the amount of time it took me to post the above message, and now it's working again.  The PC's are showing up just fine when I click on the Network icon.  Argh!

Still wish I knew how to get Amarok to play all the songs on the PC though, any suggestions?  They play fine when I do that "hold the mouse pointer over the icons" thing, but when I try to play through Amarok it tells me "Error Loading Media - No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes."

Any suggestions?

---

