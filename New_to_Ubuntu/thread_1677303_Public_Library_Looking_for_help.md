---
title: "Public Library Looking for help"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by milfordlibrary on 2011-01-28
I'm the director of a small public library and we want to switch out public access computers from Windows XP to a linux distro.

For that to happen we need to have a way for our patrons to log into the computer without a password and have their activities purged once they log off.

Guest session works great but I'll never be able to get my patrons to fish around in a drop down menu for it.

Any suggestions?

~George

---

### Post by milfordlibrary on 2011-01-28
How about this.

Is there anyway to make a shortcut to the Guest Session on the Desktop?

Then i could put it right in the middle of the screen and maybe people could figure it out.

~George

---

### Post by SoFl W on 2011-01-28
I don't know if [this user]("http://ubuntuforums.org/member.php?u=298494") can help you, he is a Librarian, and Ubuntu user.   I believe you can set Ubuntu to auto login but I am not sure about auto deleting sessions.  I would check privacy modes.

---

### Post by MrWestwood on 2011-01-28
What about a flash live disc with a pre prepared distro? You could set the PCs to boot from USB and maybe make the users return the stick when finished. Do they know how to switch the machines on and shut down?. That way the user always gets a new session.

---

### Post by Paqman on 2011-01-28
Doesn't KDE have a "kiosk mode" designed for this sort of thing?

---

### Post by SoFl W on 2011-01-28
> **Paqman said:**
> Doesn't KDE have a "kiosk mode" designed for this sort of thing?


Wow, interesting.  **[KDE kiosk Mode]("http://developer.kde.org/documentation/tutorials/kiosk/index.html")**  I learn something new all the time here on the forums.  
There is also a [Gnome kiosk type mode]("http://live.gnome.org/Pessulus").

---

### Post by bodhi.zazen on 2011-01-28
I highly advise you use Fedora, take a look at the xguest package.

Users log into the "guest" account without a password, can browse change the BG image, whatever.

When they log out their changes do not persist (ie similar to "kiosk" mode that has been mentioned).

Best of all, IMO, the account is confined by selinux so although they have physical access they really can not pose a security problem.

