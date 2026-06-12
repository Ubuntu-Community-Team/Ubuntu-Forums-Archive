---
title: "No wvdial in Jaunty"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by Bartender on 2009-08-13
I just found out about this, and wanted to get something out there for the poor saps still on dial-up.
Jaunty does not include wvdial.  I knew us dial-up users were way down at the far end of the bread line, but this is getting downright insulting.

The only things I can think of right now are to:
1) Take your PC someplace with broadband, and download gnome-ppp, which appears to include wvdial.

or:

2) Configure pppconfig properly to make a connection.  It's confusing for first-time users so follow the steps very carefully and make sure you have the correct username, password, and phone number.  Your DNS is probably "Dynamic" and if you set it to "Static" you'll never get online.  If you can set up pppconfig properly, you just open a terminal and type ```
pon
``` to get online, and ```
poff
``` to get offline.  ```
plog
``` gives you some info as it tries to connect.

3) If you can get online with pppconfig, download gnome-ppp.
```
sudo apt-get install gnome-ppp
```

gnome-ppp will give you a nicer interface (the utility will be found at Applications>Internet>GNOME PPP) it also installs wvdial so you can set up wvdialconf.

Any other ideas to get people started, please pitch in.

---

### Post by longtom on 2009-08-13
You are right - it is insulting. wvdial is the only way I get people going here in the third world with a lot of dial-up modems. 
Ubuntu developers are obviously living in the first world and don't care too much.

I was hoping that the involvement of a Mark Shuttleworth might help think of other people but the average first world user - but he doesn't live in the 3rd world, also he might have been raised here. He probably is not involved with the development of any given version either but rather concerned with general policies (like the latest Demian offer).

So here we are, using 8.04 and looking out for distros with the ease of Ubuntu but the features of distros thinking not first world only. I always thought, this is one of the "markets" of Linux (and especially Ubuntu with its African naming and theming) to reach people who can not afford expensive proprietary software and os'.

I would hate to loose those who already have given up on pirating returning to their illegal Nigerian Windows copies because Ubuntu appears to abandon them.

Any tips which other, easy to use system could help and is not as restrictive in their offer of choice as far as networking is concerned.

Any suggestions are very welcome!

---

### Post by Bartender on 2009-08-13
longtom -
have you tried out Jaunty on any of the PC's you work with?  It does have lots of little improvements to 8.04 and if we can get you going with dial-up configuration it might be worth a try...once I got Jaunty working with pppconfig, then gnome-ppp, it *seemed* like dial-up was a bit more responsive than in earlier distros.  That's an entirely subjective comment.

I have a bad feeling the powers-that-be are trying to shake loose the dial-up crowd.
  
Do a thousand people accessing the repository servers on dial-up take up more resources than a thousand people using broadband?  That's probly a stupid question. :(

I double-checked on my PC.  After installing the gnome-ppp package (you can check its contents by going to "ubuntu packages" website, entering gnome-ppp, enter, then double-click on the package name to view details) I was able to start up a terminal and begin using the typical commands to configure wvdial.  So if you downloaded the gnome-ppp package to a thumbdrive, you could copy the package to a desktop, double-click, and the package installer should do the rest.  It sounds like you're busy with numerous PC's, so that might help out.  That would only be necessary on Jaunty, of course.  I believe previous distros include wvdial.

On the other hand, if you could set up pppconfig, and download then configure gnome-ppp, perhaps there's no need for wvdial.  Maybe that's the "logic" that went into tossing it out of the distro.  One dial-up tool is enuf for those losers.  

If I had broadband and a blog I'd write a step-by-step for pppconfig.  pppconfig isn't rocket science, but confusing enuf to the Linux newb. Of course, that would only work for some people doing a very basic set-up.  I'm seeing quite a few threads from folks who are trying to configure cell phones as modems.  That was rare just a coupla years ago.  I don't know anything about that.

---

### Post by PriceChild on 2009-08-13
Have you tried contacting the developers/filing a bug on launchpad?

Not many of them are active here.

---

### Post by Bartender on 2009-08-13
Hi, Price!  Thanks for posting.

No, I never even considered filing a bug.  Pretty sure wvdial exclusion is intentional.  

And I was going to prove it to you by pointing out that earlier versions of gnome-ppp don't include wvdial.  But I was wrong.  Just looked up hardy and dapper gnome-ppp packages.  wvdial *is* included.  

I'm quite sure I set up wvdial several times on several PC's without first downloading gnome-ppp.  wvdialconfig was functional on a fresh install of those earlier distros and now it isn't.

So you've got me wondering if wvdial was tossed out of Jaunty intentionally, or if it's broken?  Jaunty's been out for a while now and it didn't occur to me that this would have gone unremarked for this length of time.

---

### Post by GeorgeVita on 2009-08-13
EDIT: after reading carefully all other posts my position is fully covered.

Regards,
George

---

### Post by Bartender on 2009-08-13
Well, I filed a bug report - #413273.

---

### Post by _duncan_ on 2009-08-14
removed

---

### Post by longtom on 2009-08-14
> **_duncan_ said:**
> 
 Can a user achieve dial-up internet connectivity with a supported modem after a default ubuntu install, without having to download anything else? Based on the OP, the answer seems to be yes.


I am not so sure.  It wasn't for me.  And wouldn't it have been for the extremly friendly help of the user lkramer and all his patience, people I know would not be connected and would probably using a well known OS in pirate mode.

Here is a thread illustrating what I am talking about:

[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)

As we see from this thread - setting up a dial-up modem is not for the faint hearted.  Does Ubuntu realise, how many potential users they are throwing away because of this?  Maybe it is true and Ubuntu tries to shut out dial-up users on purpose.

It would than be only fair to make this public, so that dial-up users can choose a different distro which will consider their needs.

---

### Post by _duncan_ on 2009-08-14
removed

---

### Post by longtom on 2009-08-14
> **_duncan_ said:**
> Ummm, you can't connect because you don't know how, not because there are packages missing in the default install of ubuntu, which is basically what my first question is all about. There is a big difference between user unfamiliarity and dev oversight.

I think I do get this.  This worked in 8.10 with wvdial.  Would I have had 9.04 I wouldn't have been able to connect because there is no wvdial.  That's my point....

What am I missing?

---

### Post by GeorgeVita on 2009-08-14
Hi again,
as 'our posts is our reference', we are sure that we (posters of this thread) are in the same position: 'helping newcomers to connect'

We all have many ways to connect (terminal or GUI) and of course other O.S. alternatives. My alternative is Puppy 4.21 (wvdial 1.53 included within 100MB of s/w). Most Ubuntu/Linux newcomers have XP or vista as the alternative.

A well documented pppconfig is probably the solution but wvdial has any more documentation? It is just the 'reputation' from the past and the so many posts with successful connections. I am sure that all methods are OK but let the user choose the appropriate for him. It is just 1 MB data and over 200K of posts explaining!

And a 'joke': I could connect just by using terminal commands (echo, tee, etc) to 'drive' my modem. Terminal will be always standard (are we sure?).

Regards,
George

---

### Post by harry2006 on 2009-08-14
i guess wvdial was not available in the base kernel of 9.04 i.e [2.6.28.11-xxx] but I think its now available in the base system, as I'm on ubuntu 9.04 and use wvdial to connect thru EVDO modeme...and I remember it was not there right after installing from the liveCD...and i must say configuring wvdial is simple and straightforward in comparison to using the other gnome-xxx method mentioend earlier...

---

### Post by _duncan_ on 2009-08-14
removed

---

### Post by longtom on 2009-08-14
> **_duncan_ said:**
> 
As long as ubuntu has the ppp daemon package installed by default, it is technically feasible for a user to dial-up using a supported modem. Now, if the documentation will include instructions on how to edit the various config files needed by pppd, whether by using one of the convenient tools or by direct manual editing, the rest is up to the user to learn and try out.

It is technical feasible, I am sure.  However, if I have to tell this somebody in a school (let alone his/her parents) they will never get it right.

> 
"Can I connect to the internet with dial-up?"

"Yes, it is technical feasible...all you need to do is to jump through this assortment of hoops.  If all goes well and with a bit of luck you might just get it right.  I know it is your first experience with a PC...you will just have to swim."

"Can I have my Windows pirate back pls...?"


But I am moving away from the wvdial issue and enter the realm of Ubuntu abandoning all dial-up users but the advanced, who happen to have another chance to get onto the internet to ask in this forum...

I still don't get it.  They are doing this on purpose for some reason, which I fail to understand.

But this has been reported - even as a bug (which it isn't) and even the most remote dev of Ubuntu must have heard and realised, that dial-up is extremely poor supported in this OS.  That means...nothing will change - apart from dial-up users, who change their OS.

---

### Post by Bartender on 2009-08-14
> **_duncan_ said:**
> While I have an account at launchpad, I normally just lurk there coz the place can be a bit overwhelming for non-devs. :)

Hiya, duncan!

I got a good chuckle from your comment.  Described my feelings exactly.  In the end I thought, aw, what the hey, the worst is I make an *** of myself.  Last time that happened was 15 minutes ago so no biggy.

I agree with everyone!  The tools are there in a default installation.  But let's tick off the hurdles for the average Linux newb -

1) Unless they have access to a Windows PC and internet, they'll never even find out about pppconfig.
2) If they do catch wind of pppconfig, they will see a confusing mish-mash of threads, none of which gives a comprehensive step by step tutorial.  Actually, you'd need several tutorials, because setting up a 3G cellphone sounds quite a bit different than setting up a serial US Robotics 56K.
3) Show of hands, please - how many of you configured pppconfig successfully the first or second time?  I didn't.  I screwed up and set the DNS to "Static", couldn't find the modem, etc.  I botched up pppconfig just the other day in Jaunty so badly that I deleted the entire profile and started over with a different one.
4) There's that confusing web of folders that must be satisfied - remember your frustration when you thought you'd finally set it up and you type in "pon" and you get the message that you are not a member of the dialout and dip group?  WTH is the dip group?

Add the general disorientation and trepidation, and the chances of a new Linux user getting pppconfig right the first or fifth time is pretty slim. 

As far as I can tell, dial-up users are on their own and it's only getting worse.  But you know what, if dial-up users were handed a solution on a silver platter, they would still have to deal with the occasional 100MB update.  What then?   

I solved the problem by buying a laptop and going to the library or some other place with wi-fi.  I can keep the machine updated, then do basic browsing at home.

For the millions of people who don't have any broadband access whatsoever, I feel your pain.

duncan, dangit now, you're saying there's some kind of demon force behind pppconfig that's even more fun to wrestle with?  Um, yeah, I'll look into that as soon as I can or when you-know-what freezes over :)

ANOTHER EDIT:  I wonder how hard it would be to offer the 700 MB main download, then a smaller one that installs all the stuff that couldn't fit?  That and/or just go to a DVD download?

BACK AGAIN:  Oh, yeah, let's not forget that even after some poor newb did 157 things right and finally got online, Firefox will open in "offline mode".  *&$^#_**

---

### Post by longtom on 2009-08-14
> **Bartender said:**
> Hiya, duncan!

I got a good chuckle from your comment.  Described my feelings exactly.  In the end I thought, aw, what the hey, the worst is I make an *** of myself.  Last time that happened was 15 minutes ago so no biggy.

I agree with everyone!  The tools are there in a default installation.  But let's tick off the hurdles for the average Linux newb -

1) Unless they have access to a Windows PC and internet, they'll never even find out about pppconfig.
2) If they do catch wind of pppconfig, they will see a confusing mish-mash of threads, none of which gives a comprehensive step by step tutorial.  Actually, you'd need several tutorials, because setting up a 3G cellphone sounds quite a bit different than setting up a serial US Robotics 56K.
3) Show of hands, please - how many of you configured pppconfig successfully the first or second time?  I didn't.  I screwed up and set the DNS to "Static", couldn't find the modem, etc.  I botched up pppconfig just the other day in Jaunty so badly that I deleted the entire profile and started over with a different one.
4) There's that confusing web of folders that must be satisfied - remember your frustration when you thought you'd finally set it up and you type in "pon" and you get the message that you are not a member of the dialout and dip group?  WTH is the dip group?

Add the general disorientation and trepidation, and the chances of a new Linux user getting pppconfig right the first or fifth time is pretty slim. 

As far as I can tell, dial-up users are on their own and it's only getting worse.  But you know what, if dial-up users were handed a solution on a silver platter, they would still have to deal with the occasional 100MB update.  What then?   

I solved the problem by buying a laptop and going to the library or some other place with wi-fi.  I can keep the machine updated, then do basic browsing at home.

For the millions of people who don't have any broadband access whatsoever, I feel your pain.

duncan, dangit now, you're saying there's some kind of demon force behind pppconfig that's even more fun to wrestle with?  Um, yeah, I'll look into that as soon as I can or when you-know-what freezes over :)

ANOTHER EDIT:  I wonder how hard it would be to offer the 700 MB main download, then a smaller one that installs all the stuff that couldn't fit?  That and/or just go to a DVD download?

BACK AGAIN:  Oh, yeah, let's not forget that even after some poor newb did 157 things right and finally got online, Firefox will open in "offline mode".  *&$^#_**

Couldn't have said it any better - poetry...:P

---

### Post by _duncan_ on 2009-08-14
removed

---

### Post by GeorgeVita on 2009-08-14
Hi **_duncan_**, thanks for replying, [COLOR="Silver"]I will repeat my "our posts is our reference", and  I would like to leave this thread as it becomes 'philosophical'. I prefer to be 'in the field' and receive some 'thanks buddy' from a 1-2 beans poster which means he just sign in to say thanks after a lot of efforts to connect...
[/COLOR]
Just to raise my knowledge, my next goal is to 'drive' pppd directly from terminal!

EDIT: ubuntu 9.10 Alpha 4 + updates, Huawei E169, WIND GR, 'terminal only connection' ```
g@KKa4:~$ sudo pppd ttyUSB0 460800 nodetach defaultroute noipdefault noauth lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','gint.b-online.gr'" "OK" "atdt*99***1#" "CONNECT"' user web password web
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
CHAP authentication succeeded
CHAP authentication succeeded
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 212.152.81.8
remote IP address 10.64.64.64
primary   DNS address 212.152.70.6
secondary DNS address 212.152.70.7 
```

[COLOR="Silver"]
I believe that in the near future broadband modems (4G+) will become [software defined radio]("http://en.wikipedia.org/wiki/Software-defined_radio") the firmware will be supplied only to 'partners', so developers will need a CD .iso just to enable it!
[/COLOR]
Thanks,
George

---

### Post by Bartender on 2009-08-14
duncan, +1 your assessment -

I think people go for wvdial because they heard it's "easier", but the reality is a bit more complicated.

Better to expend your energy on figuring out pppconfig.  Steeper learning curve, but better end results.

---

### Post by _duncan_ on 2009-08-14
removed

---

### Post by rgb1701 on 2009-10-16
For the record, I am also amazed at the lack of pre-installed and easy to setup dialup in recent Ubuntus.

It's particularly frustrating given Ubuntu's "ease of use" and "humanity to others" mantras.

Try any PuppyLinux since at least 3.x.  I am using the current 4.3 for dialup.

PuppyLinux uses wvdial v1.53, quite a bit older than the v1.60 installed by default from Synaptic in Jaunty.

Once you use dialup in PuppyLinux 3.x or 4.x, you will be appalled at the state of dialup in Ubuntu.

Puppy's dialup and modem setup are so ridiculously simple, it will make you cry and shake your fist at the Ubuntu devs.

