---
title: "Dynamic IP address change notification?"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by tegwilym on 2008-11-18
I know there are things out there for Window$ that does this, but I'm looking for something for Linux obviously.

I can probably look around a little more, but figured I would try asking here too.  I'm looking for one of those utilities that will send you an email when the IP address changes on a remote router.

I have a computer in my basement that I like to access from work, but after a couple years with the same IP, Comcast has changed the IP twice in the last month or so now.  I wonder if anyone knows of a utility that would monitor the IP between the modem and router that could send an email when the external Comcast IP changes?  Maybe check once a day or something like that.

Anyone know of anything like this for Linux?  

Thanks, 

Tom 
 - Feeling better now that I got away from M$!  :)

---

### Post by eotakos on 2008-11-18
i'm actualy working on something like this...

my case is a little bit different... i'm trying to have the machine send me and email everytime it starts (with its dynamic IP)

and the thing is that i have everything pretty much configured, but i'm having some trouble with mailing during startup.

all i can help you with is this:

you can store your -at the time- ip in a file like this:

w3m whatismyip.org > file

you can also send an e-mail with the contents of a file like this:

mail -s "topic" [email]yourmail@work.com[/email] < file

this of course means that you have "mail" and exim4 installed, and configured as client to send mail (if you are interested in more of this continue the discusion)

so... if your pc at the bassement is up all the time, all you need is a timer, and you have your script ready! (timer to execute every day for example)

---

### Post by tegwilym on 2008-11-18
OK that does make sense.  I installed mailx and exim4 (already there in 8.04).  I just need to configure SMTP to the Comcast mail server - smtp.comcast.net  

Not sure where to put that, but I'm looking around at exim sites right now - unless someone can pass me a hint here!

Tom

---

### Post by Jayock on 2008-11-18
No need to config smtp servers, as Exim is an MTA itself, and will send without SMTP.

---

### Post by Jayock on 2008-11-18
If you havn't yet, configure exim with:

> 
sudo dpkg-reconfigure exim4-config


Then maybe try a script like this (not tested, just whipped this up)

> 
#!/bin/bash

ip="`w3m whatismyip.org`"
oldip="`cat /tmp/ip.txt`"

if [ "$ip" != "$oldip" ]; then 
`echo $ip > /tmp/ip.txt`
`mail -s "IP Change" "email@host.com" < /tmp/ip.txt`
fi

chmod 755 the script, then add to crontab at whatever interval, and you should be good

---

### Post by pmsumner on 2008-11-18
Why so complicated?  Why not try a service like dyndns.ocom and ddclient (in the repos) which will automagically update your dynamic domain name for you.

---

### Post by Jayock on 2008-11-18
If all you need is incoming connection, that is a great way.  Just reference your dynamic DNS address, and let it handle ip changes.  

If you have something like mysql replication for offsite backup, or something similar which is locked by ip, you probably care about ip changes.

Either way, an 8 line bash script is hardly complicated.

---

### Post by tegwilym on 2008-11-18
> **Jayock said:**
> If you havn't yet, configure exim with:



Then maybe try a script like this (not tested, just whipped this up)


chmod 755 the script, then add to crontab at whatever interval, and you should be good

Looks like what I was needing.  I'll play around with this and see if I can get it all working. 

Tom

---

### Post by eotakos on 2008-11-18
you are actually interested in sending mail only so you need only the client side of exim which is pretty much configured by default. Read all of the following before executing :-)

this is the file where you declare smtp server, username and password
/etc/exim4/passwd.client

and the line you add looks like this:
server:user:password       
the pretty face is : + p  can't make it go away

don't mess with the permissions of the file, and the password will be secure.
Note that this configuration is for smtp-auth that uses encrypted connection (LTS sometimes mentioned as SSH). If your smtp server doesn't use encryption then have a look at the doc pages of exim under /usr/share/doc/exim4-base and click at the 2.3 SMTP-AUTH paragraph at the contents. The instructions are pretty clear. Another choise is to make a gmail account and use encrypted connection with smtp.gmail.com

Now, as far as the "sudo dpkg-reconfigure exim4-config" side of things is concerned, this gives and easy to navigate menu thing. The configuration I use and therefor it is tested to work on 8.04 goes like this:

at the first menu i chose 3rd option -> smarthost, no local mail

at the second menu you choose the @my_home.com part of your email that will appear when you send your mail

then you read the passage, and if we both want the same thing, you type-in  127.0.0.1  so that exim won't listen for any incoming connections

for the next prompt, i filled in localhost

then you enter something you fancy like "home" or business or something

then you enter the smtp server you are about to use

finally, for the two last questions the answer is no


According to the community support docs about exim, after the reconfigure, you should execute the
sudo update-exim4.conf

So! the order you should do all this, is 
1)reconfigure 2)update 3)edit passwd-client  ... etc
at least this is what i did

