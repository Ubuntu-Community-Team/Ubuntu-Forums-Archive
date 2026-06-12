---
title: "dumb question? serial port connection"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by MR McD on 2011-05-15
I have a HP M8400F, and have a Ubuntu 10.04 install disk, and I know that it can be used as a live Cd to use.

Now for the dumb Question---- Being on dial up I have a USRobotics serial modem, and on the back of the desktop there is a serial connection but covered with a plastic cap. If that cap is removed, is the serial port usable? I tried different ways to Google this but have had no luck finding an answer.

I would like to try Ubuntu, before I spend any money on either a usb modem or an adapter which are pretty expensive here in Canada.

Thanks for any help.

And also thanks to Joeb454 for the welcome to the forums.

---

### Post by timothy48342 on 2011-05-15
> **MR McD said:**
> I have a HP M8400F, and have a Ubuntu 10.04 install disk, and I know that it can be used as a live Cd to use.

Now for the dumb Question---- Being on dial up I have a USRobotics serial modem, and on the back of the desktop there is a serial connection but covered with a plastic cap. If that cap is removed, is the serial port usable? I tried different ways to Google this but have had no luck finding an answer.

I would like to try Ubuntu, before I spend any money on either a usb modem or an adapter which are pretty expensive here in Canada.

Thanks for any help.

And also thanks to Joeb454 for the welcome to the forums.

Sorry, no "Dumb questions" have so far been discovered. :)
As far as Your question... 

The maker of your computer included a seriel port, but covered it with a plastic cap. I would say absolutely you can use it. My thinking is that if it wasn't usable they would have saved the money it cost to provide it, (and to provide a plastic cap) and you just wouldn't have one. Serieal ports don't get used much these days. They probably put the cap there just to protect it so that the first time you do finally need to use it, it is free of dust.

If the female 9-pin plug for the modem exactly fits the male 9-pin plug on the back of the comp, there should be no reason not to try it out.

And good for you for making use of available older equipment that still works instead of wasting resouces on buying more stuff to be thrown away larter. 

-timothy48342

---

### Post by MR McD on 2011-05-15
> **timothy48342 said:**
> Sorry, no "Dumb questions" have so far been discovered. :)
As far as Your question... 

The maker of your computer included a seriel port, but covered it with a plastic cap. I would say absolutely you can use it. My thinking is that if it wasn't usable they would have saved the money it cost to provide it, (and to provide a plastic cap) and you just wouldn't have one. Serieal ports don't get used much these days. They probably put the cap there just to protect it so that the first time you do finally need to use it, it is free of dust.

If the female 9-pin plug for the modem exactly fits the male 9-pin plug on the back of the comp, there should be no reason not to try it out.

And good for you for making use of available older equipment that still works instead of wasting resouces on buying more stuff to be thrown away larter. 

-timothy48342

Thanks for the Response and not thinking my question being dumb. I will pull the plastic cap and give it a shot anyway, but I thought I would ask first. I will let the community know how things turn out for me. I am really anxious to give this " OTHER " operating system a go. It can not be any worse than fighting with windows constantly.

Again thank you.

---

