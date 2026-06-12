---
title: "Safety Using Unsecured Wireless Network"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by lhb1142 on 2010-07-04
My wife and I are going on a vacation and we shall be taking our computer.

There are many wi-fi hotspots, all unsecure, through which we can connect to the internet including hotel/motels (which, even though they generally have a password, are unsecure because many guests - and you don't know who they are! - have it).

My problem is that, on this vacation, I am going to have to do some online banking. I **must** obtain my credit card bills and must pay them, as well as other bills, via online checking. I have no other practical option.

Is it relatively safe (safer?) to use a dial-up connection rather than the available broadband connection (which is unsecure) to access financial sites?

If I were to use the unsecured broadband connection but, rather than typing my logins and passwords, *copied and pasted* them into the requisite dialog box on the [financial] site(s) from a previously prepared document, would this be relatively safe (safer?)?

Does using [Ubuntu] Linux rather than Micorosoft Windows make a difference in the possibility of interception, especially by such things as keyloggers which may be attached to a hotel's network?

I am not "computer-sophisticated" so I cannot prepare a "virtual machine." In any case, I do not know if that would make accessing financial sites any safer.

I am currently using Ubuntu v.10.04 'Lucid Lynx' and I have both ClamAV and Firestarter installed.

I am sure others here may have had the same question; any answers or advice would be welcome. Thank you for reading this.**

---

### Post by MichealH on 2010-07-04
I would suggest not taking any chances at all and playing it safe. Try it on maybe a Private Hotel Network if there is one. If though There is none, I would suggest trying to be safe when browsing online. Especially on a public network.

---

### Post by barney385 on 2010-07-04
There are good encryption programs you can use.

---

### Post by warfacegod on 2010-07-04
Many hotel and other "public access" wireless networks are set up as ad-hoc. That style of network is even more unsafe than the usual Infrastructure type usually found in your house, for example.

I worked in a Hotel as an Engineer (fancy work for a fix it guy!) several years ago. Being the only guy on the entire staff that could spell "Internet", I got "voted" (read drafted) on call hotel computer expert. I got dozens of complaints from the guests about there computers and anti-virus apps going berserk after connecting to the wireless network.

If you value your banking privacy, *don't* use a "public access" points.

---

### Post by lhb1142 on 2010-07-04
> **barney385 said:**
> There are good encryption programs you can use.

Such as ... ?

I already have TrueCrypt installed and I have encrypted a folder on a USB flash drive but I do not know how to use TruCrypt to connect to the internet (if that is possible). Would using it prevent nefarious persons from obtaining my logins and passwords?

Would you please enlighten me further, perhaps with some links to sites which offer the requisite information and instructions?

To those who say I should not use an unsecure network - I agree with you, of course. But, if you read my question properly, you would see that I wrote that I have no choice in this situation. Thus I **must[B]**[/B] use such sites.

I am looking for specific information on means to make such connections [at least more] secure.

Does anyone have any information concerning *copying and pasting[I]*[/I] logins and passwords rather than actually typing them?

In addition, what about a dial-up connection? Is that more secure, especially using Linux?

Thank you.

---

### Post by QLee on 2010-07-04
[QUOTE=lhb1142]My wife and I are going on a vacation and we shall be taking our computer.
...
My problem is that, on this vacation, I am going to have to do some online banking. I must obtain my credit card bills and must pay them, as well as other bills, via online checking. ...[/QUOTE]

The most important consideration since you will be taking your own computer with you on the vacation is that the financial institution with which you will be doing online banking has a secure site for that banking.

To put it not-technically, it's done from an "https" URL.

Your browser will indicate a secure site (i.e. Firefox has a lock icon in the status bar).

Since communication between your computer and the site are encrypted, it's as secure as if you were doing it from home.

---

### Post by lhb1142 on 2010-07-04
> **QLee said:**
> The most important consideration since you will be taking your own computer with you on the vacation is that the financial institution with which you will be doing online banking has a secure site for that banking.

To put it not-technically, it's done from an "https" URL.

Your browser will indicate a secure site (i.e. Firefox has a lock icon in the status bar).

Since communication between your computer and the site are encrypted, it's as secure as if you were doing it from home.

Yes, all of my financial institutions use "https" URLs. What I am most concerned about is "interception" programs, such as keyloggers and their ilk, which can be placed on an unsecure network.

Do you know if *copying and pasting[I]*[/I] the logins and passwords is safer than typing them? Is a dial-up connection inherently safer than using the unsecure network?

In short I would like to know what *others[I]*[/I] do when faced with similar situations.

(And, by the way, yes I will be using my own computer; I would not even *think[I]*[/I] of using a "public" computer to access *any[I]*[/I] site (including my e-mail) in which I must enter a login and password.)

Thank you for reading this and for replying to me.

---

### Post by J V on 2010-07-04
> Yes, all of my financial institutions use "https" URLs. What I am most  concerned about is "interception" programs, such as keyloggers and their  ilk, which can be placed on an unsecure network.They don't log keys, they log packages: And yes they can intercept your data... Banks are supposed to have good security but I've heard many a tale about banks that, although they used shttp, sent the login data unsecured in the headers....

> Do you know if *copying and pasting* the logins and passwords is  safer than typing them? Is a dial-up connection inherently safer than  using the unsecure network?No it isn't, but keyloggers don't work on ubuntu, it's not like someone can read your computer over the network.

> In short I would like to know what *others* do when faced with  similar situations.I would use TOR, it is guarenteed to be much more secure... [http://www.torproject.org/](http://www.torproject.org/)

---

### Post by QLee on 2010-07-04
[QUOTE=lhb1142]Yes, all of my financial institutions use "https" URLs. What I am most concerned about is "interception" programs, such as keyloggers and their ilk, which can be placed on an unsecure network.[/Quote]

Encrypted end to end. What could anyone see in between other than there were packets going between the two IP addresses.

[QUOTE=lhb1142]In short I would like to know what *others* do when faced with similar situations.[/QUOTE]

It's what I do. IPTables block incoming from any network I'm on, you probably have your Firestarter doing that too.

---

### Post by lhb1142 on 2010-07-04
> **J V said:**
> They don't log keys, they log packages: And yes they can intercept your data... Banks are supposed to have good security but I've heard many a tale about banks that, although they used shttp, sent the login data unsecured in the headers....

No it isn't, but keyloggers don't work on ubuntu, it's not like someone can read your computer over the network.

I would use TOR, it is guarenteed to be much more secure... [http://www.torproject.org/](http://www.torproject.org/)

I just checked TOR - this is a program to make internet connections anonymous, not to protect others from intercepting logins and passwords to financial institutions over an unsecure network connection.

I am intrigued by your claim that keyloggers do not work on Ubuntu connections; do you have a link to a site which explains this further? That would be the answer to my "problem" as all my financial institutions do use "https" and even ask for answers to personal questions prior to actually allowing me to login.

I guess that keyloggers, physically attached to an unsecure network, either wired or wireless, are my primary concern; I am also concerned that someone could "tap in" to my computer to see exactly what I am doing. I would hope that Linux is immune from both.

Thank you for your reply to me.

---

### Post by J V on 2010-07-04
Keyloggers don't work on ANY connections, they are a client side malware like a virus, and they don't work on linux (Unless you run them yourself and give them your password)

What you are reffering to are "Packet sniffers" - and yes they can be a problem especially over a crowded wireless network... It should be fine, but if you suspect your bank has lax security (Hell, ABN amro got caught with unencrypted headers) then I'd use TOR... What it does is bounce your connection secured around the world to somewhere else with (Presumably) a more secure connection...

---

### Post by lhb1142 on 2010-07-04
> **QLee said:**
> Encrypted end to end. What could anyone see in between other than there were packets going between the two IP addresses.



It's what I do. IPTables block incoming from any network I'm on, you probably have your Firestarter doing that too.

THANK YOU. You are correct - that is how I have my Firestarter set up. And I am on my own home computer with my own connection - I am trying to learn how to set up security so that when we do go on our vacation, I will have everything in place to "compute securely."

After all, we will want to obtain our e-mail daily as well as access some other sites which require logins and passwords.

The last time we went on vacation (several years ago, when security wasn't such a concern as it is today), we were still using Windows. We did not need, at that time, to access any financial institutions but we did have to access our e-mail. When we got home, we changed all of our passwords (which we normally do only once a year).

But now, with the amount of "bad things" going on, I am naturally quite concerned as to the security of my financial dealings.

I want to thank you, and everyone else, for replying to my question. I would still like to read others' experiences and opinions concerning dial-up connections, copying and pasting logins and passwords, and any other such [possible] security-enhancing procedures.

---

### Post by J V on 2010-07-04
First, get rid of firestarter, it's been out of date for ages, and ubuntu already has a firewall installed: You won't need a firewall for everyday use.

This isn't windows, you don't need to go security crazy unless you are doing something strange...

As for pasting passwords: Myth - keyloggers are designed to catch stuff, and if you store the password on a file it just makes your system a LOT easier to break into... delete the file and just remember your passwords... add to that that it would take a lot of work to get keylogger onto your system and you're set...

---

### Post by mcphargus on 2010-07-04
Packet-sniffing is a threat to be aware of, but not necessarily something that's going to be happening on a hotels public network, and in the case of you visiting a site where they use ssl (you're bank wouldn't be in business long without this), all the sniffing party is going to grab is encrypted packets.

Ask other patrons, if the network is running very slow, this can be indicative of two things, 1) the infrastructure is crap (more likely in a cheap hotel) or 2) there's a man-in-the-middle attack going on. The latter is a situation where you would want to disconnect.

Also, stay off ad-hoc networks. You'll know a network is ad-hoc because there will be a computer next to the wireless icon in Ubuntu's network manager.

Keep in mind, Tor also does its best to encrypt traffic end to end, so it's actually increasing your security beyond the standard anonymizing capabilities usually associated with it.

If you're obtaining your email, try to do that through an encrypted connection as well, if it's gmail, go through [https://www.gmail.com](https://www.gmail.com), otherwise you'll have to find out if your email provider offers an encrypted connection. If you're really cautious, you can encrypt email that you send with gnupg, but information on how to do that is for a different thread :)

Sorry if this post is a little wordy :)

---

### Post by lhb1142 on 2010-07-04
> **J V said:**
> Keyloggers don't work on ANY connections, they are a client side malware like a virus, and they don't work on linux (Unless you run them yourself and give them your password)

What you are reffering to are "Packet sniffers" - and yes they can be a problem especially over a crowded wireless network... It should be fine, but if you suspect your bank has lax security (Hell, ABN amro got caught with unencrypted headers) then I'd use TOR... What it does is bounce your connection secured around the world to somewhere else with (Presumably) a more secure connection...

Thank you. I just "Googled" < packet sniffers ubuntu > and found a myriad of answers, several of which I will examine further.

It *appears[I]*[/I] that if I use a bit of common sense (running my financial institutions from my Bookmarks, for example) I should be all right.

But, in the absence of any information to the contrary, I think I will use a dial-up connection (in conjunction with Firestarter, of course) for my financial transactions and copying and pasting logins and passwords (for e-mail, etc.) over unsecure broadband connections.

It may be overkill, of course, but I want to be safe.

Thanks again for writing to me.

---

### Post by J V on 2010-07-04
> It *appears* that if I use a bit of common sense (running my  financial institutions from my Bookmarks, for example) I should be all  right.

But, in the absence of any information to the contrary, I think I will  use a dial-up connection (in conjunction with Firestarter, of course)  for my financial transactions and copying and pasting logins and  passwords (for e-mail, etc.) over unsecure broadband connections.

It may be overkill, of course, but I want to be safe.Insanity on so many levels :)

Running from bookmarks changes nothing, pasting changes nothing, Firestarter may make things even less secure if you leave it running the  whole time.

Dial-up is more secure yes, that's a good thing.

---

### Post by QLee on 2010-07-04
[QUOTE=lhb1142]
After all, we will want to obtain our e-mail daily as well as access some other sites which require logins and passwords.[/QUOTE]

Gmail (for one) offers secure signon for email, you probably don't want your email passwords going in clear text.

[QUOTE=lhb1142]I would still like to read others' experiences and opinions concerning dial-up connections, copying and pasting logins and passwords, and any other such [possible] security-enhancing procedures.[/QUOTE]

Even if your system is not compromised by a keylogger running on it (where copy and paste might help), a keylogger which you were worried about is still possible if you use a wireless keyboard and someone is close enough to you with the correct equipment but since you aren't a secret agent, it's probably not a concern.

Dialup is certainly slower and more expensive, and for very marginal extra security (merely no local packet sniffers - the 'Net is still a jungle).

---

### Post by J V on 2010-07-04
Wireless keyboard keylogging... hmm... Didn't think about that... Will google further...

---

### Post by lhb1142 on 2010-07-04
> **mcphargus said:**
> Packet-sniffing is a threat to be aware of, but not necessarily something that's going to be happening on a hotels public network, and in the case of you visiting a site where they use ssl (you're bank wouldn't be in business long without this), all the sniffing party is going to grab is encrypted packets.

Ask other patrons, if the network is running very slow, this can be indicative of two things, 1) the infrastructure is crap (more likely in a cheap hotel) or 2) there's a man-in-the-middle attack going on. The latter is a situation where you would want to disconnect.

