---
title: "Evolution"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by JohnRory1971 on 2009-01-03
This may sound like a silly query but here goes anyway....

I have a gmail account and have configured Evolution for the account. I am sending emails in Evolution without a problem but only receive emails as long as they are not from me ie. if I send a test email from Evolution to myself it is not received back in Evolution. If I log into gmail using Firefox I can see that the test email is there.

Any idea as to why it is not received back in Evolution?

---

### Post by cmnorton on 2009-01-04
I take it you can see the email you sent to yourself using the gmail interface. Is that correct? Do you see this email in Evolution's sent folder? Could this be due to a gmail setting of some kind?

Are you using gmail's smtp to send, and do you have privs to do that? On yahoo, you have to pay extra dough to use their pop and smtp.

The only other thing I can think of is an smtp setting that's not correct but not incorrect enough to flag an error. Check you /var/log files.

---

### Post by Slowspeed on 2009-01-04
> **JohnRory1971 said:**
> This may sound like a silly query but here goes anyway....

I have a gmail account and have configured Evolution for the account. I am sending emails in Evolution without a problem but only receive emails as long as they are not from me ie. if I send a test email from Evolution to myself it is not received back in Evolution. If I log into gmail using Firefox I can see that the test email is there.

Any idea as to why it is not received back in Evolution?

Sir,
If you are using IMAP to connect to your gmail account that appears to be normal. I believe it is just the way Evolution handles the IMAP connection with gmail. 
My account does the same thing. I do know that it is not a problem with your Evolution as Google does not do a complete implementation of IMAP. At least this is my understanding.
Regards,

Slowspeed

---

### Post by JohnRory1971 on 2009-01-06
> I take it you can see the email you sent to yourself using the gmail interface. Is that correct? Do you see this email in Evolution's sent folder? Could this be due to a gmail setting of some kind?

Are you using gmail's smtp to send, and do you have privs to do that? On yahoo, you have to pay extra dough to use their pop and smtp.

The only other thing I can think of is an smtp setting that's not correct but not incorrect enough to flag an error. Check you /var/log files.

Hi I can see the email in the gmail interface and the email is in Evolution's sent folder. I'm not sure how settings in gmail would cause this problem as I'm getting other emails but I will check it out anyway.

I'm not sure about privs but will investigate. SMTP settings look ok. Where would I find the var/log files?

---

### Post by JohnRory1971 on 2009-01-06
> Sir,
If you are using IMAP to connect to your gmail account that appears to be normal. I believe it is just the way Evolution handles the IMAP connection with gmail.
My account does the same thing. I do know that it is not a problem with your Evolution as Google does not do a complete implementation of IMAP. At least this is my understanding.
Regards,

Slowspeed

I have POP enabled on my gmail account not IMAP. Is there a difference?

---

### Post by Slowspeed on 2009-01-09
> **JohnRory1971 said:**
> I have POP enabled on my gmail account not IMAP. Is there a difference?

Simple answer: POP is a protocol for downloading email to your computer, IMAP protocol keeps the email on the email server for you to read from multiple machines and or email clients.

Excerpt from [www.imap.org:](www.imap.org:)

 POP was designed to support "offline" mail processing. In the offline paradigm, mail is delivered to a (usually shared) server, and a personal computer user periodically invokes a mail "client" program that connects to the server and downloads all of the pending mail to the user's own machine. Thereafter, all mail processing is local to the client machine. Think of the offline access mode as a kind of store-and-forward service, intended to move mail (on demand) from the mail server (drop point) to a single destination machine, usually a PC or Mac. Once delivered to the PC or Mac, the messages are then deleted from the mail server. Although the limitations of offline access have triggered interest in using POP in online mode, POP simply doesn't have some of the functionality needed for high-quality online (or disconnected) operation. Indeed, POP's "pseudo online" mode of operation, wherein client programs leave mail on the server, often depends on pervasive availability of a remote file system protocol in order for the mail client to access or update saved-message folders or message state information such as status flags.

IMAP can also do offline processing, but its special strength is in online and disconnected operation. In online mode, mail is again delivered to a shared server, but the mail client does not copy it all at once and then delete it from the server. It's more of an interactive client-server model, where the client can ask the server for headers, or the bodies of specified messages, or to search for messages meeting certain criteria. Messages in the mail repository can be marked with various status flags (e.g. "deleted" or "answered") and they stay in the repository until explicitly removed by the user --which may not be until a later session. In short: IMAP is designed to permit manipulation of remote mailboxes as if they were local. Depending on the IMAP client implementation and the mail architecture desired by the system manager, the user may save messages directly on the client machine, or save them on the server, or be given the choice of doing either.

While offline and online mailers both allow access to new incoming messages on the mail server from a variety of different client platforms, the similarities stop there. The two paradigms reflect different requirements and styles of use and they don't mix very well. Offline works best for people who use a single client machine all the time; it is not well-suited for the goals of accessing one's inbox of recent messages or saved-message folders from different machines at different times. That's because if you use offline ("download and delete") mail access from different computers at different times, your mail tends to get scattered across the different computers, unless they are all linked to a common network file system (in which case your access mode is really more online than offline.)

---

### Post by Slowspeed on 2009-01-09
> **JohnRory1971 said:**
> This may sound like a silly query but here goes anyway....

I have a gmail account and have configured Evolution for the account. I am sending emails in Evolution without a problem but only receive emails as long as they are not from me ie. if I send a test email from Evolution to myself it is not received back in Evolution. If I log into gmail using Firefox I can see that the test email is there.

Any idea as to why it is not received back in Evolution?

I forgot to add this link to an answer.
sorry about that.

[http://groups.google.com/group/Gmail-Help-Discussion/web/send-email-to-self](http://groups.google.com/group/Gmail-Help-Discussion/web/send-email-to-self)

---