### Post by MR McD on 2011-05-15
Removed the plastic cap from the back of my computer, to what I thought was a 9 pin serial port. It turns out to be a 15 pin type female plug.( the cap says do not remove ):confused: So I will have to either get a usb modem or a usb to serial adapter to get connected. :(

Oh, well a few more days and I should be ready to try Ubuntu. I'll just eat:popcorn: in the meantime!:)

---

### Post by MR McD on 2011-05-15
I was reading through the forums about connecting to the internet via dialup and am a bit confused. From what i understand thus far is that 
1:I will have to have another computer with  access to the internet
2: I will have to download some packages from Ubuntu to make a connection.

Question?? do I get the packages from the Ubuntu repository and do I put them on CD or floppy, and do I need a program as well to unzip the files I will have to get? 

Or is there a tutorial somewhere that would tell me what I need to know. I realize that dialup is not the best option for updating or downloading, but I am forced to use what I have.

I have learned to be very patient as I have had to do four system recoveries with windows Vista via dialup and then the updating. 

I am just trying to be as thorough as possible before I leap into Ubuntu. I would hope that the first install is successful and not have to do it all over again. 

Thanks for any help offered.

---

### Post by lkraemer on 2011-05-15
Try Posting #4 at:
[http://ubuntuforums.org/showthread.php?t=1734723&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=1734723&highlight=wvdial)

Then, check out Posting #3 at:
[http://ubuntuforums.org/showthread.php?t=1634580&highlight=dial+modem+setup](http://ubuntuforums.org/showthread.php?t=1634580&highlight=dial+modem+setup)

Post back as you make progress, or need help.

lk

---

### Post by Bartender on 2011-05-16
If you've updated Vista several times then at least you have a forgiving & dependable dial-up connection.
Mine bails on me after an hour or two.  Sometimes it bails much sooner.

[This]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008&cm_re=usb_serial_cable-_-12-156-008-_-Product") Sabrent cable works as an adapter from a serial connection US Robotics modem cable to a USB port.  Do you have the original USR cable?  You'll need that as an interface between the oddball port on the back of the modem to the Sabrent cable.  Be advised that the modem will be found at a different address than if you use serial cable as per post #12 of this [thread]("http://ubuntuforums.org/showthread.php?t=480717&page=2")  Oddly enuf, even though that thread is quite old Newegg still carries the same adapter, at the same location on their website!

Also take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1377619")

And this [one]("http://ubuntuforums.org/showthread.php?t=1238954") too.

The info is dated, but most of it still relevant.  I have several US Robotics serial modems and have connected several PC's with various Ubuntu releases.  It's always the same...

Make sure you have an ISP that works with Linux.  Not Juno, PeoplePC, or other ones that require Windows-based software.

Get the modem physically connected and find it.  Finding it or manually entering the location is described in threads.

Do the dip and dialout thing as described in Dial-Up Redux thread.

Use pppconfig to make a connection.  As mentioned, I have had pppconfig fail several times in a row with a new install, then suddenly it'll connect.

After you've gotten online, use Synaptic to "Reload" the repository info.  This will take a while - at least an hour.

ONLY after Synaptic has reloaded can you do a Search for gnome-ppp.

---

### Post by grahammechanical on 2011-05-16
By the way, that 15 pin D-sub connector is what is called a VGA connector. You can use it to connect to a monitor or a TV/monitor. I have a DVT/monitor I use DVI to connect to my machine but I could use the 15 pin VGA connector because both the video adapter and the TV have VGA ports.

Regards.

---

### Post by MR McD on 2011-05-16
Just an update: I downloaded Puppy Linux Lucid 5.2.5 overnight and set it up to run from cd. Also, yesterday, put a call out to anyone who might have a usb to serial adapter that was Linux compatible or a usb dialup modem that was compatible with Linux. Received three responses and have received two usb serial adapters and a USRobotics usb modem, model 5637.

Puppy has wvdial within it, borrowed the wifes Toshiba Laptop, put the cd in, and ran wvdial, followed the simple step  of setting up my internet provider, phone number, username , and password and in less than twenty minutes had both modems installed and working to connect connect.

Here is my confusion, if Puppy can make it so simple to connect, being such a minor distro, why can't Ubuntu do the same  being a larger distro.

Getting dialup to work in Ubuntu seems to be a convoluted effort, going from thread to thread getting a bit of information here then directed to another thread to get a bit more information. I know personally that I just end up being totally disoriented on what I should actually do.

Puppy is nice, but I do not think that it is the distro I want as I do not want something that runs from ram.

Although Puppy would allow me to use the laptop to get conneccted to hi speed to download packages and bring them home to upgade Ubuntu.

Thanks to Bartender and all who have offered their help. I will follow their links and suggestions, but it will take me a while to digest their information in this thick skull.

I will prevail, and windows will be out of my life.:)

---

### Post by MR McD on 2011-05-18
I hope that no one has taken offense to my last comment, it was not meant to be derogatory to any of the Linux disros available. I relly appreciate the links and suggestions offered thus far.

I am probably making this more complex in my mind than it actually is, and that is one of my own shortcomings. I think too that it is a little fear of the unknown. Also being Murphy's Law personified, "What should not screw up, I will more than likely screw up" just makes me more determined to try to get this right the first go around.

I have read a lot of the links thus far and made notes and it is slowly coming together in my grey matter. I will be installing Ubuntu on the weekend when life is less hectic. I hope it goes smoothly. 

And thanks for the links again.

---

### Post by timothy48342 on 2011-05-18
I don't think anyone took any offense. I have seen other threads where an expert has responded about other distros saying in general, "If you like that one, then by all means use it and enjoy it."

I'm new to the community, but it seems that no one seems to be pushing anyone to use Ubuntu. There is no hard sell. Everyone here seems to have migrated here on there own and its a very strong community compared to anything I've seen.

I personally didn't chime back in, because I didn't think I had anything useful to add. (Although, I noticed that your thread kinda went silent.) It seems like you have the information you need to get things worked out. (I must admit, I too followed some of those links and just thought to myself, "I'm glad I'm not having to deal with all that." It was a bit beyond my skill level at present.)

These days, with multi-boot being so easy to set up, theres no reason you can't have Puppy on one partition, since it works out-of-the-box, and still work on getting Ubuntu to work as well. (And I would bet that if you actually use a non-ubuntu distro, but still come here with general linux questions, no one is going to care. It's just the feeling I get here, that no one is going to say, "your not using our stuff, so we won't support you.") 

As far as which features are included on a live CD, I believe they have to pick-and-choose what to include due to space retrictions. When I burnt my live CD I had to select "allow overburn" because of the size. (I wish they had made it about 5% smaller.) So, I imagine they decided not to include wvdial as a trade-off based on which programs they thought would benifit the most users. If enough people need a certain thing, then they will likely adjust what gets included in future releases.

That is bad for you since you need a specific thing, but the resources exist. You just have to do some exrta leg-work.

As far as "getting this right the first go-around":
It might be good for you to install ubuntu, back up the whole partition, and then play with it. Go through the procedures in the links that were... umm out-of-my-league... and then if things get messed up, just restore it from back up and try again. Have Puppy installed, too, so then you can check your e-mail and bank balance, surf, and all the stuff you need to do.  ---->Yikes.. I just noticed after typing that you said Puppy runs from RAM. I know nothing about Puppy. So, I imagine you don't "install" that, but maybe you can stil "use" that to do what you need to do while working on Ubuntu.<----- 

ABOUT YOUR CURRENT SITUATION:
You said, "Received three responses and have received two usb serial adapters..." So, what are you using that is working. You have dial-up, with a USRobotics usb modem model 5637, and wvdial gets you an internet gateway. Is that right? And how well are things working? 

About your mysterious port on the back of your HP: ("DO NOT REMOVE" LOL)
Is the 15-pin female in three rows of pins, 5+5+5? Or is it 2 rows, 7+8? Three rows of 5 is standard VGA. (ok, the newest monitors have something completely different, so maybe there is now a new "standard.") On the other hand, 2 rows, 7+8, has been used for a number of different things. The 2 times that I have seen the 7+8 were both for game controllers. One on a Sound blaster card (very old) and one on a motherboard with integrated audio (kinda old). Could that be it? (I noticed that the manual for your comp does not mention it at all.)

So, again, I don't think anyone was offended... Maybe they were all like me and just had nothing more helpful to say, and didn't want to clutter the thread with useless chatter. Also, you didn't pose any specific additional quesitons.

Since the experts have been silent, I now decided I could go ahead and respond with what could be useless chatter. :)

