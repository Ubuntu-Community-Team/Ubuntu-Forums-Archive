---
title: "HELP!!  Get old mail to Ubuntu v11.04"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by ICEhockeyGOALTENDER on 2011-06-29
I have a big problem, i need to get my old e-mails from windows (roadrunner account) to Evolution Mail. i have just installed Ubuntu on the computer and i don't know how to get the old important email back from my windows email client.... the bad part, i installed Ubuntu over windows so now there is no windows.....
i would really like to know if there is a way to get all my emails back from my old account, evolution only loads it from the previous two days and now all the important unread emails that i had. i went on my webmail.roadrunner account and it shows the same thing. i really need some big help with this issue......

wish me sooo much luck.....

thanks

---

### Post by ICEhockeyGOALTENDER on 2011-06-29
ok dont help, i only have like lots of bills to pay and lots on other importaint credit card stuff, ect. in my mail, no big deal!

---

### Post by heyho on 2011-06-29
You won't get much help bumping a 14 minute old thread with a reply like that.

I might be wrong, but as far as I know, emails are often stored encrypted, so even if you could get them back (which I doubt if you can), you may not be able to read them.

---

### Post by thane1 on 2011-06-29
Not sure, but possibly making a live cd of Knoppix would allow you to access the files, if they haven't been overwritten.  You can download the Knoppix distro from their website at [www.knoppix.org](www.knoppix.org) and then write the iso to a cd.  Boot from that and maybe you'll find what you're looking for.  cheers

---

### Post by amjjawad on 2011-06-29
Just to make sure whether Windows is overwritten or not, please run this command in the Terminal and post the output here between "code" tags.

```
sudo fdisk -l
```

it's small "L".

---

### Post by psusi on 2011-06-29
If you erased windows, and your mail was in windows, then it should be fairly obvious what happened to your mail.  Unless you made backups, it's gone.

One of the nice things about a proper email provider is that you can keep the mail stored on their server and just access it via multiple IMAP or web clients instead of having to download and store it on your computer.  Bloody road runner only supports unencrypted POP3 access, so you are forced to download it and if you ever check your mail from say, a wifi connection, someone can sniff your password and read your mail.

---

### Post by LowSky on 2011-06-29
Your email is gone. When you set up any email account, make sure you set it to not delete the emails on the server side. Its a very simple thing. Even with POP3 or IMAP. Keep them on the server and they don't go bye-bye.

We are a group of users who like to help, not a support center that gets paid. Please be nice and don't expect an in less than 5 minutes of a posting.

---

### Post by crispy_420 on 2011-06-29
From what has been said so far you may have lost it all when you installed on top of Windows. So hopefully for you one of two things happened: you made backups or you can still access them via webmail with ISP. I'm thinking your client is maybe only pulling new messages and old ones marked as read are still on the server. Have you looked there?

I would suggest setting up your client to leave a copy on the server if possible when it pulls mail.

---

### Post by psusi on 2011-06-29
> **LowSky said:**
> Your email is gone. When you set up any email account, make sure you set it to not delete the emails on the server side. Its a very simple thing. Even with POP3 or IMAP. Keep them on the server and they don't go bye-bye.


Mail providers that only support POP3 also usually have fairly low storage limits, so leaving mail on the server isn't an option.  At one point I had enough volume of email that my roadrunner box would fill up if I didn't check it for a few days.  POP3 also don't keep track of what mail has been read or support multiple mailboxes because it was originally designed to pick up mail, not leave it on the server.

---

### Post by jtarin on 2011-06-29
> **ICEhockeyGOALTENDER said:**
> ok dont help, i only have like lots of bills to pay and lots on other importaint credit card stuff, ect. in my mail, no big deal!First thing is I would go check my backup folder, which I make once a week,and I keep all the files that are valuable to me. Then I would convert my files if needed to be read by my alternate software selection. If I couldn't find what I needed there I would go to my webmail account and retrieve whatever files I needed backed up on the server of my unlimited free account then if I couldn't find it there I would go to my second email account where every mail of importance is forwarded.....either manually or by filter. If I couldn't find it there......they haven't sent it yet.:p

---

