---
title: "Hotmail inbox gone after Evolution setup"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by Contra75 on 2010-04-20
I have finally decided to sync my hotmail account into Evolution (pop3) on my laptop running Ubuntu. After I set everything up, it loaded the inbox into Evolution, but then I noticed that content of my inbox is now gone from the hotmail account. In other words when I look at my hotmail inbox in Firefox - there is nothing left. Also whenever I open mail in Evolution it is now expunged from my Inbox, and the only place I can see it is in the Evolution inbox on my Ubuntu laptop.

Is it supposed to be that way? Is there any way to return it all back?

Please help - I need to see my emails from my other computers also.

---

### Post by sydbat on 2010-04-20
As with every email client, you need to make sure that if you want your emails to remain on the server (in your case Hotmail) and be able to access them from wherever, you need to check (or uncheck) the option to "leave mail on server" in settings.

For example, I use Thunderbird. I go to Account Settings > Server Settings and chose to download all my mail from whatever server (it is the default). I can choose to leave the mail on the server too, just by checking the box next to 'Leave mail on server'.

However, since you have now downloaded all you mail from the Hotmail server onto your laptop, it is gone from your online Hotmail account. There is no way (that I am aware of) to put it back onto the Hotmail server.

---

### Post by e4uforums on 2010-04-20
I second sydbat - very good explanation.  

The only way to get your mails back on the server would be to follow the fix above, then forward the emails back to yourself at your hotmail address.  Not the most elegant solution but it would indeed get your mails back online.

---

### Post by shedo on 2010-05-03
I had the same disaster but figured out a nifty way for resolving my emails back to server:-
1- You need to configure a new IMAP account for your email in Evolution.
2- (Move) all of your emails from the POP (Inbox-Junk-Deleted-Send-etc..) account to the IMAP account.
3- Viola! You now have returned back your emails to the server !
4- You'll have the option to keep your IMAP or simply delete it and Sync your POP in order to sort your emails back to your computer (of course after checking on "Leave mails on server" checkbox ! ;)

---

### Post by -humanaut- on 2010-05-03
> **shedo said:**
> I had the same disaster but figured out a nifty way for resolving my emails back to server:-
1- You need to configure a new IMAP account for your email in Evolution.
2- (Move) all of your emails from the POP (Inbox-Junk-Deleted-Send-etc..) account to the IMAP account.
3- Viola! You now have returned back your emails to the server !
4- You'll have the option to keep your IMAP or simply delete it and Sync your POP in order to sort your emails back to your computer (of course after checking on "Leave mails on server" checkbox ! ;)

Is there IMAP support for Hotmail? I thought it was all pop

---

### Post by pricetech on 2010-05-20
You can log in to hotmail and go into your deleted items folder and move the emails back to your inbox.  You'll have duplicates when you open evolution again, but if you have checked the box to leave the emails on the server, they'll stay put this time.

---

### Post by daveuuuh on 2010-06-20
Well I had the same problem and I thought my emails were gone forever, but... they simply are in your "deleted messages" folder on hotmail.com, just "Move" them back to your Inbox, and check "Keep files on Server" in Evolution.

I hope I helped you out.

Dave Van Eetvelt

---

### Post by CookieMate on 2010-08-25
> **shedo said:**
> I had the same disaster but figured out a nifty way for resolving my emails back to server:-
1- You need to configure a new IMAP account for your email in Evolution.
2- (Move) all of your emails from the POP (Inbox-Junk-Deleted-Send-etc..) account to the IMAP account.
3- Viola! You now have returned back your emails to the server !
4- You'll have the option to keep your IMAP or simply delete it and Sync your POP in order to sort your emails back to your computer (of course after checking on "Leave mails on server" checkbox ! ;)

I've tried setting up my Evolution with IMAP but it didn't work, I'm quite new to Ubuntu.  Could you please provide me step by step instructions for this?  My hotmail deleted items are gone already :( all my email is on my computer now.  Any help is appreciate it.

---

### Post by beew on 2010-08-25
I don't know. I haven't had evolution or any mail client set up but the inbox in all save one of my hotmail accounts were wiped out, --they were not in "deleted message", just gone, cleaned. In fact, I haven't accessed hotmail through any other means than to log in honestly through firebox, no fancy mail clients, nothing at all.  Googled a bit I found out it actually happened to quite a few people. A bug in hotmail, apparently.

---

### Post by masasone01 on 2010-12-02
The same thing happened to me with the hotmail inbox. I've done this to get my email back to my inbox and also to send them to my gmail account without any forwarding, the emails seem to be the exact same.

So just follow this steps:
- Go to Edit->Preferences
- Click [Add]
- Type in whichever email address [server] you want your emails to go and click forward
- By Default you should have IMAP selected and you email already typed in, if not select it, type "imap.gmail/hotmail.com", type your username (if it's hotmail you'll need the whole [email]username@hotmail.com[/email]). Use SSL encryption. Click forward
- No need to check anything here. Click forward
- Use SSL encryption. Click forward
- Choose a profile name. Click forward
- Click apply

Now on the left side you'll see your email. You an drag and drop like any folders.

First post... hope you like it!:popcorn:

---

