---
title: "1 account, 3 pc´&#347;, 3 email adresses, problem."
date: 2009-02-10
forum: New to Ubuntu
---

### Post by captain_conrad on 2009-02-10
Hi there

as the caption states, this is my scenario:

One account (telkomsa.net)
Three Computers. (Desktop and two laptops)
Each computer belongs to a different person. Brother, Mother, Myself.
Three Email adresses. Problem is that every computer recieves everybody&#347; mail. This creates admin and I dont want the other two people&#347; mail and neither do they want mine.
The program im using is called evolution mail

please help with any advice on how i can make my computer recieve only my mail

thank you for your time
captain conrad

---

### Post by jimv on 2009-02-10
I don't understand.  You have 1 email account shared by 3 people on 3 different machines?  Or do you have 3 different email accounts?

---

### Post by captain_conrad on 2009-02-10
hey

We have one internet account. So its one payment to telkomsa a month.

This account gives you an email adress, which is what my mother uses

then the same account allows for two more email adresses, which my brother and I use

so we have

(moms email adress)@telkomsa.net
(one sons email adress)@telkomsa.net
(another sons email adress)@telkomsa.net

three adresses, three computers, each computer with its own user, yet one internet account allowing three email adresses.

my brothers computer is a desktop with that router modem thingie. my mother and I have laptops which connect to the internet via wireless, through my brothers desktop.

problem is now that each pc recieves all three email adresses´s incoming mail.

so in my inbox there is mail for my brother and for my mother, and in their inboxes is mail that is for me.

each email shows up on all three computer&#347; inboxes, its not like i have recieved their mail and they do not have it, and then i simply forward it to them.

what i need to do is set it somehow that my computer/evolution mail only recieves emails that were sent to my email adress.

hope i have clarified the situation. thanks for your help

captain conrad

---

### Post by jimv on 2009-02-10
Is it showing up like that in the telkomsa.net webmail?

You can check here:

[http://webmail.telkomsa.net/src/login.php](http://webmail.telkomsa.net/src/login.php)

As long as you have each machine set up for each individual email address, it doesn't matter if you're using the same connection.  It could be that your ISP isn't giving you different email addresses, but aliases of a single address.  Log into the webmail to see if that's the case.

---

### Post by captain_conrad on 2009-02-15
ok here´s the update on this situation

i have now found out that it is indeed one email account with three alias´s for one email account.

this explains why each pc receives all three people´s mail

now brother and mother are both running windows and using outlook express for their mail, whereas I Run Ubuntu Linux and use Evolution Mail

Now brother has his computer set so that it only receives/downloads HIS mail, he has figured out how to do it with ¨rules¨ on outlook express

Now in evolution mail there are rules but none of them allow u to NOT download anything that isn´t for you.

What we also found happening is that my mother´s pc was not downloading mail at all! and neither was brother´s! Whenever one of the pc´s downloads mail it downloads all new mail for all three aliases that is new since the last time that pc (or another pc) downloaded mail. So i´m sitting with their mail and they don´t have it! And they have my mail and i don´t! 
So If i just made a rule to delete the mail that didn´t have my alias email adress as the recipient, then the mail would be lost and the true recipient wouldn´t have received their mail. Bad idea.

so here´s the solution we came up with, please tell me if this is a good or a bad solution:

Step one

   Edit, Preferences, click on Mail accounts (on the left)
   Then selected the account, Then clicked EDIT
   In the account editor i clicked recieving options Tab
   I then put a tick in the box where it said:  Leave messages on server.
   I also set it to delete after 10 days
   then closed the account editor by clicking OK and closed the
   preferences window by clicking close

Step two

   I now clicked on the Message tab, create rule, Filter by recipients
   As criteria i made the recipient one of the alieses that was NOT mine
   As action i said delete message
   then clicked ok.

   then repeated the entire step two for the second alies that is 
   NOT mine

Done.

Now what i assume is happening ( correct me if i am wrong ) is that somebody will send a email to eg. my mother, i will hit Send/Recieve button, my pc will receive it, delete it, leave a copy on the server(for 10 days) and only place in my inbox what is MY mail.
A copy of the original message (sent to either of the other two aliases) will remain on the internet server untill my mother or brother hits send and recieve on their windows outlook express. Hopefully they do this within the 10 days i set it to, otherwise i will just have to change that 10 days to a longer period of time.

So is this problem solved? i hope it is

I&#314;l appreciate any feedback, thanks for all the help

---

### Post by Kellemora on 2009-02-15
Hi CC

Even though YOU check to leave mail for 10 days, it won't really matter, because the first person to download mail that day will cause the FLAG at the Pop3 server to show the mail was downloaded.

The only way I know around this is to set each machine to download ALL mail, even though someone already did, and then use your own filters to sort out which was read and which wasn't.

Or one other option is to ask your ISP to not use aliases and use real e-mail addresses for each person.  I have 8 e-mail accounts at one ISP, but have them forwarded either to my personal or my business mailboxs.  Your ISP shouldn't give you any problems over this, they could set up a hundred mailboxes for you at no real extra cost to them other than the time to do it.

A simpler way around it may be to use web mail instead of e-mail.  My wife actually prefers web mail, but she don't keep hers like I have to.
I know a lot of folks who have moved over to gmail, because I'm always getting notices to change their address in my address book.
So that is something to consider also!

Whom ever has the most important e-mail should probably keep the telco mailbox and the others use web mail somewhere.

TTUL
Gary

---

### Post by captain_conrad on 2009-02-24
Hi there

Just a quick update

So far the situation i described in the last post is working just fine, no problems at all...

I do end up with a lot of deleted messages as my evolution downloads copies of all the mail, and automatically deletes what is not adressed to my alias.

But the argument of using webmail is very valid. Just save all this trouble and just get your own email adress, hahahahahahaha...

Thanks for the help

Captain Conrad

---

