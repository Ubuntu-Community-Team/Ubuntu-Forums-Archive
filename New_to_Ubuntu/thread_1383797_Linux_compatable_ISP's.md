---
title: "Linux compatable ISP's"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by K-Bar on 2010-01-17
After getting my modem to work I still have a problem connecting to the internet because my ISP keeps rejecting my username and password. They told me their software was not compattable with Linux and I told them that should not matter since I was not using their software (I was using wvdial) when I was trying to connect. In the end I ask them if I have to change ISP's if I insist on connecting through Linux and their answer was pretty much yes.
 
So, what ISP's are compattable with Linux?

---

### Post by J V on 2010-01-17
All of them... the helpdesk is bullshitting you.

---

### Post by CharlesA on 2010-01-17
> **J V said:**
> All of them... the helpdesk is bullshitting you.

This.

I'm guessing the OP is using dialup or PPPoE (I think?)

---

### Post by K-Bar on 2010-01-17
> **J V said:**
> All of them... the helpdesk is bullshitting you.
I think you are right, but do you have a suggestion about how I might get past this ********. My guess is that when thier software (windows baised) transmits the password it is encripted; but if I don't know how, what can I do about that?

---

### Post by J V on 2010-01-17
You "Log in" from a page in the modem/router yes? Then the router is sending the password, you must just have the password wrong, just ask them to reset it...

Unless you have some special software thats supposed to do something about it...

---

### Post by Maheriano on 2010-01-17
Ya man, I plugged in my switch, plugged in my computer and was online in 10 seconds. The software doesn't do anything and the helpdesk didn't know what they're talking about.

---

### Post by Pappy2003 on 2010-01-17
If you contact your ISP again and the help desk can't help you, ask to speak to a Supervisor or the Technician.

---

### Post by lkraemer on 2010-01-17
K-Bar,
If your ISP keeps rejecting your Login and/or password then, you most
likely have something incorrect in the PAP or CHAP settings that were
inserted into pppconfig.

Have you tried editing/verifying these settings?  Open a Terminal Window & type:
```

sudo pppconfig

```

Follow the menu settings to create a PAP Connection.  You can leave the
ISP name "provider" or change it to your actual ISP.  Then select Dynamic
DNS, insert your login name, password, Phone number, and select the proper port.
Be sure to write the file and exit the main menu.

Check /etc/ppp for the file pap-secrets
A portion of the file includes (Version 9.10):
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"yourloginname" provider "yourpassword"

