---
title: "Yahoo Email and Evolution"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by sean neilan on 2011-03-06
I am having a real hard time getting my yahoo e-mail to work with evolution can anybody help me get it work please

---

### Post by seawolf167 on 2011-03-06
See [here]("https://help.ubuntu.com/community/UsingYahooWithEvolution"). It looks like you only get POP access and forwarding with a paid account.

---

### Post by dwasifar on 2011-03-06
> **seawolf167 said:**
> It looks like you only get POP access and forwarding with a paid account.

That is not correct.  I use Evolution with Yahoo mail successfully.

In Evolution preferences for the Yahoo mail account, set the following:

Receiving Email Tab:

 - Server Type: IMAP
 - Server: imap.mail.yahoo.com
 - Username: [your_username]@yahoo.com
 - Use Secure Connection: SSL Encryption
 - Authentication Type: Password

Sending Email Tab:

 - Server Type: SMTP
 - Server: smtp.mobile.mail.yahoo.com
 - Use Secure Connection: No encryption
 - Authentication Type: PLAIN
 - Username: [your_username]@yahoo.com
 - Remember password: checked

That should get you going.

---

### Post by Procreate on 2011-03-07
> **dwasifar said:**
> That is not correct.  I use Evolution with Yahoo mail successfully.

In Evolution preferences for the Yahoo mail account, set the following:

Receiving Email Tab:

 - Server Type: IMAP
 - Server: imap.mail.yahoo.com
 - Username: [your_username]@yahoo.com
 - Use Secure Connection: SSL Encryption
 - Authentication Type: Password

Sending Email Tab:

 - Server Type: SMTP
 - Server: smtp.mobile.mail.yahoo.com
 - Use Secure Connection: No encryption
 - Authentication Type: PLAIN
 - Username: [your_username]@yahoo.com
 - Remember password: checked

That should get you going.

I set up Evolution accordingly and I still get a "failed to fetch mail" error or something along those lines. Any advice? I've heard that Yahoo Mail doesn't work with the free accounts, only if you're paying can you use an email client.

---

### Post by GWBouge on 2011-03-07
> **Procreate said:**
> I've heard that Yahoo Mail doesn't work with the free accounts, only if you're paying can you use an email client.

I've actually heard that as well.  Everywhere.  This is the first time (I think) I've seen someone saying it can be done.  I entered everything as he has it, and works for me!

Note:  I entered the information when creating a new account, and still had to goto Edit -> Preferences -> Mail Accounts -> Edit to re-enter some information, such as the Receiving Email reverted back to POP instead of IMAP.  After I re-did that, it asked for my password and bang, I'm in.

Thanks, dwasifar!

---

### Post by Procreate on 2011-03-07
> **GWBouge said:**
> I've actually heard that as well.  Everywhere.  This is the first time (I think) I've seen someone saying it can be done.  I entered everything as he has it, and works for me!

Note:  I entered the information when creating a new account, and still had to goto Edit -> Preferences -> Mail Accounts -> Edit to re-enter some information, such as the Receiving Email reverted back to POP instead of IMAP.  After I re-did that, it asked for my password and bang, I'm in.

Thanks, dwasifar!

I fixed the setting, and it prompts me for my password...I type it in key-for-key but it says that it's incorrect. Any ideas? I'm 100% sure that I'm typing it in correctly...

---

### Post by rvchari on 2011-03-07
> **Procreate said:**
> I set up Evolution accordingly and I still get a "failed to fetch mail" error or something along those lines. Any advice? I've heard that Yahoo Mail doesn't work with the free accounts, only if you're paying can you use an email client.

i have 2 webmail accounts in yahoo, one works fine with evolution and the other doesnt. go to your yahoo mail and see if pop is active. i forgot how i did that long back. i created a fresh yahoo account and i could access from evolution with ease.

my server settings were different.

i have a free account too... so dont worry, it works for me with the above settings... it should work for you too..

as i am located in india, my settings go like this.

smtp: in.smtp.mail.yahoo.com
pop: in.pop.mail.yahoo.com.

the 1st prefix stands for country, key in yours and check out. may be you should find your solution.

i found mine (though it was only for the recent account i created !)

---

