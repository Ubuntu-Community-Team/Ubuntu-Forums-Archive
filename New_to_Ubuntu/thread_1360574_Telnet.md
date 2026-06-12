---
title: "Telnet"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Swenghk on 2009-12-21
I'm sorry if this is in the wrong section, but i did not know where to put it. Okay...

My dad is teaching me about internet Protocols and right now we are covering FTP and TELNET. I was following a tutorial he referred me to, but I have come to a standstill. I get an error when I run the following code:

```
seth@SETH-LAPTOP:~$ telnet
telnet> open pop.gmail.com 110
Trying 74.125.155.109...
telnet: Unable to connect to remote host: Connection timed out
telnet> 

```

What is going worng? Someone help me please. And thank you. Cheers mates :]

---

### Post by Grenage on 2009-12-21
It simply didn't get a reply, hence the timeout.

---

### Post by Swenghk on 2009-12-21
But how do I get a reply? What am I supposed to do? Am I doing something wrong?

---

### Post by Grenage on 2009-12-21
No, you're not.  It either doesn't respond on that port, or it just doesn't respond.

Sure the address/port is right?

---

### Post by wojox on 2009-12-21
```
telnet pop.gmail.com 995
```

---

### Post by Swenghk on 2009-12-21
Thanks "wojox"!

But I thought that was only for SSL? Can you explain please?

---

### Post by Swenghk on 2009-12-21
Dear me... Now when I do telnet port 995, i can connect but not login... Take a look if you will:

```
seth@SETH-LAPTOP:~$ telnet pop.gmail.com 995
Trying 74.125.127.109...
Connected to gmail-pop.l.google.com.
Escape character is '^]'.
user sethrobert94
Connection closed by foreign host.
seth@SETH-LAPTOP:~$ 
```

I'm sorry for all of the questions, but my dad said that it would be better if I got the answer by searching for it, and not just having him tell me.

---

### Post by Grenage on 2009-12-21
What's the difference between him telling you and us telling you?

You won't learn that way!

---

### Post by Swenghk on 2009-12-21
Learning by SEARCHING for the answer! Not like it matters no! He's asleep! It's 4:47AM where I'm at! Hahaha. But any assistance will be appreciated. I'm getting really into this! :]

---

### Post by Swenghk on 2009-12-21
bump

---

### Post by Grenage on 2009-12-21
It's considered rude to bump a thread unless it's about a day old.

---

### Post by Swenghk on 2009-12-21
I'm sorry! Woops! I didn't know! What else am I supposed to do? I still need to know! Hahaha! Do you have any suggestions Grenage?

---

### Post by fromthehill on 2009-12-21
found something

"Verify that your username is spelled correctly, and that you've entered '@gmail.com'." 

[http://mail.google.com/support/bin/answer.py?hl=en&answer=141047](http://mail.google.com/support/bin/answer.py?hl=en&answer=141047)

---

### Post by Swenghk on 2009-12-21
It's still not working:

```
seth@SETH-LAPTOP:~$ telnet pop.gmail.com 995
Trying 74.125.127.109...
Connected to gmail-pop.l.google.com.
Escape character is '^]'.
user sethrobert94@gmail.com
Connection closed by foreign host.
seth@SETH-LAPTOP:~$ 

```

I even tried another account!:
```
seth@SETH-LAPTOP:~$ telnet pop.gmail.com 995
Trying 74.125.155.109...
Connected to gmail-pop.l.google.com.
Escape character is '^]'.
user swenghk@gmail.com
Connection closed by foreign host.
seth@SETH-LAPTOP:~$ 

```

Thanks for all of you guys help... Any other suggestions... Is it me you think? maybe I'm doing something wrong...

---

### Post by fromthehill on 2009-12-21
read the link in my previous post
it isn't supposed to do anything :P

---

### Post by DrMelon on 2009-12-21
Telnet is kind of outdated and insecure, so Google probably no longer allows telnet connections. I suppose you could test telnet by hosting a telnet server on another computer...

---

### Post by Swenghk on 2009-12-21
That sounds complicated. Is there such a thing as a telnet test server? Hahaha. I don't know how to host telnet from another computer. My father has Windows Vista on his. Could I do it with that somehow?

---

### Post by Swenghk on 2009-12-21
Anyone? I've been at this for the past 5 hours. Hahaha. I haven't even went to slee yet!

---

### Post by Grenage on 2009-12-21
There's a thousand pages out there covering telnet sessions.  A few searches in google will give you all you need; do you really need to be spoon-fed?

---

### Post by t0p on 2009-12-21
Okay, slow down!  I think other members are getting you out of your depth by talking about "setting up telnet servers".  Heck, guys, he doesn't know how to connect to a server!  How's he supposed to know how to set one up!?

Your dad was right to tell you it's better to find out for yourself than to just ask him.  Unfortunately, he hasn't given you sufficient info to start with and now you can't ask him for it cos he's asleep.

The key is to do what your dad said: don't ask, find out for yourself!  But since you don't know anything, I'll help you find something helpful.

I went to Google and searched for "telnet beginner tutorial".  The very first result was [this site]("http://forums.techarena.in/guides-tutorials/29400.htm").  It claims to have tutorials for beginners, and also a list of sites that will allow you to connect to them via telnet to try things out.  Check it out.  If it's no good to you, return to Google (the results page is [here]("http://www.google.co.uk/#hl=en&safe=off&newwindow=1&q=telnet+beginner+tutorial&meta=&aq=&oq=telnet+beginner+tutorial&fp=177016bc12fe49d4")) and look for something more suitable for someone at your level of understanding.

Feel free to come back here whenever you feel the need.  But please bear in mind that we are all volunteers here.  We don't get paid anything for helping here.  If you post a question then start bumping every few minutes, you'll look very impatient, and some of our less understanding members may get impatient with *you*.  Don't worry, we're usually extra nice in the Absolute Beginners Talk forum... but we're only human!

Good luck!  And welcome to Ubuntu!!  :)

---

### Post by Swenghk on 2009-12-21
Thank you so much t0p. Seriously. You are a life saver. And Grenage, you need to calm down. You don't think I've been searching Google? I just didn't think there was going to be any tutorials. So don't waste your time posting that crap.

And thank you again t0p :]
How do I mark a thread as solved? I know... Dumb question... I've just never done it. Hahaha

---

### Post by Grenage on 2009-12-21
> And Grenage, you need to calm down. You don't think I've been searching Google?

No, I don't think so.  You're a classic case of a lazy user who would rather constantly ask questions than spend 5 minutes with a search engine.

> How do I mark a thread as solved? I know... Dumb question... I've just never done it. Hahaha

It's under *Thread Tools*.

---

### Post by Swenghk on 2009-12-21
Lazy? I've been searching how to telnet a POP3 server all night! Hahaha. That was pretty funny. lol. Alright well, I thank you too Grenage because you did help me with finding out how to mark a thread as solved :]

---

