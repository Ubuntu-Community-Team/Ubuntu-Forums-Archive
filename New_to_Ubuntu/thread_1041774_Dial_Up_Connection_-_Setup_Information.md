---
title: "Dial Up Connection - Setup Information"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by crjackson on 2009-01-16
I have a friend that wants Ubuntu on his system but he only has dial-up. Assuming he gets a compatible modem, how do I go about setting this thig up.

What is the easist GUI package that will just let me plug in the data and press dial (or something like that).

Sorry for such a basic question, but I haven't used dial up in years, and never used it on Ubuntu.

I've heard of a package called gnome-ppp and it looks good from an old screen shot I saw, but is it the best package for me to setup, or is there something better these days?

Thanks...

---

### Post by lkraemer on 2009-01-17
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1036317](http://ubuntuforums.org/showthread.php?t=1036317)

lkraemer

---

### Post by ieee488 on 2009-01-17
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Not only does your friend need a Linux-compatible modem, I hope his ISP isn't AOL or PeoplePC or Netzero or one that only works with Windows.

I know that AT&T Worldnet is Linux-compatible.

---

### Post by mgranet on 2009-01-17
> **ieee488 said:**
> [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Not only does your friend need a Linux-compatible modem, I hope his ISP isn't AOL or PeoplePC or Netzero or one that only works with Windows.

I know that AT&T Worldnet is Linux-compatible.

This is simply not true. I used PeoplePC for nearly a year in Linux, and it worked fine. AOL (Which don't even exist as an ISP anymore) was the only problem, due to the proprietary nature of connecting to the AOL network.

My recommendation is to pick up an old Conexant based modem, and head over to [www.linuxant.com](www.linuxant.com) and pick up the proper debs for the proper release of Ubuntu. They offer trial versions of the driver, and the full version only runs $20USD. It's a tiny price to pay for the speed and ease of setup.

---

### Post by ieee488 on 2009-01-17
Instead of paying $20 for the drivers, my suggestion is to buy a used Linux-compatible PCI modem on eBay for cheap. No one wants them anymore. I've seen ones similar to mine on eBay starting at $0.99 (items 130281427279, 180321544806 are two current auctions).

I'll have to take mgranet's word that PeoplePC works. I don't see anything about how to dial in with Linux except that they have free install CDs. I couldn't figure out how to try their free 30 day trial without using their install CDs which don't support Linux.

I know that AT&T works. I know that Netzero doesn't work; I can dial in, but it hangs up immediately.

---

### Post by crjackson on 2009-02-08
Okay, thanks for the replies. I forgot to subscribe to this thread and thought no one was answering...  

He does have peoplePC but he also has dialup number that connects and doesn't require their software to be installed. That's how he operates now.

Regarding the modem. It's an external hardware modem connected to a serial port. i doubt it will be a problem.

What I'm looking for is specific packages with a GUI to make setup and config easy. He needs a one click dialer basically. My friend is very old and more than that will turn him off to linux. He is shipping me his PC to configure for him, and I have no dial up experience using Linux.

what would be the favored GUI choice for config/dialer?

---

### Post by niteshifter on 2009-02-08
Hi,

gnome-ppp. Quick and simple. Has auto setup / modem detection. Pretty much a can't-miss proposition, especially with external RS232 serial modems.

---

### Post by crjackson on 2009-02-08
> **niteshifter said:**
> Hi,

gnome-ppp. Quick and simple. Has auto setup / modem detection. Pretty much a can't-miss proposition, especially with external RS232 serial modems.

Great, that's what I was looking for. I kind of came across gnome-ppp but having never tried it, I didn't know if there was something better.

Thanks...

---

### Post by Temposs on 2009-02-08
If gnome-ppp doesn't work for you, then try the command-line version, pppconfig. That's what worked when I set up my Mom's computer. For some reason gnome-ppp didn't work.

---

### Post by lkraemer on 2009-02-09
You can also use wvdial to get it all working before you try
gnome-ppp.  I've had good luck with wvdial.  It just works.
The only drawback is leaving the Terminal window open, and
Minimized while the connection is in use.

To Configure wvdial:
sudo wvdialconf /etc/wvdial.conf


[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf)
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

lkraemer

---

### Post by crjackson on 2009-02-09
Thanks for the replies. I'll be working on it next month when he ships the tower.

---

### Post by Francis60 on 2009-03-26
did you get your dial-up working. I have GNOME pppo installed but it not working right-will nnot stay connected-it found the modem alright-not sure if i did something wrong in set- what dial-up manual configuration-n ot sure if i did all that right-any ideas in the right set-up
Thanks
Allan

---

### Post by crjackson on 2009-04-01
> **Francis60 said:**
> did you get your dial-up working. I have GNOME pppo installed but it not working right-will nnot stay connected-it found the modem alright-not sure if i did something wrong in set- what dial-up manual configuration-n ot sure if i did all that right-any ideas in the right set-up
Thanks
Allan

It won't happen for me until the release of Jaunty. I've built the new system but it's just on standby until the release.

---

### Post by lkraemer on 2009-04-01
Here is a link to an updated guide.

[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)

It will get you  going.

Oh, I almost forgot................
AOL isn't a problem either.

Here is a link to another post I made which will get it working.

[http://ubuntuforums.org/showthread.php?t=973363](http://ubuntuforums.org/showthread.php?t=973363)


lkraemer

---

### Post by crjackson on 2009-04-01
> **lkraemer said:**
> Here is a link to an updated guide.

[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)

It will get you  going.

Oh, I almost forgot................
AOL isn't a problem either.

Here is a link to another post I made which will get it working.

[http://ubuntuforums.org/showthread.php?t=973363](http://ubuntuforums.org/showthread.php?t=973363)


lkraemer

Thanks - I'll be looking at it in a few days when jaunty comes out.

---

### Post by crjackson on 2009-05-14
Okay - So I built and shipped the system and having problems with logging in to the isp.

I ditched the ugly WinModem and got an external USR Sportster (RS232).

I installed gnome-ppp. I couldn't test becouse I don't have a POTS live available.

The user reports that he puts in his user ID [username]@peoplepc.com and passowrd. The modem dials out, connects, trys to authenticate but never goes beyond that point. Then after about 30 seconds, it times out and disconnects.

Does the gnome-ppp require any special editing of a conf file, or is the settings configured by the gui all that's needed?

How do I get him online at this point?

p.s. The connection works fine on the same machine booted into windows **_(No special software is installed from peoplepc in windows). _**Configured only by the windows dialer using the same username/password as gnome-ppp.

---

### Post by crjackson on 2009-05-14
> **mgranet said:**
> This is simply not true. I used PeoplePC for nearly a year in Linux, and it worked fine.

Can you tell me how to get this working?

---

### Post by crjackson on 2009-05-15
Any input?

---

### Post by bacardiandwatermelon on 2009-05-15
When I had dialup working on my ubuntu laptop it was the biggest pain in the *** to setup. I always had authentication issues. Sometimes only gnomeppp would work and sometimes only wvdial would work. I would suggest using wvdial though as it turned out to be a bit more reliable for me. But saying that a kernel update in hardy broke my dialup and I could never get it going, I ended up setting the windows pc with internet sharing to keep me going, that was until I got broadband.

I think fiddling Stupid mode and carrier check in /etc/wvdial.conf what got is going. Sorry I can't be more help, It has been a while since I used it.

---

### Post by lkraemer on 2009-05-15
crjackson,
Please go read post #4 here:
[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)

You're pap-secrets and your chap-secrets file contents must be correct.

You most likely will find those incorrect.  Double check the files. 
I don't think the file format has changed, but I am not 100% sure.

Then I'd suggest trying wvdial first and then after wvdial is working
use Gnome-PPP.

lkraemer

---

### Post by crjackson on 2009-05-15
> **lkraemer said:**
> crjackson,
Please go read post #4 here:
[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)

You're pap-secrets and your chap-secrets file contents must be correct.

You most likely will find those incorrect.  Double check the files. 
I don't think the file format has changed, but I am not 100% sure.

Then I'd suggest trying wvdial first and then after wvdial is working
use Gnome-PPP.

lkraemer

Okay, I'll give it a shot over the weekend. Dialup seems somewhat hard to setup. I'm really surprised. I expected to be able to fill out the information in gnome-ppp and be off to the races.

---

### Post by ferebee on 2009-05-28
> 
Quote:
Originally Posted by lkraemer View Post
crjackson,
Please go read post #4 here:
[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)

You're pap-secrets and your chap-secrets file contents must be correct.

You most likely will find those incorrect. Double check the files.
I don't think the file format has changed, but I am not 100% sure.

Then I'd suggest trying wvdial first and then after wvdial is working
use Gnome-PPP.

lkraemer
Okay, I'll give it a shot over the weekend. Dialup seems somewhat hard to setup. I'm really surprised. I expected to be able to fill out the information in gnome-ppp and be off to the races.

Also, you might try wvdial and gnome-ppp using sudo. In Intrepid, that worked for me. If it works, for your friend's convenience, you could drag the gnome-ppp shortcut from the applications menu to the panel, then right click and edit Properties - under Command change gnome-ppp to gksudo gnome-ppp.

I'm not sure if this is more of a security risk or not. Anyone?

---

### Post by crjackson on 2009-05-28
It dials and connects just fine. It just won't authinticate the username / password.

---

### Post by Bartender on 2009-05-28
Here's my old dial-up thread.  I tried to write it so anyone could follow.
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

Setting up pppconfig is kind of weird at first because navigation is with space bar and up/down keys, etc.  But once I got pppconfig set up, it was the fastest to get online.  I open a terminal, type "pon" and my USR external starts dialing.  Typing in "plog" gives you a basic log of activities.  Typing "poff" in the terminal turns off the modem.

The pap-secrets and - dangit, what's that other one? anyway, you gotta set up papsecrets too but there are threads describing how to do it.  If you think you've got that set up correctly but pppconfig still complains, try rebooting the PC.

The configuration with pppconfig is very basic so it's easy to see if you have the right username/password plugged in.

I'm a bit mystified by reports that PeoplePC works in Linux, because the installer CD installs a truckload of their proprietary stuff.

I know Frys.com works, and they're cheap.  That's what I use for a Linux ISP.

---

### Post by crjackson on 2009-05-29
Thanks for the input. I've hit a speed bump on the issue right now because a lightning storm took out the new modem I just sent him. I've ordered a new one but it hasn't yet arrived.  It'll be next week before we can try again.

---

