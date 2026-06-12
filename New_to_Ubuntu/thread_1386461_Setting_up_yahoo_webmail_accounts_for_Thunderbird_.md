---
title: "Setting up yahoo webmail accounts for Thunderbird 3 under Ubuntu 9.10"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by gnometorule on 2010-01-20
While there are some threads on the topic, I could not find one that actually answered this question. The one labelled 'closed'

[http://ubuntuforums.org/showthread.php?t=1372937&highlight=thunderbird+yahoo](http://ubuntuforums.org/showthread.php?t=1372937&highlight=thunderbird+yahoo)

actually discusses Thunderbird 2 and yahoo; and there are some significant differences. It also contains the idea to simply declare oneself to be Asian/European (as yahoo, probably for legal reasons, provides support there). However, moving, in yahoo's account information, to Taipeh/Taiwan (where my gf's parents are from), or Germany (where I am from), did not help (as the local yahoo address would also start with, say, 'de.yahoo...', and mine doesn't as I live in the U.S.). So here it goes. I just flipped to linux (outside gaming and maybe the still pretty Visual Studio C++ GUI), so by all means if anyone can correct me in how I express anything I post, please do so.  


***Background (for noobs like me)***

Each account you have on a yahoo webmail (as any other webmail) will have two associated servers: one SMTP (on your end, routing what you send to the web); one POP (POP2/POP3) or maybe IMAP server on the webmail host side. All those terms are names for particular transfer protocols that are easily googled. As such, for the TB/yahoo linking, note that this means that you will have to, for EACH of your webmails...

(1) Set up the SMTP account
(2) Set up the POP account 
(3) Link the two to let TB know which goes with which

I'll not cover IMAP and am not sure if this is possible under Ubuntu (there is a GNU/Linux youtube video on IMAP/yahoo though).


***Why is yahoo problematic?***

To allow TB to access your mail, your webmail provider needs to allow you to enable POP support. In gmail, you go to settings and are done. Currently, yahoo has three types of accounts:

(a) old style (free)
(b) new style (free = upgrade from (a) top left of your screen from within mail))
(c) plus (not free)

If you try to switch POP support on in (a) or (b), you will be told that yahoo only allows you to if you upgrade to (c). There is even a 'yahoo answer', apparently written by staff, that says so. This would mean that you need to cough up the money if you want to stick to your yahoo account. However, this is not true as we'll see below. If you anyway have account type (c), you will arguably be fine after enabling POP support. I cannot verify this as I don't, but try that and TB probably will do the rest for you. Stop reading here.


***Preparations***

(1) Go to webmail (TB extension suite of tools provided by Mozilla):