Hope all is well. Give us a update. Ask specific question if your still having trouble.

--timothy48342

---

### Post by Bartender on 2011-05-18
AFAIC there's no need to worry about offending anyone.  Your observation was correct - Puppy incorporates much better tools for dial-up than Ubuntu.  

I tried Puppy for a while because of the way it handles dial-up modems, but came to the same conclusion as you did - it's not the distro I want to use daily.

It took me _months_ to figure out dial-up with Ubuntu.  It was bad enuf being new to Linux and Ubuntu.

So Puppy worked with your ISP?  That's good to know.  Your dial-up ISP should be compatible with any Linux distro.

You also mentioned a laptop, and the ability to go find some broadband.  When you get the time, please take a close look at my wandering posts about Package Download Script.  I have an Acer 5920 laptop.  When it's time to update and/or add applications to the desktop Linux PC's at home, I make PDS'es from them.  I transfer the PDS to a thumbdrive.  Then I go into town with the laptop & thumbdrive and get the data.  200+ MB downloads would never work on our home connection.  It sounds like your dial-up ISP is more dependable than ours, but who wants to wait overnite??

---

### Post by MR McD on 2011-05-18
Have been reading your posts about Package Download Scriptt already, that is where I got the idea of being able to go to the library, and download anything large I may want/need in the future. Have picked up two thumbdrives already one for me and one for the wife. Thanks for the info and I like you find the forum here as welcoming from reading the many posts that I have looked at.