Also, stay off ad-hoc networks. You'll know a network is ad-hoc because there will be a computer next to the wireless icon in Ubuntu's network manager.

Keep in mind, Tor also does its best to encrypt traffic end to end, so it's actually increasing your security beyond the standard anonymizing capabilities usually associated with it.

If you're obtaining your email, try to do that through an encrypted connection as well, if it's gmail, go through [https://www.gmail.com](https://www.gmail.com), otherwise you'll have to find out if your email provider offers an encrypted connection. If you're really cautious, you can encrypt email that you send with gnupg, but information on how to do that is for a different thread :)

Sorry if this post is a little wordy :)

Wordy? Not! Your reply is *exactly[I]*[/I] what I'm looking for! Thank you!

I will do some more research on TOR. It may be a valuable adjunct.

By the way, I already use Gmail in encrypted form.

Thank you again.

---

### Post by lhb1142 on 2010-07-04
> **J V said:**
> Insanity on so many levels :)

Running from bookmarks changes nothing, pasting changes nothing, Firestarter may make things even less secure if you leave it running the  whole time.

Dial-up is more secure yes, that's a good thing.

Thank you. I thought Firestarter was a good program to have; evidently it is not?

---

### Post by mcphargus on 2010-07-04
For all intents and purposes, forget that such a thing as a keylogger even exists. They're usually in the form of a device that connects between the computer and the keyboard. So unless you hand your laptop to someone or leave your hotel room unlocked, you're pretty safe from those. You cannot log keystrokes over a network connection.