```

When you have this correct wvdial should dial, connect, and pass control to
pppd.

What version of Ubuntu are you running?

lk

---

### Post by Bartender on 2010-01-18
Who's your ISP?  Some of the above replies are just plain wrong.  I tried for years to get online with Juno.  Never succeeded for more than a few minutes, and the connection was dog slow.  That's because they wanted me to use their proprietary dialer software.

Dumped Juno, signed up with frys.com, got online.  None of the horse**** problems like Juno was shoveling.

---

### Post by K-Bar on 2010-01-18
The ISP is Juno. Per Pappy2003's suggestion I requested to speek to a supervisor. I got a reply that a senior technician would contact me but that hasn't happened yet.
 
It seems to me that all I need to know is how their software (windows baised) transmits my username and password, but they woun't tell me that.

---

### Post by MarkC502 on 2010-01-18
Buy a $50 Linksys router and then you can end all ISP BS and keep them from having any access to your LAN as well as reap the benefit of the extra security it affords. Everyone should have one, as it is the first step to being in control of your own network and not needing the lowest level phone support that has a manual in front of them that replaces their appliance that we call a brain. 

Most likely you just have DSL internet and as such you need the pppoe login, when you have a router it can do this for you. You just log into the router via Firefox or whatever browser you use and select pppoe for your WAN setup and then enter your account login and password and the click apply and plug your DSL modem into the WAN port on the router and the PC into one of the routers LAN ports and BAM you have internet and you just increased your network security VS external attacks. ( Also change the default router password - I cant believe how many business routers I have worked on that were admin/admin with wifi administration enabled , Super Dumb )

If you decide in future to get a router I would recommend the Linksys 54gl ( around $50 on newegg.com ) and if you get one you can PM me here and I will help you get it setup if you need it. But don't think this sort of thing is complicated as it is not very.

Hope this helps you

---

### Post by Bartender on 2010-01-18
> **K-Bar said:**
> The ISP is Juno.

Bingo

Time for a change.  natblast, copper.net, BasicISP, frys.com, and toast are 5 that I know will work with Linux.  Actually, any ISP that does not require any proprietary dialer software should work.

We use frys, I've tested copper several times at a friend's house, and have talked with people using the other 3 often enough that I feel confident mentioning them.

AFAIK PeoplePC, AOL, Juno, and NetZero (Juno and NZ are the same company, United Online) are all troublesome or impossible.

I know it's a hassle to change over.  I kept Juno for 3 or 4 months after signing up with frys just to make sure I'd gotten everyone.  Set up a gmail account, don't use the email supplied by the ISP.  That way changing ISP's in the future will be a LOT simpler.

Another thing - all those ads for "Accelerated" dial-up won't help you either.  Just sign up for the basic dial-up package.

RE: above post - You can't use a router with traditional dial-up service.  With a 3G modem, but not old-school dial-up.

[Here's]("http://books.google.com/books?id=PPG8PvUyTOAC&pg=PA140&lpg=PA140&dq=linux+isp+proprietary+software&source=bl&ots=MOGri6tWX-&sig=O8LjB6Yrk6DHTddNu7Fy1hnne-g&hl=en&ei=NX5US9DtL42l8AbjramkBA&sa=X&oi=book_result&ct=result&resnum=12&ved=0CD4Q6AEwCw#v=onepage&q=linux%20isp%20proprietary%20software&f=false") a link to a google books sampler.  Note the comments the author makes on Page 140

[Here's]("http://www.dialup4less.com/faqtechnical.html") another ISP claiming to be Linux compatible.  I like it when they announce Linux compatibility.  You didn't see that very often a few years ago.

---

### Post by MarkC502 on 2010-01-18
ISP home tech support is always bottom barrel for home accounts only business accounts where I am actually get a tech to speak to others get people taught to follow a flow chart of questions.

Just use a router to do your pppoe login for you, and forget about your ISP for any support other than if your modem goes out and then I am just ordering replacement parts not requesting help. This makes like much easier as their are numerous forums for help with all router config tasks and these are Operating system independant so it matters not that you might use linux and someone who helps you with your router is using Windows as their advice will be the same as it is all about the router and routers work with all operating systems.

---

### Post by jward3010 on 2010-01-18
In fact you might answer the unasked question that everyone is pushing towards. Have you got a DSL modem / broadband router (it's called lots of stupid things)?

Have they provided you with any hardware or anything to get connected, if so what is it?

---

### Post by pirateghost on 2010-01-18
isnt this 2010?  why are people still using dialup?

---

### Post by puzzler995 on 2010-01-18
> **pirateghost said:**
> isnt this 2010?  why are people still using dialup?

[LIST=1]
[*]Its Cheaper
[*]Broadband/DSL/Cable might not be available in their area
[/LIST]

---

### Post by Hogosha on 2010-01-18
being cheaper might not be true in most places any more. I know a lot of people who are paying more for dial up. They don't change because either they cannot get broad band or are stubborn and stuck in their ways or are ignorant to the idea that faster does not mean more expensive

---

### Post by MarkC502 on 2010-01-18
As to cheaper so what, you can buy a car for a couple grand and get where you need to go or spend 20$ on a skateboard and get frustrated after half a mile. Which one is your daily transport ?

The difference in price is no comparison since you get 5-10KB in usable DL bandwidth from a telephone modem and 1000KB from a cable modem 12$ VS 30$ a month ( not worth it at all ). If you can't afford it then get 2 neighbors and a router with wifi for $50 and split the bill with them. Heck 6 houses on a block sharing a 10MB cable modem wifi connection would easily eclipse 6 dialup lines and for half the monthy fees :-) 

The only reason is no other option and with the advent of cellular modems that is even less of an issue today.

---

### Post by jward3010 on 2010-01-18
> **Hogosha said:**
> being cheaper might not be true in most places any more. I know a lot of people who are paying more for dial up. They don't change because either they cannot get broad band or are stubborn and stuck in their ways or are ignorant to the idea that faster does not mean more expensive
+1, true in IRL anyway.

---

### Post by jmcgovern on 2010-01-18
I believe both of these posters live in VERY rural areas where Cable/DSL is just plain not available It happens, even in the US.  My parents are in a rural area with no cable or DSL.  They use satellite, but satellite can be just as slow as dialup, the modems require software that might be Windows-only (some support Linux), and the service has a habit of going byebye in heavy rains/snow.

---

### Post by Hogosha on 2010-01-18
The US is actually one of the worst places for broad band availability. This is a huge country with things that are far apart. Europe is great for broadband since everything is so close together. The infrastructure we need for *anything* is enormous in comparison,

---

### Post by puzzler995 on 2010-01-18
> **Hogosha said:**
> The US is actually one of the worst places for broad band availability. This is a huge country with things that are far apart. Europe is great for broadband since everything is so close together. The infrastructure we need for *anything* is enormous in comparison,

Plus our government is too stubborn to upgrade our 50 year old grid.:(

---

### Post by K-Bar on 2010-01-18
> **Bartender said:**
>   Time for a change.
I agree.

I just signed up for the last ISP you suggested and I am now on-line with Linux.

The next step is to be able to launch wvdial from my desktop (I launched it this time from the command line) and have that call Firefox,but I will do a little research on my own first before asking for help

---

### Post by Bartender on 2010-01-18
jmcgovern sums up our situation.  We only live about 3 miles out of town.  DSL comes up the road about a half mile, then quits.  No cable providers either.  Satellite is expensive, too many moving parts, unreliable in bad weather.  And Western Washington, where we live, is not exactly known for sunny skies.

I've pestered the phone company many times, asking about DSL.  It'll probly be a long time before they run it up here because there aren't enough potential customers.

K-Bar!  That's awesome that you're online!  See the "Dial-Up Redux" link at the bottom of my post?  Follow the directions in the first part of that thread and you should be good to go.  You don't need to mess with wvdial directly.  Let Gnome-ppp handle the configuration.

---

### Post by MarkC502 on 2010-01-18
True sometimes but I live in the middle of nowhere out in kentucky ( Like I can shoot an AK47 in my front yard and no one cares ) and I have DSL and cable would be an option if I didn't live 200 meters from the road or if I wanted to pay for them to run the cable ( they quoted $5000 for 2 telephone poles and the cable and I laughed ). So it is really hit and miss and I also see people all the time that just think they can't get broadband where they live because some ISP told them that last year etc. I would say for most folks even in the country you can probably get DSL or a cell modem capable of 256KB speed which is at least fast enough for enjoyable web browsing. The way web pages are designed today they do not plan for you to be using a dialup speed and so browsing is horrible. 

Its not like the days of going to a gopher site on a text based display, for that dialup worked for the Java & Flash web of today it is severely limited and outdated.

---

### Post by lkraemer on 2010-01-18
K-Bar,
The hard part is over now.  Just use Synaptics to install Gnome-PPP.
Set it up with your loginname, password, and phone number and you will
be good to go.

lk

---

### Post by crjackson on 2010-01-18
> **MarkC502 said:**
> Buy a $50 Linksys router and then you can end all ISP BS and keep them from having any access to your LAN as well as reap the benefit of the extra security it affords. Everyone should have one, as it is the first step to being in control of your own network and not needing the lowest level phone support that has a manual in front of them that replaces their appliance that we call a brain. 

Most likely you just have DSL internet and as such you need the pppoe login, when you have a router it can do this for you. You just log into the router via Firefox or whatever browser you use and select pppoe for your WAN setup and then enter your account login and password and the click apply and plug your DSL modem into the WAN port on the router and the PC into one of the routers LAN ports and BAM you have internet and you just increased your network security VS external attacks. ( Also change the default router password - I cant believe how many business routers I have worked on that were admin/admin with wifi administration enabled , Super Dumb )

If you decide in future to get a router I would recommend the Linksys 54gl ( around $50 on newegg.com ) and if you get one you can PM me here and I will help you get it setup if you need it. But don't think this sort of thing is complicated as it is not very.

Hope this helps you

How do you use a router with a dial-up connection.  The OP states he's using wvdial.  This is a script that dials a POTS modem.

---

### Post by PenguinInside on 2010-01-19
I was accessing dialup Internet from Linux in 1999, so Linux does in general support standard dialup.

Does your Windows installation (if any) work for dialling up?

---

### Post by lkraemer on 2010-01-19
K-Bar,
It would be interesting to try portmon with an External Serial Modem to see
what exactly Juno is using for the login information.  I'd suspect that
once your login was correct everything would work correctly.

[http://technet.microsoft.com/en-us/sysinternals/bb896644.aspx](http://technet.microsoft.com/en-us/sysinternals/bb896644.aspx)

You should be able to set portmon for a capture of the specific serial port
and capture just the login and password.

Also, Juno, in the past provided a .deb for some Linux distros as per
several postings on this forum.

Also:
[http://www.autohotkey.com/forum/topic10664.html](http://www.autohotkey.com/forum/topic10664.html)

lk

---

### Post by K-Bar on 2010-01-19
That did it,  thanks guys.  Gnome-ppp now launches from the desktop.

---

### Post by Shazaam on 2010-01-19
Where I live-
DSL (requires extra unneeded phone services to qualify)= $62.50/mo.
Cable internet= (requires cable tv) $85.00/mo.
Dialup- $9.95/mo.
Food- essential to life
Since I like living it's dialup for me.  :)

---

### Post by colorpurple21859 on 2010-01-30
if juno and netzero are the same here is a howto [http://www.linuxquestions.org/questions/slackware-14/netzero-628659/](http://www.linuxquestions.org/questions/slackware-14/netzero-628659/)

---

### Post by *syst3m on 2010-01-30
I've never tried this with Netzero and cant guarantee it will work but if you have an old computer just laying around you should be able to use Smoothwall [http://www.smoothwall.org/ ]("http://www.smoothwall.org/")

here's a tutorial
[http://www.youtube.com/watch?v=fEkO_mQOGGQ&feature=related](http://www.youtube.com/watch?v=fEkO_mQOGGQ&feature=related)

Minimum System Requirements 
Intel Pentium 200 or compatible processors
128 megabytes of RAM. More RAM is required for additional services.
2 gigabytes hard disk – IDE and SCSI devices supported.
2 Network Cards and also 1 modem possibly external 
If the system BIOS supports boot without keyboard, required for the initial installation.
Video card Only required when installing.
Monitor Only required when installing.
CD-ROM Only required when installing.

I've setup Smoothwall with cable and also a dsl Internet connection and know it works.
And if you cant use Smoothwall... just think of the knowledge you gained but...   

**This might be easier**
You could set up an old computer running ms winblows xp,2k, or whatever and use it as a dialup server. I know this works because I haven't always had Comcast.

What you will need

An old computer using ms winblows with Internet Connection Sharing enabled and a modem, network cards, phone line, and a cross-over cable

jack -- phone line -- modem - old computer - nic - xover cable -- nic - main computer 

How to configure Internet Connection Sharing in Windows XP
[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

and if you don't have a spare computer pick one up at a garage sale or one that some one is throwing out that might be salvageable

---