### Post by lisati on 2011-03-07
I don't have a paid yahoo account but can access my accounts via pop, possibly because my ISP switched from using MSN to Yahoo for its email a few years back. If I remember correctly, the situation before they did was that I could if it was a localized Yahoo account (in my case, yahoo.co.nz) but not if it was a "US" account (yahoo.com)

---

### Post by dwasifar on 2011-03-07
It looks like you guys found that useful.  I'm glad.  I discovered these settings when googling how to set up my Android phone to access Yahoo Mail, and they work just as well for regular mail clients.

The only warning (and I should have mentioned it before, seeing as this is the  Beginner Talk forum) is that the outbound SMTP connects without encryption.  I presume this is because it uses a server Yahoo intends for mobile devices (and hence the connection is already encrypted).  So someone with a packet sniffer who was determined to look at your outbound connection could probably do it.  But in practice I think it's probably fine.  I've never had a problem with it, anyhow.

---

### Post by Procreate on 2011-03-07
> **dwasifar said:**
> It looks like you guys found that useful.  I'm glad.  I discovered these settings when googling how to set up my Android phone to access Yahoo Mail, and they work just as well for regular mail clients.

The only warning (and I should have mentioned it before, seeing as this is the  Beginner Talk forum) is that the outbound SMTP connects without encryption.  I presume this is because it uses a server Yahoo intends for mobile devices (and hence the connection is already encrypted).  So someone with a packet sniffer who was determined to look at your outbound connection could probably do it.  But in practice I think it's probably fine.  I've never had a problem with it, anyhow.

Are you using a US-based mail account? I've been messing with it for hours yesterday and couldn't get it to work. After doing some reading, I've read that mail accounts outside of the United States work, but US accounts themselves require the upgraded mail for email client compatibility.

---

### Post by GWBouge on 2011-03-07
I have a US based account, and it works.

I actually created a gmail account a while back to use as my main email account just because (until now) I had never gotten it to work with an email client, and gmail seems to have better support for clients if you don't mind Google.  It was also starting to get passed around to a bunch of spam throwers, apparently (after about 8 years of virtually no spam ... *sigh*), so now it's pretty much my 'whatever' registration e-mail for crap I really don't care about.

But, at any rate, now I don't have to log in through the website to empty the Junk box  =oD

---

### Post by sean neilan on 2011-03-07
somebody gave me info onsetting up my yahoo mail(regular)on evolution as far as the receiving mail server type:IMAP,server imap.mail.yahoo.com,ssl encryption AUTH password
sending mail smtp server smtp.mobile.mail.yahoo.com server connection no encrytion AUTH plain remember password
now I get error while sending message host look up failed name or server not known
My yahoo is US based I'm in ca and I have had this e-mail for 3 years it is the only mail account that I have and I really don't want to get another one my college has this inf my funding and I dont want to remember a whole bunch of different accounts now can i get my basic yahoo mail to work with evolution or what I am really new at this computer stuff as you can tell by my typing skills so can ANYBODY PLEASE HELP!!:confused:

---

### Post by josephmills on 2011-03-07
> **sean neilan said:**
> somebody gave me info onsetting up my yahoo mail(regular)on evolution as far as the receiving mail server type:IMAP,server imap.mail.yahoo.com,ssl encryption AUTH password
sending mail smtp server smtp.mobile.mail.yahoo.com server connection no encrytion AUTH plain remember password
now I get error while sending message host look up failed name or server not known
My yahoo is US based I'm in ca and I have had this e-mail for 3 years it is the only mail account that I have and I really don't want to get another one my college has this inf my funding and I dont want to remember a whole bunch of different accounts now can i get my basic yahoo mail to work with evolution or what I am really new at this computer stuff as you can tell by my typing skills so can ANYBODY PLEASE HELP!!:confused:

is it not a pop/smtp? I thing that yahoo makes you pay for a "premium" account. you can set up gmail and have yahoo import everything to g-mail hope this helps.
also here is a link with the same troubles 
[http://ubuntuforums.org/showthread.php?t=305886](http://ubuntuforums.org/showthread.php?t=305886) 
once again hope this helps

---

### Post by marl30 on 2011-03-07
Make sure you have these settings if you are using a free Yahoo account in Evolution:

```
Receiving Email Tab:
Server Type: IMAP+
Server: imap.mail.yahoo.com
Username: Yahoo! ID WITHOUT "@yahoo.com"
Security: SSL encryption
Authentication Type: Password
check mark: Remember Password

Receiving Options Tab:
checkmark: Check for new messages in all folders

Sending Email Tab:
Server Type: SMTP
Server: smtp.mail.yahoo.com
checkmark: Server requires authentication
Security: SSL encryption
Type: PLAIN
Username: Yahoo! username WITHOUT "@yahoo.com"
checkmark: Remember password
```

---

### Post by sean neilan on 2011-03-07
I can not get evolution to send my e-mails,I already tried to configure yahoo but I get an error message while sending my e-mail

---

### Post by marl30 on 2011-03-07
Did you check the last thread you started? I post the working configuration that I'm using in Evolution for my free Yahoo account. 

And please do don't start multiple threads when you have active threads on the same subject.

---

### Post by teward on 2011-03-07
Unfortunately, I know the answer about this.

Yahoo won't let you use their email with external clients unless you subscribe to their Mail Plus program which has a monthly fee that goes along with it.  This applies to Windows, Mac, and Linux email clients.


Its something that Yahoo recently started, and its been angering their email users lately.

---

### Post by teward on 2011-03-07
[http://ubuntuforums.org/showthread.php?p=10535455#post10535455](http://ubuntuforums.org/showthread.php?p=10535455#post10535455)

Please read my post there, it has details about why you CAN'T make any external email client work with Yahoo.

---

### Post by teward on 2011-03-07
Here's the answer from the past 2 threads you posted:

[http://ubuntuforums.org/showthread.php?p=10535455#post10535455](http://ubuntuforums.org/showthread.php?p=10535455#post10535455)


That has details about why Yahoo free emails wont work with external email clients.

---

### Post by overdrank on 2011-03-07
Hi and welcome, please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by marl30 on 2011-03-07
> **EvilPhoenix said:**
> Unfortunately, I know the answer about this.

Yahoo won't let you use their email with external clients unless you subscribe to their Mail Plus program which has a monthly fee that goes along with it.  This applies to Windows, Mac, and Linux email clients.


Its something that Yahoo recently started, and its been angering their email users lately.

But I'm still able to send and receive email with this configuration I got from an Evolution yahoo tutorial from the "how to" section of this forum:

> **marl30 said:**
> Make sure you have these settings if you are using a free Yahoo account in Evolution:

```
Receiving Email Tab:
Server Type: IMAP+
Server: imap.mail.yahoo.com
Username: Yahoo! ID WITHOUT "@yahoo.com"
Security: SSL encryption
Authentication Type: Password
check mark: Remember Password

Receiving Options Tab:
checkmark: Check for new messages in all folders

Sending Email Tab:
Server Type: SMTP
Server: smtp.mail.yahoo.com
checkmark: Server requires authentication
Security: SSL encryption
Type: PLAIN
Username: Yahoo! username WITHOUT "@yahoo.com"
checkmark: Remember password
```

---

### Post by rvchari on 2011-03-07
> **sean neilan said:**
> somebody gave me info onsetting up my yahoo mail(regular)on evolution as far as the receiving mail server type:IMAP,server imap.mail.yahoo.com,ssl encryption AUTH password
sending mail smtp server smtp.mobile.mail.yahoo.com server connection no encrytion AUTH plain remember password
now I get error while sending message host look up failed name or server not known
My yahoo is US based I'm in ca and I have had this e-mail for 3 years it is the only mail account that I have and I really don't want to get another one my college has this inf my funding and I dont want to remember a whole bunch of different accounts now can i get my basic yahoo mail to work with evolution or what I am really new at this computer stuff as you can tell by my typing skills so can ANYBODY PLEASE HELP!!:confused:

my family yahoo account (which is a free account) runs perfectly well with in.pop.mail.yahoo.com AND in.smtp.mail.yahoo.com (SSL and TLS for receiving and sending). now my personal yahoo account was not working with pop settings, after reading ur post, i tried it and it has been set up perfectly.
my personal yahoo account is also a free account.
server settings..
receiving = imap.mail.yahoo.com (SSL)
username = [email]USERNAME@YAHOO.COM[/email] or whatever your full id is
sending = (YOUR SMTP SERVER SETTINGS AS PROVIDED BY YOUR ISP)
try smtp.mail.yahoo.com with port 25. it should also work
in addition, i tried smtp settings like this..
username = COMPLETE YAHOO ID
server = smtp.mail.yahoo.com
SSL > choose option of LOGIN from pulldown menu beside.
check remember password
your email will be set up without hitch
all the best.... evolution will replace your daily headaches of logging on to web interface !

---

### Post by marl30 on 2011-03-07
> **rvchari said:**
> my family yahoo account (which is a free account) runs perfectly well with in.pop.mail.yahoo.com AND in.smtp.mail.yahoo.com (SSL and TLS for receiving and sending). now my personal yahoo account was not working with pop settings, after reading ur post, i tried it and it has been set up perfectly.
my personal yahoo account is also a free account.
server settings..
receiving = imap.mail.yahoo.com (SSL)
username = [EMAIL="USERNAME@YAHOO.COM"]USERNAME@YAHOO.COM[/EMAIL] or whatever your full id is
sending = (YOUR SMTP SERVER SETTINGS AS PROVIDED BY YOUR ISP)
try smtp.mail.yahoo.com with port 25. it should also work

all the best.... evolution will replace your daily headaches of logging on to web interface !The only mail client I'm currently having issue setting up is a free  Yahoo account in is Thunderbird. Evolution works great with Yahoo.

---

### Post by rvchari on 2011-03-07
> **marl30 said:**
> The only mail client I'm currently having issue setting up is a free  Yahoo account in is Thunderbird. Evolution works great with Yahoo.

use the same settings i mentioned for evolution in thunderbird. that should work fine.

my personal opinion is evolution is a bit light on resources and thunderbird is a bulky software. well, opinion differs, i used thunderbird a couple of years ago but now i am happy with evolution.
similarly, i opted from firefox to chromium (eventhough firefox is installed and i didnt remove it, just in case !)

---

### Post by marl30 on 2011-03-07
> **rvchari said:**
> use the same settings i mentioned for evolution in thunderbird. that should work fine.

my personal opinion is evolution is a bit light on resources and thunderbird is a bulky software. well, opinion differs, i used thunderbird a couple of years ago but now i am happy with evolution.
similarly, i opted from firefox to chromium (eventhough firefox is installed and i didnt remove it, just in case !)
The only reason I prefer Thunderbird is how quickly it loads my gmail mails, to Evolution's slow loading time. Otherwise they both do what I need them for. 

Going to test your settings to see if it works.

---

### Post by wep940 on 2011-03-07
I realize that Outlook Express is not used in Linux, but I think what I'm doing still applies.  I only have a free Yahoo account - I don't pay for any of it.  Using Outlook I was able to set it up to use SMTP.  Sometimes I have to manually sync, but it does work pretty well.  So, knowing that it's just the settings that allow this to work (Windows/Outlook Express really have nothing to do with it), it shouldn't be much to set up Evolution to use SMTP for free Yahoo mail.  I personally have never tried the pop, because my understanding is that if you want to use pop you do have to pay for mail.  There are tutorials out there for setting up pop on a free Yahoo mail account, but I've also seen lots of caveats about it may be illegal.  I'll stick with SMTP and my free account.  I have my laptop dual-booting but just never set up my mail there yet - I just use the "online" Yahoo mail.  I may try setting up Evolution the same as my Outlook Express to see how it works.

---

### Post by rvchari on 2011-03-07
> **marl30 said:**
> The only reason I prefer Thunderbird is how quickly it loads my gmail mails, to Evolution's slow loading time. Otherwise they both do what I need them for. 

Going to test your settings to see if it works.

i have kept gmail away from evolution. i have gmail notifier loaded and i open gmail only if any perticulat mail comes that needs attention.
if you r using docky, the gmail notifier will load with subject headers so you know which one is important. its just a convenience that i have opted. 
the general policy i follow is load ur email client with just minimum accounts coz the more accounts u configure, more time it takes to load...
try to balance between speed and ease of access thru email clients.. i know gmail takes longer time in thunderbird too in comparision to other ids... so is the case in evolution.
may b this is the cause i have kept gmail away from evolution and use gmail thru email notifier in dock. you clik on one button and ur web inbox loads in default browser...

nyways, do the jugglery and let me know how u got thru..
i ll be away and be back later

---

### Post by dwasifar on 2011-03-11
Well, guys, in response to some of what I've read here, I went and tested my setup and I discovered that using Yahoo's SMTP no longer works for me either.  I don't know when it stopped working; had to have been pretty recently.  But I don't send from the Yahoo account all that much, so it's hard to know for sure.

I switched the Evolution setup to use the same relay server I use for any other email account, and that works fine.  But that may not be an option for everybody, because I know many ISPs won't send mail that doesn't have a FROM address in their own domain.  I use a third-party SMTP relay for that reason.

Sorry if I added to the confusion.

BTW, if anyone is interested, I'm using dyndns.com's outbound relay service.  Used to be called Mailhop Outbound, now it's called SendLabs SMTP, but it's the same service; $20 a year gives you up to 150 outbound emails per day.  I've never come close to hitting the limit, and I've never seen it go down.  I recommend it.  And no, I do not work for dyndns.com; I'm just a satisfied customer, and it might solve some problems for some readers of this thread.

---

### Post by yui72o on 2011-03-14
It works with this configuration, Al hamdulillah
Thank you marl

> 

                                                                        Originally Posted by **marl30**                
                   [I]Make sure you have these settings if you are using a free Yahoo account in Evolution:

[/I]```

[I] Receiving Email Tab:
Server Type: IMAP+
Server: imap.mail.yahoo.com
Username: Yahoo! ID WITHOUT "@yahoo.com"
Security: SSL encryption
Authentication Type: Password
check mark: Remember Password

Receiving Options Tab:
checkmark: Check for new messages in all folders

Sending Email Tab:
Server Type: SMTP
Server: smtp.mail.yahoo.com
checkmark: Server requires authentication
Security: SSL encryption
Type: PLAIN
Username: Yahoo! username WITHOUT "@yahoo.com"
checkmark: Remember password 
[/I]
```

---

### Post by Murphy-10332 on 2011-10-03
For what it is worth, WOW! It is several years later but thank you all who posted the setup for yahoo. It works great. Once again thank you.

---

### Post by dcstar on 2011-12-22
My freebie Yahoo Mail IMAP uses Port 993 & SSL, so in Evolution you have to enter:

imap.mail.yahoo.com:993

And your full mail Yahoo e-mail address to access the account, as well as selecting SSL. Basically I followed this guide for Evolution:

[http://help.yahoo.com/l/us/yahoo/mobile/comms/mail/imap-01.html](http://help.yahoo.com/l/us/yahoo/mobile/comms/mail/imap-01.html)

---

### Post by morhin on 2012-04-02
Okay, here it is 2012 and I've gone through this, and several other threads, and my yahoo still isn't up and running.
I'm in the USA and I'm hoping that's the issue. Also I notice some threads say to set up IMAP+ but that doesn't even show as an option on my evolution setup. What's the deal?

I have not hours, but weeks into playing with this and to say the least I'm not a happy camper. I I only knew why it wouldn't work I could at least give up on it. That's the problem. I don't know if it's me.... you..... or the program.

Morhin

:mad:

---

### Post by H A Ghani on 2012-08-17
for those who still can't access regular yahoo email with evolution or thunderbird, try this setting.

this setting should let you in on both evo and thunder. but somehow if thunder does not let you in, get into preference, click security and then click view certificates. click server on the above tabs. scroll down and look for login.yahoo.com and click it. click edit trust. click trust the authenticity of this certificate. then click ok. if there are more than one, do the same thing on all of them. get out of the preference and try again. you should be all set.

let me know if this setting works for you guys.

Receiving Email:
Server Type: imap+
Server: apple.imap.mail.yahoo.com
Port 993
Username: yahoo id (no @yahoo.com)
Security: SSL encryption Authentication 
Type: Password check Remember Password 

Receiving Options Tab: 
checkmark: Check for new messages in all folders  

Sending Email:
Server Type: smtp
Server: apple.smtp.mail.yahoo.com 
Port 465
checkmark: Server requires authentication 
Security: SSL encryption Type: plain
Username: yahoo [EMAIL="id@yahoo.com"]id@yahoo.com[/EMAIL]
checkmark: Remember password

---

