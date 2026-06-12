---
title: "Evolution - deleting read mail on server"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by kenmac2 on 2009-09-04
Hi folks,
Recently my Mailbox was shutdown because it was full.
Evolution doesn't seem to have the function  of auto-deleting the files on the mail server after they have been read.
I looked for an option but couldn't see one.
My ISP say that most Email programs do have this option.
Is Evolution supposed to delete the files after they have been marked as read ?

kenmac2

---

### Post by Zill on 2009-09-04
To delete your messages from the server after being downloaded to your PC:

Go to Edit, Preferences, Mail Accounts and edit your active account.
Select the "Receiving Options" tab
Uncheck the "Leave messages on server" box

Repeat for other accounts if desired.

If you also want to automatically empty your wastebasket of old emails then:

Go to Edit, Preferences, Mail Preferences
Select the "General" tab
Select required options under "Delete Mail"

Caveat: I am using an old version of Evolution (v2.6.1) but I guess the later versions have similar functionality!

---

### Post by stinger30au on 2009-09-04
evolution will read the files from the isp server and dlete from server and import

sounds like this tick box has been turned off on your evolution

start evolution

edit

preferences

click mail account

select user name

click edit

click receive options

make sure there is *NO* tick in the box that says "leave message in server"

click the ok button

thats it

---

### Post by t0p on 2009-09-04
In Evolution, go to **Edit > Preferences > Mail Accounts** and select to edit the account in question.  Now, under the **Receiving Options** tab, untick the box for "Leave messages on server".  Apply.  Now Evolution won't leave your emails on the server - ie, they will be deleted.

You're welcome.

---

### Post by mlentink on 2009-09-04
Uhm, eh,

Is this a POP3 or an IMAP account you're talking about?

---

### Post by kenmac2 on 2009-09-04
Thanks for the pointer to the option - I have now fixed the problem. 


kenmac2

---

### Post by tsagar on 2010-01-15
> **mlentink said:**
> Uhm, eh,

Is this a POP3 or an IMAP account you're talking about?

Hi, mine is an IMAP account. Also, my Evolution came with Karmic installation. In the mail account setting there's no 'leave mail on server' box to check or uncheck. Attached is the screenshot. Am I doomed to deleting the messages on the server manually for the rest of my life?
[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by amrooke on 2010-03-21
I too have had this issue with Evolution (using ver 2.28.1).  I have seen many different posts on this issue, and none of the replies hit the mark.  Many have offered up to uncheck the "Leave messages on server" option, but that will not work for me (and many others it appears).  I access my pop account from multiple locations and applications, so I need to keep a several week buffer of messages on the server at all times.  That said, I need to delete many spam and other unwanted messages from the client applications, and have those messages deleted from the pop server.  Thunderbird and MS Outlook (and possibly other clients) offer this option (see attachments), and it should not be difficult for Evolution to add it as well.  While I like most of the Evolution client, until this issue is addressed, I will have to use Thunderbird when in the Ubuntu environment and Thunderbird or Outlook when in the Windows environment.

---

### Post by amrooke on 2010-03-21
FYI . . .  I am actually currently using Karmic Koala 9.1 (64 bit and 32 bit, on various computers), but my profile showed me on an older distro.  Oops, it now appears that my profile has updated, never mind.  Regardless, this doesn't affect the Evolution issue . . .

---

### Post by Zill on 2010-03-21
Just a thought... I suggest you try deleting unwanted messages in Evolution, thereby moving them into the Trash folder.

Then right-click on Trash and hit "Empty Wastebasket(Trash)". Are the unwanted messages then deleted from the server as well as Evolution?

---

### Post by amrooke on 2010-03-21
Permanent deletion from within the Evolution client, which of course includes emptying of the trash has no effect on the pop server; therein lies the problem.

---

### Post by amrooke on 2010-03-21
I have added a request on Bugzilla to add this capability in future releases of Evolution ([https://bugzilla.gnome.org/show_bug.cgi?id=613550](https://bugzilla.gnome.org/show_bug.cgi?id=613550)).  If you agree that this would be a useful feature, please add your thoughts on Bugzilla too.

---

