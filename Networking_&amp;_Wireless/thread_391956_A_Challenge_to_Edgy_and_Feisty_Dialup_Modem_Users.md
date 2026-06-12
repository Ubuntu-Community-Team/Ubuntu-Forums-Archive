---
title: "A Challenge to Edgy and Feisty Dialup Modem Users"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by Michl on 2007-03-23
As dial-up modem users know, the dialup modem piece in System->Administration->Networking does not work in Edgy and it continues not to work in Feisty.  The tones setting keeps reverting to pulse and, most importantly, it does not enable or activate the modem.  Now in the bug report for this:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/94304](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/94304)

One of the ubuntu team folks sets the following reasonable challenge:

> Would be nice if one of those modem users could work on the bug then and
send a fix, most of the distribution team has no modem to work on that
and already lot to do

I wouldn't know quite where to start.  But maybe there's enough folks here with ideas and hints to fix this thing if we put the pieces together.  Would be great.

Michael

---

### Post by Michl on 2007-03-30
Why not just get rid of that feature?  Why leave it there if it doesn't
work and nobody in the ubuntu world is willing or able to fix it?
This seems bizarre to me.
Michl

---

### Post by Bartender on 2007-04-19
Michl -
IMO, dial-up users have been cut loose.  Dialup is perceived as a dead end, and the devs have apparently chosen to spend their valuable time on newer and better technologies. 
 
If I knew anything about "working on the bug" I would.

---

### Post by Michl on 2007-04-19
If that's the case, then the non-functional modem feature in admin/networking should be eliminated.  For what it is worth, there seems to be some movement in the bug report on this.

---

### Post by unisol on 2007-04-21
its not fair to the dialup users who have been using ubuntu for a while.not everybody can afford or are able to get broadband. the applet should be fixed for them.someone told me about this,  its worth a try:dial-up modem users must comment out the &#8216;auth&#8217; line in /etc/ppp/options and create an empty /etc/resolv.conf file. Once these two arcane measures are taken, dial-up modems work fine. This problem has been incorporated in every kubuntu since at least 5.04.

---

### Post by Bartender on 2007-04-22
Hi, unisol -
Ubuntu Breezy was my first experience with Linux.  Until recently considered myself an Ubuntu loyalist.  

But I'm adrift in the backwaters of dial-up, and not going to waste time with an OS that makes this unfortunate situation worse than it already is.  

Been experimenting with Mepis and PCLOS in a search for an OS that's friendlier to dial-up.  Both look promising.  Mepis 6.5 claims to incorporate drivers for some winmodems but haven't looked into that at all.

---

### Post by Michl on 2007-04-23
In fairness --- gnome-ppp works very well in both edgy and feisty.  It is
easy to set-up and so on.  The only thing you need to do is in most
cases add S19=0 to the init2 string so that it does not shut down
always when data transmission is inactive.  So ubuntu does support
dial-ups.   It's just that the flagship entry for dialups in admin/networking
is dysfunctional.

By the way, if you look at the most recent activity on the launchpad,
it now works in the latest Feisty, but with some limitations.  I haven't 
tried it yet because I haven't installed Feisty at home yet where I
use dial-up.  Here at work its a network to the internet.
Michl

---

### Post by unisol on 2007-04-23
hi bartender you could try this; dial-up modem users must comment out the ‘auth’ line in /etc/ppp/options and create an empty /etc/resolv.conf file. Once these two arcane measures are taken, dial-up modems work fine. This problem has been incorporated in every kubuntu since at least 5.04. 
--------------------------------------------------------------------------------
 try adding thid to  your wvdial.conf
carrier check = no
stupid mode = yes 
I then type wvdial and it dials and connects
However it sometimes drops suddenly

---

### Post by jitsu on 2007-04-27
I just upgraded to Ubuntu 6.10 from 6.06 

My modem, a serial port ext modem was working and now I can't configure it for 6.10 

Am I going to have to revert to 6.06 to connect to the internet with  my dial up modem?

I don't see anything in the linux books that I have that is any help.

If I can read it, I can do it. I am a Linux novice.


thanks

---

### Post by Michl on 2007-04-27
What you need to do is this.

wvdial is part of the distro.  Find the HowTo document for dialups.  If you
cannot find it, I can send you the link when I get home.  Therer are
a few additions to that document, like eliminating colons and adding
S19=0 to the init string,  but it is easy.  Don't worry.