---

### Post by lhb1142 on 2010-07-04
> **QLee said:**
> Gmail (for one) offers secure signon for email, you probably don't want your email passwords going in clear text.



Even if your system is not compromised by a keylogger running on it (where copy and paste might help), a keylogger which you were worried about is still possible if you use a wireless keyboard and someone is close enough to you with the correct equipment but since you aren't a secret agent, it's probably not a concern.

Dialup is certainly slower and more expensive, and for very marginal extra security (merely no local packet sniffers - the 'Net is still a jungle).

I don't use *anything[I]*[/I] wireless except an internet connection if that's all a hotel offers (no wireless keyboards - I use a netbook computer).

Any enhanced security will allow me to sleep better at night in the "jungle."

Thanks for writing!

---

### Post by J V on 2010-07-04
> **lhb1142 said:**
> Thank you. I thought Firestarter was a good program to have; evidently it is not?I have a premade list of why not to use firestarter :)

> The most often advised firewall interface is "Firestarter", but nowadays its a bad idea to use it. It hasn't been developed for ages now, and because ufw (A command line configuration tool) is installed, Firestarter will conflict with already running services.

On top of that, while it runs, it runs as root, so if someone were to exploit a vulnerability in Firestarter, it would give them complete access to your system.

The current interface suggestion is "[gufw]("apt://gufw")" (Click to install) which, once again, is not a firewall, but a means to configure the default firewall.

