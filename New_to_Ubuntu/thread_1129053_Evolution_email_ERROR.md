---
title: "Evolution email ERROR"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-04-18
Just set up Evolution in Ubuntu 8.10, and everything went great. I sent two test messages to different address', Gmail, and Verizon servers and all seemed to be OK.  I had two messages in OUT BOX, but nothing in SENT box.  I got [ERROR while performing operation][Host lookup failed SMPT- name or service not known]
I'm new to Evolution and manually installing email.

---

### Post by meho_r on 2009-04-18
Let say for the sake of example that you have a gmail account: [email]yed.ied@gmail.com[/email]

Take notice that your username in this example is **yed.ied** and you have to replace it with your real username when following the steps.

The settings are as follows.

1. Open Evolution and go to: Edit > Preferences > Mail Accounts > (your_account_name) > Edit

2. In the "Receiving Email" tab make sure that you have these settings:
```

Server type: POP
Server: pop.gmail.com
Username: **yed.ied**
Use secure connection: SSL Encryption
Authentication type: Password

```

3. In the "Sending Email" tab you need the following settings:
```

Server type: SMTP
Server: smtp.gmail.com
Use secure connection: SSL Encryption
Authentication type: PLAIN
Username: **yed.ied**

```

Please notice that in "Username" fields in both "Receiving" and "Sending Email" settings windows for a gmail account you have to put *only* username, not sufix *@gmail.com* (and please don't forget to replace bolded sections /i.e. yed.ied/ with your *real* username). However, for some other email providers it is possible that you have to put in the "Username" fields whole email address (i.e. Hotmail).

---

### Post by Yed Ied on 2009-04-18
I followed your instructions, I believe to the TEEE.  I'm not trying to get a gmail account, so I substituted Evolution for Gmail, I guess I didn't exactly follow your instructions, but I still have the same problem, my out going shows message in "OUT" but not in "SENT", and in fact isn't sent.  The rest of the program looks great, just not functional.

---

### Post by Ericyzfr1 on 2009-04-18
Did you get the proper server settings from your ISP or e-mail service? What e-mail service are you using?

---

### Post by Yed Ied on 2009-04-18
Re: Evolution email ERROR
For gmail, the settings are as follows:

1. Edit > Preferences > Mail Accounts > (your_account) > Edit

2. In the "Receiving Email" tab make sure that you have these settings:
Code:

Server type: POP
Server: pop.gmail.com
Username: (your_username_without_@gmail.com)
Use secure connection: SSL Encryption
Authentication type: Password

3. In the "Sending Email" tab you need the following settings
Code:

Server type: SMTP
Server: smtp.gmail.com
Use secure connection: SSL Encryption
Authentication type: PLAIN
Username: (your_username_without_@gmail.com)

_This what I have with the exception of substituting "Evolution" for "Gmail"

---

### Post by meho_r on 2009-04-18
It is maybe the best way to take a screenshots of those settings in "Receiving email" and "sending email" parts. It may be something that you omitted to notice (you may, if you like, make on those screenshots your username unreadable by smudging it in Gimp, e.g., but NOT the suffix after your username, if any, i.e., @gmail.com or @hotmail.com etc.)

Other option is that you create a gmail account for the testing purposes and follow above instruction, just to be sure Evolution actually works for you. 

And, of course, you have to get proper instruction for your email provider. As far as I can see, your SMTP settings are incorrect, and that is why you can't send any mail. It may be wrong SMTP server or wrong authentication. Check those settings again.

**[COLOR="DarkSlateBlue"]EDIT: I made some changes in my first post. Please try following those steps again.[/COLOR]**

---

### Post by Yed Ied on 2009-04-18
Server Type-   POP

Configuration
Server-   pop.evolution.com
Username-   yed_ied

Security 
Use Secure Connection-   SSL encryption

Authentication Type
Password
Remember password, checked
_____________________________________________________________________________

Sever Type-   SMTP

Server Configuration
Server-   smtp.evolution.com
Server requires authentication, checked

Security
Use Secure Connection-   SSL encryption

Authentication
Type-   PLAIN
Username-   yed_ied
Remember password, checked
________________________________________________________________________
I know this will never come out the orderly way I typed it, I just hope you can make sense of it.  I tried to copy & paste from word processor, but no dice.

---

### Post by oldos2er on 2009-04-18
Who is your email provider?

---

### Post by Yed Ied on 2009-04-18
I don't know.  I have accounts with Verizon and Gmail, I wanted this Evolution account because it is default in Ubuntu 8.10.  All I did was go into Evolution installation, and fill in the blanks, that is where I am now.

---

### Post by mlentink on 2009-04-18
But evolution is not an account, it is an e-mail program. If you have a gmail account, use the settings for gmail in your evolution setup and you'll be fine

---

### Post by Yed Ied on 2009-04-18
Thanks, I didn't know.

---

### Post by meho_r on 2009-04-18
Please, fill in exactly as in the example in my first post for your gmail account. Don't replace anything except username (which was bold in the post) with your real username. Try once again and tell us if you still cannot make it work, so we can try another ways. You'll get it working, don't worry ;)

---