Ah! and something else - if you create a gmail account, then be carefull not to be logged in to that account while sending mail from command line. I've wasted some time to figure how everything works...

I hope some of this helped!  Good luck

---

### Post by eotakos on 2008-11-18
about Jayock's post, i recommend that you check if the mail command works like this before putting it into the script.

I'm saying this because when i used the double quotes ("") to specify the topic, i got errors... i call the mail command like this:

mail -s 'topic with spaces' -v [email]tegwilym@mail.com[/email] < file
(the -v is for verbose output)

---

### Post by tegwilym on 2008-11-19
Everything looks right, but still not getting any mail outgoing.  I think I might have an idea what has happened though.

I had to change my Comcast outgoing to port 587 since they accused me of sending out spam.  Right....

Anyway, is there a place that I can set up smpt outgoing to port 587?  I assume it's going on the default 25.

Thanks for all the advice, I've learned a lot in just a few hours!

Tom

---

### Post by eotakos on 2008-11-19
hahaha spamming... i was accused of spamming too (by gmail). and i was just sending the same email to the same address while testing... lots of times...:-) 

About changing the port exim uses, I found in the exim-base doc i mentioned above (section 2.1.1.7) that the classic method is used: instead of the server you give  server::port
again the funny face is : + p  (sorry about that)

the thing is that i haven't changed any ports in my configuration, and it works with gmail that uses 465 or 587

---

### Post by tegwilym on 2008-11-19
> **eotakos said:**
> hahaha spamming... i was accused of spamming too (by gmail). and i was just sending the same email to the same address while testing... lots of times...:-) 

About changing the port exim uses, I found in the exim-base doc i mentioned above (section 2.1.1.7) that the classic method is used: instead of the server you give  server::port
again the funny face is : + p  (sorry about that)

the thing is that i haven't changed any ports in my configuration, and it works with gmail that uses 465 or 587

Hmm...I guess 587 might already be set as a "backup port" from what you said about your gmail.  No luck yet, I'll keep playing.

This isn't anything super critical, just annoying when I want to screw around with my computer at home and I can't reach it.  I often connect to my basement computer then connect to my MythTV machine upstairs and set up programs to record.  

I'll keep playing and see what happens!

Tom

---

### Post by tegwilym on 2008-11-19
Oh, I was doing the same thing as this once with Windows running one of those little utilities.  I think it was IPMonkey or something like that.  The computer was running very badly until I figured out that the "monkey" was dragging it all down.  Killed that off, and it worked again.  Ever try putting a Windows machine on the internet DMZ with no firewall? Talk about viruses....:)

---

### Post by eotakos on 2008-11-19
> Ever try putting a Windows machine on the internet DMZ with no firewall? Talk about viruses....

did you ran a collection or something :) :) :)

---

### Post by tegwilym on 2008-11-20
> **eotakos said:**
> did you ran a collection or something :) :) :)

Well, I was actually running Etrust antivirus on a Win 2000 machine exposed to the raw internet through DMZ.  The computer was so bogged down fighting viruses that I had to pretty much give up and reformat and start over.  Etrust was doing it's job, but the computer was unusable.  I have my Linux box on the same connection and it just keeps going and going and going....

---

### Post by eotakos on 2008-11-22
Ok, there are some news about my configuration which i'd like to share. First of all, i finally switched the smtp port as instructed by gmail to 587. I did this by running dpkg-reconfigure again, and giving smtp.gmail.com::587 at the field where the smtp server is requested. The smtp server parameter at the passwd.client file needn't be changed.


not quite right! - see the next post
> Also, after many tests, i realized that the email wouldn't be successfully sent if there wasn't any connection to the server the last few minutes. So, after the startup, if i would try to send a message, it would most probably fail; whereas if i logged in and out to the gmail account through http prior to sending the mail, the delivery would be successful. 

Another fact, is that a failure to send a message would go like this:
a)try to send message b)fail the authentication c)gmail tries to send message back with notes d)authentication succeeds e)the gmail's message is sent backwards. So at the end there is a successful authentication, but for the returning message.

The previous two facts considered, if you send two consecutive messages, the first one will most probably fail, but the second one will be successful. 

This don't actually fix the problem, but in the end i get what i need so...

---

### Post by eotakos on 2008-12-19
I'm posting again here, a few months later, to correct myself.

The reason for which the first sent-mail attempt would fail, is that the sent-mail request is forwarded. This means that the server that actually sends the mail is gmail-smtp-msa.l.google.com and not smtp.gmail.com  -  that is why exim won't give the password. all you have to do in order to authenticate, is to change the server name at the /etc/exim4/passwd.client

in case you aren't trying this with gmail, you can find the server to which you have to authenticate, by running the mail command with the -v (verbose) option. This way you can see something like "server"... connected. this is the one you should use. Note that you shouldn't change the server stated at the dpkg-reconfigure procedure. This is a whole other thing - this is the server that "forwards your call"

I hope this turns out to be usefull to someone... :-)

---