Once you configure wvdial and connect to the internet, you can
download gnome-ppp.  You need to activate multi-verse sources
in software sources to get it.  Then download gnome-ppp and
set it up.  It is even easer. The you can add the gnome-ppp
applet to your panel and you are connected in no time.

Michael

---

### Post by Bartender on 2007-04-28
Michl -
Thanks for the help.  Us dial-up losers gotta stick together.

Dial-up is the horse-drawn carriage of the internet highway.  Pathetically slow but the technology's been around so long that the end user doesn't have to know much to make it work.  It's easy to set up the dialer in Windows 98, an obsolete OS that doesn't even support USB.  Now let's look at Feisty, Ubuntu's latest flagship OS.  It still has a broken GUI dialer.

Other than that, it's a very impressive OS.  All kinds of improvements since Dapper.   

A Linux newbie on dial-up installs any 'buntu distro to his PC and immediately finds him/herself trying to follow arcane directions (they're going to seem arcane to the newb anyway) just to get online.  

I understand the #1 hurdle (winmodems) but it's a sad state of affairs when a person has to jump thru hoops to get his hardware modem working.

---

### Post by jitsu on 2007-04-29
Michl:

I don't have any reference that I can find to wvdial.

I would appreciate the link for dialup users.


thanks, Charles

---

### Post by Michl on 2007-04-30
> **jitsu said:**
> Michl:

I don't have any reference that I can find to wvdial.

I would appreciate the link for dialup users.


thanks, Charles

Charles,
Here is the link

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f229b8b898575bbd996c4dac3de0772d430f2a02](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f229b8b898575bbd996c4dac3de0772d430f2a02)

Follow, alternative Way 1.  You will find out in the first step if your modem is recognized.  Don't
freak out right away as it searches under various parameters.

If your modem is not recognized, I urge you just to but another one.  I can make recommendations if you wish.

If your modem is recognized, edit the file per instructions, but remember to remove the semi-colon before the ISP, phone and passwords.  Also, you will probably need to add S19=0 to the init 2 string.  You will see the sting and it's no problem adding. 

Once you are on the internet, do synaptic.  Do the software sources, but include multiverse packages.  Then reload synaptic and find gnome-ppp.  Install it and it will show-up in Applications -> Internet.  From then on everything is easy.  Remember to include S19=0 in the Init 2 strings or you will be knocked-off every few minutes.

Holler if you need more help on this.

Michael

---

### Post by jitsu on 2007-05-03
Michl:
I would appreciate the link for modem users.



thanks, jitsu

---

### Post by jitsu on 2007-05-03
Michl:
I have a Trendnet TFM-560x, serial modem and it works perfectly on Ubuntu 6.06. On Ubuntu 6.10 it won't work at all. I believe it's a recognition problem.

I've been all over this forum and I think everyone is having dial up problems. 

I appreciate your help.

thanks, jitsu

---

### Post by Bartender on 2007-05-03
jitsu -
How easy is it for you to try a different distro?  Do you have a spare HDD and access to broadband?  I'm not trying to pull you away from 'buntu, but have found the KPPP dialer in MEPIS and PCLOS to be very straightforward and simple to understand.
I'd suggest installing a popular KDE-based distro, hooking up your modem, and trying out KPPP to see if it can work with your Trendnet external.  Inside KPPP, once you've told it where the modem is (probly ttys0) you go to the "modem" tab & ask it to query the modem.  It should say bring back a report with entries for all those AT strings and all that other "init" stuff that I don't understand...:)

EDIT:  Something else I forgot to mention.  Some ISP's, such as ISP.com, have pretty decent graphic instructions for configuring KPPP on their websites.

---

### Post by jitsu on 2007-05-04
Bartender & Michl:
I have two computers. The one I'm on now is a 4 year old HP Pavilion and it has an Agere or Lucent Winmodem. In the books I have it states that this moden can work, but it says to run the "Scan tool." I accessed the scan tool website and I couldn't get the item to work. There are numerous links and I didn't know the right one to get me going.

I built my other computer about a year ago and have a inexpensive modem in it. I tried Xandros and my Winmodem worked for me without any problems. But Xandros is not for me.

I live out in the country and broadband is not available and not all phone services are available either. I had all my utilities installed underground and it would be a problem to run another phone line if broadband became available.

