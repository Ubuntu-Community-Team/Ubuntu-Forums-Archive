---
title: "Evolution Mail has stopped working"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by hector24 on 2009-08-03
I'm not sure if it's something I've done - though I've only downloaded updates - but I can't get Evolution Mail to send anything.  Messages just stay in my outbox.  I can get only my other email accounts on the same computer and send from them.  Anything I can do?  Thanks

---

### Post by jacktar on 2009-08-03
Have you ticked 'Server requires authentication' in the sending preferences?

---

### Post by hector24 on 2009-08-03
Thanks.  I've looked hard but I can't find 'sending preferences' so I can't answer your question.  Help on this would be very much appreciated.

---

### Post by mprince on 2009-08-03
*Edit>Preferences*

Highlight your email account, then click the edit button, then look for the 'Sending Email' tab

---

### Post by hector24 on 2009-08-03
Sorry, this must sound dumb, but how do I highlight my email account?  Is this in Applications?

---

### Post by hector24 on 2009-08-03
I'm also now having further problems with Evolution.  It asked me for my password for my server, although the 'remember password' is ticked.  It wouldn't let me enter my password and just completely froze.  I logged off and went back in and saw the following message on my desktop (it quickly disappeared):

"network Service discovery disabled. You current network has a .local domain. which is not recommended and incompatible with the Avahi network service discovery.  The service has been disabled."

I understand not a single word of this.  Please help.

---

### Post by mprince on 2009-08-03
> **hector24 said:**
> Sorry, this must sound dumb, but how do I highlight my email account?  Is this in Applications?

No, it would be in the Evolution menu *Edit>Preferences* 

then follow the steps in the jpeg I've attached to this post. This is the window that will appear.

[ATTACH]123495[/ATTACH]


This could be a temporary email problem. Occasionally, when an email server is having problems it keeps asking you for you password again and again and won't accept anything you enter.

On the other hand that message about avahi does make me think something more is going on here.

Do your other email accounts work?

---

### Post by hector24 on 2009-08-03
Thanks for that.  Yes, 'authentication required' is checked.  

Thanks for your help.  I will tune in tomorrow.  :D

---

### Post by cdillard-hsp on 2009-08-03
I've run into the same problem.  Evolution has always sent fine but starting a week ago, it periodically won't send mail.  We use Zimbra here and we do use auth on SMTP.  If I restart Evo it will send the mail out but after being open for a few hours (random really) it will just start piling mail up in the Outbox.

I started evo from the console and waited for maybe 10 minutes after clicking Send/Receive hoping to get the error, if any, on sending mail.

---

### Post by hector24 on 2009-08-06
Hi

Is anyone able to help me because my problem isn't resolved?  I really don't want to have to keep going to Mail2web to get my emails.  Is Ubuntu always this problematic?  I'm a complete beginner and haven't used the computer much since having Ubuntu installed yet I've had a number of problems.  I'm thinking of giving up on the whole thing.  I need convincing this is all worth it!:confused:

---

### Post by cdillard-hsp on 2009-08-06
Hector,
I can tell you with almost a certainty that "it was worth it" to go with Linux, and especially Ubuntu.  Now, regarding your problems with Evolution...
1. Please make sure that all of the settings for your email account are correct according to the guidelines set forth by your ISP or email hosting company.  You might put a call in with their support staff and have them verify your settings before you continue on with step 3 below.

2. You should consider changing the configuration on your home router if it is giving out DHCP addresses so that it assigns a domain name like **mynet.com** instead of *something.local*.  That'll make the avhi daemon happy and it'll stop bugging you.

3. You might try installing and configuring Mozilla Thunderbird (a terrific mail client) for use with your ISP or email hosting company and see if you have the same problems with sending mail.  To install thunderbird, do the following:
(1) Click on Applications on the top panel bar, then click Accessories and finally click on Terminal
(2) Type this command in the terminal and enter your password when prompted: **sudo apt-get install thunderbird**
(3) Answer yes if prompted in the Terminal and let Ubuntu download and install Thunderbird for you.
(4) Click Applications / Internet / Thunderbird to launch Thunderbird and go ahead and setup your email account according to the instructions from your ISP or whoever you have your email through.
(5) Make sure you edit your Account Settings in Thunderbird and have it leave a copy of the emails on the server or else (if you use POP) all of your mail will be removed from the server once they are POP'd down with Thunderbird.

