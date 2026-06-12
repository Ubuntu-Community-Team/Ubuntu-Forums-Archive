---
title: "Setting up Postfix in Ubuntu"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by EmyrB on 2008-04-15
Hi all,

I need some help with postfix. My request is simple. I have user A who sits with a PC in office AA with an internet connection. We use BT business broadband who have no SMTP services. I want to be able to setup user A to use Outlook to send e-mail through postfix and that's it. Postfix will not be responsible for incoming e-mail just sending.

Right I downloaded postfix onto a Ubuntu 7.10 box and answered the questions it asked and it then installed with no issues. I set outlook to use the box's IP address for the SMTP. I then go and send a test e-mail and I get an error which basically runs along the lines of error 5.7.1 <user@email.com> relay access denied. So I telnet in on port 25 and sure enough it tells me that it cannot relay. No matter what e-mail address I use it says relay denied.

I have searched the internet on how to configure postfix but they all seem to be very complicated or how to send via gmail.

Do I need SMTP-AUTH to send to any mail server? If so is there any clear and concise instructions on how to do this?

Is there a out of the box SMTP server software available that I can use without all the fuss?

Cheers

EmyrB

---

### Post by ginge6000 on 2008-04-15
Are you sure that BT aren't blocking port 25?  Quite a number of them do.

---

### Post by EmyrB on 2008-04-15
I know for sure that they are not blocking port 25 as the office in question did have a microsoft exchange server running there for about 5 years. The exchange server was removed as only one person is left in the office so hence the need to get some sort of SMTP service there.

Cheers

EmyrB

---

### Post by EmyrB on 2008-04-16
Actually the box in question is sat in my office waiting to be configured and sent to the office in question. When I use telnet and put in the address I am trying to send to, it comes up relaying denied awfully quick.

---