---

### Post by Bartender on 2011-05-19
OK, keep us posted.  

Update, please - have you figured out a way to get the US Robotics Sportster connected to the HP?  I call all the old serial USR's "Sportster", just because it's so danged hard to spell that from a keyboard.

I've heard people say the USR 5637 worked out of the box, that it worked after some fussing around with it, and it didn't work at all.  One recent poster said any of these new thumb-sized USB modems with the Conexant chipset will work with modern Ubuntu releases.

I wish I had the discretionary income to buy one each of these "mini-modems", just to compare them to the old Sportsters.  I think the Sportsters would beat them.    

I tried an old AOL-branded Actiontech serial modem a few years ago.  Similar in general size to the Sportster.  I had a good handle on Sportster performance at our house.  The average was right around 38 - 40 kbps.  I ran the Actiontech for several days and it never got past about 30 kbps.  So, it's just a theory, but I think the old USR modems just might be the best way to go.

---

### Post by Irihapeti on 2011-05-19
For what it's worth, I ran Ubuntu with dialup only for 18 months. I dealt with the large download issue by writing scripts to do those at night or when no one was at home.

It's possible to get online without wvdial. pppconfig is another option which is still in 10.04 by default. In some ways, I preferred it because I could use commands in a script to disconnect the modem when the downloads had finished. (Important when you are on a plan with only a certain number of hours per month.)

To use pppconfig, type
```
sudo pppconfig
``` in a terminal.

@Bartender
Conexant chipsets seem to have good Linux support. There's a company that makes Linux drivers. I used them during the time I was on dialup.

---

### Post by Bartender on 2011-05-20
Has anyone tried configuring dial-up with 11.04?  I haven't.  Unity is a whole new desktop environment which doesn't use Gnome, right?  Does Gnome-PPP even work??

EDIT:  According to this launchpad [website]("https://launchpad.net/ubuntu/natty/+package/gnome-ppp") gnome-ppp is available for 11.04.  

What's unclear to me is whether you have to push Unity aside and use the Gnome desktop in 11.04?   Or if gnome-ppp can run from within Unity somehow?

---

### Post by Irihapeti on 2011-05-20
I would expect that it would be possible to install Gnome-PPP through Synaptic or Software Center, run the thing from the installed apps screen (or whatever you call it) in Unity and then add the icon permanently to the panel. I've added other stuff to the left-hand panel that way, and I don't see any reason why Gnome-PPP should be any different.

I just might try that and check that it works, even though I have no modem on the EeePC with Natty.

EDIT:
Yes, it works as described.

---

### Post by _duncan_ on 2011-05-20
Unity is not a totally different desktop environment. It is a shell built on top of gnome. In its current form in Natty, it is built on gnome 2 instead of the newer gnome 3. Any gnome-centric app from the repos should work in Natty Unity.

Some tidbits for dial-up users:

1. As Irihapeti mentioned, gnome-ppp from the repos will install just fine in Unity. Can't test if it works or not coz I gave away all my modems and no longer have a dial-up account.