I picked up Estalive on my Windows XP machine and am going to have to try to remove it. My antivirus company decided it was too much for them. I'm very cautious and feel the malware came in on a security update or, I don't have an answer. If I can get Ubuntu dialup working I will be happy. I have to have internet. If I have to buy another printer I will.

With dialup downloading is out of the question. I like Ubuntu if I can get it going.

thanks

---

### Post by Michl on 2007-05-04
Jitsu,
I now have tried Feisty, Edgy and Dapper on a machine where
I use only dial-up.  For various reasons, including money, I
do not use broadbadn.

Both Edgy and Dapper work with dial-up.  In both the best option
in my mind is wvdial and gnome-ppp.  Very easy to install.  With
just dial-up, you will first need to configure wvdial (see howto),
then download multiverse packages, and then install gnome-ppp.

Although admin -> network in dapper works, it does not work as
well as wvdial.  After this Feisty dial-up fiasco, I said to hell with it
and let's just install 6.06 to see how it works, and I have to say
it is much less buggy.  The screensaver works without having
to set the monitor on never in power management.  Certain
color scrolls that track downloading work with the i810 driver
which they did not in Edgy or Feisty, and the modem is very
stable without futzing with inti2 comands.  I would highly recommend
installing 6.06.  (By the way, on the ubuntu.com sight you have
to dig around to download 6.10.  The main download page
offers only 7.04 and 6.06.  Makes sense to steer people
to those two.)

As far as modems are concerend.  I know that the US
Robotics 6105b  (I am guessing on the number here) works
with linux and specifically with ubuntu.

M

---

### Post by jitsu on 2007-05-04
Michl:
I think I'll take your advice and stick with Ubuntu 6.06. It is working perfectly.

I have copied the information you sent in case I do decide to upgrade later.



thanks, Jitsu

---

### Post by jitsu on 2007-05-05
I appreciate all the help everyone has given me--

My ext. modem is a TRENDnet-560x. I bought this from NEWEGG after reading the user reviews. I went back to see the reviews again and they were all positive when using it with a Linux distro and there were no negative reviews about Linux.

In reading one of the reviews, which was under the "con" for the product, this man wrote--
"I plugged it in and turned it on and nothing happened . . . I realized that you have to plug in and reboot since it is an rs-232 connection. I am used to USB and forgot this. My computer was then able to see it."


I know I didn't reboot as I'm also used to USB. I'm going to try this next week and see if this fixes my problem.

Hopefully this works and I'm not suggesting anyone else try it as I don't know if it will work.

thanks,
Jitsu

---

### Post by jitsu on 2007-05-05
I just tried reinstalling Ubuntu 6.10 and the rebooting didn't work.

I like Ubuntu and I'm not going to quit.

I have another computer and I installed Xandros 4.0 Home Premium and my generic Winmodem worked with no problems. Also, my Canon Pixma 3000 worked with some problems. I didn't like Xandros and opted for Ubuntu.

I'll probably try some of the other options Michl suggested.

thanks, Jitsu

---

### Post by jitsu on 2007-05-06
I've tried the Alternative Way 1 and I'm having a problem--

when I enter the command and the terminal asks for an administrative password it won't let me enter it.


The cursor is flashing and I can't input anything.

What am I doing wrong?



thanks, jitsu

---

### Post by Michl on 2007-05-06
You don't see anything.  Just enter your password and enter.

---

### Post by jitsu on 2007-05-06
Michael:
My modem was detected and I downloaded gnome-ppp. 

That password problem threw me. I appreciate all your help.


thanks, Charles

---

### Post by Michl on 2007-05-08
> **jitsu said:**
> Michael:
My modem was detected and I downloaded gnome-ppp. 

That password problem threw me. I appreciate all your help.


thanks, Charles

I remember being thrown in the same way.  I thought
this is it, I am sick of ubuntu, etc. and slammed in the
password again and slammed enter just our of
sheer frustration, and then ...

Remember that you can put the little gnome
telephone applet on the pamel on top.  Mine
sits right next to the evolution applet and I
click right from the panel.   

Michael

---

### Post by maniac_X on 2007-05-12
> **Michl said:**
> As dial-up modem users know, the dialup modem piece in System->Administration->Networking does not work in Edgy and it continues not to work in Feisty.  The tones setting keeps reverting to pulse and, most importantly, it does not enable or activate the modem.  Now in the bug report for this:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/94304](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/94304)


With Dapper, my external serial modem worked without problem. As noted above, I am experiencing those symtoms in Fiesty. I have been somewhat able to get around the problem partially.

