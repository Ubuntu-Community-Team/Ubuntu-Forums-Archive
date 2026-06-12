---
title: "Thunderbird"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by elleppahc on 2009-05-12
Help Please.
Just tried to send an email, got message saying unable to connect to SMPT
it may have a fault or not set up properly.
I have not changed anything.
So far have reinstalled Thunderbird  no luck.

Anyone any Ideas?

---

### Post by bennachie on 2009-05-12
It's not uncommon for a mail server to drop out of service briefly for one reason or another, and the problem is almost certainly unrelated to Ubuntu. Usually, the server in question will come back on air relatively quickly.

If you have previously been able to send messages with your current settings, I suggest that you save your outgoing emails as drafts, and try to send them again in a couple of hours. If the problem persists, check with your ISP.

---

### Post by philinux on 2009-05-12
> **elleppahc said:**
> Help Please.
Just tried to send an email, got message saying unable to connect to SMPT
it may have a fault or not set up properly.
I have not changed anything.
So far have reinstalled Thunderbird  no luck.

Anyone any Ideas?

Has it worked before and you've not changed any settings since? If so post #2 is spot on.

---

### Post by elleppahc on 2009-05-12
Contacted ISP Orange  Set t what the said, as they have limited support for linux in general, so no remote assistance.
Still same message unable to connect to SMTP server

---

### Post by Dill on 2009-05-12
If you highlight your Account and click on the "View Settings for this Account" option, then check the settings for your "Outgoing Server", how do you have the Outgoing Server set up? Yours won't be the same, but as an example, here's what I have (see attached screenshot).

When you set up Thunderbird with this e-mail account, did you follow a set of instructions online for setting up the account? It would have included configuration information such as the POP/IMAP server, SMTP server, and security configuration information.

Whether or not your ISP offers "Linux Support", they should be able to provide you with this information, since it's server-specific and the same for any mail client on any operating system.

Cheers,
Dill

---

### Post by elleppahc on 2009-05-13
Have checked all settings, all appear to be ok.
Still getting error message. can still receive mail, but cannot send

---

### Post by Ericyzfr1 on 2009-05-13
Try to rewrite your outgoing server settings, along with your password..if your ISP requires one.

---

### Post by elleppahc on 2009-05-13
well I have re entered all settings and still the same.
I am probably missing something very simple, but just what it is is a mystery to  me

---

### Post by philinux on 2009-05-13
Double check the smtp server name.

I made the error once of putting smpt instead of smtp

Try also secure connection = no.

---

### Post by elleppahc on 2009-05-13
Yes have tried that, still not sorted.
Even setup new account, still no success



:p

---

### Post by meho_r on 2009-05-13
Have you tried with a gmail or hotmail account? Do they work?

---

### Post by lazyart on 2009-05-13
Instead of telling them you're on Linux, ask them for the settings to configure your mail client.  Thunderbird is the same on Windows as it is in Linux.

---

### Post by Bernie Slepkov on 2009-08-25
Hi elleppahc. I've been trying to find a place to put this, so thanks for the opportunity.

Want to get thunderbird to stop asking for the password? (Before starting I apologize if I seem to be repeating myself. Trying to cover wording variations for a google search. Way too many bogus suggestions out there regarding thunderbird constantly asking for a password.) I've tried to give detailed instructions mainly for the newbies, so sorry for the length.

After a lot of trial and error, (but not making any notes), I have succeeded at stopping t-bird from always asking for a password even on launching (starting up) and on three different computers all with:
    * operating systems Linux Mint 7 (Gloria)
    * Thunderbird 2.0.0.23
    * gmail.com accounts
    * two access sympatico.ca accounts using the same password used for the gmail account.

I think that getting to the solution is more a matter of a number of settings falling into place, than which version of Thunderbird or flavor of linux you might have. Someone might know just which of the settings really do matter, meanwhile, here's how to prevent thunderbird from always asking for an email account's password.

In thunderbird, select from menu:
Edit --> Preferences --> Advanced tab.
Click 'Config Editor...' button --- about:config window opens. In the Filter input at the top of window, enter 'password' and check the values of the following Preference Names. Note that to change incorrect values, double clicking on Preference Names of the boolean type toggles the value. Double clicking on a 'Preference Name' if no value is given at all will initiate a list from which to choose the value. Just don't ask me to explain why these settings work. Actually, I think some of the settings defy logic, however, the following settings do seem to work:
    mail.password_protect_local_cache ... boolean ... false
    mail.pop_password ... string ... 
    mail.remember_password ... boolean ... false
    mail.server.server3.remember_password ... boolean ... true  (server number may vary) 
    pref.privacy.disable_button.view_passwords ... boolean ... false
    signon.expireMasterPassword ... boolean ... false

