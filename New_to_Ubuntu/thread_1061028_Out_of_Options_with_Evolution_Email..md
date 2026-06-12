---
title: "Out of Options with Evolution Email."
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-02-05
I'm honestly sorry to be such a pain in the butt, but I'm exasperated with trying to get Evolution email installed, when so many of you all seem to have had success with it.
This laptop will be my diagnostics machine eventually, but I need email.  This morning I wiped my HD, reinstalled Ubuntu 
8.10, downloaded 245 updates, and set up my wireless network.  Then I clicked on the evolution icon and got the EVOLUTION SETUP ASSISTANT page, I clked Forward to the RESTORE FROM BACKUP page. I do not know how to do that, or even if I want to do that, so I clked Forward and got the IDENTY page which I filled in using info from a Tutorial, this forum, written by [mdpalow], very detailed about how to get a Yahoo! address in Evolution, NO FORWARD OPTION WAS AVAILABLE, I went back to RESTORE FROM BACKUP page and tried to work with that, nothing I did worked.  All I have is three windows available in the WELCOME TO EVOLUTION SETUP ASSISTANT, no email screen where I could go EDIT>PREFERENCES and go from there, nothing. 
Right now it doesn't matter if all of this is my fault or not.  I am weary, I have friends that have tried to talk me into Thunderbird.  I am reminded, daily, that if I had only listened.  My thoughts were Evolution is the Default and would be easier.  I really need some help.  All I want is a reliable email provider, that I can work with.  Any offers? :(

---

### Post by apjone on 2009-02-05
If all you want is email then Thunderbird would suit.