I went into System>Administration>Network and setup the properties of my modem including checking the little activate checkbox  and then saved the configuration to a "Location" giving it the name of my ISP. I also set my Modem Monitor to the panel.

Upon restart/coldboot, while Ubuntu is loading, my modem will auto-dial out and connect just fine and hold the connection without problem. If I lose the connection during the session, then the problem above resurfaces and I have to reboot to get an working outgoing connection again.

I'm not a developer but seeing as this problem started **after Dapper**, they should look at what changes were made since then and revert if they can.

I have both the Actiontec 56k v92 external EX560LKA serial modem and Actiontec 56k v92 external EX560LKU serial/usb modem(only using the serial portion) both of which worked flawlessly in Dapper.

**EDIT**: Have since installed Gnome-ppp....much less hassle this way.

---

### Post by Michl on 2007-05-16
I disable the automatic start at boot because I prefer to
connect via gnome-ppp.  I can configure the inti string,
I can find out at what speed I am connected and so on.
The barebones fix in admin-networking is pretty useless
for dialup.

---

### Post by mainalisuyog on 2007-05-16
People in the third world countries, like myself, are never going to use ubuntu as long as it doesn't support dial up networking with winmodems out of the box. I've convinced many of my friends to install ubuntu, and a day or two later, they all come to me asking me to reinstall pirated windows on their machines. Why? because ubuntu does not let them connect to the internet! And there is no other way to connect to the internet. No broadband, even if u can afford it. I'm really looking forward to winmodem support and better dialup in 7.10

---

### Post by jitsu on 2007-05-27
My dial up connection was working perfectly in U6.06 and I decided to upgrade to Ubuntu 6.10--

My serial modem was detected and I then used:
sudo nano /etc/wvdial.conf   to enter my ISP, username and password.

The Ubuntu instructions say to hit control O to save and control X to exit the file.

The control O or whatever is not saving the file. There is apparently some other command to save the configuration which I'm unaware of. How do I save?

appreciate any help.
thanks, Charles

---

### Post by jitsu on 2007-05-28
Please disregard my previous post.

I installed Ubuntu 6.10 and got my dialup connection working.

I'm not used to the terminal editor and I'm trying to learn it.


thanks, Charles

---

### Post by jmore9 on 2007-05-28
Don't know if this will help.  When i used a modem with 6,06LTS i beleve it was !  I would setup wvdial and then use pon to dial out and poff to stop (I think those were the commands , hard to remember everything in linux)  You ude terminal and type pon to get on and poff to get off
hope this helps.  I use always on dsl now much easier to use plus faster
 jemor9

---

### Post by anjilslaire on 2007-05-28
Just a thought, & a Q:
Now to start, I've been off dialup for over a year (100mbit fiber to the house :) ), but the rest of my family is still on 56k.
I convinced my mom to buy a mac mini, as I was tired of maintaining her Windows box, and the AV/anti-spyware apps were bringing her old box to a crawl. So she has her Mini, with the external usb Mac 56k modem. Everything works fine. 

Which got me to thinking: Does Ubuntu on an Intel Mac recognize the Apple 56k modem? If this was true, it would solve a lot of hassles for many people. Granted, the Apple modem is rediculously expensive, but I would rather pay $50 for a modem I knew would work, and I imagine a lot of windows converts/noobs would do it also to save the hassle if you could use the Apple usb modem on standard x86 hardware.

Any thoughts. Does anybod know if it works? This could be great if it does!

---

### Post by FLPCGuy on 2007-06-02
> **maniac_X said:**
> With Dapper, my external serial modem worked without problem. As noted above, I am experiencing those symtoms in Fiesty. I have been somewhat able to get around the problem partially.

I went into System>Administration>Network and setup the properties of my modem including checking the little activate checkbox  and then saved the configuration to a "Location" giving it the name of my ISP. I also set my Modem Monitor to the panel.

Upon restart/coldboot, while Ubuntu is loading, my modem will auto-dial out and connect just fine and hold the connection without problem. If I lose the connection during the session, then the problem above resurfaces and I have to reboot to get an working outgoing connection again.

I'm not a developer but seeing as this problem started **after Dapper**, they should look at what changes were made since then and revert if they can.

I have both the Actiontec 56k v92 external EX560LKA serial modem and Actiontec 56k v92 external EX560LKU serial/usb modem(only using the serial portion) both of which worked flawlessly in Dapper.

