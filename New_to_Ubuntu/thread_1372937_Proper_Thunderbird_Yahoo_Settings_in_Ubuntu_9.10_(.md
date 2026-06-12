---
title: "Proper Thunderbird Yahoo Settings in Ubuntu 9.10 (IT'S WORKING!)"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by turboopugsleylx on 2010-01-05
Hey guys after several hours I finally got this Thunderbird Yahoo up and running and downloading email messages on yahoo...thank god!

Here's how I did it

Go here and Download the newest version of Webmail and the Yahoo Webmail Extension
[http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)

Save these files to any folder or to the desktop

Open up Thunderbird and click Tools-> Addons->Installs

Once you click installs find the two .xpi webmail extensions and install them.

Restart Tbird

File->New->Account

Check "Email account" and click next

Fill in Email address "youremail@yahoo.com" and click next

Check "Pop" and make your incoming server 127.0.0.1 click next

Incoming Username "youremail@yahoo.com" and click next

Name your tbird folder whatever you want and click next..


Your account should have been created....now go to Edit->Account Settings 

Under your Yahoo email click "Server settings"

Make the Port 1025 and under security settings click "never" (you can fool around with this and see if you can get it to work under other security settings)....also make sure your Username reads "youremail@yahoo.com"

Then click OK

Lastly go to Tools->Addons again and highlight Webmail and then click Preferences

Make the port in here 1025 as well and then click ok....restart Tbird again...

Now try downloading your mail!

Hopefully this works for folks here let me know if u run into any issues!

Someone else can chime in with the proper smtp settings..

---

### Post by Dayofswords on 2010-01-05
i could have told ya for yahoo you have to pay to use a client without workaround :p

buy hey, gratz, now email your mother, she'd like it

---

### Post by shuttleworthwannabe on 2010-01-05
> **turboopugsleylx said:**
> Hey guys after several hours I finally got this Thunderbird Yahoo up and running and downloading email messages on yahoo...thank god!

Here's how I did it

Go here and Download the newest version of Webmail and the Yahoo Webmail Extension
[http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)

Save these files to any folder or to the desktop

Open up Thunderbird and click Tools-> Addons->Installs

Once you click installs find the two .xpi webmail extensions and install them.

Restart Tbird

File->New->Account

Check "Email account" and click next

Fill in Email address "youremail@yahoo.com" and click next

Check "Pop" and make your incoming server 127.0.0.1 click next

Incoming Username "youremail@yahoo.com" and click next

Name your tbird folder whatever you want and click next..


Your account should have been created....now go to Edit->Account Settings 

Under your Yahoo email click "Server settings"

Make the Port 1025 and under security settings click "never" (you can fool around with this and see if you can get it to work under other security settings)....also make sure your Username reads "youremail@yahoo.com"

Then click OK

Lastly go to Tools->Addons again and highlight Webmail and then click Preferences

Make the port in here 1025 as well and then click ok....restart Tbird again...

Now try downloading your mail!

Hopefully this works for folks here let me know if u run into any issues!

Someone else can chime in with the proper smtp settings..

or just go into yahoo mail options and set the preferred content setting to Asia--then you have POP3 enabled for free; currently getting all Yahoo mail in my gmail directly. [http://picobit.wordpress.com/2009/04/10/yahoo-mail-free-pop-access/](http://picobit.wordpress.com/2009/04/10/yahoo-mail-free-pop-access/)

S

---

### Post by Excedio on 2010-01-05
> **shuttleworthwannabe said:**
> or just go into yahoo mail options and set the preferred content setting to Asia--then you have POP3 enabled for free; currently getting all Yahoo mail in my gmail directly. [http://picobit.wordpress.com/2009/04/10/yahoo-mail-free-pop-access/](http://picobit.wordpress.com/2009/04/10/yahoo-mail-free-pop-access/)
 
S
 
This is awesome...thanks for the tip. :-)
 
Now my Thunderbird will be less bloated with extensions. :-)

---

### Post by premamotion on 2010-01-05
THANK YOU so much guys!!! Finally got the informations that makes this work... after struggling with ypops and things that got me crazy...

A big thank you, again!!!

---

### Post by shuttleworthwannabe on 2010-01-06
ur all welcome--it drove me nuts to figure this out--I googled a bit and found that link. Spread the good news.
S

---

### Post by turboopugsleylx on 2010-01-07
SMTP:

set outgoing server to 127.0.0.1 again

Set the port to 2050 in outgoing server settings....set it to 2050 in the webmail extension servers....and then select TLS if available.....check use name and password for verification...

should work

---

### Post by Ubunt24me on 2010-01-08
So that article was cool.  The thing is that it doesn't work for every basic yahoo account.  My guess is that they "Yahoo" had this fixed.  I can get one of my accounts working by using the new settings, but I've had the account for two or three years.  My newer account doesn't even have a pop3 or forwarding option. LOL
Oh well you get what you pay for sometimes. If anyone is aware of a newer solution that would be great.

---

### Post by shuttleworthwannabe on 2010-01-09
stick with "turbo's" solution for now, I guess. Nothing for 'mahala'!

---

### Post by m3owner on 2010-01-09
> **shuttleworthwannabe said:**
> or just go into yahoo mail options and set the preferred content setting to Asia--then you have POP3 enabled for free; currently getting all Yahoo mail in my gmail directly. [http://picobit.wordpress.com/2009/04/10/yahoo-mail-free-pop-access/](http://picobit.wordpress.com/2009/04/10/yahoo-mail-free-pop-access/)

S

I've tried both #1 and #3 above, Yahoo Mail indicates "Asia". When I go thru the setup process TB comes back and tells me that either my login e-mail address or my password is faulty, but I know they have been entered correctly.Any other suggestions?

---

### Post by shuttleworthwannabe on 2010-01-09
The link provides a very clear set of instructions--have a look there.

---

### Post by thejoempoem on 2010-01-10
I've followed your instructions, but when I click "Get Mail" the following error message pops up:
Sending of the password did not succeed. Mail server 127.0.0.1 responded: negative vibes from "myemail"@yahoo.com
-Thoughts?

Also, to reply to post #3:
switching your content to "Asia," for the POP3 fix only works if your yahoo email account is older-- my understanding is that whether or not you have the option depends on when you signed up for your yahoo account.
Mine is about a year old, and when I switch my content I still don't get that option.

---

### Post by thejoempoem on 2010-01-11
Found a fix online @ [http://www.mail-archive.com/thunderbird-webmail-extension@googlegroups.com/msg02996.html](http://www.mail-archive.com/thunderbird-webmail-extension@googlegroups.com/msg02996.html)

I had to switch my yahoo interface from "Classic" to the new beta version. Now it works.
Good stuff.

---

### Post by tad1073 on 2010-01-11
why not just use gmail and forward all your yahoo mail tho gmail?

---

### Post by Ubunt24me on 2010-01-11
I stumbled across a link.  [www.freepops.org](www.freepops.org)  I have been using it since Friday night and think it is a great solution to our problem.

---

### Post by pizzipie on 2010-05-14
Thanks a bunch everyone.

This worked for me  !!!!!!!!!!!!!!!!!

Rp

---