---

### Post by lhb1142 on 2010-07-04
> **mcphargus said:**
> For all intents and purposes, forget that such a thing as a keylogger even exists. They're usually in the form of a device that connects between the computer and the keyboard. So unless you hand your laptop to someone or leave your hotel room unlocked, you're pretty safe from those. You cannot log keystrokes over a network connection.

Thank you for this information. I had thought that someone could in fact install something on a network (perhaps at the router) by which they could capture keystrokes. (You can see that I am not a "computer sophisticate" but just someone who reads the "horror stories" in newspapers, etc.)

Thank you again.

---

### Post by lhb1142 on 2010-07-04
> **J V said:**
> I have a premade list of why not to use firestarter :)

I just went into the Synaptic Package Manager and uninstalled Firestarter and installed gufw.

I had not realized that Ubuntu already included a firewall.

Thank you very much for the information.

---

### Post by J V on 2010-07-04
By default ubuntu uses IPTables, which is, essentially all a firewall is...

UFW is a commandline tool to configure it, and GUFW is a graphical tool to use the commandline tool...

But in the end, you shouldn't need it unless you are installing servers or something on your system...

---

### Post by lhb1142 on 2010-07-04
I want to again thank everyone who has written.

The information posted has been extremely useful to me.

I am going out now - after all, it IS the Fourth of July!