Next, in the filter box at top of about:config window, remove password and enter signon
    mail.server.default.singleSignon ... boolean ... true
    signon.expireMasterPassword ... boolean ... false
    signon.rememberSignons ... boolean ... true

Next, replace signon in filter with login
    mail.auth_login ... boolean ... true
    mail.server.default.login_at_startup ... boolean ... false
    mail.server.server2.login_at_startup ... boolean ... true
    mail.server.server3.login_at_startup ... boolean ... true (the computer I'm using to prepare these instructions accesses two accounts)

Close the about:config window, but leave the Thunderbird Preferences window open for the next stage.

For the next step, we need to start over setting up the email accounts, so there are some things to consider in preventing thunderbird from always asking for a password. If you've been using email for sometime and want to safeguard any email folders you may have, I suppose you'll have to back up your email and folders. In my case, I was pretty well starting from scratch so can't really advise you from any experience on how to do that. I can say that the following process won't affect your address books. I suppose you could back up emails and folders by moving them into the 'Local Folders' especially if, like me, you want to keep your email account folders separate.

In the Preference window, select the Privacy tab.
    Select the 'Passwords' tab.
    Select 'Edit Saved Passwords' button.
        (BTW, I've noticed that for some reason, the "Username" appearing for some 'Site's in the opening window, seem to be <not specified>. Go figure.)
    Select 'Remove All' button.
    Select 'Close' button.

    Important Note! The Thunderbird Preferences window is still open. The "Use a master password to encrypt stored passwords" check box must be unchecked ... or blank. Again, don't ask me to explain it, just do it!

    Now, finish the preferences by clicking on the 'Remove Master Password...' button. You will be asked for your 'thunderbird' password to remove it. Note that this is NOT the linux administration password. More than likely, it is the same password you've been using for your email account.
    Click on 'Close'.

The next stage involves removing any and all existing email accounts. Here is where I could have used notes and observations to better direct you, alas ...

Still in thunderbird, select from menu:
Edit --> Account Settings...
    Select each account (except Local Folders. Not sure what would happen if the 'Local Folders' was removed. Also, before you select the 'Remove Account' button, make note of whatever your settings are. You might need to refer to them.)
    Click on 'Remove Account' button
    Click on 'Outgoing Server (SMTP)' in left-hand window.
    Remove every server shown (Don't forget to first make note of your existing settings for reference.)
        Note! Be aware that for some unknown reason, Thunderbird doesn't offer you the option of removing the last remaining server and when you reestablish your accounts, as you will soon see, that server will be listed twice. Remember to remove one of duplicates.

Now close Account Settings, exit Thunderbird completely, wait a couple of minutes and relaunch. No password should be requested since no accounts currently exist, so now we set up the email account(s).
    
Select from the upper text menu:
    Edit --> Account Settings...
        You should only see Local Folders, Disk Space, Junk Settings and Outgoing Server (SMTP) at the left.
    Clicking on 'Add Account...' opens up the Account Wizard with a listing of 5 kinds of accounts, including Gmail as well as Email account. Having a sympatico.ca and gmail.com account, I can tell you there are fewer steps to setting up Gmail. I am not going to go into step-by-step detail as far as setting up each type of account. Just a couple of points you might want to know and I will list what settings are working for me as I can email out from either account without being asked for passwords beyond the first time it is requested.
    * Note that in entering a Gmail Address versus an Email Address, @gmail.com is automatically assigned. You just enter the part before the '@' sign.
    * You should have noted the setting for 'Incoming Server' before you removed the account.
    * If you want each email account to have its own set of folders, (inbox, draft, sent, etc) then remove the check from the "Use Global Inbox" checkbox.
    * Some postings I've read regarding how to stop t-bird from asking for the password raise the issue of pop versus imap. Since some suggested changing POP to IMAP, and I have POP for both my accounts, I don't think it really makes a difference.
    * In setting up the Incoming User Name, the wizard window only suggests what your user name might be. Any screw-up in setting this up can be corrected later. You may notice later as I did something like [email]your.name@email.com@email.com[/email] in the Account Settings. You can change it without any problems.
    * Setting up the Account Name I always experienced some buggy behaviour. This is intended to be the 'title' of your account, the one that appears in the Account Settings window to the left. You can also change this later. The Wizard defaults to the email address, in which case if you accept it, the Account Name will actually be set to something like: Email - [email]your.name@email.com[/email]. If you want something like just Email as the account name, put it into the wizard input form and the next stage should take you to the end of setting up the account. On one occassion, I seemed to have gotten myself into a loop where I was never brought to the 'Congratulations!' window allowing me to verify my settings. I just escaped out of the Account Settings and started over. If you do just want Account Names to simply be 'Gmail' or 'Sympatico' as I just suggested above, then I recommend clicking on the 'Finish' Button and rather then step your way through all the Account Settings that should now appear under the account heading, close the Account Settings and reopen it. I say this because if you don't, and go through the various settings for the account, the wizard might seem to have ignored settings related to the account name you would rather have than the default. Trust me. It can get confusing. Closing and reopening the Account Settings fixes this bug.

Repeat the process for each account. (For newbies, I'll list certain settings that are working for me, following the instructions for the next stage)

The next phase initiates email retrieval from the accounts. If you exit Thunder and relaunch any time later, email retrieval will kick in if you have checked off 'check for new messages at startup' in the Server Settings for any of the accounts. Either way, the 'Password' window will open, detailing for which account the password is required. Before you enter the password, be sure that this the checkbox 'Use Password Manager to remember this password' IS checked. Now enter the password and hit return ... or whatever. You should be able to tell if everything is correct, by watching the status window at the very bottom left hand of the window. Otherwise, check your account settings.

Assuming you succeeded at downloading email, or at least accessing the email server, the next stage is to set the password for outbound email. You will need to do this for each account. And if you have more than one account, when you select 'Write', you should notice the From: input enables you to select from which account you are emailing. Send yourself a few test emails. The first time, for each account, you will be asked for your password, and for each, follow the same instructions given for retrieving email.

Now, instead of retrieving your email right away. Exit from T-bird and relaunch after waiting a couple of minutes. Provided that neither of us screwed up, You should rarely if at all, be asked for your password again.

Now for my pertinent settings:
Account Name: Gmail  (since I only have one)
Server Settings:
    Server Type: POP Mail Server
    Server Name: pop.gmail.com  Port: 995 Default: 99  (Note, this depend what you have chosen for the Security Settings that appear below.
    Use secure connection 'SSL' should be selected. DO NOT CHECK 'use secure authentication'
    Leave messages on server (check this box as you wish. It shouldn't affect the password as some posts seem to indicate. Same thing with regards to checking for new messages! That only matters if you haven't overcome the password issue in the first place.)

Account Name: Sympatico  (since I only have one)
Server Settings:
    Server Type: POP Mail Server
    Server Name: pophm.sympatico.ca  Port: 995 Default: 99  
    Use secure connection 'SSL' should be selected. DO NOT CHECK 'use secure authentication'

Outgoing Server (SMTP)  - Note! One of your outgoing server will be set to default, but you can change which one is assigned the privilege.
    Description: Gmail
    Server Name: smtp.gmail.com
    Port: 587
    UserName: (whatever your email server would require. For Gmail, it's what appears to the left of the '@' sign. For my sympatico, you will see the user name is the full email address)
    Secure Connection: TLS  (Take note that it's not set to SSL!)

    Description: Sympatico
    Server Name: smtphm.sympatico.ca
    Port: 25
    User Name: (whatever your full sympatico email address is)
    Secure Connection: TLS (if available)

Important note! If you see <not specified> in the User Name, select the account and click on edit. Select the 'Use name and password' checkbox under 'Security and Authentication' and then input your User Name into the form.

That's it! Hope this all helps.

---

### Post by stalkingwolf on 2009-08-25
I had the same problem with thunderbird.  worked fine then all of a sudden
wouldnt send.  I got a tech that knew something, he said to change the port to 110.  i did and have had no problem since.

---

### Post by atroq on 2009-08-26
Hi guys,

same problem here - smtp in thunderbird used to work until a few days ago. I noticed that a thunderbird update was installed since then. Anybody know if this might be the cause of the problem?

Btw, I have the same settings in my windows thunderbird client and it still works fine, so the mail server is up and running. I also tried changing the port number as suggested in a previous post, but to no avail.

Thanks in advance for any ideas,

Jan

---

### Post by LewRockwell on 2009-08-26
> **atroq said:**
> Hi guys,

same problem here - smtp in thunderbird used to work until a few days ago. I noticed that a thunderbird update was installed since then. Anybody know if this might be the cause of the problem?

Btw, I have the same settings in my windows thunderbird client and it still works fine, so the mail server is up and running. I also tried changing the port number as suggested in a previous post, but to no avail.

Thanks in advance for any ideas,

Jan

yes, it's almost always something with the vendor side regarding SMTP failures

.

---

### Post by Sir Jasper on 2009-08-26
Hi,

As a short term workaround you could try the Portable Windows version of Thunderbird from within wine. It is downloadable free from Portable apps and it works a treat on my machine.

My regards

---

### Post by corncob on 2009-08-26
Are you logging on to a different network or ISP than you did when your SMTP was working?  I have an eeepc 1000 running Xandros Linux and Thunderbird.  I send and receive mail through my ISP's (bellsouth.net) mail server (mail.bellsouth.net).  However, when I take my netbook to some place not on bellsouth.net, I can no longer send mail tghrough Thunderbird although I can still receive it.  We figured that bellsouth.net doesn't like to send mail originating on another network.  A workaround that was suggested was to download your mail and while the server was still open quickly send your out going mail.  However, this never worked for me and I ended up logging on to their website to send mail.  I hope this makes sense.

---

### Post by atroq on 2009-08-27
corncob: that's funny. actually, I am on a different isp because I this is the first time I actually left home with this laptop of mine. Like you, I can receive email but not send any. However unlike you, I was never using the e-mail servers of my home isp, it was totally unrelated email provider.

btw, I found out that my windows thunderbird's smtp was working because it was accidentally still using an unsecured smtp connection. once I set it to TLS (same setting as my linux thunderbird), it gives me a certificate warning, saying that the encountered certificate is does not belong to my e-mail provier, but to "outbound.mailhop.org". When I try to continue anyway, the connection fails.

I know that this makes it a pure thunderbird problem - anyone happen to have any ideas what I could do to fix this nevertheless?

---

### Post by corncob on 2009-08-27
[QUOTE/] I know that this makes it a pure thunderbird problem - anyone happen to have any ideas what I could do to fix this nevertheless?[/QUOTE]

My computer came with Evolution but I downloaded and installed Thunderbird instead because it had a news reader.  Maybe Evolution has one now too as its been a while since I looked.  I should give it a try but actually its not a big thing in my life: once a month at the computer club meeting if I even get a chance to use it.  The couple of friends I take it over to are also on bellsouth.net and I haven't noticed any problems.

---

### Post by atroq on 2009-08-27
Same problem with evolution. Maybe it really is a problem of may email provider after all. Sorry for bothering you guys and thanks for your help!

---

### Post by Darkwing-Duck on 2009-08-27
I have had this problem in the past and the solution was a bit... interesting. Talk to your ISP/WebHosting company. Because of the spammers tagging onto SMTP servers and sending spam they are starting to disable the default port of 25. Most places are starting to use 26 or another one. 

Just contact them and ask them what SMTP port that you should be using and hopfully that will work. With Thunderbird it is a little harder to find the SMTP port area then it is for Evolution. 

Tools>>Account Settings>>Outgoing Server(SMTP)

Change the port there to what was supplied by your ISP/WebHost and you should be good to go.

--------------
[David Wonderly]("http://wiki.ubuntu.com/dwonderly")

There are 10 types of people in the world. Those who understand binary and those who dont.

---

### Post by mike555 on 2009-08-27
You also might check your saved passwords in Thunderbird ,if you accidentaly typed the password wrong and told it to save you might have two or more passwords saved for the same smtp ......... that is what happened to my parents ........

---

### Post by corncob on 2009-08-27
> **atroq said:**
> Same problem with evolution. Maybe it really is a problem of may email provider after all. Sorry for bothering you guys and thanks for your help!

Oh, okay, I won't bother trying it then.  Asking around at the computer club somebody said that some ISPs disable SMTP for people not on their network so they can't send out spam in your name.  This is about the same thing as Wonderly just said.

---

