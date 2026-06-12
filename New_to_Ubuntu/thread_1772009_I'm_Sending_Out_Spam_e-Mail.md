---
title: "I'm Sending Out Spam e-Mail"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by Glkanter on 2011-05-31
I'm on Ubuntu 11.04, and I'm sending out spam e-mail. Plus, some spam stuff is posting to facebook.

I found nothing in the Ubuntu Software Center or with a Google search.

Help!!!

---

### Post by LowSky on 2011-05-31
Someone hacked your email account. Change your email account passwords.

This is not a Ubuntu OS issue.

---

### Post by Glkanter on 2011-05-31
I changed my password as you advised.

We'll see if that ends the problem.

Thanks.

---

### Post by Glkanter on 2011-06-02
I changed my e-mail password. The spam seemed to have stopped. But a few hours ago, some were sent out.

As I didn't give my password to anyone or anything, some type of code must have either learned my password, or is taking advantage of my logged-in-to-e-mail PC.

In either case. I continue to believe I have malware on my Ubuntu system.

---

### Post by Paqman on 2011-06-02
What do you use for your email? An online service like Gmail or Hotmail, or something provided by your ISP? Do you use a local client like Evolution or Thunderbird, or do you just use a browser to check your mail?

---

### Post by arochester on 2011-06-02
When you changed your password, did you log out and log back in with your new password?

---

### Post by gandaran on 2011-06-02
are you using wireless, someone could have hacked the wireless password and is intercepting your email and facebook passwords.

---

### Post by Glkanter on 2011-06-02
I use Yahoo for my e-mail. I configured Evolution within the last week, but the e-mail I tried to send is stuck in the out queue.

Yes, I have signed out and signed in to Yahoo maybe a dozen times since I changed my password.

I do have a wireless router. My PC is connected via a cable. The signal is 'invisible' and password protected.

Thank you.

---

### Post by Irihapeti on 2011-06-02
If you have a "secret question" that you have to answer if you've lost your password, you should change that as well.

Otherwise, they can either retrieve the password or set a new one (I can't remember which), and they can change the second email address to which the information gets sent.

---

### Post by Glkanter on 2011-06-02
I'll do that, thanks.

The very first respondent to this thread was pretty certain my Ubuntu-based PC hadn't picked up any malware. Is he correct? I searched the web and the Ubuntu Software Center for Linux or Ubuntu virus/malware detection or repair programs, and came up with nothing.

Thanks.

---

### Post by dmizer on 2011-06-02
It is extremely unlikely (like impossible) that you picked up malware.

Do you access your yahoo email from any other device, like an iPhone or an Android phone? When you log in, does the url say [noparse]"https://"?[/noparse]

Are you using a strong password? [http://www.makeuseof.com/tag/create-strong-password-forget/](http://www.makeuseof.com/tag/create-strong-password-forget/)

When you configured Evolution, did you configure it for plain pop3, or did you use SSL? [http://webnet77.com/secure-email.html](http://webnet77.com/secure-email.html)
> When a mailbox is popped using standard POP3 protocol, the username and password are sent in the clear over the internet. This means, that anyone with the ability to "listen in" on your mail client's login session with your mail server can easily retrieve your username and password as well as read your email.
This means that if you have any other email accounts or services that have sent you emails with passwords in them, they could be compromised as well.

---

### Post by mastablasta on 2011-06-02
> **Glkanter said:**
> I'll do that, thanks.
 
The very first respondent to this thread was pretty certain my Ubuntu-based PC hadn't picked up any malware. Is he correct? I searched the web and the Ubuntu Software Center for Linux or Ubuntu virus/malware detection or repair programs, and came up with nothing.
 
Thanks.
 
 
he is probably correct as anything liek that needs user password to run on linux.
 
There are a couple free antivirus programmes available for linux as well such as:
 
AVG Free,
Avast for linux
Bitdefender
ClamAV
 
and possibly some others.

---

### Post by Glkanter on 2011-06-02
Evolution was set up with POP3 & smtp.

My password was not strong, it is stronger now.

I have an Android phone. The url is *not* https.

I sure appreciate all the help, but if it's not likely an Ubuntu issue, i guess I'm in the wrong place. How is it you can be so certain I haven't picked up anything bad? By the way, I use the Firefox browser.

Thanks, again!!

---

### Post by Glkanter on 2011-06-02
Well, maybe Evolution was where I gave it away. I have deleted my Yahoo account from Evolution. I have changed by security questions on Yahoo.

I will download AVG and maybe the others, thank you! I know how to search the web, and I checked the Ubuntu Software Center, it's odd that I didn't even find AVG.

I'm not the kind of user that picks up strange stuff. But I did go to a site the other day that was pretty shady. Maybe I got something there.

Thanks for all your help!

---

### Post by dmizer on 2011-06-02
It's far far more likely that your account was compromised due to insecure practices while accessing your email.
1) You were logging in at yahoo's plain login page. This means that your password is sent in clear text for anyone to see.
2) You configured your email software to log in over pop3 port 110 which also means that your password is sent in clear text for anyone to see.
3) If you access your yahoo email from your Android phone, that's another good possibility for a compromise.
4) Your password was weak.

