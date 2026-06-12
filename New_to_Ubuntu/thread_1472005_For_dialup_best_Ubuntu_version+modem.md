---
title: "For dialup: best Ubuntu version+modem?"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by tyler9 on 2010-05-04
Hi--I'm planning to install Ubuntu on a new machine. I'll have to use a dialup net connection, so I'm wondering: 

Which Ubuntu version is easiest to use with an external dialup modem? 

And what modems have Ubuntu users have good experiences with?

I searched the forum and read many posts about configuring Ubuntu for dialup; I'm prepared to do what's necessary for setup, but would like to avoid the blocking problems some have experienced.

Aren't most problems caused by internal modem cards, rather than external modems?

To my inexperienced eye, this US Robotics USB looks good:
[http://www.usr.com/products/modem/modem-product.asp?type=media&sku=USR5637](http://www.usr.com/products/modem/modem-product.asp?type=media&sku=USR5637)
...well-supported and documented:
[http://www.usr.com/support/product-template.asp?prod=5637](http://www.usr.com/support/product-template.asp?prod=5637)

...well-reviewed on newegg--several reviews by Ubuntu users:
[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16825104006](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16825104006)

Anyone here with similar good experiences with this unit?

fyi, for other dialup users, this seems a helpful site:
[http://www.modemhelp.org/support.html](http://www.modemhelp.org/support.html)

Great site! Thanks for info--

---

### Post by ankspo71 on 2010-05-04
I have absolutely no experience with dialup while using linux, but I found you a link. 

[http://hardware4linux.info/search/](http://hardware4linux.info/search/)
Select "working modems" from the "Type" dropdown list.
then click search. There are alot of results.

Scoring:
5	Works out of the box.
3	Works with modifications.
0	Don't know or not supported by hardware.
-3	Works partially.
-5	Does not work.

You might also want to check out [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

---

### Post by pj_kare on 2010-05-04
Can't help you with the version of Ubuntu to decide on, I have only used Ubuntu, not Xubuntu, Kubuntu etc. Though I have used Ubuntu-> Feisty Fawn, Jaunty Jackalope and currently still using Karmic Koala, (Have to wait for Lucid disc through mail because of dialup) and although setting up dialup for the first time can seem a bit daunting, once you have done it a couple of times it gets easier and quicker. (As with anything I guess).

I downloaded gnomePPP (and its dependancies) through XP, (that's all I need to get modem to work) it's available in the repos but that isn't much good when you can't get online to begin with.

I can do a clean re-install of Ubuntu and be online within a few minutes ( well, maybe 5-10 mins ). I have both a Banksia Wave SP56, and a Netcomm Wave SP56 which are the basically the same modem with different name, exactly the same to set up, and both work well, shame I have a really bad phone line though, and have to use a modem string to dial them back to 26400 :( 

Got the Banksia on ebay for about a dollar (postage cost more, lol), for the GF, but she has since gone back to only using XP.

I have a Motorola internal modem that I haven't even bothered to try and use in Ubuntu. It's strictly for XP use only.

I have written my own set up instructions (for myself in case I forget how). And although it might seem a lot at first, as I said previously, it gets easier each time you do it.

> Aren't most problems caused by internal modem cards, rather than external modems?From what I've seen in the forums....yes, as it appears most internal modems are winmodems, modems designed for use with Windows. And it takes quite a bit more to compile/set-up a driver for them. I'm no expert though and found it easier NOT having to worry about a driver. (No driver to install for my external modems.)

Sorry about the long post, hope it's of some use.:P

---

### Post by cascade9 on 2010-05-04
That US Robotics 56K USB modem looks like it would work well with linux. Rare, most USB modems are winmodems and hard/impossible toget going well with linux. 

BTW, almost all the serial port modems I've ever seen work well with linux. There might be a few that dont, but generally they work under linux well (and to be honest, they work better under windows than winmodems do). 

> **pj_kare said:**
> I can do a clean re-install of Ubuntu and be online within a few minutes ( well, maybe 5-10 mins ). I have both a Banksia Wave SP56, and a Netcomm Wave SP56 which are the basically the same modem with different name, exactly the same to set up, and both work well, shame I have a really bad phone line though, and have to use a modem string to dial them back to 26400 :( 

Sounds like you have a 'pair-gain' phone line. Basicly, thats a single phone line that has been split to service 2 different phone numbers. 

Happens far more than it should, but not much you can do about it. 

> **pj_kare said:**
> 
From what I've seen in the forums....yes, as it appears most internal modems are winmodems, modems designed for use with Windows. And it takes quite a bit more to compile/set-up a driver for them. I'm no expert though and found it easier NOT having to worry about a driver. (No driver to install for my external modems.)

Almost all internal and USB modems are winmodems. 

Its not so much a 'modem designed to be used with windows', more a control chip (not a 'real' modem chipset) with software control.

---

### Post by pj_kare on 2010-05-04
> **cascade9 said:**
> Sounds like you have a 'pair-gain' phone line. Basicly, thats a single phone line that has been split to service 2 different phone numbers.

Not really sure what you actually mean there, we may indeed have a pair-gain line, unless you are thinking we both go online at the same time, we don't, we have to share the same line, that is, GF goes online for a while...disconnects, and then I go on, or vice versa. Only 1 of us goes online at a time.

Telstra did a Molds test, and they told us we needed the modem strings, stops us from constantly getting disconnected and connection is more stable.

We live 13k out of town on a farm, the phone lines are old as........ Whilst the lines out on the main road get work done on them the ones on the property don't, a backhoe went through ours at one stage and it was patched up. (Twisted and taped.)

Thanks for clarifying the winmodem. If we ever move back into town (or elsewhere) we'll be able to get broadband.

Apologies to OP, don't mean to hijack your thread.

---

### Post by lkraemer on 2010-05-04
The best modem to use with Linux is an older US Robotics (Serial)
Hardware Modem.  These are listed on [www.ebay.com](www.ebay.com) and they work well,
and are easy to setup.  The only negative is the serial cable and the
extra Wall Wart for Power.  You can also use a Sabrent USB to Serial
Converter if your Computer doesn't have a Serial Port.  The USB to
Serial Converter works wonderful.

Some folks use the internal Win-Modem by going to [www.linmodems.org](www.linmodems.org) 
and asking for help/support.  Marvin and those folks will assist with
helping you find the correct drivers by using a script to identify what
type Win-Modem you have etc.....

But typically you are looking at several days of emails and postings to
get through that process, while the old reliable hardware Modem
shouldn't take more than 30 minutes of work to get it all set up.
And your Emails MUST BE IN PLAIN TEXT.......Or they will be REJECTED.
So, you will need to set and send your emails accordingly.........

You may need to download wvdial and all the dependencies (4) and set it
all up before going to Gnome-PPP.  I've not had much luck just trying to
get Gnome-PPP working without first getting everything setup with wvdial.

But, I guess it's worth a try.

I've posted a Guide on the Ubuntu Forum that might serve you well in
your attempt.  It's located at:
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56)
Posting #4

You may not need to change the permissions of pppd to enable dialout
on the later versions of Ubuntu.  If you must use Root permission to
dialout then it still applies.

When you get started, and need help or have a question just PM me, and
I'll try to assist.

Good Luck.

lk

---

### Post by mastablasta on 2010-05-04
I didn't know they still make those. :-)
Anyway just wanted to say that i think Linux Mint comes packaged with gnomePPP. Otherwise make sure you have on install (if you dont' have broadband access...)

---

### Post by pj_kare on 2010-05-04
@lkraemer

This is how I have to set up modem.....If I try any different it won't work.
(Any tips to make it easier would be great, as I will be doing a clean install of Lucid when I get the disc.)

Install in this order....
```
1)  libxplc0.3.13_0.3.13-1build1_i386.deb

2)  libwvstreams4.4-base_4.4.1-0.2ubuntu2_i386.deb

3)  libwvstreams4.4-extras_4.4.1-0.2ubuntu2_i386.deb

4)  libuniconf4.4_4.4.1-0.2ubuntu2_i386.deb

5)  wvdial_1.60.1+nmu2_i386.deb

6)  gnome-ppp_0.3.23-1_i386.deb
```(wvdial is a dependency of gnome-ppp so have to install it)

Setup pppconfig: 
Open *terminal* window, type: sudo pppconfig -Enter-
enter password then -Enter-
run through pppconfig setup, select CHAP. (CHAP for me anyhow)

In *terminal* type:

sudo chmod +s /usr/sbin/pppd -Enter-
sudo chmod a+x /usr/sbin/pppd -Enter-

Start Gnome-PPP and set it up.........Can connect as soon as this is done.

EDIT: There may be later versions of .deb files. I still use the ones listed.

---

### Post by _duncan_ on 2010-05-04
@pj_kare

Since you are going to set up using pppconfig anyway, why not use pon/poff to connect/disconnect and then download/configure wvdial or gnome-ppp once connected?

What I'm proposing after a fresh install is this:

1. configure dial-up connection using pppconfig.
```
sudo pppconfig
```
2. instead of the chmod commands to change permission, add your user account to the 'dip' group:
```
sudo adduser [COLOR="Blue"]yourUserID[/COLOR] dip
```
3. log out and log back in for step 2 to take effect. [COLOR="Red"](This is important)[/COLOR]

4. connect to the internet with your newly-configured pppd:
```
pon
```
5. update the package list so you can download stuff from the repo.
```
sudo apt-get update
```
6. install gnome-ppp and its dependencies, including wvdial if it's not present.
```
sudo apt-get install gnome-ppp
```
7. disconnect
```
poff
```
8. configure dial-up using gnome-ppp as you normally would and use the GUI dialer the rest of the way.


I have tested this method up to Karmic although I'm technically on broadband 3 releases back. Been using ubuntu since Breezy. Can't test it on Lucid though since I no longer have a dial-up account and gave away all my dial-up paraphernalia to people who still need them. Also getting a bit tired of the normally "ranty" dial-up threads I used to participate in, but this looks like a reasonable discussion on dial-up so I'm documenting my time-tested process here before I totally forget.

The advantage with this process is you don't have to install anything manually. Nor do you have to keep track of dependencies from one release to another. I have to warn you though that step 5 takes a long time on a dial-up connection. But you will have to do it eventually anyway if you intend to update the system or add applications from the repos.

---

### Post by tyler9 on 2010-05-04
Thanks for info!

In trying to get a grip on this modem Q, I thought in "binary" terms: internal or external. It really seems an external modem is likely to have fewer problems. 

Many of the dialup-related posts I've read here involve configuring Ubuntu for an existing modem, already in the user's machine.

But I'm starting clean, new machine, new install+setup. So being "upstream" I can choose whatever might prevent avoidable downstream problems. I'm prepared for the configuration process; but after config, I want the modem to work! 

I read about Winmodems+soft modems; it's always seemed that external modems have fewer problems by providing everything needed for a hassle-free setup. And USRobotics is a well-respected brand. (Love their website design, too!) 

I thought the above-linked USRobotics USB modem would do the trick, as it works for the Ubuntu users who posted reviews; but last nite I read in "Beginning Ubuntu Linux" by Keir Thomas and Jaime Sicam-3rd Edition, 2008-p141: "If your modem is external and connects to the serial port, then there's a very good chance Ubuntu will work fine with it. However, if the modem connects to the USB port, ....then Ubuntu support is less certain." 

And lkraemer says above:
"The best modem to use with Linux is an older US Robotics (Serial) Hardware Modem. These are listed on [www.ebay.com]("http://www.ebay.com") and they work well, and are easy to setup. The only negative is the serial cable and the extra Wall Wart for Power. You can also use a Sabrent USB to Serial Converter if your Computer doesn't have a Serial Port. The USB to Serial Converter works wonderful."

...great info--I'll try a serial hw modem and get the Sabrent converter--Yep, the new machine won't have a serial port; but it does have USB3 ports!

Btw: I know that dialup access isn't a "glamour" topic, so I especially appreciate the help. In searching this forum before posting, I found these comments:

"It seems so weird to hear people still trying to use dial-up"

"People still use dialup in Africa ... but in the US?  I'm astonished."

"I just found out about this, and wanted to get something out there for the poor saps still on dial-up."

Unfortunately, some saps lack broadband access; other saps lack financial resources.

So thanks again to all for above links and info!

---

### Post by Rasa1111 on 2010-05-04
Good info in this thread! 
thanks for posting it tyler.

 I also had dial-up still until about 4 months ago. lol
and i tried to get my internal 'winmodem' working in ubuntu for a week straight. :lol:

 I know a little more about external modems now...
but at the time...  my same reason for still using dial-up~ was preventing me from buying an external modem to try.   >  other saps lack financial resources  yep, that was it. lol

My decision had already been made to keep Ubuntu and use nothing else...
so I was determined to find the easiest [and cheapest] solution to get me online with Ubuntu, no matter what i had to do. (I was NOT going back to windows) no matter what. :lol:

eventually I came across a "special deal" by my ISP (was on netzero dial-up)
but the deal was that I would get DSL for 6 months, for $10 a month~
and after 6 months, I would have to pay about 19-20 $ a month. 

well, I has just quit smoking [hack] cigarettes, 
and as 'poor' and [financially challenged] as I am...
I figured that the old ciggy money could go towards a better connection 
(simply so I could use Ubuntu) lol

 Dial-up was starting to get on my nerves ...
but if I *had* gotten my winmodem working...
I would probably still be using the dial-up.

Many people are 'spoiled' with their connection speeds today....
and as soon as they hear of someone ["in america"]..
still using dial-up..
they get on a' high horse' and think [how funny, and how weird] that is that some people still ***have*** to use dialup. 

 as it the dial-up users dont feel bad enough already about still having to use it...
(those 'spoiled' people are half the reason for us feeling bad about it i think) :lol:
but they just go and make it worse with their ignorant, childish comments about "living in a cave" or "It seems so weird people still trying to use dialup"
and [ "Im astonished"]

really? astonished? thats what it takes to astonish you? :lol:
funny. 

This thread may come in handy in the future,
for me, and many other "poor saps". lol

 thanks <3
and good luck

---

### Post by GeorgeVita on 2010-05-04
Hi to all above!

[SIZE="1"](edit: 2nd approach to be 'in topic')
[/SIZE]

a. It is easier to use an external dial-up modem
b. Ubuntu 8.04 LTS has all dial-up options pre-installed (gnome-ppp, wvdial, pppconfig)
c. 10.04 released with wvdial into LiveCD but is not installed by default!

Although 8.04 includes by default the support, nobody can resist to the new 10.04 LTS, so get your modem (external preferred) try it and come back here for support!

In case an offline installation of wvdial is needed, read:
[http://ubuntuforums.org/showthread.php?p=7245790](http://ubuntuforums.org/showthread.php?p=7245790)
 
Regards,
George

---

