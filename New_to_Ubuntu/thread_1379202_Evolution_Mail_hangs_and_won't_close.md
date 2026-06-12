---
title: "Evolution Mail hangs and won't close"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by jermza on 2010-01-12
I've set up my Evolution mail to sync with Gmail via IMAP.  Firstly, Evolution has to reload EVERY email after rebooting.  Secondly, it takes FOREVER to open one email.  There are loads of operations running at the bottom (refreshing folder structures [labels in Gmail] and retrieving this and that).  I cancel the operations and it all starts up again within a few seconds.

Then I try shut down Evolution and it completely hangs.  It stays in my panel and I can open a second instance of it.

What is going on?

---

### Post by caravel on 2010-01-12
The problem is IMAP, set it up as use POP/SMTP and you'll be ok.

---

### Post by audiomick on 2010-01-12
my guess, and it is a _**guess**_, is that Evolution is having trouble with or completely failing to write to and read from it's config file.

If you open the file manager and choose "show hidden files" from the "view" menu, you should be able to see a directory called .evolution. Is it there?

edit: regarding the post from caravel, I am using IMAP, have been for several years, and don't have a problem. My mail is at gmx. Maybe there is a specific problem with gmail and IMAP

---

### Post by jermza on 2010-01-12
> **caravel said:**
> The problem is IMAP, set it up as use POP/SMTP and you'll be ok.
But then it's going to download emails (whether or not it leaves copies on Gmail) onto my local machine.  That means increased bandwidth usage.  For example, I might not want to download a video file that someone attached to their email.  I might want to download it later, for example.

Isn't this the purpose of IMAP?  (Which is how it works in Snow Leopard.)  Or am I misunderstanding.

---

### Post by ricardisimo on 2011-05-07
> **jermza said:**
> But then it's going to download emails (whether or not it leaves copies on Gmail) onto my local machine.  That means increased bandwidth usage.  For example, I might not want to download a video file that someone attached to their email.  I might want to download it later, for example.

Isn't this the purpose of IMAP?  (Which is how it works in Snow Leopard.)  Or am I misunderstanding.

I'd say you understand it perfectly. Evolution is hanging for me as well, intermittently before Natty, and now perpetually. There are other problems as well, but they're for another thread, most likely.

---

### Post by wadechandler on 2012-01-09
I think if the Ubuntu team spent some time on Evolution fixing its issues it would make for an awesome solution. Right now, it doesn't. POP was fine years ago, but IMAP, folders, and having the same views on different systems, including web mail, such as GMail, is a requirement today. I love the "features" of Evolution, but it is simply becoming more and more unusable less as a very simple email client. Google contact tie in, really awesome, when it works, when it doesn't work, leaves one wanting to just use the browser and say screw it. Not cool. I'm thinking about going back to Thunderbird and writing my own plugin to hook into calendars, tasks, and contacts for gmail. Would be easier than having to kill and restart Evolution in the middle of work all the time.

---