The combination of the above four points are more likely to have caused your email to be compromised. If you still have your Evolution configured, you should reconfigure it correctly, or remove the account. If you access your email through your Android phone, you should investigate the application you use for that access and see how secure it is. You should start using Yahoo's secure site for logging into your email via a browser: [https://login.yahoo.com/config/login_verify2?.intl=us&.src=ym](https://login.yahoo.com/config/login_verify2?.intl=us&.src=ym)

You indicated that changing your password caused the spam to stop, that means that your password was hacked. Since the spam started again, you should change your password again, and change your email habits so that they are more secure.

Edit:
It's not really a good idea to use antivirus on Linux as you will only ever get false positives that get you scared. It's really not necessary. Further, if your password WAS gotten by a virus or malware, no one knows that the malware exists so your antivirus won't pick it up anyway.

---

### Post by Irihapeti on 2011-06-02
Which ports is evolution using?

If it's 995 and 465, then that's the equivalent of https on pop3 and smtp.

If it's 110 and 25, then there's no encryption and it can be eavesdropped.

Edit: I see that dmizer has beaten me to it.

---

### Post by dmizer on 2011-06-02
> **Glkanter said:**
> Maybe I got something there.

Not unless you actively participated in it's installation (example: the site asked you to install something and you did). If you suspect something malicious in Firefox, you should clear all browsing history and cookies. That should leave you in the clear.

---

### Post by Glkanter on 2011-06-02
The Ubuntu Software Center didn't like AVG, so I canceled it.

Yahoo doesn't seem to use https. I tried typing it in, and I tried the link provided above. It ended up with a http url.

I'll look into the Yahoo/Android issue further.

You know, if I tipped my hand by configuring Evolution, that's kinda lousy.

If anything changes or happens, I'll post again.

Thanks for everything! It's much appreciated.

---

### Post by dmizer on 2011-06-02
> **Glkanter said:**
> Yahoo doesn't seem to use https. I tried typing it in, and I tried the link provided above. It ended up with a http url.

Yahoo most certainly DOES use https, and the fact that you can't get to the https site is suspicious. That being the case this is more likely to be your real problem.

Do not log into your email account unless you use the https site.

Have you cleared all your cookies and browsing history, and restarted Firefox? If you still cannot reach the https site, then what DNS servers are you using?

---

### Post by Glkanter on 2011-06-02
Yes, the Yahoo login uses https. The Yahoo Mail page does not.

I have cleared Firefox cookies, etc.

Thanks.

---

### Post by dmizer on 2011-06-02
> **Glkanter said:**
> Yes, the Yahoo login uses https. The Yahoo Mail page does not.

The login is the sensitive part. Once you're logged in, it's not necessary to use https, though it would be nice.

---

### Post by gandaran on 2011-06-02
> **Glkanter said:**
> I'll do that, thanks.

The very first respondent to this thread was pretty certain my Ubuntu-based PC hadn't picked up any malware. Is he correct? I searched the web and the Ubuntu Software Center for Linux or Ubuntu virus/malware detection or repair programs, and came up with nothing.

Thanks.
what you can use in ubuntu for security is _rkhunter_, install from the software center and forget the antivirus programs that only scan for windows virus.
rkhunter runs daily on your computer or on demand from terminal.