Yes, I have "high speed" 2Mb internet here in SE Michigan (low speed by the rest of the world's standards :(, a political discussion for another forum), but my lake home in northern Michigan has nothing but dialup,  Can't get DSL even if I wanted it up there.  No cable, and no, satellite is not a serious option.  I NEED reliable dialup there.  I use PuppyLinux there.  I would like to switch to Ubuntu up north, but in its current state, can't.

A sister in law who also lives in the neighborhood in SE MI uses dialup, both in her SE MI home and at her lake home.  She hasn't WANTED high speed internet- she only uses the internet for email and news, maybe travel reservations, all fine on dialup.  Yes, she can easily afford ~2Mb DSL or similar, but has no NEED.  But she does WANT occasional dialup access to the internet.

The Ubuntu devs have VASTLY underestimated the number of people who still NEED and/or WANT easy, reliable dialup.  

You would be amazed how usable much of your daily Internet use is on a good dialup connection- no, you can't Youtube, but most of your time is on forums like this, or Facebook, etc, all fine on dialup.

In conjuction with reliable, simple dialup in a default install, there needs to be a method to reliably and easily move packages and auto updates with all dependencies resolved a priori via a burned disc or thumbdrive to a dialup client from a client with high speed access. 

No, you can't just use stock .debs, which too often STILL need an internet connection to grab bits and dependencies willy nilly over the net. 

I recognize that dialup isn't sexy and devs probably don't want to spend time on it, but it NEEDS to be done.

---

### Post by GeorgeVita on 2009-10-16
> **rgb1701 said:**
> ...Try any PuppyLinux since at least 3.x.  I am using the current 4.3 for dialup.

PuppyLinux uses wvdial v1.53, quite a bit older than the v1.60 installed by default from Synaptic in Jaunty.

Once you use dialup in PuppyLinux 3.x or 4.x, you will be appalled at the state of dialup in Ubuntu.

Puppy's dialup and modem setup are so ridiculously simple, it will make you cry and shake your fist at the Ubuntu devs.

... and a Puppy is always the 'rescue linux':
boot from a USB stick, dial using wvdial and copy any 'missing' .deb file for Ubuntu!

3G rescue dialing with wvdial on Puppy: [http://www.acomelectronics.com/GeorgeVita/puppy3G.jpg](http://www.acomelectronics.com/GeorgeVita/puppy3G.jpg)

Regards,
George

---

### Post by t0p on 2009-10-16
Seems to me that yet again Ubuntu favours eye candy over functionality.

Can anyone tell me how to configure pppd in order to use a cellphone as a modem?  It's easy to do with wvdial.

---

### Post by GeorgeVita on 2009-10-16
> **t0p said:**
> Can anyone tell me how to configure pppd in order to use a cellphone as a modem?  It's easy to do with wvdial.
Hi **t0p**, **wvdial** does not exist even into Karmic but **pppd** and **chat** I suppose will be always there.

When you have a new installation (no eth/wifi, no wvdial) OR network-manager is temporarily broken (like during the development phase) you CAN connect using 'basic' commands. Most connecting programs are a text or graphical front end for **pppd**.

The way I used to find out the 'pppd connection string' was to put network-manager into debug mode and keep a note of the terminal command used to 'run' pppd. Then I read '**man pppd**' and '**man chat**'. The result is an '**oneliner**' command that I have copied to my USB memory sticks and on my Desktop.

At any time if something goes wrong, I open a terminal window, copy the contents of my oneliner text file and connecting (same with puppy). You can try 'default wvdial parameters' including those into **/etc/ppp/peers/wvdial** compare also 'pppd defaults'.

Some parameters need sudo, some others no. I tried a lot of options with one target: to make ONE command working without any modification to any file and possibly use it to some/any (?) linux dist/version
note: my modems are some Huawei (most times an E169) and a ZTE MF636

My oneliner for Huawei E169, Wind (GR):```
sudo pppd ttyUSB0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','gint.b-online.gr'" OK "atdt*99***1#" CONNECT' user web password web

```
This pppd commaaaaaand consists of two parts:
a. pppd parameters 
b. chat negotiation with the modem (basic commands only)

As (b) includes only some basic AT commands often needs a CTRL-C and a second try (depends on the modem condition), but this is a 'minimalistic' solution. If you want it 'bullet proof' or 'more attractive'  you could make a script.

Regards,
George

---

### Post by rgb1701 on 2009-10-18
> **t0p said:**
> Seems to me that yet again Ubuntu favours eye candy over functionality.

.

I wouldn't say that- Ubuntu just uses basically a stock Gnome desktop and look, except for a custom wallpaper (trivial) to distinguish each release.  No real difference desktop-environment-wise than any other Gnome distro like openSuse, Fedora, etc.

As a followup to my rant-ish previous post, I got dialup working fine on 9.04 Jaunty.

I wasn't clear in my prior post that dialup wasn't working for me with gnome-ppp and wvdial 1.60 in Synaptic on Jaunty.

After entering all the ISP info (user, password, phone number) auto-detecting the external serial modem in gnome-ppp->setup->modem tab->detect, then attempting to Connect, the modem would not go off-hook (i.e. not get a dialtone) and gnome-ppp would report "sending password".  I tried running sudo gnome-ppp, and that didn't help.

I then edited /etc/wvdial.conf as root (sudo gedit /etc/wvdial.conf) to be sure the phone number, login name and password were good, then saved it.

I also edited my ~/.wvdial.conf hidden file (in your home directory) to verify the info was correct, even though the file has a comment warning 
"Do NOT edit this file by hand!".

In the end, I don't believe either of these file wvdial.conf edits were needed- the gnome-ppp dialer finally started working when I checked "Remember password" in the main gnome-ppp dialog.

For security, I didn't want the ISP login password saved locally to one of the clear text wvdial.conf files, so I didn't think to check the box during all my dialup testing last week.  I tested a recent vintage USR 5686e External serial hardware modem and an excellent 1998 vintage DIamond Supra Express 56K external serial modem.  

However, looking at the logfile detail (wvdial term window output in gnome-ppp while it tries to connect), I could see that gnome-ppp was getting confused by the feedback from wvdial, which was displaying the word "password" when asking for the un-saved password, and the gnome-ppp GUI was interpreting that as the "password" prompt from the ISP, even before taking the modem off-hook!  

This issue may be due to a change in wvdial version and gnome-ppp wasn't updated, or maybe it's always been a gnome-ppp glitch re: the "Remember password" check box.

Anywho, I'm now able to use Jaunty fine on dialup, at least with external real, hardware serial modems ;)

It's as easy as System->Admin->Synaptic->gnome-ppp install.  Just be sure to click the "Remember password" checkbox in the gnome-ppp GUI.

This doesn't take Ubuntu "off the hook" ;) on the dialup issue, though.  These packages should fit on the install CD- or perhaps it's time to move to a DVD image, or perhaps a 2-CD install.  I think a lot more apps like DVD Styler, Avidemux, Kdenlive, Audacity, Jokosher, SMplayer, VLC, Dia, Scribus, Inkscape, and a few others should be included in the default install- a topic for another thread.

Take a look at all the work PuppyLinux has done in the latest release v4.31 to support most Winmodems "out of the box" with pertinent drivers build in.

[http://puppylinux.com/download/release-4.3.htm](http://puppylinux.com/download/release-4.3.htm)

"Internet by dialup. Unlike many other distros, Puppy has not forgotten those who access the Internet by analog modem dialup. The kernel has drivers for many modems, including Agere, ESS, Lucent, Conexant, Smartlink, Pctel and Intel chipsets. Rerwin has done an incredible job here, and in most cases we have automatic detection and configuration."

Again, PuppyLinux is great for its niche, but the strength of Ubuntu's community, Debian base, and wealth of easy to install packages is second to none.

---

### Post by gypsywind on 2009-10-24
Good afternoon,

I've been trying for three days to download Wvdial from- ubuntu-packages, with no luck.

I am downloading from the computers at our public library to a cd-r disc, and when I attempt to load them into Ubuntu 9.04 there are error messages being displayed. I'm pretty sure after three attempts that I have the process down correctly- Go to ubuntu packages/type Wvdial into the search box/ download dependencies-and their dependencies related to Wvdial to the cd-r. I then bring it home, drop the cd into the Rom drive, wait for it to load, and open the package with a right-click on the cd icon. At this point I double click the file, it appears to start the loading process, and then the error message appears ( I forget what the error message states, but it has been the same all three times).

My question is this- Could there be a problem with the download from the Ubuntu Packages site with regard to Wvdial?

I have successfully downloaded >gnome network administrator< using the process described above.

Any help would be appreciated.

Thank you.

(OH!! And will there be a default dial up package within the Karmic Koala 9.10 release on Oct. 29? Thanks for an answer for this, too.)

---

### Post by gypsywind on 2009-10-24
Ok...

Just found this post by George Vita from a little earlier on the thread...


""It is a little bit difficult to restore the missing wvdial (in 9.04) **without having internet access to this pc**. Also we must say that this is a very strange situation. I managed to install, connect via wvdial and send this post. At first I downloaded the following packages (from a pc connected to the internet, any O.S.):

1. [http://packages.ubuntu.com/jaunty/i3....3.13/download]("http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download")
2. [http://packages.ubuntu.com/jaunty/i3...-base/download]("http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download")
3. [http://packages.ubuntu.com/jaunty/i3...xtras/download]("http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download")
4. [http://packages.ubuntu.com/jaunty/i3...nf4.4/download]("http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download")
5. [http://packages.ubuntu.com/jaunty/i386/wvdial/download](http://packages.ubuntu.com/jaunty/i386/wvdial/download)

**Note that above are all for an i386 pc.**

I copied all to a USB memory stick, and then paste them to the ubuntu 9.04 running pc into **/var/cache/apt/archives/** directory using **sudo nautilus** from terminal. Then I installed all packages by double clicking the icon of each .deb package **in above order** (1,2,3,4 and finally 5) ignoring any message. Finally (after installation) I run wvdialconf, edit the /etc/wvdial.conf file and connected with **sudo wvdial**!""

I'll try this route and see what happens.

(I'm not blind, so I must be "dithering" while attempting to install Wvdial on Ubuntu 9.04. Just for the record- I think it would be wonderful if the ubuntu developers would include Wvdial in the 9.10 package. There are a lot of dial-up users still out here. But that's an ongoing dispute with AT&T and other hi-speed providers. They refuse to provide their services in this area.)

Anywho....have a fun day.  :)

THANK YOU, GEORGE!!!

---

### Post by ranch hand on 2009-10-24
I did file a "papercuts" bug on the dial up situation.  It would be good if folks would go to it and click "this bug affects me too";
[https://bugs.launchpad.net/hundredpapercuts/+bug/389792](https://bugs.launchpad.net/hundredpapercuts/+bug/389792)

Right now I am on my "test" platform on a fully updated 9.10.  For those not aware, we are in the RC so I think that all the features are here that will be in the Final that is due out the 29th.

pppconfig is the only tool available.  wvdial and gnome-ppp are in the repos but that is not a lot of help if you are not connected.

I am in the US (Montana ranch country).  Right now I am in town and have DSL.  This does not go very far out of town.  I was, until April this year, on dial up for 9 years on a remote ranch.

I got into Linux and Ubuntu at about the time I joined this forum.  I used Hardy.  I also have an internal modem, USR5610c, that wvdial could not detect.  I did get it working.  Hardy was the last release that this was really possible on.

I installed (multi boot) 8.10 three times (all at once).  They were all identical an on the same drive.  Wvdial connected one of them just real slick.  Never got the other 2 to connect at all.

Have never tried it on 9.04 as I moved (boss up and died on me-I really am a ranch hand) before installing it.

I have no idea how many people, world wide, depend on dial up.  I know the US is not on the top of the high speed connection list but up there.  I also know that there a lots of places that will not see any option but satellite or dial up.  Folks can afford dial up.

This really need addressed.  I think that if we can get some activity on my bug, it will be noticed.  the more people click on that the better.  Click and then go to the bottom of the page and make a comment.

You do need a launchpad account, but you need that to file bugs anyway so you should have one.

---

### Post by GeorgeVita on 2009-10-24
Sorry to say : **[SIZE="3"]No wvdial & [COLOR="Red"]NO 3G[/COLOR] in Karmic![/SIZE]**

Read more at: [http://ubuntuforums.org/showthread.php?t=1285294](http://ubuntuforums.org/showthread.php?t=1285294)
and relative bug#: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

(add that some wifi chipsets are NOT working out of the box with LiveCD or released .iso)

G

P.S. @gypsywind: have a nice Ubunting!

---

### Post by gypsywind on 2009-10-24
Hello Ranch Hand

Just went to your "papercuts" thread on Launchpad to add a comment.

I have a friend who runs an ubuntu OS on his machine at his coffee shop in the town 3 miles from where I live (Not sure what version). They have hi-speed there, so the OS works. I've enjoyed using the machine with the OS on it when I'm there to check emails while enjoying a good cuppa joe. 

So I ordered a cd.

I'll figure out how to get this SOB up and running, even if I have to buy a coupla spindles worth of cd-r's to do it!!. I dislike Windows That Much!! :)

Have a good one.

---

### Post by ranch hand on 2009-10-24
I hope that you are using 9.04.

I am testing, and like 9.10, but if you are just starting out you need a real stable version and 9.10 is not there yet.

There will be a lot of updates after the Final Release and dial up is a slow go.

If you are using windows and have an internal modem it is likely a winmodem.  These do not work all that well under windows.

I would get a good hardware modem (winmodems are software modems).  Jaunty should have no trouble detecting an external modem and hardware modems require no drivers as they are self contained.

Going through pppconfig should be all you need to do.
EDIT
Forgot;
Thanks for the comment.
Welcome to Ubuntu.
(I am a noob too)

---

### Post by gypsywind on 2009-10-24
I am using a 56K usb external modem- a US Robotics model 5635. I dismantled the internal modem a few months ago.....

I have written down your pppconfig instructions and will give it a go after the University of Michigan gets their heads handed to them by Penn State on the gridiron. (I'm a Michigan State fan and Iowa is in town tonight at 7pm. Go Spartans!!) :)

Thanks for your time and insights this afternoon, Ranch Hand.

---

### Post by ranch hand on 2009-10-24
> **gypsywind said:**
> I am using a 56K usb external modem- a US Robotics model 5635. I dismantled the internal modem a few months ago.....

I have written down your pppconfig instructions and will give it a go after the University of Michigan gets their heads handed to them by Penn State on the gridiron. (I'm a Michigan State fan and Iowa is in town tonight at 7pm. Go Spartans!!) :)

Thanks for your time and insights this afternoon, Ranch Hand.
WHAT.  Where the heck are you from.

I was born at Sparrow Hospital in Lansing.  They call it maze, we call it corn.

So, I second that Go Spartans.  And, maybe more imortantly, Go Penn State.

---

### Post by gypsywind on 2009-10-24
No kiddin'?!!

I'm about 45 miles west of that Sparrow Hospital. Little town called, Hastings.

Michigan got hammered today

 35-10  :)

What did the Wolverine say to the Spartan?

Can I super-size that for you, sir? :)

---

### Post by ranch hand on 2009-10-24
Well, small world.  My dad (dead now) farmed in the Nashville - Vermont area.  The John Deere and Stihl dealers in Hastings would remember him.  I think I could find Hastings.

Good news from the game.

I break for animals, not wolverines.

---

### Post by gypsywind on 2009-10-24
I am shocked that I'm speaking with someone in Montana who knows where Nashville, and Vermontville are. Not to mention being born at Sparrow Hospital. 

It is a small world. Pleasure to meet you.

I did some research on my modem while Michigan was giving that football game to Penn State like it was some sort of a gift. :) Turns out my usb modem isn't going to get the job done without going through some twists and turns at the package site. So, I'm shopping some REAL 56K serial modems while online and listening to the Spartan game on the radio out of Lansing. WMMQ Fm 94.9.

Looks like I found a few serial modems at newegg that will do the deed for a reasonable price, and one made by Trendnet is Linux compatible including the ac adapter and serial cable (I lucked out and found a serial port on the back of the pc).

So....I should be up and running without any complaints soon. 

Thanks again for showing me the path of least resistance for getting this OS up and running. Maybe I'll send my Windows XP OS to someone in, Ann Arbor. Just for grins and giggles.  [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---

### Post by ranch hand on 2009-10-24
I actually spent most of my youth on our beef farm near Laingsburg.  We wire in Clinton county, Victor township.  Voted the first time in the Grange hall with the wood stove for heat (in the 71).

Michigan is a nice place, even with mosquitoes as the state bird, but they ruined agriculture there to suck up to the auto industry and Detroit in general.  I am sure, for instance, that all the Green Bay fans in the UP were real happy to finance the Silver Dome with their tax money.

I like it where the population densolation (as my son puts it) is not so bad.

We should probably not  hijack this thread though.

---

### Post by Bartender on 2009-10-24
You're not trapped by the "legacy" serial port on an old modem like a USR 5686.  You can use a serial to USB adapter cable such as Sabrent's.  The modem will be recognized as ttyACMO, not ttys0, so you'll have to change wvdial or pppconfig, but it does work.

---

### Post by anewguy on 2009-10-25
[QUOTE  Oh, yeah, let's not forget that even after some poor newb did 157 things right and finally got online, Firefox will open in "offline mode".  *&$^#_**[/QUOTE]

I had that problem and like an idiot I had to ask for a solution (found at least 2), but you'd think it would work (BTW - I think it might be a network manager bug instead of FireFox - I think network manager is not reporting correctly when a dial-up connection, hence one of the fixes to set an option in FireFox to ignore network manager, and that FireFox does come online if you use one of the other network managers instead).


Also, just a thought here, but considering how everything seems to be built in Linux, aren't all the tools being mentioned just front-ends to ppp?  I think if someone would create a single GUI'd app that lets you set up dial-up, just as they do in Windows, everyone would be happy.  I don't know what tool today might actually be that tool, as lkreamer also pointed me in the direction of wvdial after he sent me a FREE modem when I had to move and lost my broadband.  I was looking for an interface such as the old terminal in Windows where you could actually "talk" to the modem, however by reading what he had and looking at the tools I was able to get dialup working.  But then again, I'm an ex-techie, and I guess I had no idea where to start setting up dialup in Ubuntu.  As someone has already mentioned, a good, step-by-step, in plain English (or language of choice) for the "common" person dialup help included with the distribution media could help as well.  Ubuntu has come a long way in simplifying things compared to when I first tried Linux back in 1995 or 1996.  However, sometimes the "simple" things needed for non-tech users is still overlooked on occasion - I suspect this is one of those occasions.

Since I do want to install 9.10 when it's officially out, I'm glad someone is at least calling some attention to this so I can be prepared.  Since I've been too lazy to look, I was wondering if anyone has looked at the release notes for 9.10 to see if they mention the omission of wvdial and suggest what to do in its' place.

Dave :)

---

### Post by longtom on 2009-10-25
@Ranch Hand

added to your bug a "affects me too".

It is a real shame that we "dial uppers" are snubbed at by Ubuntu.

Since I try to get people going in Africa I will probably have to change distros because of that.  That is a real bummer...start from fresh again.

---

### Post by ranch hand on 2009-10-25
Thank you.

Africa is one of the places that I imagine has a lot of folks out of range of high speed connections.

Seems like a natural concern for Ubuntu (an old African worn for "can't configure Debian" read that in someones sig - I liked it).

When a lot of the work is done by people donating their time it is hard to force the to develope something.

However, there are several distros that configure your dial up during installation with about 4 pieces of information.

I think Ubuntu could have a better system quite easily and it is, I think, more important than having a slide show in the installation process.

---

### Post by Faolan84 on 2009-10-25
I know for a fact that OpenSuSE does have easy dial-up configuration assuming you have a supported modem. They pretty much ask you what kind of network you are connecting to and whether it needs to be configured or if your "go" from the start like on most household networks.

That being said, I do think that Ubuntu could have a better install process. I always use the text installer because I don't have windows and don't like using the live install because it takes more time. They could really do a better job when it comes to installation methods.

Assuming I could code, I would get right on it, but my C is quite lacking.

---

### Post by gypsywind on 2009-10-25
Ok...

Been doing some research on 56K external serial modem installs for ubuntu operating systems on Google this morning and ran into a thread with the screen name Bartender participating (guy from the UK was trying to find an inexpensive external serial modem to use with an ubuntu install). Interesting thread. What I gleaned from it is this....

In order to get this ubuntu os up and running correctly, and fully functional to use a modem, I should hook up my PC on someone's broadband connection to get all the packages like Wvdial- pppgnome- scan modem-chipset downloads, etc. I can simply use the synaptic package manager and gather it all up. But then I'll still have to configure the modem with a really limited knowledge of Linux system commands to get it running, after spending between $35.00 and $80.00 for an external serial 56k modem that Linux/Ubuntu will recognize.

Of course, I'll have to impose on someone with a broadband connection to do all this. 

Then, as Bartender mentioned in the thread I was viewing, after going through all of this I could have as much as a ten hour update waiting for me when I get home again with my computer and reconnect it to a phone line. At this point my ISP may or may not cooperate with a ten hour update. Which means I'd have to go back and impose on a friend with a broadband connection.......Well, you get the picture.

I've had to reformat my computer, which is currently running Windows XP, a few times this year because of malware (Yes, I'm running a security software suite. Norton 360). The Windows update site is brutal with a dial-up connection, and getting more so each month (14 major updates for XP in Sept. and Oct.this year, on top of the 41 updates preceding them). Takes about five hours. Which is why I decided to take a shot with the Ubuntu OS. But a ten hour update on top of the modem connection machinations? Yikes!!

Windows recognizes my modem, actually, any modem immediately. But it's a malware magnet.

Ubuntu doesn't recognize my modem unless I have a degree in computer science from M.I.T, and can apply it. I understand it fends off malware rather nicely. (Of course, this isn't an experiential insight. I won't know that until I post on a political blog about the UAW being the dynamic, driving force behind the expansion of the American middle-class, while using an Ubuntu Os). :)

Geezus.....the things we do for passion.  :)

---

### Post by ranch hand on 2009-10-25
OK, slow down and don't panic.

I never downloaded an ISO over dial up but updated and downloaded programs and things like the "restricted extras" (large files).

I, unfortunately had Vista on here when we bought it.  Could never, over dialup update the security on it.  Our connection speed was around 4K/sec.

Hauling your box somewhere is silly, do not do it.  There are ways, if you really need a package, of getting it onto a disk.  This is easier to transport and RW media is fairly cheap.

Just about all the tools mentioned are using pppconfig as a backend, at least in part.

Why not a USB modem?  I have nothing against serial ports (this box cam without it but I put one in for my old printer).  I am just wondering.

The biggest problem with dial up modem installation and configuring is getting the OS to see the modem.  If that is done, there is not a lot of problem.

I would suggest that you fire up pppconfig and try it out.  Look in windows for what port it is on.  Subtract 1 from the port number and you have the ttySx (x=port number - 1).  Assuming it is a winmodem it will not work but you will see what the ordeal is about.  I configured liveCDs to run our modem even.  Took about 3 minutes and, under Hardy, I had to configure it twice (once each in 2 different tools). 

I think that you will find that your Win install will have a better speed with your new modem than it does now.  In our case it went from 2.6 to 3.5Kb/sec with the winmodem to 3.6 to 4.4Kb/sec.

To try your hand at that run this;
```

sudo pppconfig

```Take your time follow the directions, you can go back and wipe the info so - HAVE FUN
EDIT
Another piece of information that you may not know right off is your "localhost" or "host" adress.  Use 127.0.0.1 and, I believe they ask for a secondary 127.0.1.1.
EDIT
To try to see if it works I believe you will have to run the command "pon"  if it does work you will have to run "poff" to disconnect.  Sudo required I am sure.

---

### Post by gypsywind on 2009-10-25
Hi R H,

Actually, I am having fun with the whole thing because it's so overwhelming. I'm just letting off some steam (I love to write) while condensing this huge new plethora of information down to the essentials. I'm a trucker by trade, and I can understand how my distilling process at times, especially through writing, could be interpreted by someone reading as somewhat edgy. I once read that good writers write for their own understanding, and that was my intention this morning after reading a few more threads on the subject. It was more like a, "Gosh, GW (over-the-road cb handle).... now look what you've gone and gotten yourself into!" So, I'm sure that's what you were picking up on with regard to fun.

It's become clear to me that it is probably necessary to acquire another computer so I can be online to acquire the knowledge to stay 'in flow' and succeed in this endeavor. So, I spent the time after making the earlier post to peruse the craigslist ads in this area for inexpensive computers, and found one. It's a win-win situation because I can eventually put a fully functional ubuntu os on both, and gift the second computer to someone who really needs one. I can do this as many times as I wish, too, which is the real gift of the ubuntu OS. So, kudos to all the developers who made the choice to keep their efforts flowing freely out to others.

I've taken your post above, copied and pasted it to my Windows notepad, and will download it to floppy as soon as I finish writing this post out. In the meantime I'll be combing the forum for threads about opening and working with pppconfig. It'll be good for me to learn this stuff (I actually love learning new things once I've committed to it), and the online info is so much more detailed than the Help and Support info within the OS.

BTW- I am using a 56K US Robotics USB mini faxmodem. I'll find the tutorial for how to use pppconfig correctly sometime this afternoon (after getting tonight's dinner going), and I'm sure it will well compliment what you've shared here about configuration earlier this morning. Thank you, R H. Your knowledge, and willingness to share it is greatly appreciated, as is everyone else's here who participates.

(Ok, where was I now?.....oh yeah, the Employee Free Choice Act. Get emails out to other drivers....The boss ain't gonna like it...:) ) 

Have a great day!!

---

### Post by ranch hand on 2009-10-25
I am not familiar with that modem.  If it is a winmodem (software modem) it is not going to work as you need drivers.  It is not worth getting the drivers for them because the preformance is bad anyway.

A tutorial is really not needed for pppconfig.  A very simple gui in terminal app.  The pon and poff is needed because there is not (or wasn't in Hardy) a way to set the thing to connect automatically in pppconfig.  

Once you have your modem you will know what information you need and how to do it.  It should be easier because the external should be detected by pppconfig.  When you have it running you can get gnome-ppp or kppp or wvdial or all of them and one will dial it up auto.

Boss' don't seem to like people that work for them to communicate at all.

---

### Post by _duncan_ on 2009-10-26
removed

---

### Post by ranch hand on 2009-10-26
I came across this just now in the testing forum;
[http://ubuntuforums.org/showpost.php?p=8167208&postcount=9](http://ubuntuforums.org/showpost.php?p=8167208&postcount=9)

---

### Post by Bartender on 2009-10-26
Good morning, fellers -
If you found an ancient thread with some guy calling himself Bartender squawking about dial-up, that was probably me.

In case you haven't found it, here's my old dial-up diary.

[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

Although some things have changed, for the most part it's still applicable.  I tried really hard to write this so that someone new to dialup in Ubuntu could get thru it without screaming in anguish.

You'll notice someone else's name in that old thread... duncan, who's been a great source of information in the search for some answer to the dialup nightmare.

Oh, hey, I got an email from someone at Launchpad the other day.  Copy/pasted below.

[I]Many people have confirmed that this is a problem, so marking it as
"Confirmed."

** Changed in: wvdial (Ubuntu)
       Status: New => Confirmed[/I]

I'm still stuck with dial-up at home.  I use an old Windows XP box at home for email and light web surfing, and take the Ubuntu laptop to our new library for updates/new programs/watching video clips/picking up email that someone sent us with 5MB of pictures attached.

That's my "solution" to Ubuntu and dial-up.  I haven't tried openSUSe or other distros that are supposedly easier.  I don't know how they could be - way I understand it, the problem is winmodems and software that's not being provided by the winmodem manufacturers so somebody from within the Linux community had to reverse-engineer.

I have three or four USR serial modems and two of those Sabrent cables.  I can get Ubuntu connected at home.
But it always feels more sluggish than Windows (though connection speed tests indicate they're running very close to the same speed) and as soon as Ubuntu checks for updates the notification icon sits there waiting for attention.

I don't know about you guys, but my ISP kicks me off every couple of hours so the typical 20 to 50MB Ubuntu update ain't gonna happen.  Even if I didn't get bumped off, I don't want to tie up the phone line for a week :)

---

### Post by ranch hand on 2009-10-26
I installed PCLOS-gnome and was connected in installation by giving the phone #, provider w/adress, user name, password.

Interesting OS RPM through synaptic.

Liked synaptic for that and the ease of dialup config but that was about it.

A lot of KDE distros have the same deal as PCLOS.  I can't stand KDE.

I got Hardy to work and it was fine once I got it going.  I am sure that if I can get back on a remote ranch I can change the number and have it up and running in minutes.

What bug are you referring to?  I will hit the bugger too.

Please check this one out;

[https://bugs.launchpad.net/hundredpapercuts/+bug/389792](https://bugs.launchpad.net/hundredpapercuts/+bug/389792)

---

### Post by gypsywind on 2009-10-26
> **ranch hand said:**
> OK, slow down and don't panic.

I never downloaded an ISO over dial up but updated and downloaded programs and things like the "restricted extras" (large files).

I, unfortunately had Vista on here when we bought it.  Could never, over dialup update the security on it.  Our connection speed was around 4K/sec.

Hauling your box somewhere is silly, do not do it.  There are ways, if you really need a package, of getting it onto a disk.  This is easier to transport and RW media is fairly cheap.

Just about all the tools mentioned are using pppconfig as a backend, at least in part.

Why not a USB modem?  I have nothing against serial ports (this box cam without it but I put one in for my old printer).  I am just wondering.

The biggest problem with dial up modem installation and configuring is getting the OS to see the modem.  If that is done, there is not a lot of problem.

I would suggest that you fire up pppconfig and try it out.  Look in windows for what port it is on.  Subtract 1 from the port number and you have the ttySx (x=port number - 1).  Assuming it is a winmodem it will not work but you will see what the ordeal is about.  I configured liveCDs to run our modem even.  Took about 3 minutes and, under Hardy, I had to configure it twice (once each in 2 different tools). 

I think that you will find that your Win install will have a better speed with your new modem than it does now.  In our case it went from 2.6 to 3.5Kb/sec with the winmodem to 3.6 to 4.4Kb/sec.

To try your hand at that run this;
```

sudo pppconfig

```Take your time follow the directions, you can go back and wipe the info so - HAVE FUN
EDIT
Another piece of information that you may not know right off is your "localhost" or "host" adress.  Use 127.0.0.1 and, I believe they ask for a secondary 127.0.1.1.
EDIT
To try to see if it works I believe you will have to run the command "pon"  if it does work you will have to run "poff" to disconnect.  Sudo required I am sure.

Morning R C,

Ok, just got around to playing with sudo pppconfig. I set up the connection with the info, then clicked finished to write the info to files in etc files.

I then opened a new terminal window and typed the words  >sudo pon<  into the command line.

I then received an error message which stated-  only members of the 'dip' group can use this command.

So, I deleted the files for that set up. Reconfigured pppconfig once more, then opened a new terminal and once again entered the command >sudo pon<  and received the very same error message.

It seems like I should be a member of every group on the ubuntu os. I'm the only one on it. I'm pretty sure I have administrator rights as I installed the software.

Oh, and this is the modem I'm using. I believe people have referred to modems such as these as dongles, or some such thing.  [http://www.usr.com/support/product-template.asp?prod=5635](http://www.usr.com/support/product-template.asp?prod=5635)

(I saw a thread elsewhere on-site where  a huawei 'dongle-type' modem wasn't being recognized by ubuntu)

---

### Post by gypsywind on 2009-10-26
> **Bartender said:**
> Good morning, fellers -
If you found an ancient thread with some guy calling himself Bartender squawking about dial-up, that was probably me.

In case you haven't found it, here's my old dial-up diary.

[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

Although some things have changed, for the most part it's still applicable.  I tried really hard to write this so that someone new to dialup in Ubuntu could get thru it without screaming in anguish.

You'll notice someone else's name in that old thread... duncan, who's been a great source of information in the search for some answer to the dialup nightmare.

Oh, hey, I got an email from someone at Launchpad the other day.  Copy/pasted below.

[I]Many people have confirmed that this is a problem, so marking it as
"Confirmed."

** Changed in: wvdial (Ubuntu)
       Status: New => Confirmed[/I]

I'm still stuck with dial-up at home.  I use an old Windows XP box at home for email and light web surfing, and take the Ubuntu laptop to our new library for updates/new programs/watching video clips/picking up email that someone sent us with 5MB of pictures attached.

That's my "solution" to Ubuntu and dial-up.  I haven't tried openSUSe or other distros that are supposedly easier.  I don't know how they could be - way I understand it, the problem is winmodems and software that's not being provided by the winmodem manufacturers so somebody from within the Linux community had to reverse-engineer.

I have three or four USR serial modems and two of those Sabrent cables.  I can get Ubuntu connected at home.
But it always feels more sluggish than Windows (though connection speed tests indicate they're running very close to the same speed) and as soon as Ubuntu checks for updates the notification icon sits there waiting for attention.

I don't know about you guys, but my ISP kicks me off every couple of hours so the typical 20 to 50MB Ubuntu update ain't gonna happen.  Even if I didn't get bumped off, I don't want to tie up the phone line for a week :)

Typical is 20 to 50MB, eh?

Yeah, tying up the phone line for a week isn't gonna work for me, either. 

I imagine if I groveled with a style and grace unseen in these parts for a few decades that I may succeed with imposing on a friend to use his hi-speed connection. The price of buying him a decent lunch as a thank you would be cheaper than buying a new laptop to load ubuntu on, too. Of course, he loves to drink beer with me when we're out, and the penance for that choice would be weightier than tying up the phone line for a week. I can hear her already! :)

---

### Post by ranch hand on 2009-10-26
I carefully studied the updates and, through synaptic or terminal, downloaded in batches (do not shut down until done) that were compatable.  At our speed it took an average of 1 hour per 10Mb (4Kb/sec).  Most was done at night when we were asleep.  20 to 50 is not bad.  Sometimes you get BIG ones that really do need broken up to do on dialup.

---

### Post by gypsywind on 2009-10-26
Well, the good news about my Jaunty Jackalope install is the os has a great music player, and I'm up about $8,000 in fake ubuntu monies playing blackjack.

The bad news is the Gnu chess player is kicking my butt all over the lot.  :p

---

### Post by ranch hand on 2009-10-27
The music does rock.

Have to sleep.

---

### Post by _duncan_ on 2009-10-27
removed

---

### Post by jrev on 2009-10-27
From the beginning of Ubuntu there never was the **gnome-ppp package** in the installation CD and I had to download it from another internet connection.

On jaunty we have a number of packages to download in order to be able to connect on a dial-up connection.

So everything is done to compel you to use the broad band connection.

Thank you  for the beginners !:p

---

### Post by alexcckll on 2009-10-27
Hmmm... maybe there's something to be said for CD-based fix pack releases and definite inclusion of wvdial or similar for LTS releases?

I remember those days on dialup..

---

### Post by gypsywind on 2009-10-27
> **_duncan_ said:**
> @gypsywind



You can add your user ID to the 'dip' group by entering the following command in a terminal:

```
sudo adduser [COLOR=Blue]yourUserID[/COLOR] dip
```replace [COLOR=Blue]yourUserID[/COLOR] with the actual user ID you are using.


[edit] You don't need to use sudo with the pon, poff or plog commands.

Thank you, duncan

---

### Post by ranch hand on 2009-10-27
Yes, duncan, thanks.  I could not for the life of me remember that command.

---

### Post by _duncan_ on 2009-10-27
removed

---

### Post by Bartender on 2009-11-28
Hey, duncan, I'll try to remember to check that on one of the test boxes or next time I install from scratch.

It might be interesting to keep track of the size of some of these Ubuntu updates.  Update going on right now, Nov 28 2009 - 35.1 MB.

Sheesh.  I updated about two weeks ago.

35.1 MB would be impossible at home on our dial-up.  We're using Fry's as our ISP.  The best thing I can say about Fry's is they're cheap - $6/month.  But they drop the connection every coupla hours if I'm busy and much sooner if I'm not actively browsing.  Maybe a better quality ISP would make a difference.  

We never get more than about 40 kbps on our line.  A USR 5686 external gives us better speed than anything else I've tried.  A coupla days ago a friend gave us his old Actiontec serial modem (he's got Qwest DSL now) so I set it up on our XP machine with the official Actiontec drivers.  The Actiontec only gave me about 31 kbps.  I uninstalled it and went back to the USR.  Connection went right back to 41 kpbps.

So with the USR I'm guessing 35 MB would take 3 to 4 hours.

Update Manager completed the 35.1 MB download and installed while I was writing this post.

---

### Post by ranch hand on 2009-11-28
Are you sure about your connection speed.  I am on DSL now but when we were on Dialup the speed was about 4.4Kb/s.  It took basically an hour per 10Mb.  It is doable.

I sure didn't download any ISOs off the bugger.

Mine is a USR5610c internal (not fun to set  up) and it seemed to run faster than any of the nieghbors winmodems and was certainly faster, under VISTA, than the winmodem that came with this box.  I love their modems.

---

### Post by _duncan_ on 2009-11-28
removed

---

### Post by ranch hand on 2009-11-28
I wish I could test dial up but we can't do it here.  Our ISP is rangeweb.net, a subsidiary of Range Telephone (a co-op).  You can only have one type of connection at a time unless you want to have 2 accounts and pay for them both.

We are where there is DSL (@ 320Kb/sec).  If I can get another remote ranch job I will be back on dialup and I would like to know that I can use something other than Hardy.  8.10 was the last version that I had on dialup and of 3 installs of it I could only get one to work on dialup with this internal modem.

9.04 came out just as we moved (boss up and died on me).  It was fun to hook up the DSL and see it just connect all by itself.  It was more fun to watch the guys that installed the service (with their little disk to load MS or Mac drivers) watch it just connect on its own too.

---

### Post by _duncan_ on 2009-11-29
removed

---

### Post by Bartender on 2009-11-29
Hey, there, ranch hand, those numbers I referred to are Kbauds per second.  I've never been clear on the difference between Kbauds and Kbytes, but when I said "41Kbps" (I fixed my spelling in the earlier post) that's the number that XP reports when the modem first connects.  If there was a good dial-up speed test that would work roughly the same no matter where you dialed from, it might be interesting to compare results!  

You'll notice I said that 41Kbps is what XP reports. I don't even bother trying to connect with Ubuntu on dial-up at home anymore.  Our daily use, main home PC is a Windows PC.  That's entirely because of the connection.  The Ubuntu laptop goes into town with me.  That's probly the way it's gonna be until hell freezes over or Qwest runs DSL up this road.  I wouldn't want to place bets on which is more likely.

duncan, I've read about init strings but never fully understood.  If I were to watch the XP logs and figure out the init strings, how would I transfer that to an Ubuntu machine?

---

### Post by _duncan_ on 2009-11-29
removed

---

### Post by Bartender on 2009-11-29
OK, thanks, I'll take a look.

---

### Post by frank cox on 2009-11-29
Hi Duncan:


   I have had nightmares trying to get a winmodem to work in Ubuntu. I had the driver working well enough to hear it dial at one point and it seemed to be connected but would not let me browse.

I downloaded the network package and gnome-ppp but I cannot get them to agree on what the modem is. Network only recognizes it as /dev/modem and gnome-ppp will only detect it as /dev/ttySHSF0 . Iwent ahead and gave myself permission to dial the internet like you suggested.

Soon I will lose acess to the high speed, is there any other software I need?

With Puppy Linux I hooked up an external USR sportster flashed to 56k and it works perfectly. I wish the setup in Ubuntu was as easy as Puppy!

I am totally confused about the relationship between Network and gnome-ppp - wvdial. I understand gnome-ppp is a front end for wvdial/  I have read the manuals and it gives me a headache. Could you explain why both programs are there or are if they should be?

If I give up on the winmodem -{I have the proper driver} is there any trick to setting up the external serial modem?  I really hate to do that because I only have one sportster and I have 3 modems that will {supposedly} work off of the Linmodem driver and I have several  Dell machines one of which I know there is a driver for the winmodem for Ubuntu 9.04.

It is kind of you to help so many people with your knowledge and your time.

Thanks

---

### Post by ranch hand on 2009-11-29
I would still recommend a USR hardware modem, serial or USB.  There are no drivers needed.

Hardware modems are self contained.  Winmodems depend on the cpu for processing power.

Your modem "negotiates" with the modem at the other end for your connection, both speed and duration.  A winmodem is fairly wimpy in this department.  A hardware modem "negotiates" with a club.  With a nail in it.  If your ISP is busy, it is every winmodem that will get "timed out" before any hardware modem.

It sounds to me like you have a connexant winmodem.  I had that when we got this box.  Under Vista, I got a 33% increase in connection speed.  I got better speed under Ubuntu than Vista with the hardware modem.  I did not bother with the drivers for the winmodem because our old box had a hardware modem and we were shocked at the slow speed with the new box with the winmodem.

---

### Post by Bartender on 2009-11-29
> **ranch hand said:**
> I would still recommend a USR hardware modem, serial or USB.  There are no drivers needed.

+1  I don't care to screw around with trying to make winmodems work.  The USR is going to be faster even if you somehow made the winmodem functional.

If you find an old USR with serial, there are adapters that let you plug into a USB connection on the PC.  Such as the Sabrent SBT-USC1M.

---

### Post by frank cox on 2009-11-29
> **ranch hand said:**
> I would still recommend a USR hardware modem, serial or USB.  There are no drivers needed.

Hardware modems are self contained.  Winmodems depend on the cpu for processing power.

Your modem "negotiates" with the modem at the other end for your connection, both speed and duration.  A winmodem is fairly wimpy in this department.  A hardware modem "negotiates" with a club.  With a nail in it.  If your ISP is busy, it is every winmodem that will get "timed out" before any hardware modem.

It sounds to me like you have a connexant winmodem.  I had that when we got this box.  Under Vista, I got a 33% increase in connection speed.  I got better speed under Ubuntu than Vista with the hardware modem.  I did not bother with the drivers for the winmodem because our old box had a hardware modem and we were shocked at the slow speed with the new box with the winmodem.


Hi Ranchhand, that is not really what I wanted to hear but I don't doubt you, the USR modem seems to run a little faster with Puppy Linux than a winmodem in windows.
I really wanted to be able to use the answering machine and fax features, not to mention not have to buy a bunch of serial modems when I have the windodems coming out my ears.

I will have to buy a serial code for my newest machine as it has none. Do you know if the u=USB to serial modem adapter is a good bet? If I bought one I could use it on my laptop as well. I have no clue how else I could dial with my laptop, fortunatly I useally can connect with wireless or ethernet with the laptop.

Can you answer the question about the network and Gnome-pp not agreeing on what the modem is? Will this issue dissapear with the install of the serial modem?

One more question, I can buy internal serial modems sometimes fairly cheap, do they work as well?

It is a conextant .

---

### Post by _duncan_ on 2009-11-29
removed

---

### Post by ranch hand on 2009-11-29
I never used gnome-ppp.  I used pppconfig and the Hardy network-manager stuff.

Internal modems have a problem being seen correctly in Ubuntu.  Externals are not supposed to be any trouble at all.  Mine is an internal and it was a bugger to set up and was never seen by several parts of the OS that were supposed to see it.  Worked great anyway.

I have never used any USB/serial adapters.  Tried one with our OLD printer as it is a serial hookup.  This did not work.  I got a pci card with a serial port on it for the printer.

External modems come both USB and serial.  I would get what your box(s) will take and not worry about adapters.

---

### Post by _duncan_ on 2009-11-30
removed / unsubscribed

---

### Post by Bartender on 2009-11-30
> **frank cox said:**
> Do you know if the u=USB to serial modem adapter is a good bet? 

Yeah, I bought two of those Sabrent adapter cables and they work fine.  Thre's actually a little tiny chipset in the head of the cable.  The Linux kernel added support for that chipset a couple of years ago.  

When I plugged the USR in via the Sabrent, the modem was identified at /dev/tty/ACM0.  That's the only difference.  

Ironic thing is, I never got the Sabrent to work in Windows.  Windows needed drivers and the Sabrent drivers didn't work.  That was with Windows 2000.  The drivers would probly work with XP, I just haven't gotten around to trying it.

---

### Post by longtom on 2009-11-30
It's wonderful to see how this thread is going along.  Unfortunately it is also quite obvious, that dial up in Ubuntu is a huge pain.

It doesn't have to be.  I made a little flash install of puppy linux on an old usb stick and, in a moment of boredom, clicked the "connect" button follwed some prompts, entered my details and - I was connected - winmodem and all.

So it is possible and I have my flash stick at the ready for any dial up machine.

---

### Post by Bartender on 2009-11-30
Hey, longtom, that's a neat idea!

I keep hearing about Puppy but I like the conveniences offered by GNOME, and I'm not really using Linux at home on our dial-up anyway, so haven't taken the time to try Puppy.

But it would be interesting to do what you describe, and test the half-dozen different winmodems I've got lying around.

If the folks at Puppy have already done the hard work of figuring out drivers for some of the winmodems, it kinda makes you wonder why we can't get the same support in Ubuntu, eh?

Was it pretty easy to plunk Puppy on a flash drive?  If you found some good directions could you pass them on please?

EDIT:  Never mind.  I signed up at Pup forums.  I'm going to download Pup today or tomorrow.  I think I'll just install directly to the HDD on a test PC and cycle thru all the winmodems.  Will report back.  I'm curious of course to see how many of them work, but also if the Puppy GUI is too stripped down for the "average" Linux user.

---

### Post by ranch hand on 2009-11-30
Yes, I have tried dial up in a number of other distros and most were easier than Ubuntu to connect to dial up.

KDE (I don't like KDE) seems to be the easiest generally.

PCLOS-gnome was easy to connect.  Most of the RH (use RPMs) distros seem to hook you up with about 4 questions during install.

---

### Post by frank cox on 2009-12-01
Hey Bartender:
 
  Puppy flies on a stick, Ubuntu is slow. It is cool to boot your own operating system on someone elses machine you had tied around your neck. Most machines will see it as a usb hard drive and not a flash drive. They have a program called Wake Puppy Up, that lets you boot the stick using a cd and that will work on any maching with a cd . 
 
As far as the winmodems they are a pain and I have no idea how to make them work but this information might help you.
 
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)
 
 
That link will let you download the Dell conextant winmodem drivers for free. They are full speed . Apparently if you ship machines runing linux you have to make ALL the device drivers you used in the software repositories for free to keep the GPL agreement .  Good deal for us!
 
Please let me know if they work or if you figure out how to make them work on puppy.
I have one of the restricted drivers but all I can get it to do in Ubuntu is dial. I am green at this and I get a conflict between gnome-ppp and ppp-config as to which port the modem is on. When I tried to install the driver in puppy it said the kernel was not compatible with the driver.
 
I have some old machines I want to give as Christmas presents. I would rather run them on puppy because it is faster on old equipment and more user frirndly than Ubuntu but either would be a blessing .
 
 
 
 
 
> **Bartender said:**
> Hey, longtom, that's a neat idea!
 
I keep hearing about Puppy but I like the conveniences offered by GNOME, and I'm not really using Linux at home on our dial-up anyway, so haven't taken the time to try Puppy.
 
But it would be interesting to do what you describe, and test the half-dozen different winmodems I've got lying around.
 
If the folks at Puppy have already done the hard work of figuring out drivers for some of the winmodems, it kinda makes you wonder why we can't get the same support in Ubuntu, eh?
 
Was it pretty easy to plunk Puppy on a flash drive? If you found some good directions could you pass them on please?
 
EDIT: Never mind. I signed up at Pup forums. I'm going to download Pup today or tomorrow. I think I'll just install directly to the HDD on a test PC and cycle thru all the winmodems. Will report back. I'm curious of course to see how many of them work, but also if the Puppy GUI is too stripped down for the "average" Linux user.

---

### Post by Bartender on 2009-12-01
Well, that was easy...

It took me three tries to get Puppy installed on an old PIII 1 GHz test box.  Mostly me rushing thru and not reading the directions.  After installing Ubuntu about 30X over the last coupla years I went into it too casually.  Aside from my mistakes, it was an odd experience to install an OS that's designed for minimal installations.  I felt like Puppy was going, "Wait, I don't get it.  You just want me to install to this whole 120GB HDD??  No USB thumb drive??"

Next time I'll do it the easy way and install to a thumb drive like longtom said!!  :D

I musta tossed some of the modems last time I went to Goodwill.  In Washington State we have a new e-cycling law and Goodwill is the only place in town that takes old PC's and monitors for free.

Anyway, I only found an Intel 536 modem that was not recognized (it might be broken) and a Conexant that was recognized no prob.  I'm writing this from the old PC with Pup and the Conexant, a winmodem that Ubuntu ignored.  I forgot to write down the Conexant part # before installing so will add that later.

It's awful slow.  I'm only getting about 17Kbps.  But that might have something to do with the old PC.

OK, back to the XP unit with the good old USR external.

First impression - Puppy doesn't seem as painful as I was expecting.  I was afraid that such a lightweight OS would be really geeky.

EDIT:  The Conexant winmodem is out of a Gateway.  Gateway part #6001260.  The Conexant chipset says, "RH56D/SP-PCI  R6795-11  B93389.5  9949"

For those of you who haven't visited the Puppy forums, what a revelation.  Under the "Networking" forum, Dial-up is a discrete sub-forum!

---

### Post by longtom on 2009-12-01
I got a motorola modem which is really popular around here.  It is not popular with Ubuntu so and getting it recognised is difficult and erratic at best.

I'm glad I found a solution for this with puppy.  I even do a hdd install - you just need to configure your grub, for which puppy gives you all the instructions. You can either add to existing grub (which is great for me) or create new one if puppy is all that runs on that PC.  In the meantime I run OO and other basic programs which might be needed by most like thunderbird, Firefox or Opera, multimedia etc.

There are some things I still struggle with like getting the newest LyX going. 

But for the folks here who just want to get there P4 running and do and learn basic application and have a dial-up, which is all they can afford, puppy certainly does the trick.  I am impressed...

But we are certainly sliding of the topic just ever so slightly...:P

---

### Post by Bartender on 2009-12-01
Since I started this thread, you have my permission to go OT. :)

Besides, there's only about five of us participating.  Maybe we're helping someone who's in similar straits but afraid to ask...

I plan to spend some time in the next few days poking at Puppy and see how much I understand.  I'm curious about installing OpenOffice and such but don't want to ask about it here.  I'll have a looksee at the Puppy Forums.

EDIT:  That's where I got in trouble, was trying to install to a blank HDD!  I did it wrong twice.  Third time was the charm.

---

### Post by longtom on 2009-12-01
So far I have only installed it in a Virtual Machine to get the ins and outs.

I also have it on a 512 Flash stick and a 8GB flashstick, which I partitioned in 2 4GB partitions.  This is just to get some more applications on my "on the run" Puppy.

Yes OO and other applications are covered in the Puppy forum.  It is available as an sfs file.  Just do read what you need to do and don't just fly over the documentation like I do and do everything 3 times like me.

I mean - I even found the original Canon driver for my printer for Puppy...

Having said that, there is no recognisable system how everything (available software) is organised - so it's all a bit of a search - like a good adventure game...;)

---

### Post by bob12564 on 2009-12-01
I've been following this thread with great interest because I'm also having a tough time getting my modem to work.  There's seems to be a lot of expertise here and maybe I can ask a slightly different question.

I already have a broadband DSL internet connection.  I recently got my old dialup modem from the closet and I want to use it for fax...just fax...not for an internet connection.  The modem is an external modem connected to a serial port.

I'm trying to use it with efax-gtk.  I discovered that I have wvdial already installed and I ran some command line instruction I found somewhere and it found my modem and detected it's settings.  But so far I haven't been able to get efax working.

Here's my very basic question: Fax software needs dialer software to operate the modem.  I doubt efax can do this by itself.  Wvdial can do the job but it's meant to invoke PPP and requires a logon to an ISP.  I can't see how fax software can work with it because the fax software will hang while wvdial waits to log onto an ISP which, of course, won't exist.  Can someone explain how this all works?  Is there other dialer software I should be using?

This thread started with the comment that Ubuntu support for dialup modems is confusing and maybe more difficult than it should me.  Count me as another user who is quite lost.

Thanks!

---

### Post by Bartender on 2009-12-01
Don't know what's going on with duncan, but looks like he's left and he's covering his tracks. 
I hope that's not the case - he's always been very helpful, especially with dial-up stuff.

I have no experience with fax in Linux.  As far as I know, it'd be easier to just buy an AIO printer!!

longtom, I installed Puppy to a USB thumb drive this morning.  I tried the first time by plugging a thumb drive into the old PIII and starting Puppy from the HDD but goofed it up.  Tried again with the Puppy CD in the optical drive and that worked.  Booted our main PC, a Dell Precision 470 running XP and a USR 5686 external, with the Puppy USB drive.  It was super-easy to set up the dialer, and the u.s. netizen speed test reported 42 Kbps.  That's as fast as I've ever seen from our house.  Obviously, there are some things to learn, but at this point I'm flabbergasted at how Puppy can do so much with so little!

---

### Post by frank cox on 2009-12-01
Bartender. 
It may be the driver you used is not a Dell and if it is not a Dell or  Linuxtant you paid for it will never run much faster than 14.4 . There is  a lock on all conextant drivers for Linux except Dell or perhaps another supplier of Linux machines..
Are you going to try the Dell drivers in Ubuntu?
Puppy amazes me every time I use it, they even have a game puppy. Its so easy and so small you can build the entire OS to do one thing fast.

For anyone who missed it this is where you can get full speed Dell-conextant modem drivers for Ubuntu for free.
They may or may not work in Puppy 

[https://help.ubuntu.com/community/Di...Howto/Conexant]("https://help.ubuntu.com/community/DialupModemHowto/Conexant")

---

### Post by Bartender on 2009-12-02
I have a question for you guys.

Have any of you done enuf experimenting with Linux and softmodems vs. Linux and hardware modems to say whether a hardware modem is always going to be faster?

If the hardware modem is always going to be faster anyway, and a person has a few serial port hardware modems, then it seems to me that part of the justification for going to a distro that supports winmodems better than Ubuntu is rendered moot since I can get Ubuntu and the external working.  Does that make sense to anyone?

If, as in longtom's situation, you're dealing with lots of people who don't have external hardware modems nor access to them, then it seems the case for Puppy or similar is much stronger.

In my case, living in the U.S. and with broadband available in town, it still seems like a Windows PC with an external USR modem for home use, and a laptop with Linux when mobile, is probably pretty close to the best compromise I can cobble together at this point in time.

---

### Post by ranch hand on 2009-12-02
While it is possible to find a winmodem out performing a hardware modem, I would not hold my breath.

The very basic theory behind the winmodem is against it.  They do not run that great under Win JerryLewis Pro.  The whole purpose of the winmodem is to make the PC as cheap (not inexspensive) as possible.  By taking advantage of the cpu for processing power the modem is more "cost effective".

That this adds another layer of crap between the box and the net is not considered a problem, dial up is slow anyway so what does a little more  matter.

You are going to have to find a the MB that the origanal winmodem drivers were built for with the best cpu it will take to get any kind of competitive performance out of a winmodem compared to a hardware modem.  You are also going to have to compare it to a crappy hardware modem.

When we bought this box (see sig) it was replacing a 10 year old P2 (350MHz, 128ram, 10Gb HDD) running Win98.  There is plenty of extra power in this box to run all the modems in this county compared to that box, and still have lots left over for what ever the box is doing.

Under Vista, on a good day, the connexant modem would do ALMOST 3Kb/s (kbytes).  With the USR5610c, under Vista, it would do 4.2Kb/s pretty much anytime.  Being at the end of the phone line, at the time, the connection was lost a lot.

With the winmodem you weree lucky for a steady connection to last more than an hour and then you did not know how long it may take to reconnect.  With the hardware modem loosing the connection became a novelty.

It all comes down to the negotiating ability of the two types of modem.  The worse your connection, the more important the hardware modem is.

Here in the USA if you are on dial up it is not (probably) by choice.  It is because you are too far out to get anything else and can't afford satalite.  You have a bad connection.  You need a hardware modem.  I suspect that this is probably true in any rural and many urban dial up environments.

---

### Post by frank cox on 2009-12-03
> **ranch hand said:**
> While it is possible to find a winmodem out performing a hardware modem, I would not hold my breath.

The very basic theory behind the winmodem is against it.  They do not run that great under Win JerryLewis Pro.  The whole purpose of the winmodem is to make the PC as cheap (not inexspensive) as possible.  By taking advantage of the cpu for processing power the modem is more "cost effective".

That this adds another layer of crap between the box and the net is not considered a problem, dial up is slow anyway so what does a little more  matter.

You are going to have to find a the MB that the origanal winmodem drivers were built for with the best cpu it will take to get any kind of competitive performance out of a winmodem compared to a hardware modem.  You are also going to have to compare it to a crappy hardware modem.

When we bought this box (see sig) it was replacing a 10 year old P2 (350MHz, 128ram, 10Gb HDD) running Win98.  There is plenty of extra power in this box to run all the modems in this county compared to that box, and still have lots left over for what ever the box is doing.

Under Vista, on a good day, the connexant modem would do ALMOST 3Kb/s (kbytes).  With the USR5610c, under Vista, it would do 4.2Kb/s pretty much anytime.  Being at the end of the phone line, at the time, the connection was lost a lot.

With the winmodem you weree lucky for a steady connection to last more than an hour and then you did not know how long it may take to reconnect.  With the hardware modem loosing the connection became a novelty.

It all comes down to the negotiating ability of the two types of modem.  The worse your connection, the more important the hardware modem is.

Here in the USA if you are on dial up it is not (probably) by choice.  It is because you are too far out to get anything else and can't afford satalite.  You have a bad connection.  You need a hardware modem.  I suspect that this is probably true in any rural and many urban dial up environments.

Probably so , even getting the serial modem to work in Ubuntu is a challenge. 
I don;t understand why, with puppy it is a no brainer.

---

### Post by frank cox on 2009-12-03
> **Bartender said:**
> I have a question for you guys.

Have any of you done enuf experimenting with Linux and softmodems vs. Linux and hardware modems to say whether a hardware modem is always going to be faster?

If the hardware modem is always going to be faster anyway, and a person has a few serial port hardware modems, then it seems to me that part of the justification for going to a distro that supports winmodems better than Ubuntu is rendered moot since I can get Ubuntu and the external working.  Does that make sense to anyone?

If, as in longtom's situation, you're dealing with lots of people who don't have external hardware modems nor access to them, then it seems the case for Puppy or similar is much stronger.

In my case, living in the U.S. and with broadband available in town, it still seems like a Windows PC with an external USR modem for home use, and a laptop with Linux when mobile, is probably pretty close to the best compromise I can cobble together at this point in time.

There is one huge advantage in using Puppy {or Ubuntu} for dialup, no viruses .
The only way to be very safe with windows on line is to login with a limited account. 
That gets to be a pain when you have to switch users and shut down the connection every time you install a program etc that requires admin privileges. 

I guess it comes down to what you do with the computer.

---

### Post by longtom on 2009-12-03
> **frank cox said:**
> There is one huge advantage in using Puppy {or Ubuntu} for dialup, no viruses .


THIS!..  Ever thought of downloading daily MB updates for your anti virus with a dial-up and what it will cost you?

Linux is a real alternative.  I still can't grab why Ubuntu basically abandoned dial-up users...just doesn't make sense.

Glad to see other distros didn't.

---

### Post by Bartender on 2009-12-03
I certainly won't argue about Windows and viruses/spyware, etc.  But I think it's fair to say that a user who's aware of the situation is probly fairly safe.
I don't use the Windows firewall, which only monitors one-way traffic.  Using Zone Alarm in XP and Comodo in Vista.
I don't use IE or Outlook Express, both of which are malware magnets.
I'm running a few anti-spyware programs as well as a free anti-virus.
There are a lot of places on the internet that I won't go.
It's just my wife and me.  If there were kids using the PC it'd be a different story!

While keeping all the anti-virus and spyware apps current is a hassle, it's nowhere near as time-consuming as the typical Ubuntu update.

Having said all that, I'll probably get a virus tomorrow ;)

I was playing with Puppy again yesterday.  Plugged it into our main XP PC (running a USR 5686 external) and booted from it.  Ran the dial-up speed test at u.s. netizen's website.  47.77 Kbps!  I've never seen 47 Kbps ever before from our house with any combination of devices.

frank cox, can you explain where you're getting hung up with your USR?  Although the Ubuntu stuff is a hassle, I've gotten  USR externals to connect with every distro for the last 3 years or so.  Maybe I can help you figure it out.

At least maybe I can help out with the basic connection.  If there's some weird problem with your ISP, that might be harder to figure out via a forum.  Wait, you said Puppy worked, right?

---

### Post by frank cox on 2009-12-05
I agree that being aware and careful make it fairly safe in windows but I hate to dual boot so I have 2 computers and a switch.;)

> I was playing with Puppy again yesterday.  Plugged it into our main XP PC (running a USR 5686 external) and booted from it.  Ran the dial-up speed test at u.s. netizen's website.  47.77 Kbps!  I've never seen 47 Kbps ever before from our house with any combination of devices.

Puppy is a great program for dial up or broadband. You plug it in and it works very well. I just wish I could say the same for dial up in Ubuntu. Of course puppy was designed for remote locations where no broadband is available. It also is a no brainer with satellite internet, I just wish satellite was not such a rip off.

> frank cox, can you explain where you're getting hung up with your USR?  Although the Ubuntu stuff is a hassle, I've gotten  USR externals to connect with every distro for the last 3 years or so.  Maybe I can help you figure it out.

To be honest, no, I can't tell you . I very much appreciate your offer but as confused as I am I think it would be easier to start all over than try and explain what has happened.
First of all I don't understand the relationship between network manager and wvdial -gnome-ppp. Do I need them both? I understand that gnome-ppp is a front in for wvdial. I thought about trying to adapt the puppy dialer to Ubuntu.

I have a copy of the Linuxtant driver for the winmodem but I have never got it to connect and let me browse so I have not put the unlock code in it. Now that I have copies of the Dell drivers I think I will cancel the Linuxtant driver as their support has been a joke. All they  really did was refer me to linmodens bulletin board and when what they suggested did not work they got frustrated and claimed I lied about following their instruction and told me I was stupid. Real ambassadors for Linux that bunch is.
The machine I need to connect with Ubuntu is a Dell 530 duo core and it has no serial port . I guess I should order a usb to serial adapter but I am afraid Ubuntu won't recognize it. I hate to buy a card because I could use the usb adapter on my laptop as well.

> 
At least maybe I can help out with the basic connection.  If there's some weird problem with your ISP, that might be harder to figure out via a forum.  Wait, you said Puppy worked, right?

I have hooked puppy through the USR external to 3 different ISP's , including the one I use at home with zero problems.  The machine with Ubuntu 9.04 is in town where I have a broadband connection but that is coming to an end. I need to bring it home. 
I tried to use the USR external on my windows machine here and it failed.
I did not think to put in a puppy flash disk in the windows machine but I have no reason to doubt it will work.

If you could  start from the beginning I think it would be easier than trying to fix the mess I made. I will go ahead and order a usb to serial adapter but I would really like to solve the windmodem problem if I can. I have some old machines I want to give away and it would save me a lot of money if I could use the Dell drivers and the windmodems. I intend to use the USR myself.

Thanks Bartender!

---

### Post by frank cox on 2009-12-05
> **longtom said:**
> THIS!..  Ever thought of downloading daily MB updates for your anti virus with a dial-up and what it will cost you?

Linux is a real alternative.  I still can't grab why Ubuntu basically abandoned dial-up users...just doesn't make sense.

Glad to see other distros didn't.

It doesn't really cost anymore if you have unlimited dial-up but it slows the computer to a crawl when it is downloading the updates. If you have a limited connection it would cost a fortune, either way is a drag.

---

### Post by ranch hand on 2009-12-05
When you get to where you have dial up, I would really recommend running;
```

sudo pppconfig

```
as the first attempt to connect with your external.  You will probably have to use pon and poff to dial but it should connect you.

Then I would go to wvdial in terminal.

You might consider while you have a faster connection, downloading Kppp.  KDE seems to be friendlier to dialup.  If you do that, it is what I would try first.

---

### Post by frank cox on 2009-12-06
> **ranch hand said:**
> When you get to where you have dial up, I would really recommend running;
```

sudo pppconfig

```as the first attempt to connect with your external.  You will probably have to use pon and poff to dial but it should connect you.

Then I would go to wvdial in terminal.

You might consider while you have a faster connection, downloading Kppp.  KDE seems to be friendlier to dialup.  If you do that, it is what I would try first.

I tried the pppconfig and it would never recognize the modem.

Do I need to download anything else? What should I do with Network Manager .wvdial-gnome-ppp, and pppconfig?

Thanks

---

### Post by ranch hand on 2009-12-06
Getting modems recognized is a problem for sure.  The only OS I have really used on dial up is Hardy and I found that pppconfig was the way to go.  I also knew where my modem was so I could tell the box where it was in pppconfig (mine is at ttyS0).

The reason I suggested kppp is that KDE distros tend to be easier to hook up to dial up.  That said, Kubuntu is the worst KDE that I have hooked up.

They have made many changes in the way this stuff is set up and I had little luck getting Intrepid to hook up.  I am not the guy to ask for advice on Jaunty.  I just wish Ubuntu would realize how many folks have to use dial up.

---

### Post by frank cox on 2009-12-07
> **ranch hand said:**
> Getting modems recognized is a problem for sure.  The only OS I have really used on dial up is Hardy and I found that pppconfig was the way to go.  I also knew where my modem was so I could tell the box where it was in pppconfig (mine is at ttyS0).

The reason I suggested kppp is that KDE distros tend to be easier to hook up to dial up.  That said, Kubuntu is the worst KDE that I have hooked up.

They have made many changes in the way this stuff is set up and I had little luck getting Intrepid to hook up.  I am not the guy to ask for advice on Jaunty.  I just wish Ubuntu would realize how many folks have to use dial up.


Well thanks for being willing . Perhaps someone else will come along and we can learn and help someone else.

---

### Post by Bartender on 2009-12-16
Hi, frank -
Sorry, I didn't bother checking this thread out for a while.  Have you read my dial-up diary?

[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

It was sort of a write-as-I-learned project. I mentioned a Sabrent serial-to-USB adapter that "just works" in Ubuntu.  Post #12, the Sabrent SBT-USC1M.  I think Newegg still has it.  The Windows drivers didn't work for me, but it's supported in the Linux kernel!

pppconfig will not recognize a USR modem automagically.  At least it never has for me.  I always had to enter it manually.  Without the Sabrent it was usually at /dev/ttyS0, with the Sabrent adapter the modem became /dev/ttyACM0.

I wanted to get it all set up with GnomePPP, but I kept finding that the connection was faster and more reliable with the good old pppconfig.

You're sure your ISP is compatible with Linux?  Oh, yeah, you said you connected with Puppy.  I was on Juno for a long time, which was horrible, but Fry's seems to work OK with Linux.

The little switches on the back of your USR - 3,5, and 8 should be "down", the rest up.

I hardly ever do dial-up at home with Linux.  Just take the Linux laptop into town.  But I can take the time to go thru the steps on a fresh install and see where your experience varies from mine.  PM me if you want and we can work on it.

---

### Post by Bartender on 2009-12-16
> **frank cox said:**
> Do I need to download anything else? What should I do with Network Manager .wvdial-gnome-ppp, and pppconfig?

The basic answer is that with a USR external (and one of those Sabrent cables if you don't have a serial port) you should be able to go online with pppconfig.  After that it's up to you whether you want to download the wvdial and gnomeppp packages.

Network manager is, as I understand it, not necessary for dial-up.  It may even get in the way!

---

### Post by frank cox on 2009-12-18
> **Bartender said:**
> Hi, frank -
Sorry, I didn't bother checking this thread out for a while.  Have you read my dial-up diary?

[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

It was sort of a write-as-I-learned project. I mentioned a Sabrent serial-to-USB adapter that "just works" in Ubuntu.  Post #12, the Sabrent SBT-USC1M.  I think Newegg still has it.  The Windows drivers didn't work for me, but it's supported in the Linux kernel!

pppconfig will not recognize a USR modem automagically.  At least it never has for me.  I always had to enter it manually.  Without the Sabrent it was usually at /dev/ttyS0, with the Sabrent adapter the modem became /dev/ttyACM0.

I wanted to get it all set up with GnomePPP, but I kept finding that the connection was faster and more reliable with the good old pppconfig.

Hey bartender:

You're sure your ISP is compatible with Linux?  Oh, yeah, you said you connected with Puppy.  I was on Juno for a long time, which was horrible, but Fry's seems to work OK with Linux.

The little switches on the back of your USR - 3,5, and 8 should be "down", the rest up.

I hardly ever do dial-up at home with Linux.  Just take the Linux laptop into town.  But I can take the time to go thru the steps on a fresh install and see where your experience varies from mine.  PM me if you want and we can work on it.


I have , for the moment given up on the linmodem idea even though I kow have Dell drivers written for the modem in my machine. I bought a usb to rs232 adapter and all I had to do was reboot, change the settings in Network and gnome-ppp and it worked fine.

I appreciate the offer but I am up and running as far as the serial modem is concerned.

---

### Post by frank cox on 2009-12-18
> **Bartender said:**
> The basic answer is that with a USR external (and one of those Sabrent cables if you don't have a serial port) you should be able to go online with pppconfig.  After that it's up to you whether you want to download the wvdial and gnomeppp packages.

Network manager is, as I understand it, not necessary for dial-up.  It may even get in the way!

I forgot to check here  before I tried the USB to rs232 adapter. Gnome-ppp found it as ttyusb0 and I typed that into network and it worked.

Thanks!

---

### Post by Bartender on 2009-12-20
Hi, frank -
I know this has been frustrating you for a long time, and glad to hear you're connected.

Seems odd that ppp found the device in a different place than mine, ttyusb0 instead of ttyACM0, but it's working and that's what counts!

---

### Post by Mike Hof on 2009-12-21
Add me to the list of having problems.

I installed 9.10 on an old computer and finally got online with an isa courier v everything modem. This modem worked perfect with pppconfig,wvdial, and gnome-ppp. The learning curve was pretty steep and documentation was hard to find.

Installed the hard drive into a fairly new compaq computer with a 3cp2976 U S Robotics hardware modem.

I have had a heck of a time getting this modem to work. i have to reboot to dial up more than one time and sometimes i have to reboot multiple times before i can get online. Something is keeping one or all of these dial up programs from shutting down. 

 Hopefully the modem issue will be over after a clean install.

---

### Post by ranch hand on 2009-12-21
Have you tried the "pon" and "poff" commands?  They should connect and disconnect you in situations like that.

---

### Post by Mike Hof on 2009-12-21
Update

Tried pon and sudo pon and it worked sometimes.

It was driving me nuts.

Did a fresh install and 30 minutes later it was working. i have connected about a dozen times and it connected every time.

I wonder if connecting with a different computer and using a different isa(pci now) modem with the same hard drive didn't change a lot of files that i don't know about.

Anyway it is working fine.

Now i just have to reload all my extras again using a modem.

---

### Post by ranch hand on 2009-12-21
By Jove, I think hes' got it.

I bet you are right. probably would have been better to track down the files and edit them but as quick as backing up  is and as quick as you can have your system up and going with Ubuntu (any flavor) your way was probably easier and faster.

Not as much FUN though.

---

### Post by Mike Hof on 2009-12-22
Fun it is but after a while some problems ain't so much fun anymore.

It does keep this old man entertained.

Downloaded updates all night and modem didn't work this morning.

15 minutes later i am back online.

One good thing about all this is i am learning and relearning.

I haven't gotten this deep into computers for several years and man has it changed.

---

### Post by ranch hand on 2009-12-22
Yes the mental exersize is needed for us grumpy geezers.

---

### Post by Mike Hof on 2009-12-22
New Update

I downloaded the right nvidia drivers (185) and now i am back to not being able to connect sometimes.

At least now i kinda know where to  look for the problem.

I hate to start over again.

---

### Post by t0p on 2009-12-22
I saw this thread resurface again, and I figured this was as good a place as any to ask my question:

Does anyone know *why* the Ubuntu devs decided not to include wvdial in the default installation?

I'm lucky - I've been able to take my netbook round to a mate's house and use his broadband to install wvdial to Ubuntu.  But if you can't do something like that, getting dial-up working with Jaunty and Karmic is a pain.  Now I'm sure the devs had a reason for leaving out wvdial... but I'd really like to know what that reason is.  Wvdial is a very small program, so I don't think the devs needed the space on the CD.  Have they just decided that dial-up doesn't exist anymore?  Do dial-up users not matter any more?  Or what?

If anyone could point me in the right direction to discover their reasoning, I'd really appreciate it.

**EDIT:** There's a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/wvdial/+bug/400573?comments=all") asking for wvdial to be included in future releases of Ubuntu.  Could anyone who wants wvdial please add comments to the bug report, reinforcing our demand that wvdial is on the CDs in future?  Thanks!

Is there an official place where Ubuntu users can post wish list items for Lucid?  So I can tell 'em to include wvdial?

---

### Post by ranch hand on 2009-12-22
I am afraid that it is too late to get something included in 10.04.  It is all pretty well settled and they do not like changing things too much on a LTS release.

I am testing 10.04 now and it is looking pretty good.  A long way to release, a lot of the changes and improvements are yet to come.

---

### Post by t0p on 2009-12-22
> **ranch hand said:**
> I am afraid that it is too late to get something included in 10.04.  It is all pretty well settled and they do not like changing things too much on a LTS release.

That's flaming ridiculous.  Would it really be too much trouble for them to add *wvdial* to it?  It's a very small binary.  And I would have thought that 10.04's LTS status would be more reason why an important program like *wvdial* should be included.

But if that's the way it is, then that's the way it is.  So how about a wishlist for 10.10?  Is there such a thing?

---

### Post by ranch hand on 2009-12-22
While I agree with your sentiment, I do not know what goes on in planning except what I read.

On any release there is a plan.  On your non-LTS releases they are a lot looser in what they will change.  The LTS is focused on stability.

The feature definition freeze was 12-03-09.  The actual feature freeze is 2-18-10.

All you have to do before then is get someone on the feature team to sponsor the app and get it approved by then.

The best way to do this is with "wish list" bugs like you pointed us to and which I left a comment on.

Wvdial is not big.  They are, however taking things off the install CD to make room for the system and new features.

The really need to go to a DVD release like Mandriva uses and has, for instance, Gnome, Lxde and KDE on it and you can install one or all of them.  There is a lot of room on a DVD.

The problem with that is there are, like folks on dial up, a lot of folks with out a DVDrom.

I don't, personally, think that wvdial is the problem here.  I am not sure what they use (I am currently, for the first time ever, on DSL) but it is damned easy to connect with Mandriva.  I may be wrong but I think you need to answer 4 (might be 3) questions during installation and you are connected.  PCLOS-gnome is the same.  I have used Kubuntu and it is easier to connect (the only thing I like about KDE is all the distros I have tried with it use some version of Kppp and it is pretty much a snap) with than Ubuntu.

There are better tools out there.  It is a matter of priorities.  Making noise is good for getting the attention of those in a position to help.

I thank you for the link to that bug.  I added my noise.  Get others to.

[https://wiki.ubuntu.com/LucidReleaseSchedule?action=show&redirect=LucidLynxSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule?action=show&redirect=LucidLynxSchedule)

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by Bartender on 2009-12-23
Instead of a DVD, it seems to me (I probably don't have the "big picture") that it would be a relatively simple matter to create an accessory CD that included lots of optional stuff that isn't a priority on the main install CD.  I mean, the technology is already there with aptonCD, isn't it?

Canonical could have the main CD download, then make available an "options" CD on the same webpages.  Seems like a simple idea, but maybe it isn't.  I'm sure it's been suggested several times.

I'm running OpenSUSE on a test PC right now.  OpenSUSE was a 4.3GB download.  Big, yeah, but once it's done a person could make copies for friends on dial-up.

---

### Post by Anticitizen2 on 2009-12-23
Hello all.  I too am trying to get a dial up modem working in ubuntu, the 9.10 version of the netbook remix to be specific(I wanted the simplified interface for the computer illiterate relative the machine in question is for).  I have tried most of the suggestions in the thread for getting a modem to dial in, but have had no luck.  The lspci command returns "Agere Systems Lucent V.92 Data/Fax Modem" as one of the communications controllers, so I believe ubuntu is detecting the PCI modem card correctly.

I have been trying use gnome-ppp to set up the connection.  In the setup window, all of the device selections say they is no modem detected if I try to detect, but if I select /dev/ttyS0 as my device and try to connect, it at least seems to try to initialize the modem and start a connection.  I would really appreciate it if I could get some advice on this matter!

Also, in the off chance it will contribute to this discussion, there is a website called [http://www.linmodems.org](http://www.linmodems.org) that seems to be dedicated to modems and linux.  They have a tool that will gather and dump a lot of information about detected modems and drivers.

Many thanks!

---

### Post by t0p on 2009-12-23
> **Anticitizen2 said:**
> Hello all.  I too am trying to get a dial up modem working in ubuntu, the 9.10 version of the netbook remix to be specific(I wanted the simplified interface for the computer illiterate relative the machine in question is for).  I have tried most of the suggestions in the thread for getting a modem to dial in, but have had no luck.  The lspci command returns "Agere Systems Lucent V.92 Data/Fax Modem" as one of the communications controllers, so I believe ubuntu is detecting the PCI modem card correctly.

I have been trying use gnome-ppp to set up the connection.  In the setup window, all of the device selections say they is no modem detected if I try to detect, but if I select /dev/ttyS0 as my device and try to connect, it at least seems to try to initialize the modem and start a connection.  I would really appreciate it if I could get some advice on this matter!

Also, in the off chance it will contribute to this discussion, there is a website called [http://www.linmodems.org](http://www.linmodems.org) that seems to be dedicated to modems and linux.  They have a tool that will gather and dump a lot of information about detected modems and drivers.

Many thanks!

I believe that your "modem" is actually a winmodem.  To get it to work, you'll need to follow your own advice and go to [www.linmodems.org]("http://www.linmodems.org").  Most winmodems don't work in Ubuntu by default - you'll need to check linmodems.org for details of your modem.

---

### Post by t0p on 2009-12-23
> **Bartender said:**
> Instead of a DVD, it seems to me (I probably don't have the "big picture") that it would be a relatively simple matter to create an accessory CD that included lots of optional stuff that isn't a priority on the main install CD.  I mean, the technology is already there with aptonCD, isn't it?

Canonical could have the main CD download, then make available an "options" CD on the same webpages.  Seems like a simple idea, but maybe it isn't.  I'm sure it's been suggested several times.


I expect it *has* been suggested many times, but that doesn't make it any less good an idea.  Unfortunately, it isn't the kind of project that Canonical would undertake, just as Canonical isn't behind AptOnCD.

But if you (or some other developer-type) wanted to create such a disk, you won't meet with any objections.  So I urge you to do it.  I'm sure you'd get many grateful users.

---

### Post by Bartender on 2009-12-23
> **Anticitizen2 said:**
> The lspci command returns "Agere Systems Lucent V.92 Data/Fax Modem" 

As ranchhand and I discussed a few pages back, even if you move heaven and earth to get one of those crappy little winmodems to work, I feel pretty sure it'll never be as fast as a good old 56K external Sportster.  

And the Sportsters are as close to "out of the box" functional as you'll find for Linux dial-up.

IMO dial-up will always be a miserable experience, largely  because of the 40 to 50 MB updates that are funneled to the end-user on a regular basis, but if you've gotta use dial-up I think expending the money and effort to find a couple of used Sportsters and a serial-to-USB adapter is your best bet.

A friend of mine gave me his old Actiontec serial modem, which is a real common external modem because AOL gave away or sold millions of these years ago.  I tested the Actiontec in Windows, not Linux, with the correct drivers from Actiontec, and it was consistently 2/3 as fast as the Sportster 5686 we use for our daily online activity.

EDIT: top, I wish I could help you but I'm just a Linux end-user.  I couldn't write a line of code if my life depended on it.

---

### Post by longtom on 2009-12-24
> **Bartender said:**
> As ranchhand and I discussed a few pages back, even if you move heaven and earth to get one of those crappy little winmodems to work, I feel pretty sure it'll never be as fast as a good old 56K external Sportster.  


While this might be true in Ubuntu, it certainly isn't the case in Puppy Linux.

So if you don't get your winmodem running in Ubuntu (I got it right once - and only once...), pop in a Puppy cd or put Puppy on a USB stick (which is what I did) and do online work from there.  I do it (mostly for others) because dial-up modems are either not readily available or the external once very expensive.

But if availability and price is not the issue, get an external modem.  I am sure bartender and ranch hand will have suggestions to make sure you get one which actually works.

Good Luck!

---

### Post by GeorgeVita on 2009-12-24
Hi to all above!

> **longtom said:**
> ...So if you don't get your winmodem running in Ubuntu (I got it right once - and only once...), pop in a Puppy cd or put Puppy on a USB stick (which is what I did) and do online work from there...

This is exactly what I am doing with my 3g modems! When I was 'testing' KK last summer Puppy managed the 'backup' connection to fix system files. As 3g modems still work with AT commands, wvdial is still a solution. Due to this, wvdial is needed for the 'high end' modems also...

Regards,
George

---

### Post by Bartender on 2009-12-24
> **longtom said:**
> While this might be true in Ubuntu, it certainly isn't the case in Puppy Linux.

Hi, longtom, my statement was admittedly a bit of an assumption.  And that assumption had nothing to do with the operating system.

It was based on the fact that a good external, like the old Sportsters, are supposed to be better at cutting thru noise on the line, negotiating the best possible speed, etc.  Plus of course they don't steal computing cycles from the CPU.

I guess it wouldn't do any good to compare your Kbps to mine, because that tells us about each user's local conditions more than the modem's best possible speed, but have you had the opportunity to compare winmodems to externals from the same PC?

You're still working in Africa, right?  Trying to help people with their computers?  Sounds like a fascinating experience!

---

### Post by longtom on 2009-12-24
> **Bartender said:**
> Hi, longtom, my statement was admittedly a bit of an assumption.  And that assumption had nothing to do with the operating system.

It was based on the fact that a good external, like the old Sportsters, are supposed to be better at cutting thru noise on the line, negotiating the best possible speed, etc.  Plus of course they don't steal computing cycles from the CPU.

Oh yes, no arguments here.  As I said, if you have a chance to get a decent external modem don't even think about the winmodem any more.

But if not - see above.

> 
You're still working in Africa, right?  Trying to help people with their computers?  Sounds like a fascinating experience!

I am living, working, loving and all other things in Africa indeed, for many years.  It is fascinating indeed - sometimes a bit tiring, but still fascinating.

---

### Post by Anticitizen2 on 2009-12-24
> **t0p said:**
> I believe that your "modem" is actually a winmodem.  To get it to work, you'll need to follow your own advice and go to [www.linmodems.org]("http://www.linmodems.org").  Most winmodems don't work in Ubuntu by default - you'll need to check linmodems.org for details of your modem.

Thanks for the reply!  The problem with linmodems.org is that the site is so old that some of its pages no longer exist, but I will see what I can dig up.

---

### Post by Mike Hof on 2009-12-25
Ranch Hand you were right.

I should have  tried harder to figure out what was wrong.

After doing a fresh install i still had the same modem errors.

The problem wasn't with pppconfig, wvdial, or gnome-ppp it was Modem Manager.I think it was tying up the modem during boot up.

I removed Modem Manager , rebooted, the modem errors disappeared and I no longer have to dial out as root.

Now it just works!

---

### Post by ranch hand on 2009-12-25
That is very interesting.  I have not used dial up, regularly except in Hardy and a little in Intrepid (had three installs on the same box and could only get one to connect) but I do not remember having a "Modem Manager".

I am on 10.04-testing (they call it Lucid Lynx, I prefer Lounge Lizard) and it sure has a Modem Manager.

When I get another remote ranch job is will surely remove the bugger.  Thanks.

I think I will also hang on to my Hardy installation.

---

### Post by Mike Hof on 2009-12-25
If I remember correctly what I read, Modem Manager didn't come out until 9.10

---

### Post by ranch hand on 2009-12-25
Ah, that would explain it, I have been on DSL since Jaunty came out.

---

### Post by Bartender on 2009-12-25
Hey, fellers -
This is in regards to updating the dial-up home PC via a broadband Ubuntu PC.  I recently found an old forum thread I'd printed out but never followed thru with it.  I'll paste the applicable part:

On the dial-up PC:
1)Insert USB drive.
2)Go online
3)Start Synaptic
4)Go to Edit>Reload Package Information
5)Edit>Mark All Upgrades
6)File>Generate Package Download Script, name the file and save to the USB drive.

On fast PC:
1)Insert USB drive
2)Open terminal and enter:
3)cd/media/ <USB drive name>
4)source <filename that you saved to above>

Back to the dial-up PC:
1)Open terminal and enter:
2)cd/var/cache/apt/archives
3)sudo cp /media/ <USB drive name>/* ./
4)start Software Updates (the orange star icon)
5)click Install Updates.

OK, found the old post:

[http://ubuntuforums.org/showthread.php?t=461218](http://ubuntuforums.org/showthread.php?t=461218)

I tried the first part, but haven't been able to go any further cause it's Xmas day and the library's closed.

Got a question for the group: in the third part of the instructions, he describes the "orange star icon"?  Anybody know what he's talking about there?  I assumed he had gone back to Synaptic but didn't find the Software Updates icon or button like he described.

There's also [this]("https://help.ubuntu.com/community/InstallingSoftware")

I'll quote:

[COLOR="Blue"]Use the Synaptic package download script

Here's how: Synaptic/PackageDownloadScript

Short instructions:

    * Launch Synaptic on the offline computer
    * Mark the packages you wish to install
    * Select File->Generate package download script
    * Save the script to your USB key
    * Take the USB key to an online Linux computer and run the script there from the USB key. It will download only the packages required by the offline computer to the USB key.
    * Insert the USB key into the offline computer
    * Launch Synaptic and click on File->Add downloaded packages
    * Select the directory on your USB key containing the downloaded *.deb files and press Open. The packages will be installed.
[/COLOR]
Sounds very similar to the first set of directions, eh?  Anyway, I'm gonna try both, or at least the second one, ASAP.  This will be done with a desktop running 9.04, and a laptop also running 9.04.  I doubt this works unless it's the same OS on both PC's...

---

### Post by Bartender on 2009-12-26
I went to the library today and didn't have any luck.  Tried the very first instructions, which only downloaded 9 of the dozens and dozens of packages.  I'd also generated another download script using the instructions from Ubuntu Docs and that script didn't work at all.  The script was only a few bytes so I may have done something wrong.  Will try again.

EDIT:  I think I figured out what I did wrong to make the 10 byte package download scripts.  I forgot to "Mark All Upgrades" before creating the script.  Now the script is 28KB.  It'll take a few days to try again in town.

On another tangent, has anyone messed with init strings?  I still don't understand them.  I ran the modem query in XP and printed out the log, then rebooted into Ubuntu and went into gnome-ppp.  I was thinking of trying to add some of the init strings from the Windows modem query.  

gnome-ppp shows one line of init strings.  When I tried to modify that line, it let me, but as soon as I closed and came back the init string was the same as before.  I'm pretty sure you're supposed to be able to modify and add strings in gnome-ppp, aren't you?  Or does this have to be done from CLI?  I don't know where that would be done.

I got ppp-config working (pon and poff from terminal to run the modem then turn it off) then downloaded wvdial and gnome-ppp.  I didn't mess with wvdial, just went right to gnome-ppp and set it up.  This is on Ubuntu 9.04 with a USR 5686 external.

I use the dial-up speed test at us netizen website to check speed.  I get about 40 to 41 Kbps in Ubuntu, which is pretty much identical to Windows XP.  But web browsing definitely feels more sluggish in Ubuntu and I'm trying to figure out why.  Maybe the init string (s) has something to do with it...

---

### Post by Twitch04 on 2009-12-26
I don't run Jaunty, I run Karmic, but I have dial up [dual-booting with XP right now] and I, too, find the lack of support insulting. You'd think that with more improved versions, they could only increase the support... I'm only 17 so I have to live where my parents live until I move out and go to college. Until then, I'm stuck out in the boonies where we can't get DSL or cable, and satellite is ridiculously overpriced.

I'm trying to get my dial-up to work with gnome-ppp, but I use the AOL Dialer in XP and it's not quite working. I made a topic about it in Networking & Wireless, but have yet to get a reply [it's only been about 20 minutes]. 

I swear, I'll find a way, haha. So far the problem is that it told me [in the terminal] that I used a bad password or username, but... I'm not sure if the number matters. I'm using one of the numbers I use with the AOL Dialer in XP and I'm not sure if that number will only work if I'm using the AOL Dialer.

---

### Post by GeorgeVita on 2009-12-27
> **Bartender said:**
> ...gnome-ppp shows one line of init strings.  When I tried to modify that line, it let me, but as soon as I closed and came back the init string was the same as before.  I'm pretty sure you're supposed to be able to modify and add strings in gnome-ppp, aren't you?...
Hi **Bartender**, to change init strings:
- run Gnome-PPP
- click 'Setup'
- at 'Modem' tab click 'Init Strings'
- click into any line to change or add (click a second time in existing line to see the cursor)
- move cursor and edit or type to add a new init string (each line must start with 'AT')
- after edit/addition press <ENTER> key to accept changes
(ex. move to first line after 'E1' add ' L3' and press <ENTER>)
- click 'close'
- check them by pressing again 'Init Strings'

Also note that when trying to connect you can press 'Log' to see the current try (commands and responses).

Most times you must tick 'Ignore terminal strings (stupid mode)' at options tab.

Regards,
George

P.S. history: reading [this]("http://ubuntuforums.org/showpost.php?p=7785980&postcount=20") I forced to manage [that]("http://ubuntuforums.org/showpost.php?p=8115225&postcount=25") thanks!

---

### Post by Bartender on 2009-12-27
Hi, George -
Thanks for the tips.  I'll give it a shot later today, but as I said I was unable to make any changes stick and what you describe sounds pretty much like what I was doing.  

Twitch04, tell you what, there are a lot worse things than living with your parents.  Enjoy it while you can.  Isn't AOL out of the ISP business?  I thought they didn't provide dial-up ISP any more.  I guarantee you that trying to connect in Linux using an ISP that insists on its own proprietary Windows-based software is an exercise in futility.

If your parents are on a proprietary ISP, like Juno or AOL or PeoplePC, would it be a real uphill battle to get them to change to an ISP that just provides basic internet connect without any proprietary software?  Frys.com and copper.net are two that I know work with Linux.  Actually, most ISP's these days do but some of the big players don't and there's nothing the Linux user can do about that except to go shopping.

If they squawk about their email because they're using the ISP's POP servers for their email, get them started with gmail addresses and keep pushing them to move their contacts to gmail.

When I first got into Linux I was using Juno, with a Juno email address.  I could dial into Juno but they would kick me off after a few minutes.  I dumped Juno for Frys, started a gmail account, and got everything moved to gmail.  Dial-up is still a horrible experience, but at least I can connect.

---

### Post by ranch hand on 2009-12-27
Boy, that does sound like a hassle.  My last dial up was direct from our telephone coop just as the DSL is.  They don't care what you hook up as long as they don't have to supply support.  The only support they can give is for manufacturer supported MS and Mac OS'.

It was fun when they came to hook up the DSL with their little disks of drivers and such.  The guys just stood there and gawked as I fired up and was instantly connected.

As for your Gppp and getting settings to stick - are you doing this as "root"?

---

### Post by Bartender on 2009-12-28
> **ranch hand said:**
> As for your Gppp and getting settings to stick - are you doing this as "root"?

Um, good question, ranch.  I've never been clear on the whole 'root' thing.  I mean, I understand using sudo when in the terminal.  As far as what I described above, I just opened the Gnome-PPP GUI, went to Configure, then clicked on Init strings.

I still haven't tried changing them, but I should post what Gnome-PPP says it's using.

I'll add an attachment so we're sure everyone's on the same page.  This is the init window that keeps reverting back to the values shown.  I didn't try adding another string, just tried to modify this one.  I'm sure there are some folks who understand init strings backwards and forwards, but by now most of them are probly using broadband!

---

### Post by GeorgeVita on 2009-12-28
Hi **Bartender**,

from: [http://www.usr.com/support/5686e/5686e-ug/tech-ref.html](http://www.usr.com/support/5686e/5686e-ug/tech-ref.html)

Your init string is the 'linux default': **ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0**

**Q0** displays result codes (like OK, ERROR)
**V1** in verbal mode (OK instead of 1, ERROR instead of 0/-1)
**E1** echo=on (any character received by modem is echoed back to the modem port)
**S0=0** auto answer disabled (other values hook up automatically after n rings)
**&C1 &D2** both enable h/w handshaking with the pc
**+FCLASS=0** voice mode (and not fax)

Regards,
George

---

### Post by Bartender on 2009-12-28
George, thanks, I wasn't hitting the "Enter" key.  Thanks for the info on the "linux default".  I was wondering where that came from - if Gnome-ppp got that from the modem, or what.
I found a 3 page list of US Robotics init strings from a website called ModemHelp.org

[http://www.modemhelp.org/inits/usrobotics.html](http://www.modemhelp.org/inits/usrobotics.html)

The listing seems to be oriented towards what you want to do with the modem, rather than offering a "best" init string for each model.  I have a USR 5686E.  I tried s32=66 (listed on page 3) but it wouldn't even connect so I went back to the linux default.

I feel pretty certain that I could get the modem working a little better with the right init string (or strings) but don't know what that would be.

Is there a way that you know of to get the init strings that Windows is using?

---

### Post by GeorgeVita on 2009-12-28
> **Bartender said:**
> Is there a way that you know of to get the init strings that Windows is using? Yes! You have to enable 'log file' from:
control panel > modems & telephony (or dialling?) > modem tab > properties > diagnostics
enable log file, try a connection and come back to see contents of the log file.

'default' for developers is something that works. This 'default' is very old. I prefer to use **AT&F** which restores everything to 'factory defaults' just to have a specific and stable starting point and then use other commands which I understand for setting up my modem. There are some commands used in parallel with pppd settings that are 'provider specific' and I am not familiar. Those settings can be extracted from 'win log files'.

G

---

### Post by Bartender on 2009-12-28
Hi, George -
I'd read a couple of old dial-up posts where somebody said they ran a USR external with no init strings at all.  Of course, impossible to say whether that's what the person really did, or that he/she didn't add any to the "linux default".

Anyway, I removed the linux default and left it blank.  Forgot to "Enter" it again so had to go back.  

Oh, yeah, for anyone who's following this, just copy/paste the linux default init string to an OpenOffice or Abiword document and save it.  That way you can always drop the default back into place.  

So anyway, I just checked my dial-up connection with no init strings at all in Gnome-ppp at my favorite website (us netizen) and got 45 Kbps.  That's the fastest I've ever seen for Ubuntu, and is as good or better than I've ever seen from XP.

Would you suggest at least entering the AT&F command?  I have no idea if there are drawbacks to no init strings at all.

---

### Post by ranch hand on 2009-12-28
I have never used Gppp and I do not know how you open it, but if you are not giving a password to get in it is not likely to stick.

If you are giving a password and it is not sticking I would try opening it in terminal using " sudo".

The "root thing" is that you are a god.  Most, if not all, other Linux OS' require that you have a root password.  Ubuntu does not do that because you can do anything to your system in "root" and this includes completely destroying your system (remove your kernel or all xorg stuff).

Ubuntu lets you into this mode, generally for a single purpose, with "sudo".  Debian lets you, in terminal to "su" and do everything as "root" after giving your "root" password (different than the user password).

To be more simple, the user has control over the "tree" part of the OS, the part above ground.  The "Super User" (su) controls the "roots" part of the OS, the part underground that you never see.

If you are not using "root" powers to change basic, OS controlling, things you are not going to succeed.

You may also want to check System>Administration>Users and Groups and make sure that you have permission to administer the modem.  When you click on the U+G it will come up and you will have to "unlock" it (enter it as "root").

---

### Post by GeorgeVita on 2009-12-28
Hi **ranch hand**, as **Bartender** can dial out it is not a 'privileges' subject but this is most times the problem with new dial up (or 3g) users who try to setup a 'non Ubuntu compatible' modem and try Gnome-PPP or wvdial for their first time.

**Bartender** why do you feel that 42-45Kbps is not 'enough' for your modem? Can you get more using win?

G

---

### Post by Bartender on 2009-12-28
Hiya, ranch -

I've only dabbled with other Linux OS'es, so the Ubuntu "sudo" model is all I've had to do.

GnomePPP is just a GUI frontend for - um - wvdial, I think.  Yeah, that's it.

My SOE was: 
Configure the USR 5686 in pppconfig, get online, download wvdial and Gnome-PPP.  I then skipped past manually configuring wvdial, and instead set things up in Gnome-ppp.  It's working.  George pointed out the simple mistake I was making and now I'm able to change init strings.

One thing that kind of puzzles me is that I went into terminal and called up wvdial.conf.  It's blank.  If Gnome-ppp is a graphical front-end for wvdial, I was expecting wvdial.conf to have some entries after I'd set up Gnome-ppp.  This is one of those little mysteries that makes Linux so - "interesting" :)

Oh, hey, did I mention that I found a fix for Firefox opening in offline mode?  
Go to about:config, find toolkit.networkmanager.disable and set it to “true”.  Has worked reliably so far thru several restarts, etc.

---

### Post by ranch hand on 2009-12-28
If I remember right the information that you edit goes in 2 or 3 files.  I think that they are "hidden" files in your "home" directory.

I had a hard time with the off line crap with FF back in Hardy from before they put in that option.  I still get bug updates on it.  That option really made life better.  Having to change to "online" every time you opened FF was a pain.

---

### Post by ranch hand on 2009-12-28
> **GeorgeVita said:**
> Hi **ranch hand**, as **Bartender** can dial out it is not a 'privileges' subject but this is most times the problem with new dial up (or 3g) users who try to setup a 'non Ubuntu compatible' modem and try Gnome-PPP or wvdial for their first time.

**Bartender** why do you feel that 42-45Kbps is not 'enough' for your modem? Can you get more using win?

G
You are certainly right.  Not enough sleep last night.  Sorry.

Good thing that others watch out for us grumpy geezers.

---

### Post by Bartender on 2009-12-28
> **GeorgeVita said:**
> why do you feel that 42-45Kbps is not 'enough' for your modem? Can you get more using win?

Hi, George, I have a 2-part answer for you.

#1 What I was experiencing was roughly equivalent results at the us netizen speedtest website in Ubuntu and in XP.  In either OS I would get right around 40 Kbps.  

However, the subjective experience when browsing around could not be denied - Ubuntu "felt" slower, even after visiting the same sites several times.  I don't know how cache works in Linux but assume it's there somewhere (?)

#2 Since I've just recently gotten dual-monitors to work in Ubuntu, I'm once again on a mission to see if most, if not all, daily Internet activities can be carried out in Ubuntu instead of XP.  So that's what started this recent push to figure out init strings and such.  If I can just get Ubuntu to feel roughly as quick as XP when browsing and emailing, then XP will be used as little as possible online.

So, short answer to your question, I believe that 42 to 45 KBps is as good as we're gonna get on this rural road, and no, XP wasn't reporting better than 42 or so but it felt snappier than Ubuntu, sometimes by quite a bit.  It's too soon to say for sure but I think we might be onto something with these init string tweaks.

Now if I can just figure out a way to keep Ubuntu updated.  Update Manager says I have 225 MB to download.  Cripes.  But XP is boxing me in too, saying I "need" the .NET framework download (60+MB) before I can get the rest of the XP security patches.  Looks like I'll be lugging the whole dang PC over to a friends' house with broadband.  I try to do that as seldom as possible...

---

### Post by t0p on 2009-12-28
> **longtom said:**
> So if you don't get your winmodem running in Ubuntu (I got it right once - and only once...), pop in a Puppy cd or put Puppy on a USB stick (which is what I did) and do online work from there.  I do it (mostly for others) because dial-up modems are either not readily available or the external once very expensive.


So if winmodems work with Puppy, why don't they work with Ubuntu?  Isn't it possible to transfer Puppy's drivers or whatever to Ubuntu?  If not, why not?

PS Allow me to take this opportunity to ask you all to add comments to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/wvdial/+bug/400573?comments=all") requesting that *wvdial* is included in future versions of Ubuntu.  Please.

---

### Post by GeorgeVita on 2009-12-28
@Bartender
I also have some 'bad' thoughts about firefox or my graphics card (that makes pages seem slower). Using [Puppy Linux 4.3.1]("http://ftp.nluug.nl/ftp/pub/os/Linux/distr/puppylinux/puppy-4.3.1/pup-431.iso") I can browse faster possibly due to the 'lighter' environment (not Gnome) and other version of firefox.
>>> I feel that the problem is the same as with 'through away wvdial'.
>>> Developers are using ethernet, broadband and quad core intel!

Other 'extreme electrical' test: As dial up modems are using audio signals, which can reach a theoretical maximum of 56Kbps (if your provider and local network can do it), you could try/check a better electrical connection closer to the PTT junction box with less cable. If you succeed a better speed, you can try to replace the telephone cable (usually twisted pair) from the PTT junction box to the modem. Maybe 'lot of trouble' for some bits per second ...

>>> Assume that your baud rate setting (Gnome-PPP or wvdial.conf) is greater than 53200!

G

---

### Post by ranch hand on 2009-12-28
When I was on dial up I would pick and choose the updates (easier in synaptic than update mangler) and try for about 8 hrs worth.  Looks like you have about 22.5 hours worth for Ubuntu.

The MS stuff could take as long.  Their updates take forever.

I just picked the stuff and let it run while I slept.  In the morning I would pick more and go to feeding cows, checking water, all the usual stuff.  Check it if I got in for lunch.  Use it in the evening and start the cycle over.  Just do not reboot or shut down until done and it works fine.

---

### Post by Bartender on 2009-12-28
Wow, your dial-up provider was reliable _and_ forgiving!  I get booted off after a coupla hours at best.  "update mangler", I got a laugh outta that...

George, the wiring from the network interface box (the box on the side of the house where problems switch from Qwest's responsibility to ours)is only about seven years old.  I ran all new wire at that time, using the heaviest gauge I could find at the nearby supplier's, from the NIB to the PC about 40 feet away.  So I doubt there's much to be gained there.

---

### Post by ranch hand on 2009-12-28
I really like the USR5610c internal even if it was a real pain to connect.  Very aggressive and, if cut off, reconnected, undoubtedly kicking some poor sap off that has a "winmodem".

Synaptic and particularly apt are great at dealing with cut offs.  They start over, but everything previously downloaded is cached so it is no biggy they just pick it up.  Now after the third restart they do just quit.

I do not now, nor have I ever, trusted UM to do anything but screw up something.  I like the name Update Mangler.

But I have a thing for the names in Ubuntu anyway.  9.10 should have been Kinky Kitty and 10.04 should really be Lounge Lizard.  I advocated Lusty Limpid but another feller came up with Lounge Lizard.  I love it.

If you use Update Mangler on pre-release/testing OS'. like Lounge Lizard, your breakage will be much (MUCH) higher than the breakage that those of us that use apt or synaptic get.

I would never use it to upgrade from on release to a newer one.  The folks that did that for 9.04>9.10 had way more trouble and wasted way more time than those silly folks that edit the sources list and use apt.

---

### Post by Bartender on 2009-12-28
OK, I went over to the Windows side of our dual-boot and took a look at the log under Modem>USRobotics>Properties.  It looks like it stores the log of the last time that it connected.  Here's a copy of the pertinent part.  I'm hoping George Vita, who seems to have an understanding of these pesky init strings, can tell me what he thinks 

```
12-28-2009 13:28:20.062 - Initializing modem.
12-28-2009 13:28:20.078 - Send: AT<cr>
12-28-2009 13:28:20.078 - Recv: AT<cr>
12-28-2009 13:28:20.078 - Command Echo
12-28-2009 13:28:20.203 - Recv: <cr><lf>OK<cr><lf>
12-28-2009 13:28:20.203 - Interpreted response: OK
12-28-2009 13:28:20.218 - Send: AT&F1E0Q0V1&C1&D2S0=0<cr>
12-28-2009 13:28:20.218 - Recv: AT&F1E0Q0V1&C1&D2S0=0<cr>
12-28-2009 13:28:20.218 - Command Echo
12-28-2009 13:28:20.343 - Recv: <cr><lf>OK<cr><lf>
12-28-2009 13:28:20.343 - Interpreted response: OK
12-28-2009 13:28:20.359 - Send: ATS7=60S19=0M1&M4&K1&H1&R2&I0B0X4<cr>
12-28-2009 13:28:20.484 - Recv: <cr><lf>OK<cr><lf>
12-28-2009 13:28:20.484 - Interpreted response: OK
12-28-2009 13:28:20.484 - Waiting for a call.
12-28-2009 13:28:20.500 - Send: AT#CID=1<cr>
12-28-2009 13:28:20.625 - Recv: <cr><lf>OK<cr><lf>
12-28-2009 13:28:20.625 - Interpreted response: OK
12-28-2009 13:28:20.640 - Send: ATS0=0<cr>
12-28-2009 13:28:20.765 - Recv: <cr><lf>OK<cr><lf>
12-28-2009 13:28:20.765 - Interpreted response: OK
12-28-2009 13:28:20.765 - 115200,8,N,1, ctsfl=1, rtsctl=2
12-28-2009 13:28:20.765 - Initializing modem.
12-28-2009 13:28:20.781 - Send: AT<cr>
12-28-2009 13:28:20.906 - Recv: <cr><lf>OK<cr><lf>
12-28-2009 13:28:20.906 - Interpreted response: OK
12-28-2009 13:28:20.921 - Send: AT&F1E0Q0V1&C1&D2S0=0<cr>
12-28-2009 13:28:21.046 - Recv: <cr><lf>OK<cr><lf>
12-28-2009 13:28:21.046 - Interpreted response: OK
12-28-2009 13:28:21.062 - Send: ATS7=60S19=0M1&M4&K1&H1&R2&I0B0X4<cr>
12-28-2009 13:28:21.187 - Recv: <cr><lf>OK<cr><lf>
12-28-2009 13:28:21.187 - Interpreted response: OK
12-28-2009 13:28:21.187 - Dialing.
12-28-2009 13:28:21.203 - Send: ATDT*##,#######<cr>
12-28-2009 13:29:05.765 - Recv: <cr><lf>CONNECT 42666/ARQ/V92/LAPM/V42BIS<cr><lf>
12-28-2009 13:29:05.765 - Interpreted response: Connect
12-28-2009 13:29:05.765 - Connection established at 42666bps.
```

I see several lines of code that look like init strings but I'm not sure what if anything I should do with them.  

Comes down to it, I don't know who or what decided these were the ones I should be using in Windows!

---

### Post by ranch hand on 2009-12-28
Those are probably from USR.  They have a very nice install disk that comes with them if you get a new one.  It even has instructions for Linux.

That is for the internals anyway.  The externals my well have it built into the firmware.  You could check your modem at their site.  They may have an update.

Frankly I think that MS limits the performance of modems to make winmodems look better.

I got my modem for this box when we had Vista on it still.  Used the install disk and everything.  4.2 was peak performance on a good day.  Usually ran about 3.5 to 3.8.

Fought with getting the thing going in Hardy but when I got it going the peak was around 5 and the normal range was 4 to 4.4.  It would run for hours at an average of 4.4.

No install disk or anything.  I never set anything except the connection settings.

---

### Post by longtom on 2009-12-29
> **t0p said:**
> So if winmodems work with Puppy, why don't they work with Ubuntu?  Isn't it possible to transfer Puppy's drivers or whatever to Ubuntu?  If not, why not?


This is a very good question.  I never tried and to be honest, I probably do not have the knowledge to do it either.  Maybe it has to do with licenses or the foss philosophy or anything in that vein.

However, a "How to" to copy information from Puppy to Ubuntu or edit the decisive files in Ubuntu that they read the same way Puppy's do would be great.

---

### Post by ranch hand on 2009-12-29
What kind of package does puppy use (.deb, rpm, etc)?

---

### Post by GeorgeVita on 2009-12-29
Hi **Bartender**,
the easy way is to accept these init strings as more 'typical' for your modem and use them. Go to Gnome-PPP > Setup > Modem tab > Init Strings
click into Init2 field, edit contents to: ```
AT&F1E0Q0V1&C1&D2S0=0
``` **press <enter> key** to accept changes! Click into Init3 field, type new contents: ```
ATS7=60S19=0M1&M4&K1&H1&R2&I0B0X4
``` press <enter>, click 'close' and try to connect.
Note: 'linux default' Init1 is **ATZ** (soft reset of the modem)

>>> most of commands are the defaults using AT&F1 (for USR modems), all info from [here]("http://www.usr.com/support/5686e/5686e-ug/tech-ref.html")
**&F1** restore factory settings for 'Hardware flow control template'
**E0** echo disabled
**Q0** display result codes
**V1** in verbal mode
**&C1 &D2** use h/w handshake (already used from &F1)
**S0=0** auto answer disabled
**S7=60** wait 60 seconds for carrier 
**S19=0** disable inactivity timer (if used disconnects when no data trafic for x minutes)
**M1** speaker ON until CONNECT
**&M4** normal error control
**&K1** auto enable/disable data compression
**&H1** h/w flow control (CTS)
**&R2** received Data to computer only on RTS
**&I0** software flow control disabled
**B0** ITU-T answer sequence (?)
**X4** 'full' result codes (report anything)


**For new readers of this thread ('in topic'):** we are using **wvdial** and **Gnome-PPP** programs to connect our dial up or 3g UMTS/HSDPA modems to internet. **Some modems are not yet 'compatible' with  Ubuntu** (9.04+). These programs are not included by default and must be downloaded via other internet connection which is a [**bug**]("https://bugs.launchpad.net/bugs/400573")!

Regards,
George

---

### Post by longtom on 2009-12-29
> **ranch hand said:**
> What kind of package does puppy use (.deb, rpm, etc)?

They use their own package system and have an exiting new development using rpm as well as deb files.  But that is still in developing phase.

As far as the modems are concerned no extra packages needed to be installed.

---

### Post by Bartender on 2009-12-29
George, thanks very much for taking the time to diagnose the Windows log file.  I'll make the changes and report back.

Re: puppy, here's a link to me asking dumb questions over at the Puppy forums. 

[http://www.murga-linux.com/puppy/viewtopic.php?t=49556](http://www.murga-linux.com/puppy/viewtopic.php?t=49556)

If you go to the tail end of the thread, you'll see directions for a different Puppy download.  The standard pup download has fewer modem drivers than the one referred to in this thread.  This is one of the differences with pup that seems strange coming from a "mainline" distro.  There are several customized Puppy distros.  

So if you're going to do some experimenting with pup I'd suggest using the alternate download with expanded modem support.

---

### Post by ranch hand on 2009-12-29
> **longtom said:**
> They use their own package system and have an exiting new development using rpm as well as deb files.  But that is still in developing phase.

As far as the modems are concerned no extra packages needed to be installed.

So you should be able to get their packages for modems and use "alien" to help install them, neat.

I have never looked at Pup.  I have used Damn Small Linux.

---

### Post by GeorgeVita on 2009-12-29
> **ranch hand said:**
> I have never looked at Pup.
... 'sudo apt-get update' needs around 11 MBytes of download, [Puppy 4.3.1 iso]("http://ftp.nluug.nl/ftp/pub/os/Linux/distr/puppylinux/puppy-4.3.1/pup-431.iso") is 105 MBytes. How to get a 3g modem working? [1]("http://www.acomelectronics.com/GeorgeVita/p431_3g_1.jpg") [2]("http://www.acomelectronics.com/GeorgeVita/p431_3g_2.jpg") [3]("http://www.acomelectronics.com/GeorgeVita/p431_3g_3.jpg")

!

---

### Post by Bartender on 2009-12-29
OK, fellers, round two of the "update offline" experiment.  I'm trying to duplicate the [COLOR="Blue"]blue instructions[/COLOR] in post #132 of this thread.  

On the dial-up desktop PC at home I asked Synaptic to reload.  Then I "marked" all the packages.  Clicked on "Create Download Script" or whatever it's called under "File".  Saved that script to a 4GB thumbdrive.  

I'm at the library now with the laptop.  Plugged in the thumbdrive, double-clicked on the icon representing the script.  There's a truckload of packages downloading.

Will report back later after attempting to give the dial-up desktop PC an injection of new data.

UPDATE

It worked!!  For the first time since I started screwing around with Linux (Breezy Badger) I have an up-to-date desktop Ubuntu PC behind a dial-up connection.  This was much easier than Keryx, and it worked.  Last time I tried Keryx it failed to identify all the packages and apt-get got stuck.  It's a little bit embarrassing that I didn't know about a feature that's been available for a while.  I'm not the only one; I've read several posts in the last few months about updating an offline PC and never heard a hint about the offline script.

Next thing to try out is getting some optional packages.

---

### Post by longtom on 2009-12-30
That is great to hear.  I'll do a test myself and report tomorrow.  Can't believe it is so easy.  Must have over read your post 132...:oops:

---

### Post by Bartender on 2009-12-30
Hey, longtom -
I'm trying to think of the complications imposed by your situation.  The online Linux PC needs wget.  I think that's as simple as 

```
sudo apt-get wget
```

That's one of the bits that Keryx needed too, so I already had it on the laptop.  I could be wrong about this, wget may be in the default install.

Also, both our laptop and the at-home desktop are running 9.04.  I don't know if this will work in your situation if you're dealing with a mish-mash of PC's running several different versions of Ubuntu.  I'd sure suggest doing your first test with two PC's running the same version, then going from there.

Since I had a smattering of other files on the thumbdrive, I made a new folder and called it "Packages".  All the downloads were saved to that folder.  Since all navigation is within the Nautilus GUI this adds very little complication to the process.  You won't have to type in terminal commands to get where you need to be.

On the laptop, the one connected to broadband, there was no notification when the downloading of packages was finished.  So I just surfed around for a bit until I was quite sure there were no new files going to the thumb drive.

Back at the desktop, when I asked Synaptic to "Add Downloaded Packages", then navigated to the correct folder on the thumbdrive and clicked "Open", nothing happened for at least 20 seconds.  Synaptic even faded to that dark scheme that you get when the computer's thinking or stuck.  Suddenly things started happening.  So be patient - depending on the speed of the computer and the USB interface it might take a bit.  I don't know what sort of PC's you're dealing with in Africa but guessing some of them might be USB 1.1 instead of USB 2?

Good luck, and hope to hear that you had success!

---

### Post by frank cox on 2009-12-31
> **Bartender said:**
> Wow, your dial-up provider was reliable _and_ forgiving!  I get booted off after a coupla hours at best.  "update mangler", I got a laugh outta that...

George, the wiring from the network interface box (the box on the side of the house where problems switch from Qwest's responsibility to ours)is only about seven years old.  I ran all new wire at that time, using the heaviest gauge I could find at the nearby supplier's, from the NIB to the PC about 40 feet away.  So I doubt there's much to be gained there.


I have been using Natblast.com  81.00 per year and no knockoffs!

---

### Post by frank cox on 2009-12-31
I love Puppy Linux. Highly recommend you trade the default browser-sea Monkey, for FireDog. Follow the directions to remove Sea Monkey.  It works great on a USB stick and so far has recogmnized all but one of the winmodems  modems I tried it on and 4 of them work perfect with the drivers already there in the install!

One thing I have learned is NetWork Manager is no friend to Ubuntu Dial Up users. I removed it and the dial up works on a USB to serial adapter on a USR Sporster external.
I have not tried the Dell drivers or the modems puppy found yet but I have a feeling it will work on the winmodems as well.

Believe it or noot I can tell little difference on puppy between the winmodems and the external.

---

### Post by t0p on 2009-12-31
> **Bartender said:**
>  It's a little bit embarrassing that I didn't know about a feature that's been available for a while.  I'm not the only one; I've read several posts in the last few months about updating an offline PC and never heard a hint about the offline script.


Me too.  How long has this "create download script" option been in Synaptic?  I've noticed it before, but never gave any thought to what it might be for.  And I've so many posters in these forums asking how to download updates on another computer for their offline box.  I've made suggestions like AptOnCD, when a simpler solution was near to hand.  Oh my.

---

### Post by Bartender on 2009-12-31
Hi, top -
I'm glad I'm not the only one who feels a bit silly about this...

I included a few links that talka bout various ways to try and get packages offline.  They all get more complicated pretty quickly.  Let's call the computer that does have access to broadband PC "A", and the computer that's stuck in some God-forsaken part of the world (such as my rural road) without broadband PC "B".  

If you look at these instructions, you'll see guidance for how to transfer packages to PC "B" if it's completely off-line.  In other words, you can't even get a decent dial-up connection so that you can at least click the "Reload" button and get the list of packages the PC wants.  Those instructions quickly head into "I don't think I understand what they're saying" territory for me.

But as long as you can get a decent dial-up connection, and PC "A" is running the same Linux OS as PC "B", the instructions were so simple that even I only screwed it up twice! :P

[https://help.ubuntu.com/community/Synaptic/Offline](https://help.ubuntu.com/community/Synaptic/Offline)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

It's a little bit ironic, but the fastest way to test this would be if you HAD broadband at home, and two PC's.  You would plug a thumb drive into PC "B", go online, Reload, Mark the packages, save the Download Script to the thumb drive, then close Synaptic and unplug PC "B" from the internet.  Eject the thumb drive, turn to PC "A", run the script, get the packages, eject the thumb drive, and bring it back to PC "B".  

It took me several days, what with the holidays and failed attempts (I forgot to Mark the packages before creating the Download Script).  With a broadband connection at home I could have learned what I needed to learn in a few hours.

I wonder how longtom is doing??

---

### Post by Bartender on 2009-12-31
> **frank cox said:**
> I have been using Natblast.com  81.00 per year and no knockoffs!

Hi, frank -
Gotta couple of questions for you.  First, re: natblast, I've never heard of them.  They have two phone numbers listed that are local for us.  The price is within a few bucks of Frys.com if not the exact same.  I realize there are no guarantees with this sort of thing, but would you say they've got your stamp of approval?

Second, re; Puppy.  Are you running the stock-standard pup, or did you download the one with more winmodem drivers, or did you maybe install the standard version then manually download more drivers?

This has been an interesting couple of weeks for me.  I'd decided months ago that Linux and dial-up were a complete write-off, but suddenly I'm using Linux more than XP on our main PC!!

---

### Post by GeorgeVita on 2009-12-31
Hi again!

... and this way is 'distro-independent' as the created script has the full link for the .deb files to be downloaded (including dependencies). Just **wget** must be installed. I checked above using puppy booted from microSD card (was into my ZTE MF636 modem), connected, run script, download completed, boot Ubuntu 9.04 (from SDHC card) run synaptic again (following **Bartender**'s info) and my 'offline' installation done!
[COLOR="green"][SIZE="4"]![/SIZE][/COLOR]

And an 'in topic' note, Jaunty HAS wvdial into DVD:
[http://cdimage.ubuntu.com/releases/jaunty/release/ubuntu-9.04-dvd-i386.list](http://cdimage.ubuntu.com/releases/jaunty/release/ubuntu-9.04-dvd-i386.list)

---

### Post by Bartender on 2009-12-31
George, I really appreciate your input.  I'll feel a lot more confident about this after a few people report in with success stories. 

And you're saying you did it using a completely different OS??!  I imagine that would be very good news for longtom, who works with lots of dial-up users.

I don't understand your last comment about jaunty.  There's a DVD??

I'm working on the next step now.  I want to install RubyRipper, my favorite tool for ripping audiobooks.  There's a RubyRipper .deb [package]("http://linux.softpedia.com/progDownload/Rubyripper-Download-20741.html"), which is really dinky.  But there are roughly 18MB of packages that should be installed before installing Ruby.  I found a list of those [packages]("https://help.ubuntu.com/community/CDRipping"), copy/pasted them one by one into Synaptic "Search', checked each Search result for installation, then Marked the list and created a new Download Script.  This is a little different than just asking Synaptic to Reload.  Will let everyone know how it goes.

---

### Post by GeorgeVita on 2009-12-31
> **Bartender said:**
> ...I don't understand your last comment about jaunty.  There's a DVD??

Yes! As my main connection is a 3g modem (AT commands interface, a lot of bugs to hound, dnld speed 20-150 KBytes/sec) it is like an upgraded dial up connection ...
... every time I am close to my 'broadband library' (a cofee shop actually with free WiFi) I get my cdimages to test from: [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

Searching /releases sub directory there is only the 'dvd' version of old releases which include ALL packages for that release >>> including wvdial <<<

Full list of packages included can be found to .list file (small text file) so you can find if a package is there. For Jaunty i386 this is:

[http://cdimage.ubuntu.com/releases/9.04/release/ubuntu-9.04-dvd-i386.list](http://cdimage.ubuntu.com/releases/9.04/release/ubuntu-9.04-dvd-i386.list) 

Enough for this year

I wish you (all) a **Better New Year for you and your family!**

George
(counting 234 minutes to get Year 2010)

---

### Post by Bartender on 2009-12-31
OK, George, thanks again - 
Found the DVD sites.  
Learning something new every hour or so :)

I'm gonna have to start a new "Dial-up" thread with all the little bits and pieces put together in a more concise fashion...

---

### Post by Bartender on 2010-01-01
Next step of the "Download Script" tests...

Ran the Download Script that was created after copy/pasting the list of packages that should be downloaded first in order to install RubyRipper, as described a few posts back.  At the library, that script appeared to work.  The laptop downloaded a couple dozen packages anyway.

Back at home, Synaptic recognized the packages and installed them.  Then I clicked on the rubyripper.deb file (it's a small file so I'd already downloaded it at home) and the installation failed.  Said it needed five packages.  Dialed out and tried again.  gdebi downloaded for about ten-fifteen minutes.  It then installed RubyRipper and I ripped audiobooks all afternoon.  Works fine.

---

### Post by Bartender on 2010-01-03
Well, I'm still pretty happy with the Package Download Script (PDS) but need to pass on some new experiences.

I think the PDS will work just fine for run-of-the-mill updating as long as the dial-up PC can at least reload the latest package information.

Installing new programs gets more complicated.

I created a PDS for Mozilla Sunbird.  That installed without having to get any more stuff off the internet.  Sunbird is working fine as far as I can tell.

Same thing for ccsm, the Compiz Configuration Settings Manager.  It didn't need any extra packages.

Tried to install hugin, it needed too many extra packages.

Tried hplip, the HP printer tools utility, same thing happened.  Synaptic read the packages and started to install, but said it needed 20+ MB of extra packages.  So I asked for details, then copy/pasted all the extra packages to a document and printed it.  copy/pasting took a few tries because there were about 25 packages and it was a little window, so I basically moused out into thin air a few times until I finally got all of them.

Printed out the list, then manually entered each one of them into Synaptic Search.  When I finally had the whole list showing in the left-hand column, I marked for install, created a download script, and saved to a thumb drive.

I haven't tried to get the extra packages yet, but I think it'll work.  I "opened" the script instead of "running" it, and the list looked complete.  BTW, the script looks _very_ simple.  If a person knew what they were doing they might be able to drop the original copy/pasted list of packages right into the script instead of manually searching/marking them like I did.  I created a blank script by mistake the first time so that part's easy.  All you do is click on File>Generate Package Download Script before asking Synaptic to Reload or Marking any packages. 

What I'll do after getting the extra packages is drop them into the same folder that has the first set of hplip packages so that Synaptic sees all of them at once.  I think it'll work :)

EDIT:  The above did work to install HPLIP to the at-home PC.  It was a bit laborious to type in the whole list of extra packages, but it worked.

---

### Post by Bartender on 2010-01-05
Message to George Vita - and anyone else wondering about init strings :)

I have a vague idea of how init strings function but the details are lost on me.  I finally plugged in George's recommendations (post #158) after he reviewed my post of the modem diagnostics from within Windows.

Take a look:
 
```

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F1E0Q0V1&C1&D2S0=0
AT&F1E0Q0V1&C1&D2S0=0
OK
--> Sending: ATS7=60S19=0M1&M4&K1&H1&R2&I0B0X4
OK
--> Modem initialized.
--> Sending: ATM1L1DT*70, [COLOR="Teal"]phone number, edited[/COLOR]
--> Waiting for carrier.
CONNECT 36000/ARQ/V92/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
\nWelcome to the Intarweb
Login: 
--> Looks like a login prompt.
--> Sending: [COLOR="Teal"]my full email address here - edited out[/COLOR]

Password: 
--> Looks like a password prompt.
--> Sending: (password)
    Entering PPP Session.
    IP address is 69.41.141.47
    MTU is 1524.
--> Looks like a welcome message.
--> Starting pppd at Tue Jan  5 07:28:18 2010
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 8300
--> Using interface ppp0
--> local  IP address 69.41.141.47
--> remote IP address 69.41.141.5
--> primary   DNS address 64.136.173.8
--> secondary DNS address 64.136.164.66

```

With no init strings at all, I got some funny messages like "don't know what to do next, trying ppp" The connection worked, but with the init strings plugged in there appears to be less confusion.  "Welcome to the intarweb" is also new.  Don't know what that means.  Maybe I should post the log with no init strings...

---

### Post by GeorgeVita on 2010-01-05
Hi **Bartender**,
most 'funny' messages are 'status reporting' created by wvdial (it is a very old program written by enthusiasts).

```
--> Carrier detected.  Waiting for prompt.
\nWelcome to the Intarweb
Login: 
...
Password: 
```Above is the 'old way' to connect using your keyboard (bbs style). This supposed to be the 'stupid mode' and can be bypassed adding into your /etc/wvdial.conf file the 'well known': ```
Stupid mode = yes
``` There is also an option box at:
Gnome-ppp > Setup > Options Tab > Ignore Terminal Strings (stupid mode)

The 'real information' comes from: ```
CONNECT 36000/ARQ/V92/LAPM/V42BIS
-
``` which shows the type/quality of your connection (assume that you have set a baudrate >57600 in /etc/wvdial.conf or at Gnome-PPP).
Trying different parameters (or better electrical wiring) you may get better speed (>36000).

Regards,
George

---

### Post by Bartender on 2010-01-05
Where did you learn all this stuff about modems and init strings?  I've prowled around on the net and never found any good source of information.  I'd download and print it out and study it if I could find a source that laid the whole thing out in a logical fashion.  

Instead what i find is bits and pieces scattered all over the place.  And it's hard to say if it's even good info if you know what I mean..

EDIT: I mentioned it earlier, but my /etc/wvdial.conf file is mt.  Well, not empty, it has the default lines but nothing more than that.  I don't understand how gnome-ppp can be working without it modfiying /etc/wvdial.conf.  Maybe it made a new one somewhere else??

---

### Post by ranch hand on 2010-01-05
Check you pppconf file(s).  The others are just different ways to modify it, I think.  I do not remember where all of them are and that would be in Hardy anyway it could have changed.

---

### Post by frank cox on 2010-01-06
> **Bartender said:**
> Hi, frank -
Gotta couple of questions for you.  First, re: natblast, I've never heard of them.  They have two phone numbers listed that are local for us.  The price is within a few bucks of Frys.com if not the exact same.  I realize there are no guarantees with this sort of thing, but would you say they've got your stamp of approval?

Second, re; Puppy.  Are you running the stock-standard pup, or did you download the one with more winmodem drivers, or did you maybe install the standard version then manually download more drivers?

This has been an interesting couple of weeks for me.  I'd decided months ago that Linux and dial-up were a complete write-off, but suddenly I'm using Linux more than XP on our main PC!!

I was mistaken about the unlimited-they shut me off for a day yesterday for excessive usage. Max is 200 hours and I fell asleep downloading a few times. 200 hours is the limit and they restored it today. However the no knock offs is accurate and I am using a winmodem in Puppy Linux.  200 hours is usually plenty for me.
As far as the signal yes, I recommend it highly. They will refund your money for any pre-paid service not used if you cancel. If you are not happy with Fry's and 200 minutes is enough go for it.  There is another one they link to that is unlimited for 10.00 a month but I like the 81.00 a year price.



I was so frustrated with getting Ubuntu to dial before I uninstalled Network Manager I never gave Puppy a chance. I have 4 winmodems that work full speed in Puppy and may work on Ubuntu believe it or not. I have a few more Puppy recognizes but won't connect from, it may e they need a different config string. I can' tell the difference in the USR serial speed wise. 

I did not know you could download a package of drivers, no I am using the standard package. I am having a little trouble getting wine to work and may change to a different distro with Wine preinstalled. I use FireDog for the browser and I like it much better than Sea Monkey. If you switch be sure to follow the directions for removing Sea Monkey. If you don't see them email me and I will send the link.

Also I have decided I like the frugal install on the Windows or Ubuntu drive and then just boot from the install disk. It is easier and makes upgrading and backing up the whole OS a snap. When you get it tweaked you can re master the disk and reinstall the system on another machine or in the event of a crash.

Game Puppy is pretty cool too!

I am using SoftMaker 2008 because thy were giving it away free and it is a nice compromise between Open Office and AbiWord. Nest time I am on a high speed line they are going to give me a Beta of SoftMaker 2010 for Linux.

This modem is the one I am using right now. 

DESCRIPTION: Conexant HSF 56k Data/Fax Modem
VENDOR: 14f1  DEVICE: 2f20  KERNEL MODULE: hsfpcibasic2

It works great on Puppy but I need WinXp drivers for it and do not know if they exist, go figure? LOL! I am going to write the company ans see.  Puppy has a scan that works well-it told me the brand of Ethernet card and type in a friends windows machine . Conextants scan gave me the name of this modem's manufacturer.

 RESULT OF MODEM QUERY                                = 
===================================================================== 
NUMBER OF MODEMS FOUND = 1 
 
MODEM #1: 
  PCI CONFIGURATION INFORMATION READ: 
     VENDOR ID              : 14F1 
     DEVICE ID              : 2F20 
     SUBVENDOR ID           : 14F1 
     SUBDEVICE ID           : 2000 
     REVISION ID            : 00 
 
  DEDUCED INFORMATION: 
     VENDOR NAME            : CONEXANT 
     DEVICE NAME            : UNKNOWN 
     SUBVENDOR NAME         : ACTIONTEC                   -- [HTTP://WWW.ACTIONTEC.COM/](HTTP://WWW.ACTIONTEC.COM/) 
     MODEM TYPE             : HSF 
     WINXP INBUILD SUPPORT  : NO 
 
Of course you have to run this scan under Windows unless WINE will run it.

And be sure to install the VLC pet for movires and music. Gxine is a good program so keep both just in case but VLA is better and more versatile. Aqualung is garbage as far as I can see.



.

---

### Post by frank cox on 2010-01-07
> **GeorgeVita said:**
> Hi again!

... and this way is 'distro-independent' as the created script has the full link for the .deb files to be downloaded (including dependencies). Just **wget** must be installed. I checked above using puppy booted from microSD card (was into my ZTE MF636 modem), connected, run script, download completed, boot Ubuntu 9.04 (from SDHC card) run synaptic again (following **Bartender**'s info) and my 'offline' installation done!
[COLOR=green][SIZE=4]![/SIZE][/COLOR]

And an 'in topic' note, Jaunty HAS wvdial into DVD:
[http://cdimage.ubuntu.com/releases/jaunty/release/ubuntu-9.04-dvd-i386.list](http://cdimage.ubuntu.com/releases/jaunty/release/ubuntu-9.04-dvd-i386.list)

For what it is worth I never was able to dial in Ubuntu until I nuked the network manager!

---

### Post by Shazaam on 2010-01-07
I use toast.net for my dialup ISP. Yes, they DO warn you that they MAY disconnect/terminate you for excessive use but I haven't been bumped off yet and I have been using them for almost a year. $9.95/month, and they use webmail and/or IMAP through gmail (you can run Evolution/Thunderbird).
They use their own "Page Not Available" error page so if you are the paranoid type (or, like me, you would rather have the standard Firefox page pop up on errors) you might want to add it to your hosts file or whatever blocking app(s) you use.

---

### Post by Bartender on 2010-01-08
Yeah, I'm using Frys.com, which is budget ($6/month).  They say unlimited, and I've never been told I've crossed the line for the month, but the flip side is I get disconnected every coupla hours.  Maybe that's because of something I haven't set up correctly in the modem, but I don't know what that could be.  We have call waiting, so I add [COLOR="Blue"]*70,[/COLOR] to the phone numbers in Gnome-ppp.  Without that, I believe you get booted off the internet every time someone phones your house.

---

### Post by frank cox on 2010-01-08
This modem also works in Puppy . I am starting to see a pattern. This modem has no in built support for WinXP , it has does have an XP driver though and works fine in XP.
I forgot to write down the  Linux driver but if anybody needs to know e-mail me or pm. Or just wait till I check in here.

But although I like the idea of using the winmodem I have become sold on the serial, My old Sportster USR 33.6 flashed to 56k runs faster on Puppy than the winmodems by a huge margin, Average 54k compared to 47k . That is 10% but it is deceptive because the winmodems vary and run at 30 sometimes..The serial has never clocked below 46 and that was only once ,I have clocked it at 59! Of course I am taking the online tests as accurate . The true numbers may be different but comparatively speaking I say they are correct, the serial is faster. 
On windows there is less difference which makes sense .

It would be neat if you had all the sound features in Linux but it is not a big deal.



======================================================== 
=              SYSTEM INFORMATION                                   = 
===================================================================== 
Date         : 1/7/2010 
ListMdm Ver  : 1.6 
Windows OS   : Microsoft Windows XP  
Build Number : 2600  
 
===================================================================== 
=              RESULT OF MODEM QUERY                                = 
===================================================================== 
NUMBER OF MODEMS FOUND = 1 
 
MODEM #1: 
  PCI CONFIGURATION INFORMATION READ: 
     VENDOR ID              : 2000 
     DEVICE ID              : 2800 
     SUBVENDOR ID           : 122D 
     SUBDEVICE ID           : 2800 
     REVISION ID            : 02 
 
  DEDUCED INFORMATION: 
     VENDOR NAME            : UNKNOWN 
     DEVICE NAME            : UNKNOWN 
     SUBVENDOR NAME         : AZTECH                      -- [HTTP://WWW.AZTECH.COM](HTTP://WWW.AZTECH.COM) 
     MODEM TYPE             : HSF 
     WINXP INBUILD SUPPORT  : NO

---

### Post by frank cox on 2010-01-12
If you could get the same drivers that puppy comes with to work in Ubuntu it would be a huge help. I installed the "XP" Puppy and it found the modem in my Dell 530 that 4.31. did not and it tested at 42kps. SO far I have gotten the winmodems in ever desktop I have tries , 5 in total, and 3 more modems as well.

---

### Post by Bartender on 2010-01-13
Hi, frank -
And this is the standard Puppy Linux, right?  I remember mentioning a week or so ago that there's a Pup with more modem support.

Can you list the modem chipsets that have worked for you in Puppy?  The brand isn't all that helpful.  It's the chipset that really counts.

I'm sure that someone with coding skills could bring the Pup drivers over, but that's way beyond me :(

What's XP Puppy?  Oh, OK, you talking about [this]("http://puppylinux.org/news/puplets/new-xplike-puplet/")?

---

### Post by Bartender on 2010-01-14
Hey, ranch!
I'm thinking about trying out one of those USR intenal modems.  The Performance Pro.  I think they're also called 5610?

Can you give me a quick outline of what you did to get it going?  I know you said it was a pain...

---

### Post by ranch hand on 2010-01-14
The problem I had was getting the thing seen by the system.

We bought this box with Vista on it and a connexant modem.  I was used to a real modem so I got a new 5610c and plugged it in.  Worked fine under vista.  Ubuntu didn't see it.

One problem was that it was on ttyS5 and Ubuntu only supports modems on tty0 - 3 (ports 1 -4 in MS).  I moved it and checked with vista and it was on port 1 or ttyS0 in Ubuntu.

I was using Hardy.  Pulling up the network manager on Hardy gave you the options for configuring a modem.  I did so.  This did not work.  I wiped all that and the folks here on the forums told me to use pppconfig.

I did that and it did not work.  I found, though, that if I did it in pppconfig first and the nin network manager it worked just great.

The thing is that not all of the system saw the modem at all.  FF didn't because the network manager didn't.  If you cursored over the network applet it would inform you that there was no connection.  If you right clicked on it you got the option to disconnect and it would work and then you could reconnect but the applet would continue to say, while you were downloading something, that there was no connection.

Intrepid was the last version that I connected with that modem.  I had gotten the terrible affliction of multi-booting by then and had three drives that I was trying to learn to use.  I had Intrepid on all three.  Wvdial came with it as it had in Hardy (worthless to me in Hardy) and the NM was changed so that it did not support configuring a modem at all.

Tried Wvdial and it connected me right up.  I was thrilled.  Went to my other 2 installs of Intrepid and did the same thkng and it did not work on either one of them.  I was not thrilled with that at all.

I never did get them to work.  This is why I am not real thrilled with the idea of using wvdial.  I should have played with them and pppconfig but I did not.  I gave up on them and stuck with Hardy.

So, all I ca ntell you is that you better know what ttySx you install on so that you can tell the box where it is.  I hope that modem manager will set up the thing or at least make it so you connect automatically.

I know that I saw, flashing past on the boot screen, in 9.10-testing (no quiet on the boot for a long time) the modem detected in my box when it was not even connected to anything so I have some hope from that.

It is seen by "lspci" but then it was in Hardy too.
> 
04:00.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)


---

### Post by Bartender on 2010-01-15
OK, thanks -
I'm on the prowl for a few of these 5610's.  I want to install (successfully would be good) in Karmic and Jaunty, then add some directions to my new [Dial-Up Redux]("http://ubuntuforums.org/showthread.php?t=1377619") thread.

---

### Post by TopEnder on 2010-01-25
G'Day Bartender & Ranch Hand,  Hope this does not short cut your original post Bartender.  I have A D-link DU-562M external USB modem , in Puppy Linux it shows as USB HSF modem.  The modem was auto detected by Puppy Linux and performance exceeds that of any of my other external modem, it shows up as being on ttyHSF0 is there a equivlent port under Ubuntu and is there anyway to have it detected using wvdial.  Thanks in advance young men, TopEnder

---

### Post by ranch hand on 2010-01-25
I suspect that is the same as ttyS0.  I know that my internal is seen by the 9.10 modem manager (and 10.04).

I am not on dial up now so I have no idea about anything else.

---

### Post by GeorgeVita on 2010-01-25
Hi **TopEnder** and **ranch hand**. Some ideas below:

**ttyS0-ttyS3** are the h/w serial ports (com1-com4 at old PCs).
Although these ports are not all (0-3) physically implemented, they exist for compatibility reasons (some h/w addresses and interrupts are reserved).

**ttyUSBx** is used for a typical USB peripheral that most times can be used as a serial communication port. A 'general' driver (usbserial/option) is used.

**ttyACMx, ttyHSx, ttyHSFx,** etc. are other 'names' for USB communication ports created by more 'specific' drivers (Linuxant creates ttyHSFx).

Puppy Linux integrates more drivers for dial up modems (also sometimes it goes better with 3g).

**wvdial** and **wvdialconf** search for /dev/modem /dev/ttySx and /dev/ttyUSBx (by default). To test another port you can firstly see if it is created (dmesg or 'ls /dev/ttyXYZ') and then try to communicate with it. Easier communication can be done with the command **screen** (read more using 'man screen').
```
screen /dev/ttyUSB0
```
Note: screen command may 'lock' this port (reboot to be sure). You can 'release' any port by 'killing' screen' processes. Check with '**ps -A | grep -i screen**' and '**sudo kill xxxx**' any 'screen' process.

When the modem is 'external', tests can be done with the following procedure:

- Boot without modem, **wait** for the system to load
(if you are using USB to RS232 cable or i/f DO NOT attach it)
- do NOT RUN any communication/connection program
- open a terminal window and try: **sudo dmesg -c**
(this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show only 'new' activity)
- from terminal: **lsusb**
- attach modem, power it ON
- **wait** 30-40 seconds
- from terminal: **dmesg**
- from terminal: **lsusb**

Notice any changes comparing 'lsusb' outputs. The 'new line' must be the modem.
> Bus 001 Device 004: ID **19d2:2000** ONDA Communication S.p.A. The vendorID : productID numbers are your 'search string' to find help. For above output you must search for **'19d2:2000'** and their HEX definitions '**0x19d2 0x2000'**

Second 'dmesg' will show all system activity, possible drivers used and any communication port created. If you see something like **ttyUSB0** you can 'list it' using: **ls /dev/ttyU***

In general, most new communication ports created can be listed with:
```
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
```

If you need help, add the output of the terminal command: **uname -a**

Regards,
George

---

### Post by TopEnder on 2010-01-25
ranch hand & GeorgeVita, Thanks for the info, I'll try your suggestions in the next couple of days,  TopEnder

---

### Post by Bartender on 2010-01-25
George -
You don't mind if I copy/paste those directions for identifying the modem's location into the first post of my Dial-up Redux thread, do you?  I knew my directions for finding the modem were weak.  Yours looks very comprehensive.

Also, how do you create a link to a single post?  I've seen you do that but don't understand how it's done.

Thanks!

---

### Post by GeorgeVita on 2010-01-25
> **Bartender said:**
> ... (1) You don't mind if I copy/paste ...
(2)how do you create a link to a single post? 

1. **Please** do it!
2. right click on post# (this one is 196) and 'copy link location'
then select word to have the link and use the 'insert link' sign (editor) to paste it. Or just paste the whole link,

Regards,
George

>>> P.S. I edited my [post]("http://ubuntuforums.org/showpost.php?p=8716584&postcount=23") at 'Redux' finalizing my 'offline' installations with only a 10MBytes 'update'.

---

### Post by Bartender on 2010-02-03
OK, fellers -
I just received two 5610 USR internal modems.  Here's the output from lspci -v:

```
01:09.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01) (prog-if 02)
	Subsystem: 3Com Corp, Modem Division Device 00d3
	Flags: medium devsel, IRQ 17
	I/O ports at b800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: serial
```

pppconfig and gnome-ppp are both telling me I have no modem, which is kind of what I expected.

I installed setserial.  I think I have to enter a command or two, but not sure what or how to do it.  Will read up on this but hoping someone will know exactly what I gotta do next so I'm not guessing.

Thanks!

---

### Post by ranch hand on 2010-02-03
If that is an internal you need to know the ttySx port and tell pppconfig what it is and it will work.  I has to be one of 4 between ttyS0 and ttyS3.

If you have MS on your box you can check what port it is on (1 through 4) and translate that to 0 through 3.

---

### Post by Bartender on 2010-02-03
Hi, ranch -
You didn't have to dink around with setserial?
This one's not a dual-boot.  I'm not making much headway on this.  Just fumbling around with ancient links that don't make a whole lot of sense to me.

EDIT:  Online with the 5610
[http://ubuntuforums.org/showthread.php?t=1397947](http://ubuntuforums.org/showthread.php?t=1397947)

There was some confusion and fumbling around.  I have another 5610 and another test PC, so I'll try to go step by step and see if I can record more specific notes.  I don't think setserial had anything to do with it.  I believe we probably have the benefit of kernel improvements since those old 2005/2006 posts I was trying to follow.  Still, gnome-ppp didn't seem to find the modem until I knew for sure from puppy where it was and told gnome-ppp "look here, ya moron".  I think that setting permissions in User/Group made a difference too but not sure.  I could go back and change them but it's working and it might take a few days before I screw up the courage to risk breaking it!

---

### Post by ranch hand on 2010-02-04
I was working with only Hardy when I got all this stuff straight.  I never heard of set serial.

I doubt it would help but I could dig up the threads.  I saved them in my CP under sur5610c (I just looked).

The reason I do not think that they are that helpful is that network management has changed too much.  It changed in 8.10 MUCH for the worse.   That is when wvdial became the main tool.

---

### Post by Bartender on 2010-02-04
Good morning, ranch -
Hey, thanks for the offer but I don't think it's necessary.  I agree with you regarding network manager.  I haven't even looked at NM since the distro you mentioned or thereabouts.

I've got modems up the yin-yang now.  I figure the surest way to get Qwest to run DSL up the valley is to keep buying dial-up modems. :)  Next I'd like to get my hands on one of those little Rosewill RNX-56 USB units.  They're *supposedly* controller based and good to go with Linux.  Seein's believin'

---

### Post by Bartender on 2010-02-08
Hey, ranch!
If it wouldn't be too much trouble, could you see about digging up whatever records you have re: the 5610??  I'm thinking you must have worked thru the same problems I'm having.  The 5610's work, but I'm having some weird problems with ownership, or the /var/lock files, or group settings, or ?.

The tty/S1 device (internal 5610) is owned by root, and the things I've tried so far to change that only work til the next reboot.

The weird thing is, /dev/ttyS0 is also owned by root; shows the same permissions.  That's where the external modem is.  It dials out without a fuss.

---

### Post by ranch hand on 2010-02-08
I will look into that.

I have to go catch a cat with the Dreaded Mother in Law to get it fixed.

Testing for the upgrade of the old LTS 8.04 straight to the new LTS 10.04 started the 4th.  I have been successful in doing this.  I am impressed.  Wvdial was updated in the upgrade.  I have been thinking of just plugging the thing in and disconecting the DSL and seeing if the modem is seen well.  I do not have an account for dialup so I can 't try it but I would like to see.

---

### Post by ranch hand on 2010-02-08
I am on my test platform which is also where my old 8.04 resides.

My Hardy Heron (or Horny Horse) /var/lock directory is empty.

My wvdial file looks like this;
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS0
ISDN = 0
Phone = 7844688
Password = xxxxxxxxxx
Username = xxxxxxx@rangeweb.net

```
I believe that I had to edit that for it to be correct but that may have been in 8.10.  It was generated by pppconfig.

This is a thread that actually got me up and going;

[http://ubuntuforums.org/showthread.php?t=940903](http://ubuntuforums.org/showthread.php?t=940903)

I had to get the modem in a slot that was right for the OS.  Set it up in pppconfig.  Then set it up in the 8.04 Network Manager.   I really think that pppconfig is the best route but I have no idea with these newer releases.

I installed 8.10 three times on the same drive.  The first one hooked right up using wvdial.  The other two I never got to work at all.  I kept them on there until we moved and I wiped them all as  I never liked the bugger and I really like 9.04.

10.04 is looking real good too but who knows what it will really be like at this point.  I prefer it to 9.10 already.  I think that is the kernel and I am not sure but what, when released, it may not be better for dial up.

If you are interested in trying it for that I would wait for beta1 at least (3-18-10).  I do know that it is seeing my inactive modem when I have to boot to recovery (testing is fun).  The only problem is that testing stage OS' have a LOT of updates.  On dial up I would guess about 6 to 8 hours worth per day most of the time.  It seems like about a month after a release it gets reasonable.

---

### Post by Bartender on 2010-02-09
Hi, ranch, thanks for looking in the archives :)

So, the long and short of it is you moved the 5610 to a different slot and it started working?

Did the minicom program every make a difference?  Rather than focus on one path that I'm pretty sure will work, I've been shot-gunning the problem using old threads that talk about setserial, etc.  I'm under the impression that I don't need setserial because of improvements in the kernel, but not sure.
Other threads talk about making changes to /var/lock, but again I'm not sure if that's applicable.
Other threads talk about adding a file to rc.local (or similar) that creates a rule to identify the modem during startup.
Other threads talk about permissions, groups, etc.

Like I said, shotgun.  I've now got one of the 5610's in a test PC that can be botched up, so less afraid to try things.  Moving the card around on the slots is easy, so I'll give that a shot.  Interesting thing - I believe that the 5610 has shown up as using IRQ 17 on all three PC's.  And some of the threads indicate that it needs to be on a lower IRQ.  Again, I don't know if that's accurate or not.

Puppy Linux sees the 5610 on ttyS1 and dials.  Frustrating that Ubuntu can't do that.

---

### Post by ranch hand on 2010-02-09
The only reason that I had to move my modem was that in MS it was listed as being on com6 (ttyS5).  That tty is not supported as a modem slot under Ubuntu.  It has to be on ttyS0 through ttyS3.

With yours on ttyS1 it should be fine.

Minicom was useless as tits on a boar hog.

What really got my modem working was to configure through pppconfig and tell it where the modem was as it could not find one.  The only place it showed up was when I ran "lspci".  It was never seen by the NM.  Always claimed that there was no connection.  I did have the option to connect or disconnect through NM and it worked fine but if you cursored over it there was a message that there was no connection.

I ran the Suse LiveCD and hooked up with no trouble anywhere on it.  I installed PCLOS-gnome and during installation had t ogive my user name, name of provider, password and the number to dial.  When installation was done and I rebooted I was on line.  I tried a couple of KDE OS' (not Ubuntu) and they all worked that same way or were easy to configure  with kppp.

Kubuntu worked, kind of but it, of coarse did not see the modem so you had to fight with it a bit.  Still easier than Ubuntu.

That is the biggest thing that bothers me about the whole Ubuntu family.  Not detecting internal modems.  You would think that a guy from SA, no matter how rich, would realize that a huge number of folks in that country and the continent are lucky to have dial up service.  An OS that does not hook you up easily is of no use to the poor guy on the street that just wants a legal OS.

They are being forced, by Ubuntu, to use some other OS.  Gets on my thungus.

After setting the modem up in pppconfig I needed to do it again in the NM to get auto connection.  You could not set it up by doing the NM first.  Had to be pppconfig and then NM.  I goot so that I could fire up the liveCD and be on line in less than 5 minutes (usually about 3).

I never had permission problems and can not see why you should.  That is bull.  If that is a problem it has to be something stupid connected with the newer NM setups.  DSL is a snap on any Ubuntu, including 8.04.  No permission problems there (well, I have only used it on 8.04, 8.10, 9.04, 9.10 and 10.04).

We got our first laptop from System 76 and the wireless came right up when I got where there was something to detect.  No permission problems there either.  There is no excuse for permission problems in dialup.

If you do not mind using pon and poff pppconfig is the only thing you should have to fool with.  After that I think that Wvdial or editing the rc.local may be the way to get it automatic.

pppconfig is nice in that it has the option to delete the account so that it is easy to fix if you really screw it.  It also has an edit option.  Just very nice to use.

---

### Post by Bartender on 2010-02-09
This morning I spent about 2 hours trying to be methodical, take notes, etc. so that I might actually gain something out of it.  

pppconfig would find the 5610 one time, then five minutes later it would say no modem.  Then a little later it said something about etc/ppp/users files after I wiped the dialer and rebuilt it from scratch.

wvdial seemed pretty consistent.  After going on and off a few dozen times wvdial seemed to start having problems with password, but that may have been the ISP's servers starting to get paranoid.

Another odd quirk - sometimes wvdial had to re-send one of the basic AT init codes that it usually just breezes through.  I have no reason to think the 5610 is faulty, but it *is* used.  I could pop in the other one and try some more.

Oh, yeah, first thing I did was move the card.  It went from IRQ17 to 21.  Didn't seem to make a difference - sudo wvdial went online after starting the PC like nothing had changed.

Maybe I should try some other OS'es and see if they're less hassle.  I've got Fedora and OpenSUSE install discs.  I'm feeling kind of "at home" with Ubuntu, and dial-up makes it hard to just start over again.  But I could try some other distros just to see if they give me less grief than Ubuntu.  Puppy certainly is easier.

I'm very thankful that at least the good old US Robotics externals work like a clock in Ubuntu.

---

### Post by ranch hand on 2010-02-09
I noticed when upgrading fro m8.04 to 10.04 that wvdialer xxx.1 was replaced by wvdialerxxx.3.  It could well be that the newer one is much better.  This, of coarse, would mean that there is a good tool that is tiny and being left out of the install for some really stupid reason.

I doubt that the problem is your modem.  Leave that puppy in and  I bet one of your live CDs for just about anything else will go on line with tools included in the Live Session.

---

### Post by Bartender on 2010-02-10
Latest News on USR 5610 - 

I installed Fedora 12 from scratch with the 5610 installed.  I was really hoping Fedora would handle things better.  It didn't.

Fedora doesn't come with pppconfig, but does come with wvdial.  I got it set up, and was able to dial out, but it sat there at the password part  until timing out.  Obvious guess is that I entered the password incorrectly, so I triple-checked, still nothing.  OK, plug in a USR 5686, re-run sudo wvdialconf so that it spotted the external, dialed out, I'm online.

Enough of this.  Decided I'd wasted too much time trying to get the 5610's working when I have four 5686's that work just fine.  Erased Fedora and installed Puppy to the HDD (instead of running it off the thumb drive) just to make sure it wouldn't behave differently.  Puppy sees the 5610, dials out, and it's fast.  us netizen seems to consistently report 42 Kbps or more, whereas Ubuntu hung around 40-41.  That's certainly not a huge difference.  Since I've only checked a few times it'd be premature to say "Puppy is faster" but it ain't slower.

Puppy is a niche OS.  Not a lot of people writing packages tailored for it, unlike Ubuntu.  But dial-up forces you to make choices that you might not make otherwise.  Puppy might work pretty good as a dual-boot, or on a second PC just used for internet work, or some other hybrid solution.  

One of the neat things about Puppy is that many of the additional packages are specifically set up to work without dependency problems.  Kind of like a Windows .exe.  I went into town and downloaded the latest Firefox.pet package, brought it home on a thumb drive, two clicks and it's installing.

---

### Post by ranch hand on 2010-02-10
If you want a full size OS I would try PCLOS-gnome (or PCLOS if you can stand KDE).  I know that when I tried Suse Live it worked easy.

Kubuntu hooked up all right but the interface is confusing to set up.  You do need to know the tty address.  Then you could install gnome and delete most of the Krap.

---

### Post by Bartender on 2010-02-11
OK, I'll try that.  Something's wrong at the library - download speeds have dropped about 40X from what they were a month ago.  Used to get 700 to 800 kB/s, now it's around 30.  I've been emailing the library techies and hoping they'll look into it soon.  

If they can get that straightened out I'll try PCLOS-gnome.  Haven't looked at PCLOS for a coupla years!  It'll be fun to revisit.

I appreciate your help :D

---

