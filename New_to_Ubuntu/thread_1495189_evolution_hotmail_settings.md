---
title: "evolution hotmail settings"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by mvalviar on 2010-05-27
I can't get hotmail to work. I've used the settings suggested in ubuntuforums and else where. I can retrieve mail but cannot send them. Tried port 25 and 587. I always get connection timed out or connection reset by peer.

---

### Post by -humanaut- on 2010-05-27
Hotmail doesn't work real well with Evolution,Thunderbird,etc... I think *which i've read on here* you'll only be able to receive e-mail from hotmail.

---

### Post by jameshigley on 2010-05-28
gimme a few mins, i'm trying to remember how to do it exactly, i've NEVER HAD any issues when set up correctly!

---

### Post by Paresh on 2010-05-28
I have no problems receiving and sending hotmail from evolution

I used the settings in this [thread]("http://ubuntuforums.org/showthread.php?t=1124293") (see comment 9) and it works in Lucid.

---

### Post by jameshigley on 2010-05-28
OK MY FRIENDS, I WOULD LIKE TO MAKE THIS ONE A STICKY, BUT I DON'T KNOW HOW!

To make hotmail work with evolution, without any stupid programs on the side, 

put your basic info in, you need to have pop3.live.com for incoming with a port of  995, in other words, your incoming is "pop3.live.com:995 and you want your encryption to be SSL .  THEN on your incoming you want [EMAIL="SMTP@LIVE.COM"]SMTP.LIVE.COM[/EMAIL]:587 AND you want TLS encryption here.  then before you click ok, make sure, on the second screen, you have a space that will have your full email address, but for some reason evolution removes the "live.com" for me everytime, fix that and you should be good to go!  Any questions, just holler, i'll hook you up!  

UBUNTU FORUMS!  IF YOU WANT TO, SEND THESE QUESTIONS MY WAY, MAYBE I CAN HELP THE NEWBIES OUT A LITTLE MORE, AS I KNOW YOU GET TIRED OF ANSWERING THESE QUESTIONS!  :popcorn:

---

### Post by startgame412 on 2010-05-28
For using hotmail with evolution, you set up hotmail as a pop3 account. Create a new e mail account. Type your name and your e mail address either @hotmail.com or @msn.com depending on what your e mail address is. The server type is pop3 and the server is pop3.live.com. The username is your full hotmail or msn e mail address. Use secure connection should be set to use SSL encryption. On the next page be sure to check leave messages on server if you want your messages to stay on the hotmail site for viewing on other computers. For sending e mail the server type should be SMTP and the server should be smtp.live.com. Make sure server requires authentication is checked. Use secure connection should be set to TLS. Your username again should be set to your full hotmail or msn e mail address.

---

### Post by warfie on 2010-06-21
Cheers jameshigley, I've set it up a dozen but didn't remember to add the port numbers this time until I read your post... I was going mad! You saved my sanity!

One small point though, you said incoming instead of outgoing when referring to the SMTP settings... *I* knew what you meant but others might not...

---

### Post by philinux on 2010-06-21
[https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution)

---

### Post by Mi11z on 2010-08-13
> **jameshigley said:**
> OK MY FRIENDS, I WOULD LIKE TO MAKE THIS ONE A STICKY, BUT I DON'T KNOW HOW!

To make hotmail work with evolution, without any stupid programs on the side, 

put your basic info in, you need to have pop3.live.com for incoming with a port of  995, in other words, your incoming is "pop3.live.com:995 and you want your encryption to be SSL .  THEN on your incoming you want [EMAIL="SMTP@LIVE.COM"]SMTP.LIVE.COM[/EMAIL]:587 AND you want TLS encryption here.  then before you click ok, make sure, on the second screen, you have a space that will have your full email address, but for some reason evolution removes the "live.com" for me everytime, fix that and you should be good to go!  Any questions, just holler, i'll hook you up!  

UBUNTU FORUMS!  IF YOU WANT TO, SEND THESE QUESTIONS MY WAY, MAYBE I CAN HELP THE NEWBIES OUT A LITTLE MORE, AS I KNOW YOU GET TIRED OF ANSWERING THESE QUESTIONS!  :popcorn:

This one works, thank you, saved it as a note in gedit for future occurrences :)

---

### Post by Dreagonith on 2010-10-27
[B]Quote:

"Re: evolution hotmail settings[/B] 			 			 			 		   		 		 		OK MY FRIENDS, I WOULD LIKE TO MAKE THIS ONE A STICKY, BUT I DON'T KNOW HOW!

To make hotmail work with evolution, without any stupid programs on the side, 

put your basic info in, you need to have pop3.live.com for incoming with  a port of  995, in other words, your incoming is "pop3.live.com:995 and  you want your encryption to be SSL .  THEN on your incoming you want [EMAIL="SMTP@LIVE.COM"]SMTP.LIVE.COM[/EMAIL]:587  AND you want TLS encryption here.  then before you click ok, make sure,  on the second screen, you have a space that will have your full email  address, but for some reason evolution  removes the "live.com" for me everytime, fix that and you should be good  to go!  Any questions, just holler, i'll hook you up!  

UBUNTU FORUMS!  IF YOU WANT TO, SEND THESE QUESTIONS MY WAY, MAYBE I CAN  HELP THE NEWBIES OUT A LITTLE MORE, AS I KNOW YOU GET TIRED OF  ANSWERING THESE QUESTIONS!  :popcorn:[B]"

I know this has already been said but I researched for two days trying to fix my problem and this was the only one that worked. Thumbs up. Specifically the :587 was the fix. Ty.
[/B]

---

### Post by LordDelta on 2011-01-13
Didn't actually figure this out from here, but wanted to say this solution works here as well, figured it out independently from pictures on someone's Wordpress blog, actually...

...now if I can find out if hotmail has any secret imap settings...

Or how exchange syncing works on linux. :/

---

### Post by Yogotiss on 2011-01-21
> **philinux said:**
> [https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution)

Thank you so much this helped out a lot. Even though Thunderbird 3 configures with no problem, I wanted to use something different and you solve my issue by providing the link. Thanks!!

---

### Post by Ealadin31 on 2011-02-07
> **jameshigley said:**
> OK MY FRIENDS, I WOULD LIKE TO MAKE THIS ONE A STICKY, BUT I DON'T KNOW HOW!

To make hotmail work with evolution, without any stupid programs on the side, 

put your basic info in, you need to have pop3.live.com for incoming with a port of  995, in other words, your incoming is "pop3.live.com:995 and you want your encryption to be SSL .  THEN on your incoming you want [EMAIL="SMTP@LIVE.COM"]SMTP.LIVE.COM[/EMAIL]:587 AND you want TLS encryption here.  then before you click ok, make sure, on the second screen, you have a space that will have your full email address, but for some reason evolution removes the "live.com" for me everytime, fix that and you should be good to go!  Any questions, just holler, i'll hook you up!  

UBUNTU FORUMS!  IF YOU WANT TO, SEND THESE QUESTIONS MY WAY, MAYBE I CAN HELP THE NEWBIES OUT A LITTLE MORE, AS I KNOW YOU GET TIRED OF ANSWERING THESE QUESTIONS!  :popcorn:
This rocked and worked perfectly TY

---

### Post by phillustine on 2011-09-11
That worked! Many thanks.

---