[http://www.howtogeek.com/howto/internet/firefox/get-your-yahoo-mail-in-mozilla-thunderbird-for-free/](http://www.howtogeek.com/howto/internet/firefox/get-your-yahoo-mail-in-mozilla-thunderbird-for-free/)

But Evolution has tesk/calander etc. I found the setup was fairly easy for evolution (cant remember exactly what i did) [http://linux.about.com/od/linux101/a/desktop09b.htm](http://linux.about.com/od/linux101/a/desktop09b.htm)

hope this helps

---

### Post by Therion on 2009-02-05
Are you certain that Yahoo! allows POP forwarding?  I thought only the "Premium" Yahoo! accounts (that you have to pay for) allowed for POP forwarding.  Can you confirm that, please, because if your account doesn't allow for POP forwarding, you're out of luck as far as I know.

I haven't seen the tutorial you refer to, could you post the link to it please?  It might help me, help you.

Gmail, on the other hand, is a snap through Evolution:  [http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)

---

### Post by Yed Ied on 2009-02-05
Thanks, I'm a MS guy, just really getting interested in the Linux sys.  I'm working on my A+ now but feel really stupid not being able to function in this world.  I want this laptop to be my diagnostics machine and the email is all thats left.

---

### Post by Yed Ied on 2009-02-05
He said If I wanted POP3 I would have to pay. He took me through it on POP.

---

### Post by Temposs on 2009-02-05
Thereion is right. Yahoo doesn't allow POP forwarding(EDIT: except on its premium accounts). There is a nice hackish solution out there that I have actually implemented for my wife, but it was a bit challenging to figure out how to get it working properly, even for me.

Yed, do you have a premium yahoo account?

It sounds like you're just having trouble getting through the GUI for Evolution's Setup Wizard. Hmm. Why don't you get to where you get stuck and then take a screenshot(press the Print Screen button on the keyboard, or use Applications->Accessories->Take Screenshot). Post the screenshot on here so we can see exactly what it looks like when you get stuck, and we can help you from there.

---

### Post by stchman on 2009-02-05
Apparently Yahoo allows POP email.  Here are some instructions for Outlook Express but should be easy enough to substitute Evolution.

[http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-08.html](http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-08.html)

It looks as though Yahoo only allows POP when you subscribe to Yahoo Plus email.  So looks like you are going to have to pay.

---

### Post by Temposs on 2009-02-05
> **Yed Ied said:**
> He said If I wanted POP3 I would have to pay. He took me through it on POP.

Yed,
   POP3 and POP are the same thing.

---

### Post by Temposs on 2009-02-05
> **stchman said:**
> Apparently Yahoo allows POP email.  Here are some instructions for Outlook Express but should be easy enough to substitute Evolution.

[http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-08.html](http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-08.html)

It looks as though Yahoo only allows POP when you subscribe to Yahoo Plus email.  So looks like you are going to have to pay.

Yes, but there is a way to get around the POP mail restriction even if you don't have Yahoo Plus. As I said before, it's not exactly easy as pie.

---

### Post by stchman on 2009-02-05
> **Temposs said:**
> Yes, but there is a way to get around the POP mail restriction even if you don't have Yahoo Plus. As I said before, it's not exactly easy as pie.

I consider Yahoo, Hotmail, Gmail, etc. SPAM email accounts.  I use them for general BS email.  Anything more serious I use my other email accounts.

---

### Post by Roving Sign on 2009-02-05
All of these email clients are more or less the same...

The critical details have to come from your email provider to make this work. Some providers have quirky setups...You should be able to use your providers instructions for configuring Outlook, the details and settings are the same.

example: When configuring ANY email client, my ISP, Embarq, requires that I use my entire email address (i.e. [email]meuser@embarqmail.com[/email]) in the SMTP "Username" field rather than just the username (meuser)

Gmail requires just the username...Dont know about Yahoo.

Regional ISPs have differnet setups - Some ISPs want you to use their servers...etc.

Those details probably arent going to be found in this forum...

---

### Post by Roving Sign on 2009-02-05
> **Therion said:**
> Are you certain that Yahoo! allows POP forwarding?  I thought only the "Premium" Yahoo! accounts (that you have to pay for) allowed for POP forwarding.  Can you confirm that, please, because if your account doesn't allow for POP forwarding, you're out of luck as far as I know.

I haven't seen the tutorial you refer to, could you post the link to it please?  It might help me, help you.

Gmail, on the other hand, is a snap through Evolution:  [http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)

Not certain they even want POP forwarding - I take it they just want to fetch and send from Evolution...POP forwarding is something else ,correct?

---

### Post by Yed Ied on 2009-02-05
I really liked Therion's gmail shot.  I have to go for a while, thanks for the interest, and you all are right about POP, that Tutorial was posted a long time ago.  The problem I'm having now is my ISP. I know its my internet provider, Verizon, but it doesn't recognize anything I put in there.

---

### Post by Therion on 2009-02-05
> **Roving Sign said:**
> Not certain they even want POP forwarding - I take it they just want to fetch and send from Evolution...POP forwarding is something else ,correct?
Maybe I should have called it POP3 *access*.  

POP3 or Forwarding are both "services" that require direct access to the email server. Yahoo! has decided to charge for these services.  I don't know about "hacks" for getting around this, but I can't believe it's hard to do <shrug>.  I'm sure little creative use of Google would provide some solutions.

Gmail makes all this stuff easy though which is why I suggested it might be an option.  That and I find that Evolution is a pretty snappy little email client.  It's spam filtering alone is astoundingly accurate for me right from the get go.

---

### Post by Foster Grant on 2009-02-05
> **apjone said:**
> If all you want is email then Thunderbird would suit.

[http://www.howtogeek.com/howto/internet/firefox/get-your-yahoo-mail-in-mozilla-thunderbird-for-free/](http://www.howtogeek.com/howto/internet/firefox/get-your-yahoo-mail-in-mozilla-thunderbird-for-free/)

But Evolution has tesk/calander etc. I found the setup was fairly easy for evolution (cant remember exactly what i did) [http://linux.about.com/od/linux101/a/desktop09b.htm](http://linux.about.com/od/linux101/a/desktop09b.htm)

hope this helps

Adding the Lightning plug-in to Thunderbird turns the program into a true PIM.

---

### Post by Yed Ied on 2009-02-05
Therion, I have my gmail add. It keeps giving a window that it doesn't recognize any of the ISP's I've put in there.  My package provider, TV-internet-etc is Verizon.  It doesn't recognize it. I'm almost there.

---

### Post by Therion on 2009-02-05
> **Yed Ied said:**
> Therion, I have my gmail add. It keeps giving a window that it doesn't recognize any of the ISP's I've put in there.  My package provider, TV-internet-etc is Verizon.  It doesn't recognize it. I'm almost there.
Try using:  **outgoing.verizon.net**

If your connection is *wireless* try using:  **smtp.vzwmail.net**

---

### Post by Yed Ied on 2009-02-06
I've given up on Evolution.  This will be my diagnostics machine, after I put a gig and a half more Ram in it, and I don't need any calenders or gismoos, just email. I Bookmarked "Verizon Central" to access my PC email and Bookmarked my "gmail" home page to take care of everything else. I appreciate all your help, and I'm sure the main problem is on this end, but if I were to be paid for the time I spent fooling with this, we all could go on a short vacation.    
Thanks again

---