[http://danwalsh.livejournal.com/14778.html?thread=98490](http://danwalsh.livejournal.com/14778.html?thread=98490)

[http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_10_selinux_user_guide/fedora_10_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html](http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_10_selinux_user_guide/fedora_10_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html)

Both those links are old, going back to Fedora 8, so as you can imagine xguest is quite mature.

---

### Post by milfordlibrary on 2011-02-08
Thanks alot everyone.  I looked at KDE kiosk mode but I like Gnome a lot better than KDE.  I'll take a look at the Gnome Kiosk and Fedora and let you know what I think.

~Geo

---

### Post by milfordlibrary on 2011-02-09
Well I downloaded and installed Fedora 14 and all in all it seems to work pretty well (after I fiddled around to get the wireless to work anyway) I downloaded xguest but when I try and initiate the session from the log in screen it says "cannot initiate session"

I checked the security mode and it's set to enforcing.  Any ideas otherwise?

---

### Post by milfordlibrary on 2011-02-24
Well after playing around with things for a while I'm not really any closer to getting this to work than I was.

I do however have lots of new questions.  :P

Foremost is this.

We have 4 identical computers. Would it be possible to use [Remastersys]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") to create a LiveUSB without the install option?

The idea is that I could set up one of the computers the way I want it, create the LiveUSBs and plug them into all the other computers for them to boot from.  Nothing that is done should persist once they log off and the system reboots (at least if i understand this all correctly).

Then once a week or so I login to the main computer, download all the updates and create a new image for the USBs.

That way the installation stays up to date and the patrons can do what ever they want without messing things up for those that come after them.

Does this make sense/Is this possible?

Can anyone think of a better way?

In the grand scheme of things one of the few things that would keep Libraries from using Ubuntu is the lack of a program similar to Steady State.  If we can find a way to get a similar effect without too much time requirement I know a lot of Librarians that would happily dump their aging copies of XP for Ubuntu.

~George

---

### Post by bodhi.zazen on 2011-02-24
> **milfordlibrary said:**
> Well after playing around with things for a while I'm not really any closer to getting this to work than I was.

Did you try Fedora with xguest as I suggested ? That solution should work "out of the box".

---

### Post by milfordlibrary on 2011-02-24
I did but after a week of playing with it the guest account still gives me a "unable to open session" message when ever i try to open the xguest account.  I've looked around a tried the various things that were supposed to fix this issue but so far no luck.

---

### Post by bodhi.zazen on 2011-02-24
> **milfordlibrary said:**
> I did but after a week of playing with it the guest account still gives me a "unable to open session" message when ever i try to open the xguest account.  I've looked around a tried the various things that were supposed to fix this issue but so far no luck.

IMO you really want some kind of kiosk mode (and not remastersys).

My guess is that it is a selinux problem.

See also: [http://www.linuxbsdos.com/2010/11/12/how-to-enable-auto-login-and-create-a-guest-user-account-on-fedora-14/](http://www.linuxbsdos.com/2010/11/12/how-to-enable-auto-login-and-create-a-guest-user-account-on-fedora-14/)

But I did not need to do that ^^ here.

Did you post on the Fedora Forums ? If not -> post 
If so, linky ?

As an alternate there are kiosk specific distros, google search for them.

If you want to build one from scratch, be prepared to do a lot of reading and, IMO, this will be less reliable and thus less secure.

You can start here:

[http://jadoba.net/kiosks/firefox/](http://jadoba.net/kiosks/firefox/)

---

### Post by deconstrained on 2011-02-24
The public library system in my county (Santa Cruz, CA) have **exactly** what you are speaking of - a bunch of inexpensive/old computers running a secure, stripped-down Linux that deletes user info when the guest/patron logs out.

I do not, however, think it was Ubuntu. It was something far more simple than Ubuntu. You might try contacting them and asking them who did it, and then getting in touch with that person;

[http://www.santacruzpl.org/](http://www.santacruzpl.org/)

---

### Post by bodhi.zazen on 2011-02-24
> **deconstrained said:**
> The public library system in my county (Santa Cruz, CA) have **exactly** what you are speaking of - a bunch of inexpensive/old computers running a secure, stripped-down Linux that deletes user info when the guest/patron logs out.

I do not, however, think it was Ubuntu. It was something far more simple than Ubuntu. You might try contacting them and asking them who did it, and then getting in touch with that person;

[http://www.santacruzpl.org/](http://www.santacruzpl.org/)

As I said, there are several kiosk distros.

One of many :

[http://webconverger.com/](http://webconverger.com/)

[http://webconverger.com/screenshots/](http://webconverger.com/screenshots/)

---

### Post by mastablasta on 2011-02-24
i saw a Ubuntu kiosk working nicely in an internet cafe in Bali.
so i guess it can work good as well.

also what do you not like about KDE (kubuntu) ? To make it look more like windows XP you need to **right click the K** and select **classic style** menu. it will look almost exactly as WinXP (or maybe more like Win7) and users shouldn't have any problem switching.

---

### Post by milfordlibrary on 2011-02-24
The classic view might help.  The primary thing I didn't like was that the KDE desktop was annoying.  The way things were laid out just didn't click with me.

Also when I tried to find the KDE Kiosk Admin Tool i couldn't.  I looked all over for it and eventually got fed up.

---

### Post by MrWES on 2011-02-24
> **milfordlibrary said:**
> I'm the director of a small public library and we want to switch out public access computers from Windows XP to a linux distro.

For that to happen we need to have a way for our patrons to log into the computer without a password and have their activities purged once they log off.

Guest session works great but I'll never be able to get my patrons to fish around in a drop down menu for it.

Any suggestions?

~George

Here's a link to the HOWTO: Ubuntu in the Pubic Library:

[http://ubuntuforums.org/showthread.php?p=4404000]("http://ubuntuforums.org/showthread.php?p=4404000")

---

### Post by grg3 on 2011-03-05
> Public Library Looking for help
I'm the director of a small public library and we want to switch out public access computers from Windows XP to a linux distro.

For that to happen we need to have a way for our patrons to log into the computer without a password and have their activities purged once they log off.

Guest session works great but I'll never be able to get my patrons to fish around in a drop down menu for it.

Any suggestions?

~George

For a couple of years, I have been maintaining a remix of Ubuntu for a few libraries in my area. The current build is based on Ubuntu 10.04 LTS, which will be supported by Ubuntu for two more years. I can give you instructions for how to do your own system or I can provide you with an installable dvd/usb image that was made with Remastersys.

The system comes with two accounts setup. The first is the admin which is used by staff to maintain the system. The second account is the patron account which is setup to wipe and restore at every logoff. In addition, the system is setup to automatically login to the patron account so it is always ready to go.

So far I only get complaints when the hardware breaks or the admins forget to change the password and someone guesses it.:D

---

### Post by Hakunka-Matata on 2011-03-05
@grg3:
Would you be willing to share your 'remix of Ubuntu' with me as well?  I've been getting more involved with my local library and would love to explore your 'distro' to see if it might be worthy of approval with my local library director?  The local PC-Club meets @ this library, it would be oh-so-nice to introduce them to LINUX[COLOR="DarkOrchid"] read "save them from MS-Winxxxx"[/COLOR] in this way.

---

### Post by Hakunka-Matata on 2011-03-05
@~George:  Milford, CT. is right up the road from me currently, I thought I might stop by and see how it's going but it appears you're in some other state than CT?  Since @ Milford, CT. Library web-site lists different person as director.

---

### Post by grg3 on 2011-03-06
> @grg3:
Would you be willing to share your 'remix of Ubuntu' with me as well?

You bet! Here it is: [http://linuxtracker.org/download.php?id=c1dccdc66ef745a7e1d63ea5c512bf53d2befece&f=Ubuntu-Public-Remix-311.torrent]("http://linuxtracker.org/download.php?id=c1dccdc66ef745a7e1d63ea5c512bf53d2befece&f=Ubuntu-Public-Remix-311.torrent")

Most of the principle behind this came from this site:[http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm]("http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm")

The administration was a little difficult for non-geek types, so I added some scripts to make things a little easier for admin. Fortunately, as long as the super user has a decent password, it works fairly well. It could always be hardened, but then the whole system can be rebuilt by running the live dvd and reinstalling.

Private message me with questions and suggestions. I am always looking for input.

Almost forgot, the password for super is changeme. I used to use super as password, but the libraries kept forgetting to change the password. Patron has no password and they need none. Public Fox password is still super.

rick

---

### Post by Hakunka-Matata on 2011-03-06
grg3, thank you, it's *torrenting* on the *interweb* now!

---

### Post by Bluenoser81 on 2011-03-06
Hello George, librarian-in-training here! Although I don't have the technical skills to give you an answer, you might be interested in checking out this setup for public libraries:

[https://www.library.ns.ca/content/linux-terminal-server-project-nsla-presentation](https://www.library.ns.ca/content/linux-terminal-server-project-nsla-presentation)

(there is a powerpoint at the bottom of the screen)

Craig

---

### Post by grg3 on 2011-03-08
The torrent is back up today, if anyone was trying to get it and couldn't. They have been having trouble with the tracker.

If you download the iso please help seed. If you are having trouble seeding see this:[http://linuxtracker.org/smf/index.php?topic=2.0]("http://linuxtracker.org/smf/index.php?topic=2.0")

---

### Post by Hakunka-Matata on 2011-03-08
> **grg3 said:**
> You bet! Here it is: [http://linuxtracker.org/download.php?id=c1dccdc66ef745a7e1d63ea5c512bf53d2befece&f=Ubuntu-Public-Remix-311.torrent]("http://linuxtracker.org/download.php?id=c1dccdc66ef745a7e1d63ea5c512bf53d2befece&f=Ubuntu-Public-Remix-311.torrent")

Most of the principle behind this came from this site:[http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm]("http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm")

The administration was a little difficult for non-geek types, so I added some scripts to make things a little easier for admin. Fortunately, as long as the super user has a decent password, it works fairly well. It could always be hardened, but then the whole system can be rebuilt by running the live dvd and reinstalling.



Private message me with questions and suggestions. I am always looking for input.

rick

Torrent downloaded, and ISO too.  I'd be happy to seed for this ISO but don't understand how to accomplish that.  Is there a new "torrent" file I can download to SEED with?  At your pleasure,

---

### Post by bodhi.zazen on 2011-03-08
> **Hakunka-Matata said:**
> Torrent downloaded, and ISO too.  I'd be happy to seed for this ISO but don't understand how to accomplish that.  Is there a new "torrent" file I can download to SEED with?  At your pleasure,

Your torrent client should automatically act as a seed. Just leave it running.

---

### Post by grg3 on 2011-03-08
> **Hakunka-Matata said:**
> Torrent downloaded, and ISO too.  I'd be happy to seed for this ISO but don't understand how to accomplish that.  Is there a new "torrent" file I can download to SEED with?  At your pleasure,

Normally, just leave Transmission running and it will seed. If that is the case then no problem. Linux tracker has been having issues with seeding and I had to use the workaround mentioned above.

There was one other person trying to download the iso, but it looks like they may have given up. I will keep it going for a while, just in case someone is interested.

Did you try it yet?

---

### Post by Hakunka-Matata on 2011-03-08
> **grg3 said:**
> You bet! Here it is: [http://linuxtracker.org/download.php?id=c1dccdc66ef745a7e1d63ea5c512bf53d2befece&f=Ubuntu-Public-Remix-311.torrent]("http://linuxtracker.org/download.php?id=c1dccdc66ef745a7e1d63ea5c512bf53d2befece&f=Ubuntu-Public-Remix-311.torrent")

Most of the principle behind this came from this site:[http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm]("http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm")

The administration was a little difficult for non-geek types, so I added some scripts to make things a little easier for admin. Fortunately, as long as the super user has a decent password, it works fairly well. It could always be hardened, but then the whole system can be rebuilt by running the live dvd and reinstalling.

Private message me with questions and suggestions. I am always looking for input.

rick

The original torrent file has a bad id, it does not work any longer.  check out post#25.

---

### Post by grg3 on 2011-03-08
> **Hakunka-Matata said:**
> The original torrent file has a bad id, it does not work any longer.  check out post#25.

The fix is to go to Properties, Tracker tab, Edit Tracker and replace tracker with:> [http://linuxtracker.org:00000000000000000000000000000000/announce](http://linuxtracker.org:00000000000000000000000000000000/announce)

That's 32 zeros! It seems to work.

---

### Post by Hakunka-Matata on 2011-03-08
did that, no workie, see Thumbnail please.  It doesn't present any problem for me other than not being able to SEED to others:  If you're going to have Karma, might as well attempt to make it good Karma, eh?

---

### Post by grg3 on 2011-03-08
My tracker announce does not have the 2710 in there and it seems to work. No biggie, I'll keep it up for a while.:D

---

### Post by anand warik on 2011-03-08
Sorry, but i thought instead of starting a new thread why not get clarifications here itself. 

What is a Guest session? 
What is a kiosk and can i install it from the repository?

> **SoFl W said:**
>  [Gnome kiosk type mode]("http://live.gnome.org/Pessulus").

The site of the GNOME kiosk provided doesn't show any download page.

---

### Post by Hakunka-Matata on 2011-03-08
edited the [2700] out and all's well now.  Thanks

---

### Post by grg3 on 2011-03-08
> **anand warik said:**
> Sorry, but i thought instead of starting a new thread why not get clarifications here itself. 

What is a Guest session? 
What is a kiosk and can i install it from the repository?



The site of the GNOME kiosk provided doesn't show any download page.

To my knowledge there is not a kiosk mode for KDE or Gnome at the moment. The KDE Kiosk system worked on 3.5 and that is feature that has not yet been implemented in KDE4. Occasionally, I have seen reference here and there to development but, it is not yet out there (that I have seen).

There was never a Gnome Kiosk system quite like the old KDE Kiosk that I have ever seen unless you count commercial ones like Linutop.

Pessulus is one lockdown tool that can help in the building of a kiosk system. I used it in the one I built (see above torrent). 

I relied heavily on this site [http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm]("http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm")

The object for a kiosk is either to boot to a single full screen app or to boot to a locked down user session that automatically cleans itself on user logout. My build is the second.

In my opinion, this is an underdeveloped area in Linux. Libraries and other institutions need easy to use stable public access stations that do not cost and arm and a leg to purchase, run and maintain.

---

### Post by bodhi.zazen on 2011-03-08
> **grg3 said:**
> Libraries and other institutions need easy to use stable public access stations that do not cost and arm and a leg to purchase, run and maintain.

Options :

1. Fedora - see xguest account.

2. Possibly Edubuntu with a netboot.

---

### Post by sandyd on 2011-03-08
nvm.

---

### Post by bodhi.zazen on 2011-03-08
There are several kiosk specific distros.

[http://webconverger.com/](http://webconverger.com/)

Zenwalk made one as well.

---

### Post by grg3 on 2011-03-08
> **bodhi.zazen said:**
> There are several kiosk specific distros.

[http://webconverger.com/](http://webconverger.com/)

Zenwalk made one as well.

I have tried Webconverger and it works well for just a browser, but you must purchase any customization. Linutop works well but it is not free either. I have attempted to fill a niche with a free alternative.

A few hardy souls have setup kiosk systems with LTSP and this is a good solution for utilizing low end hardware as terminals, but standalone machines generally work better for internet apps and do not have a single point of failure.

I had hopes for the Fedora Kiosk Spin, but so far they have not released. For now, I will stick to doing Ubuntu LTS stations. I have been doing it for two years now and it seems to work for me!

---

### Post by cptr13 on 2011-03-09
I haven't read this whole thread, maybe this will help.

[http://www.dnalounge.com/backstage/src/kiosk/](http://www.dnalounge.com/backstage/src/kiosk/)

---

### Post by Hakunka-Matata on 2011-03-09
> **cptr13 said:**
> i haven't read this whole thread, maybe this will help.

[http://www.dnalounge.com/backstage/src/kiosk/](http://www.dnalounge.com/backstage/src/kiosk/)

+1

---

### Post by tvleavitt on 2012-08-17
> **deconstrained said:**
> The public library system in my county (Santa Cruz, CA) have **exactly** what you are speaking of - a bunch of inexpensive/old computers running a secure, stripped-down Linux that deletes user info when the guest/patron logs out.

I do not, however, think it was Ubuntu. It was something far more simple than Ubuntu. You might try contacting them and asking them who did it, and then getting in touch with that person;

[http://www.santacruzpl.org/](http://www.santacruzpl.org/)

The Santa Cruz Public Library uses LTSP, deployed off Debian, and with end user accounts locked down. This is less than perfect, for various reasons, but better than leaving client machines unconstrained.

---

### Post by lisati on 2012-08-17
Old thread closed

---

