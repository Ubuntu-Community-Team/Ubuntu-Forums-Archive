---
title: "Trialling Ubuntu in Windows"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Rob Maddison on 2009-09-02
Hi all,
 
First post for newbie so be gentle with me.
 
I'm trialling Ubuntu 9.04 in Windows using Vurtual Box as suggested here - [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox). I only got it yesterday - yep, very new!
 
It looks great and I know it will all work. I have a new laptop and before it's too embedded in Vista and windows stuff I want to clear it completely and go Ubuntu all the way.
 
My problem at the moment is that in Virtual Box I can surf via Firefox but even thought I've configured the e-mail software to my account, and it checks the mail server without a problem, it's not showing any new messages. I had 5 this am in Windows Mail after trying to dl them on Ubuntu first with no success.
 
Any clues as to what's going wrong here as it all looks good to me.
 
Rob M

---

### Post by t0p on 2009-09-02
Which email client are you using?  (Evolution?  Thunderbird?)  What exactly is happening that makes you think it's all working fine except it's not downloading your mail?

---

### Post by ad_267 on 2009-09-02
I can only guess that your email application on Windows is running in the background and downloading the email first, otherwise I'm not sure what else could be the problem.

---

### Post by Rob Maddison on 2009-09-02
Thanks for the replies.
 
I figured it may be MS Mail getting in the way so opened Ubuntu without opening Mail this morning with no success.
 
I'm using Evolution Mail in Ubuntu, t0p. When I say it's working I mean it looks like it is connecting to the mail server but isn't finding any messages.
 
I also tried sending to my shop e-mail address from Evolution but never received it either in Evo or in MS Mail.

---

### Post by howefield on 2009-09-02
> **Rob Maddison said:**
> My problem at the moment is that in Virtual Box I can surf via Firefox but even thought I've configured the e-mail software to my account, and it checks the mail server without a problem, it's not showing any new messages. I had 5 this am in Windows Mail after trying to dl them on Ubuntu first with no success.

Open up your email client using Ubuntu and send yourself a test message, can you receive it using Ubuntu ?

Ah, I see you've done that, who is your email provider ?

---

### Post by Rob Maddison on 2009-09-02
Howefield - e-mail is with talktalk.net.
 
I've set up Evolution to the same settings as Mail - POP3 and smtp and server not requiring authentication so it looks like it should work. When checking mail Evo says 'getting mail' in the info bar at the bottom left but gets nothing.

---

### Post by jrothwell97 on 2009-09-02
The reason you aren't seeing any messages is because of the way POP works.

POP downloads the messages from the e-mail server and then deletes them. This means that if you check e-mails on a different computer, you won't download any e-mails that have already been downloaded.

Ideally, you should try using an IMAP mail provider. Google Mail can be configured to use IMAP, and it'll keep your mail boxes consistent across systems.

---

### Post by Rob Maddison on 2009-09-02
Thank you Jonathon but I don't think that's the problem given that it's not getting new mails either. I'm not trying to see old e-mails in Evo just trying to get it get new ones :-)
 
My last laptop was stolen a couple of weeks ago and I lost a whole load of history in e-mail that I know can't be replaced, hence the Ubuntu trial while everything is fresh outa the box :-)
 
Thx for explanation of POP though - not something I'd considered (or even knew anything about) and given both the business and home are with talktalk it's not something I'll look into in the near future either!
 
PS - I think tonight I'll burn the .iso onto CD and then do a dual boot to see if that solves the issue - now I know Ubuntu does what I need. I'm a man of simple demands from his 'puter - I want it quick, cheap/free if possible, surf the 'net and do e-mail. I do a bit of graphic work on GIMP and run the business records on Open Office that are clearly Ubuntu standards anyway. I'll test out more software and some hardware when I've got a dual boot going on rather than virtualbox.
 
Thx for the advice so far :-D

---

### Post by Gaweph on 2009-09-02
I would advise partitioning your vista to make it say 20GB, then making another partition for ubuntu say another 20GB.

Then use the rest of your hard drive for your HOME partition, accessible by both vista and ubuntu, to store your files.

Then in the future youl have your HOME partition safe and sound if you ever want to do anything to the rest of the systems.

Also it sounds like your MS mail propgram could be runnign in background and still stealing the mail ;)  CFheck the MS settings of outlook to check that it says "Leave messages on server"

---

### Post by Rob Maddison on 2009-09-04
Thanks for the advice on this.

I've now installed Ubuntu completely in a partition and Evo has just downlaoded all e-mails from the server.

That's it for me - just have to sort out the 'windows omly' software and all is well in my new world. Thanks for the help,

---

