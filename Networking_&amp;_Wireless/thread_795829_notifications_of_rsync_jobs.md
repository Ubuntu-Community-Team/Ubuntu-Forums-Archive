---
title: "notifications of rsync jobs?"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by jcup on 2008-05-15
I am in the midst of discovering what rsync can do... awesome technology...

I'm to the point where I have a test run going right, after a long days work, everything seems to be working smoothly...

I have been searchin the internet and forum posts here to find out how I can set up email notifications once the job is done.

I would like for my computer to email me the results like success/failure and possibly all the details if it fails.

Is that something I can specify in the cron job, or in the rsync script...

I'm still a little new at this, but not really a noob either, so technical talk or general help would be great...

So, if anyone knows how to do this, I would be really very appreciative...

THANKS!!

---

### Post by jcup on 2008-05-16
bump

yes/no/please anyone?

thank you

---

### Post by SpaceTeddy on 2008-05-16
cron will autoamticially mail you ANY output that a job procudes for every time it runs. That is why most cron jobs only produce output when they encounter errors. so, no, there is nothing special to do to setup email notification. Just specify your job as you would normally run it (including the output) and cron will email you the log.

I guess the real question is how to email the stuff to you. THAT is a more tricky business. I can see three things happening here...

1.) local mail only and you simply use pop3 to access your server directly to get the results. I have that setup with my server so i get the cron mails.

2.) you configure your MTA (mail transfer agent) to use a smarthost (external email host) to send out email. This usually needs an smtp server that you can relay the emails to. I have only done that configuration for exim4 so far but can tell you how to do it.

3.) you configure a full MTA on your machine. This requires you to have a static ip (sort of anyways), a DNS hostname and an MX record at your provider. This is the most powerful setup, yet the most complex to achive too. 

In your case, i would go for 1.) if it is only one server, or 2.) if you have more than one server that you want emails from. 


cheers :)

---

### Post by jcup on 2008-05-18
Thanks for the info, I will deffinately learn a bit more about cron... haven't had a need for it till now.

Thanks

---

### Post by gjosef on 2008-11-11
Thanks SpaceTeddy for good info!

> **SpaceTeddy said:**
> 2.) you configure your MTA (mail transfer agent) to use a smarthost (external email host) to send out email. This usually needs an smtp server that you can relay the emails to. I have only done that configuration for exim4 so far but can tell you how to do it.

I'd like to try this. Any advice on how to get started?

---