**EDIT**: Have since installed Gnome-ppp....much less hassle this way.

This was my experience exactly.  I have several external serial 56k modems. I got help from the forum suggesting wvdial and pppconfig via the terminal; pppconfig worked for me and then I downloaded the kppp dialer.  I also believe that dialup networking was trashed with the new Network module in Edgy.  Others indicate that ppp auth problems started a bit sooner.

I don't mind connecting manually but using this method Ubuntu has no network awareness so firewalls and other network aware apps don't work using this method.   I wish someone could tell me how to force Ubuntu to be aware of my manual ppp connection.  

I continue to prefer Ubuntu 6.10 even with lousy dialup support because Ubuntu's low bandwidth performance using Firefox is much better than any other OS I use (SuSe 10.2, Win2k, WinXP).  I don't plan to upgrade to Feisty.  It adds nothing useful to me and is reportedly a lot less stable.  At this point I have managed to download all but 21 big updates to Edgy, including one kernel upgrade.  Edgy is very solid and snappy on my old 1 GHz Dell performing as well as SuSe (on an AMD 2500) and with better dialup Internet response.

I've seen dialup problems documented before as a bug then eventually disappear without being corrected.  Fixing dialup issues has had NO priority in Ubuntu development and probably never will.  I agree that fixing it would require starting from the Dapper networking code.

---

### Post by sarum on 2007-06-02
Earlier in this thread  someone wrote from Nepal explaining why Ubuntu is useless in remote places where modem connection is a far bigger problem  than in places where access to hard wear etc:, available. 
I suspect there are many places in the third world (and in less affluent areas elsewhere) where an OS that wont work out-of-the-box without problems, is not much good to anyone.
Ubuntu; with it's heavy accent on humanity, should surely be doing something about this. Xandros  can do it - so can Puppy. Has anyone here tried Puppy? I found it to be the best for Winmodem recognition; and set up.

---

### Post by preacherd on 2007-06-03
There are still many, many locations in the US where dialup is the only option for internet, unless you have a few hundred up front and $70/month to spend on an unreliable satellite connection which goes out every time a storm blows through.

After seeing that Dell was shipping 7.04, I downloaded it from work and installed it at home. Fortunately I had the forethought to set up a dual boot with XP, so I can still get online at home. At this point, until I can get online with it, Ubuntu will be nothing more than a novelty for me.

---

### Post by FLPCGuy on 2007-06-04
> **preacherd said:**
> There are still many, many locations in the US where dialup is the only option for internet, unless you have a few hundred up front and $70/month to spend on an unreliable satellite connection which goes out every time a storm blows through.

After seeing that Dell was shipping 7.04, I downloaded it from work and installed it at home. Fortunately I had the forethought to set up a dual boot with XP, so I can still get online at home. At this point, until I can get online with it, Ubuntu will be nothing more than a novelty for me.

It looks like your best bet is to find an external serial dial-up analog 56k modem that is truly OS independent like the BestData 56SX or dual 56NET. I think all such modems are out of production as they are rare and prices are rising.  I had to also buy a PCI serial port card from [PCMIcro.com]("http://www.pcimicro.com/.sc/ms/dd/1066117464386813/9/nc/Controller") for $14.99.  [Using this add-in card, your serial port may not be ttyS0.]

If you can find hardware that actually works, obtain a dialup Internet provider like 550access.com (referred by strapane) which has the most local access numbers nationwide. Check for a local toll-free number before you sign up.  Switching to a cheaper provider can offset the cost of the new hardware.

Then search this forum's network section for 'dialup' and follow the instructions to  do some or all of the following config changes as needed.

                                       [FONT=Tahoma][SIZE=2]1. comment out the 'auth' line in /etc/ppp/options or change it to noauth and create an empty /etc/resolv.conf file.  [From Accessories, Terminal][/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]sudo gedit /etc/ppp/options[/SIZE][/FONT]

[FONT=Tahoma][SIZE=2]2.  Add dial-out permissions for your basic username.[/SIZE][/FONT]                                        
[FONT=Tahoma][SIZE=2] $ sudo adduser USERNAME dip[/SIZE][/FONT]
    [LEFT][FONT=Tahoma][SIZE=2] $ sudo adduser USERNAME dialout[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]
