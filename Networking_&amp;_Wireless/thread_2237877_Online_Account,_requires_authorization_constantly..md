---
title: "Online Account, requires authorization constantly."
date: 2014-08-04
forum: Networking &amp; Wireless
---

### Post by digblade on 2014-08-04
Hello,
I use an online account for my Ubuntu 14.04 from google.com. So far I had no problems but now I see that Ubuntu is telling me it requires authorization to be used by Ubuntu.
I re-enter the password and it says everything is fine, but if I try to access my Calender or Contacts with Evolution the program says 
"Unable to connect to 'Calendar': Cannot open calendar: GDBus.Error:com.google.code.AccountsSSO.SingleSignOn.Error.UserInteraction: userActionFinished error: 10"
And my Online Account requires authorisations again and again.
I use the same account for reading my mails with Thunderbird with no problems, but that does not use my "Online Account" from Ubuntu.
Meanwhile Empathy uses this Online Account without a problem, even when it is not Authorised?
I saw a solution that made you set your IPv4 setting so that it will stop the Internet access and that does make your account appear as Authorized but it stops your Internet connection so that is no good.
This started a couple of days ago but till now I didn't notice that it only affects my Calendar and Contacts that are being accessed from the "Online Account"
I am thankful for all your help and support.

I just tested it on another Distro (Archlinux) with Latest Gnome 3 Version. The situation is the same.
Account is accepted, connection to other Programs like Empathy or Documents ( Google Drive ) is working but calendar and accounts on Evolution is not. E-Mails on evolution are working.
This is of course only with the use of this account as an "Online Account". 
I could assume the Problems lies in Evolution not working with the Online Account System right now? But that is a part of Ubuntu.
Can you tell me how to fix my accounts and Calendar to be synced with my Online Account ?

---

### Post by Mick21367 on 2014-08-08
Hi Digblade,
I have had exactly the same problem with online accounts recently (Ubuntu 14.04). It appears to be a problem with the Online Accounts mechanism, as you say. I've managed to work around the problem as follows:-
1. Disable all online access to Evolution Data Server in Online Accounts - these should stay disabled (at least until someone clever fixes 'em :-) )
2. Open Evolution. The Google accounts should now be gone.
3. Create new account in Evolution for Google (I only created a calendar, not e-mail, as I only use it to integrate my Google Calendar with Ubuntu's system calendar).
4. Once created, you should be prompted to enter your Google password. Once done, your calendar and mail (if required) should appear in evolution. If everything has gone OK, your system calendar should now show your appointments (if it is set for this - mine is!) and notifications should start to appear (mine's started from 2005, disconcertingly).
5. Close Evolution.
6. Optional step - if you do not use Evolution as your e-mail client, you can remove it through Synaptic. The Evolution Data Server will remain on your system, and the calendar events *should* still appear on your system calendar. It's no big problem to leave it on though.

That (hopefully) should be it ... until someone fixes Online Accounts - or better still - fixes the system calendar so it doesn't have to go through Evolution (please!)

Cheers

Mick

---

### Post by peter-fristedt on 2014-08-09
Thanks Mick!

Once I realised  Google was blocking my login attempts (step 4) because it regards Evolution as unsafe ([https://support.google.com/accounts/answer/6010255?hl=en](https://support.google.com/accounts/answer/6010255?hl=en)) it worked like a charm.

Perhaps  Google was blocking the net account in the first place? Ah well,  this is working and I leave it at that.

Thanks again.

/Peter

---

### Post by Mick21367 on 2014-08-10
No problem, Peter - though I didn't realise that Google was blocking unsafe clients! My settings are to allow 'unsafe' connections, so I must have encountered the problem at some point :-)

Mick

---

