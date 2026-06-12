---
title: "Control your computer through the power of email?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-07-28
I was just curious, is it possible to type a command in the subject or body, then send the email, and the other computer would read the subject and/or body and execute it? or even better, would be to attach a bash script and have it automatically run it? :P

---

### Post by philcamlin on 2009-07-28
aha no its not possible :(

---

### Post by halitech on 2009-07-28
didn't you basically ask the same thing earlier?

[http://ubuntuforums.org/showthread.php?t=1224932](http://ubuntuforums.org/showthread.php?t=1224932)

---

### Post by taylor102387 on 2009-07-28
yea, but shutting down would require superuser privileges, and I just want to know if it's possible to execute simple commands, not limiting answerers to only shutting the pc down.

---

### Post by PhoHammer on 2009-07-28
> **philcamlin said:**
> aha no its not possible :(

Not for RFS: [http://lwn.net/Articles/262570/](http://lwn.net/Articles/262570/)

I don't know if your asking about the same sort of thing though....

---

### Post by s3a on 2009-07-28
If you want to control a computer from another computer's terminal, then look into *ssh*.

---

### Post by philcamlin on 2009-07-28
> **PhoHammer said:**
> Not for RFS: [http://lwn.net/Articles/262570/](http://lwn.net/Articles/262570/)

I don't know if your asking about the same sort of thing though....

he wants remote desktop through email :popcorn:

---

### Post by HotShotDJ on 2009-07-28
> **taylor102387 said:**
> I was just curious, is it possible to type a command in the subject or body, then send the email, and the other computer would read the subject and/or body and execute it? or even better, would be to attach a bash script and have it automatically run it? :P

:shock:

Automatic execution of commands sent via email?  That is the most insanely insecure thing I have ever heard of!

---

### Post by philcamlin on 2009-07-28
> **HotShotDJ said:**
> :shock:

Automatic execution of commands sent via email?  That is the most insanely insecure thing I have ever heard of!

+1 its liek having a terget saying hack me :popcorn:

---

### Post by philcamlin on 2009-07-28
why dont you look into ssh

---

### Post by NullHead on 2009-07-28
This is insanely insecure.

---

### Post by s3a on 2009-07-28
If you want to control a computer from another computer's terminal, then look into *ssh*.

---

### Post by donkyhotay on 2009-07-28
Seriously, imagine what would happen if the spammers that are always trying to convince us to buy male enlargement devices and pr0n could start issuing commands to your computer? If you *really* want your computer to be part of a botnet you might as well get something out of it...
As mentioned before, look into ssh, your system will thank you for it.

---

### Post by ahndoruuu on 2009-07-28
Why would you even ask a question like that?

You know email is one of the main perpetrators in spreading viruses...

That said, what you are asking is not impossible, but very implausible and grossly insecure.  

However there are similar technologies that allow you to control your computer remotely, and much more securely. As everyone else said, look into ssh.

---

### Post by llamabr on 2009-07-28
I'm sorry that you asked an interesting and reasonable question, and then 10 people replied with nothing more constructive than name calling.

Yes, what you want is possible.  You could execute some commands easily with procmail recipes.  But any sensitive commands would leave you open to attack by malicious emails, or even accidental ones.

---

### Post by taylor102387 on 2009-07-28
What if you have to put the password at the beginning of the body or subject, then the command, if the passwords no right you cant get in. But email is in plain text, so not the safest way.

---

### Post by whitethorn on 2009-07-28
I agree with most of the ppl here, have a look into ssh and dyndns.  If you want to be able to connect to your pc from windows all you need is putty.  Using emails is just way to insecure.

---

### Post by taylor102387 on 2009-07-28
I also just wanted to know if this was possible, I have ssh on my pc, and was thinking about the advantages of email. Here are some you said and what I think.

SSH:

1. Secure
2. Works
3. Accesses files like ftp, and executes commands
4. Just freakn' SAFE

E-Mail:

1. Easy to use (Even though SSH is easy) Easier
2. Accessible on almost every internet abled device
3.  Faster access

This is stupid, but ive seen ssh over the internet, it's just a hack waiting to happen.

---

### Post by oldos2er on 2009-07-28
> **taylor102387 said:**
> I was just curious, is it possible to type a command in the subject or body, then send the email, and the other computer would read the subject and/or body and execute it? or even better, would be to attach a bash script and have it automatically run it? :P

 There used to be FTP by email, and I think Usenet by email too. Found a link that might be helpful to you: [http://www.faqs.org/faqs/internet-services/access-via-email/](http://www.faqs.org/faqs/internet-services/access-via-email/) . This is from the period before spam became a huge problem, obviously.

---

### Post by donkyhotay on 2009-07-28
> **jasonbird said:**
> It sounds terrible....
Can we???

It's linux, you *can* do anything you want. Even if there isn't any way to do it yet you just take the source code of some Email client and modify it to read the Emails and execute bash commands from them. On the other hand you need the technical know-how to do something like that. I'll admit it'd be beyond my capabilities as a programmer but it's interesting as a concept theory (I'd never put it into practice due to the inherent dangers). Reminds me of a similar idea I had years ago which involved having an Email server that would read specially crafted Emails, turn that information into a URL, go online, covert the website into some sort of static image (like a PNG) then Email that image back to the sender as an attachment along with the URL's of any hyperlinks identified within the HTML code of the site. The idea was to have a way to browse the internet on my cell phone in a limited fashion. This was some time ago when MMS was new and cell phones didn't come with browsers. I never put it into action because I had no clue where to even begin and of course cell phones started coming out with browsers making the concept obsolete.

---

### Post by taylor102387 on 2009-07-28
Thats a good concept, but yes, it is a little outdated, and the internet through email was very intresting.

---