Try sending and receiving some emails.  See if you have the same sort of issues.  You might actually prefer Thunderbird and ditch Evolution.  That's what I did.  With the Lightning Calendar extension it makes for a nice substitute to Evolution and/or Outlook.

Let us know how this goes!

Cheers,
Clay

---

### Post by Wim Sturkenboom on 2009-08-06
I like to resume first. You have multiple email accounts (for one Ubuntu user). One account does not send or receive and the others do send and receive.

I also at occasion experience that Evolution does not want to send. I always see that as a problem of my ISP (but I might be wrong) and it resolves itself after a while.

---

### Post by kapi on 2009-08-06
I have had major problems with evolution a few weeks ago and finally switched to thunderbird and IMAP settings on gmail. That seems to have done the trick. give IMAP ago it's better than pop

Kapi

---

### Post by hector24 on 2009-08-06
I cannot receive emails either.  I'm no longer getting any error messages.  Nothing has been sent from my Sent box, the messages I've tried to send have just accumulated there, and I've not received any mail (which I should have because I've found new mail when I've checked my account on Mail2web).  Any help would be very much appreciated.

---

### Post by hector24 on 2009-08-06
Sorry, I missed the above messages.  I will try this.  Thanks.

---

### Post by LewRockwell on 2009-08-06
the first thing I do with any operating system is to install Firefox and Thunderbird...

nothing more need be said...

.

---

### Post by cwmoser on 2009-08-08
Evolution failed with me too -- got errors storing to folders, locked up, could not quit Evolution - had to force quit, etc.

Switched to Thunderbird - works better now.

Don't know what happened to Evolution.  I had been using it for 3 years without a glitch but suddenly it started acting up.

I'm running 64-bit Ubuntu Jaunty and Open Office 3.1.0 -- that might be a reason.

Carl

---

### Post by hector24 on 2009-08-10
To everyone who's tried to help - many thanks.  I've switched to Thunderbird and it seems to be working fine.  :P

---

### Post by mattotoole on 2009-08-23
I've been having the same problem -- Evolution was working fine until a few days ago, then stopped sending mail.

I've had this problem twice before but never resolved it.  I used webmail and Thunderbird until I had reason to upgrade/reinstall Ubuntu, and had a fresh installation of Evolution.

---

### Post by cwmoser on 2009-08-27
I too gave up on Evolution and switched to Thunderbird.

I really liked Evolution and had been using it for years but something just went wrong with it.

Carl

---

### Post by cdillard-hsp on 2009-09-14
Having the same issue so today I launched Evo from a Terminal hoping to catch the cause of the problem but since launching from Terminal it has been working fine non-stop.  Launching from the menu leads to messages accumulating in the Outbox (seems like after I've send a handful) and I have to close/open Evo and hit Send/Receive to get them to take off into the ether...

I'm running 32-bit Jaunty with latest updates from Ubuntu repos.

---

### Post by LewRockwell on 2009-09-14
Thunderbird

.

---

### Post by cdillard-hsp on 2009-09-16
I am updating this post because I've filed a bug on LaunchPad and the guys there state that this is not an Evolution problem but a problem with my setup or our email server.  I disagree and ask that anyone using Ubuntu and Evolution that has this problem, please add your comments to the bug ticket in hopes that it will be reverted back to a bug and start getting some attention.

**Link to Bug Report:** [http://ubuntuforums.org/showthread.php?t=1190064&highlight=evolution+outbox](http://ubuntuforums.org/showthread.php?t=1190064&highlight=evolution+outbox)

**Description of the Problem/Symptoms:**
Since about a month ago, Evolution has suddenly stopped sending outbound mail after several items have been successfully sent. After some period of time where sending mail works fine, something in Evolution causes mail to start piling up in the Outbox. If I close Evolution and re-open it and then hit Send/Receive the mail gets sent. There are other users that have this exact same issue as evidenced by posts on ubuntuforums.org.

What I've observed is that if I start Evolution from within a Terminal, it does not exhibit this behavior.

I'm running Ubuntu 9.04 32-bit with all of the latest updates and Evolution 2.26.1 from the default Ubuntu repos.

---