3. Determine the serial port your modem device is on and configure ppp.
sudo pppconfig.  
Use the default provider name 'provider' so you can dis/connect by simply typing pon or poff.  Otherwise, you must pass a parameter with the provider name (for alternate numbers).
[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]4. [/SIZE][/FONT]                            [FONT=Tahoma][SIZE=2]    correctly setting the dial-out command from "ATDTW" or "ATDPW" to "ATDT" or "ATDP" in /etc/chatscripts/ppp0.  
[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]sudo cp /etc/chatscripts/ppp0 /etc/chatscripts/ppp0.bak    sudo gedit /etc/chatscripts/ppp0
[/SIZE][/FONT]
                                        [FONT=Tahoma][SIZE=2][search for %external_line%W%phone_number% and replace with %external_line%%phone_number%][/SIZE][/FONT]

[/LEFT]
      After some or all of that, you should be able to get online.  Once online, download KPPP or gnome ppp for an easy GUI interface dial-up dialog.  I know this is probably too much trouble for most people, but it is probably still easier than getting a winmodem to work with each new Linux distro.

---

### Post by adrianus on 2007-07-09
If you are using softmodem or winmodem, one of the driver that can be used is sl-modem
Note :
I find that sl-modem-daemon for Feisty doesn't work for me. It reports that "Carrier is not detected" although I already instruct gnome-ppp to omit carrier detection.
I then downgrade sl-modem-daemon to the version for Edgy and now I can do dial-up again.

The network manager applet also works to initiate dial-up, but the indicator that the computer is online is not working. So by far gnome-ppp is more mature in dialup.

---

### Post by robert shearer on 2007-11-12
I am a newbie and this is a first post so bear with me please.
I tried configuring my dial-up in Ubuntu with no success so went to Kubuntu as it had kppp.
I had used kppp in Mepis with no troubles other  than having to add a line in the chatscript to make it pause 1 second before starting pppd.
Kubuntu did not do it for me so i installed Ubuntu again and added the kubuntu install cd to my software sources list, reloaded then used synaptic to install kppp straight from the kubuntu cd.

All works ok and I didn´t even leave the GUI.
hope this helps someone

---

### Post by Bartender on 2007-11-13
robert -
That's an interesting idea, adding the Kubuntu CD to your sources list.  How'd you do that?  Was it relatively easy?

Little tricks like that might be very useful to those of us who are stuck with dial-up at home, but have access to broadband somewhere else like at work or school.  

I'd tried recently to download the KPPP package to my thumb drive while on broadband but when I took the thumbdrive home to the Ubuntu PC dependencies weren't met.  I can download the entire Kubuntu CD.  If you can explain the process of adding it as a source list or point me to a link I'd sure like to try what you describe.

Thanks!

---

### Post by Michl on 2007-11-24
Just to summarize:
Dial=up under Admin Networking does not work properly
in Edgy and Feisty.

Dial-up using wvdial and gnome-ppp works in Edgy and
a non-soft modem, internal or external.  If I remember
correctly, in Feisty I had to use the serial connection,
and hence an external modem, to get wvdial and
gnome-ppp to work.

Michael

---

### Post by robert shearer on 2007-11-25
> **Bartender said:**
> robert -
That's an interesting idea, adding the Kubuntu CD to your sources list.  How'd you do that?  Was it relatively easy?

Little tricks like that might be very useful to those of us who are stuck with dial-up at home, but have access to broadband somewhere else like at work or school.  

I'd tried recently to download the KPPP package to my thumb drive while on broadband but when I took the thumbdrive home to the Ubuntu PC dependencies weren't met.  I can download the entire Kubuntu CD.  If you can explain the process of adding it as a source list or point me to a link I'd sure like to try what you describe.

Thanks!
Hi Bartender,
Even when you do connect the vagaries of rural Dial-up apply. I have just been offline for a week due to a short in the neighbours electric fence causing the modem to drop-out  after 2 minutes.Noise on the line.

However,in Synaptic package manager,click on Settings, then Repositories. When the window opens click on Third Party Software, then Add CD Rom.
You will be promted to insert the( Kubuntu) cd and the index of packages will be added to Synaptic.
When it has then close and you will be prompted to Reload software sources/package lists.Click on Reload.
Then, in Synaptic, search for kppp.Click on apply and you will be asked if it is ok to load all the dependencies it needs.Click on Mark.Click on install.
You will be prompted to insert the Kubuntu cd and the programs will be copied and installed,with all dependencies.
Worked for me using Ubuntu as the o/s and adding kppp from the Kubuntu alternate install cd.
Best of..

---