---

### Post by Irihapeti on 2011-06-02
I would say DON'T install rkhunter unless you have real reason to think you have a rootkit and you have read up on how to use it.

I've never yet seen a user of these forums who's been infected by a rootkit. But I've seen lots of new members install it "just to be sure" and then get scared witless by false positives.

---

### Post by Glkanter on 2011-06-04
So, it seems like configuring Evolution is a recognized way to put private info out there in an unsecured manner.

Other than configuring Evolution last week, I did nothing different regarding e-mail and security.

Last week my e-mail got compromised.

It would seem like this Evolution thing should be addressed. You know, I was just trying to be a good Ubuntu-er by messing with Evolution, certainly there was noting wrong with Yahoo mail in the browser.

What happened should not have happened. Actually, it's a bunch of BS.

Thanks to all of you for thoughtful and valuable help.

Garry

---

### Post by dmizer on 2011-06-04
> **Glkanter said:**
> So, it seems like configuring Evolution is a recognized way to put private info out there in an unsecured manner.

Other than configuring Evolution last week, I did nothing different regarding e-mail and security.

Last week my e-mail got compromised.

It would seem like this Evolution thing should be addressed. You know, I was just trying to be a good Ubuntu-er by messing with Evolution, certainly there was noting wrong with Yahoo mail in the browser.

What happened should not have happened. Actually, it's a bunch of BS.

Thanks to all of you for thoughtful and valuable help.

Garry
This could have happened on any system with any email client including Outlook Express and Thunderbird, as well as on Windows, Mac, or any Linux variety. The problem here is that you did not know or did not think to use secure ports to configure your email.

Perhaps there should be a warning of some kind, but really no email client has a warning when configuring email with unsecured ports.

---

### Post by Thewhistlingwind on 2011-06-04
> **dmizer said:**
> The login is the sensitive part. Once you're logged in, it's not necessary to use https, though it would be nice.

Wait, if I'm configured to use SSH to login to my email, I'm good even if I'm using pop3 right?

---

### Post by Glkanter on 2011-06-04
Well, I reject the responsibility for not knowing that what I did was the risky thing that I apparently fell victim to.

I've been on PCs and the internet as long as anyone. I keep my nose clean. That I chose to configure Evolution, which is part of the standard Ubuntu installation, should not unwittingly throw me into some category of risk takers.

---

### Post by Irihapeti on 2011-06-05
It's possible that you were just unlucky - in the wrong place at the wrong time. I was running unsecured email for a year or so (because my ISP didn't offer SSL at the time) and nothing bad happened to me. Or maybe I was just extremely lucky - who knows.

