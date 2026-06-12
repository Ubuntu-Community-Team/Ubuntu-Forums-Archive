---
title: "SMTP mail box abroad"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by Gretha on 2011-06-03
When at work abroad, I usually buy a local pay-as-you-go 3G Mobile Broadband SIM card for my mobile broadband dongle to connect to the internet on my netbook. (The netbook has Ubuntu 11.04 Desktop Edition.)  A common problem is that the local Mobile Phone service provider often does not offer any SMTP server address for my outgoing e-mail.  Therefore, I cannot send any e-mail via Thunderbird.

Can I set up an SMTP server on my netbook which will accept my outgoing e-mails sent from Thunderbird, and which will route them properly via the internet to the addressee?

There are two issues to consider:

(1)  It is intended merely as a helper utility to get SMTP functionality, for just a few (usually max 10-20) e-mails sent per day by myself.  And netbooks have limited capabilities.  Therefore a very lightweight minimum solution seems the best, simply to get an "on-board" SMTP address that will always work whatever my 3G service provider.

(2)  Unfortunately I have no meaningful experience in non-GUI applications.  So, if it involves terminal commands and configuration file editing, then please help with full step-by-step instructions.  Thanks!

---

### Post by jtarin on 2011-06-04
[Try this.]("http://my.opera.com/Contrid/blog/show.dml/478684")

---

### Post by Gretha on 2011-06-04
@ jtarin 
 
Thanks for this.  I installed and set up Postfix as instructed in your link.  (Apart from following the installation instructions in your link and apart from specifying the new SMTP server in Thunderbird, I did not change anything else.) 
 
Next, I sent a test e-mail with Thunderbird on my netbook (using a 3G Mobile Internet connection, ie, not my own ISP) to my works account.  This properly arrived in my works inbox, without any significant delay. 
 
Then I also sent a test e-mail to a gmail.com account.  But that e-mail did *not* arrive in the GMail inbox.  However, there was no error message returned to Thunderbird either, saying that GMail had failed to deliver this e-mail.

So, it appears this second e-mail has simply disappeared without notice.  I waited a few hours to allow for any possible delays, but neither proper delivery nor a bounce message materialized. 
 
This is disconcerting.  What should I do to stop any e-mails disappearing without trace or notice?

---

### Post by jtarin on 2011-06-04
Wasn't aware of the Gmail...Secure ports is the problem, but your lucky.[ Read carefully, including comments section. Should be good to go. Ensure your have correct ports for Gmail. ]("http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html")

---

### Post by Gretha on 2011-06-09
@ jtarin

Thank you so much for your help.  Your references put me on track!

For other netbook or laptop users who encounter the same problem of not having an SMTP server when abroad, I have written a step-by-step beginners instruction.  It follows in the next post.

Thanks again!

PS  Any further comments and contributions by readers of this post are most welcome.

---

### Post by Gretha on 2011-06-09
[B]

(0)  Introduction:  No SMTP Server with your 3G/4G Dongle?[/B]

Let us assume, you use your *works e-mail account* in Thunderbird on your netbook.  You are out of the office.  And you are connected to the internet using a 3G/4G dongle from some TelCo mobile phone service provider.  Then your works e-mail system will not normally allow you to send any outgoing e-mail through its SMTP server:  It will *block your outgoing e-mail* if it receives it from you *while you are on the internet through a third-party ISP*.  So, how can you send e-mail using Thunderbird on your netbook using a 3G/4G dongle?

Now, let us also assume that you cannot remotely access your internal works computer system through a secure VPN (virtual private network).

Then, you will need an *outgoing e-mail (SMTP) server* that works *while you are online through your dongle's TelCo*.  Preferably, in fact, you would want a solution that is independent of the 3G/4G TelCo service provider which you happen to be using.  Then you can use any 3G/4G dongle / SIM card wherever you are in the world, without the need ever to change any SMTP settings in Thunderbird.

There are at least two solutions.

The first employs a proper _*Mail Transfer Agent*_ (MTA), such as *Postfix*.  (See section (1), below.)  The Postfix package is available in the Ubuntu main repo, and you can set it up on your netbook.  It offers powerful and versatile functionality.  But, as all mail server software, it is command-line-only software (no GUI).  So, you must be sufficiently experienced working in command-line mode.  And you must be willing to explore the detailed ins and outs of Postfix.  This may be more than you need.

The second solution uses a _*Google SMTP server*_.  (See section (2), below.)  This is simpler and quick to set up and test.  It does the job well, but it does nothing more.  For example, it cannot easily and neatly handle two different work e-mail addresses.  (There are some possibilities using aliases in Google Mail, but they are very limited.)