[http://webmail.mozdev.org/index.html](http://webmail.mozdev.org/index.html) 

and download, into any folder, the current version of the following two extensions:

Web-Mail
Yahoo

The short documentation there is very good; however, ***note that it too refers to TB 2, not 3***! (while the extensions clearly work for TB 3, as you can check in the version history).

(2) Install the extensions from within TB:

- go to Tools-Add-ons
- click install and find the files
- install them
- restart TB

(3) If you have account type (a), upgrade to account type (b). While you will still get the feedback that you cannot enable POP for (b) either, this does not matter: the above extensions will take care of matters. If you get an error message telling you something to the sort of

<error>bad vibes from <name>@yahoo.com

during what follows below, you have forgotten to upgrade from (a) to (b). ***It is not possible to keep using account type (a) with TB***; only (b) and (c).

(4) The default ports suggested by TB (and general port protocol) will be

- 25 for SMTP
- 110 for POP

However, there is a note in the webmail extension that 'some OS will block ports below 1000'. Ubuntu apparently does. So you need to assign new ports to the services. Check the webmail page for more info; it's easy. However, keep in mind that if you are firewalled, you need to open the ports that you rewire this through. If you are new to UFW but want to use it/have used it a bit, check out this nice intro: 

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

It'll be something like

sudo ufw insert 3 allow in 1025,1100/TCP
sudo ufw insert 4 allow out 1025,1100/TCP,

assuming that you, like me, made the 25/110 ports into > 1000 numbers by just adding zeros at the end. For simplicity, I'll assume for the rest of this post that the ports will be 1025 (SMTP) and 1100 (POP). Go back to Add-ons, and check, under the 

web-mail extension: preferences button, 

if the POP and SMTP servers are running (they should if you did all of the above - and restarted TB). If not, check first what went wrong before you continue, and start them.


[B][I]Setting up the yahoo account on TB
[/I][/B]
General remark: We'll use wizards that quite often will insert wrong information that we'll adjust later, but I don't think there is a way around using those wizards. It's easy though if you made it to here. 

(1) Go to

- File->New->Other Account (*NOT mail account)*, 
- check *webmail* on the next page
- click next

(2) On Identity (the next page)...

- Choose your name
- Enter your webmail (*full* address, as in <name>@yahoo.com)
- Click next

(3) On User Name (the next page)...

- Enter your webmail (*full* address, as in <name>@yahoo.com)
 - Click next
 
(4) On Congratulations! (the next page)...

- unclick *Download messages now* (as it would not yet work)
- click finish

(5) Under 'All Folders' on the left in TB, you will now notice a new User Account with name

<name>@yahoo.com

If not, refresh or click around, then come back. It'll be there.


[I]**Adjusting the account information**
[/I]
(1) Bring up the account sheet

Serveral options; easiest...

- select (left click) the new account name on the left, then
- right click the account, and 
- choose setting

The Account Settings overview will pop up, with your new account selected. Keep it selected for now.

(2) Account Name:

- remove the " on localhost" at the end

(3) Fill out...

- Your name
- Email Address (might not be needed, but can't hurt)

(4) On the left, click *Server Settings* relating to your new account. It will pop up on the right.

(5) Change 'Port' from 110 to 1100. The rest should be fine; however, check if it is (for me it automatically does here), aka, if it conforms to

[http://webmail.mozdev.org/serversettings.html](http://webmail.mozdev.org/serversettings.html)

(server: localhost; user: <name>@yahoo.com). This is the POP page, just to be clear; so check POP settings per the link.

(6) At the very bottom on the left you will see (not belonging to any account per se)

[I]Outgoing Server (SMTP)
[/I]
Left click it. For each account, the wizard may or not add a new SMTP server here (see above). However, the parameters, if such an entry is created, usually do not conform to  

 [http://webmail.mozdev.org/serversettings.html](http://webmail.mozdev.org/serversettings.html)

(SMTP part), and we'll change them now or create a new account.

(7a) If entry was created...

- change to the values of the link (server: localhost; user: <name>@yahoo.com)
- make the port 1025

(7b) If not,

- click add
- choose a name (doesn't matter)
- add values from the link (server: localhost; user: <name>@yahoo.com)
- make the port 1025

We have now successfully set up the SMTP and POP server, and all that remains is to link those two.

- go back to the Account Settings page if you are no longer there
- left click your new account (top line before the different sections of it)
- on the bottom right, you'll see *Outgoing Server (SMTP)*. Click it
- you see a list of all SMTP servers you set up in the past. Click the name of the one we set up in steps (6) and (7) above. 
- click ok

We are done. :)  Enjoy.

---

### Post by papibe on 2010-06-15
Yahoo!... I mean, Thanks :-D

So many little things to consider, and the help pages on webmail.mozdev.org are so...well, not the best in the world.

Thanks again for this well explained tutorial. BTW this works like a charm on Lucid too.

Regards.

---

### Post by Sharang.d on 2010-06-18
> **gnometorule said:**
> 
(5) Change 'Port' from 110 to 1100. The rest should be fine; however, [B]check if it is (for me it automatically does here), aka, if it conforms to

[http://webmail.mozdev.org/serversettings.html](http://webmail.mozdev.org/serversettings.html)[/B]  

(server: localhost; user: <name>@yahoo.com). This is the POP page, just to be clear; so check POP settings per the link.

I lost you here. What do i do with that link?

---

### Post by philinux on 2010-06-18
Yahoo now allow pop on the free accounts. I've just set it up in evolution last week. It's in their webmail settings to turn on pop support.

pop.mail.yahoo.co.uk
smtp.mail.yahoo.co.uk
ssl needed for both. No need to specify ports.

Very easy setup.

---

### Post by Sharang.d on 2010-06-18
> **philinux said:**
> Yahoo now allow pop on the free accounts. I've just set it up in evolution last week. It's in their webmail settings to turn on pop support.

pop.mail.yahoo.co.uk
smtp.mail.yahoo.co.uk
ssl needed for both. No need to specify ports.

Very easy setup.

Apparently it's not allowing me.
Check Screenie..

---

### Post by philinux on 2010-06-18
I'm not a plus user just regular as in free.

---

### Post by lisati on 2010-06-18
I think it can depend on *which* free accounts you're using. The last time I checked yahoo.com email addresses wouldn't work, but I've been using pop and smtp access with yahoo.co.nz for a few years now. 

The ISP I'm with started using Yahoo as their email host a couple of years back, making it largely academic at my end....

---

### Post by Sharang.d on 2010-06-18
Damn it! No wonder I'm not able to get it! Mine is .com!
Can you please just explain the text i quoted? 

> **gnometorule][I](5) Change 'Port' from 110 to 1100.  The rest should be fine said:**
> check if it is (for me it  automatically does here), aka, if it conforms to

[http://webmail.mozdev.org/serversettings.html](http://webmail.mozdev.org/serversettings.html)[/B]   

(server: localhost; user: <name>@yahoo.com). This is the POP page,  just to be clear; so check POP settings per the link.
[/I]

---

### Post by papibe on 2010-06-18
philinux, you got me exited! but... no luck for me:

```

POP & Forwarding
	
Upgrade to Mail Plus so you can:

    * download your Yahoo! Mail in an email client, such as Outlook
    * forward your Yahoo! Mail to a different address

```

---

### Post by Sharang.d on 2010-06-19
> **papibe said:**
> philinux, you got me exited! but... no luck for me:

```

POP & Forwarding
    
Upgrade to Mail Plus so you can:

    * download your Yahoo! Mail in an email client, such as Outlook
    * forward your Yahoo! Mail to a different address

```

Same here :(

---