2. wvdial seems to be available from the Natty live CD. I did not attempt to install it though.

3. pppconfig is installed by default as in past releases. This means dial-up users don't have to download anything from a default Natty install to achieve dial-up connectivity.

For users with no access to broadband but wish to connect using gnome-ppp, it may be prudent to install wvdial (together with the dependencies) from the live CD, attempt an initial connection using either pppconfig or wvdial, update the package list, then install gnome-ppp. This will save time downloading wvdial (and dependencies) from the repos. The gnome-ppp deb package by itself is quite small and easily manageable even using a dial-up connection. Updating the package list though will take considerable time on a dial-up connection.

-------------------------

A word of caution: Some versions of nVidia graphics cards seem problematic with Unity and may require installation of 3rd party drivers to get Unity working. This is not a problem for broadband users, but the download size of the drivers can be hefty for dial-up users.

---

### Post by Bartender on 2011-05-21
duncan, thanks for reminding me.  

I couldn't figure out a way to grab the nvidia drivers for our desktop PC at the library and bring them home, so went online via dial-up with the desktop PC and crossed my fingers.  Took about an hour but it worked.

---

### Post by MR McD on 2011-05-28
I apologize for the delay in updating my situation. I am proud to say that I am a noob Ubuntu user and am fully connected to the internet.

I first went to the library and downloaded wvdial and its dependencies, as I found Gnome ppp a bit confusing. Brought wvdial home and installed it and had the internet ready to use in no time. I first tried the 5637 USb modem, no problem and then tried the 3 Sporsters and they all worked no problem. Two of the Sporsters were 56k and the third was a 33k modem.

I used Keryx 0.92 to accomplish the bringing home of wvdial. And also for obtaining the updates. I wish I were more confident in the command line. But I will work at that and have set a period of time aside to read and practice trying to become used to this concept of Linux. 

I really appreciate the help offered here.

The ironic part now: after all the frustration of connecting with dial up, our dial up provider Bell Canada offers a hi speed Netgear Turbo Hub that plugs into the wall for rural customers with 3gig per month limit that we picked up yesterday and are now using. It works fine with Linux as well.

In retrospect, I am glad that the hassle with dial up occurred as it made me more determined than ever to use Ubuntu. It was a challenge, frustrating, but worth the effort. Thanks Ubuntu!

SOLVED, with great help!

---

### Post by Irihapeti on 2011-05-28
Glad to hear it. I just *love* success stories.

I wouldn't worry too much about lack of confidence in the command line. You've probably already done more than many new users. The thing is simply to keep going and not be afraid to try new things.

Before getting too adventurous, it's probably a good idea to read up on [backing up]("https://help.ubuntu.com/community/BackupYourSystem"); if you [have a working backup]("https://help.ubuntu.com/community/BackupYourSystem#Recovery"), you can just restore if you really mess things up. 

Been there, done that - numerous times. I sometimes think that you haven't *lived* unless you've trashed your system at least once. :)

---

### Post by MR McD on 2011-05-28
> **Irihapeti said:**
> Glad to hear it. I just *love* success stories.

I wouldn't worry too much about lack of confidence in the command line. You've probably already done more than many new users. The thing is simply to keep going and not be afraid to try new things.

Before getting too adventurous, it's probably a good idea to read up on [backing up]("https://help.ubuntu.com/community/BackupYourSystem"); if you [have a working backup]("https://help.ubuntu.com/community/BackupYourSystem#Recovery"), you can just restore if you really mess things up. 

Been there, done that - numerous times. I sometimes think that you haven't *lived* unless you've trashed your system at least once. :)

Thanks for the advice, will check that out!:)

---

### Post by Irihapeti on 2011-05-28
> **MR McD said:**
> Thanks for the advice, will check that out!:)

If you do that, it will *really* put you among the elite. :)

If you're sceptical, just look around at all the "I lost all my files!" laments and you'll see what I mean.

Which reminds me, I'd better go and do my backup now... ):P

---