Below, you will find a _step-by-step beginners guide_ to these two approaches.


**(1)  Setting up Postfix as an SMTP Server on your Netbook, whatever your ISP**

Use Applications > Ubuntu Software Centre to install Postfix (or, in a terminal screen called up by Ctrl+Alt+T, enter: [FONT=Courier New][SIZE=3]sudo apt-get install postfix[/SIZE][/FONT][SIZE=2])[/SIZE].[INDENT]Note:  Suppose you have an existing old installation of Postfix on your netbook, and you are unsure about its current configuration settings.  Then you may wish to completely remove it first (including all its old configuration files) by typing the following instruction in a terminal window:

[FONT=Courier New][SIZE=3]sudo apt-get purge postfix[/SIZE][/FONT]

You can then do a clean re-install of Postfix, as described above.
[/INDENT]During the installation of Postfix, *two pop-ups* appear, asking for a *computer name* and for *Postfix use*.  Enter [FONT=Courier New][SIZE=3]localhost[/SIZE][/FONT] and choose [FONT=Courier New][SIZE=3]internet[/SIZE][/FONT], respectively.

Next, open Thunderbird, Edit > Account settings > Outgoing Server (SMTP).  Here, enter:

[FONT=Courier New][SIZE=3]Server Name:  localhost
Port:  25
Connection security:  None
Authentication method:  No authentication[/SIZE][/FONT]

Finally in Thunderbird, go to Edit > Account settings > your own works account details.  On the first configuration panel for your own works account, select from the drop-down box at the bottom:

[FONT=Courier New][SIZE=3]Outgoing Server (SMTP):  localhost[/SIZE][/FONT]

This completes the b[SIZE=1]asic[/SIZE] setup of Postfix on you netbook.  Whichever 3G/4G TelCo service provider you use for internet connectivity, this setup will usually function for all e-mail sent.  And your outgoing e-mail messages will be properly routed and delivered to the addressee.

However, there is at least _one major exception_:  When the e-mail recipient has a _GMail_ address, then we have a big problem:  GMail dumps any e-mails received from your netbook's Postfix server as spam.  So, the intended e-mail recipient is unlikely ever to see your messages.

This is a nasty problem.  However, it cannot be a problem in principle:  Postfix is used by many professional ISPs as a core component of their e-mail systems.  But solving this problem properly will requiring delving deeper into Postfix.  Quite possibly, the definitive solution lies in trusted authentication of your Postfix installation through signed certificates from a respected Certificate Authority.  The following links might be helpful:

[http://www.postfix.org/](http://www.postfix.org/)
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

[COLOR=Red]It would be nice if an experienced Postfix user would write step-by-step instructions here to resolve this matter.[/COLOR]

In the mean time, a functional quick and easy work-around solution is *by relaying all e-mail sent* from your netbook with Postfix *through Google's SMTP server*.  It requires the setting up of a GMail account.


**(1A)  Postfix Relaying through GMail's SMTP Server**

Let us say, you have set up the following GMail account:  [FONT=Courier New][SIZE=3]myrelayaccount@gmail.com[/SIZE][/FONT] with password [FONT=Courier New][SIZE=3]myrelaypassword[/SIZE][/FONT].

Then you modify the Postfix configuration settings as follows:

Open a terminal screen (Ctrl+Alt+T, or via Applications > Accessories > Terminal) and type:

[FONT=Courier New][SIZE=3]gksudo gedit /etc/postfix/sasl/sasl_passwd[/SIZE][/FONT]

In the gedit file that opens, append the line

[FONT=Courier New][SIZE=3][smtp.gmail.com]:587      [EMAIL="myrelayaccount@gmail.com"]myrelayaccount@gmail.com[/EMAIL]:myrelaypassword[/SIZE][/FONT]

Save the gedit file and exit gedit.

Next, in the terminal screen, type:

[FONT=Courier New][SIZE=3]gksudo gedit /etc/postfix/main.cf[/SIZE][/FONT]

In the gedit file that opens, change [FONT=Courier New][SIZE=3]relayhost= [/SIZE][/FONT]to [FONT=Courier New][SIZE=3]relayhost= [smtp.gmail.com]:587[/SIZE][/FONT]

Next, add the following four lines at the bottom of the gedit file:

[FONT=Courier New][SIZE=3]smtp_use_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl/sasl_passwd
smtp_sasl_security_options = noanonymous[/SIZE][/FONT]

Save the gedit file and exit gedit.

Finally, in the terminal screen, type:

[FONT=Courier New][SIZE=3]sudo postmap /etc/postfix/sasl/sasl_passwd
sudo postfix stop
sudo postfix start
exit[/SIZE][/FONT]

You are now ready to send e-mail from your netbook, whichever way you connect to the internet.  There remain some minor issues if you use relaying via Google:  See items (3) and (4) below.  But there may well be a more important matter first:


**(2) Using only the Google SMTP Server on your Netbook, whatever your ISP**

Now, assume you exclusively intend to use Postfix as an SMTP server so that you can send e-mail when out of the office, whatever your 3G/4G TelCo provider.  And assume that you choose the quick solution to relay via Google (see (1A)).  Then, of course, you might as well use the Google SMTP server direct, rather than via Postfix.  In that case you* do not need to install Postfix on your netbook at all*.  Instead, you can then simply proceed as follows:

Again, let us say, you have set up the following GMail account:  [FONT=Courier New][SIZE=3]myrelayaccount@gmail.com[/SIZE][/FONT] with password [FONT=Courier New][SIZE=3]myrelaypassword[/SIZE][/FONT].

Then open Thunderbird, Edit > Account settings > Outgoing Server (SMTP).  Here, enter

[FONT=Courier New][SIZE=3]Server Name:  smtp.gmail.com
Port:  587
Connection security:  STARTTLS
Authentication method:  Normal password
User Name:  [EMAIL="myrelayaccount@gmail.com"]myrelayaccount@gmail.com[/EMAIL][/SIZE][/FONT]

The *password* for the GMail relay account ([FONT=Courier New][SIZE=3]myrelaypassword[/SIZE][/FONT]) will be asked by Thunderbird when you next send your first message.  Thunderbird will offer to remember this password.

Finally, in Thunderbird go to Edit > Account settings > your own works account details.  On the first configuration panel for your own works account, select from the drop-down box at the bottom:

[FONT=Courier New][SIZE=3]Outgoing Server (SMTP):  smtp.gmail.com[/SIZE][/FONT]

You are up and running.  But there remain some minor issues.


**(3)  NOTE about FROM and REPLY TO when Using a GMail Relay Account**

Google will _alter the message header_ of any e-mail relayed.  As a result, by default, any e-mail sent will *not show your proper works account* which you use in Thunderbird on your netbook.  Instead, your sent messages will show your GMail relay account both in the *From* line and as the *Reply-to* address.

Clearly, when the GMail account is used only as a relay tool, this is undesirable for professional works e-mail.  But, fortunately, the details which GMail writes in the message header can now be changed to any other e-mail address you own, such as your works e-mail address which you normally use in Thunderbird.  To make this change, you proceed as follows:

*Open the GMail relay account in your browser* and go to the *Mail settings* menu (click on the sprocket wheel in the top RH corner, next to the account name).  Go to *Accounts and Import*.

In *Send mail as*, click the button [FONT=Courier New][SIZE=3]Send mail from another address[/SIZE][/FONT].  GMail then takes you through a number of steps which are self evident.

When done, then click to *make this other address* the [FONT=Courier New][SIZE=3]default[/SIZE][/FONT].

In *Send mail as*, click *edit info* for the [FONT=Courier New][SIZE=3]myrelayaccount@gmail.com[/SIZE][/FONT] GMail relay account.  Then the *reply-to address* can also be freely chosen.  You can co-ordinate this with the reply-to address which you have set up as standard for your works account in Thunderbird.

Note that, under the bonnet (specifically, in the sender and return-path fields), the message header of any e-mail relayed via GMail will still retain the GMail relay account e-mail address as well.  However, the sender field and the return-path field are not normally displayed by the e-mail client (such as Thunderbird) of the recipient.  So, the recipient won't see this.


**(4)  NOTE about SENT MAIL when Using a GMail Relay Account**

By default, the GMail relay account will *indefinitely store copies of all relayed e-mails* in its *Sent Mail folder*.  If you only use the account for relaying, then you can set up a filter to *automatically remove* the relayed messages.

*Open the GMail relay account in your browser*.  In GMail, choose *Create a filter*.  GMail will then take you through two short pages to set up a filter.  Simply enter just two details as follows:

On the first page in the *From* field, enter:  [FONT=Courier New][SIZE=3]me[/SIZE][/FONT]
On the second page, select *Action*:  [FONT=Courier New][SIZE=3]Delete[/SIZE][/FONT]

Then any messages which you have sent yourself will be *moved direct to the Bin* (Trash) in GMail.  They will be automatically deleted from the Bin (Trash) after 30 days.  This will keep your GMail relay account clean.


__________

---

