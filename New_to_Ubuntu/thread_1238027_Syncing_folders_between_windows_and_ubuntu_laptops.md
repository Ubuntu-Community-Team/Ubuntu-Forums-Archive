---
title: "Syncing folders between windows and ubuntu laptops"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by grj23 on 2009-08-12
Hi All

I know there've been a few post along these lines before, but I was hoping to get some advice.  I've used windows quite a lot, am relatively new to Linux (assume nothing!), and extremely new to networking (ditto!).  In the past I've used foldershare (now windows live sync) to synchronise folders between different computers (it works extremely well, by the way for anyone doing windows and mac os synchronisation of folders).

I'll tell you where I've got to so far, but would really appreciate advice at quite a basic level.

As far as I've been able to figure out, rsync or unison is the way forward, probably for me unison, as I want to be able to work on either system and have the changes propagated in both directions.  I want to do this over the internet.  Now the issue becomes how to SSH between the machines.  The help with unison says I need a Host and User, as well as a SSH client and server.

Now I might have this totally wrong, but here's my plan.
1.  Install Hamachi on both machines, to create a LAN like environment (DONE).  As far as I can tell I should now be able to ping from one computer to the other when they are both on with the IP address.
2.  Somehow make the directory on one machine available to the other.  Ideally this is something that happens automatically when the machines are switched on.  The Hamachi login occurs automatically, so something like that perhaps.  Is this where SSH comes in?  Windows File Sharing?  Can I mount a remote windows directory on my Linux machine?
3.  Run unison.  I've got unison running between eg ubuntu machine and external HD.  It seem the later acts like a windows machine (NTFS or something like that) and so needs perms = 0 set in the configuration file (thanks Philip Guo [http://www.stanford.edu/~pgbovine/unison_guide.htm](http://www.stanford.edu/~pgbovine/unison_guide.htm)), among other things.

So the key trickiness for me is step 2.  Unless I need to be doing this a whole 'nother way!  This is what Unison help file says:
1) To synchronize using SSH, there must be an SSH client installed on
this machine and an SSH server installed on the remote machine.  You
must enter the host to connect to, a user name (if different from
your user name on this machine), and the directory on the remote machine
(relative to your home directory on that machine).

Okay, so forgive the stupid questions, but what SSH client and SSH server should I install.  What's the host name (is it the same as the Hamachi IP address?) and user name (Hamachi name?)?  By the way, I have cygwin on my windows machine, and am not opposed to using it at all, but if this is going to be used everytime I log on, won't that take up RAM and be a big performance hit?

I feel like I'm close - just a few pointers to give me a little more understanding than I have right now, would be hugely appreciated.  I'm sorry that my question feels vague - I just feel hampered by the lack of knowledge.  I guess that's what happens when you leap in with both feet and no training...:P

Thanks

G

PS  Relatively new install of Ubuntu on new laptop - incredibly impressive!  Thanks all!

---

### Post by mapes12 on 2009-08-12
I'm not sure what Hamachi is but this thread may help you out:

[http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

EDIT: > but what SSH client and SSH server should I install.My understanding is that SSH only works across Linux boxes.

---

### Post by grj23 on 2009-08-14
So, the problem with pyNeighbourhood and samba is that they work over a LAN (at least that's my understanding).  Neither of my computers is a server, and neither has a static IP address.  Thus, my thinking was, that they need hamachi to create a LAN like environment.

Of course hamachi isn't working at the moment anyway.  I can see on both machines that the other is logged on, but pinging results in a time out from the Windows side, and Destination Address Unreachable from the Ubuntu side.

Okay, can I just ask if there's anyone who's managed to do what I'm trying to do?  I'd have thought it would be quite a common request, but apparently not!

Best

G

---

### Post by Clorow on 2009-08-14
SSH will work on any Unix box. Install [here]("apt:ssh")

Though for simple file sync like Foldershare, I recommend Dropbox.

---

### Post by mapes12 on 2009-08-14
> Okay, can I just ask if there's anyone who's managed to do what I'm trying to do? I'd have thought it would be quite a common request, but apparently not!Yours is I common request, at least for me anyway. I am also trying to connect my Ubu machine to my XP machine. Here's my post and the progress made so far: [http://ubuntuforums.org/showthread.php?t=1238509](http://ubuntuforums.org/showthread.php?t=1238509)

I've worked out how to connect two Ubu machines using SSH. I can post my HowTo but only if you need it as it's off topic given that SSH will not work to connect to windoze. If I eventually get pyNeighborhood working satisfactorily I'll post back to let you know.

Best.

Mark

---

### Post by grj23 on 2009-08-17
Thanks for the help!  Drop box is indeed a neat program.  Thanks for the suggestion.  Only trouble is that the free version only allows 2GB.  I'm not too worried about having a copy on a server somewhere, which is the big advantage of dropbox, I suppose.

My plan is to synchronise my home folder with my "my documents" folder, over the internet, between two laptops, regardless of where they are connected!

I think Hamachi + SSH + Unison could do it, but (a) I'm tripping up at the first step, (b) I need to do some actual work! and (c) I'm not confident that I'm heading off in the right direction!  If someone could confirm that such an approach would work, or correct/tweak the approach, or give me a better approach altogether, I'd be very grateful.

I'm assuming that Unison will be able to run between a local folder and ssh://myhamachiIPaddress/myfoldersundermyhome.  But I'm not at all confident about this.  Or sure that it's necessary.

Thanks again

G

---

### Post by Adam65 on 2009-08-17
My system sits at home and I can log on and access it's files from any internet connection (with my laptop, or whatever, while on the road).

I used Ubuntu Server on the machine at home (static ip aswell) and Ubuntu desktop on my laptop.

---

### Post by mapes12 on 2009-08-17
Hi grj23

I finally figured out how to connect up my XP and Ubu boxes. I've posted my solution here: [http://ubuntuforums.org/showthread.php?t=1238509](http://ubuntuforums.org/showthread.php?t=1238509)

My machines are connected over a local network at home, not over the internet though. IP addresses's are assigned by DHCP not static. But the numbers never seem to change

:lolflag:

---

### Post by Beemt on 2009-08-20
I use SpiderOak for syncing my machines (windows and linux) it also creates a back up for the folders you have selected, it syncs files automatically and recognizes changes within the files. This solution works for me, it is easy, fast and free.
 
[https://spideroak.com/](https://spideroak.com/)

---

### Post by grj23 on 2009-08-20
Okay, spideroak looks very interesting!  Question.  Can I sync folders that are larger than 2GB?  I don't want need the online backup thing, but just want a synchronisation.  I'll check it out and write back...

G

---

### Post by mapes12 on 2009-08-20
> **grj23 said:**
> Okay, spideroak looks very interesting!  Question.  Can I sync folders that are larger than 2GB?  I don't want need the online backup thing, but just want a synchronisation.  I'll check it out and write back...

GI had alook at this but spideroak want $10 a month to upgrade above 2GB. Looks the same as Dropbox to me.

---

### Post by grj23 on 2009-08-20
yup.  I downloaded it.  It's much more integrated than dropbox, that is, it works with your existing file structure, while dropbox creates a separate folder for backup/syncing.

However, "please note, folders you are interested in synchronizing must first be backed up to your SpiderOak Network", meaning a 2GB limit for the free version.

G

---

### Post by scorp123 on 2009-08-20
SpiderOak is messy. In order to sync two folder you have to download it first again to one of the target computers (too stupid if it's already there), and then it will upload all again .... Stupid, stupid, stupid.

I use Dropbox. With Dropbox you can also place symlinks into the ~/Dropbox folder. And on the target system you can work with symlinks too. Syncing two computers is very easy that way.

But if you'd like to sync two computers directly (e.g. no on-line service in between), why not use **unison**? It exists for both Windows and Linux.

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

---

### Post by grj23 on 2009-08-20
If you read my first post, you'll see that unison is exactly what I'd love to do!!

Trouble is, that I want to do this over the internet with both laptops using a variety of internet connections (eg travelling to various places, LAN and wireless etc).  I just don't get how to do this.

So, I'm accepting that in the time I can afford to allocate to this, the above objective will not be possible (BTW with windows/Mac it *is* possible with Windows Live Sync (formerly Foldershare)).  :(

So perhaps a reasonable compromise is to do it when I'm at home with both laptops connected to the wireless router.  Is it possible to use unison then?  All the examples I've seen of unison working uses SSH to some server.  Anyway, I'm a bit lost in how to begin doing this!  Probably the best will be to use an external harddrive and do it the manual way.  Just means the frequency of sync will be severely reduced!! :)

---

### Post by scorp123 on 2009-08-21
> **grj23 said:**
>  Trouble is, that I want to do this over the internet with both laptops using a variety of internet connections (eg travelling to various places, LAN and wireless etc).  I just don't get how to do this. You should go for Dropbox then. Sync'ing happens automagically as soon as you are logged into the desktop. And it does not matter whether it's Linux, Windows or Mac ... it just works. So all you need is a working Internet connection and that's it. Works like a charm. 

And if you get 4-5 friends to sign up Dropbox will give you additional 250 MB for free for each friend who really installs the software. So my on-line storage right now is 3.25 GB instead of the standard 2 GB you get for free.

And the one complaint I very often hear about Dropbox is this "one folder only?! Seriously?" thing. It's a non-issue for me, because I work with symlinks. I don't drag stuff into my Dropbox folder. I symlink stuff into it. That's already enough. If you do that on all systems that participate you can easily share any folder that you'd like (just like in SpiderOak).

If you really insist rolling your own thing ... oh well. There is still iFolder from Novell. Apparently there's a new version out. Finally ... after the free versions had been abandoned for almost two years.

[http://www.ifolder.com](http://www.ifolder.com)
[http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/](http://www.x2b4.com/howto/how-to-install-ifolder-on-ubuntu-server/)

[https://bugs.launchpad.net/ubuntu/+bug/87122](https://bugs.launchpad.net/ubuntu/+bug/87122)

So "iFolder" is very similar like Dropbox or SpiderOak or you-name-it. With the exception that you'd be running the server part too.

Supposedly this stuff works pretty well on OpenSUSE. Duh. Both "iFolder" and SUSE are from Novell so that's kind of to be expected. But getting this stuff to work on Ubuntu might be quite an adventure ... your mileage may vary.

I myself tried out the guide above and I did get it to work (despite my inital complaints in the bug report above) but ultimately it's too much of a hassle and my wife doesn't want me to run a server here 24 x 7 x 365 ... so I settled with Dropbox which works tip top.

I hope this was helpful?

Regards

---

### Post by vgrisham on 2009-08-23
> **scorp123 said:**
> SpiderOak is messy. In order to sync two folder you have to download it first again to one of the target computers (too stupid if it's already there), and then it will upload all again .... Stupid, stupid, stupid.

I use Dropbox. With Dropbox you can also place symlinks into the ~/Dropbox folder. And on the target system you can work with symlinks too. Syncing two computers is very easy that way.

But if you'd like to sync two computers directly (e.g. no on-line service in between), why not use **unison**? It exists for both Windows and Linux.

[http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/%7Ebcpierce/unison/")

I totally agree. SpiderOak is just not ready for usage. The sync feature simply doesn't work. Worse, SpiderOak is triggering Synaptic errors whenever I update. Steer clear.

---

