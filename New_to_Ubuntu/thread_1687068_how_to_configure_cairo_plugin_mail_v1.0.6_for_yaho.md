---
title: "how to configure cairo plugin mail v1.0.6 for yahoo mail?"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by ebycs on 2011-02-13
How to configure cairo plugin mail v1.0.6 for yahoo mail? please help me...

---

### Post by Daveth on 2011-02-13
you need to add it to the dock, then right click the icon and get to the "configure this applet" dialogue. There you can change the icon, how it behaves and, on the 3rd tab, what it connects to. Yahoo is one of the drop-down options, and you need to add you account details. Looks straightforward.

---

### Post by ebycs on 2011-02-14
Thank u daveth for u r replay. But in cairo mail plugin i am able to configure gmail. There is no yahoo option in the configuration dropdown list.. Instead there is POP and IMAP options. When i select POP option the  default server address is 'pop3.myHost.org'. is it correct??? If not please give me the correct configuration.

---

### Post by ebycs on 2011-02-14
**Yahoo POP3 and SMTP Settings: **

 Find below the basic POP3 settings that you need to configure in the email program where you want to access Yahoo mails.
 
[LIST]
[*] **Incoming Mail (POP3) Server**: pop.mail.yahoo.com (Use SSL, port: **995**)
[*] **Outgoing Mail (SMTP) Server**: smtp.mail.yahoo.com (Use SSL, port: **465**, use authentication)
[*] **Account Name/Login Name**: Your Yahoo! Mail ID (your email address without the &#8220;@yahoo.com&#8221;)
[*] **Email Address**: Your Yahoo! Mail address (e.g., [email]user@yahoo.com[/email])
[*] **Password**: Your Yahoo! Mail password
[/LIST]
 Note that you also need to enable &#8220;**Web & POP Access**&#8221; on your **Yahoo Mail account** to send and receive Yahoo! Mail messages through any other email program.
 [CENTER][IMG]http://techblissonline.com/wp-content/uploads/pop3-yahoo-smtp.jpg[/IMG][/CENTER]
 
[LIST]
[*] Log on to your Yahoo mail account
[*] If you&#8217;re using the **new Yahoo Mail interface**, Click &#8220;**Options**&#8221; in the upper-right corner of the page, then choose &#8220;**More Options&#8230;**&#8221; from the pull-down menu and On the left side of the page, select the &#8220;**POP & Forwarding**&#8221; option.If you&#8217;re using the **original Mail interface**, click &#8220;**Mail Options**&#8221; in the upper-right corner of the page, then click the &#8220;**POP and Forwarding**&#8221; link on the left.
[*] On the &#8220;Pop and Forwarding&#8221; page, choose the &#8220;**Allow your Yahoo! Mail to be POPed**&#8221; option. You can instead choose to forward your emails to an external email account by choosing the option &#8220;**Forward your Yahoo! Mail**&#8221;  and specifying the external email address. But you can&#8217;t simultaneously  Forward and POP your mail. Also note that forwarded mail skips your  Yahoo! Mail Inbox entirely and goes straight to the new address you  designate.
[/LIST]
 Next you need to configure your Yahoo POP3 and SMTP settings (if you had chosen &#8220;*Allow your Yahoo! Mail to be POPed*&#8221; option) into your other mail program, to access Yahoo mails via the other program.
[LEFT][COLOR=#000000]
Read more:  [http://techblissonline.com/yahoo-pop3-and-smtp-settings/#ixzz1E0JEmvEg](http://techblissonline.com/yahoo-pop3-and-smtp-settings/#ixzz1E0JEmvEg)
[/COLOR][/LEFT]

---

