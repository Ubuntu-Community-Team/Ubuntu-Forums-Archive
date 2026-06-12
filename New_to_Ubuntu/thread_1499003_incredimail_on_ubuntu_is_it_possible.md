---
title: "incredimail on ubuntu is it possible"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by saakeman on 2010-06-01
ok incredimail on ubuntu is it possible 

(I dont want a wine version )

---

### Post by Sukarn on 2010-06-01
There are alternatives if you're willing to move away from incredimail -
Thunderbird
Evolution
Kmail

---

### Post by SRST Technologies on 2010-06-01
> **saakeman said:**
> ok incredimail on ubuntu is it possible 

(I dont want a wine version )

Have you looked in the repositories yet?

---

### Post by saakeman on 2010-06-01
> **SRST Technologies said:**
> Have you looked in the repositories yet?

no , what must i look for

---

### Post by SRST Technologies on 2010-06-01
I'd say that if you got on here asking if it could be installed, you know what to look for.

---

### Post by saakeman on 2010-06-01
> **Sukarn said:**
> There are alternatives if you're willing to move away from incredimail -
Thunderbird
Evolution
Kmail

i always liked my incredimail 

I have tried thunderbird
                                and it didn't worked

---

### Post by saakeman on 2010-06-01
> **SRST Technologies said:**
> I'd say that if you got on here asking if it could be installed, you know what to look for.

I did not asked could it be installed a asked is it possible


---------------------**
join facebook's dustbin of history

dustbin of history**

---

### Post by SRST Technologies on 2010-06-01
How could it be possible but not installable?

---

### Post by saakeman on 2010-06-01
> **SRST Technologies said:**
> How could it be possible but not installable?


thats what i asked is it possible ?

---

### Post by NUboon2Age on 2010-06-01
> **saakeman said:**
> thats what i asked is it possible ?

(At the risk of getting too basic) I'm unfamiliar w/ incredimall, so here's the steps I took to investigate whether it was possible to run incredimail on Linux.  To 'check the repositories' I started System->Administration->Synaptic Package Manager and searched for incredimail and didn't find it.  So I can guess there is not a Linux native version of it (which is what prompted your mention of Wine I guess).  So then I confirmed its an M$ Windows native program by Googling for it.

So that narrows it down.  Basically from that I know of two ways to possibly run it.  

1) Maybe it will run under Wine (yes I know you said you didn't want to do this, but for the sake of completeness I'm describing how to investigate it).  I went to the WineHQ's Application Database, [http://appdb.winehq.org/](http://appdb.winehq.org/) where people describe their results of attempting to run programs.  Browsing the database I find [this entry for incredimail]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1156").  It says it requires DirectX support and is graphics heavy (not encouraging).  And the two reported test results are failures.  Its possible that newer versions of Wine might work, but its uncertain at best.

2) Possibly it could run on Windows running on VirtualBox (or another virtualization program) sitting on top Linux.  This would involve installing VirtualBox (or whatever other virtualisation program) via Synaptic, then using Windows disks to install Windows on top of that.  I've installed VirtualBox (not hard w/ Synaptic), played w/ configuration (considerably more challenging) but haven't climbed the mountain top of installing virtualized Windows on top of it (which I get the impression could be quite challenging indeed).  Wow, that's an awful lot of trouble to go through for one mail program.  If its a program that you just have to have though, maybe its worth it.

3) Are there other possiblities I'm not aware of or forgetting?

Otherwise maybe Evolution or KMail or some other Linux native program will do the trick for you???   Incredimail does look really fun.  Yahoo and others allow emoticons and some of the features, but maybe not the whole backgrounds, signatures, animations and other neat stuff.  Well, I hope you can find something satisfying.

---

### Post by mike555 on 2010-06-01
many people consider incredimail spyware and perhaps a virus ..... you might want to reconsider ......

---

### Post by jrothwell97 on 2010-06-01
No, it is not possible without WINE.

You might want to contact IncrediMail and ask them for a Linux version if you're *that desperate* to use it.

---

### Post by NUboon2Age on 2010-06-04
Today for a test I tried to install incredimail on the latest version of Wine.  Unfortunately it was not able to install.  I guess that Windows VirtualBox on Ubuntu would be my next inquiry if I wanted to run incredimail on Ubuntu.

---

### Post by Paqman on 2010-06-04
> **NUboon2Age said:**
> I guess that Windows VirtualBox on Ubuntu would be my next inquiry if I wanted to run incredimail on Ubuntu.

It would be waaaaaaay simpler to just use one of the many excellent Linux email apps. If you let us know what went wrong with Thunderbird we can help you fix it, guaranteed.

---

### Post by izark47 on 2010-06-04
saakeman, The closest program that Linux has is Evolution.  It is basically a Outlook clone. 

I work for an ISP and deal with email programs all the time. Incredimail is what I call a skin over Outlook express/Windows mail.  It is extremely popular with our less experienced more life experienced customers in Florida.  IT is created by a company out of Israel.  The reason it is so popular is the "cute" themes, stationary, and effects.  That being said, I feel the best solution is Evolution as it seems more Outlook like.  It does not however have all he "cutesy"  stuff.

---

### Post by saakeman on 2010-06-05
> **izark47 said:**
> saakeman, The closest program that Linux has is Evolution.  It is basically a Outlook clone. 

I work for an ISP and deal with email programs all the time. Incredimail is what I call a skin over Outlook express/Windows mail.  It is extremely popular with our less experienced more life experienced customers in Florida.  IT is created by a company out of Israel.  The reason it is so popular is the "cute" themes, stationary, and effects.  That being said, I feel the best solution is Evolution as it seems more Outlook like.  It does not however have all he "cutesy"  stuff.

is there a program similar to incredimail ? 
with like notifiers/sound

---

### Post by XubuRoxMySox on 2010-06-05
I do alot of those "cutesy" e-mails to penpals and stuff using Thunderbird. It allows for all the formatting (you can even choose a different background color) plus you can insert pictures - including animated gifs. I put animated sparkles and all kindsa fun stuff like that in my messages (well, the ones to penpals and especially other dancers). It sounds like it's pro'lly the closest thing to Incredimail there is for Linux. You just need to have a nice collection of animated gifs and cutesy pictures and stuff to insert in your mail. I never actually used Incredimail (even my penpals have abandoned it because of malware fears), but Thunderbird's way-cool composer sounds like what you want. SeaMonkey is the same way (it's like the older version of Thunderbird, better for POP3).

Playfully,
Robin

---

### Post by diablo75 on 2010-06-06
I gave Thunderbird a try recently and was blown away by how fast it auto-configured my server settings for me (I didn't have to go look them up on my hosting providers website; it auto-detected everything).  So Thunderbird has my endorsement.

I would actually be inclined to pity you a little if you felt more compelled to use VirtualBox just to continue using an email application rather than investigate some alternative replacements.  Because to use VirtualBox, you have to install it (easy to do really), then install Windows inside of it (not quite as easy; also, do you have a copy of Windows handy that hasn't been activated too many times?), then you have to install Incredimail, and THEN you have to boot VBox every time you want to access it.  That's a lot of hassle for simple emails, in my opinion.

---

### Post by roberthr on 2010-06-08
I would strongly advise you NOT to use Incredimail. You will not be able to recover or export mail and settings to any other mail client without buying a special program. Also, Incredimail does not conform to standards when it comes to mail protocols, it just uses it's own implementations that could make you loose all your emails if not set up properly.

Somebody mentioned Incredimail is spyware or virus. The way it acts and invade system, I would totally agree :-)

---