But I'll be back later or, more probably, tomorrow to see if there are any further comments.

Thanks again. I really feel better now - and so does my wife (and THAT is the most important thing!).

---

### Post by QLee on 2010-07-04
[QUOTE=lhb1142]Thank you. I thought Firestarter was a good program to have; evidently it is not?[/QUOTE]

Firestarter is a GUI front end to iptables, it makes it somewhat easier for people to write rules. The GUI does not have to be running for those previously written iptables rules to be in effect, they start with networking. Thus, no need to run a "root" application during surfing and the "hits" logged would probably drive you crazy if you watched them anyway.

You could switch to ufw if you want but deny incoming would be the same no matter which GUI front-end writes the information to iptables.

---

### Post by Bachstelze on 2010-07-04
Uh, guys? Any serious bank will use HTTPS for all data transmissions, so the fact that the wireless network is unsecured is totally irrelevant: transmissions will be encrypted anyway.

---

### Post by J V on 2010-07-04
Yes, but unfortnately some banks recently got caught that they send the login data unencrypted and encrypt everything *after that* - just make sure the "Secure" bar is there on the login page and it will be fine...

---

### Post by mcphargus on 2010-07-04
> **QLee said:**
> Even if your system is not compromised by a keylogger running on it 

If your system is compromised to that degree, the keys you're touching are the least of your worries :)

Don't factor the following into your security concerns, unless you work for the CIA or something. I merely post the following because it makes for interesting reading.

This takes an MIT degree and a decent pile of capital to execute, but keystroke sniffing via sound waves has become possible within the last few years. [http://www.schneier.com/blog/archives/2009/03/sniffing_keyboa.html]("http://www.schneier.com/blog/archives/2009/03/sniffing_keyboa.html")

---

### Post by QLee on 2010-07-04
[QUOTE=mcphargus]If your system is compromised to that degree, the keys you're touching are the least of your worries :)[/QUOTE]

+1 

...And in that case, the black hats would already have the passwords, before these people even leave on their holiday.

---

### Post by J V on 2010-07-04
Can't be long before someone comes up with a keyboard that deliberately emits random noise on every keystroke :)

---

### Post by mcphargus on 2010-07-04
> Can't be long before someone comes up with a keyboard that deliberately emits random noise on every keystroke.

I used to have an operating system that did something like that. It would *ding* on nearly every other keystroke, and the window I was working with would lose focus to be replaced by some erroneous complaint about the way I was trying to do my job. It was called win-something-or-other. Glad those days are over.

---

### Post by lhb1142 on 2010-07-05
I again want to sincerely thank everyone who has contributed to this thread. The answers and information given have been very useful to me, especially the information about TOR and about the ufw firewall (and the gufw graphical interface).

Everyone who offered opinions and suggestions most definitely contributed to my and my wife's peace of mind as we were quite concerned about the possibilities of identity theft or financial theft brought about by the use of our computer on the road.

Thanks to all of you our fears have now been allayed.

Just as an aside, I had installed ClamAV and yesterday I ran a scan of my /home (the recommended scan); one virus was picked up (of course it could not affect Ubuntu); it was something I had downloaded a few years ago when I was still using Windows. I kept the file as it does contain some interesting information but I find it informative to discover that it was infected. I "guess" I won't send that file to anyone else (unless I don't like you - ***BEWARE[B][I]***[/B][/I] ---  :) - ]just kidding, of course]).