I think we all have the obligation to find out about security and to keep on learning. The trouble with just blaming evolution is that nothing gets learned, and a similar mistake could be made down the track. The consequences could be much worse the next time, such as finding that your PC is being used for criminal activities. (I know some people this happened to, and it wasn't fun for them.)

Learning more about security is a good idea. The stickies in the security forum are a good place to start, and I think that other members would be prepared to offer useful links if they were asked.

---

### Post by Glkanter on 2011-06-05
I am not unaware of internet security issues or of my own role in preventing/avoiding malware infections.

---

### Post by QLee on 2011-06-05
[QUOTE=Glkanter]I am not unaware of internet security issues or of my own role in preventing/avoiding malware infections.[/QUOTE]

Reading through this thread, I understand what you are referring to and you do have some idea of the issues, however, there are also aspects about which you are somewhat confused. Not the least of which is the idea that any client application (i.e. Evolution) or any operating system has the role of protecting the person configuring it from their own ignorance or mistakes. Certainly you know more now after this issue and that will help you in the future. None of the spam was actually coming from your local system and your compromised email passphrase wouldn't give anyone access to your user account on Ubuntu as long as you didn't use the same for both and you likely knew better than to do that.

The people helping you have been giving you the benefit of their greater knowledge and have been trying to give some reassurance that the symptoms you have seen are extremely unlikely to be the result of a fault in Ubuntu or Evolution and there isn't an indication in the data you have detailed that a rootkit or other malware is involved. I add my opinion to that.

---

### Post by dmizer on 2011-06-05
> **Glkanter said:**
> That I chose to configure Evolution, which is part of the standard Ubuntu installation, should not unwittingly throw me into some category of risk takers.

I want to stress again, that you would have fallen victim to this kind of attack on any computer with any email client, because none of the currently popular email clients give any kind of warnings about connecting to an email account over an unencrypted channel.

Furthermore, this may be of interest to you -> [http://www.ibtimes.com/articles/157401/20110604/microsoft-yahoo-hotmail-protocol-trencd-micro-pdf-doc-phishing.htm](http://www.ibtimes.com/articles/157401/20110604/microsoft-yahoo-hotmail-protocol-trencd-micro-pdf-doc-phishing.htm)

Meaning that you may have simply been the victim of an organised attack. The above is why I suggested that you dump cookies. To protect yourself from this attack, it's advisable to disable the "remember the password to this site" option and always manually type in your password ever time you check your email.

---

### Post by dmizer on 2011-06-05
> **Thewhistlingwind said:**
> Wait, if I'm configured to use SSH to login to my email, I'm good even if I'm using pop3 right?

I don't know how you would do this unless you have a direct connection to the email server and are tunnelling pop3 over the secure SSH channel. If that's the case, then yup ... no problem. Though, I don't know why you'd consider doing that over using the built in encrypted ports that are supported by the email client itself.

---

### Post by SeijiSensei on 2011-06-05
> **dmizer said:**
> I want to stress again, that you would have fallen victim to this kind of attack on any computer with any email client, because none of the currently popular email clients give any kind of warnings about connecting to an email account over an unencrypted channel.

That's not true of current Thunderbird releases.  When you set up an account, it automatically scans the mail server to see which protocols are available and opts for the secure ones whenever possible.  It will also warn you if it can only find insecure ports or secure servers with self-signed certificates.

I've seen postings here that Tbird will be replacing Evolution in future Ubuntu releases.  That's bad news for Exchange users, but probably good news for everyone else.

---

### Post by cpetercarter on 2011-06-05
The fact that spam e-mails appear to come from your account does not mean that they were actually sent from your Yahoo account or your e-mail client. It is the easiest thing in the world to spoof the "from" address on an e-mail.

These attacks on Yahoo mail accounts are distressingly common (google "yahoo sending spam emails from my account"). If an attacker is once able to download your address book, he can carry on sending spam emails to your contacts using your e-mail address even if you subsequently change your password and other login details. The answer may be to open another email account, perhaps with a different provider, and to tell your contacts to delete your old e-mail address from their address books.

---

### Post by SeijiSensei on 2011-06-05
Unfortunately what I've been seeing more of lately are spams being sent from the user's own account rather than simply a forgery of the From field.  I manage closed-subscription mailing lists that have received spams from registered members.  Looking at the entire set of message headers shows that the spam was sent from GMail, Yahoo, or AOL themselves.  In these cases it's pretty apparent the person's credentials were stolen and being used to spam through their actual webmail accounts.  

You can read about one person's experiences with a GMail account hijacking [here]("http://www.theatlantic.com/technology/archive/2011/04/i-guess-i-should-never-taunt-spammers/237241/").

---

### Post by Glkanter on 2011-06-05
There were actual spam e-mails in my Sent Messages folder. I conclude they got into my account.

I changed my password, and did every other recommendation that I received on this forum.

Look folks, I invoked Evolution, I contributed to the problem. But I did nothing 'unnatural', and I received no warning.

I still call it BS, regardless of whatever other systems might have acted the same way. I don't give Linux a pass for other systems' hypothetical faults that didn't happen.

I got hacked, one way or another, and that's not 'supposed' to happen with Linux. That it was (likely) Linux' Evolution makes it all the worse.

So yes, I suppose I learned something today. I will not experiment further with Evolution.

So, what IM program should I use for Yahoo, and what precautions should I take?

Thanks!

---

### Post by Glkanter on 2011-06-05
Evolution could have told me to temporarily change my password on Yahoo, before configuring. Then, once the configuration or whatever was done, change the password back to what it usually is.

I think that work-around would be doable by Evolution, would have made me aware of the risks, would have prevented my account from being hacked, and would have prevented the spam from being sent out.

Instead, I'm at fault for not knowing. That's BS.

---

