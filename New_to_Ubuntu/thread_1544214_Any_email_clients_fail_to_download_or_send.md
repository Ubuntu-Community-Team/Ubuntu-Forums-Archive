---
title: "Any email clients fail to download or send"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Andrew Cook on 2010-08-02
Problem disappeared and can't find how to delete post!!

---

### Post by chamber on 2010-08-02
Who are you using for your e mails? GMail, Hotmail etc?

---

### Post by Andrew Cook on 2010-08-02
Hi,
I'm sorry that I deleted my original query as I thought problem solved but not so.
Here is problem. My email address is with yahoo. It's a ..@yahoo.co.uk account which can and is set to allow pop3 access and my mail can be sent and received with any pop3 client I use in windows Vista. Having discovered Ubuntu I find I can use it for all my work except email as  no pop3 client works. Though thats not  quite correct, inexplicably, with out changing any settings pop3 occasionally works. Hence I tried to delete my original post. Tried several clients and different versions of linux same problem no matter what email client or linux distribution. 
Trying to be cleaver today I tried Zimbra desktop for windows using wine and at same time tried it on Vista. Worked fine on Vista failed to connect on Ubuntu using wine. 
So any email client on vista works every time.
No email client works (rarely works) on Ubuntu, Mint Fedora and a couple of others I tried.
My thoughts so far:-
Ubuntu (I believe) installs with the fire wall completely open, so I presume cant be that.
I run Vista on a Toshiba laptop and Linux on a Compaq. Read somewhere hardware should not affect running of pop3 client.
Both computers connect through same router. Toshiba wireless and Compaq wired. 
Don't know if this helps but fire fox does not work on my Ubuntu but Chrome works perfectly.
Plying with Sylpheed for last few hours. Intermittently works getting mail. Not yet persuaded it to send. The only other client I had any success with was Eudora 7.1  which, again, intermittently sent and received. The open source version of it did not work. Bear in mind as the mail clients are intermittent in their working others may have worked on occasions if I'd have kept trying to send and receive.
I am no expert but I am savvy enough to enter all incoming and outgoing server details correctly with port numbers etc. Went so far as to copy paste details from yahoo help pages to ensure no typos crept in.
So I am thinking there is a Ubuntu setting some where that needs switching on/off. This matter has now taken days of research and trial and error and it's no further forward.  While tying this I did a get mail about 7 times on Sylpheed. It worked once giving connection failed on other attempts.
Any help greatly appreciated.

Andy

---

### Post by Andrew Cook on 2010-08-02
Further to my original postings. As a newbie to Linux is my problem that I need a Mail delivery agent installed and running? I'm reading and trying to understand how things work!!!!! I am getting the impression any pop3 client needs a Mail delivery agent to be able to send and receive emails. I shall read on, and hopefully start too understand enough to sort out this problem unless some with more experience can come to my rescue first.

Andy

---

### Post by Yogotiss on 2010-08-02
You should have try at thunderbird 3. Works perfect for all types of email. Thunderbird should be in your software center

---

### Post by jtarin on 2010-08-02
Try starting your mail clients from the command line. Then watch the output as you try to send or receive.

---

### Post by Andrew Cook on 2010-08-03
> **Yogotiss said:**
> You should have try at thunderbird 3. Works perfect for all types of email. Thunderbird should be in your software center

Tried it and same problem.

Andy

---

### Post by Andrew Cook on 2010-08-03
> **jtarin said:**
> Try starting your mail clients from the command line. Then watch the output as you try to send or receive.

Tried in terminal. First get mail operation worked and then tried again a few minuets later and get mail failed.  Terminal out put read:-
(sylpheed:2249): LibSylph-WARNING **: sock_connect_address_list_async: connection to pop.mail.yahoo.co.uk:995 failed


(sylpheed:2249): LibSylph-WARNING **: can't connect to server.

(sylpheed:2249): LibSylph-WARNING **: [07:01:00] Connection failed.

I found this problem in another forum posting. With no solution.

Sadly I cannot spend any more time on this.   
Ubuntu is great and it did everything I wanted except mail. So sadly for the time being I shall have to return to using windows. I will however keep an I on Ubuntu it obviously has a great future and maybe the pop3 problem will disappear in future issues..

Andy  :(

---

### Post by jtarin on 2010-08-03
Try the command  ```
telnet mail.somewhere.com 25
```where  "somewhere.com" is your mail provider.

I'm thinking you have a port problem. Who is your mail provider and where can I find instructions for setting up a client?

---

### Post by Andrew Cook on 2010-08-03
> **jtarin said:**
> Try the command  ```
telnet mail.somewhere.com 25
```where  "somewhere.com" is your mail provider.

I'm thinking you have a port problem. Who is your mail provider and where can I find instructions for setting up a client?

I will try telnet command tonight when I have more time to learn what I will be doing.
Mail provider is Yahoo.co.uk
instruction page for pop3 settings
 [http://help.yahoo.com/l/uk/yahoo/mail/classic/manage/pop-14.html;_ylt=ArNOQN57OONgv7FyeqYnXvJWRCV4](http://help.yahoo.com/l/uk/yahoo/mail/classic/manage/pop-14.html;_ylt=ArNOQN57OONgv7FyeqYnXvJWRCV4)
Should link not work coped and pasted instructions below:-

Incoming Mail (POP3) Server:	pop.mail.yahoo.co.uk (use SSL, port: 995)
Outgoing Mail (SMTP) Server:	smtp.mail.yahoo.co.uk (use SSL, port: 465, use authentication)
Account Name/Login Name:	Your Yahoo! Mail ID (your email address without the "@yahoo.co.uk")
Email Address:	Your Yahoo! Mail address (e.g. [email]user@yahoo.co.uk[/email])
Password:	Your Yahoo! Mail password

My account at Yahoo is set up for pop access and I have accessed it that way for years, using a client on Vista. The above setting were cut and pasted into account settings under various Ubuntu mail clients and different Liux distributions always same result,   intermittent working of send and receive. Mostly not working.

Regards and thanks for your efforts

Andy

---

### Post by jtarin on 2010-08-03
Try seting up an email client account logged in as root or give your user admin rights.

---