Thanks again to everyone! The people on the Ubuntu forums, each and every one of you, are the most helpful, kind, and generous people with whom I have ever dealt when having a computer question.

Lawrence

---

### Post by Grim-Fandango on 2010-07-07
> I would still like to read others' experiences and opinions concerning  dial-up connections, copying and pasting logins and passwords, and any  other such [possible] security-enhancing procedures.

I use KeepassX to store my passwords; I have a terrible memory. :)

---

### Post by bodhi.zazen on 2010-07-07
On an unsecured network you do not need to do all *that* much ...

1. Enable ufw

```
sudo ufw enable
sudo ufw default deny
```

2. Since the network is not secured, you must assume your packets can be sniffed. You should avoid financial transactions if possible.

If you *must* , I suggest you tunnel your traffic over ssh :

[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

---

### Post by warfacegod on 2010-07-07
I read an article a while ago, that I can't find of course, spoke of a Bank in Florida that was considering giving out Ubuntu discs or USB's because they regarded a Live Environment as safer for on-line banking than an Installed OS. I'll try again to find it.

---

### Post by bodhi.zazen on 2010-07-07
> **warfacegod said:**
> I read an article a while ago, that I can't find of course, spoke of a Bank in Florida that was considering giving out Ubuntu discs or USB's because they regarded a Live Environment as safer for on-line banking than an Installed OS. I'll try again to find it.

The Live CD is not safer as it is not up to date and does not have the latest security updates.

Internet banking has less to do with the operating system and more to do with Phishing and securing your browser. The only "exception" to that would be key loggers and Window sis certainly more susceptible then Linux to key loggers, but this risk can be minimized on Windows as well (do not install software from untrusted sources and do not browse the web with the admin account).

IMO you should use NoScript at a minimum.

---

### Post by AlanR8 on 2010-07-07
This has been an interesting thread and informative! Just to add my little bit of perceived wisdom. Like warfacegod said, I also saw the same reports and using a "live" Ubuntu environment makes a lot of sense as nothing is stored locally.

The other thing is access to the Interweb from hotels. This is something close to my heart as I spend a lot of time away from home when working. I absolutely REFUSE to pay the extortionate costs that hotels in the UK (my experience) have the nerve to charge. The OP said an option was to use a dial up connection and my observation would be that if that was done through a hotel bedroom phone it would cost a fortune! Not an option in my mind.

Tonight I'm 250 miles form home, sitting in my sad hotel room in Exeter, connected via a dial up connection through my 3.5 G Nokia Navigator mobile phone. I use it as a modem, have an "unlimited" internet access package (fair use) in my monthly tariff and it works. 

Would that be an option for you to take away the basic fear of a public access point to the Web?

---

### Post by warfacegod on 2010-07-07
Found it: [http://blogs.computerworld.com/15815/can_ubuntu_save_online_banking](http://blogs.computerworld.com/15815/can_ubuntu_save_online_banking)

---

### Post by bodhi.zazen on 2010-07-07
> **AlanR8 said:**
>  ... using a "live" Ubuntu environment makes a lot of sense as nothing is stored locally.

That is the least of your worries. On portable devices I suggest an encrypted installation.

As I said, a live CD is, IMO, more vulnerable as the packages will become out of dated rapidly and there are no security updates available.

ufw + ssh tunnel is, IMO,  more secure and sufficient for what you need.

---

### Post by lhb1142 on 2010-07-08
Thanks to Earl Malmrose at ZaReason Computers < [http://zareason.com/shop/home.php](http://zareason.com/shop/home.php) >, from whom I just purchased a ZaReason Teo Netbook < [http://zareason.com/shop/product.php?productid=16250&cat=250&page=1](http://zareason.com/shop/product.php?productid=16250&cat=250&page=1) >, an absolutely excellent netbook, I now know how to set up a dial-up connection on a Ubuntu computer, something I have been previously unable to do.

It's actually quite simple - once you know how. (I "reverse-engineered" what Mr. Malmrose did on the Teo and am now able to connect via dial-up on my "regular" Acer Extensa 5620-6419 on which I have Ubuntu installed [Windows is completely removed].)

On most computers, it is necessary to use an external modem; I use a USRobotics USR Model 5637, a USB-modem, which is excellent, but I'm sure that any Linux-capable external modem will do.

Here are the instructions to set up dial-up on a Ubuntu computer:

(Note: you must have Gnome PPP, available from the Synaptic Package Manager, installed.)

Access System > Administration > Users and Groups

Access Advanced Settings (enter password)

Open User Privileges Tab

Make sure EVERYTHING (especially "Connect to internet using a modem" plus "Use modems") is checked.

Plug in this external modem, open Gnome PPP, click on Setup, click on Detect (Gnome PPP will then detect this modem), close the setup box, and then enter your connection (login) information.

That's all there is to it. (Does it sound complicated? It's not really - and you only have to do it once.)

I feel very strongly about security and, as we are going on a trip during which I must perform some online banking, I wish to use a dial-up connection for that purpose rather than a hotel's definitely-not-secure network.

The only computer I owned which could do that was my Asus EeePc 1000/Linux, an otherwise unsatisfactory (much too slow and limited - plus its modified-Xandros OS is no longer being maintained by the manufacturer) netbook.

I contacted ZaReason and asked them if I could mail my USR modem to them to see if it would work with their Teo; if it did, I told them I would buy one.

It did - and I did! (It's *quite[I]*[/I] a netbook. It arrived yesterday and I HIGHLY recommend it - and ZaReason, which sells computers pre-configured with any Linux distribution you wish. It's a "small" company - but they make "big" computers!

This is the computer which I'll be taking on my trip. There is no such thing as "absolute" security, but I certainly feel much better, thanks to all the answers and information posted here.

And a very LOW bow to Earl and Cathy Malmrose at ZaReason for apparently easily accomplishing something (connecting a Ubuntu computer to dial-up) that, for the past two years, I have been unable to do (and have not previously found any cogent or useful information concerning this on any of the forums or even Google).

Check out ZaReason. Barring changes, my wife and I have agreed that any of our future computer purchases will be made from them. (Sorry for the "shameless plug," but my wife and I are really excited about this - we'll actually, for the first time, have a good, small, and fast computer, ***with Ubuntu***, to take with us on a trip!)

---

### Post by nadjo on 2011-06-10
please can anyone here help me ?
i am so scary ,
last week my internet connection got down , the i got connected for 1 week to unsecured internet connection , i signed in to hotmail messenger alot and talked to my friends , and started a video calls with them , 
my question is , 
is anyone on this unsecured network could viewed my video calls ? did they saw my video ? please try to reply me ASAP please =

---

### Post by lhb1142 on 2011-06-11
> **nadjo said:**
> please can anyone here help me ?
i am so scary ,
last week my internet connection got down , the i got connected for 1 week to unsecured internet connection , i signed in to hotmail messenger alot and talked to my friends , and started a video calls with them , 
my question is , 
is anyone on this unsecured network could viewed my video calls ? did they saw my video ? please try to reply me ASAP please =

It is possible that some or all of what you did on the unsecured network could have been observed by someone, especially if the network were set up by a hacker.

I would suggest that, once you are back on your secure network, you change your Hotmail password. As a matter of fact, you should change the passwords of any site into which you logged in while on that unsecured network.

I now avoid all unsecured wireless networks except for merely surfing the web (never signing in to any site); that includes hotel wi-fi networks.

Anything on an unsecured network (or even a secured network that has an open password, such as those hotel networks) can be intercepted by a hacker.

That is why, on occasion, I still use a dial-up internet connection, especially for online banking, etc. While dial-up does not guarantee perfect security, it is less likely to be intercepted than an open network.

---

